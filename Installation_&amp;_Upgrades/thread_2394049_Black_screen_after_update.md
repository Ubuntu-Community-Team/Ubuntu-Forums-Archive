---
title: "Black screen after update"
date: 2018-06-11
forum: Installation &amp; Upgrades
---

### Post by brunushky on 2018-06-11
Hi, I come here looking for help....

After a normal week update I reboot my PC, just to found that I lost graphic support. 
I can log using tty, but I  can get login screen, instead just a black screen... I face a problem like this on the past and reinstalling drivers did the trick but this time I need some help.

Im running a desktop PC with dual graphics cards, the PCI express is a NVIDIA corporation gt218 Geforce210 rev a2. I normally use this one, used to use it with propietary drivers and aslo with ubuntu repository drivers... it works well with both.

The onvoard is a radeon 3000 series RS780L... In never take the time make run this one.


Right now I'm using the the nvidia-current-updates drivers in my case it's install nvidia-304.xxx
Also FailsafeX didnt work, in resume I only can use tty... I can get graphics in anyway....what should I search in logs and stuf like that... I dont
want to reinstall, I use this machine for work and have a many of things  preconfigured to my every day tasks.

thhnkas in advance

---

### Post by brunushky on 2018-06-13
Bump

---

### Post by Bashing-om on 2018-06-13
brunushky; Hello- 

You want the 340 version driver:
[http://www.nvidia.com/object/IO_32667.html](http://www.nvidia.com/object/IO_32667.html)

Try:
```

sudo rm /etc/X11/xorg.conf #Maybe does not exist; OK
sudo apt purge nvidia
sudo apt update
sudo apt full-upgrade
sudo ubuntu-drivers autoinstall

```

[INDENT][INDENT]maybe Yes
[/INDENT][/INDENT]

---

### Post by cruzer001 on 2018-06-13
Hello people

Also...

We recently had kernel/microcode updates.  Have you tried reverting back to the previous kernel at boot?

And what are you running?  Ubuntu?  16.04?

---

### Post by brunushky on 2018-06-16
Hi thanks to all for your effort, I finally found the problem and fix it...

I found this error on multiple lines in the greeter log...```
**nano** [B]/var/log/lightdm/seat0-greeter.log

[/B]...
/usr/sbin/unity-greeter: error while loading shared libraries: libwayland-egl.so.1: cannot open shared object file: No such file or directory
...

```Also in terminal executing some command return this  ```
**unity-control-center -l**

libwayland-egl.so.1: cannot open shared object file: No such file or directory
Failed to load module: /usr/lib/i386-linux-gnu/unity-control-center-1/panels/libuser-accounts.so
Unknown option -l

```With this references, I found that these files were lost in my system under /usr/lib/x86_64-linux-gnu folder. 
So looking with google I found this ... [B][latest mesa breaks wayland – workaround]("https://wordpress.padoka.org/2018/06/09/latest-mesa-breaks-wayland-workaround/")
[/B]
So running this command in terminal solve the missing lib in my system, after reboot the graphics return to normal.
```
**apt install libwayland-egl1**
```
Hope this help others with same problem... Thanks. ):P

---

### Post by Bashing-om on 2018-06-16
brunushky; Hey -

Great find ! Pleased you provided the solution and I have passed it on along .

[INDENT][INDENT]'buntu
[INDENT][INDENT]all in this together
[/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by brunushky on 2018-06-16
@cruzer001, yes Ubuntu 16.04

---

