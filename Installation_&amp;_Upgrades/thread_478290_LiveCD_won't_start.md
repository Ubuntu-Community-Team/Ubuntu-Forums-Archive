---
title: "LiveCD won't start"
date: 2007-06-19
forum: Installation &amp; Upgrades
---

### Post by yigals on 2007-06-19
I've been trying to load Ubuntu LiveCD on my new computer without success, so far I tried with Ubuntu 7.04, Ubuntu 6.10, and Kubuntu 7.04.
They all came out with the same problem:
After the LiveCD image is shown I choose "start or install.." it is starting to load and after a while with the loading image, a text screen is shown with a lot of tech information that doesn't make any sense (to me at least), and the computer is stuck, waiting for long hours nor ctrl+alt+del won't help, only hard reset.

specs:
motherboard: Asus p945gz-mx
Intel  Core 2 Duo  E4300  @ 1.80GHz
NVIDIA GeForce 7300 LE

Please hurry, I'll probably kill myself at some stage if i'll keep using this XP

---

### Post by Pumalite on 2007-06-19
> **yigals said:**
> I've been trying to load Ubuntu LiveCD on my new computer without success, so far I tried with Ubuntu 7.04, Ubuntu 6.10, and Kubuntu 7.04.
They all came out with the same problem:
After the LiveCD image is shown I choose "start or install.." it is starting to load and after a while with the loading image, a text screen is shown with a lot of tech information that doesn't make any sense (to me at least), and the computer is stuck, waiting for long hours nor ctrl+alt+del won't help, only hard reset.

specs:
motherboard: Asus p945gz-mx
Intel  Core 2 Duo  E4300  @ 1.80GHz
NVIDIA GeForce 7300 LE

Please hurry, I'll probably kill myself at some stage if i'll keep using this XP

Download a new iso. Torrent is better than HTTP or FTP. Do checksum. Burn at 4x or 1x. Then try again. What hard drives? How did you partition? Are you dual booting? XP or Vista?. It all makes a difference.

---

### Post by wpshooter on 2007-06-19
Did you check the integrity of your Ubuntu CDs by running the verification function that is found on the initial boot screen menu ?

Did you try start in safe graphics mode ?

---

### Post by yigals on 2007-06-19
My cd's are OK (my Kubuntu is the original from shipIt, and the others passed the integrity check, safe mode didn't help).

But, I managed to get it running once, and I did it with the integrated graphic card on the board instead of the Nvidia. (I don't know why, sometimes it boots from there).

Do I need to install some drivers to make it work properly with the Nvidia card?

Anyways, i'm dual-booting with XP, but the problem is with the LiveCD, before it boots from the HD

---

### Post by Znupi on 2007-06-19
I think the only way to fix this is to download the Alternate Install CD and install from there, and after the installation install drivers for your video card. I don't know how, though...

---

### Post by yigals on 2007-06-19
I can manage to install & run Ubuntu if it's booting from the integrated graphic card (currently I don't know what causing the random boot from the two graphic cards, really weird)  but what then? How do I make it work with the Nvidia card as well?

---

### Post by Pumalite on 2007-06-19
> **yigals said:**
> I can manage to install & run Ubuntu if it's booting from the integrated graphic card (currently I don't know what causing the random boot from the two graphic cards, really weird)  but what then? How do I make it work with the Nvidia card as well?

Go to the NVIDIA site and download the driver of your choice ( I use 9755 ). Place it in home/<username>. At the command line ( Ctrl+Alt+F2):
Code:  sudo /etc/init.d/gdm stop

Code:  sudo sh NVIDIA*.run
Accept license
Let it reconfigure your xorg file.
Back at the command line:
Code:  sudo /etc/init.d/gdm start

---

