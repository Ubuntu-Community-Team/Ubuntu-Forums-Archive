---
title: "Installing game"
date: 2008-11-05
forum: Installation &amp; Upgrades
---

### Post by Chamillionaire2 on 2008-11-05
Hey.

ok im a complete newbie to ubuntu and wanted to know how do i install a game that i downloaded.

its in .tar format. anyone know?

Thanks bye.

---

### Post by hwttdz on 2008-11-05
Well you're going to want to take it out of the tar format first, in the graphical interface you can double click and tell it where to put the contents.  There should be some sort of a readme in the contents that should walk you through the install.  

The command to untar the archive is 
tar -xvf archivename.tar

Hope that helps.

---

### Post by renzokuken on 2008-11-05
whats the game and what do the instructions say? what is the exact filename?

a .tar file is simply an archive, like .zip or .rar. extract it by right clicking and selecting Extract Here. then go into the new folder and look for a README or INSTALL file. open them and see what they say.

if it says to compile it you will need gcc and make which can be installed easily via

```
sudo apt-get install build-essential
```

---

