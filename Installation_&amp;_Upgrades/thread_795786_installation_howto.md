---
title: "installation howto??"
date: 2008-05-15
forum: Installation &amp; Upgrades
---

### Post by hey_ram on 2008-05-15
Hi!

i am a newbie to linux...

 i use a laptop that runs XP and open SUSE 10 (dual boot). i want to get rid of the open SUSE distro and install instead Ubuntu (7.01). 

so my problem is this: how do i install a new linux OS(ubuntu) over an existing OS (SUSE)??

thanx..

---

### Post by iaculallad on 2008-05-15
Use your Ubuntu LiveCD to boot from you laptop. On the partition option, just edit the location (Partition) which OpenSUSE resides. Re-create your swap, /, /home directory and don't touch any NTFS drive that you see in order for you to keep you windows OS.

---

### Post by housam on 2008-05-15
Or you can manually reformat the open suse partition by inserting the ubuntu live CD and using the Gparted tool( sys. >> admin. >. partition editor ) .

---

### Post by Sef on 2008-05-16
Read [Psychocat's Installing]("http://www.psychocats.net/ubuntu/installing").

---

### Post by hey_ram on 2008-06-14
thanx to all you guys for the help..
i managed to install 7.10 on my system and keep windows as well!!!

i faced some other problems which i was not able to find an answer to. 

1. i downloaded ubuntu 8.04 (hardy heron) from the ubuntu website.
2. burnt the iso onto a cd and tried to boot the system from the cd. it just did not boot. i tried booting the system with the 7.10 version and it worked just fine.
3. when i looked up the website, the instructions said that i had to unpack the iso image and then try booting the system. 
4. i tried tthat and it still would not boot.

any answers as to y tht must have happened??
i did an MD5sum integrity check on the downloaded iso and it matched with the one provided on the web site.

i am still clueless...

---

### Post by avtolle on 2008-06-14
Since the 7.10 version worked "just fine" (herein assuming you booted the CD upon which you burned the 7.10 iso), first thought is a bad burn. So, as the iso checks out md5sum-wise, burn the iso again to a CD-R (that's what works best for me) at a slow speed (4x) and see if it boots then. Good luck.

---

### Post by housam on 2008-06-14
You just have to burn the iso as it is as an image using the infra recorder . here is the [official instructions]("https://help.ubuntu.com/community/BurningIsoHowto") for doing so.

---

