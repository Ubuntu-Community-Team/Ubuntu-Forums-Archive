---
title: "Can't get Ubuntu to boot Windows CD"
date: 2010-06-12
forum: Installation &amp; Upgrades
---

### Post by JustSteph on 2010-06-12
I want to completely uninstall Ubuntu and install Windows XP, but I restarted with the disc in the drive and nothing happened, it all loaded up as normal.

Help?

---

### Post by ronnielsen1 on 2010-06-12
Has nothing to do with Ubuntu. Your computer bios has to be set to boot  from cd and your XP disk needs to be bootable.

Sorry to see you go.
From your posts, the major problem is you're wanting to install [B]Movie Magic Screenwriter 6. According to winehq it's supposed to work. I will try to run it on my computer. You don't say whether you have the demo or full version. I will test the demo and post back

Ubuntu is a much better system if you learn it but there's a learning curve. 
[/B]

---

### Post by JustSteph on 2010-06-12
Thank you.

I remembered how to boot from disc and did it. The Windows setup began but then told me it couldn't find my hard drive. Any idea why?

There's a whole load of programs I can't run on it, as well as other problems. I'd rather just go back to Windows just now. Planning on getting a Mac sometime next year anyway.

---

### Post by wilee-nilee on 2010-06-12
You probably have the bios set to sata rather then ide, you have to have sata drivers on the CD or on a floppy or thumb to load XP. You can go into the bios to change the drive type. I like the idea though of you at the least having a dual boot possibility so the other person helping may find some answers for you.

---

### Post by ronnielsen1 on 2010-06-12
Click Wine > Configure wine

Click Drives Tab > Auto Detect > Apply

Click Libraries Tab > Click Arrow beside New Override for library: > Scroll down to 
msxml3 and click on it to highlight it and click add > Apply

Go to your MovieMagicScreenwriter6Trial.exe file > Right click > Properties
 > Permissions tab >Make sure that [COLOR=Blue]Allow executing file as program[/COLOR]
 is clicked 
Right click on the exe and click on open with wine. Install the program.


 _[IMG]http://s80.photobucket.com/albums/j177/ronnielsen1/?action=view&current=Screenshot-6.png[/IMG]_

[IMG]http://ubuntuforums.org/home/ron7/Downloads/MovieMagicScreenwriter6Trial.exe[/IMG]

---

### Post by Rubi1200 on 2010-06-12
This link will provide useful information about dual-booting Windows and Ubuntu:

