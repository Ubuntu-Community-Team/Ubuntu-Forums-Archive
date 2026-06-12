---
title: "Dual boot questions"
date: 2005-06-16
forum: Installation &amp; Upgrades
---

### Post by Jere on 2005-06-16
Hello there everyone. I am just as new to this forum as I am to Ubuntu Linux.

I have a 120 GB hard drive with a ~4.7 GB partition where I have Mandrakelinux 10.1 installed. The rest is WinXP Pro... Mandrake has installed LILO to take care of my dual booting. As far as I know, LILO has taken over the MBR.

Now, I'm not too fond of Mandrake (or Mandriva as it is called now) not only because I cannot get it to connect to the internet. So I want to try out Ubuntu but I want to be sure Windows stays intact. I have heard there are certain issues with GRUB, the MBR and Win 2000/XP, which could prevent Windows from working.

I've been thinking of what to do and read some howtos, including the Ubuntu wiki. I think I firstly need to get rid of LILO, meaning get Windows to rewrite the MBR so that my computer automatically boots into Windows. Then I'd install Ubuntu and opt not to rewrite the MBR to boot into GRUB. This should leave me with Ubuntu installed but with a computer booting directly into Windows. AFAIK, I can then edit boot.ini in Windows to bring up a dual boot menu allowing me to boot Ubuntu.

Tell me, is this a good idea, is it possible, and how do I do it? Particularly how do I make Windows restore the MBR?

Thanks in advance :)

---

### Post by lorenzo on 2005-06-16
Hi,
I've been using dual booting windows/linux for long now. I have always let linux set the MBR. Both lilo and grub works well. I have installed ubuntu with grub and I've had no problems at all.
I thik you better set grub/lilo to chose the OSs. I suppos that when you install ubuntu it will overwrite lilo.

To set again the win MBR before installing linux: [http://www.microsoft.com/resources/documentation/Windows/XP/all/reskit/en-us/Default.asp?url=/resources/documentation/Windows/XP/all/reskit/en-us/prkd_tro_ldau.asp](http://www.microsoft.com/resources/documentation/Windows/XP/all/reskit/en-us/Default.asp?url=/resources/documentation/Windows/XP/all/reskit/en-us/prkd_tro_ldau.asp)

1) enter in recovery console 
2) execute fixmbr command

Ciao,
Lo

---

### Post by Jere on 2005-06-16
[QUOTE=lorenzo]Hi,
I've been using dual booting windows/linux for long now. I have always let linux set the MBR. Both lilo and grub works well. I have installed ubuntu with grub and I've had no problems at all.
I thik you better set grub/lilo to chose the OSs. I suppos that when you install ubuntu it will overwrite lilo.

To set again the win MBR before installing linux: [http://www.microsoft.com/resources/documentation/Windows/XP/all/reskit/en-us/Default.asp?url=/resources/documentation/Windows/XP/all/reskit/en-us/prkd_tro_ldau.asp](http://www.microsoft.com/resources/documentation/Windows/XP/all/reskit/en-us/Default.asp?url=/resources/documentation/Windows/XP/all/reskit/en-us/prkd_tro_ldau.asp)

1) enter in recovery console 
2) execute fixmbr command

Ciao,
Lo[/QUOTE]
 Ok. I suppose if Linux messes up the MBR I could always recover it from the XP installation CD? It's just problematic because I don't have the CD... So I'm actually using XP illegally, just another reason to move to Linux isn't it :D

I will obviously backup my files but having to reinstall Windows would still be a pain in the ass because of all the reinstalling of everything. I'd still need Windows for some stuff even if Ubuntu turned out to work perfectly also with the internet connection. I could probably not reinstall XP either so Win2000 would have to do.

I'll have to see what to do... The Mandrake installation was problem free, though it installed LILO not GRUB. I hope GRUB doesn't fail on me... or does Ubuntu come with LILO too? On the other hand, I've heard GRUB is easier to deal with when upgrading.

---

### Post by jsuen on 2005-06-16
[QUOTE=Jere]Ok. I suppose if Linux messes up the MBR I could always recover it from the XP installation CD? It's just problematic because I don't have the CD... So I'm actually using XP illegally, just another reason to move to Linux isn't it :D

I will obviously backup my files but having to reinstall Windows would still be a pain in the ass because of all the reinstalling of everything. I'd still need Windows for some stuff even if Ubuntu turned out to work perfectly also with the internet connection. I could probably not reinstall XP either so Win2000 would have to do.

I'll have to see what to do... The Mandrake installation was problem free, though it installed LILO not GRUB. I hope GRUB doesn't fail on me... or does Ubuntu come with LILO too? On the other hand, I've heard GRUB is easier to deal with when upgrading.[/QUOTE]
 you should be able to hit the recovery console for WinXP, even if your installation CD is illegitamite (i think, not 100% sure. i guess if you can detect it on your install from boot then it should be ok). alternatively you can look around for system restore sites that offer downloads you can run should you need to restore the MBR.

i think you can choose to use lilo instead of grub, it's been mentioned on these forums (somewhere) before... my install worked off the bat with GRUB so i'm happy (and lucky, looking at some of the problems i've read about!)

cheers

jon

---

### Post by Jere on 2005-06-16
[QUOTE=jsuen]you should be able to hit the recovery console for WinXP, even if your installation CD is illegitamite (i think, not 100% sure. i guess if you can detect it on your install from boot then it should be ok). alternatively you can look around for system restore sites that offer downloads you can run should you need to restore the MBR.

i think you can choose to use lilo instead of grub, it's been mentioned on these forums (somewhere) before... my install worked off the bat with GRUB so i'm happy (and lucky, looking at some of the problems i've read about!)

cheers

jon[/QUOTE]
 As I said, the problem is that I don't have the CD at all. If I'd lose my Windows, I only have Windows 2000 to install. Not that I dislike Win2000, I find it better in some manners, but I would really not like going through the trouble of reinstalling all my programs.

It seems now that I will install GRUB and let it fiddle with the MBR. I don't know yet when I will go for the installation though; I need to get some things ready first. It's best to wait a while too in case someone has something to say on this regard.

---

