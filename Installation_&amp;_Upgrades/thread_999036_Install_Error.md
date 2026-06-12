---
title: "Install Error"
date: 2008-12-01
forum: Installation &amp; Upgrades
---

### Post by Kalec on 2008-12-01
I have the disc burned and when i put it in the menu loads up nicely and then i click Install Ubunutu and a message pops up and says Boot Loader at the title and in the message /casper/vmlinuz with a big ok button at the bottom. Also when i click check CD for defects it just goes to a black screen. I tried re burning the disc multiple times with no luck. Im currently re-downloading the disc image but if you have any suggestions that would be great.

---

### Post by glotz on 2008-12-01
Take a look at [https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto) and its various links. What kind of a machine are you trying to install on?

---

### Post by Pumalite on 2008-12-01
Follow this guide:
[https://help.ubuntu.com/community/BurningIsoHowto?highlight=%28burn%29%7C%28](https://help.ubuntu.com/community/BurningIsoHowto?highlight=%28burn%29%7C%28)
Do not use CD-RW
Burn at 4x or less
Clean the lens in your burner

---

### Post by Kalec on 2008-12-01
> **glotz said:**
> Take a look at [https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto) and its various links. What kind of a machine are you trying to install on?

Its just a PC built out of some scraps.

---

### Post by Kalec on 2008-12-01
> **Pumalite said:**
> Follow this guide:
[https://help.ubuntu.com/community/BurningIsoHowto?highlight=%28burn%29%7C%28](https://help.ubuntu.com/community/BurningIsoHowto?highlight=%28burn%29%7C%28)
Do not use CD-RW
Burn at 4x or less
Clean the lens in your burner

Are DVDR's ok? Thats all i have.

---

### Post by glotz on 2008-12-01
I think DVDRs should work just fine. One thing that's not mentioned in the link is trying different kernel parameters at boot. When having booted off the CD or DVD some function key will bring out a help offering some options for special hardware, like ACPI or something.

---

### Post by Pumalite on 2008-12-01
Dowload ImgBurn and install it.
[http://www.imgburn.com/](http://www.imgburn.com/)
Put a DVD on. Go to Mode>ISO>Burn
Select 1x as speed of burn.

---

### Post by Kalec on 2008-12-01
I did a MD5SUM check and they didn't match so i threw the file back into UTorrent and did a re-check and i was missing .1 files so i downloaded those and did another check and they matched so now im going to try re burning the disc.

---

### Post by glotz on 2008-12-01
Yeah, no wonder. Always a good idea to perform a hash check if you're downloading a larger file.

---

### Post by Kalec on 2008-12-01
No luck. And when i try to live boot it stops and at the bottom says "Kernal Panic - not syncing: VFS: Unable to mount root fs on unkno wn-block(8,1)"

---

### Post by Kalec on 2008-12-01
And sometimes when i go to check disc the computer just restarts.

---

### Post by glotz on 2008-12-01
I guess one thing you could do is to try the alt CD. Or another version altogether... :???:

Did you try the memtest option?

---

### Post by Kalec on 2008-12-01
> **glotz said:**
> I guess one thing you could do is to try the alt CD. Or another version altogether... :???:

Did you try the memtest option?

Memtest worked i think i just don't know what a Memtest looks like in the first place but it seemed to work.

Is it possible the computer is juts to old and slow to run it?

It has 384MB of Ram
1.3 GHZ processor
and i have a BFG 6800 OC for it but i'm waiting to get an operating system to work before i install it. Could it also be the BIOS? Because when i had windows Xp in it it was crashing literally all the time and i would not load firefox or internet explorer. It kept saying it wasn't fully ACPI compliment or something and kept telling me to update my BIOS. And currently it wont start windows cause it says its missing a driver file in system 32 or something. Haha now that i think of it that's probably the problem.


Any ideas on how to get my computer in good enough condition to run Ubuntu?

---

### Post by glotz on 2008-12-01
That should be enough. It wont be too fast but it should run. Yeah, I guess it could be something in the BIOS. You might need to actually flash it too but first you should try perhaps to mess around in the BIOS setup since flashing could potentially funk it up. You could also try the acpi=off kernel parameter when booting the CD. (The amount of ram is the first thing to update there once you get it working.)

Always a good idea to let memtest do its thing through a couple of times. Flaky ram can give you the strangest of problems.

---

### Post by Pumalite on 2008-12-01
These could help too:
noapic nolapic acpi=off  irqpoll pci=noacpi pnpbios=off
(try one at the time or in different combinations)
[http://grumpymole.blogspot.com/2007/05/ubuntu-how-to-edit-grub-boot-parameters.html](http://grumpymole.blogspot.com/2007/05/ubuntu-how-to-edit-grub-boot-parameters.html)

---

### Post by Kalec on 2008-12-01
I switched hard drives and things seemed to be going smooth i clicked install it did some stuff but now it saying over and over 3 random #s . 7 more numbers the number combination are different everytime and after the numbers it says "Buffer I/O error on device sr0, logical block 1147534"
"end_request: I/O error dev sr0, sector9180280"

---

### Post by Kalec on 2008-12-01
> **Kalec said:**
> I switched hard drives and things seemed to be going smooth i clicked install it did some stuff but now it saying over and over 3 random #s . 7 more numbers the number combination are different everytime and after the numbers it says "Buffer I/O error on device sr0, logical block 1147534"
"end_request: I/O error dev sr0, sector9180280"

The same exact thing happens when i try to just use Ubuntu from the disc without installing it. and when i try to do a disc check.

---

### Post by Kalec on 2008-12-01
I don't have a clue on what else to try other then replacing some of the parts

---

