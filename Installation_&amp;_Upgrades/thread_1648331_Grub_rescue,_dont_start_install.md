---
title: "Grub rescue, dont start install"
date: 2010-12-18
forum: Installation &amp; Upgrades
---

### Post by Anaximadros on 2010-12-18
Hi, here is my problem i am trying to install ubuntu 9.04 in a desktop but when loading the first screen it appears a box writing somthing "vmlifuz" the only choose that have is "ok" when i am hit button "ok" does not working, if a press it again (when the box with the ok disappears) load the dialog saying "Try ubuntu" , "install ubuntu" etc. Then if a hit one of this the dialog comes again saying something about "live-install" i hit ok but this time not process in the installation. After that I had try to intall windows xp but when go to load kernal prompt a message could not load a setupdd.sys. I had try to install Linux mint after the starting screen says ready and then nothing , i had try to install fedora only running the cd without even a message only a black screen. At last i had install ubuntu to another pc and i took the hard disk and plug it to this one, when i power on the pc after bios info in the screen come this "grub rescue>" any idea what the problem and how can i fix it ?[-o<

---

### Post by sikander3786 on 2010-12-19
Welcome to the forums :-)

Your post is a pretty complicated one and I accept I couldn't understand whole of it.

> At last i had install ubuntu to another pc and i took the hard disk and plug it to this one, when i power on the pc after bios info in the screen come this "grub rescue>" any idea what the problem and how can i fix it ?

Do you mean you took the HDD that had Ubuntu installed to it and placed it in another system? If yes, there might be 2 HDDs in that system and Grub (Ubuntu bootloader) might have been installed to one and Ubuntu to the other so you are getting a Grub> prompt.

If you mean you took out the Ubuntu HDD from that PC and connected the other HDD to that for installation and you got a Grub> prompt, were you booting from the proper device then? I mean the Ubuntu Live CD or USB?

If none of those, please elaborate your problem.

Thanks.

---

### Post by theasprint on 2010-12-19
Hi, 

For your first attempt (about installing Ubuntu), you mentioned 
> but this time not process in the installation

From my Point of View, I think is it that your PC is not displaying anything on the screen?

And there seems to be problems installing Win XP, Linux Mint and Fedora

I think my best elaboration could be that while you were installing Ubuntu during your first installation, you deliberately CANCELLED the installation upon seeing that there is "no process in the installation"

And then for the subsequent installations, all failed because perhaps grub was PARTIALLY installed in your PC.

Here: [https://help.ubuntu.com/community/Grub2#Using%20CLI%20to%20Boot](https://help.ubuntu.com/community/Grub2#Using%20CLI%20to%20Boot)

Hope this link helps to solve your human-computer stalemate!

*Sorry, I am not an expert in facing grub-rescue issues. But I am sure I  have met some more users who have the same issue in other threads. Keep  a lookout for them! And, yes, I also gave them this link.

*Tip, perhaps try to be less HASTY in facing installation problems.

Perhaps a clean install with everything reformatted would help?

---

### Post by Anaximadros on 2010-12-19
First of all thank you for the comments, and i am sorry for the way tha i wrote that text. I was pretty confused and i didn't realize it. My problem solved very easy, i just plug the RAM to another slot of motherboard and the installation of ubuntu 10.04 finished successfully. :D

---

