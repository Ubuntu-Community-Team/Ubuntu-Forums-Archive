---
title: "upgrading to lucid"
date: 2010-03-21
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by jsriz on 2010-03-21
well all i can say is that i am on a really slow internet and cannot download a 700mb file
all i can do is leech for hours so i downloaded a mini.iso of karmic and successfully installed a miinimal installation of karmic.
that took almost a whole day to do that and i dont want to do that again for the upgrade coz i really want to use my laptop during the install.....
i decided to chroot into this system from my main karmic installation
heres my fdisk -l:
```

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xa0000000
   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1305    10482381   83  Linux
/dev/sda2            1306       14153   103201560   83  Linux
/dev/sda3           14154       16703    20482875    b  W95 FAT32
/dev/sda4           16704       30401   110029185    5  Extended
/dev/sda5           16704       29839   105514888+  83  Linux
/dev/sda6           29840       30401     4514233+  82  Linux swap / Solaris

``` 
sda1 being the minimal installation of karmic and sda5 being my main install....
these are the commands that i ran 
```

sudo mount /dev/sda1 mnt/
sudo mount --bind /proc /mnt/proc
sudo mount --bind /sys /mnt/sys
sudo chroot /mnt

```
it gives:
chroot: cannot run command `/bin/bash': Exec format error
plz help

---

### Post by zvacet on 2010-03-21
Maybe this is not answer you are looking for but that is what i think.Best way (if your internet connection is slow) is to download alternate CD from somewhere else (your friend for example) and upgrade to next release with it.If I´m on your place I will wait until final release of Lucid is out,because between beta and final you will have many updates.

---

### Post by phillw on 2010-03-21
> **jsriz said:**
> well all i can say is that i am on a really slow internet and cannot download a 700mb file


Hi, 
there may be a much simpler way. It's called LoCo Team (LOcal COmmunity). The indian one is [https://lists.ubuntu.com/mailman/listinfo/ubuntu-in](https://lists.ubuntu.com/mailman/listinfo/ubuntu-in)

If you join their LoCo they may be able to sort out a CD for you or put you in touch with someone close by who can help.

Regards,

Phill.

---

### Post by jsriz on 2010-03-21
> **phillw said:**
> Hi, 
there may be a much simpler way. It's called LoCo Team (LOcal COmmunity). The indian one is [https://lists.ubuntu.com/mailman/listinfo/ubuntu-in](https://lists.ubuntu.com/mailman/listinfo/ubuntu-in)

If you join their LoCo they may be able to sort out a CD for you or put you in touch with someone close by who can help.

Regards,

Phill.

thank you but why isn't chroot working i need it also for installing gdm and X11 on the minimal install

---

### Post by zvacet on 2010-03-21
> installing gdm and X11 on the minimal install

I don´t understand why are you doing this with slow internet.It is ~400MB (if I remember correctly) download.**jsriz** advice is quite resonable.

---

### Post by jsriz on 2010-03-21
> **zvacet said:**
> I don´t understand why are you doing this with slow internet.It is ~400MB (if I remember correctly) download.**jsriz** advice is quite resonable.
you mean phillw's advice.
but i am unable to chroot into any environment i create....
i think i messed up somewhere in the commands or i broke something in my system.....

---

### Post by zvacet on 2010-03-21
> you mean phillw's advice.

Sorry for mistake!If I understand you correctly you have two Ubuntu installations.

> sda1 being the minimal installation of karmic and sda5 being my main install....

Is there any specific reason for that?

---

### Post by uRock on 2010-03-21
If your local library has internet and allows downloading, you can download and save to a thumb drive.

---

### Post by jsriz on 2010-03-21
> **zvacet said:**
> Sorry for mistake!If I understand you correctly you have two Ubuntu installations.
Is there any specific reason for that?
nope i just wanted to remove the unwanted apps and make a minimal install 
and then try to minimise the boot time.
on my main installation i have tried kde lde xfce and it it crowded up with apps

---

### Post by phillw on 2010-03-21
jsriz,

If you're looking for slim versions of ubuntu with a small 'foot-print' you may want to consider xubuntu or lubuntu, like the rest of the family, they're in beta stage.

lubuntu is actually a smaller down-load than doing minimal install of ubuntu and then dropping lxde on top of it.

You can read more about both of them below.

lubuntu = [https://wiki.ubuntu.com/Lubuntu](https://wiki.ubuntu.com/Lubuntu)
xubuntu = [https://wiki.ubuntu.com/Xubuntu](https://wiki.ubuntu.com/Xubuntu)

Regards,

Phill.

---

