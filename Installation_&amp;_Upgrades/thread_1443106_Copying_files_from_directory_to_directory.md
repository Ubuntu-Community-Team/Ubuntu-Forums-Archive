---
title: "Copying files from directory to directory"
date: 2010-03-30
forum: Installation &amp; Upgrades
---

### Post by Datamac on 2010-03-30
I have some configuration files that are in the wrong directory.  The files are web server configuration files that are in the apache2 directory.  I need to get them into the sites-available directory.  Using the GUI I get error moving files.  Seems I don't have the necessary permissions to get the job done.  Can anyone help me?

---

### Post by Xog on 2010-03-30
```
sudo mv directory1 directory2
```

or

```
sudo mv "file" directory
```

^^^^^
replacing 'directory' with the actual directory, and 'file' with the actual file

---

### Post by Datamac on 2010-03-30
Thank you!:KS

---

