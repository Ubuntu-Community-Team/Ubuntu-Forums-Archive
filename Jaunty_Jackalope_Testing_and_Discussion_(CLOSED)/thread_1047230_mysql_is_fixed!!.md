---
title: "mysql is fixed!!"
date: 2009-01-22
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by DougieFresh4U on 2009-01-22
Setting up mysql-server-5.1 (5.1.30-2ubuntu3) ...
 * Stopping MySQL database server mysqld                                                                             [ OK ] 
 * Starting MySQL database server mysqld                                                                             [ OK ]

---

### Post by ruik on 2009-01-22
Yeah, finally!

---

### Post by super.rad on 2009-01-22
Noticed this earlier, finally configured mysql and amarok successfully :D

---

### Post by inportb on 2009-01-22
Yayyyy Amarok =D

---

### Post by ruik on 2009-01-23
Installing akonadi-server after installing amarok is still broken though.

---

### Post by felix.rommel on 2009-01-28
> **ruik said:**
> Installing akonadi-server after installing amarok is still broken though.

Todays updates fixed that problem here.

---

### Post by LordVeovis on 2009-01-29
mine is not working.  What can I do?

```
Setting up mysql-server-data-5.1 (5.1.30-2ubuntu5) ...
Setting up mysql-server-5.1 (5.1.30-2ubuntu4) ...
 * Stopping MySQL database server mysqld                                                                   [ OK ]
 * Starting MySQL database server mysqld                                                                   [fail]
invoke-rc.d: initscript mysql, action "start" failed.
dpkg: error processing mysql-server-5.1 (--configure):
 subprocess post-installation script returned error exit status 1
```

---

### Post by felix.rommel on 2009-01-31
> **LordVeovis said:**
> mine is not working.  What can I do?
invoke-rc.d: initscript mysql, action "start" failed.
dpkg: error processing mysql-server-5.1 (--configure):
 subprocess post-installation script returned error exit status 1[/CODE]

Do you want to update an existing mysql-server version or do you want to install it?

I upgraded from older versions of mysql-server and it worked with the newest update.

---

### Post by hapee on 2009-01-31
I still got the same errors as LordVeovis, what can we do to have a working upgraded mysql-server?

---

### Post by LordVeovis on 2009-02-01
I have an older post about mysql being broken (will link when I look it up) and I was able to use that again for a fix.  On my laptop this does not solve the problem though.

EDIT: [http://ubuntuforums.org/showthread.php?t=1040786](http://ubuntuforums.org/showthread.php?t=1040786)

---

### Post by omgbots on 2009-02-01
The botched original 5.1 upgrade left my mysql install in a state that I had to resolve manually.  Fortunately, it was easy to do.  If you have multiple .flag files in /var/lig/mysql, you probably do have the same problem.  Remove all of them and then reinstall the packages.

---

### Post by hapee on 2009-02-02
Did this, and indeed had to flag files, deleted both and reinstalled mysql-server-5.1 but same error, so no installation, seem error as above.

---

### Post by durand on 2009-02-06
> **hapee said:**
> Did this, and indeed had to flag files, deleted both and reinstalled mysql-server-5.1 but same error, so no installation, seem error as above.

Thanks! I was trying to get mysql-server installed which failed because the 5.0 -> 5.1 upgrade script kept dying and completely ignored the 5.1 package.

---

