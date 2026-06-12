---
title: "Raid 0, ubuntu, windows, grub and SSD"
date: 2012-07-01
forum: Installation &amp; Upgrades
---

### Post by Gargintua on 2012-07-01
ubuntu is installed by itself on a ssd. 

i made a stable raid 0 on a gigabyte mobo with 2 320gb HDDs.

I installed windows 7 on the raid 0

but apparently the raid 0 has "fAILED"
even though i can access files on the raid 0 from ubuntu

grub boots ubuntu fine but cant boot windows because the raid has apparently faileed

has ubuntu caused the raid 0 to fail and how can i keep teh raid 0 stable with ubuntu and windows on different HDDs/SDD?

---

### Post by Gargintua on 2012-07-02
maybe theres not enough time during the bios for the HDDs to spin up in order to be be recognized as a raid??

---

### Post by darkod on 2012-07-02
This is a strange situation. I have no idea if ubuntu can break the raid and why.

One thing that can happen is if it's not seeing it as raid at all. Because ubuntu was first installed on the SSD, it couldn't detect the raid during installation.

Usually you activate existing fakeraid with something like:
sudo dmraid -ay

Not sure if that can help, or if it will keep it activated after reboot. Maybe it would have been better to install win7 on the raid first, and then install ubuntu with the raid already present.

---

### Post by Gargintua on 2012-07-02
ok raid is being recognized fine now after a cold shutdown (not a quick restart).
i think it was because of the time recquired for the hdds to spin up
it works on and off
its good enough for me i have enough control to choose windows or ubuntu

if anyone has any questions just lemme know thanks

---

