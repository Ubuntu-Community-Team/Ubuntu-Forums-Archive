---
title: "update-grub doesn't update grub"
date: 2011-07-22
forum: Installation &amp; Upgrades
---

### Post by MountainX on 2011-07-22
I installed 11.04 on a Thinkpad T61 that already had Windows installed. I installed using the Live CD and I did everything very standard and followed all the default recommendations. I shrank the existing Windows partition and installed Ubuntu alongside it as recommended.

Now I would like the computer to boot into Ubuntu without prompting me to choose the OS and without showing the grub menu.

There are two problems:

1. I cannot find clear instructions for grub 1.99 for disabling the grub menu with multiple-OSes

2. any changes I make either by editing the grub config file or by using grub-customerizer are ignored. None of my changes have any effect -- and I am running grub-update.

Anyone know what is going on, especially with issue #2? Thanks

---

### Post by stlsaint on 2011-07-22
Please see grub2 link in my signature.

---

### Post by MountainX on 2011-07-22
> **stlsaint said:**
> Please see grub2 link in my signature.

I visited that page already. In particular, I looked at this section:
[https://help.ubuntu.com/community/Grub2#Hidden](https://help.ubuntu.com/community/Grub2#Hidden)

But I could not find answers to either of my questions on that page. Did I miss it?

---

### Post by haresear on 2011-07-22
> **MountainX said:**
> 
2. any changes I make either by editing the grub config file or by using grub-customerizer are ignored. None of my changes have any effect -- and I am running grub-update.

Anyone know what is going on, especially with issue #2? Thanks
Exactly what "grub config file" are you editing?

If you edit "/boot/grub/grub.cfg", and then run update-grub, the edits will be lost (over-written by update-grub).

On the other hand, if you edit "/etc/default/grub" or any of the files in "/etc/grub.d", and then run update-grub, the changes should be reflected in the new "/boot/grub/grub.cfg" generated. If this doesn't happen, one possibility is that update-grub is exiting early before it gets to your changes. Are there any error messages when you run update-grub? If you check the modification date-time on the "/boot/grub/grub.cfg" file (ls -l /boot/grub/grub.cfg) you will be able to tell if update-grub actually generated a new "/boot/grub/grub.cfg" file.

Is there any possibility that there is more than one installation of grub2? You have only one hard drive?

Haven't used grub-customizer, so I can't help there.

BTW, it is *update-grub* that you run, not "grub-update", correct?

---

### Post by MountainX on 2011-07-22
Thanks for your help.

> **haresear said:**
> Exactly what "grub config file" are you editing?


If you edit "/boot/grub/grub.cfg", and then run update-grub, the edits will be lost (over-written by update-grub).

On the other hand, if you edit "/etc/default/grub" or any of the files in "/etc/grub.d", and then run update-grub, the changes should be reflected in the new "/boot/grub/grub.cfg" generated.


Yes, I have tried editing "/etc/default/grub" and several of the files in "/etc/grub.d". I edited them by hand as well as with grub-customizer.

>  If this doesn't happen, one possibility is that update-grub is exiting early before it gets to your changes. Are there any error messages when you run update-grub? If you check the modification date-time on the "/boot/grub/grub.cfg" file (ls -l /boot/grub/grub.cfg) you will be able to tell if update-grub actually generated a new "/boot/grub/grub.cfg" file.
Oh, that was it! grub-customizer was just reporting the new cfg file had been saved, but it was not letting me know there were errors. When I ran the commands in a terminal, I saw errors. I fixed the errors and it works now. 

grub-customizer works now too. I can make changes either by hand editing or with grub-customizer, so I'm in good shape now. Thank you.

>  BTW, it is *update-grub* that you run, not "grub-update", correct?Yes, thanks.

---

### Post by haresear on 2011-07-22
Great! Glad you solved it.

---

