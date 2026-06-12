---
title: "No Boot Loader...."
date: 2006-08-12
forum: Installation &amp; Upgrades
---

### Post by Sarkamen on 2006-08-12
Hi, I am sorry if I am doing something stupid here. For the last hour I have been cycling from booting from the cd. Making a partition installing, then it says at the end "If you restart now please remove the CD so it doen't boot back up from the live cd" er uh I paraphrased but anyway. I tryed removing the cd but the drive wont open then it starts booting and get to a "please remove cd if there is one in the drive. So I do and it restarts saying cannot load operating system.](*,) 

 OK, so I have a version of XP on the same drive with the Ubuntu partion and when using the live cd I can't see anything on either of my 2 installed HDs.A friend took me through some steps for mounting and what not but I kept getting already mounted or busy responses. Then he found out apprently I can't access the drives from live cd? I am including that hoping it may be of some use..... My final thoughts are I need to maybe manually install the boot loader which I though what supposed to be installed before the reboot. Please HELP! Thanks in advance!

Edit: Oh, excuse my limited knowlege after reading some other posts it seems grub must have been installed before the reboot prompt but I wasn't watching :-k 

-Sark_Amen

---

### Post by confused57 on 2006-08-12
I'm not sure what's going on, but yes, grub should have been installed to the mbr, then the CD drive should open automatically then you remove the CD, close door and press "enter", then your system is supposed to reboot...sounds like this didn't go exactly as it should have.

You could try booting up with the Live CD, open a terminal(Applications---Accessories---Terminal), enter:
```
sudo fdisk -lu
```
This will show your partition table.
You can mount partitions or hard drives:
[http://psychocats.net/ubuntu/index.php](http://psychocats.net/ubuntu/index.php)
See the "Mount Windows" or "Mount Linux" sections.

If you want to get your Windows booting again, you can bootup with the Windows Install(not the recovery one) CD, press "r" for recovery mode, then enter **fixmbr**, which should repair your mbr and enable you to boot Windows again...you could also try to reinstall Ubuntu again, later.
Here's a link for recovering Windows:
[http://www.users.bigpond.net.au/hermanzone/p18.htm](http://www.users.bigpond.net.au/hermanzone/p18.htm)
Here's a link for installing Ubuntu:
[http://psychocats.net/ubuntu/installing.html](http://psychocats.net/ubuntu/installing.html)

---

### Post by Sarkamen on 2006-08-13
hmm thanks alot, haven't tryed fixmbr yet but this solves my original problem and means I don't need to even install ubunto to do what I needed to do. If you don't mind answering a few newbie questions, I can't figure out how to change to a directory with spaces in the name:-#  I know I know.....my original purpurse in using this OS was to possibly recover some files off my second HD that are inaccessible in XP for reasons unknown.....if anyone can tell me if that's even possible and or help with the above mentioned command issue that would be great....thanks! :mrgreen:


Edit:Woot screw it I figured out an easy way... now I just have to figure out how to copy the directory.....any help would be great in the meantime I am gonna search newb guides for commands to help.....

---

