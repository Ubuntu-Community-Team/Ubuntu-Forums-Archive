---
title: "Ugrade"
date: 2011-02-14
forum: Installation &amp; Upgrades
---

### Post by odulzaides on 2011-02-14
Hi,

I have just upgraded my Ubuntu OS using the "ugrade-manager -d" command from 10.10 to 11.04.
I was using 10.04 and upgraded to 10.10 no problem, When I did the upgrade to 11.04 from 10.10 the disk only gets me to the grub> prompt. From there I am able to boot using grub commands.

The grub.cfg file has entries for root (hd0,msdos1) which I have never seen before it is usually root (hd0,1) no msdos. This is a single operating system machine and never booted to the grub menu although there are other older kernels in the system to boot from as a result of updates.

I have tried update-grub, removing the "msdos" and leaving just the (hd0,1) in the grub.cfg and nothing. I have also booted up with the live cd of the 10.10 edition and tried grub-install which returned no errors yet I still keep getting the grub> prompt and have to boot from there.

By the way I also check the version and it is natty (development branch) so the upgrade was successful. The grub version is 1.99~rc2-2ubuntu1. I have tried to do grub-install form the os itself and get a message that grub is not installed??? yet version shows as above.

If I could get some help on this issue it would be great as my skill set is exhausted on this one.
Thank you

---

### Post by zvacet on 2011-02-15
You can try to reinstall grub following [https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD](https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD)

---

### Post by Rubi1200 on 2011-02-15
Hi and welcome to the forums odulzaides :-)

Natty is still in alpha.

Therefore, alpha = bugs

My advice, unless you are willing to deal with this type of situation stick with more stable releases.

Oh, and your question needs to be asked in the relevant sub-forum:
[http://ubuntuforums.org/forumdisplay.php?f=394](http://ubuntuforums.org/forumdisplay.php?f=394)

---

