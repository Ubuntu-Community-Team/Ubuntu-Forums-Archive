---
title: "First timer here with a failed installation"
date: 2008-10-03
forum: Installation &amp; Upgrades
---

### Post by dmfagan9 on 2008-10-03
Hi All-
I just attempted my first ubuntu installation and it did not work. I downloaded 8.04, did the check md5 sums, defragged my windows hard drives, restarted my computer with the CD in and the first prompt was a full screen language page. Clicked English and then arrived at a menu with 5 or so options- the first being install ubuntu. I pressed enter and then got a small prompt saying that a linux kernel was being installed. the measure quickly went to 100% but then just remained there for a long time, the computer locked and i wasnt able to get into the F1 help or F4 options. I restarted the computer and tried again and arrived at the same kernel window. I left it for longer and it went into a dos prompt screen (i think) and I received this message

SQUASHFS error: sb_bread failed reading break oxa6ec9
SQUASHFS error: unable to read cache block
SQUASHFS error: unable to read inode.

Don't know if this bit of information is helpful but I had a bit of a windows installation problem last week. The first time I installed windows it loaded on the small C drive and made it so that the large 150 gig drive was inaccessible. I reloaded windows onto the large drive and thus the large drive was avaliable for all its space. Each time i restarted my computer i got a prompt asking which OS to use and there were 2 windows options- old and new one. Right before I tried installing ubuntu, i deleted the windows program files from the C drive which I was not using. Don't think that should be an issue but might be of use to someone who knows better. As it should be obvious from this post- i know very very little about computers but a friend who works in programming has been trying to get me onto ubuntu forever. Just got a new laptop and thought its worth a shot.

Does anyone have any ideas about how I should proceed? Thanks so much for your help

Dylan

---

### Post by cariboo on 2008-10-03
Have you tried running the disk integrity check, I believe it is the third choice in the menu.

Jim

---

### Post by dmfagan9 on 2008-10-03
The CD check came up with 20 errors in only doing about 1/3 of the scan. I did the md5 check sum which said that the files were correct. Does this mean that I should try burning with a different sort of CD? Or do I have to download ubuntu again? Thanks a lot

---

### Post by Idefix82 on 2008-10-03
Try burning the CD at a very low speed, like 4x. That minimises the chance of errors.
After that, please tell us where you want your Ubuntu to go, whether you want to replace Windows altogether or whether you want to have the option of booting windows or Ubuntu when you switch on the computer. I am saying this, because I am not sure you picked the option you wanted during the installation.

---

### Post by ZhuaSD on 2008-10-03
So the disc integrity check does not complete after 1/3 of the scan?  Or what?

You may want to get a new install disk if its not too difficult, with so many errors on check.

For your windows, you may have created a problem for yourself.  I don't know how it will affect the Ubuntu install, but I want to point it out.

If I am not mistaken, the second install of Windows recognized the first one, and therefore set itself up as a secondary installation.  The reason you had two windows install options upon boot up is that the second install wrote to the boot.ini file of the first install.

If you deleted the windows files such as the boot record from the first install you will not be able to boot to windows anymore.  Once Ubuntu is up and running all your files will be there, and you can recover those Windows installs I believe.

I am still new to Ubuntu myself so I will not say more and risk taking you in the wrong direction.  Good luck!

---

### Post by dmfagan9 on 2008-10-03
I am burning right now at 4X. I am a bit confused about the dual boot- I do want to have a dual boot option. I have read the wiki (chapter 4, 7) about the different partitions that are required but I never arrived at the first screen that  the wiki says:

Once the Ubuntu installation CD has booted successfully, you will be presented with a desktop, with an icon labelled Install. Double-click this icon to start the Ubuntu installer

Does this come after the menu with the 5 options 1 being install and 3rd being check cd integrity? Thanks

---

### Post by dmfagan9 on 2008-10-03
The windows boot (2nd one) still works- or it seems to be ok- that what I am working on right now- but the 1st one still appears in the dos prompt start up screen when i dont have the ubuntu disk in- so i still have to press enter to boot it.

---

### Post by ZhuaSD on 2008-10-03
Ok so you didn't create a big problem for yourself I think.  I did that once, deleted the boot file because I thought the second install was a stand-alone one, and, ha ha, it wasn't ;-)

I don't exactly understand exactly what's going on with your Windows, but its not too important right now, it might matter later when you are configuring your dual boot system.  I guess you are only going to want one Windows install, but that's really up to you.

Yes the desktop with the language question and install and other options and so on is what that means.

When Unbuntu installs, it is hopefully going to recognize the windows installations and provide you with dual boot capabilities right away.  

Certainly the grub loader (boot loader basically) will look for those installations and IF it can get the right booting data it will offer the boot options to Windows.

