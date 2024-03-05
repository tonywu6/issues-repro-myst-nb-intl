MyST-NB with gettext

```
python==3.11
sphinx==7.2.6
docutils==0.20.1
myst-nb==1.0.0
myst-parser==2.0.0
```

To reproduce:

```bash
python -m pip install -r requirements.lock # rye sync
python -m sphinx -T -E -b html -D language=de docs docs/_build/html
```

```
Traceback (most recent call last):
  File ".venv/lib/python3.11/site-packages/nbformat/reader.py", line 20, in parse_json
    nb_dict = json.loads(s, **kwargs)
              ^^^^^^^^^^^^^^^^^^^^^^^
  File "~/.rye/py/cpython@3.11.8/install/lib/python3.11/json/__init__.py", line 346, in loads
    return _default_decoder.decode(s)
           ^^^^^^^^^^^^^^^^^^^^^^^^^^
  File "~/.rye/py/cpython@3.11.8/install/lib/python3.11/json/decoder.py", line 337, in decode
    obj, end = self.raw_decode(s, idx=_w(s, 0).end())
               ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
  File "~/.rye/py/cpython@3.11.8/install/lib/python3.11/json/decoder.py", line 355, in raw_decode
    raise JSONDecodeError("Expecting value", s, err.value) from None
json.decoder.JSONDecodeError: Expecting value: line 1 column 1 (char 0)

The above exception was the direct cause of the following exception:

Traceback (most recent call last):
  File ".venv/lib/python3.11/site-packages/sphinx/cmd/build.py", line 298, in build_main
    app.build(args.force_all, args.filenames)
  File ".venv/lib/python3.11/site-packages/sphinx/application.py", line 355, in build
    self.builder.build_update()
  File ".venv/lib/python3.11/site-packages/sphinx/builders/__init__.py", line 293, in build_update
    self.build(to_build,
  File ".venv/lib/python3.11/site-packages/sphinx/builders/__init__.py", line 313, in build
    updated_docnames = set(self.read())
                           ^^^^^^^^^^^
  File ".venv/lib/python3.11/site-packages/sphinx/builders/__init__.py", line 420, in read
    self._read_serial(docnames)
  File ".venv/lib/python3.11/site-packages/sphinx/builders/__init__.py", line 441, in _read_serial
    self.read_doc(docname)
  File ".venv/lib/python3.11/site-packages/sphinx/builders/__init__.py", line 498, in read_doc
    publisher.publish()
  File ".venv/lib/python3.11/site-packages/docutils/core.py", line 236, in publish
    self.apply_transforms()
  File ".venv/lib/python3.11/site-packages/docutils/core.py", line 216, in apply_transforms
    self.document.transformer.apply_transforms()
  File ".venv/lib/python3.11/site-packages/sphinx/transforms/__init__.py", line 83, in apply_transforms
    super().apply_transforms()
  File ".venv/lib/python3.11/site-packages/docutils/transforms/__init__.py", line 182, in apply_transforms
    transform.apply(**kwargs)
  File ".venv/lib/python3.11/site-packages/sphinx/transforms/i18n.py", line 397, in apply
    patch = publish_msgstr(self.app, msgstr, source,
            ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
  File ".venv/lib/python3.11/site-packages/sphinx/transforms/i18n.py", line 73, in publish_msgstr
    doc = reader.read(
          ^^^^^^^^^^^^
  File ".venv/lib/python3.11/site-packages/docutils/readers/__init__.py", line 70, in read
    self.parse()
  File ".venv/lib/python3.11/site-packages/docutils/readers/__init__.py", line 76, in parse
    self.parser.parse(self.input, document)
  File ".venv/lib/python3.11/site-packages/myst_nb/sphinx_.py", line 89, in parse
    notebook = nb_reader.read(inputstring)
               ^^^^^^^^^^^^^^^^^^^^^^^^^^^
  File ".venv/lib/python3.11/site-packages/myst_nb/core/read.py", line 38, in standard_nb_read
    return nbf.reads(text, as_version=NOTEBOOK_VERSION)
           ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
  File ".venv/lib/python3.11/site-packages/nbformat/__init__.py", line 89, in reads
    nb = reader.reads(s, **kwargs)
         ^^^^^^^^^^^^^^^^^^^^^^^^^
  File ".venv/lib/python3.11/site-packages/nbformat/reader.py", line 76, in reads
    nb_dict = parse_json(s, **kwargs)
              ^^^^^^^^^^^^^^^^^^^^^^^
  File ".venv/lib/python3.11/site-packages/nbformat/reader.py", line 26, in parse_json
    raise NotJSONError(message) from e
nbformat.reader.NotJSONError: Notebook does not appear to be JSON: 'Franz jagt im komplett verwahrlosten Ta...

Exception occurred:
  File ".venv/lib/python3.11/site-packages/nbformat/reader.py", line 26, in parse_json
    raise NotJSONError(message) from e
nbformat.reader.NotJSONError: Notebook does not appear to be JSON: 'Franz jagt im komplett verwahrlosten Ta...
```
