<template>
    <div class="container">
        <h1 class="text-center">Employees List</h1>
        <table class="table table-striped">
            <thead>
                <th>Employee Id</th>
                <th>First Name</th>
                <th>Last Name</th>
                <th>Email</th>
            </thead>
            <tbody>
                <tr v-for="employee in employees" v-bind:key = "employee.id">
                    <td>{{employee.id}}</td>
                    <td>{{employee.firstName}}</td>
                    <td>{{employee.lastName}}</td>
                    <td>{{employee.email}}</td>
                </tr>
            </tbody>
        </table>
    </div>
</template>

<script>
import EmployeeService from '../services/EmployeeService'
    export default{
        name:'Employees-com',
        data(){
           return{
                employees : []
           }
        },
        methods:{
            getEmployees(){
                EmployeeService.getEmployees().then((response) => {
                    this.employees = response.data;
                });
            }
        },
        created(){
            this.getEmployees()
        }
    }
</script>

