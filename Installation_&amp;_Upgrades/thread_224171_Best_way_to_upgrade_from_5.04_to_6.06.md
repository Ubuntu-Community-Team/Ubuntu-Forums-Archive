---
title: "Best way to upgrade from 5.04 to 6.06"
date: 2006-07-27
forum: Installation &amp; Upgrades
---

### Post by Odyssey1942 on 2006-07-27
Newbie here. Have read quite a number of posts and guides and am thoroughly unsure at this point. 

It seems to me that a safe way to go would be to repartition, reducing the present 5.04 partition to just a comfortable bit larger than it now occupies, and install 6.06 into the new partition. The idea is that there will certainly be problems to solve if one upgrades to 5.10, then a repeat when going to 6.06

I am assuming that if one runs into difficulty with the new install and it involves something already working in the older version, one could just reboot into the old partition, get the required job done, then boot back into  6.06 and continue to smooth out the install?

If good idea, any thoughts/guidance, e.g., how much larger should the 5.04 partition be than now occupied?

If bad idea, why and any suggestions for better way?

Or, is there just a plain, better way, and why?

TIA

---

### Post by linuxfanatic1024 on 2006-07-27
The best way to do that is to do a full upgrade to 5.10 first, and *then* to 6.06. There is a Wiki page about this: [https://wiki.ubuntu.com/DapperUpgrades](https://wiki.ubuntu.com/DapperUpgrades)

Hope this helps.

---

### Post by Odyssey1942 on 2006-07-27
lf, thanks for yours and I had seen it, but as far as  I can see, it does not specifically address my question.

---

### Post by catlett on 2006-07-27
If you have the hard drive space I would do it like you suggested. I could almost guarantee you would have an issue doing a double dist-upgrade.
I lost my whole configuration when I dist-upgraded from 5.10 to 6.06
Your suggestion is actualy a great one. You will always have a "failsafe" system that you know works and is bootable. If you have an issue with Dapper or even Hoary, you can boot into the other install and search for a solution.
The best part is that you can mount the other install's partition so any data saved in that install can be easily accessed from the one you booted into.
I would use gparted live [http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php) to resize your current install to only a few hundred mb over the amount of used space. Then make your Dapper partition. (they can both use the same swap. no need to make another one for Dapper).
When you get Dapper installed, I follow this guide to get my multimedia etc [http://doc.gwos.org/index.php/DapperGuide](http://doc.gwos.org/index.php/DapperGuide)
There are 2 install cds for Dapper. The live cd which runs from a live session and the Alternate Install CD which is like the 5.04 and 5.10 text based install.

---

### Post by Lord Illidan on 2006-07-27
Reinstall the whole thing. From Breezy to Dapper, things could get a little out of hand. From Hoary to Breezy to Dapper, things could get a lot more out of hand.

---

### Post by Odyssey1942 on 2006-07-28
catlett, Thanks for the guidance. Am d'ling gparted iso as I write. If I understand it, the file should be iso'd to a cd, then boot from CD (or just run from CD?) This seems the most logical alternative of the three to me also.

Little bit 'fused about 6.06. Is there one CD for an install to a hard drive from a CD, and a different CD (live) to run from CD without an install to hdd? Or something else?

Lord Illidan, Unsure what you mean by re-install? Are you saying it is #3 above (something else)? If you are suggesting just install 6.06 over 5.04 (which would be an install, not be a re-install given it was never installed in the first place), why is this a superior route? Thanks

---

### Post by catlett on 2006-07-28
Yes, you boot to the gparted cd after you burn the iso to the cd.
There are 2 ways to install Dapper. One is a live session installer. You boot to the Daper live cd and when you get to the desktop there will be an icon on the desktop that says install. You double click the icon and the install runs . It doesn't allow you to configure much. It does auto-detection for your x setup i.e. monitor,keyboard etc Then it installs grub to your mbr.
The Alternate Install CD is like the install you used when you installed 5.04 You boot to a menu and then go throught all the steps. You don't enter a live session.
I believe Lord Illian is just concurring with you."Re-install the whole thing" Meaning an upgrade from 5.04 to 6.06 in his mind "could get a little out of hand."
I believe your instincts were right. Keep a stripped down 5.04 and install 6.06 fresh.
In my signature are 2 guides with pictures of the Live Installer and the Alternate CD installer, just in case you wanted to get an idea of what they look like.
Any problems, post.

---

### Post by Odyssey1942 on 2006-07-28
That is very helpful indeed. Many thanks. Will try to get into it this weekend. As soon as, will report back here.

---

### Post by Odyssey1942 on 2006-08-01
A couple of issues before starting:

Windoze has various defrag progies and defragging is probably a good idea before creating the new partition, no? If so, what is a good defragger to use under my Linux Ubunutu 5.04 (recall that I do not have Windows on this machine)?

Do I need the computer name that I gave when I installed 5.04, or can I use any name during the 6.06 install?

Do you have a recommendation between using the Live CD installer or the text based install? If the former, does it not contain gparted, and so no need for a separate gparted CD?

TIA

Edit: P.S. Here is the best partitioning concept guide that I have seen:

[http://www.psychocats.net/ubuntu/partitioning.html](http://www.psychocats.net/ubuntu/partitioning.html)

---

### Post by catlett on 2006-08-01
That is Aysiu's site. It is great. All Aysiu's guides are step by step and graphical. Aysiu used to be an english teacher and the ability to instruct others well is obviously still there.
Anyways the live cd is simple but doesn't give many options. If you didn't have an issue with the 5.04 install then I would use the alternate installer but if it was a bit confusing go with the live cd.
I would make your partitions ahead of time with gparted live [http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)
Aysiu and Herman's guides to dual booting are both in my signature if you want to check them out.

---

### Post by Odyssey1942 on 2006-08-02
Catlett, I am working my way through your guides and they are very helpful. Each of them usually leads to a whole string of new URL's with good info and I tend to get a bit lost in the overload. Will go back soon and make sure that I have looked at all of them.

---

### Post by catlett on 2006-08-02
> **Odyssey1942 said:**
> Catlett, I am working my way through your guides and they are very helpful. Each of them usually leads to a whole string of new URL's with good info and I tend to get a bit lost in the overload. Will go back soon and make sure that I have looked at all of them.

Sorry to not post the 2 important one's.
Alternate install cd guide [http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)
Live cd installer guide [http://www.psychocats.net/ubuntu/installing.html](http://www.psychocats.net/ubuntu/installing.html)

---

