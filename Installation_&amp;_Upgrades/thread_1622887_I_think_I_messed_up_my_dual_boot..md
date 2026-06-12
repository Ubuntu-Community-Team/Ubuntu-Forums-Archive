---
title: "I think I messed up my dual boot."
date: 2010-11-16
forum: Installation &amp; Upgrades
---

### Post by cheung.louis_f on 2010-11-16
I have a Dell pc with a 250 GB internal hd. I partition as I remember around 88(or 18GB not sure)GB for Ubuntu 10.4 LTS. I first reformats with Window Vista, then I install Ubuntu with by restart with disc inside. The 18GB of space was partition by Ubuntu. 

Problem start here. I either reformat (Vista) or install (Ubuntu) with my external hard disk plugged in. So without the external hhd plug in, I will not meet the screen with GNU list for me to choose to boot with Vista or Ubuntu. Even with if I press F12 and choose boot from bootable hard disk it will get something like GNU rescue. 

If I keep the ex.hhd plug in then unplug it after choosing to boot from Vista. I will get a blinking screen with Red, Green Yellow...

If I log in Ubuntu I hear it is my external hdd loading instead of my internal disc. If I had have my ex.hdd unplug while running Ubuntu. All the icons will turn in to red "x". 

So which let me draw the conclusion that I install the boot sector and Ubuntu OS into my external hard disk. I dun know very much about computer.

I hope somebody can help me.


Internal Hrd disk
*(see first attachment*)

External Hard disk (label as Extended 88GB)
*(Second attachment)*

---

### Post by Rubi1200 on 2010-11-16
Hi and welcome to the forums :)

If you are able to boot into Ubuntu normally or use a LiveCD to boot the computer, then please follow the instructions in the link at the bottom of my post.

We need you to post the results back here so we can offer solutions.

Thanks.

---

### Post by cheung.louis_f on 2010-11-16
Anyone has more specific method to help me? How I can erase the Ubunut OS with the partition from my external hard-disk.

---

### Post by Dex73 on 2010-11-17
Run Ubuntu from the startup disk and then connect to the external drive. Now go to system/administration/gparted. (Gparted is a application that lets you change sizes and other features when dealing with partitions.) Last step, play with the partition using gparted to fix it. I think that should/could work.

NOTE: gparted will not be their if your not running Ubuntu off the start up disc.

---

### Post by wilee-nilee on 2010-11-17
> **cheung.louis_f said:**
> Anyone has more specific method to help me? How I can erase the Ubunut OS with the partition from my external hard-disk.

the advice from rubi1200 is spot on and couldn't be much easier, if you just take the time to read the instructions. Trying to fix this without the information given by running this script is basically flailing in the dark. This is standard procedure here I would take advantage of this feature.;)

Do you want advice that without some pertinent info that may make things a lot longer in trying to help and may bork your setup completely?

---

