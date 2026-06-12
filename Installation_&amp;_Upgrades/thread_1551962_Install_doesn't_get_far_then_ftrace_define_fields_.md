---
title: "Install doesn't get far then ftrace_define_fields_sys_exit"
date: 2010-08-13
forum: Installation &amp; Upgrades
---

### Post by Bike_13 on 2010-08-13
There has been some progress - see later posts please.....


Hi all,

I have just purchased a new PC (HP All-in-one 200) and of course want to install 10.04 LTS on it.

I have created a boot USB and when I boot , and select to try Ubuntu (ie not install) the following seem to complete fine:

Loading /casper/vmlinuz ...........
Loading /casper/initrd.lz .............

Then I get a black screen with the following detail scrolling (computer hangs) "? ftrace_define_fields_sys_exit +0x3b/0x90" (there is also some mention of IRQ as well .....

Any suggestions?:confused:

Thanks, J

---

### Post by dino99 on 2010-08-13
you might try to boot by adding on the boot line: irqpoll and/or nomodeset, noacpi, nolapic, noapic

better to remove quiet splash to see all the verbose process and know about errors, that help to go ahead

---

### Post by Bike_13 on 2010-08-13
> **dino99 said:**
> you might try to boot by adding on the boot line: irqpoll and/or nomodeset, noacpi, nolapic, noapic

better to remove quiet splash to see all the verbose process and know about errors, that help to go ahead

Thanks dino. I am not too technical, so do you mean turning on the F6 options for "irqpoll and/or nomodeset, noacpi, nolapic, noapic"?

How do I "remove quiet splash"?

Thanks a heap, J

---

### Post by Bike_13 on 2010-08-14
Groovy, managed top get the live CD working by checking all the options available by pressing F6 immdeiatley after selecting the live CD option.

Fingers crossed for the install ....

---

### Post by Bike_13 on 2010-08-26
So, I have managed to get the 10.04 Live CD to boot, using "noacpi", but now I am unable to get wireless to work. 

***Would this be an issue with the PCI Express slot that the wireless card is installed in?***

***I did use 32-bit, should I be trying 64-bit?***

If I install using "noacpi", does this mean that ACPI funstionality won't work on the machine once Ubunut is installed?

Thanks for your help - trying to work out if I persist, or take the machine back to the shop (would prefer not - I like it - but I don't want to have to live with Win7).

J

---

