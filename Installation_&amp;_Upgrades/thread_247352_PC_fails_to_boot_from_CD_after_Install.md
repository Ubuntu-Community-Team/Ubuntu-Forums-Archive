---
title: "PC fails to boot from CD after Install"
date: 2006-08-30
forum: Installation &amp; Upgrades
---

### Post by tlimon on 2006-08-30
My system has been running well using XP pro for quite a while.  My family is quite happy with the way things worked until...

My curiosity about free OS's led me to install Ubuntu on a spare hard drive.  XP is on a SATA Seagate 160GB single partition as Drive 0.  I put Ubuntu on the spare SATA Seagate 160GB hard as Drive 1.  Drive 1 has dual partitions, one partition for the swap , and one for the OS.  During the install, I made the mistake of saying "yes" to the question about the GRUB Boot loader.  

If I could only go back in time....

After some time exploring the Ubuntu OS, I decided to boot back to Windows.  I chose restart, and popped into the BIOS to switch the boot order so that XP would boot first.  I saved the changes and was presented with the GRUB menu again.  Strange....Hmmm....  

I did some reading and found that the GRUB thingy actually rewrote the MBR on my XP drive.  I could easily get back to booting direclty to XP by using the repair function and FIXMBR or FDISK /MBR from my XP install CD.  All would be right once again Until...

A quickly popped into the bios to change the boot order to CD first and saved the changes and rebooted.... I'm seeing the "searching CD for boot secter, then GRUB? Again?  WTF?

Now I'm starting to sweat.  Fear of the wrath of the family is wearing me thin.  I need some help.  

What should I do to get the system back to booting from the bios selected boot device?  

Any help restoring the system to would be graciosly appreciated.

---

