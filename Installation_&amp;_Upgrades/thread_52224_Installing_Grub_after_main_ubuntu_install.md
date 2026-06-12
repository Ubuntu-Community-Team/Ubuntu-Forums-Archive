---
title: "Installing Grub after main ubuntu install?"
date: 2005-07-27
forum: Installation &amp; Upgrades
---

### Post by powderific on 2005-07-27
I'm used to gentoo installs and grub, but I was putting the new Ubuntu on my girlfriends computer for ease of use purposes and after updating I encountered a LILO error that apparently occurs when your kernel has too many modules.  I know exactly how to get grub into my gentoo computers in such a situation, but I'm not sure how to do a fresh install of the program from the rescue console in ubuntu?  Thanks for any help!

---

### Post by angkor on 2005-07-27
To reinstall grub:

1. boot from your Ubuntu InstallationCD
2. type rescue at the boot prompt.
3. select your root partition
(4. mount /usr if it's on a different partition, like it is in my case)
5. type grub-install

should work.

---

### Post by powderific on 2005-07-29
I've tried such and I get some warning about a benign error that is possible when using xfs file system, and then nothing happens.  (for a VERY long time.  I know that probing the devices can take a while but I left it for hours and it never took that long when I installed gentoo).

---

### Post by Xian on 2005-07-29
[QUOTE=powderific] I know exactly how to get grub into my gentoo computers in such a situation, but I'm not sure how to do a fresh install of the program from the rescue console in ubuntu?[/QUOTE]
There is the su command 'grub-install /dev/hdx' which should work.
Of course this is assuming you've already done a 'apt-get install grub'.

But there is no difference between the commands used to place grub to the MBR in Gentoo and Ubuntu. If you are familiar with this process then you should have no problems, save that there is another issue present which would prevent the proper configuration.

You know the drill:

$ grub
grub> root (hd0,0)
grub> setup (hd0)
grub> quit
$

**modify the partitions for your box*

---

### Post by missingxtension on 2006-09-21
ohh jesus thanks xian your post helped me out a lot
i was doing grub-install and it wasnt doing shiat 
but when i went to the grub shell it installed without a hitch 
you have saved my livelihood and by the way just so u guys know
WINDOWS IS THE CAUSE OF ALL PROBLEMS
aftere beeing windows free for months i wanted to play fear
2 days latter here i am aparantly windows thnkis my linux partitions are fat16 even though theyre listed as 83

---

