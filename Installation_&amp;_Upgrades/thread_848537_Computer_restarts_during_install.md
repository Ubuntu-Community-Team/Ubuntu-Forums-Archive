---
title: "Computer restarts during install"
date: 2008-07-03
forum: Installation &amp; Upgrades
---

### Post by Fischeja on 2008-07-03
Hi,

I recently bought a computer without an operating system on it and decided to try out Ubuntu.  I booted from the LiveCD and selected install, but after the kernel loads and reaches 100% the computer restarts.  I've attached a txt file of what I was able to get from the serial port.  Sometimes the computer will not restart and just hang.

I thought maybe the CD was bad, but it works fine in other computers.  

Thanks

---

### Post by Pumalite on 2008-07-03
Post your specs.

---

### Post by Fischeja on 2008-07-03
My specs are:

Pent 4 3GHz
2 GB ram
80 GB HD

---

### Post by Pumalite on 2008-07-03
Burn a new CD after doing md5sum on the iso. Burn at 4x or less. Don't use CD-RW.
[https://help.ubuntu.com/community/BurningIsoHowto?highlight=%28burn%29%7C%28](https://help.ubuntu.com/community/BurningIsoHowto?highlight=%28burn%29%7C%28)

---

### Post by Fischeja on 2008-07-03
Ok i'll try that and post the results.

---

### Post by jnw222 on 2008-07-03
how old is it

maybe it is a bad cd drive

---

### Post by Pumalite on 2008-07-03
> **Fischeja said:**
> Ok i'll try that and post the results.

Clean the lens in your burner too.

---

### Post by Fischeja on 2008-07-03
> **jnw222 said:**
> how old is it

maybe it is a bad cd drive

I just bought the computer off of ebay. It's at least 3 years old. It's a Dell optiplex gx280

---

### Post by Fischeja on 2008-07-03
I ran md5sum on the iso and it was fine.  I also cleaned the lens and burned at 2x on a CD-R and the same thing is happening.

---

### Post by damis648 on 2008-07-03
> **Fischeja said:**
> I just bought the computer off of ebay. It's at least 3 years old. It's a Dell optiplex gx280

Hmm.... could be bad. If you have an extra CD drive lying around, try putting it in there and try with that drive. I am thinking it is a bad CD drive.

---

### Post by Fischeja on 2008-07-03
> **damis648 said:**
> Hmm.... could be bad. If you have an extra CD drive lying around, try putting it in there and try with that drive. I am thinking it is a bad CD drive.

I'll try to get a hold of one and post the results.

---

### Post by Fischeja on 2008-07-08
Is it possible to boot from an external cd drive that connects via usb?

---

### Post by Pumalite on 2008-07-08
Absolutely. There are several threads around that explain how to install to USB and boot from it.

---

### Post by upchucky on 2008-07-08
there is no monitor, screen, or vid driver in his log, does the machine boot in live cd mode? if so the settings for that boot scroll by and you can get them then edit into xorg.conf Via the live cd editor.

---

### Post by Fischeja on 2008-07-08
Unfortunately I still can't boot into live cd mode. I was able to create a bootable usb stick and I tested on another system and it worked fine.  I then tried it on my system and I get the same results as booting from the cd (It restarts the computer after it loads the kernel).

---

### Post by Pumalite on 2008-07-08
Memory? Graphics?

---

### Post by Fischeja on 2008-07-08
> **Pumalite said:**
> Memory? Graphics?

I have 2GB memory. For graphics, I opened up the case and didn't see a video card.  I have a slim optiplex gx280 and it only has two slots and they are both empty. I assume they are agp and pci express slots. So I'm guessing I'm running off of the onboard graphics.

---

### Post by Pumalite on 2008-07-09
You should give the Alternate CD a try. (text based, easier to use, more control, it avoids possible hardware and/or/graphics problems.

---

### Post by Fischeja on 2008-07-09
I tried the Alternate CD for Ubuntu 8.04, 7.10, and 7.04 and I got the same results.  Ubuntu 8.04 restarted the computer while 7.10 and 7.04 just hung before any prompts came up.

---

### Post by Pumalite on 2008-07-10
Here are some boot parameters to try:
[http://www.hispafuentes.com/hf-doc/HOWTOs/BootPrompt-HOWTO-html/BootPrompt-HOWTO.html#toc1](http://www.hispafuentes.com/hf-doc/HOWTOs/BootPrompt-HOWTO-html/BootPrompt-HOWTO.html#toc1)
[http://d-i.alioth.debian.org/manual/en.i386/ch05s02.html](http://d-i.alioth.debian.org/manual/en.i386/ch05s02.html)
[http://www.tldp.org/HOWTO/BootPrompt-HOWTO.html](http://www.tldp.org/HOWTO/BootPrompt-HOWTO.html)

[http://grumpymole.blogspot.com/2007/05/ubuntu-how-to-edit-grub-boot-parameters.html](http://grumpymole.blogspot.com/2007/05/ubuntu-how-to-edit-grub-boot-parameters.html)
[https://help.ubuntu.com/7.04/installation-guide/hppa/boot-parms.html](https://help.ubuntu.com/7.04/installation-guide/hppa/boot-parms.html)
[http://www.cyberciti.biz/tips/10-boot-time-parameters-you-should-know-about-the-linux-kernel.html](http://www.cyberciti.biz/tips/10-boot-time-parameters-you-should-know-about-the-linux-kernel.html)
[http://www.knoppix.net/wiki/Cheat_Codes](http://www.knoppix.net/wiki/Cheat_Codes)
[http://www.knoppix.net/wiki/Kernel-parameters-2.6.11](http://www.knoppix.net/wiki/Kernel-parameters-2.6.11)
noapic nolapic acpi=off  irqpoll pci=noacpi pnpbios=off vga=0x317 vga=788 vga=789 vga=791 all_generic_ide
To be used alone or in different combinations.

---

