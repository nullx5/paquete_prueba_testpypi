### Este es un paquete de prueba para aprender a subir paquetes a TestPyPI.

<img src="https://i.imgur.com/bNGurz8.png" alt="PyPI logo" width="300" height="200">

> Instalamos las librerias para construir y cargar el paquete.

```bash
pip install build setuptools wheel twine
```

> Estructura basica del paquete.

```bash
├──  paquete_prueba_bl3ssedc0de
│  ├──  __init__.py
│  └──  hola.py
├──  pyproject.toml
└──  README.md
```

> Construimos el paquete, esto creara el directorio dist/

```bash
python3 -m build
```

> Creamos una API token en TestPyPI, y la configuramos en local.


```bash
nvim ~/.pypirc
[testpypi]
  username = __token__
  password = pypi-Token
```

> Subimos el paquete a TestPyPI.


```bash
twine upload --repository testpypi dist/*
```

> Descargamos el paquete de TestPyPI.

```
pip install -i https://test.pypi.org/simple/ paquete-prueba-bl3ssedc0de==0.1.0
```

> Ejecutamos el paquete.

```
python3 -c "import paquete_prueba_bl3ssedc0de.hola as h; print(h.saludar())"
```
