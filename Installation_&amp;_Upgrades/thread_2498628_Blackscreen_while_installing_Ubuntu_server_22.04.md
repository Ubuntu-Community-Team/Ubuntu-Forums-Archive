---
title: "Blackscreen while installing Ubuntu server 22.04"
date: 2024-06-22
forum: Installation &amp; Upgrades
---

### Post by outnumbered on 2024-06-22
Hello guys,
I have had a problem for some time now which is driving me crazy:
I am trying to equip my self-built server with Ubuntu server 22.04. Previously I had TrueNAS Scale on it. The problem now is the following:
After I select "Try or Install Ubuntu ..." and console output appears on the screen for a while, the installation does not continue and a black screen appears.
No error messages or other things that could indicate a faulty installation appear beforehand.

I am using a 3.0 USB with the installation ISO compiled with rufus (I tried balenaEtcher as well), I've set the BIOS to fast boot OFF and safe boot OFF as well.
The requirements of Ubuntu server 22.04 are more than adequately provided. Maybe something to mention is that I am using no GPU but an AMD Ryzen™ 5 5600G Desktop Processor with Radeon™ Graphics.

If you need any more information feel free to ask I'm desperate because I am also fairly new to this matter.

---

### Post by Rubi1200 on 2024-06-22
If this is a new/fresh install is there a reason not to install the latest LTS, 24.04?

I would recommend choosing to write in dd mode with Rufus and check if that helps.

Alternatively, when the try or install Ubuntu line comes up, press e and remove quiet splash and type nomodeset instead.

Then Ctrl+X to continue booting.

Does that help?

---

### Post by outnumbered on 2024-07-07
Hi!
First of all: sorry for the late reply. I was on vacation and couldn't try it out.

I tried writing in dd mode but it didn't help. I also tried editing in the GRUB menu like you said but there is another problem.
I opened the editor with e and the only thing in there is following:
```

setparams 'Try or Install Ubuntu Server'
set gfxpayload=keep
linux    /casper/vmlinuz  ---
initrd   /casper/initrd

```

And btw. I used the new LTS 24.04 as well.

Hope you can still help me :´(

---

### Post by him610 on 2024-07-08
> AMD Ryzen™ 5 5600G Desktop Processor with Radeon™ Graphics.
Been running LTS Xubuntu 22.04.4 without any issues using AMD 5 5600G APU for several months now.

When I upgraded from a Ryzen 5 2600 (no integrated graphics) to Ryzen 5 5600G, it was necessary to upgrade my AsRock B450M motherboard firmware before I installed the Ryzen 5 5600G. 

Does your motherboard have the latest firmware release?

---

### Post by outnumbered on 2024-07-09
Hi,
I checked my BIOS version and did see that its wasn't the latest one so I updated it to latest 4604.
But unfortunately it didn't solve the issue. I still get the blackscreen :(

Thank you for the suggestion updating the firmware.

Anyone got other ideas??

Edit:
Oh and btw. I checked again editing in the GRUB menu but it still only has this content:
```

setparams 'Try or Install Ubuntu Server'
set gfxpayload=keep
linux    /casper/vmlinuz  ---
initrd   /casper/initrd

```

---

