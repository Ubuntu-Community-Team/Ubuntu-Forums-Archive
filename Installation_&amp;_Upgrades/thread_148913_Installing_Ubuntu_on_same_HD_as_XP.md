---
title: "Installing Ubuntu on same HD as XP"
date: 2006-03-22
forum: Installation &amp; Upgrades
---

### Post by Aggort on 2006-03-22
So, I've never installed a Linux OS on a computer, or even betetr yet, I have never installed 2 OS on 1 computer. I have a 150gb hard drive and a gig of memory. How hard or safe for that matter would it be to install Ubuntu on the same HD? (since I only have one) Could you possibly walk me through it? Please and thank you!

---

### Post by Qrk on 2006-03-22
It is safe provided you take the following precautions:

1) Defragment your Drive in windows and run disk cleanup wizard first
2) Backup crucial data --- just in case.

Then you can put the ubuntu cd in, reboot and install like normal. Ubuntu's partitioning tool isn't graphical, but it is resonably easy to use.

You should see the partition when the installer gets to the partitioning step, it should be the first option, (hda1 on IDE master, ~150 GB) and you can resize it to your desired size.

Ubuntu should take care of the rest. Be sure to read what the installer is going to change before the final OK.

---

### Post by Aggort on 2006-03-23
OK, what about booting? I don't want to dual boot, but will it allow me to select what operating system to boot? I want to use Linux, but my mom uses the same PC so I need her to be able to boot to XP. My friend says that just installing won't allow me to do this and that it will mess up my master boot record(MBR). Is this true?

---

### Post by Aggort on 2006-03-23
Can't Anyone Help? please? lol

---

### Post by KansasJoe on 2006-03-23
You have to dual boot if you want both options....load up the cd and it will take you to the partitioner after a couple of steps....manually edit partition tables....take away however many gigs from xp you want to....create new ext3 partition labeled / and another swap partition (may want to create /home as well but is optional) that's it...follow directions from there and install grub where it defaults to since you only have xp and linux....good luck....p.s. if you don't want to dual boot then look into vmware or something similar but it's really not that hard to dual boot and whatever your mom does she can probably do on linux as well unless she's a gamer....lol...when you restart it will have option to boot to ubuntu or windows and you can change the order in /boot/grub/menu.lst

another note...you can make the partions primary unless you're gonna install more os's then you'll have to start making those extended....fine if xp and ubuntu will be only os

---

### Post by barthel on 2006-03-23
[QUOTE=Aggort]OK, what about booting? I don't want to dual boot, but will it allow me to select what operating system to boot? I want to use Linux, but my mom uses the same PC so I need her to be able to boot to XP. My friend says that just installing won't allow me to do this and that it will mess up my master boot record(MBR). Is this true?[/QUOTE]

Although it sounds like booting both at the same time, the phrase "dual boot" means that you can start either system.

Ubuntu's installation script will add a line for booting into the MS-Windows OS. It does ask for confirmation first, but Ubuntu does take care of it for you.

As far as "messing up the master boot record" goes, it is true that Ubutu's installation script will ***change*** the MBR. ("Messing it up" is a matter of interpretation: from Microsoft's perspective, anything that is not sanctioned by them is "messed up".)

I'm sure that others who are more familiar with GRUB (the boot loader) can give you more specific help on configuring it to default to Windows XP to make it easier for your mother.

But I can assure you that Ubuntu does handle it cleanly and safely. There's always a certain amount of risk when you're modifying the boot process, but I had no problems whatsoever with my installation of Ubuntu coexisting with the WinXP on my laptop.

---

### Post by aysiu on 2006-03-23
These two links have everything you need:

