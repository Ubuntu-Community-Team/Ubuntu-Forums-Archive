---
title: "installed ubuntu, then XP now only XP loads! HELP!!"
date: 2010-07-30
forum: Installation &amp; Upgrades
---

### Post by Vuk Matic on 2010-07-30
okay so i really like ubuntu so i installed that first and then i decided that it would be handy to have windows xp as well; since it is one of the most compatible OSs ever. I installed it on a separate partition to ubuntu. Now it automatically boots me into Win XP, i dont get a boot loader or anything (no choice to change OS). now im wondering what can i do to fix this? Some other guy on the forum said to type :sudo grub-install /dev/sdx 
sdx being the whole drive and not the partition. Now i tried this but i had no idea what to change sdx to? :( since im a newbie ubuntu user! any help is appreciated! 


thanks in advance,
Vuk Matic

---

### Post by Goolie on 2010-07-30
It's always best to install Windows OS's and *then* Ubuntu.  Basically, the Master Boot Record has been altered.  So you're only option is to boot into Windows.  You'll need to alter the MBR.  I think you should do this from Ubuntu.  I know it's not detailed, but hopefully this will point you in the right direction.

---

### Post by Vuk Matic on 2010-07-30
> **Goolie said:**
> It's always best to install Windows OS's and *then* Ubuntu.  Basically, the Master Boot Record has been altered.  So you're only option is to boot into Windows.  You'll need to alter the MBR.  I think you should do this from Ubuntu.  I know it's not detailed, but hopefully this will point you in the right direction.


thanks for the quick reply! yeah i thought thats what happened! But i ll wait to see if someone has a more detailed answer or something i can do. If all goes wrong i can always start over by installing windows first.

---

### Post by dino99 on 2010-07-30
boot on unbuntu cd or usb stick, then install grub-pc on /dev/sdx

where sdx is your ubuntu mbr

then 

sudo grub-mkconfig
sudo update-grub

---

### Post by Vuk Matic on 2010-07-30
> **dino99 said:**
> boot on unbuntu cd or usb stick, then install grub-pc on /dev/sdx

where sdx is your ubuntu mbr

then 

sudo grub-mkconfig
sudo update-grub


im sorry im a complete noobie... how do i know what the mbr is? because there is no such file in my /dev ! theres an shm file which i tried to boot through and that didnt work.
when you say install grub-pc do you mean:
sudo apt-get install grub-pc because that tells me that its at the newest version! i dont know how to install it to a specific place (dev/sdx) ! when i tried the rest of the commands 
it says (for the first one) /usr/sbin/grub-probe: error: cannot find a device for / (is /dev mounted?)

and for the next command i get the exact same error!

---

### Post by robertomano24 on 2010-07-30
> **Vuk Matic said:**
> im sorry im a complete noobie... how do i know what the mbr is? because there is no such file in my /dev ! theres an shm file which i tried to boot through and that didnt work.
when you say install grub-pc do you mean:
sudo apt-get install grub-pc because that tells me that its at the newest version! i dont know how to install it to a specific place (dev/sdx) ! when i tried the rest of the commands 
it says (for the first one) /usr/sbin/grub-probe: error: cannot find a device for / (is /dev mounted?)

and for the next command i get the exact same error!

mbr = master boot record

i would use the live cd to re-install grub in the installation. rescue broken system. thats what i did. since ive done what you did 400 times :)

---

### Post by Vuk Matic on 2010-07-30
screw it, i deleted my ubuntu and now im reinstalling it and i ll see where that takes me :D

---

### Post by robertomano24 on 2010-07-30
that works too :D

---

### Post by Vuk Matic on 2010-07-31
worked like a charm :)

---

