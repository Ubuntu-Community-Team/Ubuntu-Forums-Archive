---
title: "error: externally-managed-environment"
date: 2023-03-24
forum: Installation &amp; Upgrades
---

### Post by hoboy on 2023-03-24
error: externally-managed-environment

    I am using ubuntu 23.04 since some updates I can''t use python comment in the terminal
    it cause this error.
    as far as I know this is not debian.
    python -m pip install Jinja2
    error: externally-managed-environment

    × This environment is externally managed
    &#9584;&#9472;> To install Python packages system-wide, try apt install
    python3-xyz, where xyz is the package you are trying to
    install.

    If you wish to install a non-Debian-packaged Python package,
    create a virtual environment using python3 -m venv path/to/venv.
    Then use path/to/venv/bin/python and path/to/venv/bin/pip. Make
    sure you have python3-full installed.

    If you wish to install a non-Debian packaged Python application,
    it may be easiest to use pipx install xyz, which will manage a
    virtual environment for you. Make sure you have pipx installed.

    See /usr/share/doc/python3.11/README.venv for more information.

    note: If you believe this is a mistake, please contact your Python installation or OS distribution provider. You can override this, at the risk of breaking your Python installation or OS, by passing --break-system-packages.
    hint: See PEP 668 for the detailed specification.

---

### Post by oldfred on 2023-03-24
Closed, duplicate.
You already has same post in Development sub-forum.
[https://ubuntuforums.org/showthread.php?t=2485257](https://ubuntuforums.org/showthread.php?t=2485257)

---