[http://users.bigpond.net.au/hermanzone](http://users.bigpond.net.au/hermanzone)

[https://wiki.ubuntu.com/GrubHowto/ChangeDefaultOS](https://wiki.ubuntu.com/GrubHowto/ChangeDefaultOS)

---

### Post by Aggort on 2006-03-23
OMG you guys Rock. Thank you so much for the help!

---

### Post by Aggort on 2006-03-27
Well I have some big problems. XP will not boot at all. It will load into GRUB, as will Ubuntu, but it will not completely boot, instead it just restarts the PC after a blue screen flashes for a millisecond. Ubuntu boots to the login screen. After logging in the desktop won't load. The usual splash load screen doesn't appear and there are no icons, no toolbars, no background image, just a tan/brown background and a mouse that does nothing. So, I need some help. I am sure it is my MBR, and I have an MBRfix.exe I might try that, but any help will be useful. Please HELP! I need XP for school.

---

### Post by aysiu on 2006-03-27
Well, let's take the problems one at a time.

First of all, the Ubuntu brown screen with cursor... sounds as if it might be a graphic configuration / screen resolution issue.

Try pressing Control-Alt-F1. This should get you to a black screen with some white text. Log in. Then type ```
sudo dpkg-reconfigure xserver-xorg
``` You'll be asked some questions. Answer them as best you can. If you don't know the answer to a question, go with the default. When that's done, type ```
exit
``` and press Control-Alt-F7 and then Control-Alt-Backspace.

If that works, that's one problem.

The second problem is "needing" XP for school. What exactly do you need? The programs? The files? If it's just the files, you can use Ubuntu to mount the Windows partition and get the files from there (I'm assuming you need something to open Microsoft Office files, and OpenOffice can do this--if you have something more complicated like MatLab or Adobe InDesign, then... well, say so, and we'll try to figure out something).

If it's just a matter of having access to the files, follow this tutorial:
[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

The last problem... unfortunately, I don't know much about fixing problems with Grub not booting to Windows, but someone else may be able to help you if you post the output of these two commands: ```
sudo fdisk -l
cat /boot/grub/menu.lst
```

---

### Post by Aggort on 2006-03-27
Unfortunately I need Windows for the specific programs. I already can acess my files using other linux distributions so thanks, but I do know that much lol. I'll definitely try out the commands for the screen, the problem is, when I tried anything before it seemed as if my keyboard weasn't responding. However, I never tried Control-Alt-F1. Hopefully it works out, becuase even without Windows runnign  or if I egt it fixed, I want to run ubuntu! As for the last bit, I don't think  it's so much GRUB not booting XP, rather XP not liking GRUB or I may have screwedup the partition? Is that even possible? Anyway, thanks for the help with Ubuntu, I'll try what you gave me and I'll be sure to reply back.

---

### Post by aysiu on 2006-03-27
It's not unheard of that this sort of thing happens, but it's not the usual situation either.

If you definitely need those Windows programs, go ahead and use a Windows CD to restore the MBR to Windows:

[http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/bootcons_fixmbr.mspx?mfr=true](http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/bootcons_fixmbr.mspx?mfr=true)

After you've done what you need to do, and once you have some time to troubleshoot in case it doesn't work, try reinstalling Grub:

[https://wiki.ubuntu.com/phbc50/howtos/how-to_reinstall_grub](https://wiki.ubuntu.com/phbc50/howtos/how-to_reinstall_grub)

---

### Post by Aggort on 2006-03-28
A friend of mine suggesed the fact that it might be my NTFS partition being ruined. Possible? And the commands you gave me worked, but the desktop still froze at the same point! So, I'm still short an OS!

---

### Post by Aggort on 2006-03-29
Bump

---

### Post by Sef on 2006-03-29
You probably just need to reset GRUB.  Don't have the time to search now for it...but just do a search in here.  This has been discussed before.

---

### Post by Aggort on 2006-03-30
I had already reset GRUB, it wasn't that anyway. I fixed my MBR and rid of Ubuntu off my hard drive. I deleted every other partition and made sure NTFS filled up my hard drvie again and now my PC is fixed. I am gettign a second hard drive to install Ubuntu on, so I'm good. BUT, I need help getting Ubuntu to boot. It still has the problem with hanging at the brown screen. Even if I installed it on my new Hard Drive, it would still hang, so please help me to get Ubuntu to boot!

---

### Post by Aggort on 2006-03-31
OK, I just need help booting Ubuntu, I have it installed now, but I still need help!

---

### Post by insane_alien on 2006-04-09
wow just followed the tutorials on this thread and got ubunto working first time and with no problems in windows. this rocks

---

