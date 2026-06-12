---
title: "Uninstall a bin file"
date: 2008-08-24
forum: Installation &amp; Upgrades
---

### Post by ultimate_aektzis on 2008-08-24
Hello everybody!I want to uninstall a program that has been installed by a bin file.I tried some things such as chmod +x uninstaller but I cant do anything.
first of all I would like to know how to restore the file's access rights
And also what can I do to uninstall the file.the program is google earth

---

### Post by Ehtetur on 2008-08-24
ultimate_aektzis - This command makes any file executable:
> chmod 755 filename

I had google earth installed once upon a time.. but my memory sucks :evil:
I do kind of recall there being an uninstall script in the directory in which google-earth installed itself.. Run that as sudo and it will uninstall itself.

---

### Post by SudoScience on 2008-11-04
> **Ehtetur said:**
> ultimate_aektzis - This command makes any file executable:


I had google earth installed once upon a time.. but my memory sucks :evil:
I do kind of recall there being an uninstall script in the directory in which google-earth installed itself.. Run that as sudo and it will uninstall itself.
Hey, I'm new at Linux, but that uninstall folder is in filesystem/opt/google-earth, all the way at the bottom of the list.
(Note: make sure to check the View Hidden Files icon in the View window)

---

