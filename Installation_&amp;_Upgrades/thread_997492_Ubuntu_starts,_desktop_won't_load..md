---
title: "Ubuntu starts, desktop won't load."
date: 2008-11-29
forum: Installation &amp; Upgrades
---

### Post by Guyon on 2008-11-29
I used to run 8.04 on this system and it worked fine. When 8.10 came out I wrote a disk and got into the installation. I tried to run it without making changes, but all I got was a black screen and the pointer. I tried this multiple times with the same result, even in safe mode. I checked it for errors and found none, and the md5sum matched. I figured it was that 8.10 doesn't work with my system.

I re-downloaded 8.04 and tried to run it and got the same result. This makes me happy because I know it's not 8.10, but then again I have no idea what the problems is, so that makes me sad. :(

Now I'm stuck in XP, halp. :-k

---

### Post by sosaudio1 on 2008-11-29
> **Guyon said:**
> I used to run 8.04 on this system and it worked fine. When 8.10 came out I wrote a disk and got into the installation. I tried to run it without making changes, but all I got was a black screen and the pointer. I tried this multiple times with the same result, even in safe mode. I checked it for errors and found none, and the md5sum matched. I figured it was that 8.10 doesn't work with my system.

I re-downloaded 8.04 and tried to run it and got the same result. This makes me happy because I know it's not 8.10, but then again I have no idea what the problems is, so that makes me sad. :(

Now I'm stuck in XP, halp. :-k

graphics card change???

---

### Post by Guyon on 2008-11-29
> **sosaudio1 said:**
> graphics card change???
Nope, haven't changed any hardware.

---

### Post by sosaudio1 on 2008-11-29
> **Guyon said:**
> Nope, haven't changed any hardware.

graphics card driver error maybe?

---

### Post by sosaudio1 on 2008-11-29
> **sosaudio1 said:**
> graphics card driver error maybe?

lets try something else...can you get to terminal.....I think it is ctrl+alt+f1

if you can try start x or start gnome....may have to be with out the space...others on here will correct me...

---

### Post by alienseer23 on 2008-11-30
i am having the  same issue. I believe it has something to do with the nvidia driver

---

### Post by ericlovecn on 2008-11-30
> **alienseer23 said:**
> i am having the  same issue. I believe it has something to do with the nvidia driver

I have the same problem,I tried this:
killall gdm
ctrl+alt+f1
login
install the nvidia driver...
then i found the problem
the kernel of the ubuntu 8.10 is not supported by the nvidia driver
one solution is to compile yourself...
so GCC 4.2 is required so is source files...
but GCC4.3 8.10 supplies does not work...

---

### Post by Guyon on 2008-11-30
> **ericlovecn said:**
> I have the same problem,I tried this:
killall gdm
ctrl+alt+f1
login
install the nvidia driver...
then i found the problem
the kernel of the ubuntu 8.10 is not supported by the nvidia driver
one solution is to compile yourself...
so GCC 4.2 is required so is source files...
but GCC4.3 8.10 supplies does not work...
I also tried it on 8.04 too, and that didn't work either.

sosaudio1: I've tried that to no avail.

---

### Post by Guyon on 2008-11-30
Bump

---

### Post by Guyon on 2008-12-01
Fixed by 'Fix X Server' on boot.

---

### Post by nowhere@cox.net on 2008-12-02
Hey guys,

I have a quirky nvidia card (Geforce 7800 GT) that Ubuntu just doesn't like. It seems the open source nvidia driver just won't load on this card. You can try a couple things I did. The trick is to get a generic driver running at initial start up.

First question is does the live CD start ok? If so boot it up. If not and you have another machine on your network you should be able to ssh into the problem machine. Edit your xorg.conf file.```
sudo nano /etc/X11/xorg.conf
``` In the device section change the driver line to driver "vesa"```
Section "Device"
	Identifier	"Configured Video Device"
	Driver	        "vesa"
EndSection
```Save and reboot. This should get you running graphically but not with the nvidia drivers so no 3D. Now you should be able to run the Hardware Drivers from the System menu and install the recommended driver. Pay attention: if your driver installed successfully, then the little grey light next to the driver should turn into a circular arrow indicating a reboot is needed. If it doesn't then it didn't install. This is the only indication of success.

If you didn't get the reboot indicator, open a terminal and try it via apt.```
sudo apt-get remove nvidia-glx-177 (or your version)
sudo apt-get install nvidia-glx-177
```You should pay attention to see if there are any errors and post them for further help. You may have to install a lower version, remove it and install the higher version to get it to show any errors. I did. Mine complained about kernel headers missing because the apt-get install ubuntu-desktop on top of ubuntu server gives troubles with generic headers vs. server headers. If you have this problem I can help more getting you running.

Hope this gets you further along!

---

### Post by Guyon on 2008-12-06
Thanks [email]nowhere@cox.net[/email], I found instructions similar to yours in an Ubuntu book. This is what I did.

Put in the Live CD and started, and on the main menu that asks what you want to do, I pressed F6, and deleted "quiet splash --" from the boot options line. Next, I pressed F4 to go into Safe Graphics Mode so that I could use VESA graphics drivers. It worked fine and I did the installation, however now I ran into a separate issue.

I restarted and I chose Ubuntu 8.10 from the OS list. Maybe 5 seconds after hitting this, an error came up as shown:
```

Boot from (hd1,0) ext3   D829242f-5a86-4e8b-8945-021766b87d78
Starting up . . .
[        0.760144] Kernel panic - not syncing: VFS: Unable to mount root fs on unknown-block(0,0)

```

---

### Post by nowhere@cox.net on 2008-12-08
That sounds like a Grub issue and I'm not very good with Grub. How many hard drives do you have in the system? Do you have a Windows partition?

---

### Post by Guyon on 2008-12-10
> **nowhere@cox.net said:**
> That sounds like a Grub issue and I'm not very good with Grub. How many hard drives do you have in the system? Do you have a Windows partition?

I have windows installed on my hard drive but I'm installing Ubuntu on an external drive and telling it to take over the whole thing.

---

