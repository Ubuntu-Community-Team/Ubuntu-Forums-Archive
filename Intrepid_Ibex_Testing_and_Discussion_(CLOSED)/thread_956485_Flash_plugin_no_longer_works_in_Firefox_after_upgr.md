---
title: "Flash plugin no longer works in Firefox after upgrade"
date: 2008-10-23
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by trolley on 2008-10-23
I have two systems I upgraded to the 8.10 beta. With one of them Flash kept working fine in Firefox, but on the other it no longer works and doesn't show up in about: plugins. I have uninstalled and reinstalled the flashplugin-nonfree package but it still doesn't work. Anyone know what else I could try?

---

### Post by philinux on 2008-10-23
In a terminal use

locate libflashplayer.so

see what you got in your system

---

### Post by trolley on 2008-10-23
No libflashplayer.so:

```
trolley@ubuntu:~$ locate libflashplayer.so
trolley@ubuntu:~$
```

However:

```
trolley@ubuntu:~$ sudo apt-get install flashplugin-nonfree -s
Reading package lists... Done
Building dependency tree       
Reading state information... Done
flashplugin-nonfree is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
```

---

### Post by trolley on 2008-10-23
Sorry, had to update my locate db:

```
trolley@ubuntu:~$ locate libflashplayer.so
/usr/lib/flashplugin-nonfree/libflashplayer.so
```

Still doesn't show up in about: plugins.

---

### Post by philinux on 2008-10-23
Close firefox. Go to your home folder and look in your firefox profile folder 
.mozilla/firefox/######.default and delete the file xpti.dat

Restart firefox see if it get picked up. 

Failing that create a folder plugins in the .mozilla folder and copy your libflashplayer.so file into it. Should not really need to do this but it can work.

---

### Post by trolley on 2008-10-23
I already blew away my whole ~/.mozilla/firefox directory and that didn't fix it. I'll try copying the plugin manually though.

---

### Post by trolley on 2008-10-23
Tried that. Still doesn't work. This is frustrating...

---

### Post by trolley on 2008-10-23
Ahha...found something. Ran firefox with strace and got:

```
write(2, "LoadPlugin: failed to initialize"..., 167LoadPlugin: failed to initialize shared library /usr/lib/flashplugin-nonfree/libflashplayer.so [libnss3.so: cannot open shared object file: No such file or directory]
) = 167
```

---

### Post by trolley on 2008-10-23
Fixed!

[http://ubuntuforums.org/showpost.php?p=5987637&postcount=11](http://ubuntuforums.org/showpost.php?p=5987637&postcount=11)

Thanks for the help though :)

---

### Post by philinux on 2008-10-23
Must have been the upgrade that didn't go well with flash. :)
Glad you're sorted.

---

