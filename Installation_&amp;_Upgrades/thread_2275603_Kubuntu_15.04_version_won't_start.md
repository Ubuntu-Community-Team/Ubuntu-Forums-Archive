---
title: "Kubuntu 15.04 version won't start"
date: 2015-04-27
forum: Installation &amp; Upgrades
---

### Post by mellow2 on 2015-04-27
I tried to register to kubuntu forums, but for some reason cannot create an account, so maybe someone here can help. I upgraded my Kubuntu to 15.04. Everything went fine until I tried to reboot. Grub starts alright, I choose Ubuntu 15.04, then there's a flash, the screen turns black and back on and I get a message "Starting version 219" and a blinking cursor and it just freezes there. Well, I snoop around and find out that i should hit ctrl+alt+f2, then run "sudo systemctl enable  sddm.service -f" then reboot. Ok sounds easy, but ctrl+alt+F2 doesn't do anything. I reboot to recovery mode and run the terminal as root, then try to run ```
sudo systemctl enable  sddm.service -f
``` As I already guessed, it sounds too easy. I get "Error getting authority: Error initializing authority: Could not connect: No such file or directory (g-io-error-quark, 1)". Ok, I search for more information and find some other people with the same problem. Apparently the solution is to first run ```
sudo dpkg --configure -a
``` then ```
sudo  systemctl enable  sddm.service -f
``` This has worked for everyone so surely this will work for me too? Well, after "sudo dpkg --configure -a" I get "dpkg: error: unable to access dpkg status area: Read-only file system". Are you kidding me? I try to google the meaning of this error message and apparently it should be fixed after removing /var/lib/dpkg/lock and then running ```
dpkg --reconfigure -a
``` Sounds good but after "rm lock" I get "rm: cannot remove lock: Read-only file system". On top of that "dpkg --reconfigure -a" gives "dpkg: error: unknown option --reconfigure". 

Turns out I am able to start Kubuntu by first going to recovery mode then choosing resume and then plasma. If I choose openbox, all I get is a grey background and cursor, nothing more. I am at a loss here. Can someone please help?

---

### Post by dino99 on 2015-04-27
try:

> sudo chown +x .Xauthority

[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)
note : respect lowercase, uppercase, and the spaces have to be respected

---

### Post by mellow2 on 2015-04-27
> **dino99 said:**
> try:

This gives chown: invalid user +x

---

### Post by FranklinSt on 2015-04-27
I've got essentially the  same issue except that I get to the sign on screen, enter my password, the screen flashes and returns to the sign on screen ad infinitum.

---

### Post by jorgitomarcano on 2015-04-28
I have the same exact problem and I have followed the exact same advises to no avail. The only difference is that I am using or trying to access after installation Ubuntu 15.04. Now, I am stuck and using nomodeset all of the time. Would really appreciate a fix on this. Very disappointing release.

---

### Post by dwaltz on 2015-04-28
In Openbox you should simply right-click on the desktop and access the Openbox menu to start at least a terminal, where you should be able to work to try the repair.

---

### Post by bapoumba on 2015-04-29
To the OP, you may be experimenting this if running from recovery mode : [https://bugs.freedesktop.org/show_bug.cgi?id=89289](https://bugs.freedesktop.org/show_bug.cgi?id=89289)

By "rm lock", you do mean removing the /var/lib/dpkg/lock file with root permissions, right ?
What are the outputs to :
```
mount
cat /etc/fstab
```

I may not be able to help you all the way with the filesystem mount problems, but a read only may be a sign of lots of error on that partition (failing partition ? corrupt upgrade ?).

And you last command should be (the --reconfigure option does not exist for dpkg) :
```
sudo dpkg-reconfigure -a
```

---

### Post by domhans on 2015-05-02
Observing the same issue. Kubuntu actually not usable. 
I'd prefer not to reinstall, so did anyone found a solution to this yet?

thanks 
dom

---

### Post by mellow2 on 2015-05-07
Ok I got my Kubuntu to work. First I changed my graphics card driver to nouveau. After that I was able to get Kubuntu working but the screen resolution was messed up so I changed back to nvidia drivers, and all of a sudden Kubuntu was working. The only problem is if I try to change to virtual console with alt+ctrl+f12 for example, I just get the starting version 219 text and blinking cursor. Does anyone know what is the problem here?

---

