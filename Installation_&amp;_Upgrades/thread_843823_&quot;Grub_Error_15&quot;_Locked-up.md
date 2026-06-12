---
title: "&quot;Grub Error 15&quot; Locked-up"
date: 2008-06-28
forum: Installation &amp; Upgrades
---

### Post by DMAnthony on 2008-06-28
Hi,

I had been having some problems with my copy of Kubuntu, so I decided to format it's hard drive partition and then reinstall. My other partition has Windows XP installed on it.

Once I formatted the Kubuntu partition and tried to reboot into XP, all that my laptop would do is display:

---------------------------------
GRUB Loading stage1.5.

GRUB loading, please wait...
Error 15
---------------------------------

I have tried searching the internet for hours without a solution. :confused:  The only keys on my keyboard that seem to do anything now are CTRL+ALT+DEL, which brings me back to the same screen.

If anyone can help me get my computer running again, I will be much obliged.

Darren.

---

### Post by unutbu on 2008-06-28
Have you reinstalled Kubuntu, or have you only reformatted the Kubuntu partition?

---

### Post by logos34 on 2008-06-28
> **unutbu said:**
> Have you reinstalled Kubuntu, or have you only reformatted the Kubuntu partition?

grub stage1.5 is looking for menu.lst on the (reformatted) kubuntu partition...you won't be able to boot back into windows until you reinstall kubuntu or restore the windows bootloader

---

### Post by DMAnthony on 2008-06-29
> **logos34 said:**
> grub stage1.5 is looking for menu.lst on the (reformatted) kubuntu partition...you won't be able to boot back into windows until you reinstall kubuntu or restore the windows bootloader

Thanks for the advise. I just removed my hard drive from the laptop so that the kubuntu disk could boot-up, but when I try to reinstall kubuntu, my hard drive is not found.

I will now try using my windows install cd to see if that can help me out. I will let you know what happens.

---

### Post by mbarvian on 2008-06-29
Try booting from the Windows XP CD, then press R to repair installation, then type in fixmbr to fix the MBR so that you can boot into XP, and then re-install Kubuntu.

---

### Post by DMAnthony on 2008-06-29
I was unable to get Windows XP to boot, but I am able to reinstall it. Once I get Windows XP installed again, I will be able reinstall Kubuntu.

---

### Post by DMAnthony on 2008-06-29
> **DMAnthony said:**
> I was unable to get Windows XP to boot, but I am able to reinstall it. Once I get Windows XP installed again, I will be able reinstall Kubuntu.

I got Windows XP installed successfully, but it too will not boot-up. I now got a new error:

---------------------------------
GRUB Loading stage1.5.

GRUB loading, please wait...
Error 22ÿ
---------------------------------

---

### Post by logos34 on 2008-06-29
it seems windows failed to overwrite grub on the mbr with its own bootloader

hmm...check your Bios settings (maybe you have a feature called write-protect or AV for mbr--disable it)

---

### Post by DMAnthony on 2008-06-29
> **logos34 said:**
> it seems windows failed to overwrite grub on the mbr with its own bootloader

hmm...check your Bios settings (maybe you have a feature called write-protect or AV for mbr--disable it)

ummm... :? no such setting is available.

---

### Post by logos34 on 2008-06-29
ok, just a guess.

What about the hard disk detect setting? (maybe it got changed)

---

### Post by DMAnthony on 2008-06-29
I have stumbled upon something that seems promising. 

RecoveringUbuntuAfterInstallingWindows
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

I'm not totally sure if this has fixed my problem fully, but it is allowing me to boot into Windows XP. Since I reformatted XP, I will have to wait until I go through it's setup nonsense.

---

### Post by DMAnthony on 2008-06-29
> **DMAnthony said:**
> I have stumbled upon something that seems promising. 

RecoveringUbuntuAfterInstallingWindows
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

I'm not totally sure if this has fixed my problem fully, but it is allowing me to boot into Windows XP. Since I reformatted XP, I will have to wait until I go through it's setup nonsense.

:guitar: Okay then, I got my laptop booting into XP all by itself now. I downloaded an ISO from the RecoveringUbuntuAfterInstallingWindows website and burned it to a CD. Using that CD, I managed to restore the Windows boot manager. If only I could have found this before reformatting Windows XP.

:?: Before I reinstall Linux again, which distro is best :?:

---

### Post by logos34 on 2008-06-29
> **DMAnthony said:**
> :guitar: Okay then, I got my laptop booting into XP all by
itself now. I downloaded an ISO from the RecoveringUbuntuAfterInstallingWindows website and burned it to a CD. Using that CD, I managed to restore the Windows boot manager. If only I could have found this before reformatting Windows XP.

I wonder why Super Grub Disc succeeded where 'fixmbr' failed from the XP cd...it does the exact same thing. hmm

---

### Post by upchucky on 2008-06-29
google for supergrub, the original problem was the master bootloader did not know where the reinstall went, and now it is confused cause windows did not overwrite it either.

they are both still there unless you repartitioned, but now grub needs to know where the bootloader is.

supergrub can fix this, and can fix windows bootloader too.

there are instructions that do need to be understood so read carefully.

---

