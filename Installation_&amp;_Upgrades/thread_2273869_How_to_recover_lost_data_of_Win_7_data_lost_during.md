---
title: "How to recover lost data of Win 7 data lost during ubuntu 14.04 LST install on HP 430"
date: 2015-04-16
forum: Installation &amp; Upgrades
---

### Post by Mohit_Jiindal on 2015-04-16
Hello Friends/Experts

  I am new to ubuntu and as well to this forum. I have yesterday only installed ubuntu 14.04 LST on my HP 430 Notebook/Laptop with the 'replace' option selected. Like I said earlier, I am all new to this world of linux, ubuntu and this is the reason I had no clue that selecting this option would erase all the data on my D:\ drive partition of around 250 Gb alongside that of C:\. I have installed this ubuntu 14.04 LST twice within a span of 1 hour once with no wifi option selected and second time with wi-fi option selected hoping that it would enable and get my wi-fi connection working on my laptop but it disappointed me totally. I have posted a thread related to this in the networking forum. 

  In view of aforesaid, I did now like to recover all my D:\drive partition data as the same was of utmost importance to me. I don't mind loosing on video files but really need the rest of the stuff. It would be very kind of you , if you could please help me reover my lost data. For the sake of information I did also like to state there I haven't done much changes to my system after the installation of ubuntu - I only browsed the web using a wired eternet connection and also tried to upgrade the OS through Software Centre and also by making use of these two commands :

```
sudo apt-get update
sudo apt-get dist-upgrade
```

I shall be very thankful for the kind favor.

P.S: Staff members may please move this tread to appropriate place if required.

---

### Post by Mark Phelps on 2015-04-16
In my experience, Windows filesystem utilities have been best at recovering data from former Windows partitions; Linux filesystem utilities have been best at recovering data from former Linux partitions. Your best bet at recovering data in a useful form from the Windows filesystem is to do as indicated below ...

Since your data was on a Windows partition, based on my experience at doing this successfully, my suggestions are the following:
[NOTE: If your PC has a working copy of MS Windows on it, skip to step 4]
1) Find someone with a working MS Windows PC
2) Remove your drive from this PC.
3) Connect your old drive to the MS Windows PC.
4) Download and install the trial version of RecoverMyFiles from [http://getdata.com](http://getdata.com).
5) Right-click the RecoverMyFiles shortcut and select "Run as Administrator"
6) Select the option to Recover a Drive
7) You will get a list of drive, scroll down to find the one for your USB stick or memory card
8) Select Automatic Driver recovery, press Start button
9) It will run for a while but when done, will show a directory tree in the left pane. Do NOT interrupt it.
10) When done, browse the folders in the directory tree -- and be SURE to check the filesizes of the files you want to recover.  If the filesize is zero, the file is trashed and you will NOT be able to recover it.

If the files look OK, you will need to contact Runtime Software to purchase a license for the recovery. You won't have to reinstall the app; instead, they will email you an activation code which you can use to turn on the recovery feature.

According to their website, the "standard" version of the app is $70 USD.  They also have a Pro version for $99 dollars, but if you go to their website, you can compare versions and features.

Your data ... your money ... your choice.

---

### Post by Mohit_Jiindal on 2015-04-16
any possiblity of recovering the data without removing hdd from this machine ?

---

### Post by Mark Phelps on 2015-04-17
> **Mohit_Jiindal said:**
> any possiblity of recovering the data without removing hdd from this machine ?

Basically, no.  If you have overwritten the former partitions, every time you use this drive, you are overwriting files that were previously there.  In a short period of time, you will not be able to recovery your former files because they will have been overwritten.

You can't recover data to the same drive you are using in the case where partitions got overwritten.  You need to be running the recovery app from a different drive, and recover data to that drive.

---

