---
title: "Installing Ubuntu"
date: 2005-10-10
forum: Installation &amp; Upgrades
---

### Post by jakewc2 on 2005-10-10
Hi everybody, I only just found this site, so I'm new here. I hope that you don't mind me jumping in and asking for some help. I hope I have posted to the right forum now, I am sorry if its not.

I am using a pc, and its windows ME. I want to be able to use Ubuntu, but without paritioning my existing hard drive. I have managed to by a second HD, installed it. At the moment it is attatched as the primamry slave. Its not formatted, so there are no Cd-rom drives or floppy disk drives on it.

I want to install the ubunto software onto the new hard drive, but I have no idea of how to go about it. 

When I go to install, how do I get windows to install it to the empty hard drive?
Once I can get it installed, how do I get windows to allow me the choice of booting obuntu, without windows, or can both be bootted at the same time? 

I have no idea about Linux, so please could you be as simple in your explanations as you can.

Thanks for your help.

John.

---

### Post by adwait on 2005-10-10
Ok....lets start of with basics, Ubuntu is not a software that can be installed by windows. It is a complete Operating System, on par with windows. You cannot install Ubuntu in Windows. You need to put the cd rom in the drive, and then boot the computer from the CD. After that, follow the instructions on screen and answer the questions. When it asks you where to install, select hdb (that would be your second hard drive). Also......the ubuntu CD will automatically install the boot loader, which is a software that will ask you which OS you want to boot into every time you turn the computer on.

---

### Post by jakewc2 on 2005-10-10
Thank you for your reply. I usually use Windows, but want to get used to Ubuntu, how do I get it so that I can swap and change? Would I have to put the ubumtu cd in everytime I wanted ti use it?

Sorry just read your last post again, and understand what you wrote.

Once its installed, do I need to install the cd rom and floppy disc or will it do that for me?

---

### Post by DJ_Max on 2005-10-10
> Would I have to put the ubumtu cd in everytime I wanted ti use it? 
That's why Linux will install [Grub](https://wiki.ubuntu.com/GrubHowto) or Lilo.

Anyhow, when you boot the Ubuntu CD, it should recongnize both hard drives, granted your jumper settings are correct. (for IDE/ATA drives of course, since SATA drives don't have jumpers).

The installer is very straightforward. Since the second HD is blank, you won't have to partition anything manually, the installer will do it for you.

The first HD may be /dev/hda, the second HD will depend on your computers setup. [http://www.tldp.org/HOWTO/Partition/partition-2.html](http://www.tldp.org/HOWTO/Partition/partition-2.html)

For further explantion, you can do a search on these forums, as well as visit some of the many sites. There are a few in my sig.

> Once its installed, do I need to install the cd rom and floppy disc or will it do that for me?
What do you mean by install? You should already have the CDROM and Floopy drive attached.

---

### Post by jakewc2 on 2005-10-10
Hi DJ Max, sorry not sure I understand much of what you said, because I have never used Linux before. I got the bit about the HD's, and my second HD is recognised by windows as the Primary Slave, so would that be right?

This is what I am wondering about. When I open up the second HD, its totally blank, and shows nothing. Have I connected it wrongly?

---

### Post by DJ_Max on 2005-10-10
[QUOTE=jakewc2]Hi DJ Max, sorry not sure I understand much of what you said, because I have never used Linux before. I got the bit about the HD's, and my second HD is recognised by windows as the Primary Slave, so would that be right?

This is what I am wondering about. When I open up the second HD, its totally blank, and shows nothing. Have I connected it wrongly?[/QUOTE]
If Windows recognizes the second HD as a slave, it should be setup correctly.

---

### Post by jakewc2 on 2005-10-10
Ok, thank you for your help, I am going to try and install, I might be back, if it works, I just hope it does nothing to my pc. :???:

---

### Post by jakewc2 on 2005-10-10
Hi, bit of a panic, when I put the ubuntu cdrom in, loads of script came up, pages and pages of it, but there was nowhere for me to direct the installation to a specific place. I stopped it, and came out. Its not somethign I've come across before. Does it eventually give you a direction of where to install the cd? 

Sorry, I did say in my first message I'm totally new to something like this. 

John.

---

### Post by DJ_Max on 2005-10-10
[QUOTE=jakewc2]Hi, bit of a panic, when I put the ubuntu cdrom in, loads of script came up, pages and pages of it, but there was nowhere for me to direct the installation to a specific place. I stopped it, and came out. Its not somethign I've come across before. Does it eventually give you a direction of where to install the cd? 

Sorry, I did say in my first message I'm totally new to something like this. 

John.[/QUOTE]
Yes, it's toward the partitioning stage in the middle/end.

---

### Post by jakewc2 on 2005-10-10
OK, thank for getting back to me, I really appreciate the help. I'll go take a look again. 

John.

---

