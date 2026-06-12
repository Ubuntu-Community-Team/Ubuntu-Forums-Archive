---
title: "Help with install+drive mounting issues"
date: 2007-11-21
forum: Installation &amp; Upgrades
---

### Post by fiddilydee on 2007-11-21
okay here is the whole story. I have a computer that was preloaded with vista. I am now fed up with it's infinite amount of verification and comfirmation and stupid seemingly unfixable errors. I decided to install ubuntu, I am completely new to linux. 

I booted off of the cd and messed around with it to make sure I could still do everything I wanted (media and photo editing) of course it is even better than windows for this stuff. So I want to get rid of windows completlely and put Ubuntu on. I boot into it again make a seperate partition for my media and format the windows partition. After a couple of installation attempts (it did stall a few times) it finally completed but it will not accept the username/passowrd i typed in even though I know they are right. 

So I try a couple of things I read on here to change the password in recovery mode, it is telling me my user does not exist even though it automatically named my computer the same thing and this is printed in the bottom left corner the whole time. I try installing it again it is still booting from the old computer name and not accepting any of the things I put for username/password. 

So I load up my friends external hard drive to put my media on so I can do a full format and it cannot mount it even though it was working fine before. I am starting to get rustrated with this. 

Any tips or ways I can format everything besides my media partition because the first install created 3 or 4 locked partitions which I figure is causing my reinstallation issues (not recognizing new user profile)

I know that was long but any help would be appeciatied

---

### Post by rmemm on 2007-11-21
If you really want to wipe your whole drive and reinstall -- that should be pretty simple.  It's been a while since I did this (and it was with Dapper) -- but you should be amble to just boot from the install CD and go through the standard install procedure.  When you asked how to setup the drive -- select the option that wipes everything out.  Remember of couse this this will delete EVERYTHING.

To backup first, you need some other media like a USB drive or USB flash drive.  You'll need a live CD for this -- one that boots Linux without installing.  I use Knoppix for this -- but I think the Ubuntu CD comes with a Live CD option or maybe the standard install CD has that Option -- can't remember.

One reminder -- you do need to make certain your booting from the CD not from the installed distribution.  You set the boot order typically in the system BIOS/setup settings.  Since you were able to install before -- seems like you must have the CD drive before the Hard Disk -- but just thought I'd mention that.

Rob

---

