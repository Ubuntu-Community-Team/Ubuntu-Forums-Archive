---
title: "GRUB disappears not after windows installation, but after windows boot"
date: 2009-11-26
forum: Installation &amp; Upgrades
---

### Post by matthewhaworth on 2009-11-26
Hello,

I have just installed 9.10 alongside Windows XP, the installation was successful and everything was fluent.  I then booted into linux shut down shortly afterwards.. I then booted up windows, and shut that down.  This was to check that they were both working properly.  
However, when I booted again, I didn't get a boot menu and the system automatically booted into Windows, so I don't understand where grub has gone!

This has actually happened before and in trying to fix it I made a mess of my partitions and decided to format everything freshly.  
I tried booting Ubuntu 'live' and then using grub with:

```

find /boot/dev/stage1
root (hdx, y)
setup (hdx, y)
boot

```

(Should I try this again?)

etc, but that didn't work!  And I have a feeling even if I did get grub to come back then windows or whatever would erase it again.

Does anybody have any idea about what is actually happening here?

---

### Post by darkod on 2009-11-26
I don't know if and why windows is deleting grub, but the command find you executed didn't find anything because it looks as part of grub while 9.10 uses grub2.

In case you want to reinstall grub2, boot with the ubuntu cd, select Try Ubuntu option and in terminal execute:

```
sudo -i
mount /dev/sda7 /mnt
mount /dev/sda6 /mnt/boot (only if you have separate /boot partition)
grub-install --root-directory=/mnt/ /dev/sda
```

Replace the sda7 and sda6 with your root and /boot partition numbers, if you have separate /boot. If not just skip that line. See if that helps and whether grub2 will stay there.

---

### Post by matthewhaworth on 2009-11-26
You were certainly right about me using the wrong grub, thank you!

However, after doing this I rebooted and got the menu, great :), but then I booted into windows and shut down again.  Now I find myself in a prompt called 'grub rescue'?  I don't really know what's happening or why Windows is doing something so strange on this machine.

Any ideas?

Thank you.

---

### Post by ecarcole on 2009-12-02
I am having the same problem here.

I changed the flag "boot" with gparted from my windows partition to my Ubuntu partition but it did not work at all.

I need to work with both OS.

This problem has been already reported as a bug:

[https://bugs.launchpad.net/grub/+bug/26058](https://bugs.launchpad.net/grub/+bug/26058)

If somebody knows a solution please help!!!!!

---

### Post by oldfred on 2009-12-03
ecarcole - The bug you posted to was for grub legacy, and grub2 is not related. Their is a known bug for some HP and Dell computers that write some data into the MBR that corrupts grub2 since it is larger than old grub and the windows MBR. 

HP ProtectTools and Dell Recovery Tool write into MBR
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/441941](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/441941)
Dell Media direct issues with MBR
[http://ubuntuforums.org/showthread.php?t=923576](http://ubuntuforums.org/showthread.php?t=923576)

Ubuntu does not use the boot flag but windows does, keep the boot flag on the windows partition you want to boot windows from. If you have multiple installs of windows the flag is on the one copy that has the boot for both and lets you choose which windows to boot.

---

### Post by ecarcole on 2009-12-04
Thank you so much oldfred!!!!
I have an HP....

---

### Post by oldfred on 2009-12-04
I saw this user who pointed out a program that is causing the problem.

[http://ubuntuforums.org/showthread.php?t=1344828](http://ubuntuforums.org/showthread.php?t=1344828)
Found out today after numerous searches the issue. I found the answer here -- I had heard dynamic disk partioning may be the cause (which I don't have) or virus software (which I removed). I have a Compaq netbook -- HP product. Turns out they have HP Recovery tools that will overwrite parts of the MBR. The thing is, I uninstalled every single piece of their recovery software, sync software, etc, cuz I didn't want any of that crap. I went into services, and lo-and -behold -- there was the hpqwmiex service running. So I disabled it, did the update-grub thing again, logged into Windows then back into Ubuntu, and all is well!

---

### Post by phillw on 2009-12-04
I have this thread as a bookmark --> [http://ubuntuforums.org/showthread.php?p=8433673](http://ubuntuforums.org/showthread.php?p=8433673)

We had our rant on there, as well ;-)

Phill.

---

### Post by efflandt on 2009-12-04
Many computers including HP have a recovery partition, and in the case of HP, if you boot to that instead of the grub Windows menu entry that includes (loader), HP Recovery tends to replace the mbr with standard Windows mbr and mark the Windows partition as bootable.

In my case, I had actually put grub2 on a primary partition instead of the mbr.  So all I had to do after I made the mistake of booting HP Recovery was to use Linux fdisk (or gparted) from install CD or bootable USB stick to change the boot partition back to the one containing grub2.

---

