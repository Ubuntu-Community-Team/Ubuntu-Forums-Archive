---
title: "Failed to upgrade 3 packages in 18.04 LTS"
date: 2018-05-05
forum: Installation &amp; Upgrades
---

### Post by terrylshg on 2018-05-05
Since upgrading to the Ubuntu 18.04 LTS, there are three packages cannot be updated to the latest version:

```

Package   Version Latest Type--------- ------- ------ -----
pycairo   1.16.2  1.17.0 sdist
pygobject 3.26.1  3.28.2 sdist
pyxdg     0.25    0.26   wheel

```

If I try to use the PIP INSTALL --UPGRADE command to upgrade the above three packages, here are the error messages:

```

[COLOR=#000000][FONT=&amp]Cannot uninstall 'pycairo'. It is a distutils installed project and thus we cannot accurately determine which files belong to it which would lead to only a partial uninstall.[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]Cannot uninstall 'pygobject'. It is a distutils installed project and thus we cannot accurately determine which files belong to it which would lead to only a partial uninstall.[/FONT][/COLOR]
[COLOR=#000000][FONT=&amp]Cannot uninstall 'pyxdg'. It is a distutils installed project and thus we cannot accurately determine which files belong to it which would lead to only a partial uninstall.[/FONT][/COLOR]

```


Any idea how to upgrade the above three packages properly? Thanks in advance.

---

### Post by Frogs Hair on 2018-05-05
Hello and Welcome

The link _may_ be related.
[https://github.com/pypa/pip/issues/5247](https://github.com/pypa/pip/issues/5247)

---

### Post by terrylshg on 2018-05-06
Thanks for the response. It seems that this command can help to upgrade the package without checking the installed package:

[COLOR=#000000][FONT=&quot]sudo -H pip install pycairo --upgrade --ignore-installed pycairo

Now, all the three packages had been updated successfully.[/FONT][/COLOR]

---

