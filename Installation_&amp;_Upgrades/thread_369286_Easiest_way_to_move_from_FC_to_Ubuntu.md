---
title: "Easiest way to move from FC to Ubuntu ?"
date: 2007-02-24
forum: Installation &amp; Upgrades
---

### Post by elmerfud on 2007-02-24
I know nothing about Ubuntu. I'm thinking of switching to it. I've used RH/Fedora since RH8.
 
 What is the easiest way to switch from fc6 to Ubuntu ? I have about 5 years of "stuff" on my computer - apps, data, projects, etc.
 
 Is there a way to install Ubuntu over what I already have or does one need to install fresh ?
 
 Thanks.

BTW: I double posted this.  I posted the same thing here before I realized this would be a better forum. 

[http://ubuntuforums.org/showthread.php?t=369269](http://ubuntuforums.org/showthread.php?t=369269)

---

### Post by Gerard Barberi on 2007-02-24
Is your /home directory mounted on a separate partition?

---

### Post by elmerfud on 2007-02-24
Nope, home is not mounted to a separate partition.

And I have XP mounted on a separate partition.

I can back up home to another hard drive easily enough.

---

### Post by aysiu on 2007-02-24
I would use [http://www.fs-driver.org](http://www.fs-driver.org) in Windows XP to back up all your important files (documents, pictures, music, etc.) and config folders (for me, that's .mozilla and .thunderbird for internet settings and emails), then do a clean reinstall of Ubuntu *over* Fedora and then copy over the important files and config folders.

---

### Post by elmerfud on 2007-02-24
Just to clarify, what do you mean by "over Fedora" ?

When one updates Fedora, it senses that there is already a Linux installed.  It thus leaves everything alone and updates the appropriate packages.  Is that what you mean, only for Ubuntu ?

Next question... does Ubuntu use rpm ?  I use synaptic right now, so I assume its the same, right ?  I've got a lot of apps installed that are -fc6.  If I update to Ubuntu, will they still run or do I have to reinstall ?

Thanks

---

### Post by elmerfud on 2007-02-24
Umm.... there isn't a way that I could point to a repository and do a yum update or something like that, is there ?

---

### Post by aysiu on 2007-02-24
I mean **erase** Fedora by installing Ubuntu *over* it. After you install Ubuntu over Fedora (not next to--over), Fedora no longer exists. I thought that's what you meant when you said > I'm thinking of switching to it. I've used RH/Fedora since RH8.

What is the easiest way to switch from fc6 to Ubuntu ? I'm talking about a fresh install.

---

### Post by elmerfud on 2007-02-24
Ok

---

### Post by elmerfud on 2007-02-24
How does one wipe the old Linux partitions ? (/boot and /)  Reformat them ?

---

### Post by aysiu on 2007-02-24
> **elmerfud said:**
> How does one wipe the old Linux partitions ? (/boot and /)  Reformat them ?
During the Ubuntu installation process, select **Manually Edit Partitions** instead of **Erase Entire Hard Drive**. You'll then be allowed to mount certain partitions at different mount points (/boot and /) and have the option to format or not format them. I would recommend formatting them.

More details (including screenshots) here:
[http://psychocats.net/ubuntu/installing](http://psychocats.net/ubuntu/installing)

---

### Post by tgalati4 on 2007-02-24
With the dropping price of disk drives these days, it's easier to buy another drive and pop in and partition it smartly for a fresh Ubuntu install.  That way you can triple boot: XP, FC, and Ubuntu.  In Ubuntu, you can mount the other two drives to have access to your work.

You can take your time customizing your shiny new Ubuntu install, while maintaining a working Fedora Core system.

After a year or so, you should have all of the data that you need and you can wipe the FC partition and use it for general data storage.

I can't understand why people are so quick to thrash a working system--especially one that has worked for 5 years.

---

### Post by elmerfud on 2007-02-24
Unfortunately its in a laptop.  But I can move all of home to a USB drive easy enough.  I'm worried about losing my password wallet !

I'm pretty frustrated with Fedora.  I've fixed and put up with a lot of bugs over the years.    Having mouse issues and wireless quit on a working system is the last straw.

---

### Post by tgalati4 on 2007-02-24
Here's a trick from the mac world:  Buy a good sized notebook drive and a USB enclosure.  Partition it correctly (decent swap size, 100 MB partition for DSL or other emergency linux and tools, separate home partition and Ubuntu partition).  

Load Ubuntu onto the external drive--keeping FC intact.  Edit your grub menu (/boot/grub/menu.lst) to include the Ubuntu install with the usb connection (something like /dev/sda1)  You might have to create a link to get grub to recognize the hard drive  (sudo link -s /dev/sda1 /dev/hdb1) so that grub can use the proper root command (root (hd1,2) for example)

When your FC drive fails (most laptop drives get wonky after 5 years of use, you can pop in your Ubuntu drive and you are good to go.  You will also have a backup of your data, since you will have a snapshot of /home in your new Ubuntu drive.

Search the forums for USB booting.  There may be a few steps that I have left out.

Macs can boot directly from firewire (but not USB) drives with a key press during power on (T, I believe for target drive).  PC's require a few hoops since USB drives are not considered hard drives by the BIOS.

That being said, there may be a BIOS option for USB boot and then you can ignore all the grub stuff.  Ubuntu when you are plugged in and FC/Windows when you are not.

---

### Post by elmerfud on 2007-02-24
Hmmm... the external boot is an interesting idea.  I could run that for a month or so and then make my choice.

I have to give this some thought.  I don't think my laptop will boot an external device though.  Hmmm....

---

### Post by elmerfud on 2007-02-26
Now that I think about this more, I'd like to do the reverse of what has been suggested, that being move my current Fedora to an external USB drive.  Then wipe my hard drive and install Ubuntu.  Then make Fedora bootable from the external drive so that I can go back and run it at any time. 

I am really afraid of losing my data and applications ! 

I am starting a new thread on this.

---

