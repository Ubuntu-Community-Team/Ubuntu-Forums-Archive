---
title: "[SOLVED] Help! Trying to install Hardy Heron...epic fail"
date: 2008-06-20
forum: Installation &amp; Upgrades
---

### Post by fiddler616 on 2008-06-20
Hello,
So I've been trying to get a dual-boot (windows xp, ubuntu) on my laptop for the past week or so, and after bad experiences with Wubi, went the old-fashioned way with a live CD. It was made fine, and when I booted, I chose "Try Ubuntu" because a very techy friend was going to walk me through the installation process through IM. We got up to about step 3, when the previously slow process slowly ground to a halt (complete with gray screen), and I ended up hardbooting.
On take two, I just did "Install Ubuntu", because it seemed pretty straightforward, and I wanted it to be a bit faster.
So I succesfully completed the installation, putting it on my Western Digital external USB drive. Ubuntu told me to reboot. I did. It popped out my CD, and then gave me "Error 21", and something about Grub (Sorry, I'm not willing to jeopardize this web connection to get the exact wording). So I definitely want my Windows back (I saw nothing about dual-booting), and if some smart person gets me a working dual-boot, great, but I chiefly want an un-wiped Windows because my mom needs her Outlook Express, complete with old messages, and isn't the type to make the switch to Evolution.
Thanks...

---

### Post by easybake on 2008-06-20
You should be able to simply unplug your drive and reboot if you loaded Ubuntu only on the external. Now if you did a clean install you might have a tougher time getting your windows back.

---

### Post by fiddler616 on 2008-06-20
I did try that, and it gave me the same Error 21.
Incidentally, and I don't know if this is relevant or not, I can access all of my hard/CD drives in Ubuntu...except for the C drive (different name, but whatever). In my laptop, I have both C and D, and the external is partitioned (F and G?). So I feel like it's weird that I can get D but not C...

---

### Post by onlineapps on 2008-06-20
I think the problem is that GRUB is installed on the internal for some reason. I'm recommending using fixmbr in the Windows install disk.

---

### Post by jimv on 2008-06-20
I'm pretty sure that by default, Grub installs on the MBR of your primary drive.  In order to fix this, you need to run fixmbr on your Windows drive, and then use something like a supergrub disk to install grub onto your USB drive.

OR you can make a 1 gig partition on your main windows drive for /boot so all your boot files (menu.list) are stored there.

---

### Post by fiddler616 on 2008-07-03
SOLVED...sort of.
I decided to give up on Wubi--the point was for it to be easy, and installed Ubuntu the manly way. After a few speed bumps, I'm a happy Linux user! :KS

---

