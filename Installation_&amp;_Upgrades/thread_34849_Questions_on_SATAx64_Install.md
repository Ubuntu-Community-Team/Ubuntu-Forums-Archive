---
title: "Questions on SATA/x64 Install"
date: 2005-05-16
forum: Installation &amp; Upgrades
---

### Post by Crazy_Monkey on 2005-05-16
Put simply, does it play nice?

I ordered a 250 gig SATA to put all my data on, freeing up a 80gb PATA drive for an Ubuntu install I've been wanting to put on for a long time now. BUT, I've been reading that Ubuntu doesn't like SATA all that much. And since the MBR is on my windows system drive, which is an SATA drive, I was going to post and get some feed back from some pros.

Does it "Just Work"? Or will I have to do a GRUB workaround?

System specs in sig.

---

### Post by pointym5 on 2005-05-16
I have no problems with a new 250GB SATA drive on my setup.  Ubuntu detects it as "sda", and my two real SCSI drives as "sdb" and "sdc".  My system is on the SCSI drives, but (I think) the MBR is written to the SATA drive with GRUB pointed at the boot partition on the first SCSI drive for stage 2.

---

### Post by DutchLau on 2005-05-16
It "just worked" with me. I`m sure it will work with you also :P

---

### Post by Sam on 2005-05-16
Everthing was fine for me. I'm running Ubuntu 64bit with two 120Go SATA.

---

### Post by Crazy_Monkey on 2005-05-17
Hey everyone, thanks for the replies! I'll be able to install with a bit more confidance.

My only question is of the dual boot and PATA/SATA cross-controller nature. All of you seem to be talking about single boot (Ubuntu) and SATA only, whereas I'd like to begin with a dual boot with Ubuntu on a PATA and windows with the MBR on a SATA.

Is there a better way other than putting Grub in the MBR on the SATA and install on the PATA? I've NEVER had any luck in this configuration, from Gentoo to Debian, they all bomb hard with error 22 or just never even coming back from the installer's initial reboot.

Still, the quick and assuring replies boost my confidence in trying Ubuntu. Thanks!

---

