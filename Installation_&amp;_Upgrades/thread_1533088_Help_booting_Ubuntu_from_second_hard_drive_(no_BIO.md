---
title: "Help booting Ubuntu from second hard drive (no BIOS option)"
date: 2010-07-17
forum: Installation &amp; Upgrades
---

### Post by d3mncln3r on 2010-07-17
I have a Sony VAIO AR series, it contains two separate 120GB hard drives that were originally configured in a raid. They're called hd0, and hd1. 

I disabled the raid and partitioned hd1 in 3 ways, one medium sized partition for the operating system (ext4), one large partition for storage (ext4) and one small partition for Swap space. I then installed Ubuntu onto hd1 with help from UNetbootin.

After installation went fine I loaded up Windows installer, created two NTFS partitions, one medium and one large, and installed Windows 7 of the medium sized partition.

Now I can't figure out how to boot into the Ubuntu side on hd1. Needless to say, in Windows, hd1 is not visable at all. I can see my two NTFS partitions fine.

When booting up I go through two main screens. The first screen "Matrix Storage Manager Option ROM," lists the physical disks (0, and 1.) and gives me the option to enter configuration with [cntrl+i].

The second screen gives me a list of options to boot from, Yet they are all Windows options and many are redundant. The list includes "Enter Command Line," which when selected tells me "Boot failed! Press any key to enter command line."

command line brings me to "grub>"

I tried booting Ubuntu from this command line, but don't have much to work with here. I followed this guide, but it didn't take me to completion and I'm not sure where to go from here. [http://www.mepis.org/docs/en/index.php/GRUB_from_command_line]("http://www.mepis.org/docs/en/index.php/GRUB_from_command_line")

Sorry for the long post, hope someone can help!


UPDATE:

Just followed this guide for recovering ubuntu after installing windows: [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows")

As per thread instructions, I reinstalled GRUB on Sda (that may have been a mistake, since my Ubunto OS is on Sdb1.) Upon reboot, now my PC loads directly into Ubuntu! LOL it seems my hard drives will not play well with one another. I need to find a way to choose which OS (or which HD) I want to load into upon start up.

UPDATE 2: FWIW I am fine with overhauling the system another time and trying to do a better job of dual booting. I installed both Operating Systems from a USB stick so it doesn't take all that long. I think it's just a matter of doing it right the first time, and I think I may have screwed something up

---

### Post by oldfred on 2010-07-17
Grub should also give you a choice to boot windows.

try this if it is not already shown in your menu from terminal:
sudo update-grub

If that does not work from Ubuntu or liveCD:

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the post's menu and then paste the contents between the generated ```

``` tags.

---

### Post by ajgreeny on 2010-07-17
The "sudo update-grub" should do the trick.  There should be no need to reinstall either OS.

Your problem is that you installed Ubuntu first and therefore it knew nothing about windows even existing on your computer.  Then when you installed windows it put the windows bootloader on to the MBR of sda, but that does not detect linux so you have a sort of stalemate.

Anyway, having got grub back and being now able to boot to ubuntu, that command from oldfred should find windows and add it to the grub menu, giving you the option at boot time to go to either OS.

---

### Post by d3mncln3r on 2010-07-17
Excellent fellas! Thank you I now have a functioning dual boot system, thanks again!

---

