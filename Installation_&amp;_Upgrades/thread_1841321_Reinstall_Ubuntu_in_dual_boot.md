---
title: "Reinstall Ubuntu in dual boot"
date: 2011-09-09
forum: Installation &amp; Upgrades
---

### Post by mac4rfree on 2011-09-09
Hi Guys,
 
I have a dual boot of Natty with Win7. 
 
I want to clean up the whole Ubuntu and reinstall it again or for that matter some other flavours of Ubuntu.
 
Can somebody let me know some tutorial or guide me through the process.
 
Thanks for your help in advance..
 
Cheers!!!!!

---

### Post by ~!geek!~ on 2011-09-09
> **mac4rfree said:**
> Hi Guys,
 
I have a dual boot of Natty with Win7. 
 
I want to clean up the whole Ubuntu and reinstall it again or for that matter some other flavours of Ubuntu.
 
Can somebody let me know some tutorial or guide me through the process.
 
Thanks for your help in advance..
 
Cheers!!!!!

 (Follow this post only after you have backed up your data in ubuntu partition [your home folder and other directories] if you want! After following these instructions, your old ubuntu partition will be gone completely )  Its quite easy to wipe old ubuntu and start once again!! Actually you need to follow the exact same process which you followed while installing it very first time! In this case you have the partition already created for you to install ubuntu filesystem on.Here it is: boot your machine with a live cd (or live usb)->install ubuntu->in partition window change the size of partition containing old ubuntu, if you want to increase or decrease the partition you were using or else format the partition containing old ubuntu and select it as the which will hold new ubuntu! Swap is already set up for your old ubuntu! if you want to change the size do it here!! -> Select the partition to install ubuntu on and click forward and follow the steps it asks you to!! Done!!!!

---

### Post by nothingspecial on 2011-09-09
Boot up the live cd or usb

When you get to the "how do you want to install ubuntu" bit, choose "something else"

Choose your ubuntu partition and choose to use it as an ext4 journaling file system.

Choose to format it

Choose a mountpoint of /

Choose to use your swap partition as swap space.

**[SIZE="2"][COLOR="Red"]Do not touch your windows partition[/COLOR][/SIZE]**

You will be able to tell which is which because your windows partition will be labled as ntfs and your ubuntu one as ext4 and your swap one as ..er swap

That's it.

Oh and make sure you back everything up that you don't want to loose.

---

