---
title: "Installing Ubuntu for the 1st Time, need help with Partitions"
date: 2010-01-10
forum: Installation &amp; Upgrades
---

### Post by MariosFFX on 2010-01-10
Greetings to the Community,
I got bored with Windows and tried ubuntu for the 1st time some hours ago and I would like to install it as the Main OS without and other OS (Single Boot).

The problem I have is with the partitions because I saw some options like: /, /home, /boot and some other options which I don't remember at the momment

Since I will use ubuntu as the main OS I want it to take complete control of the PC and use the hard drives and whole system to the fullest.

Here are my system specs:

CPU: Core i7 920
M/B: DFI LanParty UT X58-T3eH8
RAM: OCZ Intel i7 6GB DDR3-1600 RAM Kit (8-8-8-24, Triple Channel)
VGA: Sapphire Radeon HD4870 1GB
HDD: Adata 80GB X25-M SSD by Intel, 
WDCaviar Black 1TB (WD1001FALS, 7200rpm, SATA), 
WD 250GB

1) Since I had Windows 7 I had configured it to store my files as the Pictures,Downloads,Videos (default location if you prefer) to the other drives is it possible with Ubuntu?
2) What partitions should I make?
3) What /, /home and the other options actually do?
4) Is VMWare available for Linux or any other software which will enable me to use Windows as well?
5) Also which file systems are the best? (NTFS, ext3, ext4 etc.)

---

### Post by itachisxeyes on 2010-01-10
well when your installing it you would need to select "guided: use whole disk" 
or just delete the windows partition 

i'm not sure that VMware is available, never looked for it. but i use virtualbox for emulating things
the best format would be ext4, ubuntu won't install on NTFS though it can read it
and if you just use the guided install you won't have to worry about making swap partitions and all that.
ubuntu does have default folders (music, video, documents and such)

---

### Post by Revolutionary101 on 2010-01-10
1) Yes
2) Make 3 partitions on your SSD. One should be a / partition (65 GB), another /boot (5GB) and the other should be swap (10GB). Then make /home on your 1TB Hard Drive and do whatever you want with your 250 GB drive
3) They just represent folders. / is mostly system files and /home is like your My Documents folder. Your /boot folder is where your computer stores the information for boot up. Another important one is swap and this is basically just like your pagefile (virtual RAM) in Windows.
4) Yes, I would suggest using virtualbox
5) I would suggest using ext4

---

### Post by llawwehttam on 2010-01-10
> **Revolutionary101 said:**
> 1) Yes
2) Make 3 partitions on your SSD. One should be a / partition (65 GB), another /boot (5GB) and the other should be swap (10GB). Then make /home on your 1TB Hard Drive and do whatever you want with your 250 GB drive
3) They just represent folders. / is mostly system files and /home is like your My Documents folder. Your /boot folder is where your computer stores the information for boot up. Another important one is swap and this is basically just like your pagefile (virtual RAM) in Windows.
4) Yes, I would suggest using virtualbox
5) I would suggest using ext4

I agree with this. You could also use your 250GB drive for backups.

---

### Post by theozzlives on 2010-01-10
With 6 GB RAM, you want to install the 64 bit version as 32 bit supports up to 4 GB. Your / only needs to be about 20 GB, anything more and you're just wasting space. You don't need a /boot, it'll be in /. I would consider the 1 TB as /home. the leftover real-estate can be used as mount points of your choosing. Like your 250 GB could be /home/<username>/backup and Back-up important stuff to it. The installer will set that up, you're not limited to only the mount points the installer gives you. Looks like it'd be fun to play around with, good luck.

EDIT: Oh I would put a 6-12 GB swap on the SSD with /.

---

