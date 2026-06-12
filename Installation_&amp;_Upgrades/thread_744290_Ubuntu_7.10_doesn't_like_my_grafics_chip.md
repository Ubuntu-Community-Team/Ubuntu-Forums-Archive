---
title: "Ubuntu 7.10 doesn't like my grafics chip"
date: 2008-04-03
forum: Installation &amp; Upgrades
---

### Post by Old1 on 2008-04-03
Hi,
I've got a rather old notebook here. It's an relabeled Asus with Pentium3@600mhz, 192 mb ram and a Silicon Motion SM720 Lynx3DM chip that has 8mb grafic ram. The TFT has 1024x768.

Ubuntu worked up till 7.04.

Now I tried to install the 8.04 beta from the alternate CD in a seperate partition. Right after the installation starts the screen switches to - I guess - 640x480 textmode and after a couple of hours Ubuntu boots the first time.
The boot screen looks nice till it switches to the liogin scree. From here graphics is screwed up.
It looks all dark and totally anreadable.

Then I tried 7.10 only to get the same result.

Then I made a partimage and upgraded 7.04 to 7.10 and got screwed graphics as well.
So something got broken after 7.04.

I even copied xorg.conf from 7.04 to 7.10 and got nowhere.
What can I try now?

Btw. How can I boot into runlevel 3 (text, multiuser, network) ?

---

### Post by notoriousdbp on 2008-04-03
With that spec have you considered xubuntu instead?

---

### Post by Old1 on 2008-04-03
No, but xubuntu wouldn't solve the basic graphics issue anyway as it needs xorg, too.

I tried the last KNOPPIX Live CD with kernel 2.6.24 and it works.
Knoppix is also based on debian so it should be a near relative of Ubuntu though Knoppix defaults to KDE.

This problem must be the X-configuration of Ubuntu 7.10 + 8.04.
As I mentioned 7.04 works but gets broken in the upgrade to 7.10 and a fresh installed 7.10 is broken from the verry beginning.

---

### Post by Old1 on 2008-04-04
I've come a bit further.
Obviuosly there is a kernel issue in Ubuntu 7.10 and later.
I found a couple of discussions regarding framebuffer related problems with 2.6.22-13++

Someone proposed to enter the fbcon module into the initrd.
I tried this after deleting S30gdm from runlevel 2 to get a text console at all.

Now it all looks still as bad as before when it boots up.
The splash-screen is normal and gdm shows all the wrong colors.
I logged in to see if it gets better but it didn't.
Next to blindly I tried to find the shutdown button until I got p.o. and pressed ctrl+alt+backslash to get back to the console.
It dropped me just to gdm but the graphics got reinitialised and from there it was all pretty.

After booting gdm is broken until I kickstart it the hard way.

What can be done about that?

---

### Post by yagi on 2008-04-12
Hi,

did you find any solution to that? I have exactly the same problem. I also realised that when you login, the resolution is very small but the grafics and colors are ok. but the notebook is not usable, because xorg needs about 60% of the cputime.

---

