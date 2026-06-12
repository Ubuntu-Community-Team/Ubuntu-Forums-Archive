---
title: "Error 17"
date: 2006-06-12
forum: Installation &amp; Upgrades
---

### Post by lawerencef14 on 2006-06-12
Ok, I have searched through the forums and there seems to be a fix for my problem but I want to make sure.  This is my first foray into Linux. 

First off the issue:
I have a Windows XP Home install on my master hd and Vista Beta on my second hd which dual booted before trying to install Ubuntu.  I don't care if I lose the Vista install it just is too unstable on my machine.  I have a Dell 5100with 768RAM and 2.00ghz processor or something close to that...going on memory. 

So I tried to install Ubuntu on the second drive and used the resize option.  Everything seemed to go fine except on reboot I get the Error 17 message.

It seems there is a way to get to a command line kind of thing...again I am a newbie on this.  So how do I get to the command line and how do I fix GRUB?  I think I understand the situation is that the mapping is incorrect but not really sure.  I liked the Live CD and really want to try it out as a system...I have two other computers at home for my kids and thought it might be safer for them on Ubuntu or something not Windows...

Ok, I am babbling...but again I don't care if I lose the Vista install on the second hd and that is where I want my Ubuntu installed.  I have alot of important/sentimental stuff on my first hd and don't want to lose any of it. 

How do I get to the command line to fix it and what othe information can I provide so someone can help?  I read somewhere there is a rescue option, is that available from the Live CD or will I need to download something?

Please help!

Thank you in advance for any help anyone can provide!!!

---

### Post by lawerencef14 on 2006-06-12
Ok, maybe I didn't ask the right question, sorry but I am new to Linux...how can I use the Live CD to fix the boot loader?

Thank you!

I am a newbie at this...

---

### Post by johnk93 on 2006-06-12
Hey,
I'm completely new as well and can't offer a solution, but I am having the same trouble installing dapper to my second (actually 4th) hd.  

GRUB appears to start OK when I load the linux hd first, but when I select to load linux, i get an error 17, and when I select to load windows I get a different error (don't have the exact errors in front of me now).  I used to alt install disk and selected to install GRUB to my mbr, but the problem persists.  

Can anyone offer a fairly detailed guide to installing ubuntu on a different hd than windows?  I've tried everything that I could find on the forums regarding dual-booting, but can't seem to get it right.  I believe that my linux partitioning is OK, but I can't get windows to play nice with linux from a different drive.  Would re-partitioning my windows drive and installing linux here solve this problem?  

Thanks,
John

---

### Post by lawerencef14 on 2006-06-12
FYI...I used my Windows XP Home Reinstall disk to fix the MBR.  I don't see the Linux partition from XP now so I am not sure if it was wiped when I did that.  Regardless, I do have windows back up.  Now, I will try to reinstall Ubuntu.  My question is, should I choose to uninstall Vista on the second drive and then just install Ubuntu on there?  As I said earlier, I don't care for vista now still too unstable to do anything with it.  Any advice on going that route?

---

### Post by confused57 on 2006-06-12
[QUOTE=lawerencef14]FYI...I used my Windows XP Home Reinstall disk to fix the MBR.  I don't see the Linux partition from XP now so I am not sure if it was wiped when I did that.  Regardless, I do have windows back up.  Now, I will try to reinstall Ubuntu.  My question is, should I choose to uninstall Vista on the second drive and then just install Ubuntu on there?  As I said earlier, I don't care for vista now still too unstable to do anything with it.  Any advice on going that route?[/QUOTE]

You don't need to uninstall Vista on your slave drive, just choose erase entire disk and install Ubuntu onto hdb, Ubuntu will reformat and write over Vista, hda should be your WinXP...grub will be installed to the mbr of WinXP on hda.

There's another option, if you don't mind opening up your computer:

[http://www.ubuntuforums.org/showthread.php?t=179902](http://www.ubuntuforums.org/showthread.php?t=179902)

---

### Post by lawerencef14 on 2006-06-13
Thanks, I will try the erase entire disk option.

---

### Post by lawerencef14 on 2006-06-14
I formatted the drive with Vista on it and then installed Ubuntu on it...very easy everything in the world is right now.

Thank you Confused 57!!!

---

### Post by confused57 on 2006-06-14
[QUOTE=lawerencef14]I formatted the drive with Vista on it and then installed Ubuntu on it...very easy everything in the world is right now.

Thank you Confused 57!!![/QUOTE]

Great, glad you got Ubuntu installed...now the fun begins.  I was quite apprehensive starting out, until I found out how easy it was.  
You'll be answering questions & giving advice in the forum before long...

---

