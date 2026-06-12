---
title: "cnt copy file to .wine directory"
date: 2007-04-04
forum: Installation &amp; Upgrades
---

### Post by graha on 2007-04-04
i cnt figure this out for kubuntu, so i am trying to do this tutorial to work in photoshop
[http://http://blog.publicidadpixelada.com/how-to-adobe-photoshop-cs2-on-ubuntu-10-steps/]("http://http://blog.publicidadpixelada.com/how-to-adobe-photoshop-cs2-on-ubuntu-10-steps/")
but i cant seem to copy the folder into 
home/'myusername/.wine/drive_c/Program Files/
i did everything what it said but when i tried copy the photoshop folder from my windows it wont copy or drag and drop it said in the bottom 
'you cannot drop any items in a directory in which you do not have write permission'
i've been using linux for about 1 month
:confused:

---

### Post by renzokuken on 2007-04-04
thats weird becuase you should have write access to all folders in your home directory.

are you replacing 'myusername' with *your* actual username? are you logged in with the same username as the directory you are copying to?

---

### Post by graha on 2007-04-04
there's only one username which is my actuall name .

---

### Post by geirha on 2007-04-04
what does this command run from a terminal say? ```
ls -ld ~/.wine/drive_c/Program\ Files/
```

---

### Post by graha on 2007-04-04
drwxr-xr-x 3 root root 4096 2007-03-19 18:16 /home/graha/.wine/drive_c/Program Files/

---

### Post by geirha on 2007-04-04
Well, there's your problem, the directory is owned, and only writable by root. You can run this command to make Program Files, and all subdirs and files be owned by you again:
```
sudo chown -R graha:graha ~/.wine/drive_c/Program\ Files/
```

---

### Post by geirha on 2007-04-04
And btw, I see these commands in the guide you pasted:

**sudo wine regedit adobe.reg**
**sudo wine &#8211;winver winxp &#8220;[path to Photoshop]/photoshop.exe**

There is no reason to run these with sudo, they will just mess up permissions/ownership, so try running them without sudo.

---

