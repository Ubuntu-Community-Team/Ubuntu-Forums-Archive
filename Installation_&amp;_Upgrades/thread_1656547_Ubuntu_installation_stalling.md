---
title: "Ubuntu installation stalling"
date: 2010-12-31
forum: Installation &amp; Upgrades
---

### Post by idiota115 on 2010-12-31
Hi there!

I am currently installing ubuntu 10.10 amd64 onto my newly assembled computer via usb stick. I checked the BIOS before loading the OS onto the computer and everything is detected. 

Upon loading the OS, the screen goes into a Ubuntu loading purple screen with the word "Ubuntu" displayed. It has been there for at least 30 min. I have tried to restart the computer and reinstall the OS, but I encounter the same problem. 

What could be wrong?

Additional Info: 
HDD is 800 Gb, caviar green
AMD phenom II 6 core processor
MSI ATI 5570


thank you in advance!

---

### Post by Quackers on 2010-12-31
If you press the F6 key during boot you should get some options. First try the check cd for errors one.
If it's ok, reboot and when the first purple screen appears (with the symbols on the bottom) press Esc key. A new screen should appear then press F6. You should get some boot prompt options bottom right, which include "nomodeset". I'm not sure which of the options is correct for your graphics card, so you may have to try each one, one at a time. Hopefully one of those options will allow you to have a GUI so that the installation can run. Please make a note of the prompt that works. You may need it later in order to make the change permanent.

---

### Post by idiota115 on 2010-12-31
Hi! Thank you soo soo much for your help! I disabled every option except for the "Use Free Software only" option. Now it is installing. 

Do you know what those options do ...? If you do, can you explain them to me in "english?" 

Thank you thank you thank you!

---

### Post by Quackers on 2010-12-31
What options were on the screen at the time? Can you remember? It doesn't sound like you got to the nomodeset,/i915.nomodeset=0 etc, etc.
It's been quite some time since I saw the options screens :-)

---

### Post by grahammechanical on 2010-12-31
How up-to-date is your hardware? If it is the very latest then you may be ahead of the Linux developers. What graphic card are you using? Are you sure that it is supported by Linux?

regards.

---

### Post by idiota115 on 2011-01-01
Hi all, Thank you so much for your help! I checked everything under the "option" menu xcept for the "use Free Software only" (something like that) and it worked! 

I have  MSI ATI Radeon 5570. Ubuntu detected a driver for it and a ATI catalyst center is installed on my ubuntu (pretty cool). 

Now I ran into another problem. I formated a new partition on my 800 gb caviar for cloning my old PC's hard drive (~20 gb). Clonezilla worked great; everything was good, but I cannot make the partition bootable. 

Then, I went to disk utilities and edited the selected partition and checked "bootable." However, computer refuses to change. 
I tried changing it to "bootable" when the partition was mounted and not-mounted. 

Right now it says:
Partition Type: empty (0x00)  <--- the system refused changing that too.
Partition Flag: - 
Type: NTFS

btw, the partition has windows XP SP1 OS in it. 

Thanks! and Happy New Year! :)

---

