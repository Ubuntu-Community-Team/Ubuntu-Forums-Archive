---
title: "Moving Wubi 10.04 install to another Windows partition"
date: 2010-12-08
forum: Installation &amp; Upgrades
---

### Post by druglord187 on 2010-12-08
Hello Ubuntu community,

First of all, I'll let you know I'm pretty new to this community, so I apologize if I missed some forum etiquette.

I have a Wubi install of 10.04 in my C: partition. I had given it 20GB of space but over the months my C: has become almost full, so I need to move the Wubi install to another partition (say E:). I looked around for instructions on how to do it, but I could only find instructions for grub-legacy (that ask you to modify C:/ubuntu/disks/boot/grub/menu.lst) and not grub2 (which doesn't have menu.lst) used by 10.04.

So, any help on how to move a 10.04 Wubi install to another partition in Windows is appreciated. Kindly note that I'm not trying to remove Wubi and convert it to an actual installation, but rather simply move it to a different location in Windows.

Thank you and have a nice day!

---

### Post by Megaptera on 2010-12-09
I found this answer "Wubi is installed in C; Drive of windows as a folder using grub4dos as boot and the host being windows in file system."

Here:[http://ubuntuforums.org/showthread.php?t=1579629](http://ubuntuforums.org/showthread.php?t=1579629)

So unless anyone knows different, I think it needs to stay on 'C'. Unless you're OK to go for a dual boot installation, which is not as tricky as some might think.

---

### Post by bcbc on 2010-12-09
It's possible to do it. For this you need to know what physical partition drive C: and drive E: are on. In this example I'll assume drive C: is /dev/sda2 or (hd0,2) and drive E: is /dev/sda5 or (hd0,5)

1. Copy all the .disk files e.g. c:\ubuntu\disks\root.disk outside of the c:\ubuntu folder (important that it's outside the ubuntu as this gets deleted in step 2.)
2. Uninstall Wubi
3. Reinstall Wubi on drive E: (just the windows part)
4. When it prompts you to reboot, copy over the .disk files to the new install (into e:\ubuntu\disks\)
5. Reboot.
6. Select Ubuntu. When you see the grub menu, press 'e' on the first entry.
Change (hd0,2) to (hd0,5). Change /dev/sda2 to /dev/sda5 (modifiy for your own partitions). Also delete the line that starts "search --..."
7. CTRL+X to boot.
8. Once booted, go to terminal, CTRL+ALT+t, run "sudo update-grub".

That's about it.

PS avoid updating packages grub-pc and grub-common - you don't need to and they tend to break Wubi installs.

---

### Post by druglord187 on 2010-12-09
Thanks for the reply.

I did exactly what you told but at step no. 6, after choosing "Ubuntu" I don't get the grub menu. Instead it just proceeds to install Ubuntu (no idea where it was installing)! Probably something went wrong in the copying, so I'm now re-doing the steps once again. I'll come back soon.

---

### Post by Megaptera on 2010-12-09
> **bcbc said:**
> It's possible to do it.

Thanks, I'm pleased it is possible!

---

### Post by druglord187 on 2010-12-09
Ok, I have tried this multiple times but what happens is when I choose "Ubuntu" after rebooting it just continues to format the entire "partition" (i.e, root.disk) and installs a fresh copy in it. Removing that from Windows and copying the old root.disk again does not work. When I restart and choose "Ubuntu" it shows some kind of terminal (grub terminal, I believe?) instead of the grub menu.

So basically I'm stuck with a freshly installed root.disk and an old root.disk which I'm trying to boot. Any help?

---

### Post by bcbc on 2010-12-09
> **druglord187 said:**
> Ok, I have tried this multiple times but what happens is when I choose "Ubuntu" after rebooting it just continues to format the entire "partition" (i.e, root.disk) and installs a fresh copy in it. Removing that from Windows and copying the old root.disk again does not work. When I restart and choose "Ubuntu" it shows some kind of terminal (grub terminal, I believe?) instead of the grub menu.

So basically I'm stuck with a freshly installed root.disk and an old root.disk which I'm trying to boot. Any help?
OK... that's worked for me before - maybe they've modified the initial boot files. So just don't copy your *.disk files until after the second installation is completed. Then copy them over after that and pick it up with the rest of the instructions.

---

### Post by Horza on 2011-01-02
Doesn't work for me (from using updated 10.04.1): grub2 can't find the copied root.disk even tho it's sitting right there.

---

### Post by bcbc on 2011-01-03
This is how many people back up their wubi installs. Copy the root.disk, then copy it back over if they want to revert to the backup.

If it's not able to read the root.disk you may get a grub prompt. In that case I'd recommend running fsck on it. The [wubi guide]("https://wiki.ubuntu.com/WubiGuide#How can I access my Wubi install and repair my install if it won't boot?") shows how to do this. Also confirm that you can loop mount and view your files on the root.disk - you can do this after booting a live CD. If you can do this, then there's no reason that you shouldn't be able to get it to boot that I can think of.

So check out your root.disk and then post back if you have any issues. If not, I'll run a test on 10.04.1 - but it's always worked for me and I've done it a lot (including moving root.disk's between computers, and different drives).

Edit: by the way, there's a wubi + grub issue at the moment on 10.04.1 Make sure you don't have this problem because moving the root.disk to a 'new install' won't fix that. See the [wubi megathread]("http://ubuntuforums.org/showthread.php?t=1639198") (Problem #2) for more info.

---

