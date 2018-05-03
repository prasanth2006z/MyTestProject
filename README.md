<!DOCTYPE html>
<html>
<script src="https://ajax.googleapis.com/ajax/libs/angularjs/1.6.9/angular.min.js"></script>
<body>

<div ng-app="myApp" ng-controller="myCtrl"> 

<tr ng-repeat="item in content">
            <td>
				<h3>{{item}}</h3>
						
			</td>
</tr>

</div>



<script>
var app = angular.module('myApp', []);
app.controller('myCtrl', function($scope, $http) {
		 $http({
		   url: "http://localhost:8080/read?count=0", 
		   method: "GET",
		   headers: {"userName": "test", "password":"test"}
		 })  
  .then(function(response) {
      $scope.content = response.data;
  }, function(response) {
      $scope.content = "Something went wrong";
  });
});
</script>

</body>
</html>
