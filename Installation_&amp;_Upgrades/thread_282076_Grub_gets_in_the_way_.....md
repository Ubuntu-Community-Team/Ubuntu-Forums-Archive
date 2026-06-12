---
title: "Grub gets in the way ...."
date: 2006-10-22
forum: Installation &amp; Upgrades
---

### Post by expatCM on 2006-10-22
I am dual booting W2K and Linux ...   Had Kubuntu 5.10 in place but for some reason it died big time.  I now want to start off fresh and install Ubuntu 6.06 in the place of Kubuntu.

There is a problem .....  I boot from the 6.06 CD ..  it tries to load and then grub appears and asks me to make a selection from the menu.  Since Kubuntu is hosed I can only then use W2K.

How can I get grub out of the picture so that I can install Ubuntu without putting my W2K at risk?

---

### Post by Najand on 2006-10-22
You mean you cannot boot your cd-rom?

---

### Post by expatCM on 2006-10-22
I do not know what your question means .....   the CD rom appears to be accessed (light on, starts to load on screen)  but the CD will not load fully before the grub menu cuts in ....  (hope it is a bit clearer to you :)  )

---

### Post by expatCM on 2006-10-22
oh .... and the CD media is just fine ...  it will work on other machines.

and the CD drive is apparently working fine ....

---

### Post by Najand on 2006-10-22
I think you need to change your bias setting and make it boot CDROM first and then your hard drive... You can enter BIAS Setting menu using one of the keys: F2 F12 or Delete... It usually appear when you turn on your computer.

---

### Post by Kateikyoushi on 2006-10-22
I agree, try to change the boot order in your bios, if the machine is an older one it might not be able to boot from cd.

---

### Post by expatCM on 2006-10-22
Nice idea but ... no

The BIOS boot order is CD as the first accessed priority ...

---

### Post by bulldog on 2006-10-22
Well if you boot the live cd,you never should see GRUB.

You should see a menu with several options to start the live session.

If you get GRUB instead there should be something seriously wrong.

---

### Post by expatCM on 2006-10-22
well ... perhaps that is the case but I am using a 6.06 LTS CD from  Canonical.  It will load fully on other machines but not so on this.

The boot order is without question CD drive first.

The CD does start to load but then grub appears and takes over.

That is what is happening.

So how do I tame grub?

---

### Post by bulldog on 2006-10-22
Think your cd player lose focus and hdd takes over.

Maybe another player to check things out?

You can't do anything to GRUB,it's your cd-player who's to blame I think.

---

### Post by gn2 on 2006-10-22
Have you tried booting the Live CD with the hard drive unplugged?

If it boots, the CD drive is not the problem.

How old is the CD drive, old ones sometimes struggle with newer media.

---

### Post by kondor on 2006-10-22
Did you check the MD5 hash of the CD? It is likely the CD that is amiss, not the CD player. Your player "reads" the CD, finds no bootable content, then reverts to GRUB as your HD bootloader.

Goodluck!

---

### Post by expatCM on 2006-10-24
This appears to be the solution .......

I changed the Power Supply upgrading to a larger wattage.

Guess what .....  no more problem :)

---

### Post by Kateikyoushi on 2006-10-24
That's a bit surprising solution but good to know, thanks for reporting it back. Was the machine unstable under full load ?

---

### Post by expatCM on 2006-10-24
not normally unstable but I have some problems with a stable mains power supply which seems to mess things up now and again.  Even use of a UPS does not help out too much.  So I went clutching straws and came up lucky :)

---

