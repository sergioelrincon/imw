# PHP

## Aspectos básicos del lenguaje

* [Sintaxis](https://www.w3schools.com/php/php_syntax.asp)
* [Comentarios](https://www.w3schools.com/php/php_comments.asp)
* [Variables](https://www.w3schools.com/php/php_variables.asp)
    * [Ámbito](https://www.w3schools.com/php/php_variables.asp)
* [Mostrar salida por pantalla](https://www.w3schools.com/php/php_echo_print.asp)
* [Tipos de datos](https://www.w3schools.com/php/php_datatypes.asp)
    * [Cadenas de caracteres](https://www.w3schools.com/php/php_string.asp)
    * [Números](https://www.w3schools.com/php/php_numbers.asp)
* [Constantes](https://www.w3schools.com/php/php_constants.asp)
* [Operadores](https://www.w3schools.com/php/php_operators.asp)
* Estructuras de control
  * [*if*](https://www.w3schools.com/php/php_if_else.asp)
  * [*switch*](https://www.w3schools.com/php/php_switch.asp)
  * [Bucles](https://www.w3schools.com/php/php_looping.asp)
* [Funciones](https://www.w3schools.com/php/php_functions.asp)
* [Arrays](https://www.w3schools.com/php/php_arrays.asp)
* [Variables superglobales](https://www.w3schools.com/php/php_superglobals.asp)
* [Formularios](https://www.w3schools.com/php/php_forms.asp)
* [include/require](https://www.w3schools.com/php/php_includes.asp)
* Manejo de ficheros
  * [readfile](https://www.w3schools.com/php/php_includes.asp)
  * [fopen/fread/fclose](https://www.w3schools.com/php/php_file_open.asp)
  * [fwrite](https://www.w3schools.com/php/php_file_create.asp)
* MySQL
  * [Conexión](https://www.w3schools.com/php/php_mysql_connect.asp)
        <?php
        $servername = "localhost";
        $username = "username";
        $password = "password";

        try {
          $conn = new PDO("mysql:host=$servername;dbname=myDB", $username, $password);
          // set the PDO error mode to exception
          $conn->setAttribute(PDO::ATTR_ERRMODE, PDO::ERRMODE_EXCEPTION);
          echo "Connected successfully";
        } catch(PDOException $e) {
          echo "Connection failed: " . $e->getMessage();
        }
        ?>
  * [Inserción de registros](https://www.w3schools.com/php/php_mysql_insert.asp)

        <?php
        $servername = "localhost";
        $username = "username";
        $password = "password";
        $dbname = "myDBPDO";

        try {
          $conn = new PDO("mysql:host=$servername;dbname=$dbname", $username, $password);
          // set the PDO error mode to exception
          $conn->setAttribute(PDO::ATTR_ERRMODE, PDO::ERRMODE_EXCEPTION);
          $sql = "INSERT INTO MyGuests (firstname, lastname, email)
          VALUES ('John', 'Doe', 'john@example.com')";
          // use exec() because no results are returned
          $conn->exec($sql);
          echo "New record created successfully";
        } catch(PDOException $e) {
          echo $sql . "<br>" . $e->getMessage();
        }

        $conn = null;
        ?>

  * [Consulta de registros](https://www.w3schools.com/php/php_mysql_select.asp)

        <?php
        $servername = "localhost";
        $username = "username";
        $password = "password";
        $dbname = "myDBPDO";

        try {
          $conn = new PDO("mysql:host=$servername;dbname=$dbname", $username, $password);
          $conn->setAttribute(PDO::ATTR_ERRMODE, PDO::ERRMODE_EXCEPTION);
          $stmt = $conn->prepare("SELECT id, firstname, lastname FROM MyGuests");
          $stmt->execute();

          $result = $stmt->fetchAll(PDO::FETCH_ASSOC);
          foreach ($resul as $row){    
            echo $row["firstname"]." ".$row["lastname"];}
        } catch(PDOException $e) {
          echo "Error: " . $e->getMessage();
        }
        $conn = null;
        echo "</table>";
        ?>

  * [Eliminación de datos](https://www.w3schools.com/php/php_mysql_delete.asp)

