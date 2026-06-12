---
title: "fiesty install"
date: 2007-04-24
forum: Installation &amp; Upgrades
---

### Post by n8ek on 2007-04-24
I am trying to install kubuntu feisty on to a 300g SATA partitioned HD, the partition i want it to go on is /media/sda2 or /dev/sda2 which is 25g everything goes ok (i think) then at the end it shows an error box saying "Executing 'grub-install (hda1)' failed.

how can i get it to install grub?
Thanks in advance

---

### Post by bulldog on 2007-04-24
Do you have more than one hdd?
It should install to (hd0) instead of (hda1).

---

### Post by n8ek on 2007-04-24
Ive tried that and it still comes back with the same error

---

### Post by bulldog on 2007-04-24
Yes,but do you have more than one hdd?
Is there for example an IDE hdd in your system?

---

### Post by n8ek on 2007-04-24
Yes there is as a slave as i type this i am trying to get it to install grub on hdd5

---

### Post by bulldog on 2007-04-24
If you have the choice on which hdd you want to install GRUB,I would recommend to use the hdd were you installed ubuntu.
Make this disk the master boot device.

About your IDE,this one should be a master hdd,because GRUB will install to the first IDE hdd by default.
I think when this is a slave device you'll get this error.

To install GRUB you need to use (hd0),(hd1) and so on.
If you use something as hdd5 it will fail for sure.

---

### Post by Annie Versary on 2007-04-24
Hi n8ek,

according to my experiences (with Ubuntu _not_ Kubuntu - but that shouldn't matter) you just have to try the installation of GRUB **twice**.

After getting the error message that "Executing 'grub-install (hda1)' failed" just return to the menu listing the installation agenda (if you haven't already been redirected there) and select "Bootloader installation" or something like that. Second attempt always worked for me :)

Annie

---

### Post by n8ek on 2007-04-24
The partition i am trying to put it on is /dev/sda2. i have tried to install grub on sda, sda1 /media/sda1 ect i will give it 1 last try b4 i give up.

---

### Post by n8ek on 2007-04-25
i have now removed the ide drive and carryied on with the install but it still will not load grub?

any ideas any one

thanks in Aadvance

---