### Post by randell6564 on 2006-08-30
Hi!  Dont give up!  Read this [http://linuxmafia.com/faq/Hardware/sata.html](http://linuxmafia.com/faq/Hardware/sata.html)

S-ATA Raid devices are tricky when it comes to Dual-booting.

Good Luck!

---

### Post by tlimon on 2006-08-30
Thanks for the tips, but it really doesn't help me get my system back.  Both SATA drives are seen by each OS, along with the IDE DVD and CD drive.  Its not really a drive support issue with either OS.

What I'm trying to understand is why GRUB just blows right past the BIOS boot selection choices.  I've tried every BIOS boot order imaginable, even removing both SATA drives from the list, and the computer still insists on booting into the GRUB bootloader.  My next step is to open the case and physically disconnect the offending Ubuntu drive and then try and repair the remaining XP MBR. This would be my last resort, and I don't hold out much hope as I've read of others who've wiped out the ubuntu partition only to make the system un bootable in either OS.

Alternatly, I could change the menu.lst file such that the default is the XP menu choice.  I cant get the permissions worked out in order to save my changes.  Is there a default password for root on a fresh Ubuntu install?  My user password isn't doing the trick.  This option still leaves me out to dry should I ever need to boot from a CD to run the XP recovery console.

Soooo... Thanks for the help, I welcome other suggestions to this puzzle...Can you help me boot from the CD drive?

---

### Post by zxee on 2006-08-30
> **tlimon said:**
> 

Soooo... Thanks for the help, I welcome other suggestions to this puzzle...Can you help me boot from the CD drive?

You have selected the optical drive as first boot device in your bios _and_ have a bootable cd in the drive?
There is no reason no matter how messed up the mbr is that you shouldn't be able to boot from your cdrom. I would check to be sure you saved changes in the bios and try again-either that or the drive is going bad?

If you have a floppy drive you could use a dos rescue disk to boot from that and enter the fdisk /mbr command.
Check out more details here: [http://www.novell.com/coolsolutions/qna/1742.html](http://www.novell.com/coolsolutions/qna/1742.html)

---

### Post by a-man on 2006-08-31
(I realized that I accidentally posted this to the wrong page in the tab that was open. I know this may help some people because it helped me but it may have nothing to do with your situation. sorry for the confusion)

I had a similar problem when I installed Ubuntu on 1 of the 2 drives (both IDE) in my PC. The primary drive was XP which I replaced with Ubuntu. The second drive was another XP I wanted to keep. After the install, I booted in Ubuntu, messed around, then did what I thought I needed to do in grub to get the XP drive to boot. I could never get the XP drive to boot for a long time and I almost gave up. I always got "NTLDR is missing" or something like that. I noticed a lot of people had the same problem. I was able to mount the XP drive in Ubuntu and grab files from it so I knew it was still there and working fine.

Then recently I ran across something and I got it so I could boot into XP. There is a new error with the boot.ini being corrupt but at least XP would boot up and I could worry about the boot.ini later on. Here's what I tried:

Boot with XP CD.

Press R to load the Recovery Console.

(for the next step D: would be the CD drive with the XP CD)

Type:
copy D:\i386\ntldr C:\
copy D:\i386\ntdetect.com C:\


(two other files needed - just in case)

Type: 
attrib -h -r -s C:\boot.ini del C:\boot.ini

Type: 
bootcfg /rebuild

this will get rid of any damaged boot.ini, search the disk for systems and make a new one. This might even result in a damaged windows reappearing; but gives another chance of getting at the repair.

Anyway, this worked for me except for the boot.ini error while booting now and I will get that repaired next when I get the chance.  I've only done this fix once so I don't know if it would work every time on any PC. I wanted to post this fix so other people with the same problem could try it but I saw your post here first while I was looking for something else. I'll probably post this again soon under "NTLDR is missing"

Good luck getting it fixed.

---

### Post by randell6564 on 2006-08-31
Yes, if you installed ubuntu onto a box that already has XP on it, then grub will place itself in the MBR.  Whats wrong with that?  In this situation, you should have a dual boot option.

If you have a messed up MBR then boot into the live CD, open up a terminal and type:

**sudo grub**

**find /boot/grub/stage1**

 if you know which is your XP drive say for example hd0,0, then you would do:

**root (hd0,0)**

**setup (hd0)**

**quit**

That will reinstall grub to your MBR and should give you a dual-boot option

I know in your case you should see 'sda whatever' when you do the **'find'** command,

---

### Post by randell6564 on 2006-08-31
> **tlimon said:**
>   Is there a default password for root on a fresh Ubuntu install?  My user password isn't doing the trick.  

Soooo... Thanks for the help, I welcome other suggestions to this puzzle...Can you help me boot from the CD drive?

You cant use **sudo** for root priviledges?

To boot from the CD, go into your Bios and set your boot order to CD first.

---

### Post by randell6564 on 2006-08-31
> **tlimon said:**
> 

 I made the mistake of saying "yes" to the question about the GRUB Boot loader.  

After some time exploring the Ubuntu OS, I decided to boot back to Windows.  I chose restart, and popped into the BIOS to switch the boot order so that XP would boot first.  


Saying "yes" was not a mistake if you wanted to dual-boot!  When you said yes, grub should have been installed onto your MBR.

Why are you "popping" into your Bios to switch the boot order?  Again, you should have a dual-boot option! When you boot you should come to the grub options menu and see Ubuntu and XP!

---

### Post by mxreader on 2006-08-31
Randall,

I have a similar problem, but posted in a new thread (dont want to hijack this one) but what you wrote has given me a possible clue.

Can you tell me how to determine the drive assignment or what ever you call it for root(hd...,0)
and I am guessing it should be the same as what Grub points to. So if it is true that it should be the same, and it isnt how do I change it?

Thanks

---

### Post by mxreader on 2006-08-31
Oops sorry.. rand**e**ll

---

### Post by tlimon on 2006-08-31
Okay I've made some progress and am happy for the time being.  I found instructions on editing the menu.lst file using [this technique]("http://psychocats.net/ubuntu/permissions")  I changed one line of code (default 0 to default 3).  The system boots right into windows unattended now.  So, for the most part, I'm good.  Thanks randell6564, for your efforts.

At some point, I'd like to try other Linux distributions, like SUSE , without an actual install.  Booting from the CD would allow me to run the Live CD versions.  Also, when XP dies, I'll need to get into the recovery console by booting from the CD as well.

**zxee** has the problem nailed:

> You have selected the optical drive as first boot device in your bios and have a bootable cd in the drive?
There is no reason no matter how messed up the mbr is that you shouldn't be able to boot from your cdrom. I would check to be sure you saved changes in the bios and try again-either that or the drive is going bad?

I think perhaps the old Pioneer AO5 drive is going bad.  Earlier in the week I got errors loading the OpenSUSE Live CD and gave up.  I've been looking for an excuse to buy a new DL-DVD drive, so this is my ticket to go hardware shopping at Fry's. So, you see, there is a bright side afterall! 

In the mean time, I'll try booting from the the Teac CD drive and post the results.  Thanks to all for the kind suggestions.  I feel like I'm becoming a member of the family.

---

### Post by zxee on 2006-08-31
> **tlimon said:**
> Okay I've made some progress and am happy for the time being.  I found instructions on editing the menu.lst file using [this technique]("http://psychocats.net/ubuntu/permissions")  I changed one line of code (default 0 to default 3).  The system boots right into windows unattended now.  So, for the most part, I'm good.  Thanks randell6564, for your efforts.

At some point, I'd like to try other Linux distributions, like SUSE , without an actual install.  Booting from the CD would allow me to run the Live CD versions.  Also, when XP dies, I'll need to get into the recovery console by booting from the CD as well.

**zxee** has the problem nailed:



I think perhaps the old Pioneer AO5 drive is going bad.  Earlier in the week I got errors loading the OpenSUSE Live CD and gave up.  I've been looking for an excuse to buy a new DL-DVD drive, so this is my ticket to go hardware shopping at Fry's. So, you see, there is a bright side afterall! 

In the mean time, I'll try booting from the the Teac CD drive and post the results.  Thanks to all for the kind suggestions.  I feel like I'm becoming a member of the family.

Good luck at fry's I would go for a drive with a high MTBF, you could check out [www.newegg.com](www.newegg.com) (good prices and fast shipping).
I'm not connected with them in any way just like their service.

---

### Post by Fatjoint on 2006-08-31
> **tlimon said:**
> Okay I've made some progress and am happy for the time being.  I found instructions on editing the menu.lst file using [this technique]("http://psychocats.net/ubuntu/permissions")  I changed one line of code (default 0 to default 3).  The system boots right into windows unattended now.  So, for the most part, I'm good.  Thanks randell6564, for your efforts.

At some point, I'd like to try other Linux distributions, like SUSE , without an actual install.  Booting from the CD would allow me to run the Live CD versions.  Also, when XP dies, I'll need to get into the recovery console by booting from the CD as well.

**zxee** has the problem nailed:



I think perhaps the old Pioneer AO5 drive is going bad.  Earlier in the week I got errors loading the OpenSUSE Live CD and gave up.  I've been looking for an excuse to buy a new DL-DVD drive, so this is my ticket to go hardware shopping at Fry's. So, you see, there is a bright side afterall! 

In the mean time, I'll try booting from the the Teac CD drive and post the results.  Thanks to all for the kind suggestions.  I feel like I'm becoming a member of the family.



I would suggest that if you wanted to try other OS's without actually installing them, that you go to [vmware](www.vmware.com) and download the free player.  You can also download images to play with inside of vmware of free OSs.

---

### Post by tlimon on 2006-08-31
Okay, More progress to report:  

I put the XP disk into the Teac drive, selected it as first boot in the BIOS and.....  It booted from the CD!  I goofed around a bit and was able to get the Pioneer drive to boot the Live SuSe disk once.  

Here's my theory:  

I think adding the additional hard drive dropped the available power somewhat.  The PC is chocked full of add-on cards and adding the 4th drive may be taxing the 400W power supply a bit thus making the Pioneer drive dodgy.  I'll try a new drive (or a better power supply) since I can't pass up an opportunity to buy new hardware.

I've had similar experiences years ago when a failing power supply caused my components to fail one by one. It was nerve racking but eventually solved.  I believe I'm on to something.  Thanks again!

---