So basically what that means is that you might have to change your grub loader data, but again that's after your install.  Let's see if the new disc works.

---

### Post by dmfagan9 on 2008-10-03
Same problem- I went to the menu of check for cd integrity it gets to 20% of linux kernel created and then freezes. Is this a CD burner issue? The md5 check was OK. Do I have to download again? I am in indonesia right now and getting sent CDs will take many weeks I fear. Ok thanks for all of your help

---

### Post by ZhuaSD on 2008-10-03
Do you use a torrent client?  Even if your speed isn't great you could d/l overnight or within a day basically. The files are only 700 MB or so.

I searched for ubuntu torrent download and found lots of sites to use.  One choice is this one: [http://releases.ubuntu.com/8.04/](http://releases.ubuntu.com/8.04/)

I can only assume the install file you got is corrupt, maybe there is a way to salvage it but I don't know how.  Its possible that its a cd burner issue but I can't imagine the md5 check would be ok then.  If it was a cd burner issue I believe you can just put the installation file on a pen (flash, external) drive and boot from that drive to install. That's a little tricky but not too bad.

You might want to start a new thread with this specific question, if you can't find an answer in the forums.  Something like "MD5 check good, disc integrity check fails, install fails: Bad distro or bad burner?"

Maybe while you are d/ling the torrent at the same time. ;-)

---

### Post by miegiel on 2008-10-03
Your cd-writer might be dirty or so old that the laser can write disks properly anymore.

Try cleaning your cd-writer or copy the ubuntu iso to a usb-stick or external disk and burn the cd on a other pc.

> Once the Ubuntu installation CD has booted successfully, you will be presented with a desktop, with an icon labelled Install. Double-click this icon to start the Ubuntu installer

The top option in the menu after the language selection lets you boot ubuntu from the cd without installing it. That's what they are talking about in the quote.

---

### Post by dmfagan9 on 2008-10-03
The computer is brand new so maybe I should go for the USB boot? A little bit intimidated by BIOS. Do you have to do anything besides change the boot lineup to say usb first? and then do I have to switch it back later? Thanks

---

### Post by ZhuaSD on 2008-10-03
You might get lucky and your bios is configured to check for a usb drive before your hard drives.  Throw the iso on a usb drive and try it.  If you have multiple usb ports you could try all of them.

If you need to mess with the bios, its not hard, just a little intimidating.  The bios is the part that you first see when you start up, and it will always say 'click [esc, or F8 or delete or something] to enter settings'. If you do that you just tab through the options to boot order, and move the usb port up.  That just tells the bios (the most basic part of your computer) to *first* look to the usb drive port for a bootable system.  You will also notice that the cd-rom is set to be checked first, that's why the live disc boots up instead of your windows 2-install load up page. First bootable system in the order loads, the rest do not  ;-)

---

### Post by ZhuaSD on 2008-10-03
Oh I read miegiel wrong, I am not sure exactly how to make a pen drive that can be used to install from.  He said load it on a pen drive and burn on another computer, I thought he said just load it from the pen drive directly...

ah yes, it is a little involved, you have to make the drive bootable:

[http://www.teamteabag.com/2008/05/17/howto-easy-install-ubuntu-804-hardy-heron-or-most-other-distros-from-usb/](http://www.teamteabag.com/2008/05/17/howto-easy-install-ubuntu-804-hardy-heron-or-most-other-distros-from-usb/)

At the bottom of those instructions it mentions the boot order step that I wrote about above

---

### Post by miegiel on 2008-10-03
If the bios finds no bootable device on the 1st option the will try the 2nd and after that the 3rd, etc. If you don't have a bootable usb device permanently connected to your pc you won't need to change it back if your harddisk is the 2nd boot option.

Don't let the bios intimidate you, just change 1 option at the time so that if you do something wrong you still remember what change is causing the problem. there&#347; also a option to restet the bios to it's default values.

I'd still try burning the cd with a other pc/writer. If I'd want to know if my writer is causing problems I'd burn an ubuntu cd and test it for errors :D (still I'd have to be 100% sure there's nothing wrong with the image 1st)

---

### Post by ZhuaSD on 2008-10-03
Brand new laptop, so you would want to know sooner rather than later ;-)

Interesting that both discs you burnt of the same image had the same type of error and failure.  If there are some small write errors that are leaking in, so that the md5 checks out but the disc has so many errors, would the result be just the same both times?  I would think image corruption is more likely than burner failure.

If you don't have another burner then you could download another iso image and try to burn that.  If both images don't burn right then the burner is looking pretty shady.

Also keep in mind that if the image you have is corrupt then a bootable drive will not help you, because it will just hit the same problem and freeze up.

---

