---
title: "Removing a Linux partition from a multiboot system"
date: 2014-09-18
forum: Installation &amp; Upgrades
---

### Post by archp2009 on 2014-09-18
I read the following post [http://ubuntuforums.org/showthread.php?t=1465896](http://ubuntuforums.org/showthread.php?t=1465896) and noted Oldfred's comment about not deleting a partition that controls the MBR.  I have more OS's than I can immediately remember 5 Windows and 9 or 10 Linux I think.  I didn't realize that Old distro's; for example, Mint 15 and Mint 16 are no longer secure because they don't even update the Firefox browser.  I seem to recall that I began by installing Mint 16 after the final Windows, so it is possible that Mint 16 controls the MBR.  I wanted to delete 15 and 16 and somehow use the 30-40 gb of space to increase the free space for some other volumes.  How do I figure out what partition controls the MBR and how to safely delete that one?  In time I will likely delete other Linux partitions because they are mostly Ubuntu derivatives and essentially the same but I am in no immediate need for space.

---

### Post by grahammechanical on 2014-09-18
I do not advise on Linux Mint. I suggest that you decide which version of Ubuntu you want to keep. Then load into it and run

```
sudo update-grub
```

If this version of Ubuntu is on sda then run

```
sudo grub-install /dev/sda
```

It Ubuntu is on sdb or sdc then change the command accordingly. That will put the Grub of Ubuntu in charge of the boot menu. Every time you remove an OS/distribution run sudo update-grub again to reconfigure the boot menu. Or download and create a Linux Secure Remix live disk. It has an application called OS-Uninstaller. I have never used it myself. But there you go.

Running update-grub will produce a printout showing all the OS and the partitions they are on. Take things from there.

[https://help.ubuntu.com/community/LinuxSecureRemix](https://help.ubuntu.com/community/LinuxSecureRemix)

Regards.

---

### Post by yancek on 2014-09-18
Boot any of the Linux installs and go to the site below and read the instructions, download and run the bootinfoscript.  It will output a resultx.txt file and at the top of the file it will tell you which partition has Grub in the mbr.  Should do the same for any drive on which you have Grub in the mbr.

[http://sourceforge.net/projects/bootinfoscript/](http://sourceforge.net/projects/bootinfoscript/)

---

### Post by oldfred on 2014-09-18
Bootinfoscript has not been maintained well in the last year or so. With grub2 2.00 it does not correctly show the partition grub uses to boot from in MBR.

This site has a minor change that fixes it so you can directly tell which partition the MBR uses.
[https://github.com/arvidjaar/bootinfoscript](https://github.com/arvidjaar/bootinfoscript)

I just downloaded the .zip version in lower right corner and extracted that.

---

