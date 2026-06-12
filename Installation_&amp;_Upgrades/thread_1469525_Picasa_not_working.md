---
title: "Picasa not working"
date: 2010-05-02
forum: Installation &amp; Upgrades
---

### Post by rajesh120 on 2010-05-02
Hello friends i hav downloaded picasa from
```
http://picasa.google.com/linux/thanks-deb.html
```
i used the deb file and installed it but when i go to applications>graphics>picasa>picasa
nothing happens...:(
Even when i open a image file i dont get an additional option to view it in picasa..
Plz help...:confused:
can anyone also tell me hw to install google gadgets and googl toolbar ??

---

### Post by rajesh120 on 2010-05-03
> **rajesh120 said:**
> Hello friends i hav downloaded picasa from
```
http://picasa.google.com/linux/thanks-deb.html
```i used the deb file and installed it but when i go to applications>graphics>picasa>picasa
nothing happens...:(
Even when i open a image file i dont get an additional option to view it in picasa..
Plz help...:confused:
can anyone also tell me hw to install google gadgets and googl toolbar ??
Plz reply

---

### Post by infamous-online on 2010-05-03
So are you trying to make Picasa the default program for your pictures?

---

### Post by bbrand on 2010-05-03
Same here, trying Picasa from the console ... oh oh

/usr/bin/picasa: line 139: 11246 Segmentation fault      "$PIC_BINDIR"/wrapper check_dir.exe.so
/usr/bin/picasa: line 175: 11350 Segmentation fault      "$PIC_BINDIR/wrapper" regedit /E $registry_export HKEY_USERS\\S-1-5-4\\Software\\Google\\Picasa\\Picasa2\\Preferences\\

OK, so who owns this one? Google?

---

### Post by rajesh120 on 2010-05-03
So i want to tell u the message i m getting at terminal
-->
/usr/bin/picasa: line 139:  2045 Segmentation fault      "$PIC_BINDIR"/wrapper check_dir.exe.so
/usr/bin/picasa: line 175:  2148 Segmentation fault      "$PIC_BINDIR/wrapper" regedit /E $registry_export HKEY_USERS\\S-1-5-4\\Software\\Google\\Picasa\\Picasa2\\Preferences\\
.........plz help???

---

### Post by oceanexplorer on 2010-05-03
I can also add that I am having this issue with a current clean install of Lucid Lynx 10.04. It worked fine on the Beta releases so not sure what has changed!

---

### Post by oceanexplorer on 2010-05-03
The thing with Picasa is it's not a native program to Linux, when you launch the program it actually launches Wine to run it, albeit behind the scenes. The error talks about HKEY USERS which is from the Windows registry, so it leads me to think it might be a Wine issue. Will try installing Picasa under the latest Wine and let you know the results!

---

### Post by rajesh120 on 2010-05-04
> **oceanexplorer said:**
> The thing with Picasa is it's not a native program to Linux, when you launch the program it actually launches Wine to run it, albeit behind the scenes. The error talks about HKEY USERS which is from the Windows registry, so it leads me to think it might be a Wine issue. Will try installing Picasa under the latest Wine and let you know the results!
I understand what are u trying to say but the poblem is the packege is originally made for for linux..(ubuntu)
ie a .deb file
So i dont think it will use wine for it.......u can use picasa of exe version using wine but this version is made by google for linux only........so

---

### Post by aeiah on 2010-05-04
> **rajesh120 said:**
> I understand what are u trying to say but the poblem is the packege is originally made for for linux..(ubuntu)
ie a .deb file
So i dont think it will use wine for it.......u can use picasa of exe version using wine but this version is made by google for linux only........so

its actually still a windows version, its just that google packages it with wine to make things seamless.

im having issues too with picasa under 10.04... it starts up fine, but finds no photos. no errors in the terminal because of the way it launches its self (seems to detach from the terminal...)

---

### Post by rajesh120 on 2010-05-05
> **aeiah said:**
> its actually still a windows version, its just that google packages it with wine to make things seamless.

im having issues too with picasa under 10.04... it starts up fine, but finds no photos. no errors in the terminal because of the way it launches its self (seems to detach from the terminal...)
for me even picasa installer is not workin

---

### Post by kellemes on 2010-05-05
[How to install Picasa 3.6 in Ubuntu]("http://www.facebook.com/note.php?note_id=385280874742")

Don't click the Places-Button!!
If you do, see following post for fix.
[http://ubuntuforums.org/showpost.php?p=8694147&postcount=1]("http://ubuntuforums.org/showpost.php?p=8694147&postcount=1")

Working fine on my system (Lucid).

---

### Post by infamous-online on 2010-05-05
Picasa is working fine for me did you guys download the deb from the site or did you use the terminal or the package manager?

---

### Post by T_W on 2010-05-16
The answer is here:

[http://groups.google.com/group/Google-Labs-Picasa-for-Linux/browse_thread/thread/91d956e2d643cb19?hl=en]("http://groups.google.com/group/Google-Labs-Picasa-for-Linux/browse_thread/thread/91d956e2d643cb19?hl=en")

> Recent kernels (including Fedora and Ubuntu) disable low-address page
mapping, to fix a known local root exploit.  Many typical Wine apps
crash with something like:
    wine: Unhandled page fault on read access to 0x00000000 at address
0xb7d3b463

To disable this security fix, as root do the following:
    sysctl -w vm.mmap_min_addr=0
(Picasa should work again.) 

I did a 'sudo sysctl -w vm.mmap_min_addr=0' and Picasa worked.

---

### Post by Nemo34 on 2010-06-17
Didn't work for me.

I don't mess too much with my install, got Picasa stable 2.7 version directly from the repository. What gets on my nerves is that I've been switching between gThumb, F-Spot and Shotwell but non is a decent pick:

F-Spot is too slow and keep on messing with my directories
gThumb doesn't display pictures other than directory after directory
(troublesom after fspot passed by
Shotwell is pretty, but it is only pretty: no feature at all!

---

### Post by aasche on 2010-07-02
> **Nemo34 said:**
> Didn't work for me.

I don't mess too much with my install, got Picasa stable 2.7 version directly from the repository.
Picasa 2.7 for Linux is broken (in newer Ubuntu versions). Please use 3.0 beta for Linux (*wine* included) or install *wine* and then the windows version of Picasa.

---

### Post by marriedbachelor18 on 2010-08-11
i was having problems with opening picasa and im not sure what is different from the way i did it the first time and the walk through given below but it works. it opens seamlessly now and im not having any problems.
[http://www.ubuntugeek.com/how-to-install-picasa-30-beta-in-ubuntu.html](http://www.ubuntugeek.com/how-to-install-picasa-30-beta-in-ubuntu.html)

---

### Post by 130s on 2011-03-02
> **T_W said:**
> The answer is here:

[http://groups.google.com/group/Google-Labs-Picasa-for-Linux/browse_thread/thread/91d956e2d643cb19?hl=en]("http://groups.google.com/group/Google-Labs-Picasa-for-Linux/browse_thread/thread/91d956e2d643cb19?hl=en")


Unfortunately, this won't solve the issue on my machine.

> **marriedbachelor18 said:**
> i was having problems with opening picasa and im not sure what is different from the way i did it the first time and the walk through given below but it works. it opens seamlessly now and im not having any problems.
[http://www.ubuntugeek.com/how-to-install-picasa-30-beta-in-ubuntu.html](http://www.ubuntugeek.com/how-to-install-picasa-30-beta-in-ubuntu.html)

This solved! Thanks!

Env: Ubuntu 10.04 Netbook edition, Starling Star3

---

### Post by hiralrajani on 2011-04-21
> **marriedbachelor18 said:**
> 
[http://www.ubuntugeek.com/how-to-install-picasa-30-beta-in-ubuntu.html](http://www.ubuntugeek.com/how-to-install-picasa-30-beta-in-ubuntu.html)

Worked for me as well!!

---

### Post by Khakilang on 2011-04-22
Picasa seem to work fine for me. I am using Ubuntu 10.10 64bit and Picasa 3.0 64bit. Just install after the download. Are you trying to run a 32bit Picasa under 64bit Ubuntu?

---

