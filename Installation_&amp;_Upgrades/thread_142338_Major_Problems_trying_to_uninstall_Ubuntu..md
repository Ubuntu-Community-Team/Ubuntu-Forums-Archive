---
title: "Major Problems trying to uninstall Ubuntu."
date: 2006-03-10
forum: Installation &amp; Upgrades
---

### Post by mewse on 2006-03-10
Alright, for you that's reading this, thanks already, and hopefully you can help me with this problem.

I had a dual-booting environment set up for my laptop.

Windows XP Home + Ubuntu.

For a while, when I tried booting Windows, I got a message about something missing and it would restart, but I solved that problem by performing a couple commands in GRUB.

So, with a feeling a relief I booted into Windows. Theen, I did something I shouldn't have. I went and deleted the partition that my Ubuntu was running on.

Now I get this when booting.

> GRUB Loading stage1.5


GRUB Loading, Please wait...
Error 17

_

I've searched Google. I learn that I could boot off my copy of Windows. Next, I learn that my laptop's CD drive is a piece of poo, and has problems reading CD's. It sometimes works, but like, in a 1/80 chance.



So, what would be the BEST and RIGHT way to solve my problem?


Thanks for any help in advance \\:D/

---

### Post by 4dz0 on 2006-03-10
If you want to have ubuntu installed then you can simply just install ubuntu again to that partition, installing grub to your MBR will solve your problem. However, if you deleted the partition because you want rid of ubuntu then let me know.

---

### Post by mewse on 2006-03-10
Err sorry that I didn't add that onto my post.

Yes, I would like Ubuntu DELETED for now.

It's just that I deleted the partition, and from my knowledge and guessing, I wont be able to install Ubuntu anyways since the deleted partition isn't formated right :/

---

### Post by ~INVASION~ on 2006-03-10
i have the almost exact same error message, im afraid i might have ti reload windows if i cannot solve this.

I tried instaling ubuntu 5.04 on an external hard drive connected with usb, everything seemed nice and in order and it told me to restart and take out the disk, when it tried to restart it said

"grub error 21"

any ideas for help on this error message would be GREATLY appreciated

---

### Post by mewse on 2006-03-10
*bump*

---

### Post by Milamber_Cubed on 2006-03-10
I have had grub issues in the past and have managed to solve them by using my XP install CD to get my windows install back to where it was (i.e. starting up) and then trying again.

This is done by using the Recovery Console - [http://support.microsoft.com/?kbid=314058](http://support.microsoft.com/?kbid=314058)

follow the instructions on that page to get into the command line and use the fixboot and fixmbr commands.

Beware though that microsoft tells you the following about fixmbr:
> 
Warning This command can damage your partition tables if a virus is present or if a hardware problem exists. If you use this command, you may create inaccessible partitions. We recommend that you run antivirus software before you use this command.


It has never caused me any problems though. 

Just want to say that Ubuntu has never messed up my grub install either - it has always been me "playing" with stuff.

---

### Post by RJMacReady on 2006-03-10
> It has never caused me any problems though.

I think its just a forewarning that, if you're doing to do a fixmbr or fixboot and suddenly you get a power cut or something, your HDD will get bad karma and cease to work.

---

