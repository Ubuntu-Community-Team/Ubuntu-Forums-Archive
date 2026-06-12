---
title: "Ubuntu locks up after upgrade"
date: 2010-10-29
forum: Installation &amp; Upgrades
---

### Post by rhossack on 2010-10-29
I have a dual boot system with Ubuntu 10.04 LTS in its own partition.

I checked updates and it said there were 70 of them so I let it do its thing and download and install.

When rebooting now the system locks up at the password prompt and I have to do a hard boot.

When this happened before I recieved this message about using'nomodeset xforcevesa' after the 'quiet splash':

[B]Originally Posted by lechien73  
You could try adding 'nomodeset xforcevesa' after 'quiet splash' because it could be a graphics driver issue. There have been problems with the ATI drivers.[/B]

Unfortunately this didn't work this time and it still locks up.

SYSTEM INFO:
CPU	Intel Core 2 Quad Q8200 @ 2.33GHz	118 °F Yorkfield 45nm Technology
RAM 4.0GB Dual-Channel DDR2 @ 399MHz (6-6-6-1
Motherboard Dell Inc. 0M017G (CPU 1)
Graphics WS231 @ 1600x1200
256MB ATI Radeon HD 3450 (Dell)
Hard Drives
625GB SAMSUNG SAMSUNG HD642JJ ATA Device (IDE)	99 °F 977GB Western Digital WDC WD10EAVS-55D7B1 ATA Device (IDE)	96 °F
Optical Drives
YMAX MagicJack USB Device
TSSTcorp DVD+-RW TS-H653F ATA Device
Audio
Realtek High Definition Audio

---

### Post by David52 on 2010-11-13
ya know i had and do have this issue with the program locking up when the password is needed. I have found out that when I reboot, and "fi the number lock button is on" then it will do this. So when I reboot and go to the ubuntu I always make sure my #lock button is off and it always boots up. Hope this helps ya. As for running magicJack, I have downloaded Virtual Box 3.2.10 have instlalled the Guest Addition, I loaded Windows XP inside VBox. After I got VBox going I copied the MagicJack file from the single boot XP on to a disk, Loaded it into the XP inside VBox and do hav it working but it is choppy. I think the issue is because of the "pulse system" Like the old style phone companies from the early 70's but I am not giving up yet. If you need info you can email me or do a search on virtual box and make sure that you install the correct vbox for your setup. Also a good idea is to read the documation from the vbox page or download it as a pdf file and read it. That part has helped me alot.

David

---

### Post by rambo15 on 2010-11-13
I experienced a similar issue. I found that by unplugging the keyboard and mouse and then plugging them back in fixed the problem.

---

### Post by David52 on 2010-11-13
Ok, but isnt just making sure the number lock is off easier?

---

### Post by rhossack on 2010-11-28
I'm still not able to get Ubuntu to run.

Tried adding 'nomodeset xforcevesa' after 'quiet splash' and still locks up.

Tried the number lock key on and off and it still locks up at the prompt to enter password.

Any other ideas?

---

