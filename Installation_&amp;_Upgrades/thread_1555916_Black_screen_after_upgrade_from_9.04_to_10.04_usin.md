---
title: "Black screen after upgrade from 9.04 to 10.04 using Update Manager"
date: 2010-08-18
forum: Installation &amp; Upgrades
---

### Post by nu2u904 on 2010-08-18
I installed 10.04 using update manager from working 9.04 system. Four seconds before completion of 30 min auto download of packages, screen went black. After several CtrlAltDel got window saying ubuntu was running in reduced resolution and could not auto detect my monitor. I attempted a reboot in recovery mode, grub loaded and processes loaded at some point Recovery menu appeared with cursor on normal recovery the top ite. Arror keys  no effect; Enter no effect, except few more lines of processes--no command promp. last item: [1306.234613] on demand governor failed, too long latency of HW, fallback to performance generator.

When I installed 8.10 I had to make change so my nvidia  nforce2 sff esd : 199 mhz
card would be recognized. I had no problem upgrading to 9.04 card and monitor auto found. Now 10.04 can't find it and I can't access the programs to fix it.

---

### Post by tommcd on 2010-08-18
> **nu2u904 said:**
> I installed 10.04 using update manager from working 9.04 system. ...
So, do you mean this is a dist-upgrade from 9.04 to 10.04, and not a clean install of 10.04??? Is that correct???
If so, then that is your problem right there. You can only upgrade in sequence. That is, upgrade from: 9.04 > 9.10 > 10.04.
My recommendation, based on 5+ years of running Ubuntu on several systems, would be to do a *clean install* of Ubuntu 10.04. It will be the fastest, simplest, and most fail safe method of getting a pristine working 10.04 installed on your computer.
I always do clean installs, and never dist-upgrades. And I never have problems.

---

### Post by nu2u904 on 2010-08-19
Thank you tommcd. Its possible I did upgrade to 9.10. If so then how do I resolve my problem? Can I use a 9.04 disk to do a live boot and then locate the xorg.conf file that I once changed for my old nvidia gforce card?

After I obtain a 10.04 iso file and burn it to disk. Do I  uninstall  the installed 10.04 system?  Are the partitions intact [root and swap]? Can I then acquire more free space from Xp [20GB] and create  more partitions and do a manual install?

---

### Post by harshguy on 2010-08-22
How did you upgrade directly from 9.04 to 10.04? Don't you have to upgrade to 9.10 first and then to 10.04?

---

### Post by mörgæs on 2010-08-22
> **nu2u904 said:**
> Thank you tommcd. Its possible I did upgrade to 9.10. If so then how do I resolve my problem? Can I use a 9.04 disk to do a live boot and then locate the xorg.conf file that I once changed for my old nvidia gforce card?

After I obtain a 10.04 iso file and burn it to disk. Do I  uninstall  the installed 10.04 system?  Are the partitions intact [root and swap]? Can I then acquire more free space from Xp [20GB] and create  more partitions and do a manual install?


It is always a good first step to boot the new system as a live CD and see how that goes.

Assuming everything works well: Back up your files in /home, your browser bookmarks, xorg.conf and other stuff you want to keep. After that you delete the Ubuntu partitions, leaving Windows intact. You now have empty space for a fresh install of Ubuntu.

Be aware that you might not get a big resolution on this screen card. I have one myself.

---

### Post by mörgæs on 2010-08-22
> **harshguy said:**
> How did you upgrade directly from 9.04 to 10.04? Don't you have to upgrade to 9.10 first and then to 10.04?

Neither :-) Go for the clean install.

---

