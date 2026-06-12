---
title: "more help with grub!"
date: 2008-03-22
forum: Installation &amp; Upgrades
---

### Post by Manzmann on 2008-03-22
Hi folks this is my first post. My name is Stu and I'm having a spot of bother reinstalling grub after installing vista.

I spent most of yesterday trying the various methods of reistalling grub but none of them seem to work.

I tried via live cd opening a terminal and doing it that way which appears to work and even completes with a success message but when i reboot it goes straight into vista.

I also tried the method I saw using the live cd and going through the installation process but only installing grub. this method fails me at the disk partition point. The method says to mount your required linux partions 
/
/boot
/swap

dont have a /boot in these options!
anyway whatever i chose there it doesnt allow me to continue due to "no root specified" or something similar.

I finally tried using Unetbootin - supergrubdisk, which was the most recent method but alas this fails too.
When I try to execute the final action and rewrite grub it hangs and does nothing more. This appears to be the same as the first method in terminal which apparently works, but here it just hangs.
Perhaps I should mention, I can boot into ubuntu using the supergrubdisk if i load the mbr from my linux partition.

Any other tips insights would be great, Any info I can supply to help someone diagnose my probs, please just ask.

Also, if this doesnt work will it be alot of hassle reinstalling ubuntu?

Thanks

Stu

---

### Post by Pumalite on 2008-03-22
If you use Vista, you have to use Vista's partitioner to allocate space for Ubuntu FIRST. You cannot partition with Ubuntu Live CD or Alternate
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)
[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)
[http://www.howtoforge.com/dual_boot_windows_xp_vista_ubuntu_feisty_p2?](http://www.howtoforge.com/dual_boot_windows_xp_vista_ubuntu_feisty_p2?)
[http://ubuntuforums.org/showthread.php?t=464425](http://ubuntuforums.org/showthread.php?t=464425)
[http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)

---

### Post by Terminating.proprietary on 2008-03-22
Yea, ^^^ I had to learn the hard way. Just in case you didn't know the vista partitioner is built in. Right click on Computer or my computer then select manage. The manager comes up and there are multiple options on the right. Click the option "disk management" under storage. Right click the partition in the work area that holds your windows files and select the option shrink volume.

---

### Post by Pumalite on 2008-03-22
You need only 3 partitions.
Go Manual.Make the first partition 15000 (beginning).Mount point '/'
1 GB for /swap
The rest for /home
Then press 'Forward'

---

### Post by Manzmann on 2008-03-23
Thanks for your help folks but I already have Ubuntu installed on a seperate hard drive. all i want is to install grub again.

Are you giving me instructions for reinstalling ubuntu? and does that mean you think itll be easier to reinstall ubuntu?

---

### Post by Pumalite on 2008-03-23
If it's a new installation, I'd just reinstall Ubuntu.
In any case, post:
sudo fdisk -lu

---

### Post by Dennis on 2008-03-23
Try this:

[http://apcmag.com/5045/how_to_dual_boot_vista_with_linux](http://apcmag.com/5045/how_to_dual_boot_vista_with_linux)

---

### Post by Manzmann on 2008-03-23
Huge thanks dennis!! I just downloaded the "easybcd" program and configured the boot through vista and that was the easiest method by far and its all good and working.
thanks for your help too pumalite!

Stu

---

### Post by Pumalite on 2008-03-23
No 'problema'. Godspeed.

---

