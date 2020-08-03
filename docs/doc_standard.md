Each repo to have README.rst in root dir.

README.rst should have a 'Features' section near ths start:

    .. features-start

    Features
    --------

    * `e.g. Configuration Manager` <url-to_config_manager_docs>`_
    * `Feature 2 <url_to_generated_docs>`_
    * etc

    .. features-end

The features-start/end comment strings will allow us to extract this section and put it at the top of the main documentation page.

Documentation in /docs subfolder, may need to be renamed from /doc for some projects. Should contain the following files (other files will be autogenerated by sphinx):

    /docs
        index.rst
        module_ref.rst
        readme.rst
        tutorial_list.rst
        tutorial1.rst
        tutorial2.rst

# readme.rst
Generates a copy of the root level README.rst using the rst/sphinx `include::` directive:

    .. include:: ../README.rst

# index.rst
generates the front page for read the docs, and the table of contents on the left hand side. Table of contets entries are based on the contents of readme.rst, module_ref.rst and tutorials.rst

# module_ref.rst
The module reference should contain an entry for every .py file in the module. Taking a simplified version of surgerycore as an example:

    sksurgerycore/
        algorithms/
           averagequaternion.py
           pivot.py
        configuration/
            configuration_manager.py

`module_ref.rst` would contain something like

**Note** The reason we have to use the `.. features-start` strings is due to GitHub not processing the `include::` durective in .rst files, for security purposes. If this was possible, we could have a separate features.rst file, and use `include::` in both README.rst and docs/index.rst.
    

