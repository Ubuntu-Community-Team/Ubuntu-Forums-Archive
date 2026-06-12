---
title: "BURG install problems"
date: 2011-08-10
forum: Installation &amp; Upgrades
---

### Post by john2307 on 2011-08-10
Hi, this is my first post and I am newer to ubuntu so I will apologize in advance for any redundancy in this post. I have searched for similar problems, but could not find a solution 

I am running 10.10 with a dual boot windows XP through wubi, and I thought I would try to install burg so I could get a more interesting boot up screen. I didn't realize you shouldn't do this with wubi. I now get

GRUB loading.
error: no such device: 00d084ba-0cee-42c4-b7a1-d3739f923677
Entering rescue mode...
grub rescue>

prompt at start up and get no further. I created an ubuntu live cd and can boot off of that, but I am not sure where to go from this point. I am hoping I didn't just lose all of my files on the ubuntu part of the hd and if I didn't already, hopefully I can avoid it..

If somebody could walk me through this I would be very thankful. 

The procedure I followed is here:
[http://www.howtogeek.com/howto/45164/how-to-customize-the-ubuntu-bootloader-screen/](http://www.howtogeek.com/howto/45164/how-to-customize-the-ubuntu-bootloader-screen/)

The forums I looked at:
[http://ubuntuforums.org/showthread.php?t=1600373](http://ubuntuforums.org/showthread.php?t=1600373)
[https://help.ubuntu.com/community/Grub2#Copy](https://help.ubuntu.com/community/Grub2#Copy) LiveCD Files

---

### Post by dino99 on 2011-08-10
how to do a real install:

[http://ubuntuforums.org/showpost.php?p=10161428&postcount=2](http://ubuntuforums.org/showpost.php?p=10161428&postcount=2)

[http://www.unixmen.com/linux-tutorials/linux-distributions/linux-distributions4-ubuntu/1679-how-to-install-burg-in-ubuntu-](http://www.unixmen.com/linux-tutorials/linux-distributions/linux-distributions4-ubuntu/1679-how-to-install-burg-in-ubuntu-)

---

### Post by Rubi1200 on 2011-08-10
Hi and welcome to the forums john2307 :)

As you discovered, BURG and Wubi do not mix well.

Use the Ubuntu LiveCD to boot the computer and then follow the instructions at the bottom of my post to run the boot info script.

Post the results here and we can take it from there.

---

### Post by bcbc on 2011-08-10
I just want to add that the error you are getting looks particularly serious... but it's not. It's just the Windows bootloader in the drive MBR that you pooched. So don't do anything drastic (all your files are still there on both Windows and Ubuntu).

---

### Post by john2307 on 2011-08-11
Thank you for all of your help. The problem has been solved very easily with the following:

sudo apt-get install lilo
sudo lilo -M /dev/sda mbr

It didn't work originally because the computer was not connected to the internet off the live cd... Thanks again!

---

### Post by Rubi1200 on 2011-08-11
Excellent! Glad you got this sorted out :-)

Please mark this Solved using the Thread Tools near the top of the page.

---

