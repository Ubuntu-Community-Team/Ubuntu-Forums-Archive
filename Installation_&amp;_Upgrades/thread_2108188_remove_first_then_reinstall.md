---
title: "remove first then reinstall?"
date: 2013-01-24
forum: Installation &amp; Upgrades
---

### Post by nervynewman on 2013-01-24
I added ubuntu 12.1 to a partition on a hdd with some windows 7 programs and media(but not the OS) a few days ago without thinking ahead. I'd like to have ubuntu on a partition on a ssd instead and still keep a grub2 dual-boot. Will it be easier and safer to uninstall it from the hdd using the windows 7 installation disc or ubuntu cd? Then do I still need to remove/reformat the partition from inside windows before a reinstall, or will the uninstallation take care of that?

The computer has a ssd with windows 7, another ssd with with ms office and a few games(this is where ubuntu will go), and the hdd.  Windows is backed up and imaged.

---

### Post by grahammechanical on 2013-01-24
You need to think out these steps clearly otherwise you will not be able to boot Windows 7.

By installing Ubuntu you put the Grub boot loader in charge of the Boot process. Is this not correct? So if you delete the partition with Ubuntu on it you will break the Grub boot loader becasue it will look for its configuration files in Ubuntu which has been removed.

You need to get Windows 7 back in control of the boot process and then use Windows 7 utilities to remove the partition with Ubuntu on it and expand the Windows partition to take up unused space.

You might want to look at Ubuntu Secure Remix. It runs as a live session and it has a utility called OS-Uninstaller. That may uninstall Ubuntu for you.

[https://help.ubuntu.com/community/UbuntuSecureRemix]("https://help.ubuntu.com/community/UbuntuSecureRemix")

Then you need to install Ubuntu on to the SSD that you want it on. Make sure that you do not mess up Windows 7.

Regards.

---

### Post by nervynewman on 2013-01-25
Thank you

This is exactly what I did, and windows 7 booted on its own until I deleted the partition that had ubuntu on it, but now it boots to a "grub rescue>" command.

Commands from the windows recovery cd system prompt such as "bootrec /fixmbr", "bootrec /fixboot", or "bootrec /rebuildbcd" do not help. Even the command "bootsect /nt60 c:\" from the boot directory loads a boot sector restoration tool, but again does not seem to switch back and remove GRUB.
 
If reinstalling ubuntu on the other ssd will fix this, then I'll gladly do it, however the ssd has only the single ntfs partition with windows software.  Can I add another partition for the ubuntu installation during setup or with GParted without deleting the drives windows software?

---

### Post by nervynewman on 2013-01-25
Please disregard the last post; Ubuntu is on its own partition.

Now the first boot device has to be the drive with Ubuntu installed on it in order to load the GRUB menu.  Originally, it was the one with Windows 7, but it still boots to say "grub rescue".  Windows and Ubuntu now load as they should but is this common?  

In the GRUB menu there's also two Windows 7 choices that both work, and in the GParted program, two "windows loader" partitions exist as well.

Even though everything works now, can I correct this so I can stop worrying and feel a little more competent?

Thanks in advance

---

### Post by Bucky Ball on 2013-01-25
Boot from a LiveCD, kill the Ubuntu partition, install Ubuntu on the SSD. This will also reinstall grub on sda and overwrite the existing grub there. Easy.

Ubuntu can be on any partition, even a logical inside an extended partition. It doesn't  need to be first. No diff anyhow; grub is installed at the beginning of the first drive, sda.

---

### Post by furything on 2013-01-25
Ignoring the ubuntu side and grub.

If you want to get windows 7 booting try your repair options from bios. Nowadays windows has a recovery partition rather than a separate disk.

You can use the auto repair to try and fix or there is a cmd line type
```
FixMBR
```If you have a windows recovery disk then follow on screen instructions and say at first menu prompt recover windows. This will probably dump down to the cmd window. Again enter the command above. (I have and use a genuine disk and so this is the option I see.)

Once windows is again bootable (as already suggested above) plan where you want your installs e.g. to what disk and partition. **Note for windows back up to work and be successful** it has to be sda partition 2 (part 1 is normally 100mb recovery partition) drive so bare that in mind when choosing your partitions

---

### Post by nervynewman on 2013-01-25
Windows 7 is on sda1

Ubuntu is now on sdd2

sdd1 and sdb1 are solid-state drives with misc windows apps and media files.

sdc1 is a hdd that previously had Ubuntu on a second partition(sdc2) that is now deleted, but the drive still shows up on the grub menu as a "Windows 7 (loader  /dev/sdc1)".  This drive has even more windows apps like ms office that I still want for now.

It all works for now and I'll keep reading and learning until I figure it all out and it isn't as much fun, but I still don't know if grub is on sdd or sda.

---

### Post by Bucky Ball on 2013-01-25
Where did you install it? Should be at the beginning of sda by default unless you manually put it somewhere else during install. Do a search for bootinfoscript, run it and have a look. That will tell you where grub is if you're not sure.

---

### Post by nervynewman on 2013-01-25
I downloaded  bootinfoscript yesterday, but the terminal prompt says command not  found.   
```
sudo ~/Downloads/bootinfoscript
```I reinstalled Ubuntu on sdd using the install alongside another os option instead of the something else option that I used the first time when I already had another partition ready to format. 

grub still loads windows 7 from sda but only if sdd where ubuntu is loads from bios first.   I'll load it from the cd  later, but I'd love to hear an opinion about all this first.  Should I repost this in the absolute beginners section?

---

### Post by Bucky Ball on 2013-01-25
> **nervynewman said:**
>   Should I repost this in the absolute beginners section?

No. Post a new thread in this section as it has to do with installation if you think your problem is now different enough to warrant it or you have a new question which does not fit under the current thread description.

---

