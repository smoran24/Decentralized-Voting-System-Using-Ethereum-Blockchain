El sistema de votación descentralizado que utiliza Ethereum Blockchain es una solución segura y transparente para la realización de elecciones. Aprovechando la tecnología blockchain de Ethereum, este sistema garantiza registros de votación a prueba de manipulaciones, lo que permite a los usuarios emitir sus votos de forma remota mientras mantienen el anonimato y evitan el fraude. Explora este innovador proyecto para procesos de votación confiables y descentralizados.
Está hecho con Python (backend servidor local), Javascript, y Solidity (contratos inteligentes).

- Implementa JWT para la autenticación y autorización segura de votantes.
- Utiliza la blockchain Ethereum para registros de votación transparentes y a prueba de manipulaciones.
- Elimina la necesidad de intermediarios, lo que garantiza un proceso de votación confiable.
- Panel de administración para administrar candidatos, establecer fechas de votación y monitorear los resultados.
- Interfaz de usuario intuitiva para que los votantes emitan sus votos y vean la información de los candidatos.

Instalación:

1. Abrir un terminal en una carpeta donde se clonará el repositorio.
2. Clonar el repositorio mediante el comando: git clone https://github.com/smoran24/Decentralized-Voting-System-Using-Ethereum-Blockchain.git
3. Descargar e instala Ganache.
4. En Ganache crear un espacio de trabajo llamado Development. Agregar un proyecto haciendo clic en el botón ADD PROJECT en la sección de proyectos de Truffle(.truffle-config.js).
5. Descargar la extensión Metamask para el navegador.
6. Crear una billetera en Metamask, luego Importar cuentas desde Ganache (usando las cadenas que aparecen ahí)
7. Agregar red a Metamask. (Nombre de la red: Localhost, Puerto 7575, RPC URL: http://localhost:7545, ID de cadena: 1337, símbolo de moneda: ETH)
8. Abrir MySQL Workbench y crear una base de datos llamada voter_db.
9. En la base de datos creada, crear una nueva tabla llamada voters en el formato dado y agregar algunos valores (por ej, un usuario admin y un par de votantes):
   CREATE TABLE voters (
    voter_id VARCHAR(36) PRIMARY KEY NOT NULL,
    role ENUM('admin', 'user') NOT NULL,
    password VARCHAR(255) NOT NULL
    );
10. Abrir terminal e instalar Truffle a nivel global: npm install -g truffle
11. Ir al directorio raíz del repositorio local e instalar los node modules: npm install
12. Instalar dependencias de python: pip install fastapi mysql-connector-python pydantic python-dotenv uvicorn uvicorn[standard] PyJWT
13. Importante: Actualizar las credenciales con las de tu base de datos en el archivo: ./Database_API/.env
14. Abrir una terminal de windows en el directorio raíz del proyecto y ejecutar el comando:  truffle console
15. En la misma terminal, compilar los contratos inteligentes con el comando:  compile

Uso:
1. Abrir Ganache e ir al espacio de trabajo Development.
2. En Visual Studio Code, abrir el proyecto, abrir dos terminales y en una agrupar la app.js con browserify:  browserify ./src/js/app.js -o ./src/dist/app.bundle.js (Si no funciona por algún error de política de ejecución, correr el siguiente comando en Powershell como administrador: Set-ExecutionPolicy RemoteSigned)
3. En la segunda terminal, navegar a la carpeta Database_API, y escribir lo siguiente para iniciar el servidor de bases de datos:  uvicorn main:app --reload --host 127.0.0.1
4. En la primer terminal, iniciar el servidor node:  node index.js
5. La app debería correr en http://localhost:8080/ (ABRIR 2 PESTAÑAS, una para user admin y otra para cliente)
6. En una tercer terminal, migrar el contrato de truffle a la blockchain local:  truffle migrate
7. Recargar ambas páginas. Iniciar sesión en las dos.
8. En la página de admin, agregar 2 candidatos y establecer fecha de votación. (Se abrirá Metamask cada vez que se presione un botón pidiendo hacer una transacción con ETH. Confirmar)
9. En la página de user, votar por uno de los candidatos.
