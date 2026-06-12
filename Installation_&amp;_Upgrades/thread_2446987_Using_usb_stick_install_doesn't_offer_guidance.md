---
title: "Using usb stick install doesn't offer guidance"
date: 2020-07-10
forum: Installation &amp; Upgrades
---

### Post by Dirk_Ouellette on 2020-07-10
So... have been running Linux on all of my machines since 1998. I use Linux Mint these days, 18.03 on a Lenovo T500 , and 19.2 on a Lenovo T430.
 I hade Mint on a Lenovo T61, but wiped the drive with Dban ( which I've used successfully in the past).
 I downloaded the [https://ubuntu.com/#download](https://ubuntu.com/#download) LTS file, used Disks to clean the USB stick, used "Make Bootable USB Stick" and started the T61 with Ubuntu stick in the machine. Started giving me an Ubuntu logo at the bottom of the screen, then watched the stick start running, but NO INTERFACE  ON THE SCREEN, a lot of designs on the screen, then the designs disappear, then blank screen for the most part.  Every now and the USB stick lights up as though it is loading, but after 2 hours, a blank backlit screen.
  Any ideas anyone?
Thanks all.

Just now I'm getting a screen of steplike graphics running from lower left to upper right screen in gray, and black filling the screen.
I have changed the boot options to accept USB hdd, USB FDD, USB CD.

---

### Post by Dirk_Ouellette on 2020-07-10
OK, the stick won't even start on my good working T500.
Bad stick...

---

### Post by TheFu on 2020-07-10
Read the [COLOR="#FF0000"]Release Notes[/COLOR] for the Release you are trying to use ...   which you didn't actually say above.  There are 3 supported LTS Ubuntus today.  [COLOR="#FF0000"]Check the stuff related to video driver problems.[/COLOR]

---

### Post by Dirk_Ouellette on 2020-07-10
I was wrong. Both sticks wouldn't start on my other Mint T500. Sticks are good. I downloaded the [20.04 LTS]("https://ubuntu.com/download/desktop/thank-you?version=20.04&architecture=amd64").

---

### Post by Dirk_Ouellette on 2020-07-10
I'm installing ubuntustudio instead. It is installing just fine, so far...

---

### Post by C.S.Cameron on 2020-07-12
Did you know that instead of just cleaning everything up with Disks, you can click the three lines upper right, select "Restore Disk Image", select your ISO and Disks will finish making a bootable USB for you. (I just discovered this today).

---

### Post by TheFu on 2020-07-12
I've always been disappointed with gnome-disks application.  It is dumbed down so much as to be lying, IMHO.  The summary of file systems to format is a joke.  Best to use **gparted** for anything related to partitioning or formatting file systems - or fdisk + mkfs if in a shell-only environment.

Just seems odd that ubuntustudio would work and straight ubuntu wouldn't.  OTOH, I haven't installed any Ubuntu directly on hardware in about 18 months. By far, my installations are all virtual machines which ends up with extremely well supported fake hardware, skipping pretty much all the incompatibilities with any new HW that isn't well supported.

---

