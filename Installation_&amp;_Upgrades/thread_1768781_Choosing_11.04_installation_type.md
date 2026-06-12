---
title: "Choosing 11.04 installation type"
date: 2011-05-27
forum: Installation &amp; Upgrades
---

### Post by Tornikee on 2011-05-27
Hello.

I currently have Windows 7/Ubuntu 11.04 dual boot, and have decided to get rid of Windows. So I booted up the Ubuntu installation CD which gives the following options on install:

[IMG]http://i.imgur.com/Mv3TP.jpg[/IMG]

So my question is: will my personal files (which I have on partition 'D:', separate from the Windows installation partition) be erased with this option?

Thanks in advance.

---

### Post by 3xp10r3r|X13 on 2011-05-27
well if it says "erase everything" it does really mean it.

--> the thing you should be doing is basically booting into ubuntu and formating the partitions windows is installed on. That will give you more free space available. If you want to make this free space accessable in your os left, you have to extend your ubuntu partitions.

any questions?

PS: hope this helped :)

---

### Post by Tornikee on 2011-05-27
Thank you for the reply. I did first go to 'edit partitions' stuff of this  installation, although was a bit confused with partitions and their types listed there, as I'm new to Ubuntu, so I thought I'd just erase both OSs and install a fresh Ubuntu, and I hoped my personal files wouldn't be touched as they were on the partition that no OS was installed on.

I will enter that section again and post what is there that I don't understand.

---

### Post by Tornikee on 2011-05-27
OK so I got into this partition menu and assumed the NTFS partitions were the Windows ones, so deleted the first one (which, according to its size, is 'C:', where Windows is actually installed):

[IMG]http://i.imgur.com/ycsj2.jpg[/IMG]

Then I tried creating a new partition in its place, but after clicking 'Install' there was an error message saying I needed to select partition type. I guess it's in this menu?:

[IMG]http://i.imgur.com/3rVgm.jpg[/IMG]

Which format should I select here?

And finally, will I also need to format the other NTFS partition in Ubuntu format as well, in order to be able to use it normally in Ubuntu?


Appreciate your help.

---

### Post by mörgæs on 2011-05-27
If you will only have Ubuntu on the computer, I would recommend only using ext3 or 4. There is no advantage in NTFS, only trouble. 

The best approach is simply to back up all user files and do a fresh install using the entire drive.

---

### Post by Tornikee on 2011-05-27
Thanks for the information.

---

