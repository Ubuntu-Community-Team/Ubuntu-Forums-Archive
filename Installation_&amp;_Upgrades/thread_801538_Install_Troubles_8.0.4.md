---
title: "Install Troubles 8.0.4"
date: 2008-05-20
forum: Installation &amp; Upgrades
---

### Post by sniper910 on 2008-05-20
i cannot install ubuntu 8.0.4 
i hit enter on install and it loads ubuntu then goes to a text based saying thing (this is not the alternate) and now is saying 

*random numbers* ata1.00:status: [DRDY] 
*random numbers* ata1.00:exception emask 0x0 SAct 0x0 Serr 0x0 action 0x2 frozen
same ata random crap then cmd and it goes to I/O error on devide sda, logical block 2102506

HELP!

---

### Post by Pumalite on 2008-05-20
Post your specs.

---

### Post by sniper910 on 2008-05-20
erm where would i find those? my uncle built this computer a while ago but xp got corrupted and now i dont know what to do

---

### Post by Pumalite on 2008-05-20
Try the Alternate CD. Download from here:
[http://www.ubuntu.com/GetUbuntu/download](http://www.ubuntu.com/GetUbuntu/download)
Check the box below sign 'Start Download'

---

### Post by sniper910 on 2008-05-20
ok i'll post back if that works

---

### Post by Pumalite on 2008-05-20
Ok.

---

### Post by wpshooter on 2008-05-20
> **sniper910 said:**
> i cannot install ubuntu 8.0.4 
i hit enter on install and it loads ubuntu then goes to a text based saying thing (this is not the alternate) and now is saying 

*random numbers* ata1.00:status: [DRDY] 
*random numbers* ata1.00:exception emask 0x0 SAct 0x0 Serr 0x0 action 0x2 frozen
same ata random crap then cmd and it goes to I/O error on devide sda, logical block 2102506

HELP!

1) Did you check the integrity of your Ubuntu CD by running the verification function that is found on the initial Ubuntu boot screen menu ?

2) Have you ran the memtest that is also found on the initial Ubuntu boot screen menu ?

---

### Post by sniper910 on 2008-05-20
hold on let me do that

---

### Post by sniper910 on 2008-05-21
now it's saying cannot find acpi for the alternate version and i think it said it has 128 mem or something like that

---

### Post by Pumalite on 2008-05-21
If your computer has 128 MB of RAM; try Xubuntu Alternate CD. Ubuntu 8.04 would be too heavy a Desktop for you.

---

### Post by sniper910 on 2008-05-21
whats the diffrence between xubuntu and ubuntu

---

### Post by Pumalite on 2008-05-21
It's a lighter Desktop and therefore able to run well in your system. It's a form of Ubuntu for computers with little RAM.

---

### Post by sniper910 on 2008-05-21
still takes me to the text interface area
says acpi something then the error-ish message as listed above

---

### Post by sniper910 on 2008-05-21
i changed boot options to instead of quiet -- at the end i just removed that and now it seems to be blazing with a bunch of stuff appearing at a good space in that text-ish terminal i was refering to is that a good thing?

---

### Post by sniper910 on 2008-05-21
ok now it went to just a blank black screen with a blinking _ half way down it after all that code

---

### Post by Pumalite on 2008-05-21
You might need some boot paramete3rs. Try your luck:
[http://grumpymole.blogspot.com/2007/05/ubuntu-how-to-edit-grub-boot-parameters.html](http://grumpymole.blogspot.com/2007/05/ubuntu-how-to-edit-grub-boot-parameters.html)
Try first the common ones. To be tried alone or in different combinations until you hit the right one:
noapic nolapic acpi=off pci=noacpi irqpoll pnpbios=off vga=0x317

---

### Post by sniper910 on 2008-05-21
worked now it says could not find common cd drivers

---

### Post by Pumalite on 2008-05-21
Maybe you need to update your firmware or change your CD drive. I also noticed you never answered in the other thread if you had done md5sum on your iso, burn at 4x, on CD-R and check CD integrity before install.

---

### Post by sniper910 on 2008-05-22
oh yeah i did that srry didn;t see that question

---

### Post by sniper910 on 2008-06-03
ok i upgraded the ram to 352mb and the graphics card now for the ubuntu install non alternate it goes down a long list then gives a kernal error message

---

### Post by molotov00 on 2008-06-03
> **sniper910 said:**
> ok i upgraded the ram to 352mb and the graphics card now for the ubuntu install non alternate it goes down a long list then gives a kernal error message

hahaha.  "a kernel error message"

yeah. I know how to fix that!

How on EARTH can you expect a helpful response when all you provide is that crap question?

---

### Post by Pumalite on 2008-06-03
Post your new specs and the exact error messages.

---

### Post by sniper910 on 2008-06-03
i got my ubuntu cd's  today but i installed server but cannot login i type in account name in the black and white thing and i can't type in password help ?

---

### Post by Pumalite on 2008-06-03
You type your password, but it doesn't show. Just complete your password and then hit 'Enter'

---

### Post by sniper910 on 2008-06-03
ah ok thanks

---

### Post by sniper910 on 2008-06-03
ok now im still on the black and white text thing how do i get it to something like ubuntu desktop?

---

### Post by Pumalite on 2008-06-04
If you want a GUI:
sudo aptitude install ubuntu-desktop

---

### Post by sniper910 on 2008-06-04
ya i want a gui but this computers not connected to the internet it will be later tho but  is there another way i can some how  download gnome and install it?

---

### Post by sniper910 on 2008-06-04
> **molotov00 said:**
> hahaha.  "a kernel error message"

yeah. I know how to fix that!

How on EARTH can you expect a helpful response when all you provide is that crap question?

can you actually try and post something useful? beside makeing remarks like that

---

