---
title: "HOW TO: Roll Back 7.10 to 7.04????"
date: 2007-10-25
forum: Installation &amp; Upgrades
---

### Post by Em-Buntu on 2007-10-25
My Gutsy experience has been not too pleasing. Wish I hadn't done it.
Now need to attempt to roll back upgrade to Feisty.

I used the upgrade to Gutsy link to perform the upgrade from Feisty to Gutsy.
Anyone have any good luck using tried & true procedure for accomplishing this? Please share.

---

### Post by linuxwizard on 2007-10-25
Look at this

[https://help.ubuntu.com/community/DowngradeHowto](https://help.ubuntu.com/community/DowngradeHowto)

---

### Post by Em-Buntu on 2007-10-25
> **linuxwizard said:**
> Look at this

[https://help.ubuntu.com/community/DowngradeHowto](https://help.ubuntu.com/community/DowngradeHowto)

Thanks.
That sounds reasonable, except it's for hoary and breezy and not specific to returning to Feisty from Gutsy. For example, what would be the Pin priority for Feisty/Gutsy?

Following the upgrade, my system will not boot Gutsy using the new 2.6.22.14 kernel, but will boot using the 2.6.20.16 kernel.

---

### Post by linuxwizard on 2007-10-25
Read carefully
For this guide, [COLOR="Red"]we'll use the example of downgrading Ubuntu Breezy to Ubuntu Hoary[/COLOR]. This guide can be adapted to downgrade any combination of releases.

---

### Post by vambo on 2007-10-25
> **Em-Buntu said:**
> Thanks.
That sounds reasonable, except it's for hoary and breezy and not specific to returning to Feisty from Gutsy. For example, what would be the Pin priority for Feisty/Gutsy?

Following the upgrade, my system will not boot Gutsy using the new 2.6.22.14 kernel, but will boot using the 2.6.20.16 kernel.

What errors do you get with the new kernel. It's just after I upgraded I had a problem with the new one reading logical device entries in my fstab. It's fine now that I've fixed it.
Just wondered if it might be the same thing - could save you a lot of hassle.

---

### Post by Em-Buntu on 2007-10-25
> **linuxwizard said:**
> Read carefully
For this guide, [COLOR="Red"]we'll use the example of downgrading Ubuntu Breezy to Ubuntu Hoary[/COLOR]. This guide can be adapted to downgrade any combination of releases.

I did.
[B]
I have *YET TO TEST THE PROCEDURE*. Please pursue at your own risk until this documentation is completed![/B]

I'm not prepared to jump from one experiment (Gutsy) to another.

---

### Post by Em-Buntu on 2007-10-25
> **vambo said:**
> What errors do you get with the new kernel. It's just after I upgraded I had a problem with the new one reading logical device entries in my fstab. It's fine now that I've fixed it.
Just wondered if it might be the same thing - could save you a lot of hassle.

I wish it were merely one issue.
Following the install, the boot menu (grub) provides two boot options for Gutsy. Version 2.6.22.14 and 2.6.20.16.
If I select the 1st, the system gets to the gnome login screen but after entering username& password will create a black screen and just sit there. It will not accept any keyboard input, but shows a large X for the mouse cursor. Hitting ESC takes me back to the gnome login screen. I can then boot in the failsafe mode where I've attempted a number of suggested fixes but none have made a difference.
It sees all my devices fine, all except my RAID which I share with Windows, so I don't wish Gutsy to have access and take the risk of losing data.

If I select option 2 (2.6.20.16) the system will boot normally, but there are major issues with network performance, Firefox, Evolution, Open Office, where each will hangs or go to lunch for long periods of time. I don't believe this is a valid or tested configuration and not something I wish to live with.

I'm not liking this one bit. After5 months of Feisty bliss, for the last two days I've been forced to revert back to using Windows XP-64.

---

### Post by vambo on 2007-10-25
Sounds similar, but not identical to the trouble I had. If you want to post your fstab I could quickly say yea or nay if it is the same problem.
As to actually rolling back to a Feisty install, all I can really think of is using a Feisty live CD.

---

### Post by Em-Buntu on 2007-10-25
> **vambo said:**
> Sounds similar, but not identical to the trouble I had. If you want to post your fstab I could quickly say yea or nay if it is the same problem.
As to actually rolling back to a Feisty install, all I can really think of is using a Feisty live CD.

My thoughts exactly. I've just completed downloading the image file and burning the CD.
Was your system having problems loading web pages in Firefox as well? When in failsafe mode, if I surf the web, 80-90% of the sites I browse will hang or take an usually long time to load. I mean up to 5 minutes a page, and it seems to be a caching problem also, because if I revisit the page it still takes the same long period of time to load. These were pages that loaded in seconds under Feisty.

A search for fstab on my system comes up empty. Where is the file located?

---

### Post by vambo on 2007-10-25
Doesn't sound the same. Initially the new kernel didn't mount my /home partition, but the old (Feisty) one did. Seemed to work OK with the old kernel and new packages ifar as I remember. Hope the fresh install works for you.

---

### Post by Em-Buntu on 2007-10-25
> **vambo said:**
> Doesn't sound the same. Initially the new kernel didn't mount my /home partition, but the old (Feisty) one did. Seemed to work OK with the old kernel and new packages ifar as I remember. Hope the fresh install works for you.

Thanks.
I just finished backing up my data files to CD. 
I think a fresh install will be more reliable then attempting a roll back anyway.

---

### Post by Dilbert59 on 2007-10-25
I installed 7.10 today, and, after selecting the restricted mode drivers for my Nvidia card (I didn't specify, but it's an FX5500 card) the subsequent required reboot didn't complete.  I've used a couple of Linux installs, 7.4 and previously Suse 10, but, I'm not very good with them yet.  I have reinstalled 7.4 from the LiveCD.  What I would like to be able to do, is go back to my previous 7.4 configuration.  In places I see a disk1 which contains the old files (although it won't let me use the Documents subdirectory).  How would I boot to the fresh 7.4 install in that logical disk?

---

### Post by myke on 2007-10-25
I concur.  A fresh install was the only option for me.  There were to many errors I couldn't fix with the upgrade.  It seemed that when I would get one thing fix, something else would break.  I'd download an iso image, burn it to disk, and start over.   I have a winxp/linux dual boot system (still need win for work) and had to use the win side to download the iso but at least i have a working system now.  And ... since the fresh install -- NO PROBLEMS.

---

### Post by Em-Buntu on 2007-10-25
OK, I've done a fresh install and the system is booting under the new kernel now. 

The system is much more responsive then before under the upgrade, however I am still experiencing an unpleasant browsing experience using Firefox. The pages are still taking far too long to load. Perhaps this is due to the often mentioned IPV6 issue. If I can resolve this issue with Firefox, I'll be content to live with Gutsy.

BTW, I upgraded to Gutsy because it sees my cheap TV tuner while Feisty did not. Perhaps now I can finally get a media center Television working under Ubuntu since it or Windows XP-64 will not see my AIW.

Thanks to all the Ubuntu members who helped me out with this! Free future Ubuntu upgrades to you all. :lolflag:

---

