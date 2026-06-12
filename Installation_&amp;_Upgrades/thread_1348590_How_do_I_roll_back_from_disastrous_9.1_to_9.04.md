---
title: "How do I roll back from disastrous 9.1 to 9.04"
date: 2009-12-07
forum: Installation &amp; Upgrades
---

### Post by John.St on 2009-12-07
I unfortunately upgraded my excellent ubuntu 9.04 to 9.10 and now my computer goes completely dead after boot.

Using 2.6.27-11 generic
"Ubuntu is running in low graphics mode
Failed to load NVIDIA kernel module
Please check your"
<rest of text hidden and inaccessible>

After a CR
"What would you like to do?
o Run ubuntu in low graphics
o Reconfigure graphics
o Troubleshoot"
<rest of text hidden and inaccessible>

Neither mouse, CR, PageDown, nor other keys are working.

Using the recovery mode does not work either:
It does not accept the root password, is waiting for access to swap, then stops.

Fortunately I can use this computer in a town only 22 km away (living high up in the Andes mountains) to get access to my mail and ubuntuforums.

I want to get rid of the ubuntu 9.10 disaster and roll back to dear, old 9.04.

Let me add that I installed (upgraded) using the UpdateManager update option.

How to, anyone?

---

### Post by wilee-nilee on 2009-12-07
In the recovery are you using your login name then password.

---

### Post by jaylsi on 2009-12-07
Could be very difficult to rollback. Don't know if that is even possible. It is very likely you just need to install a proper nVidia driver. If you figure out how to proceed with recovery mode, you can try to rename /etc/X11/xorg.conf to another file and reboot, see what happens.

---

### Post by howefield on 2009-12-07
> **John.St said:**
> I want to get rid of the ubuntu 9.10 disaster and roll back to dear, old 9.04. How to, anyone?

Back up your files/data ect and reinstall from scratch. Only realistic way to do it.

---

### Post by JBAlaska on 2009-12-07
If your going to backup /home and re-install, you might want to give 9.10 another chance with a **clean install** rather than the upgrade you did.

If all else fails you will still have your /home backup and you can do a fresh install of 9.04 if you want.

BTW: In addition of backing up /home you can also backup and restore all your installed packages (In your case by booting from a LiveCD and mounting your HD Linux partition), like so:

**Copy all installed packages to a file:**
```
sudo dpkg --get-selections > myPackages
```

**Reinstall the packages after installation:**
```
sudo dpkg --set-selections < myPackages && sudo apt-get dselect-upgrade
```

---

### Post by ezsit on 2009-12-07
> Using 2.6.27-11 generic

This kernel is from Intrepid, a.k.a. 8.10. Ubuntu 8.10 is two versions behind the current 9.10. Are you sure that is the kernel you are trying to boot into?

If so, this explains a lot of problems. Ubuntu 9.10 should be running kernel 2.6.31.something and Ubuntu 9.04 should be running 2.6.28.something. Check into this.

---

### Post by presence1960 on 2009-12-07
> **ezsit said:**
> This kernel is from Intrepid, a.k.a. 8.10. Ubuntu 8.10 is two versions behind the current 9.10. Are you sure that is the kernel you are trying to boot into?

If so, this explains a lot of problems. Ubuntu 9.10 should be running kernel 2.6.31.something and Ubuntu 9.04 should be running 2.6.28.something. Check into this.

+1 Right on. I have noticed in a lot uf upgrades to 9.10 threads that the kernels from the old version are still booting.

---

### Post by John.St on 2009-12-07
> **howefield said:**
> Back up your files/data ect and reinstall from scratch. Only realistic way to do it.How do I backup from a HD on a computer that doesn't finish booting?

---

### Post by John.St on 2009-12-07
> **wilee-nilee said:**
> In the recovery are you using your login name then password.I am asked for the root password only and I seem to have some 0.5 seconds to type it before the process continues.

---

### Post by John.St on 2009-12-07
> **ezsit said:**
> This kernel is from Intrepid, a.k.a. 8.10. Ubuntu 8.10 is two versions behind the current 9.10. Are you sure that is the kernel you are trying to boot into?

If so, this explains a lot of problems. Ubuntu 9.10 should be running kernel 2.6.31.something and Ubuntu 9.04 should be running 2.6.28.something. Check into this.This is what grub says, but it also showed 8.10 while I was successfully running 9.04 for months - it's obviously text only.

Thus I have no idea which kernel it actually tries to load.

---

### Post by howefield on 2009-12-07
> **John.St said:**
> How do I backup from a HD on a computer that doesn't finish booting?

Use a live cd to access the disk. It isn't hard.

---

### Post by JBAlaska on 2009-12-07
And it would seem that installing the latest kernel may solve your problem, although a clean install is always a better choice.
 To mount your Linux partition from the Live cd:
1-boot the LiveCD
2-open the terminal and do:
```
sudo fdisk -l
```

3-examine the output and determine your Linux partition (example sdax where x is the Linux partition)
4-create a mountpoint for your partition:
```
mkdir /media/root
```
5-mount your partition in it:
```
mount /dev/sdax /media/root
``` (again replace x with your partition number)

6-do:
```
ls /media/root
``` That should list your directories, now you can copy your /home and packages as in my above post to another partition or a USB thumb drive, or other removable media.

---

### Post by presence1960 on 2009-12-07
> **John.St said:**
> How do I backup from a HD on a computer that doesn't finish booting?

Download backtrack linux and burn it to CD. Get it [here]("http://www.remote-exploit.org/backtrack.html"). boot off CD. Always saves me when clients using windows bring me an unbootable machine.

---

### Post by John.St on 2009-12-08
This is how I solved my problem:

I succeeded in booting from an old 8.04 memory USB stick, mounted my /dev/sda6 containing ubuntu 9.10 and in /boot I found both the old u8.10 2.6.27-11 kernel etc. and a full set of u9.10 2.6.31-16 stuff.

Copied everything, deleted the 2.6.27-11 and renamed all 2.6.31-16 **copies** to 2.6.27-11

Everything honky-dory except the icons on my desktop were moved around and a few icons in the menu bars were corrupted.

Grub still says 8.10 and 2.6.27-11 but that's just a minor annoyance.

Now I have a working ubuntu 9.10. :popcorn:

One last question: Somehow I can **mark this thread as solved**, but I've forgotten how?

---

### Post by jwmeyer on 2010-01-31
Don't know if you ever solved this but the problem is that the upgrader writes the grub menu.lst to the wrong HD. The clue was the wrong kernel. I opened the menu.lst file from the HD that the upgrade was done and copied the 9.1 lines and pasted them into the menu.lst that had the bogus 8.1 line. The boot then worked properly.

---

