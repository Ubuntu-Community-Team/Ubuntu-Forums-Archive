---
title: "Issue upgrading from 10.04 -&gt; 11.04"
date: 2011-04-17
forum: Installation &amp; Upgrades
---

### Post by Ventai on 2011-04-17
Hi there, 

I recently upgraded from 10.04 to 11.04 (Natty Narwhal). 
When upgrading, the system reported I was running out of memory in boot, also before the upgrade finished, the screen went blank and I had to hard reboot. 

At first it looked as though everything installed ok, but a few errors came up, it tried to do a 'partial upgrade' but there were some errors still. 

After running apt-get dist-upgrade i got the below:- 


system@ubuntu:/var/lib/dpkg/info$ sudo apt-get dist-upgrade 
Reading package lists... Done 
Building dependency tree       
Reading state information... Done 
Calculating upgrade... Done 
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded. 
1 not fully installed or removed. 
After this operation, 0B of additional disk space will be used. 
Do you want to continue [Y/n]? y 
Setting up initramfs-tools (0.98.1ubuntu6) ... 
update-initramfs: deferring update (trigger activated) 
Processing triggers for initramfs-tools ... 
update-initramfs: Generating /boot/initrd.img-2.6.35-28-generic 

gzip: stdout: No space left on device 
E: mkinitramfs failure cpio 141 gzip 1 
update-initramfs: failed for /boot/initrd.img-2.6.35-28-generic 
dpkg: error processing initramfs-tools (--configure): 
 subprocess installed post-installation script returned error exit status 1 
Errors were encountered while processing: 
 initramfs-tools 
E: Sub-process /usr/bin/dpkg returned an error code (1) 


I guess this could be to do with the little space left - it looks like root is full / usage at 100% (?) 
(see attachment)

I was going to run 'Computer Janitor' but didn't want to remove anything required for the interrupted install process. . 

Thanks

---

### Post by TheExposedOne on 2011-04-17
aren't you supposed to upgrade to 10.10 and then 11.04?

---

### Post by Ventai on 2011-04-17
Oh no, don't say that - I was trying to just go to 10.10, but because of the issue, when I did a hard reboot, it had gone straight to 11.04!!

:)

---

### Post by dFlyer on 2011-04-17
If root is full, your going to have to make more room before you proceed. I would recommend you try sudo apt-get autoclean which should strip out older deb files and give you a little more room. Also I'm under the impression that the upgrade route is 10.04 to 10.10 to 11.04.

---

### Post by Ventai on 2011-04-17
Thanks very much, that did free up about 400MB, but I'm still getting the same error. . 

Is there any other way to free up more space / go back to 10.04/10?

Cheers

---

### Post by Ventai on 2011-04-17
Please see the attachment...

Interesting, it seems to have installed multiple versions, or part of multiple versions (maybe that's 

why root is full(?))

From the top of the screen grab:- 

- The first is 11.04 (even though it shows a 10.10 splash at the beginning(!?))

- The second freezes at the splash 

- The third freezes at the splash 

- The forth freezes at the splash 
	- but the first time I tried to boot it said 'press 'c' to cancel all checks currently 	  

underway' (I have a feeling this was the previous 10.04 install)
UPDATE: I got into this with recovery mode and it still said 11.04

- The fifth freezes at the splash 


Hmm, I'm a bit lost :(

---

### Post by Ventai on 2011-04-17
Can anyone please advise (or point me to somewhere that can) as to how I would do a complete Ubuntu 10.04 re-install? (or I could download 10.10 and burn to disk)

As mentioned, I also have a Windows 7 installation on another partition that I'd like to retain. 

And I think this is important -> Grub is managing the OS boot structure (from the initial 10.04 install). 

Many thanks

---

### Post by garvinrick4 on 2011-04-17
##You can try:
```

[CODE]sudo dpkg --configure -a
``````
sudo apt-get -f install
``````
sudo apt-get install aptitude
``````
sudo aptitude update && sudo aptitude safe-upgrade
```##I would say you do have to resize your Ubuntu partition to make
it have more space, it is tough to run an OS with no room on partition.
To go from 10.10 to 11.04 is:
```
sudo sed -i 's/maverick/natty/g' /etc/apt/sources.list && sudo aptitude update && sudo aptitude dist-upgrade 

```##But again you do not have enough space on partition to upgrade.

