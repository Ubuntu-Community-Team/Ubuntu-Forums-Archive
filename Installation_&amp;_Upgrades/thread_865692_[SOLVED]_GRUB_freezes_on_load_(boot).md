---
title: "[SOLVED] GRUB freezes on load (boot)"
date: 2008-07-20
forum: Installation &amp; Upgrades
---

### Post by fowie on 2008-07-20
I re-imaged my hard drive from a backup copy.  Now when I try to boot I get the usual POST, then the screen goes blank, and prints out
```

GRUB

```
and freezes there (i.e. GRUB doesn't finish loading).  I put in a live CD, booted from it and selected "Boot from first hard disk" and the computer loads just fine (boots up GRUB, boots into Ubuntu, no problems).  What's going on and how do I fix this?

---

### Post by Wazoot on 2008-07-20
hmm...
maybe something messed up during your installation?
try reinstalling a clean version us Ubuntu, or try and reintall GRUB.

---

### Post by warp99 on 2008-07-20
> **fowie said:**
> I re-imaged my hard drive from a backup copy.  Now when I try to boot I get the usual POST, then the screen goes blank, and prints out
```

GRUB

```
and freezes there (i.e. GRUB doesn't finish loading).  I put in a live CD, booted from it and selected "Boot from first hard disk" and the computer loads just fine (boots up GRUB, boots into Ubuntu, no problems).  What's going on and how do I fix this?

Check the UUID of the partition you restored in /etc/fstab and /boot/grub/menu.lst. To do this boot to the LiveCD open a terminal and issue the following:

```
sudo vol_id -u /dev/<system_name_of_partition>
```

Make sure they all match. If not replace the ones in fstab and menu.lst. You also need to reinstall your Grub bootloader since it appears to have been overwritten. Here is a guide on reinstalling Grub using the Ubuntu LiveCD:

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows?highlight=(grub)|(reinstall)#Quick%20Start](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows?highlight=(grub)|(reinstall)#Quick%20Start)

---

### Post by upchucky on 2008-07-20
your install is fine, grup needs to be told where the mbr is now, search the hundreds of posts here look for ones that say grub solved, you fix is very simple, if you cant find the answer post your drive specs here

```
sudo fdisk-l
```

to edit grub file, ```
sudo gedit /boot/grub/menu.lst
```
instead of gedit if gnome is not running then use nano as the editor.

fix mbr, ```
sudo grub
```
find stage 1, ```
find /boot/grub/stage1
```

to set root, ```
root (hdo)[CODE] or what ever find says stage 1 is on.

if the find found stage 1 on hd0 then do this
setup root drive mbr, [CODE]setup (hd0)
``` the brackets are part of the code, and you must substitute the hdo with what ever it says the stage is found on.

the above may have to be done from a live cd if you cant get the commandline or ubuntu to boot.

---

### Post by fowie on 2008-07-21
Thanks, I was pretty sure I didn't need to do a reinstall since I *can* boot into the OS if I select "boot from first hard disk".  I got into grub and the search told me
```

(hd0,0)

```
so I did 
```

root (hd0)

```
but
```

grub> setup (hd0)

```
tells me:
```

Error 17: Cannot mount selected partition

```

Guess that means I'll have to do it from a live CD?

As for editing menu.lst and fstab, since I'm on dapper, fstab is still the old style that uses /dev/hdx descriptors, instead of the UUID form.  I'll update that in fstab, but I'm not sure where in menu.lst it would show up unless you mean just the ko= option line, and that one is using the correct UUID.

---

### Post by warp99 on 2008-07-22
> **fowie said:**
> ... I'm not sure where in menu.lst it would show up unless you mean just the ko= option line, and that one is using the correct UUID.

That's correct in the kopt line since the UUID is placed their so with any future kernel updates the string is automatically appended to the /boot kernel line. You see those single number signs (#) in that section of the menu are not comments, but options and are used by Grub during updates. If you have any special parameters attached to your kernel /boot line in grub you can also add them.

Edit:

Use the LiveCD and follow the guide in my previous post.

---

### Post by fowie on 2008-07-24
I re-did the lines posted above and setup(hd0) worked.  Haven't had a chance to reboot and test it yet though.

---

