---
title: "/dev/hda1 missing help!!"
date: 2006-06-19
forum: Installation &amp; Upgrades
---

### Post by gorilla_king on 2006-06-19
alright i'm very new to ubuntu actually i just installed it yesterday. Well easly this morning i acidently stepped on the power cord as it was starting up, well then i plugged it back in and started it again and it fianlly said that it exited to a shell because /dev/hda1/ was missing. Well i foudn something about running fsck, well ofcourse it didn't recognize that command, so now i don't know what to do. Please any one have any ideas how i can get hda1 back? I used to run kde studio to go and it would work fine if i ran fsck, but not now, any ideas anybody??

Also sorry if i posted this in the wrond forum, i wasn't really sure if it was an installation thing or not, because it was working great until i accidently unplugged it. Grrrr. Thanks in advance.

---

### Post by gorilla_king on 2006-06-19
*bump* 

please anyone, this is really getting annoying, help please!
thank you in advance

---

### Post by gorilla_king on 2006-06-19
i promise i'm only bumping this up when it goes onto other pages, but someone please help me

---

### Post by tonyr on 2006-06-19
How did you do the install? LiveCD? Alternate CD?  How are you accessing this forum?

If you used the LiveCD, reboot that.  Then we can get more information.

---

### Post by gorilla_king on 2006-06-19
well, i used the alternate cd and i'm using this forum on my other computer.

---

### Post by confused57 on 2006-06-20
You might want to enter your bios to see if your hard drive is still recognized.
Your hd "could possibly" have been damaged, because it was being written to when the power was interrupted...hope that's not the case.

As tonyr suggested, boot up your computer with the livecd and see if it recognizes your drive & if it can be mounted.

---

### Post by tonyr on 2006-06-20
If the BIOS recognizes your drive, you can try this:

1. boot your alternate cd
2. choose the option that says something like **Rescue a broken installation**
(I forget exactly what it says, but it's the only one that says **rescue**.
3. Answer all the questions as you normally would.  If you have an ethernet cable
connected, fine.  If not, when it gets to the part about setting up your network connection
with DHCP, let it fail and it will eventually offer you an option to skip the network configuration.  Choose that.
4. It will come to a point where it should ask you to choose a partition to use as the
root partition for the rescue operation.  If the partition table on the disk is more or less 
intact, there will be list of partitions.  If the partition table is hopelessly corrupted,
there may not be a list.  

If you got this far, post a reply and describe the situation.

---

