---
title: "black screen after install of 10.04"
date: 2010-05-08
forum: Installation &amp; Upgrades
---

### Post by A.S. on 2010-05-08
Hello,

I have searched the forum but have not found a solution.

I have installed Kubuntu 10.04 on an older laptop (Pentium 4, ATI grahics card) two times, but after restart there appears only a black screen with a blinking cursor and nothing else happens.

I have updated grub from a livecd with xforcevesa and nomodeset, but it helped nothing.

Has anybody an idea what I should try.

---

### Post by alenn on 2010-05-08
I have the same problem, just wait for 3-4 minutes and system will start normally.

---

### Post by A.S. on 2010-05-08
Thank you for your reply.

I've tried waiting, but nothing happended.

There is still the black screen with the cursor.


Has anyone an idea?

---

### Post by paydaydaddy on 2010-05-08
Have you tried recovery? Do you have the option of booting with an earlier kernel? Safe graphics Mode?

---

### Post by bturrie on 2010-05-08
You didn't say whether you are getting the grub boot menu or not. If you are, I agree with the earlier post that suggested booting the recovery console. If that works, try

dpkg --configure -a

I'm not at all sure this will help but I did read a rant on the kubuntu forum about problems with jockey getting the video driver right in 10.04.

On the other hand, if you aren't getting the grub boot menu you may need to reinstall grub from a live cd. 

As an aside, I used to upgrade kubuntu a few days after the latest release came out. I had enough problems that now I wait a couple of months after the release date to upgrade.

---

### Post by Catharsis on 2010-05-08
If you aren't getting the grub menu, hold down Shift while you boot. 
[http://www.ubuntu.com/getubuntu/releasenotes/1004#No%20delay%20for%20boot%20menu%20with%20GRUB%202](http://www.ubuntu.com/getubuntu/releasenotes/1004#No%20delay%20for%20boot%20menu%20with%20GRUB%202)

Also, see if this helps:
[http://ubuntuforums.org/showpost.php?p=9235797&postcount=16](http://ubuntuforums.org/showpost.php?p=9235797&postcount=16)

---

### Post by A.S. on 2010-05-10
Thank you for your replies.

No I did not get the grub menu.

But I'd started kubuntu from cd and then started fdisk. fdisk has told me, that something was wrong with the size of my first partition (/dev/sda1) - the root partion of the installed system was /dev/sda2. Maybe I have resized the first partition in the past.

So, I had deleted the whole disk and installed kubuntu again and it is working now.

---

