---
title: "Grub does not install"
date: 2007-01-28
forum: Installation &amp; Upgrades
---

### Post by Mr Smith on 2007-01-28
Hi Everyone!
     I have this problem when I try to install Ubunty 6.10 on my laptop. Now, my laptop has a 20 Gb h-disk, and dual boots windows and Mandrakelinux 2005. In Ubuntu installation, I go with the default settings for the grub (install to 'hd0'). When the installation gets to GRUB, it says it cannot install to hd0, fatal error. And that's it. I have installed Ubuntu onto the exactly the same partitions as Mandrake was installed. Also, the Mandrake GRUB is still there, it loads my Windows fine, but no linux (neither Mandrake, i guess it was overwritten, nor Ubuntu). Here are the settings if anything would be of any help -

1. Mandrake installed its GRUB file or whatever on 'First Section of Disk (MBR)'. That's exactly how it said at the installation.

3. Running the fdisk-| command returns ' > '. And nothing more. Tried fdisk /dev/hda/ and Ubuntu says the disk can't be openned.

4. My hard disk layout looks like this from gnome partition manager (from Ubuntu liveCD) - 
/dev/hda1                               -fat32         (this is my Windows partition)
/dev/hda2                               -extended
=>      /dev/hda5                   -ext3          (my ' /  'mount point in Mandrake and Ubuntu)
           /dev/hda6                    - linux -swap
           /dev/hda7                    -ext3          (my ' /home ' mount point in Mandrake and Ubuntu)

The entire hard disk is called /dev/hda

5. So what is the 'First section of Disk (MBR)' here? Maybe if I knew I could try to install the Ubuntu GRUB file into it. Since the error comes up after all the files have been istalled, maybe I could edit the mandrake grub somehow from windows or something to specify the path to Ubuntu so that it would load.
                          
                              Thank you.

---

### Post by confused57 on 2007-01-28
> **Mr Smith said:**
> Hi Everyone!
     I have this problem when I try to install Ubunty 6.10 on my laptop. Now, my laptop has a 20 Gb h-disk, and dual boots windows and Mandrakelinux 2005. In Ubuntu installation, I go with the default settings for the grub (install to 'hd0'). When the installation gets to GRUB, it says it cannot install to hd0, fatal error. And that's it. I have installed Ubuntu onto the exactly the same partitions as Mandrake was installed. Also, the Mandrake GRUB is still there, it loads my Windows fine, but no linux (neither Mandrake, i guess it was overwritten, nor Ubuntu). Here are the settings if anything would be of any help -

1. Mandrake installed its GRUB file or whatever on 'First Section of Disk (MBR)'. That's exactly how it said at the installation.

3. Running the fdisk-| command returns ' > '. And nothing more. Tried fdisk /dev/hda/ and Ubuntu says the disk can't be openned.

4. My hard disk layout looks like this from gnome partition manager (from Ubuntu liveCD) - 
/dev/hda1                               -fat32         (this is my Windows partition)
/dev/hda2                               -extended
=>      /dev/hda5                   -ext3          (my ' /  'mount point in Mandrake and Ubuntu)
           /dev/hda6                    - linux -swap
           /dev/hda7                    -ext3          (my ' /home ' mount point in Mandrake and Ubuntu)

The entire hard disk is called /dev/hda

5. So what is the 'First section of Disk (MBR)' here? Maybe if I knew I could try to install the Ubuntu GRUB file into it. Since the error comes up after all the files have been istalled, maybe I could edit the mandrake grub somehow from windows or something to specify the path to Ubuntu so that it would load.
                          
                              Thank you.

The command you want is:
```
sudo fdisk -l
```
The -l is a small "L"

The command you did, fdisk-|,  was asking for more input(>), since your last symbol in the command was the pipe symbol(|)...pressing ctrl+c will get you back to a terminal prompt.

You might want to try to reinstall grub using the live cd:
[http://www.ubuntuforums.org/showthread.php?t=224351](http://www.ubuntuforums.org/showthread.php?t=224351)

If you're still booting Windows from the Mandrake grub, it appears Ubuntu wasn't installed...you can't install Mandrake & Ubuntu root onto the same partition.  You'd need to select to format the partition that you're going to install Ubuntu on to overwrite Mandrake and install Ubuntu.

This link explains grub & mbr:
[http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)

Here's an excellent link that might help:
[http://www.psychocats.net/ubuntu/index.php](http://www.psychocats.net/ubuntu/index.php)

---

### Post by Mr Smith on 2007-01-29
Hello!
         Thanks a lot for your help. I have solved the problem, and Ubuntu has installed fine. Excellent links. Thank you.

---

