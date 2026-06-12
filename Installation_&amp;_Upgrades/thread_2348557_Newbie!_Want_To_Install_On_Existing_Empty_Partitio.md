---
title: "Newbie! Want To Install On Existing Empty Partition Without Deleting Other Partition"
date: 2017-01-04
forum: Installation &amp; Upgrades
---

### Post by go7hic13 on 2017-01-04
Hi All...

I'm new to Ubuntu and have a question regarding installation of the OS.

I have a Windows 10 Laptop which has:
 1. a 256gb SSD
 2. 1TB 7200 RPM HDD.

I currently have the 1TB HDD partition into a 60/40 split and have Windows 10 Apps and Data on the First Partition of the drive.  I would like to install Ubuntu (Any recommended version for web development) onto the existing (but empty) 2nd partition on the same drive WITHOUT destroying or losing the first partition on the 1TB HDD (E:Windows & G:(Soon to be Ubuntu) according to windows 10).

I know others have posted similar questions yet I'm a bit confused and don't want to lose any data on the existing first partition.  I would like to install Ubuntu on to the 2nd Partition on the 1TB drive without overwriting or repartitioning the drive.

Can someone break down the steps into the simplest form to get this done.  I've tried but the menu options are VERY unclear as to what is going to happen to the first partition and don't want to lose the data.  I don't want to reformat or repartition the drive.  I would like to just install Ubuntu onto the 2nd partition (40%) of the 1TB drive.

If you need additional information please let me know and I can provide it regarding my laptop.

Also, I would like to be able run things like php and other web environments for web development and a recommended flavor of Ubuntu would be welcomed.

Thanks in advance!

---

### Post by TheFu on 2017-01-05
a) Make a backup of anything you cannot afford to lose BEFORE starting. If you can't/won't do this, you accept the risks of total data loss. AND test the restore. I can't be clearer. 

b) "other web environments" is extremely vague. There are hundreds of those, each with very different requirements.

c) If your computer has enough power and RAM, perhaps using a virtual machine would be a better choice?  It removes the risks involved with partitioning.  I ran for a few years inside a VM before wiping Windows and loading Linux as my primary OS. Now, Windows runs in a VM and only gets used for about 5 specific things a few times weekly. Everything else, including webapp development, is done inside Linux, usually on a remote system. Remote can be 6 inches or 12K miles. For the way I work, it doesn't matter.

d) BTW - if you are really worried, you can get a $50 raspberry Pi and use that system as a web-app development machine. The r-pi v3 has plenty of power for this stuff - especially for perl, python, ruby, and php webapps.  Or build a $120 "server" based on a relatively powerful, but cheap, Intel G3258 CPU.

With Linux, "the network is the computer" - hard to explain this to people coming from a desktop-only background.  Right now, my chromebook (running Ubuntu) has 10 windows open in the current "workspace".
[LIST=1]
[*]Firefox
[*]Thunderbird
[*]alarm-clock
[*]xterm (local)
[*]xterm (local)
[*]xterm (video processing system)
[*]xterm (video storage system)
[*]xterm (main desktop running inside a VM in a "private cloud")
[*]xterm (main backup/storage server)
[/LIST]
I have 3 workspaces (basically virtual desktops). Each is used for different purposes. Not doing web-app development today, sorry. 

Any chance I can convince you NOT to do php?  Billions of people do php already, so pay for that skill isn't as good as for some other web-app languages.  Php at the non-expert level has other issues too.

Finally, if you are determined to dual boot, please post the data from the **boot-info** script. My signature has links.

---

### Post by SeijiSensei on 2017-01-05
During installation you will be asked how to set up the disk. Choose "manual" or whatever that option is called today and you can tell the installer to use the empty partition.

---

### Post by TheFu on 2017-01-05
I vaguely recall on the storage page, "Do something else" as the option.
BTW, normally people setup a swap partition, so having 2 free partitions would be helpful.

With that info, we can guide you on sizing for each. The old 2x RAM for swap is wrong.

---

