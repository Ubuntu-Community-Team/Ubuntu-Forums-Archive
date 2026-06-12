---
title: "Black Screen on Boot after upgrade vom Lubuntu 13.04 to 13.10"
date: 2014-08-28
forum: Installation &amp; Upgrades
---

### Post by d018398 on 2014-08-28
Hi, 

I am keeping an old PC (normally unchanged, kind of like a "living back-up/archive instance").

Yesterday I needed that machine. When in the net, I was advised to upgrade from Lubuntu 13.04 to 13.10 since this would be safer / with support of updates.

So I performed the update without any problems. When it came to the last step, of rebooting the machine, the boot progress got stuck, after the intial Lubuntu logo was displayed shortly. The screen simply went black.

I used a live-cd to boot into memory and ran the standard boot-repair for Grub (result: [http://paste.ubuntu.com/8164889](http://paste.ubuntu.com/8164889)). In the same process, it hinted, that "FlexNet" was detected and I should save my data (it is a back-up anyway) and I can access the data on the disk through a live-cd boot. But I would prefer to have a working system, that I can simply start from the hard-drive.

So after Boot-Repair, the system now displays Grub with the options of Safe-Boot and similar. If I continue the normal boot, I again end up at a black screen, that is prior to any Lubunto log-on prompt for user and password.

I am not sure what to do next. Do you have any hints I can follow? I ran the file-system check (fsck) and it mentioned 0.2% of files that are not together. I am not sure, if that is at all related to my booting topic.

My assumption is, that I miss some driver or similar after the upgrade.

Any help is much appreciated.

Thanks, Jochen

---

### Post by claracc on 2014-08-28
Lubuntu 13.04 reached its end of life support past january, I think this is the cause that upgrading to 13.10 has failed (repositories are removed from server) and you obtain a black screen on boot.
See [https://ro-ro.facebook.com/Lubuntu.Official.Page/posts/10152238662641694?reply_comment_id=32605164&total_comments=1](https://ro-ro.facebook.com/Lubuntu.Official.Page/posts/10152238662641694?reply_comment_id=32605164&total_comments=1)

What I would do is backup your data (home folder) and fresh  install the new and supported lubuntu 14.04.

---

### Post by sudodus on 2014-08-28
Welcome to the Ubuntu Forums :-)

I'm sorry that you were advised to upgrade your system to 13.10. That system has (also) passed end of life. See this link
[URL="http://ubuntuforums.org/showthread.php?t=2229730"]
Forums Staff recommendations on EOL Ubuntu releases, in particular 10.04 desktop.[/URL]

The current policy of Ubuntu is more focus on long time support versions released in April even years (12.04 LTS, 14.04 LTS, 16.04 LTS ...), and the other releases, like 13.10, 14.10, 15.04, 15.10, are supported only 9 months.

So one problem could be that there is no support, or at least no complete support of 13.10. If you have a backup, I suggest that you restore from it and prepare for a fresh install, where you keep (a copy of) your /home directory in a separate partition, a ***home*** partition.

Then make a fresh install of 14.04.1 telling the installer that you have not only a root partition but also a home partition. Select ***Something else*** at the partitioning window of the installer. This way you will keep your personal settings, and may need only a few tweaks.

If you have no backup, you can still try the trick with a home partition and a fresh install. It might work well, because I don't think the updater 'messed too much' with the home directory.

---

### Post by mörgæs on 2014-08-28
Both 13.04 and 13.10 are unsupported. If you manage to get the latter working there's another upgrade waiting. 

Though FlexNet is not a virus it's a parasite in the boot sector (you can easily google it for details). Likely a leftover from an old Windows install.

I suggest a fresh install of 14.04, which will eliminate the upgrade problems and remove FlexNet.

(Whoa, ninja'd twice. Getting slow in the keyboard.)

---

### Post by d018398 on 2014-12-20
Hi there, 

I did not work on this for a while, as it is "only" my "back-up" machine. Now I have some time over the holiday, and tried to bring back to live my old Dell Latitude D800. 

I did as recommended:
a) backed up the home directory (after a boot into memory from CD)
b) tried a fresh install of 14.04 (unsuccessfull / had to use "forcepae" option / installation was canceled with error twice)
c) successfully reinstalled a 12.04 Lubuntu from CD (my plan was not to apply any upgrades, once I have it running)
d) deleted the /home content as it was created on a seperate partition
e) imported the /home content from the backup (pure copy)
f) now when logging on, the user (same name on the old and the new system) would not accept the password at logon
g) I reset the password in recovery mode (as advised in some wiki pages, once PW is forgotten)
h) ...still it will not let me "logon" again

Can you please advise, where I made a mistake in the steps above? 
I can easily "redo" all, but would rather have some guidance before I spend more time on this.

thanks and best regards, 
Jochen

---

### Post by mörgæs on 2014-12-20
Let's stop at step 2. We need to get a clean 14.04.1 or 14.10 running before thinking of /home.

Using [https://help.ubuntu.com/community/PAE](https://help.ubuntu.com/community/PAE) do you manage to get it rolling? If not please post the exact error message you see.

---

### Post by d018398 on 2014-12-21
Hi again, 

thanks for requesting me to try this again. The full install of 14.04 worked without problems, when "overwriting" the 12.04 installation. I have no clue what the issue was before. I did use the "forcepae" option again. So the issue was not related to that, I assume. 

Now I am pulling in the latest patches. Once this is done, I would like to regain access to the extra partition, that I had created and already populated with my back-up data. 

I fear, that I may run into the same "logon" problem. I have also seen, there are quite a number of wiki articles, that related to this topic.

Do you have any special info for me, that I should take into account, before trying to "switch" the current "empty" /home (that works fine) to the one (with my old "restored" /home content) on the extra partition?

I will wait for your advice, before continuing. 
Thanks in advance!!
BR, Jochen

---

### Post by d018398 on 2014-12-21
one correction: 
after the patches installed, I realized now, that the "extra partition" is gone. The installation has used the full disk and created a new partition (keeping the swap partition untouched). 

So my points reg. accessing the old /home (restore) are still valid, but I would simply want to "replace" the current content, with my old one, on the main partition - if that is feasible at all.

Thanks and best regards, 
Jochen

---

### Post by mörgæs on 2014-12-21
I don't recommend recycling an old /home. There's a risk of bringing a lot of strange settings into the new install.

Better to move relevant files one by one from the old to the new.

---

### Post by d018398 on 2014-12-21
ok - that's what I will do then. 

Thanks for your support and I put this one on solved !!

Merry Christmas ; o

---

### Post by mörgæs on 2014-12-21
Good luck and merry Christmas to you, too.

---