##Like post above to clean out cache is:
```
sudo apt-get clean
``````
sudo apt-get autoclean
```##Have a nice day:
[/code]The better way is to just download 10.10 maverick and burn a new disk and install after resizing partition in gparted.
[Download Ubuntu | Ubuntu]("http://www.ubuntu.com/getubuntu/download")
##Nothing like a nice fresh install, well a few things but a fresh install is nice:

---

### Post by Ventai on 2011-04-17
> **garvinrick4 said:**
> ##You can try:
```

[CODE]sudo dpkg --configure -a
``````
sudo apt-get -f install
``````
sudo apt-get install aptitude
``````
sudo aptitude update && sudo aptitude safe-upgrade
```##I would say you do have to resize your Ubuntu partition to make
it have more space, it is tough to run an OS with no room on partition.
To go from 10.10 to 11.04 is:
```
sudo sed -i 's/maverick/natty/g' /etc/apt/sources.list && sudo aptitude update && sudo aptitude dist-upgrade 

```##But again you do not have enough space on partition to upgrade.

##Like post above to clean out cache is:
```
sudo apt-get clean
``````
sudo apt-get autoclean
```##Have a nice day:
[/code]The better way is to just download 10.10 maverick and burn a new disk and install after resizing partition in gparted.
[Download Ubuntu | Ubuntu]("http://www.ubuntu.com/getubuntu/download")
##Nothing like a nice fresh install, well a few things but a fresh install is nice:


Hey there, 

You say 'resize the partition', how do you mean?

The partitions are already set up. This is pretty much how I did it:- 

Grub Boot partition 128MB	- 	ext3	
Swap partition 6 GB 		-	filesystem type linux-swap?
Ubuntu part. 20 GB		- 	formatted as ext4? (/ meaning root)
Logical partition 30GB		-	formatted as ext3 or ext4 for linux storage (/home)
Logical partition 20GB		- 	formatted as FAT32


I've never done a Linux reinstall with grub and a dual boot before, and want to make sure I don't mess anything up :)
You can also see above that my grub appears to have multiple Linux installs in, as well as Windows. I'm not sure how to wipe those but leave Windows on there. . 

Cheers

---

### Post by Dutch70 on 2011-04-17
Those aren't different installs, they're kernels. Although I'm not sure how -28 got above -31 in the list.

You don't need a /boot partition, but as I've never had a separate /boot, I can't tell you anything about it.

If / is 20GB, I find it difficult to believe it's full.

Why the FAT32 partition instead of NTFS? :confused:

To remove the older kernels, open synaptic & search for "linux-image-2" Be careful not to remove the wrong one & it's best to keep at least 2. 
I wouldn't do anything with those until you get your other problems sorted out.

Also, open gparted and take a screenshot of your partitions. 
Attach it to your next post using the paper clip on the toolbar.

---

### Post by garvinrick4 on 2011-04-17
+1 with Dutch70
 Just did a install of natty with upgrading to a pretty nice system and it
is at 3.2 gig with nothing in /home
 Something is wrong if you got a / of 20 gig and it is full with a seperate partition
for /home
 Needs investigation install gparted if not installed and give Dutch70 a screenshot
```
sudo parted -l
``` That is a lower case L (above will show sizes in gigs.)
## And give gparted screenshot as Dutch70 recommended.

---

### Post by Ventai on 2011-04-18
> **Dutch70 said:**
> Those aren't different installs, they're kernels. Although I'm not sure how -28 got above -31 in the list.

You don't need a /boot partition, but as I've never had a separate /boot, I can't tell you anything about it.

If / is 20GB, I find it difficult to believe it's full.

Why the FAT32 partition instead of NTFS? :confused:

To remove the older kernels, open synaptic & search for "linux-image-2" Be careful not to remove the wrong one & it's best to keep at least 2. 
I wouldn't do anything with those until you get your other problems sorted out.

Also, open gparted and take a screenshot of your partitions. 
Attach it to your next post using the paper clip on the toolbar.



