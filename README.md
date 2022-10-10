<-- MySQL Commands -->

<-- Flow of database Database->Tables->Collections -->

                show databases; 		        <!-- taki pure list of databse ko dekh sake -->
                create database college;	    <!--  new database creation with name college  -->
                select database(); 		        <!-- kon se database me kaam kr rhe hai ye batata hai.-->
                use college;  			        <!-- Taki college database ko use kr store karne ke liye -->
                drop database college; 	        <!--	Delete karne ke liye. -->


 <-- SQL Queries for tables -->
        <-- DataTypes in SQL -  -->

             <!--   int - 	+ve,-ve and 0 value
                    Float -	decimal (5,2) matlab total 5 digit likhsakte hai aur 2 digit decimal ke baad hai eg. 456.22	
                    Varchar -	Text add karne ke liye we use varchar 
                    Enum -	yes/no & true/false         -->

        <!-- Attributes in SQL -jo variables like name,email,phone                    -->

        <!-- Constraints in SQL - Ye validation ke liye use hote hai

	                not null- validate krta hai ki null value nhi hogi
	                unique key- validate krta hai ki sari unique value honi chahiye
	                primary key- not null and unique banata hai
	                foreign key- connect karne ke liye 2 tables ko
	                default value - default me kuch de sakte hai -->


        show tables;   <!--selected database ke tables dekhne ke liye -->
                    <!-- Creating a Rough Table
                    1. No. of attributes
                    2. datatypes and validation-->

<-- CODE FOR TABLE CREATIONS -->

                    create Table student (
                    s_no INT NOT NULL   ,
                    name VARCHAR(255) NOT NULL ,
                    registration_number VARCHAR(255) NOT NULL,
                    gender VARCHAR(255)
                    );      

    <!-- Table Me DATA Add Karne ka command -->
		 INSERT INTO student(name,registration_number, gender) VALUES ("vikash", 1434332, "Male"); <!--1st method-->
		 INSERT INTO student VALUES (1,"deepak", 14332, "Male");                                   <!-- 2nd method-->                    
                    

    <!-- Fetching The data - to all data and spevific data -->
                SELECT * FROM `student`                             <!--pure table ke data ko fetch karne ke liye-->
                SELECT name FROM `student`                          <!-- Specific column ko -->
                SELECT * FROM student WHERE s_no>0;                 <!--vo data jiski sno. 0 se jyafa hai-->
                SELECT * FROm student ORDER BY name ASC;            <!--name ko ascending order me lane ke liye-->
                UPDATE student SET
                    registration_number = 14332
                        WHERE s_no =1;                              <!--update karne ke liye-->

                DELETE FROM student WHERE s_no =1;                  <!--delete karne ke liye-->     

    <!-- Foreign KEY CONCEPT -->

                        <!-- jub hum two different tables ko connect karna chahte hai to we use foreign key -->
                                <!-- eg. Student Table ko connect karna with library table -->

                            <!-- COLLEGE1 DATABASE -->


                                CREATE TABLE companies(
                                id INT NOT NULL AUTO_INCREMENT,
                                name VARCHAR(255) NOT NULL,
                                ctc VARCHAR(255) NOT NULL,
                                location VARCHAR(255) NOT NULL,
                                PRIMARY KEY(id)
                                );


                                CREATE TABLE students(
                                id INT NOT NULL AUTO_INCREMENT,
                                name VARCHAR(255) NOT NULL,
                                cgpa FLOAT  NOT NULL,
                                company_id INT,
                                    PRIMARY KEY(id),
                                FOREIGN KEY(company_id) REFERENCES companies(id)
                                );

                                
                                INSERT INTO companies VALUES (1,"Amazon","2.4lac","Banglore");

                                INSERT INTO students VALUES (1,"vikash","8.4",1);
                                