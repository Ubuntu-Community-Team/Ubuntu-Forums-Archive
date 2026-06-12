---
title: "Win7 and Ubuntu 12.04 fubar after Ubuntu update and boot-repair"
date: 2012-05-03
forum: Installation &amp; Upgrades
---

### Post by Mimalito on 2012-05-03
Hello folks, 

First and foremost I apologize for being the newbie whose first post is similar to others found on here.  I did browse the sticky and a couple other posts, however taking bits and pieces of advice from random forums without understanding everything I was doing led me to my current problem.

Background:

I am an average/slightly above average windows user and a novice linux user.  I understand the basics of linux but a lot of the terminology is still new to me.

I've had Win 7 installed on my SATA internal drive on this machine for about 5 months.  1-2 months ago I decided to play with linux but was weary of the partition process so I split an external 2TB drive in two and installed 11.10 on it.  

Because I'm not really familiar beyond the basic concepts of MBR and GRUB I dual booted my machine but in a less then smooth fashion.  I set my BIOS to boot first from my external drive (Ubuntu) and then my internal drive (Win7).  This way I could turn on my external if I wanted to boot linux, and if I wanted windows I would simply leave the external off during the boot sequence.  It never worked flawlessly but I could successfully boot into it and run Ubuntu.  Some days it was all I would use.

My problem:

So a few days ago I booted into Ubuntu and was prompted to update to 12.04.  I clicked away.. why not?
The update seemed to go smoothly, no noticeable errors.  Upon reboot it said that there was no operating system present or something to that effect.  I rebooted into Win 7 and read up on the error.  Forum posts were talking about it not being  a big deal and to use boot-repair on it.  I rebooted again and used my Ubuntu 11.10 thumb drive to use boot-repair.  After I did and successfully(?) repaired it I rebooted.  

Ubuntu 12.04 was found but I did notice something new.  It was giving me messages about it taking a long time to mount certain drives.  If was listing a few partitions on a separate internal drive so I skipped them.  Ubuntu 12.04 loaded up and it immediately saw the partitions it claimed not to anyway.  I messed around with 12.04 a bit and the few personal files I had were still there and accessible.  

I decided I wanted to connect my Kindle to Win 7 and put some music on it since Ubuntu said it couldn't mount it.  I rebooted the machine and it now said the same thing on my Win7 install, that there was no OS found.  Thing is when using boot-repair I went exploring the advanced options and I now remember listings regarding MBR and windows boot.  I think I messed with one too many settings and now I can't boot into Windows or Ubuntu regardless of any BIOS settings.  While I don't claim to fully understand grub and boot loaders in general I do understand the basic functions.  It's my assumption that something happened on both drives and now the boot loader/s are missing/corrupt/etc and not pointing to the installed OSs.

A few things..
Windows boots directly to Windows Error Repair.  Nothing I do in there helps.  I can run a command prompt but it's been so long (win 3.1) since I've messed with command prompt I wouldn't even know what commands would be helpful.  As in other posts I get mentions of "GPT partition style" which I'm not familiar with what this is.  Also when I try to auto repair the boot it says "Failed to save start up options" and at some point mentions a missing 1mb partition I think?

Weapons in my arsenal:
Flash drive with Ubuntu 11.10 installed on it (it's how I'm on the Internet now and how I initially installed Ubuntu)
Windows 7 install disc (I've booted from this and can't fix boot)
Windows 7 backup on my external (it's an image from mid March, I don't want to use this unless totally necessary, I will loose personal files from the time in between and no saying that this will fix anything.  I'm still convinced it's just a boot loading problem.)

I'm sorry for the epic story.  I figure everyones story is unique and perhaps someone can help me shed some light on this.  I can stand to lose and reinstall the Ubuntu, Win 7 however has a lot of the wife's homework.. /gulp

If there are any reports I can run and post please let me know.  Huge thanks in advance.
Cheers!

---

### Post by Bouvet on 2012-05-03
I am new to 'very new' to Linux as well.
I hope someone has an answer, I'd like to read more.

---

### Post by BlastXng on 2012-05-03
Unfortunately it won't be the easy to recover.. Basically Ubuntu has hosed you and lots of other people (including myself) with the update to 12.04. ](*,)

To get back to your Windows working, I'd suggest you download and burn Hiren 15.1 CD.. It has partition tools that can remove grub (which is what Ubuntu probably did and screwed you over in the process) edit grub and redo your MBR. 

If you have the Windows 7 Boot CD, you can boot into the command prompt of it and there are commands that will allow you to rewrite the MBR.. These are all over the web and on the ms support site.. At least you'll be able to run Windows 7.. 

Ciao

---

### Post by darkod on 2012-05-04
Lets not jump into conclusions what will be easy or difficult to recover.

First of all, first chance you have, create another usb stick (or the same one) with 12.04. You should always have a copy of the system you are running, since best repairs are done with the same version.

Having said that, 11.10 will do for a start.

You can follow the link in my signature to run the boot info script, but since you had already used boot-repair it might be easier to do it that way. Boot-repair has a button to run the boot info script and will give you a link to the results. Post that link here so we can see what is where.

---

### Post by Mimalito on 2012-05-05
Thanks for getting back to me.  I do not have 12.04 on a flash drive, but I do still have the 11.10.
I'll see about getting the log from the boot-repair.  Just wanted to respond to let you folks know I'm still looking for help.

Cheers

---

### Post by Mimalito on 2012-05-05
Is this what we are looking for?

