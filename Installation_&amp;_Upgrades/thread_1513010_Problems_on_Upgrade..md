---
title: "Problems on Upgrade."
date: 2010-06-18
forum: Installation &amp; Upgrades
---

### Post by tattushenoi on 2010-06-18
I am relatively new to Linux. Only a few weeks old. I had Karmic Koala  installed on my system along with windows xp. I have 3 partitions. 15Gb  for Linux. 18 for XP and one 43 Gb for data. 

I upgraded to Lucid Lynx recently. I have 2 queries.

1) In Karmic Koala I had set passwords to open my partitions. But after I  upgraded to Lucid Lynx, the partitions are opening without asking for a  password. But if I try to install a program it asks for authentication.  Only while opening a partition it is not asking anything.

I want Ubuntu to ask for a password everytime I open a partition. What  should I do?

2) After the upgrade I chose to keep the 'present version of grub' when  asked for choice[maintainers version etc etc]. But now I get to see the  option for Karmic Koala login as well in grub. But if I try to select  that it says there is no such thing installed and rightly so. I want  that extra option removed as Karmic Koala is no longer there. 

Please provide suggestions.

---

### Post by tattushenoi on 2010-06-18
To add about the Grub problem, I got this when I ran sudo update-grub.


tattushenoi@TATTUS:~$ sudo su
[sudo] password for tattushenoi: 
root@TATTUS:/home/tattushenoi# sudo update-grub
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.32-23-generic
Found initrd image: /boot/initrd.img-2.6.32-23-generic
Found linux image: /boot/vmlinuz-2.6.31-22-generic
Found initrd image: /boot/initrd.img-2.6.31-22-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Microsoft Windows XP Professional on /dev/sda2
done
root@TATTUS:/home/tattushenoi#

---

### Post by tattushenoi on 2010-06-19
any one?:confused:

---

### Post by tattushenoi on 2010-06-24
Any one with solution?

---

### Post by tattushenoi on 2010-07-05
Some one help me please.

---

### Post by tattushenoi on 2010-07-11
now after one more upgrade 3 options are being shown....22 23 and 24...how do i remove them ?
my grub is too crowded

---

### Post by bondo101 on 2010-07-11
Well its time to start all over again reload your karmic I am assuming you have your karmic cd . I hoped you backed up all your files. I am assuming that xp is still there . Don't up grade from the internet get a cd with lucid on it .Run your karmic or your lucid cd. you will have to clean up all the grubs you have started.and put a fresh lucid or karmic back on your drive. If you just get rid of one of the grubs sometimes it won't boot. 22 should be karmic 23 should be lucid. get back to bacis get one or the other working .when you get it working again use virtual box for xp. I have karmic on one partion on my drive and lucid on the other. I personally like karmic better.Hope this helps I am learning also don't have all the answers .:)

---

