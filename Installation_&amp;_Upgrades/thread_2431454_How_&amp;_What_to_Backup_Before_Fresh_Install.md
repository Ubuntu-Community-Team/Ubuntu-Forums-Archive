---
title: "How &amp; What to Backup Before Fresh Install?"
date: 2019-11-16
forum: Installation &amp; Upgrades
---

### Post by eldavar on 2019-11-16
I'm currently running Ubuntu 18.04.3 LTS (I originally had 14.04, upgraded to 16.04, then to 18.04), but for a month now I've been having issues with the whole system freezing at random times with no warning. When this happens, nothing works, and both the mouse & keyboard don't respond, so REISUB isn't even an option. I've checked the logs for obvious errors, but nothing looks out of the ordinary to me. So, I'm hoping a fresh install could fix these random freezes that force me to restart by holding down the power button. 

My question is about exactly how and what to back up so I don't lose all the custom settings and things I've become so used to over the years. I'm not sure exactly what config files and things are relevant and linked together, and I'd hate to miss something important. For example, it took me weeks to figure out how to get my scanner to actually work. (It's an Avision AW210, was listed as Linux compatible on the company website, but there were still errors and the company told me their only Linux engineer had quit, so they had no clue how to help...) Since it was more than a year ago that I went through all that hassle, I'd like to make sure the settings and configs for the scanner don't get lost, but I don't remember where and what they all are. 

The main things I can think of that I really want to preserve are:
[LIST]
[*]scanner & printer
[*]aliases
[*]bash & terminal customizations
[/LIST]

One more thing, is there a way to get a list of installed software? Not everything is shown in the Applications list. 

Sorry for the long post, I'm just hoping to minimize downtime when I do the clean install. Any help would be greatly appreciated!

---

### Post by Skaperen on 2019-11-16
if you have enough space for everything, then i suggest backing up everything.  you might start by telling us about your means of backup (is it an external USB 3 [blue tab coonectors] hard drive?) and what size you have.  the outputs of these commands can also help.
```

df
du -s /home

```
the 2nd command could take quite a while.

---

### Post by TheFu on 2019-11-16
Sometimes settings for a single userid are the issue.
Create a new userid, login using that and see how stable things are.

In general, 
system settings are in /etc/.
userid settings are in the userid's HOME.
If you backup those areas, you can slowly move settings over one at a time until the issue happens again.

To get a list of manually installed packages that were installed using APT, use **apt-mark**.

Beware, backing just the files isn't sufficient. You must also capture the owner, group, permissions and ACLs for each file.  That's why a real backup tool is necessary and why using Linux file systems is almost always required.  Do not use NTFS or FAT-whatever.

BTW, similar questions have been asked here and got lots of responses.  I would encourage searching through the threads here for those other answers and specifics.

---

### Post by eldavar on 2019-11-16
Skaperen, 

Space isn't an issue. My NAS has about 8TB free, so I can stash any necessary files there. My house is hard-wired with Cat-6, so any local file transfers should be relatively fast. 

Here's the output of **df**:
```
Hello, Master Greg
[greg]$ df
Filesystem     1K-blocks      Used Available Use% Mounted on
udev             8163060         0   8163060   0% /dev
tmpfs            1643748      3816   1639932   1% /run
/dev/sdb1      471877848 346123032 101715036  78% /
tmpfs            8218732    458660   7760072   6% /dev/shm
tmpfs               5120         4      5116   1% /run/lock
tmpfs            8218732         0   8218732   0% /sys/fs/cgroup
/dev/loop0         45312     45312         0 100% /snap/gtk-common-themes/1353
/dev/loop1          4352      4352         0 100% /snap/gnome-calculator/544
/dev/loop2         55936     55936         0 100% /snap/core18/1265
/dev/loop7         91264     91264         0 100% /snap/core/7917
/dev/loop3        144128    144128         0 100% /snap/gnome-3-26-1604/98
/dev/loop11       144128    144128         0 100% /snap/gnome-3-26-1604/97
/dev/loop9          8832      8832         0 100% /snap/canonical-livepatch/88
/dev/loop10         1024      1024         0 100% /snap/gnome-logs/81
/dev/loop12         4352      4352         0 100% /snap/gnome-calculator/536
/dev/loop13        15104     15104         0 100% /snap/gnome-characters/367
/dev/loop4         43904     43904         0 100% /snap/gtk-common-themes/1313
/dev/loop14        15104     15104         0 100% /snap/gnome-characters/359
/dev/loop15        88960     88960         0 100% /snap/flameshot-app/188
/dev/loop5        159872    159872         0 100% /snap/gnome-3-28-1804/91
/dev/loop6        160512    160512         0 100% /snap/gnome-3-28-1804/110
/dev/loop8         91264     91264         0 100% /snap/core/8039
/dev/loop16         1024      1024         0 100% /snap/gnome-logs/73
/dev/loop17        55936     55936         0 100% /snap/core18/1223
/dev/loop18         8832      8832         0 100% /snap/canonical-livepatch/84
/dev/loop19         3840      3840         0 100% /snap/gnome-system-monitor/107
/dev/loop20         3840      3840         0 100% /snap/gnome-system-monitor/111
/dev/sdb5        7725716     34800   7278756   1% /swap
tmpfs            1643744        16   1643728   1% /run/user/120
tmpfs            1643744        44   1643700   1% /run/user/1000
[greg]$ 

```

TheFu,

After talking with my family, I think you may be right that the problem is only with my userid. The 2 other users on this machine have never had the same freezing issues that I have, and there have been times in the past few days where they've used the computer for several hours without a problem. I, however, sometimes get the freezing after just a few minutes and other times only after a few hours. If that's the case and it is just my userid with the problem, do you have a recommendation for how to proceed? 

If I do still decide to fresh install, what backup tool do you recommend? 

Thank you both!

---

### Post by Harry66 on 2019-11-16
I use duplicity for backup the whole system (I have it set up in anacron to do a full backup every 2 weeks, and incrementals daily)

---

