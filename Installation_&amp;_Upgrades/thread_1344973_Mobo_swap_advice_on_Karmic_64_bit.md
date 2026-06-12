---
title: "Mobo swap advice on Karmic 64 bit"
date: 2009-12-03
forum: Installation &amp; Upgrades
---

### Post by apesa on 2009-12-03
Hello,
I have a well tuned and great running 9.10 64 bit desktop. It is running an AMD Phenom 955 Quad core with 4Gb mem on an ECS Black 785 Mobo with a Radeon 4890. 

I want to swap the ECS 785 with a Gigabyte GA-790XTA-UD4 mobo because I need more PCI E slots and I already have it on hand. My question is will I run into any issues with getting the box back up after the swap.

What would be the best way to accomplish this short of a new install.

Thanks for any advice,
Pat

---

### Post by u.b.u.n.t.u on 2009-12-03
HDD(s) are read by the BIOS at boot, and such is specific to the mainboard. 

Just make sure the new mainboard BIOS is correct in the detail you input, install the HDD(s) in the correct order (if more than one) and then boot.

As long as you attach the HDD connections correctly, set up the mainboard correctly, set up the BIOS correctly, it should work.

It is essentially a hardware and not a software question.

---

### Post by apesa on 2009-12-03
Thanks for the input. I failed to mention that I am currently booting from a mobo supported RAID1 mirror. 2x500gb HDD's. I knew I forgot to add something to the original post.

I was thrilled that 9.10 supported the RAID1 setup that I had config'd in the BIOS prior to install. But I am unsure I will have the same success when swapping mobo's. My plan is to boot straight to the BIOS and configure the RAID1 support there and then reboot and cross my fingers that it boots and shows up as a single drive.

Thanks again for the input.
Pat

---

### Post by u.b.u.n.t.u on 2009-12-03
All the best. No doubt you will be consulting the mainboard manual extensively during the process.

Once you have everything setup on the hardware front, consider taking a breather, go back to it and just double check everything.

Everything is correctly plugged in, nothing left undone.

Once you have done all that then boot up.

You know about ridding yourself of static (touch a metal object like a metal door frame etc), and do turn off AND unplug the power cable. Work in a well lit environment and make sure you have all the space and any work tools you may require.

---