[http://paste.ubuntu.com/970180/](http://paste.ubuntu.com/970180/)

---

### Post by darkod on 2012-05-05
I guess you ran the script with the external disconnected because it's not shown.

You are using gpt table on your disk, and EFI boot. At least it seems so.

I think there is a bug in grub2 when you are trying to use a dual boot, and it overwrites the windows boot files on the efi system partition.

On top of that it seems there is a broken grub2 on /dev/sdb.

You should be able to fix your windows boot but you have to boot the windows disc in EFI mode too, not in the older type BIOS mode. Refer to your board manual if you need help with that, I have very little experience with EFI. That should make your windows work independently of the external disk.

---

### Post by Mimalito on 2012-05-05
So sorry! just noticed that..  oops

here it is again with external on

[http://paste.ubuntu.com/970268/](http://paste.ubuntu.com/970268/)

---

### Post by darkod on 2012-05-05
With the external connected, and a 12.04 cd in live mode, install grub2 to /dev/sdd (your ext disk):
sudo mount /dev/sdd5 /mnt
sudo grub-install --rot-directory=/mnt /dev/sdd

That will take care of the bootloader for the ext disk.

You will still need to run the win7 dvd in EFI mode and repair the boot. Since you use EFI boot for windows, you need to boot the dvd in EFI mode too.

On the other hand, the installation of ubuntu seems for normal boot, so I am bit puzzled how are you actually booting your computer.

---

### Post by Mimalito on 2012-05-05
Thanks for the info, I'll have to look into this EFI thing since I'm not familiar with what you re talking about.

Also when I do boot from the Win7 disc it says it detects problems but can't solve anything because the Win7 recovery mode doesn't see my SATA drive to initiate the repair.  Perhaps the EFI thing you are talking about will help out?  I'll look into it.

---

### Post by Mimalito on 2012-05-05
follow up on the commands for my ext drive..

"sudo grub-install --rot-directory=/mnt /dev/sdd" 

Was this supposed to say "root" directory? If so...
Am I supposed to be actually typing "root directory"? or are you telling me to type my root directory.  If so I'm not sure what I'm supposed to put there.  I'm sorry.  I really am a novice at Linux

Also I'm not sure how to/if booting in EFI mode is an option for me?  I did some searches and looked at my boards documentation and couldn't find any reference to it.  I'm using a MSI 890GXM-G65 if that helps any.

---

### Post by darkod on 2012-05-05
Sorry, typo. Yes, the option used is --root-directory, use it exactly as it says:
sudo grub-install --root-directory=/mnt /dev/sdd

---

### Post by Mimalito on 2012-05-05
Ok.  I think that worked.  I guess I'll have to wait and see if I can boot to it.  So... boot to Ubuntu 12.04 might be fixed.

Still not sure on this EFI thing

I really appreciate your zen like patience

---

### Post by Mimalito on 2012-05-07
Here is my latest boot-repair log.

[http://paste.ubuntu.com/972961/](http://paste.ubuntu.com/972961/)

I've been offline for a whole day because for some reason even my Ubuntu flash drive stopped booting.  I'm back up using a newly loaded Ubuntu 12.04 live flash drive as suggested and ran the commands listed a few posts back.  

I also looked into booting in EFI mode.  I'm still not really clear but found an option in my BIOS to for IDE, RAID or AHCI.  Some Win7 forum posts mentioned EFI and AHCI in the same sentence so I assumed they were similar.  For the first time when running windows repair from my CD it actually found my windows install and called it Windows 7 Home (recovered) on (unknown) local drive.  I can attempt an auto repair but it always fails with a long list of "Problem Signatures" with #7 being missing boot manager.  I tried all sorts of command line commands to no avail.

So I'm not sure where to go now?  Can I use boot-repair within this 12.04 live USB to repair the windows boot manager?  Can I delete something and install a different boot manager to start windows?

I'm really over my head here and my wife had homework she couldn't do this weekend.  Yikes. 

Husband broke the computer is the "new" dog ate my homework.

---

### Post by darkod on 2012-05-07
No, EFI (or UEFI) and AHCI is not the same.
IDE, AHCI or RAID are the modes available for the sata controller/ports. IDE is the older type, for backwards compatibility if you are installing XP for example. AHCI is most commonly used these days unless you want to create raid in which case you use RAID.

UEFI is also a new standard about booting. The older type which lasted for decades is usually called just BIOS boot. I'm still unclear about UEFI myself, but so far I don't see any benefit, only problems.

Since in the results you can see that the windows disk has the EFI System Partition on it, it is logical to assume you are/were using EFI boot, not BIOS boot. Even if you find where to change it in BIOS, I'm not 100% sure windows can contonue working because in most cases it doesn't want these options changed once it is installed. On the other hand, you might be able to simply repair the windows boot process much easier with BIOS boot.

For more details about that, I think a windows forum is the better place. You have ubuntu on a separate disk, so it's much easier to fix the windows boot, ubuntu is not in your way. One thing is for sure, EFI is not AHCI, it's not the same. Look around in the BIOS options for UEFI enable/disable or in your board manual. If you find an option like that, consult the windows forum will it keep working if you disable UEFI and try to repair the bootloader.
The board might not even have the option to disable UEFI. It seems you can do it on some, and not on others. It's so new I don't really have a clue and I'm far from using it.

Even if this situation is a consequence of the ubuntu upgrade, there is no reason why windows wouldn't be able to repair itself. That's strictly up to windows and its repair process.

---

### Post by Mimalito on 2012-05-07
I agree that regardless of what caused the boot issue that I'm heading into Microsoft waters here.. 
I'll probably receive more insight on a MS problem from such a forum.  

And I'll have to look more into this EFI issue.  I don't remember seeing anything like that in the bios but I'll have another look.  I'm weary of messing with settings I don't understand.  

When this is all fixed, said and done I'll be back for more Ubuntu help.  I still want to use and learn this operating system.  Thanks for all the help.

---