### Post by tommcd on 2010-08-22
> **nu2u904 said:**
> Thank you tommcd. Its possible I did upgrade to 9.10. If so then how do I resolve my problem? Can I use a 9.04 disk to do a live boot and then locate the xorg.conf file that I once changed for my old nvidia gforce card?
First, how exactly did you go about upgrading 9.04? If you did it the recommended way, like this:
[https://help.ubuntu.com/community/KarmicUpgrades](https://help.ubuntu.com/community/KarmicUpgrades)
It would not have offered to upgrade directly to 10.04. It would have only offered to upgrade to 9.10. What do you get when you run:
```
cat /etc/lsb-release
```
This should report the version of Ubuntu you are running. However, I am not sure if that file is updated when you do a dist-upgrade, since I always do clean installs.
In your first post, you said:
> Four seconds before completion of 30 min auto download of packages, screen went black. After several CtrlAltDel ... I attempted a reboot in recovery mode ...
So do you mean the upgrade was interupted and did not finish when you rebooted? If so, and since you are not even sure what version of Ubuntu you upgraded to, your upgrade is likely hosed.
What happens if you boot to recovery mode and run:
```

apt-get update
apt-get dist-upgrade

```
Do you get errors? Are you even able to boot to recovery mode at this point?
I think you would be much better off with a clean install of 10.04.
For future refernce, see this on upgrading Ubuntu:
[https://help.ubuntu.com/community/UpgradeNotes](https://help.ubuntu.com/community/UpgradeNotes)
> **nu2u904 said:**
> 
After I obtain a 10.04 iso file and burn it to disk. Do I uninstall the installed 10.04 system? Are the partitions intact [root and swap]?
Your linux partitions will still be there. You can just install 10.04 right over the old Ubuntu install. Since it looks like you did not have a separate /home partition, any data you need to save will have to be backed up first. For this I would recommend a Parted Magic live CD or a System Rescue CD:
[http://partedmagic.com/](http://partedmagic.com/)
[http://sysresccd.org/Main_Page](http://sysresccd.org/Main_Page)

How big is your hard drive? And how much free space do you have?
It would be advantageous to use manual partitioning and create a separate home partition. Here is an excellent tutorial on how to do that:
[http://www.psychocats.net/ubuntu/installseparatehome](http://www.psychocats.net/ubuntu/installseparatehome)
Another great site for dual booting:
[http://members.iinet.net/~herman546/index.html](http://members.iinet.net/~herman546/index.html)
Just create a 10GB root partition. You could get by with a bit less, but go with 10GB to be sure you have enough space for almost anything you may want to install. My Ubuntu root partitions seldom grow larger than about 4-5GB unless I install a big game like Doom3 or Quake4 or something.
> **nu2u904 said:**
> 
Can I then acquire more free space from Xp [20GB] and create more partitions and do a manual install?
You can elect to shrink the XP partition during the install to acquire more space for Ubuntu. If you only have 20GB for XP, keep in mind that you need to have at least 15% of the XP partition as free space in order to properly defrag XP's NTFS file system. You also need some free space for XP's virtual memory (which functions similar to the swap partition in lunux).
I have had XP installed on as little as a 10GB partition. However, I had no personal data on the XP partition, and very few 3rd party programs were installed. I pretty much only had Firefox, Crap Cleaner, and perhaps a couple others I can't remember.
Speaking of the swap partition, if you are tight on hard drive space, you can limit swap to 500mb-1GB. If you have enough memory (at least 1GB, preferably more) a 1GB swap is plenty. If you ever want to suspend the system to memory, then swap should be at least as big as how much memory you have.
So, how big is your hard drive?
How much free space do you have after you leave enough room for XP?
How much memory do you have?
I hope I have not confused you here. Write back if you need more help.

---

### Post by nu2u904 on 2010-08-22
> **mörgæs said:**
> Neither :-) Go for the clean install.

Thank you for the posta morgaes andl harshguy. As per my quoted reply I did upgrade 

to 9.10 before upgrading to 10.04. Here are contents of my grub display.
Ubuntu  9.10 2.6.31.22 generic
                "      recovery

ubuntu  9.10 2.6.31.20 generic
                "      recovery

ubuntu  9.10 memtest 86-1

other os
win NT2000/xp
win xp home

Ran 9.10 2.6.31.22 recovery. At end of grub display:

ubuntu 10.04.1 LTS donald-deskttop tty1
donald-desktop logon  which I was able to do and execute ls,du,df. Now 

what?  I agree that I will do a clean install. But now that I have a working 10.04 albeit in command mode what can I do in this mode to run programs . What change can i make to x.org.conf to  allow gnome to function?Can I do much,  running in command mode?
Can I access open office or mozilla firefox or what?

When I installed 9.04  I got an error message about my nvidia card and it told me what steps to take to obtain full resolution, which I did but now forget. Does anyone remember? My 9.10 upgrade accepted these changes but 10.04 did not. I suspect that 10.04 overwrote xorg.conf. I now don't know what to change in xorg.conf to restore my diplay. Right now I'm in the pre GUI world.

---

### Post by mörgæs on 2010-08-22
The command **startx** shoud bring up the GUI.

---

### Post by nu2u904 on 2010-08-22
New Note 7

Thank you tommcd. Your advice was great I did the apt-gets:
sudo apt-get update and got the reply that dpkg was interruped and I had to take manual action. This I did and 31 minutes of screen displays. I got a new command line.

Idid the apt-gets again and a few more packages were downloaded and installed. I did a shutdown and rebooted. Now the top choice was ubuntu 10.04. I selected this choice and everything came up in high resolution. I am composing this  response using  Tomboy Notes new note 7. 
I now have the problem that I have only 300MB disk space am unsure what big files I could delete. To make room for 10.04 I had deleted 3 iso files. Xp is running on a 500GB hard drive from which I had  carved out 10GB for ubuntu. I would like to carve out another 20GB for ubuntu and create separate partitions for home and perhaps another directory.  My problem is how do I assign another partion as /home while /home istill assigned to /. I haven't yet checked the site you recommended, but will do so now. I just did a cat /etc/lsb-release and got this:
ID=Ubuntu;release=10.04;codename=lucid;description=Ubuntu 10.04.1 LTS. Thank you for giving me something to think about

---

### Post by tommcd on 2010-08-24
> **nu2u904 said:**
>  
I now have the problem that I have only 300MB disk space am unsure what big files I could delete.
To clean ot the apt cache of old files that can no longer be downloaded, run:
```
sudo apt-get autoclean
```
To remove obsolete dependencies from your system run:
```
sudo apt-get autoremove
```
To clean out the apt cache of all downloaded files run:
```
sudo apt-get clean
```
Those 3 commands above should free up a bit of space for you.
To see what directories are using the most hard drive space run: ```
sudo du -csh /*
``` This takes a minute to run. You will likely get errors of the /proc directory. You can ignore that. You can run the **du** command without sudo, but you will get "permission denied" errors of the root partition and any other directories your user does not have read permission for.
To see how much space is used on your partitions run:```
df -h
```.
> **nu2u904 said:**
>  
  My problem is how do I assign another partion as /home while /home istill assigned to /. 
It is a lot easier to make a separate home partition during the install of Ubuntu, as per the psychocats link in my last post. 
You can move home to a separate partition after installing Ubuntu, but it is a bit more difficult. See these:
[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)
[https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving)
> **nu2u904 said:**
>  
To make room for 10.04 I had deleted 3 iso files. Xp is running on a 500GB hard drive from which I had carved out 10GB for ubuntu.
You can use a Parted Magic live CD (the link is in my last post) to shrink the XP partition(s) and then grow the Ubuntu root partition into the newly created free space. The partitions have to be contiguous to each other to do this. The GParted on the Ubuntu live CD can also do this. I like using Parted Magic for this stuff though.

---

### Post by nu2u904 on 2010-08-25
Thank you tomcmd. I tried 3 times last night to post a reply but the forumn wouldn' let me. I'm not at my Compact circa 2004 now and I did run the commands and cleared a half GB. I also found in Documents 3 large ms Office files 1.5GB that I had  migrated from Xp and will now remove. So I will have 2GB tp work with. I read the 2nd link and printed it and plan to try it out on my Dell laptop running 8.04. If it goes wrong I take your advice and make a clean install of 10.04  and do manual partitioning. Would it be wis e to make partions for other mount points?
 
I plan initially to create a partition mount ext3 filesystem and then move the contents of ~/Documents to it thus freeing up /. If that works then I'll create a separate partition for /home.

---

### Post by tommcd on 2010-08-25
> **nu2u904 said:**
> ... If it goes wrong I take your advice and make a clean install of 10.04  and do manual partitioning. Would it be wise to make partions for other mount points?

You can make as many partitions as you want and have room for when you use manual partitioning.
If you also have Windows partitions or other partitions with data on them, you can elect to choose mount points for them. You could mount them in the /media directory or wherever you want them.
I have a /data and a /data2 partitions on my desktop, for example.

---

