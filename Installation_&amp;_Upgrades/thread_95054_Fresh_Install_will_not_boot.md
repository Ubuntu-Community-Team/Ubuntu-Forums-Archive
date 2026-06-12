---
title: "Fresh Install will not boot"
date: 2005-11-25
forum: Installation &amp; Upgrades
---

### Post by zootreeves on 2005-11-25
I don't know whether this is a problem with my motherboard, bios, hard drive or ubuntu...

I have just installed ubuntu on my brand new 160GB maxtor (which I got from ebay) however when I plug the IDE cable in and turn the PC on it just says insert system disk (Which I presume means it found nothing to boot from) - I have no CD or floopy attached. When I saw this first I automatically thought it was a problem with the hard drive or cable, so I used the same IDE cable to try the hard drive in my other PC and it booted straight away into ubuntu...

I upgraded the bios of the mobo (Asus P4S800) to the latest version, but it still won't boot. Also I tried the 80GB hard drive with windows on from my other PC and It booted straight away. Does the Ps4800 no support 160GB hard drives or something? Please help...

---

### Post by zootreeves on 2005-11-25
Are ATA and IDE the same thing? The Asus P4S800 supports IDE and my hard drive says "ATA / 133" is this the reason why it will not work? The hard drive is recognised in windows though when I put using the 80GB one with it still connected....

Please tell me i'm not right...

---

### Post by bwog on 2005-11-26
There are 2 kinds of cable for IDE hard disks (40 or 80 conductor cable). Did you get a cable with this new hard disk?

Check the manufacturors site for the cable that goes with your disk and the jumpersettings (master slave) on the hard disk.

I cant imagine how you could have installed with the wrong cable though, unless you installed on another disk. Can you clarify this?

---

### Post by zootreeves on 2005-11-26
The cable did not come with the drive, but it works with the drive if I put is in my other PC. The cable says on it ATA 100 when the rive says ATA 133, could that be the problem? When I installed ubuntu it was the only drive connected and it installed without error...

---

### Post by bwog on 2005-11-26
So you installed ubuntu on this drive with the drive in another PC? 

Do check the manufacturors site for the cable and master/slave settings, those things are also on the manual that you get with your maxtor. It is probably ok but you have to be sure.

Edit: the Asus P4S800 motherboard has 2 x UltraDMA 133/100 so that should be ok.

---

### Post by Tiede on 2005-11-26
I was just checking the specs for your motherboard, it seems like it should be able to support high capacity HDs... But since you said that you installed Ubuntu on  another PC, I was wondering if you overlooked going into the BIOS and setting the Disk as a bootable one?
It is just too easy a step to be overlooked.

---

### Post by zootreeves on 2005-11-26
Thanks for your help....

No I installed ubuntu on the PC which won't boot, I tried it my other Pc and it booted fine. I just went and bought a new IDE cable which says ATA 133 on it - still no improvement. It seems that everything is working but not together...

In the BIOS only sometimes is the hard drive detected - Other times it just says None For both primary mastor and slave. I have set it to boot from the hard drive 1st. I have tried every jumper setting in the manual. I don't know whether it needs a 40 or 80 conductor cable - but the cable works when I try it in the other PC so I presume It must be correct.

---

### Post by bwog on 2005-11-26
[QUOTE=zootreeves]
In the BIOS only sometimes is the hard drive detected - Other times it just says None For both primary mastor and slave. I have set it to boot from the hard drive 1st..[/QUOTE]

That still looks like a hardware problem, autodetection by the motherboard has problems. What does the manual of the motherboard say about drive settings? It could also be a defective connector.

From your answers it seems that the empty disk was detected. It was formatted in ext3 by the install disk, you installed and now it is not seen by the motherboard.

Perhaps you can see in what state the partitions are when you plug it in the other computer?

---

### Post by Tiede on 2005-11-26
I actually had the same prob' with my old PC, zootreeves. The omtherboard sometimes would recognize my HD, sometimes say it has a failure, sometimes not see it at all...
I dunno how to fix it, however, since BOTH the mobo and the HD died on me. (So I am thinking that it might be a sign you should change one of 'em).
I hope i am wrong, for your pocket's sake ;)

---

### Post by zootreeves on 2005-11-29
got a new PCI IDE controller and it booted striaght away, so must have been the motherboard.

---

### Post by bwog on 2005-11-29
That is great. Good thinking.

---

