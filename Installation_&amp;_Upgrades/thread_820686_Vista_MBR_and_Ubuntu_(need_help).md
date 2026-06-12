---
title: "Vista MBR and Ubuntu (need help)"
date: 2008-06-06
forum: Installation &amp; Upgrades
---

### Post by eynestyne on 2008-06-06
I recently decided to try ubuntu. never used anything other than windows.

I have a HP laptop with vista. I installed ubuntu on an external drive and it worked ok. But, grub was installed to the internal drive of the laptop.

Is there a way to install ubuntu and grub to the external drive? I don't want any changes to the internal drive.

The laptop bios gives me the ability to boot from the external.

---

### Post by Pumalite on 2008-06-06
Yes. on step 8 of the installation go to 'Advanced Tab' and change (hdo) for /dev/???
Where ??? is your USB drive.
You can find out with sudo fdisk -l
In the meantime, fix your Windows MBR with Super Grub:
[http://users.bigpond.net.au/hermanzone/supergrubdiskpage.html](http://users.bigpond.net.au/hermanzone/supergrubdiskpage.html)

---

### Post by eynestyne on 2008-06-06
thanks, i'll do that

---

### Post by Pumalite on 2008-06-06
You are welcome.

---

### Post by eynestyne on 2008-06-06
ok, i ran the installation again but there was no step 8; steps go up to 7. i did not go pass step 4 because i did not want to have to repair the mbr again. in step 4 i had the option of selecting guided or manual for creating the partition. please advise on now proceed from here.

---

### Post by eynestyne on 2008-06-06
i also see my internal drive is listed as sda and the external as sdb

---

### Post by Pumalite on 2008-06-06
Go Manual and choose sdb

---

### Post by Herman on 2008-06-06
The following illustrated guide shows you how to access the boot loader options in step 7 of the 'Desktop' CD installation, [COLOR=#000000][Hardy Heron LTS / Windows XP Dual Boot Installation A]("http://www.herman.linuxmaniac.net/p24.html").
Type an alternative location for GRUB in the field titled 'Device for Boot Loader Installation', or click on the arrow button to the right of that feild for a drop-down menu with a list of possible locations and select one from the list.
That how-to shows 'guided partitioning though.
This one shows the same thing again, but shows the Desktop CD installation using the manual partitioning, [/COLOR][COLOR=#000000][Hardy Heron LTS / Gutsy Gibbon Graphical Installation B]("http://www.herman.linuxmaniac.net/p23.html").

Regards, Herman :)
 [/COLOR]

---

