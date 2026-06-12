---
title: "Ubuntu 10.04 will not boot after install"
date: 2010-05-09
forum: Installation &amp; Upgrades
---

### Post by Cloud Wolf on 2010-05-09
Hey,

I just installed Ubuntu 10.04 onto my netbook (HP Compaq Mini 311c) using unetbootin and the iso downloaded off the main site, but it is not booting. It just hangs.

When booting into recovery mode, it hangs on the line
```
[    1.533998] b43-pci-bridge 0000:03:00.0: PCI INT A -> Link[AX3A] -> GSI 16 (level, low) -> IRQ 16
```

If I plug an ethernet cable into the netbook ( I know broadcom wireless cards do not work out of the box) then it hangs instead on
```
[    1.529413] forcedeth 0000:00:0a.0: PCI INT A -> Link[APCH] -> GSI 22 (level, low) -> IRQ 22
```

What is happening and how can I sort it?

EDIT:
10% of the time it allows me to boot into recovery mode. I repaired broken packages, but apart from a new GRUB entry, the problem still exits. Anything anyone can help with? Please!

---

### Post by Catharsis on 2010-05-09
Are you sure it's actually hanging and not just lagging? Does your disc activity light turn off when it stops?

What screens do you see as you boot normally? Where does it hang and what does it look like?

---

### Post by Cloud Wolf on 2010-05-09
Sorry, forgot to say I had solved this myself. It defiantly hangs, as I left it for 3 hours with no change :P

In the end, I managed to boot it into low res graphics mode and install the drivers for my wireless card. all worked after that for some reason. I'm using it now! Thanks anyway :)

---

### Post by SirKonstantine on 2010-05-09
Hey, I just googled this thread. Can you provide more detail as to how you fixed it? I'm also on a HP mini 311 and I'm getting the same messages on boot up.

First, how do you get into low res mode? I'm editing GRUB with 0x303 on single user mode, but I'm still getting the same error.

Also, where is the drivers found at? in the repo or is it from the manufacture?

cheers.

---

### Post by SirKonstantine on 2010-05-10
Bump.

Does can anyone tell me how to get into low res mode? I added "vga=0x303" to grub but I'm still getting the error and it won't boot up all the way.

Thanks.

---

### Post by Catharsis on 2010-05-10
Just go into grub and select the recovery mode kernel.

Enable your wireless drivers through System->Administration->Hardware Drivers.

---

### Post by N2G(bn#7+ on 2010-05-11
**Hey, can you let me know how you fixed this?** 

I'm getting very similar errors but on a Gateway ZA3 (equivalent to the Acer Aspire One 771H I think). I just need to know what to add to the boot options in GRUB to get it into low res graphics mode.

@Catharsis, it won't boot into the recovery mode kernel, as Cloud Wolf said in the first post "10% of the time it allows me to boot into recovery mode." though for me that's 0% of the time.

---

### Post by Catharsis on 2010-05-11
> **erlandh said:**
> **Hey, can you let me know how you fixed this?** 

I'm getting very similar errors but on a Gateway ZA3 (equivalent to the Acer Aspire One 771H I think). I just need to know what to add to the boot options in GRUB to get it into low res graphics mode.

@Catharsis, it won't boot into the recovery mode kernel, as Cloud Wolf said in the first post "10% of the time it allows me to boot into recovery mode." though for me that's 0% of the time.

You can try "xforcevesa".

---

### Post by SirKonstantine on 2010-05-11
SOLVED!

I realized that the problem was because of the broadcom wireless drive so I went to single user mode (recovery) and added the kernel option "noirq"

Boot up to the command line, logged in, typed "start x," and went to restricted drivers and added the b43 driver.

hope this helps you erlandh

---

### Post by N2G(bn#7+ on 2010-05-12
Thanks for your help Catharsis & SirKonstantine.

I've fixed (both) my problems now.

I think the thing that was actually stopping it from booting was that I had installed the new poulsbo packages for 10.04 that tried to fix the problems with the Intel GMA 500 graphics card - that's the last thing I did before it wouldn't boot.

I did a clean install and this time the first thing I did was switch to the proprietary "Broadcom STA" wireless driver.

And just for anyone else out there with the same problems, I then fixed the GMA 500 problems with [this fix]("https://help.ubuntu.com/community/AspireOne/AO751h#Lucid%20%2810.04%29%20workaround-via%20915resolution%20in%20GRUB2") using 915resolution:

[https://help.ubuntu.com/community/AspireOne/AO751h#Lucid%20%2810.04%29%20workaround-via%20915resolution%20in%20GRUB2](https://help.ubuntu.com/community/AspireOne/AO751h#Lucid%20%2810.04%29%20workaround-via%20915resolution%20in%20GRUB2)

Thanks again.

---

### Post by SirKonstantine on 2010-05-13
> **erlandh said:**
> Thanks for your help Catharsis & SirKonstantine.

I've fixed (both) my problems now.

I think the thing that was actually stopping it from booting was that I had installed the new poulsbo packages for 10.04 that tried to fix the problems with the Intel GMA 500 graphics card - that's the last thing I did before it wouldn't boot.

I did a clean install and this time the first thing I did was switch to the proprietary "Broadcom STA" wireless driver.

And just for anyone else out there with the same problems, I then fixed the GMA 500 problems with [this fix]("https://help.ubuntu.com/community/AspireOne/AO751h#Lucid%20%2810.04%29%20workaround-via%20915resolution%20in%20GRUB2") using 915resolution:

[https://help.ubuntu.com/community/AspireOne/AO751h#Lucid%20%2810.04%29%20workaround-via%20915resolution%20in%20GRUB2](https://help.ubuntu.com/community/AspireOne/AO751h#Lucid%20%2810.04%29%20workaround-via%20915resolution%20in%20GRUB2)

Thanks again.

LOL

The B43 driver worked for one night, but when I turned it on in the morning, I got the same error again.

I tried booting with "noirq" but it didn't do the trick so I went with "noirq noapci apci=off noacpi acpi=off" because I could not remember what command was what. Guess what? that let me logged in and I switched to the STA driver also.

Works perfect now.

---

### Post by N2G(bn#7+ on 2010-05-16
> **erlandh said:**
> And just for anyone else out there with the same problems, I then fixed the GMA 500 problems with [this fix]("https://help.ubuntu.com/community/AspireOne/AO751h#Lucid%20%2810.04%29%20workaround-via%20915resolution%20in%20GRUB2") using 915resolution

Well, not quite - there's still a bunch of problems like you can't adjust screen brightness & the frame rate is horrible so you can't watch videos full screen, etc.

---

