---
title: "Big pile of hard drives and Sabayon X86_64 install problems"
date: 2007-05-14
forum: Installation &amp; Upgrades
---

### Post by nice68dude on 2007-05-14
Hiya to You all out there! I'm a total n00b on Linux and firstly i want to thank You all so very much for getting me in this nice forum... And a special BIG thank to all people working on this wonderful distro!!!

Now... Every fairytale has a little quirk... I do too :p .

I have a big pile of drives installed in my computer:

1 Maxtor 40 GB (identified as /dev/sdi and the one that should host "Feisty Fawn")
1 WD Raptor 74GB (2 partitions: 1 with Win 2K and one with Win XP: the latter contains the MBR and NTloader. Identified as /dev/sdg)
1 Maxtor 200 GB
1 Maxtor 250 GB
1 WD 250GB
2 Maxtor 300 GB
4 Maxtor 500 GB

Now the problem is: i install FF on the 40 GB drive and everything goes straight but, after the installation completes, it suggests me to install GRUB on /dev/sda(!) and, after rebooting, nothing seems to happen! I Still can boot from the Raptor and "see" the NTloader with default choices (Win2k and XP).

If i mount the ext3 partition created with the Installer i can see the partitions are there, fully installed and populated.

So it seems a GRUB installation problem...

Can please anyone help?

Thank You so very much in advance and forgive my awful english!

Forgot to say i own an AMD X2 4800+ (x86_64), the BIOS is set to find the MBR from the Linux drive. I also tried to switch to the Raptor drive but nothing happens.

David (nice68dude).

---

### Post by logos34 on 2007-05-15
> the BIOS is set to find the MBR from the Linux drive. I also tried to switch to the Raptor drive but nothing happens.

Not sure about the problem booting windows on the raptor, but if Grub was installed on the mbr of sda, then you need to set the BIOS to boot from that drive, not sdi. (During setup Grub gets installed to the mbr of the first detected hard disk which is not always the same drive as your ubuntu install).

---

### Post by joe.turion64x2 on 2007-05-15
> **nice68dude said:**
> Hiya to You all out there! I'm a total n00b on Linux and firstly i want to thank You all so very much for getting me in this nice forum... And a special BIG thank to all people working on this wonderful distro!!!

Now... Every fairytale has a little quirk... I do too :p .

I have a big pile of drives installed in my computer:

1 Maxtor 40 GB (identified as /dev/sdi and the one that should host "Feisty Fawn")
1 WD Raptor 74GB (2 partitions: 1 with Win 2K and one with Win XP: the latter contains the MBR and NTloader. Identified as /dev/sdg)
1 Maxtor 200 GB
1 Maxtor 250 GB
1 WD 250GB
2 Maxtor 300 GB
4 Maxtor 500 GB

Now the problem is: i install FF on the 40 GB drive and everything goes straight but, after the installation completes, it suggests me to install GRUB on /dev/sda(!) and, after rebooting, nothing seems to happen! I Still can boot from the Raptor and "see" the NTloader with default choices (Win2k and XP).

If i mount the ext3 partition created with the Installer i can see the partitions are there, fully installed and populated.

So it seems a GRUB installation problem...

Can please anyone help?

Thank You so very much in advance and forgive my awful english!

Forgot to say i own an AMD X2 4800+ (x86_64), the BIOS is set to find the MBR from the Linux drive. I also tried to switch to the Raptor drive but nothing happens.

David (nice68dude).
I have never seen that amount of hard drives together before, not in the same machine!
And what does Sabayon have to do here?

Joe.

---

