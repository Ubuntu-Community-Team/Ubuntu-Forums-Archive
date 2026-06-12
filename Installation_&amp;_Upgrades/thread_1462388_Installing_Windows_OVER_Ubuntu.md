---
title: "Installing Windows OVER Ubuntu"
date: 2010-04-25
forum: Installation &amp; Upgrades
---

### Post by madmax.santana on 2010-04-25
Hi there!!!
I would say I am a pretty old Ubuntu user. Been like this for past 3 years. And I am a big fan and supporter of Linux, of Ubuntu and of Open Source software foundation.

But like many of the Linux Gurus would agree with me, there are some, very few, things which are a bit complicated and difficult to do in Linux, whereas same things can be done very easily in Windows. Although I have long left Windows but I have some serious urgent matters at hand for which I need to keep Windows installed on my system just for a few weeks.

Now, I haven't done that before. What I want is, I back up my Ubuntu System and install Windows and then again install Ubuntu and copy my backup back into the system. (I choose this routine since I have a particularly low disk-space == 80Gigs and I need to reformat and rearrange the disk configurations of my system to meet the requirements of Windows and other software which I would install in Windows system later)

Now, is this possible that [COLOR="SeaGreen"]I copy WHOLE of my Ubuntu drive, into a portable HDD and after installing Windows, insert a Ubuntu disk into my system, format a drive to Ext4 and copy my Ubuntu drive back onto it, play with GRUB and just.[/COLOR]