Good morning (If you're in the UK :))


Do I not want to remove all kernals? As I want to do a complete reinstall, but leave windows on there (in grub). 

Please see attached for the screenshot.

As I'm sure you can see, this is what's going on:- 

/dev/sda1-3 are Windows partitions (it's just the way it panned out :))

/dev/sdas4 is the extended partition with 5 logical partitions for Ubuntu (Studio)

/dev/sdas5 is the almost full boot partition

/dev/sdas6 This was meant to be the swap partition (there's an error here)

/dev/sdas7 root

/dev/sdas8 home

/dev/sdas9 shared storage for Windows and Linux

---

### Post by Dutch70 on 2011-04-18
If your doing a fresh install, you don't need to delete any kernels. I would consider repartitioning some though. 

First, I would reformat the fat32 prtn to ntfs. Just back up whatever you have on it. 

Do you have 6GB of RAM? Your swap prtn just needs to be equal to the size of your physical RAM, slightly larger for overflow if you want.

If I was going to reinstall, I'd back everything up and repartition like this.

/boot = Not needed 
/ = 15-20GB - you're only using 6.55GB now.
swap = equal to the size of your RAM
/home = the remainder of your extended partition.(see below)

I'm not sure what you use the 20GB fat32 prtn for, but there are a few different ways to do that. One is to use ntfs not fat32. Another is to just use a folder in sda3 & add that 20GB to /home. Also you could format /home to ext3 and install fs-driver in windows, then windows can read ext3 file systems.
[[COLOR="RoyalBlue"]http://sourceforge.net/projects/ext2fsd/[/COLOR]]("http://sourceforge.net/projects/ext2fsd/")

---

### Post by Ventai on 2011-04-18
> **Dutch70 said:**
> If your doing a fresh install, you don't need to delete any kernels. I would consider repartitioning some though. 

First, I would reformat the fat32 prtn to ntfs. Just back up whatever you have on it. 

Do you have 6GB of RAM? Your swap prtn just needs to be equal to the size of your physical RAM, slightly larger for overflow if you want.

If I was going to reinstall, I'd back everything up and repartition like this.

/boot = Not needed 
/ = 15-20GB - you're only using 6.55GB now.
swap = equal to the size of your RAM
/home = the remainder of your extended partition.(see below)

I'm not sure what you use the 20GB fat32 prtn for, but there are a few different ways to do that. One is to use ntfs not fat32. Another is to just use a folder in sda3 & add that 20GB to /home. Also you could format /home to ext3 and install fs-driver in windows, then windows can read ext3 file systems.
[[COLOR="RoyalBlue"]http://sourceforge.net/projects/ext2fsd/[/COLOR]]("http://sourceforge.net/projects/ext2fsd/")

Ok.. Can you advise me on whether this guide would be applicable to my type of re-install (if I use my 10.04 disk as I need to get this done very soon):- 

[http://sites.google.com/site/easylinuxtipsproject/reinstallation](http://sites.google.com/site/easylinuxtipsproject/reinstallation) 

- With wanting to retain Windows grub presence
- It says there that you should not destroy the swap, however my appears to be damaged 


Many thanks

---

### Post by Dutch70 on 2011-04-18
That site seems to be ok. The only reason I can think of that it would tell you not to destroy the swap prtn is because it can be used for a quicker install. N/A to you, because you don't have one. :)

When you reinstall and update grub (as root) it will pick up windows & put it in the menu.

Do you plan to wipe & re-create all of your partitions? If so, I would boot up the live cd/usb & select Try Ubuntu. Then create the prtns and click "install" from there.

---

### Post by Ventai on 2011-04-18
Hi, 

Thanks for your time with this....

I'm planning to 'destroy' the partitions as mentioned in that guide. 

> When you reinstall and update grub (as root) it will pick up windows & put it in the menu.

Will using GParted from the live CD reinstall and update as root?

---

### Post by Dutch70 on 2011-04-18
You're welcome.

After you use Gparted to repartition your hdd & then install Ubuntu. You have to login to the installed Ubuntu system to update grub.
Open a terminal and run...
```
sudo update-grub
```

Also, the more info you give, the more you get.

---

### Post by Ventai on 2011-04-19
Right, excellent stuff - gonna go for it and hope for the best :) 

Thanks again

---

### Post by Ventai on 2011-04-19
Went perfectly - I actually just chucked in the 10.04 live CD, installed, formatted the current partitions during the install, and voila! It did the 10.10 upgrade for me :)

---

### Post by Dutch70 on 2011-04-19
Great! Did you partition your hdd differently?

---

### Post by Ventai on 2011-04-19
To be frank I've completely over spent time on this already. So I pretty much left it as is. 

Thank's a lot for the helpful advise Dutch70!

---

### Post by Dutch70 on 2011-04-19
As long as you got it installed & you're happy with it, that's all that really matters. 
At least you know you've got back up if you decide you ever want to do something different. ;)

---

