---
title: "dvd drive not detected upon boot"
date: 2007-07-14
forum: Installation &amp; Upgrades
---

### Post by zenfyre on 2007-07-14
Ok here is my problem I have the vaio PCG-R505JE with an external pcmcia dvd drive(pcga-dvd51)

I have always used slackware since version 3.1 and upon getting this laptop I had the same problem but I was able to pass the boot parameter to lilo to force to boot from the device since it was not detected with the fallowing parameter bare.i ide2=0x180,0x386

I started using ubuntu on my workstation and really enjoy many things about it and would like to install it on my laptop.Any suggestions ?I have searched all over the web but since my laptop is not all that new I have had difficulty finding an anwser.

you can also contact me @ [email]zenfyre.x@gmail.com[/email]

---

### Post by Pumalite on 2007-07-14
Post your /etc/fstab.

---

### Post by zenfyre on 2007-07-14
I cannot do that since I have no installation.My current install is slackware which is not in any way significant.I am unable to install ubuntu since my drive is not detected.sorry if i didnt make my self clear enough.

---

### Post by Pumalite on 2007-07-14
You have to install Ubuntu then and worry later. It recognizes all my USB devices and all my other hardware. For all I know is the best distro around, and I run 5 in my comps.

---

### Post by zenfyre on 2007-07-14
Ok..... maybe i am not making myself clear here I CANNOT install ubuntu since it does not recodnize my dvd drive so I have nothing to install from.

---

### Post by Pumalite on 2007-07-14
Is not Ubuntu that does not recognize your drive. It's your computer or a defective CD. Check your iso (Md5sum),bur at 4x or less, check CD for corruption before install. Does your BIOS recognize your DVD? Is it set to boot first?

---

### Post by zenfyre on 2007-07-14
please read the original post very carfully .Im sure there is a way to pass the same parameter with grub which ubuntu uses as I did with lilo.I just dont know what this parameter may be.

---

### Post by zenfyre on 2007-07-27
?

---

