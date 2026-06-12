---
title: "Jaunty Install Didn't Partition Enough HDD"
date: 2010-02-03
forum: Installation &amp; Upgrades
---

### Post by Uadebisi on 2010-02-03
Hi,

Well, after a couple of months of fiddlin w/ 9.10 I decided to try 9.04 Jaunty. So, on my dual booted w/ Windows machine, I wiped out 9.10 from directly from the HDD using Gparted. I have a 40 gb HD & about 14 gb was allocated for 9.10 so, when I removed 9.1 from the HD & left 14 gigs or so unallocated, I assumed that my new install of Jaunty would fill its place. I chose the option on install to have Windows & Ubuntu run side by side & Windows seems to be fine. I can boot into either on startup yet when I ran Update Manager, I learned that I do not have enough HDD space. See info below:


Filesystem            Size  Used Avail Use% Mounted on
/dev/sda5             2.3G  2.1G  136M  94% /
tmpfs                 245M     0  245M   0% /lib/init/rw
varrun                245M  108K  245M   1% /var/run
varlock               245M     0  245M   0% /var/lock
udev                  245M  144K  245M   1% /dev
tmpfs                 245M   76K  245M   1% /dev/shm
lrm                   245M  2.4M  243M   1% /lib/modules/2.6.28-11-generic/volatile

I reinstalled Gparted to get a look at the HD & noticed that Windows is taken 34 gigs now, not 22 as it was with 9.10 running. I don't know what happenned or how to fix it w/o effecting Windows. 

I assume I will need to remove 9.04 & install it again but I am guessing that I need to do something different this time. Any help will be appreciated. Time to go to bed. Will check back in the AM. Thanks!
 		                   		  		  		  		  		  	   	 		 [IMG]http://ubuntuforums.org/images/statusicon/user_online.gif[/IMG]  		 		 		 		 		  	 	 	 	 		  		 		 		 			[[IMG]http://ubuntuforums.org/images/buttons/quote.gif[/IMG]]("http://ubuntuforums.org/newreply.php?do=newreply&p=8762390")

---

### Post by Zifnab06 on 2010-02-03
If you boot from the install cd, you can "Try Ubuntu without changing your computer". You can also start gparted from there, and fix partition sizes. Just right click a partition on /dev/sdxx where xx is the drive letter and partition number. Click resize. Put the new sizes in and wait. Maybe backup first.

---

### Post by darkod on 2010-02-03
When you already have unallocated space on the hdd, you need to use the Largest Available Free space option during install. Do not get confused by the Side-by-Side option, that option is used when you need to resize the windows partition to make space for ubuntu at the same time.
When you have only one hdd of course they will be side by side, regardless which option you use.
If you wanted ubuntu to take the 14GB space you needed to use the option I mentioned.

Also, in the screen in step 4 you can see one colored bar at the top, and one at the bottom. The top shows your hdd partitions as they are currently, the bottom bar shows how they will be after the install. You need to pay attention to the bottom bar when using any of the guided options. For side-by-side there is a slider on the bottom bar that you need to set how to split up the space between windows and ubuntu. That's how windows can actually get enlarged, depending where the slider was.

---

### Post by Uadebisi on 2010-02-04
Thanks for the info!

**Darkod**,

I didn't notice the info while installing Jaunty that you described but it certainly does explain things :)

So, I did what **Zifnab06 **suggested & I believe everything is working fine. I wanted some input before I messed with the HDD again as I did not want to disturb Windows. 

I believe Windows is okay after the resize although it needed to restart initially as it found some sort of device that required a restart to function. The prompt wasn't specific. According to the Event Log, there was some issue finding a driver, & a couple of other things but all seems to be working now. We'll see...

Haven't had much chance yet to play with Jaunty....I hope I do not experience the many bugs that I did with Karmic. I will now be starting a thread pertaining to upgrading to a newer version of Firefox from Jaunty:)

Thanks again!

---

### Post by Uadebisi on 2010-02-04
**Darkod,**

On second thought....I do seem to remember something about "the largest available space". Anyway, I didn't rush through that part of the install & *thought* I investigated all options very carefully... but apparently not.

I do not like not knowing! I almost want repeat the process & install again, just so I will know what happened....almost ;)

---

