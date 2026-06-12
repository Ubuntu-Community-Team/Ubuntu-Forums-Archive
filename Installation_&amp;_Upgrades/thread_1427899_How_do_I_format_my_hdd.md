---
title: "How do I format my hdd ?"
date: 2010-03-12
forum: Installation &amp; Upgrades
---

### Post by Nailox on 2010-03-12
Hi. I need to remove my ubuntu and install Win7. When I boot from the Win7 dvd it says it cannot proceed the installation because the partition must be in NTFS format and this partitoion is unrecognized format. I cant see an option to format the hdd. I need to format it completely and then install Win7. tyia

---

### Post by dusdus on 2010-03-12
too bad you want to remove ubuntu!

To format your harddisk, boot your ubuntu LiveCD and start the program GParted.

This program shows you your harddisk(s) and here you can select it, right-click on it and select format.

---

### Post by Nailox on 2010-03-12
well I used to love it in the beginning - it was a new experience and I really liked the idea and philosophy of the open source software but later on there were a few bugs that started to annoy me. For example the flash wasnt working properly on a game that I play, the build-in mic in my notebook is not working, I need to use a few programs made for windows and they all run pretty ugly in WINE and also its too much hassle to setup games under WINE and Im starting to miss gaming. It was a great experience and a great community here in the ubuntu forums but I think its time to go back to Windows. The only advantage of linux turns out to be security and that there is no malware to worry about imho. It may be good for programmers and ppl that know what they are doing so they can debug kernels, modify the programs and what not but for me Windows seems to be the better option. Goodbye to all the people from this lovely community and thanks for your help!

---

### Post by howefield on 2010-03-12
It's no fun when things don't go well, or work as you want.

Just to add that dual booting with Windows 7 and Ubuntu is another consideration you might care for, giving you the best of both worlds.

Back to the original question, isn't there an option in the Windows 7 installation process at the stage of telling it where to install, that allows you to delete the disk and format ?

---

### Post by Nailox on 2010-03-12
> **howefield said:**
> It's no fun when things don't go well, or work as you want.

Just to add that dual booting with Windows 7 and Ubuntu is another consideration you might care for, giving you the best of both worlds.

Back to the original question, isn't there an option in the Windows 7 installation process at the stage of telling it where to install, that allows you to delete the disk and format ?

I thought there would be but there isnt. For some reason I dont like the dual boot option, I might use some linux distro from a pen drive though. So i booted from the ubuntu install cd but I cant find Gparted anywhere. I installed gparted on the hdd but I cant find a format option anywhere. I found in system>administration>disk utility that there is an option to erase the whole device (hdd) So what will happen if I use this option? Is it going to properly format it under NTFS ?

edit: I found that on the Windows installation cd there are options "delete" and "format" drive but the "format" is not clickable. Should I use the "delete" option

---

### Post by howefield on 2010-03-12
> **Nailox said:**
> So i booted from the ubuntu install cd but I cant find Gparted anywhere.

It might be called something else depending on the version of the live disk that you are using, maybe Partition Editor or something like that ?

> I installed gparted on the hdd but I cant find a format option anywhere.

You won't be able to format your disk if it is mounted, hence the reason for using the live CD.
 
> I found in system>administration>disk utility that there is an option to erase the whole device (hdd) So what will happen if I use this option?

Don't know, I don't use that utility.

---

### Post by howefield on 2010-03-12
> **Nailox said:**
> edit: I found that on the Windows installation cd there are options "delete" and "format" drive but the "format" is not clickable. Should I use the "delete" option

Just noticed your edit.

You can delete then format. I'm sure you already have a backup of anything you don't want to lose ?

---

### Post by Nailox on 2010-03-12
Its a ubuntnu jaunty jackalope install cd. I didnt find any similar option. I tried everywhere. So what if I use the delete option from the windows cd ?

---

### Post by sdpiowa on 2010-03-12
When using Windows, you'll often have to delete all used partitions on the hard drive before it will let you format it.

---

### Post by srs5694 on 2010-03-12
If you can't seem to get your partitions deleted using GParted or whatnot, there's always the "nuclear option:" Using a Linux text-mode prompt, type:

```

dd if=/dev/zero of=/dev/sda bs=512 count=1

```

You may need to add "sudo" to the start of this line, depending on how you've logged in. This command will blank out the partition table on /dev/sda, assuming you're using a Master Boot Record (MBR) partition table. When you reboot into the Windows installer, there won't be any partitions there for it to complain about, so your Windows re-installation should go much more smoothly.

---

