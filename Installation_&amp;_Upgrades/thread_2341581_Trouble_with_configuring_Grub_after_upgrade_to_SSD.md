---
title: "Trouble with configuring Grub after upgrade to SSD: No such device ... Grub rescue."
date: 2016-10-29
forum: Installation &amp; Upgrades
---

### Post by steco on 2016-10-29
I am having big troubles with properly configuring Grub after having changed/deleted some partitions. This was the scenario after I did a fresh install of Ubuntu 16.04 on my new installed Notebooks internal SSD:

Internal SSD with MSDOS:

```
Device     Boot      Start        End    Sectors   Size Id Type
/dev/sda1   *         2048  235522047  235520000 112,3G  5 Extended
/dev/sda2        235522048 1362749439 1127227392 537,5G 83 Linux                    # Used as data partition
/dev/sda3       1362749440 1444669439   81920000  39,1G 83 Linux                    # Used as empty spare partition
/dev/sda5             4096   16388095   16384000   7,8G 82 Linux swap / Solaris     # swap
/dev/sda6         16390144   98310143   81920000  39,1G 83 Linux                    # /
/dev/sda7         98312192  235522047  137209856  65,4G 83 Linux                    # Home
```

After having installed and configured Ubuntu I have swapped my Notebooks DVD drive for the original HDD which was installed before I swapped for the SSD. At this time the HDD still did contain a dual boot install of Mint and Windows 10 (unfortunately I can't post an 'fdsik' anymore). Because I did an 'update-grub' from the SSD with the aforementioned configuration from now on I always had to go into my boot manager when starting the Notebook to select the boot from SSD. Otherwise the old grub menu would have shown up which was related to the dual boot on the HDD. When I picked the SSD for booting grub would also show up but with the old Mint and Windows install as well as the new Ubuntu install.

Now to the tricky part: I have recently deleted every partition of the former dual boot HDD and created a new empty NTFS partition to be used as an internal backup storage. Then I did another 'update-grub'. From now on each time I am booting my Notebook I get the following error message: ```
error: no such device: ... Entering rescue mode... grub rescue>
```
What I tried was setting 'prefix' to grub path and setting the 'root' parameter, after that 'insmod normal' and 'normal' which was bringing me to the new Ubuntu install perfectly fine. There I did an 'sudo grub-install [--force] /dev/sda/' and another 'sudo update-grub'. Unfortunately when rebooting I am still getting the error message. I also tried an 'sudo apt-get update' and deleting the NTFS partition. BIOS setting should be fine as well. What else could I try that will hopefully fix the Grub configuration? I really dont want to do another fresh install.

Greetings!

Edit: Btw when I am manually picking the SSD at startup/boot everything is working well. So may the problem just be a wrong boot order? This is actually configured the right way but I am a little afraid that the HDD installed in the DVD drive could be the reason for this trouble...

---

### Post by ajgreeny on 2016-10-29
See Boot-Repair in my signature below and follow the instructions there to run the Boot-Info-Script.	 
**Do not run the default repair just yet** but simply copy back here the pastebin link you get which will show us a lot more about your system.

---

### Post by steco on 2016-10-29
I finally fixed this. The problem was not related to Grub but instead to the BIOS/UEFI menu of HP. Inside the boot ordering tab there was another group for the installed hard drives and only the first one (in my case the HDD in the caddy) was shown. Only by using the F-keys it was possible to change the first hard drive to the new installed SSD (which even didn't showed up at all before). Anyway thanks a lot for answering!

---

### Post by ajgreeny on 2016-10-29
Great! Please mark as SOLVED from the Thread Tools menu up-top if this is now solved to your satisfaction. It is a great help to users searching the forum.

---