Can I have my system back, without any damage, in that way?
If no (:() please let me know about some other way. I DO NOT wanna lose my Ubuntu system in this Windows fiasco. Also, I would need to get rid of Windows in future so I shall have to apply the technique you suggest a number of times.

**[COLOR="Red"]In short, I want to reformat and install Windows on my system without causing any damage to Ubuntu.[/COLOR]**

---

### Post by e-Gee on 2010-04-25
Try this [http://www.geekconnection.org/remastersys/remastersystool.html](http://www.geekconnection.org/remastersys/remastersystool.html)

---

### Post by madmax.santana on 2010-04-25
Thanks man. I am reading it right now. But what if I don't have so many DVDs as to copy and keep 30 GB of Ubuntu installation... That's just a card for discussion. I am reading the article and it might lead me to something.

---

### Post by madmax.santana on 2010-04-25
There is something else. To install remastersys, I need to add the repository to sources and then run apt-get update to be able to install it.
But I am behind a proxy server which has an http filter on it. It is denying access to the repository.
Can you suggest another option?

---

### Post by ajgreeny on 2010-04-25
Have a look at **clonezilla** to clone your current ubuntu partitions or disk, or even consider **partimage**, another way to do more or less the same thing.

---

### Post by madmax.santana on 2010-04-25
> Partimage does not support ext4 or btrfs filesystems.

And for Clonezilla, the disk has to unmounted for backup. Even if I do log on from a live CD and run Clonezilla from there (which I am at loss to imagine how, since Clonezilla doesn't come in the default Ubuntu installation), and it just copies the hard drive data, can't it be done easily enough by > cp -r /media/sda1/* /media/Backup-Drive/

The remastersys was a good option. I shall talk to my IT support office and tell them to do something so that I can access the repository (which is gonna be difficult since most of them shall not know what on earth a repository is, damn Linux ignorant population :P)

---

### Post by beta.tester on 2010-04-25
> **madmax.santana said:**
> Hi there!!!
I would say I am a pretty old Ubuntu user. Been like this for past 3 years. And I am a big fan and supporter of Linux, of Ubuntu and of Open Source software foundation.

But like many of the Linux Gurus would agree with me, there are some, very few, things which are a bit complicated and difficult to do in Linux, whereas same things can be done very easily in Windows. Although I have long left Windows but I have some serious urgent matters at hand for which I need to keep Windows installed on my system just for a few weeks.

Now, I haven't done that before. What I want is, I back up my Ubuntu System and install Windows and then again install Ubuntu and copy my backup back into the system. (I choose this routine since I have a particularly low disk-space == 80Gigs and I need to reformat and rearrange the disk configurations of my system to meet the requirements of Windows and other software which I would install in Windows system later)

Now, is this possible that [COLOR="SeaGreen"]I copy WHOLE of my Ubuntu drive, into a portable HDD and after installing Windows, insert a Ubuntu disk into my system, format a drive to Ext4 and copy my Ubuntu drive back onto it, play with GRUB and just.[/COLOR]

Can I have my system back, without any damage, in that way?
If no (:() please let me know about some other way. I DO NOT wanna lose my Ubuntu system in this Windows fiasco. Also, I would need to get rid of Windows in future so I shall have to apply the technique you suggest a number of times.

**[COLOR="Red"]In short, I want to reformat and install Windows on my system without causing any damage to Ubuntu.[/COLOR]**

Hi

Silly question but have you considered visualization?

Virtual box is a dream and easy to use and you can install it into Ubuntu and then the windows you need within the virtual-box. I have it installed here for the occasional windows must have that I need and also to use it to safely try out other alpha/beta versions :) When it goes wrong you simply delete it and install another :)

Hope this helps and keep on Ubuntuing,   john

---

### Post by madmax.santana on 2010-04-25
> **beta.tester said:**
> Hi

Silly question but have you considered visualization?

Virtual box is a dream and easy to use and you can install it into Ubuntu and then the windows you need within the virtual-box. I have it installed here for the occasional windows must have that I need and also to use it to safely try out other alpha/beta versions :) When it goes wrong you simply delete it and install another :)

Hope this helps and keep on Ubuntuing,   john
Thank you very much of your serious consideration of my issue. No it is not silly at all and in fact I have considered virtualization.

Actually my computer is an old one, Celeron 3.0GHz with just 1GB of RAM. I rarely use Firefox because it highly effects the performance of my PC by putting so much burden on my already feeble processor.

In case I use virtualization to run Windows on my system, the load of Ubuntu system, the virtualization engine and the operating system, all falls on the processor. Also, when I create a virtual machine, I have to assign some RAM to the machine. Out of mere 990MB of RAM, how much do you suggest I give to an OS so memory inefficient as Windows?

That was why I rejected the idea of running the particular software on WINE and thought better of it to buy a Windows CD and use ONE-AT-A-TIME instead.
 
So these are my limitations... 

I am very thankful to you, and of course everybody else who has helped me take a start on this. I have just found a deb of remastersys somewhere and I am gonna have a go at it now.

---

### Post by toolfan2k4 on 2010-04-25
I have never done this so I cannot give you the exact procedure. But I can tell you that I have heard of people partitioning the HDD and then installing Windows on the new partition. After that you would need to restore the GRUB boot loader so that you can actually access the Ubuntu partition and boot from it. I have seen many how-to articles on restoring the GRUB boot loader..a simple google search is certain to bring up at least one of them. I know this doesn't exactly answer your questions but it may help you out.

---

### Post by padnoter on 2010-04-25
> **toolfan2k4 said:**
> I have never done this so I cannot give you the exact procedure. But I can tell you that I have heard of people partitioning the HDD and then installing Windows on the new partition. After that you would need to restore the GRUB boot loader so that you can actually access the Ubuntu partition and boot from it. I have seen many how-to articles on restoring the GRUB boot loader..a simple google search is certain to bring up at least one of them. I know this doesn't exactly answer your questions but it may help you out.

Here's one such link that I am thinking of trying..

[http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm?page=1](http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm?page=1)

---

### Post by beta.tester on 2010-04-26
> **madmax.santana said:**
> Thank you very much of your serious consideration of my issue. No it is not silly at all and in fact I have considered virtualization.

Actually my computer is an old one, Celeron 3.0GHz with just 1GB of RAM. I rarely use Firefox because it highly effects the performance of my PC by putting so much burden on my already feeble processor.

In case I use virtualization to run Windows on my system, the load of Ubuntu system, the virtualization engine and the operating system, all falls on the processor. Also, when I create a virtual machine, I have to assign some RAM to the machine. Out of mere 990MB of RAM, how much do you suggest I give to an OS so memory inefficient as Windows?

That was why I rejected the idea of running the particular software on WINE and thought better of it to buy a Windows CD and use ONE-AT-A-TIME instead.
 
So these are my limitations... 

I am very thankful to you, and of course everybody else who has helped me take a start on this. I have just found a deb of remastersys somewhere and I am gonna have a go at it now.

Hi again :)

From my own settings *within* Virtualbox 3.1.6r59338 for the install of Win 2KSP4 on Ubuntu 10.04 RC (now as all updates applied ;) (I use Windows 2000 with SP 4 slipstreamed into it)

Base memory = 168 Meg
Video       = 61 Meg

These settings give me a full screen (after installing Guest additions) of 1024x768 and 2D acceleration :)

Maybe worth a shot of your remastersys lets you down.

Keep on Ubuntuing and kind regards     john

---

### Post by mk1w86 on 2010-04-26
To the OP:

You could backup your system using Clonezilla as suggested and then resize your partitions using Gparted on the Ubuntu LiveCD so there is enough space for a Windows partition.  However, this depends on you having enough free space on your Ubuntu partition to shrink it and you mentioned you only have a 80GB hard drive. :-|

You would then have to reinstall Grub because Windows will overwrite it.  There is a guide here:

[https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD](https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD)

---

