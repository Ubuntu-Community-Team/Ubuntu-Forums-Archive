---
title: "Computer inaccessible after AMD driver update/TTY not working"
date: 2015-08-23
forum: Installation &amp; Upgrades
---

### Post by Kenneth_Andreasen on 2015-08-23
Hi

I tried to update the AMD Catalyst drivers on my computer but something went wrong and now I can't log in to my computer. 

I can get to the Ubuntu log on screen but when I enter my password the screen goes black for a couple of seconds and I am returned to the log on screen. So I can't log in to my user account.

I thought of deleting the Catalyst drivers through the TTY terminal but when I press ctrl-alt-F1 I just get a completely black/blank screen and I can't input anything. 

Is there a way of deleting the Catalyst drivers and revert to the open source drivers even if TTY doesn't work?

I use Ubuntu 15.04.

Any help is greatly appreciated.

---

### Post by QIII on 2015-08-23
You can enter recovery mode from GRUB, which we can explain in a bit.

First, however -- How did you install the fglrx driver?

---

### Post by Kenneth_Andreasen on 2015-08-23
> **QIII said:**
> First, however -- How did you install the fglrx driver?

I downloaded the latest deb files from the AMD page, and installed them using this command:
```
[COLOR=#000000]sudo dpkg [/COLOR][COLOR=#666600]-[/COLOR][COLOR=#000000]i fglrx[/COLOR][COLOR=#666600]*
[/COLOR][COLOR=#000000]sudo aticonfig [/COLOR][COLOR=#666600]--[/COLOR][COLOR=#000000]initial[/COLOR]
```

I thought of removing the driver again like this:
```
[COLOR=#000000]sudo apt[/COLOR][COLOR=#666600]-[/COLOR][COLOR=#000088]get[/COLOR][COLOR=#000000] remove [/COLOR][COLOR=#666600]--[/COLOR][COLOR=#000000]purge fglrx fglrx[/COLOR][COLOR=#666600]-[/COLOR][COLOR=#000000]amdcccle fglrx[/COLOR][COLOR=#666600]-[/COLOR][COLOR=#000000]core fglrx[/COLOR][COLOR=#666600]-[/COLOR][COLOR=#000000]dev[/COLOR]
```

I have already been trying the the low graphics mode from recovery. From this mode my GFX is not detected.

---

### Post by QIII on 2015-08-23
You should be able to remove it like that, but you should also get rid of the xorg.conf that was created when you initialized.

Rename it for now in case you want it later:

```
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
``` should work.

When you remove the driver, watch to see that apt doesn't try to replace it with the -updates packages.  If it says it is going to install them, don't continue.  Modify your purge command to add the -updates versions of everything.  That is, issue the command to purge both.

By the way

```
sudo apt-get purge
```

has the same effect as 

```
sudo apt-get remove --purge
```

but is less wear and tear on the fingertips.

---

### Post by Kenneth_Andreasen on 2015-08-23
Where do I put in those commands when the TTY Terminal is not working? I just have a blank screen with no way of entering anything.

(Propably a stupid question, but I am still fairly new to Ubuntu.)

---

### Post by QIII on 2015-08-23
Reboot your machine and hold the shift key down as soon as you hear the POST beep.  (If you don't have a motherboard speaker, just wait half a second and hold the shift key)

That should get you to GRUB.  Select Advanced Options and drop to Root.

When you get to the command prompt, type

```
mount -o remount,rw /
```

to mount your file system read/write.

You can do your work from there.  Remember, however, that you are root at that point and you need to be very careful what you do.

---

### Post by Kenneth_Andreasen on 2015-08-23
Thank you so very much!! 

It is working and I am able to log in again.

Is there a "correct" way of installing the FGLRX driver without risking problems like this?

---

### Post by QIII on 2015-08-23
Were I you, I would simply use the package available in the Ubuntu repo.  It is exactly the same driver as AMD had at the time Ubuntu was released in April.  It may be a version or two behind, but it is guaranteed to work with your release of Ubuntu.

I would also use the -updates version. 

```
sudo apt-get install fglrx-updates
```

This should also install fglrx-amdcccle-updates (the Catalyst Control Center) and fglrx-core.  If you don't see it in the list of things to be installed, answer "No" and modify the command to this:

```
sudo apt-get install fglrx-updates fglrx-amdcccle-updates fglrx-core
```

Be sure to run 

```
sudo amdconfig --adapter=all --initial
```

before rebooting.

If you would like to add the available hardware acceleration, please see the ATI driver link in my signature.  Scroll down a bit and you will find the section I added on installing hardware acceleration.

---

