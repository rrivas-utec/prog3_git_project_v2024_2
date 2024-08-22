# Sistema de Gestión de Archivos de Datos Tabulares

## Descripción del Ejercicio

En este ejercicio, construirás un **Sistema de Gestión de Archivos de Datos Tabulares** en C++ que permite manejar diferentes tipos de archivos de datos, incluyendo CSV, Excel, YAML y binarios. El sistema te permitirá practicar conceptos de programación orientada a objetos, incluyendo herencia, polimorfismo, y manejo de recursos con constructores de copia y movimiento.

## Objetivo

Implementar un sistema que permita:
1. Leer y escribir datos en diferentes formatos de archivo.
2. Utilizar herencia para definir diferentes tipos de archivos de datos.
3. Aplicar constructores de copia y movimiento.
4. Sobrecargar operadores y usar relaciones de amistad (`friend`) entre clases.

## Requisitos

### Clases Principales

- **Clase Base `DataFile`:**
    - **Atributos:**
        - `filename`: Nombre del archivo.
        - `data`: Contenido del archivo, representado como una estructura tabular en memoria.
    - **Métodos:**
        - Constructor que acepte un nombre de archivo.
        - Métodos para obtener el nombre del archivo y los datos.
        - Métodos virtuales `read()` y `write()` para leer y escribir datos del archivo.
    - **Constructores:**
        - Constructor por defecto.
        - Constructor con parámetros.
        - Constructor de copia.
        - Constructor de movimiento.
    - **Operadores:**
        - Sobrecargar el operador de asignación de copia.
        - Sobrecargar el operador de asignación de movimiento.

- **Clase Derivada `CSVFile`:**
    - **Métodos:**
        - Implementación de `read()` y `write()` para el formato CSV.

- **Clase Derivada `ExcelFile`:**
    - **Métodos:**
        - Implementación de `read()` y `write()` para el formato Excel.

- **Clase Derivada `YAMLFile`:**
    - **Métodos:**
        - Implementación de `read()` y `write()` para el formato YAML.

- **Clase Derivada `BinaryFile`:**
    - **Métodos:**
        - Implementación de `read()` y `write()` para el formato binario.

### Funcionalidad Adicional

- **Funciones Amigas (`friend`):** Implementa una función amiga que permita comparar los datos de dos archivos para verificar si son iguales.

### Programa Principal (`main`)

- Crea instancias de diferentes tipos de archivos (`CSVFile`, `ExcelFile`, `YAMLFile`, `BinaryFile`) utilizando tanto el constructor por defecto como el constructor con parámetros.
- Utiliza los constructores de copia y movimiento para crear y manipular copias de archivos.
- Lee y escribe datos en diferentes formatos.
- Utiliza la función amiga para comparar los datos de dos archivos y muestra el resultado.

### Ejemplo de Uso

```cpp
int main() {
    CSVFile csv("data.csv");
    ExcelFile excel("data.xlsx");
    YAMLFile yaml("data.yaml");
    BinaryFile binary("data.bin");

    csv.read();
    excel.read();
    yaml.read();
    binary.read();

    csv.write();
    excel.write();
    yaml.write();
    binary.write();

    // Comparación de datos
    if (compareData(csv, excel)) {
        std::cout << "CSV and Excel files have the same data." << std::endl;
    } else {
        std::cout << "CSV and Excel files have different data." << std::endl;
    }

    // Uso de constructores de copia y movimiento
    CSVFile csvCopy = csv;  // Constructor de copia
    BinaryFile binaryMove = std::move(binary);  // Constructor de movimiento

    return 0;
}
```


**versión**: prog3_git_project_v2024_2