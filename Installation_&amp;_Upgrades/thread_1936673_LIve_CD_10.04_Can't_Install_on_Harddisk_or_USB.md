---
title: "LIve CD 10.04 Can't Install on Harddisk or USB"
date: 2012-03-06
forum: Installation &amp; Upgrades
---

### Post by overcast on 2012-03-06
I am in interesting situation which makes it very hard for me to use computer. I am literally holding onto some random hopes in the universe. 

OKay, i am running ubuntu 10.04 cd on this machine where i can't install because the installation is jammed on step 3. I have only one Dvd reader where this cd is running so i can't install new iso of any new linux version while live cd is running on this machine. This machine has lost windows xp installation due to constatnt rebooting during cpu heating issue. 

NOw that issue is partially solved i am using live cd but can't use hard disk for linux installation. ALl previous versions are also stalling on step3 after keyboard selection. Now i am looking for a way to get myself out of this. I thought installing some small linux on 2gb drive and then using the iso of say ubuntu 11.10 (if downloaded) could solve this issue. MY problem is- which distro is small enough to fit under 2gb that gives me access to both Internet and also lets me burn the ubuntu 11.10 iso?
ALso any help on issue of installer hanging? Should I download alternate install from the torrent?

Any help?

---

### Post by Quackers on 2012-03-06
What exactly do you mean by step 3? What is on the screen at the time and why can't you continue?

---

### Post by overcast on 2012-03-06
Step where you choose the keyboard, that's on step 3. for me it's US keyboard. I cant continue setup because it keeps on buffering for hours ( last time tried it took 6 hours for nothing). I don't know what seems to be the problem but not even older ubuntu 7,8,9 version can go past that. It could be because of CPU heating but not sure what to do about it. I don't have anything on USB to boot and run GUI. I failed to make bootable USB via Live CD. For the rest check my OP.

---

### Post by darkod on 2012-03-06
Are we talking about wireless keyboard or wired one?

Do you select your keyboard from the list or let it detect it? The detection maybe gets stuck from what ever reason.

EDIT: Try to check the MD5SUM of the iso you used for the cd. Also, try burning a new cd at low speed, not more than 8x or 10x. Did you burn this cd at max?

To be honest, I don't understand most of your OP. You say you have only one dvd drive like that's a bad thing. You only ned one since I guess you are trying to install onto the hdd.

Does live mode (Try Ubuntu) work fine? Does it load correctly?

If yes, can you see the hdd correctly?

---

### Post by overcast on 2012-03-06
I have wired keyboard. Logitech and it doesn't let me select the type, it just stops at choosing the layout - US in this case. SO that's step 3. 

UBuntu 10.04 CD is from shipit so not downloaded one.

The reason having one drive is bad thing is because ubuntu livecd is not installing and i can;t use it for burning the iso of new linux image which is 11.10. I guess you can understand why that drive is not helping here because one livecd is not installable and another iso is not burned and cant be burned as there is no OS. 

I am posting this from live cd browser and i can see the hdd (windows partitions ) too. But the instllation doesn't work for 10.04 and when i boot the cd, it shows message,"unrecoverable error in installer occured, check the error and see it on desktop"soething like that and the livecd desktop loads everytime i boot with it. 

Should I format the boot partition and see if the livecd works? or boot partition of disk has nothing to do with livecd? I am just getting dense here.

---

### Post by darkod on 2012-03-06
The hdd shouldn't matter, but if you are happy losing the data on it (and you seem OK with that), I would:
Boot into live mode. Open Gparted. Write a new msdos partition table with the Device - Create Partition table option.

That will write a new blank partition table. There will be no existing partitions after that.

Try the install once more after that, maybe it gets stuck trying to continue from the keyboard step, not because of the keyboard. There is no need to create partitions in advance, simply try the install once more after you created the new part table.

Also, if you have a usb stick at hand (at least 1GB), you can try:
Make a ntfs partition on the hdd (if you created new table as above).
Download the 11.10 iso there.
Plug the stick in, format it as FAT32 (that will delete all data).
Use the Start Up Disc creator to create the live usb with the iso you downloaded.
See if you have better luck installing 11.10.

---