[https://help.ubuntu.com/community/DualBoot](https://help.ubuntu.com/community/DualBoot)

As wilee-nilee points out, there are people willing to help you with finding solutions to the issues you have had/are having.

Dual-booting gives you the option of testing Ubuntu and becoming acquainted with it and also the chance to learn how Linux works.

If you persevere, I am sure you will find that Ubuntu is an OS very much worth having on your computer.

In any event, good luck!

---

### Post by JustSteph on 2010-06-12
Thanks, but I don't want Ubuntu any more, even as dual boot. I've had nothing but problems with it since I installed it. It's not just MMS6. There's a whole load of other programs it wont let me install. Wine doesn't even work properly. It wont even keep the time set right. Open Office is a pain in the rear end. I tried to rip a CD and it told me it was invalid (it was a perfectly legit CD). I haven't managed to successfully run a DVD, even though I downloaded all the right drivers. And to be honest, I can't be bothered fixing it all, or learning about Linux systems when I'm just going to go buy a Mac next year anyway. This I am certain I am doing as I'll need one for my career.

> **wilee-nilee said:**
> You probably have the bios set to sata rather  then ide, you have to have sata drivers on the CD or on a floppy or  thumb to load XP. You can go into the bios to change the drive type. I  like the idea though of you at the least having a dual boot possibility  so the other person helping may find some answers for you.

Thanks. But none of that made any sense to me. How do I go into the bios  to change the drive type?

---

### Post by ronnielsen1 on 2010-06-12
I tried to post a pic. I'm not sure why it didn't let me. I always have trouble with that. The program does work in wine

---

### Post by JustSteph on 2010-06-12
> **ronnielsen1 said:**
> I tried to post a pic. I'm not sure why it didn't let me. I always have trouble with that. The program does work in wine

Wine didn't even install properly on my computer though. Don't know why. I followed directions to the letter.

I ran the Ubuntu install disc to see if that's how I could reformat my hard drive and even though i cancelled it before clicking install, it's already uninstalled Ubuntu anyway. I'd rather just put XP on it.

---

### Post by JustSteph on 2010-06-12
Actually, it didn't, it was just running from the disc rather than the hard drive.

How do I format my hard drive so Windows recognises it?

---

### Post by ronnielsen1 on 2010-06-12
[http://support.microsoft.com/kb/314458](http://support.microsoft.com/kb/314458)

> This article explains how to remove the Linux operating 		  system from your computer and install Windows XP. This article  assumes that 		  Linux is already installed on your computer's hard disk, that Linux  native and 		  Linux swap partitions are in use (which are incompatible with  Windows XP), and 		  that there is no free space left on the hard disk.

**NOTE**:  Windows XP and Linux can coexist on the same computer. For 		  additional information, refer to your Linux documentation. [[IMG]http://support.microsoft.com/library/images/support/kbgraphics/public/en-us/uparrow.gif[/IMG]]("http://support.microsoft.com/kb/314458#top")

---

### Post by ronnielsen1 on 2010-06-12
[http://pcsupport.about.com/od/fixtheproblem/ss/bootorderchange.htm](http://pcsupport.about.com/od/fixtheproblem/ss/bootorderchange.htm)

> Changing the [boot order]("http://pcsupport.about.com/od/termsb/g/bootorder.htm")  of the "[bootable]("http://pcsupport.about.com/od/termsag/g/termboot.htm")"  devices on your computer like your [hard  drive]("http://pcsupport.about.com/od/componentprofiles/p/p_hdd.htm"), [floppy  drive]("http://pcsupport.about.com/od/componentprofiles/p/p_fdd.htm"), [optical  drive]("http://pcsupport.about.com/od/componentprofiles/p/p_odd.htm"), etc. is very easy. The [BIOS]("http://pcsupport.about.com/od/termsb/p/bios.htm") setup  utility is where you change boot order settings.
 Turn on or  restart your computer and watch for a message during the [POST]("http://pcsupport.about.com/od/termsns/g/termpost.htm")  about a particular key, usually **Del** or **F2**, that you'll  need to press to *...enter SETUP**.*** Press this key as soon as  you see the message.


---

### Post by darkod on 2010-06-12
> **JustSteph said:**
> Actually, it didn't, it was just running from the disc rather than the hard drive.

How do I format my hard drive so Windows recognises it?

You already have the answer to that in earlier posts. You don't need any specific formatting of the hdd before installing XP. The installer is capable of deleting existing partitions and creating new ntfs partitions.

The problem with XP is not seeing SATA disks without supplying the driver for the SATA controller on a floppy and pressing F6 when the XP cd boots.

One option to avoid this is setting your BIOS to use the SATA controller in IDE or Native IDE mode. If that option exists in your BIOS. Look around.

If there is no such option you have no other options than to provide SATA drivers on floppy or slipstream them into a XP cd.

As you noticed, Linux sees SATA disks by default, XP doesn't. It's your choice to use XP and you already got the answers you need.

---

### Post by JustSteph on 2010-06-15
> **ronnielsen1 said:**
> Click Wine > Configure wine

Click Drives Tab > Auto Detect > Apply

Click Libraries Tab > Click Arrow beside New Override for library: > Scroll down to 
msxml3 and click on it to highlight it and click add > Apply

Go to your MovieMagicScreenwriter6Trial.exe file > Right click > Properties
 > Permissions tab >Make sure that [COLOR=Blue]Allow executing file as program[/COLOR]
 is clicked 
Right click on the exe and click on open with wine. Install the program.
[IMG]http://ubuntuforums.org/home/ron7/Downloads/MovieMagicScreenwriter6Trial.exe[/IMG]


I tried this and when I tried to click "Allow executing file as program", I got the error message:
Sorry, could not change the permissions of "Screenwriter6CD.exe": Error setting permissions: Read-only file system

EDIT: Never mind. I copied the files from the disc to my hard drive and installed it from there.

Thank you

---

