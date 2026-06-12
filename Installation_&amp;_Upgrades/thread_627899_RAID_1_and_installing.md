---
title: "RAID 1 and installing"
date: 2007-11-30
forum: Installation &amp; Upgrades
---

### Post by vsiege on 2007-11-30
I have a RAID 1 set up under my BIOS, and now Im going to install the system, and I havent a clue on how to partition the drives - what to pick from the list

---

### Post by Pumalite on 2007-11-30
Read this first:
[https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)

---

### Post by vsiege on 2007-11-30
I was told software RAID was terrible b/c if something ever happened that i could not take the disk out and bring it to another machine to recover the work

my install so far:
only going to be using this machine for 7.1 server edition (for now)
that documentation is not for 7.10
i am not at terminal

where do i go from here? my bios has the drives already in a RAID 1 config (theres an Intel controller in it)

---

### Post by mozkill on 2007-11-30
I tried the FakeRaidHowTo document and failed because my Ubuntu 7.10 install doesn't give me the option to install "dmraid" package.  Its obvious that the FakeRaid document needs to be updated.

I have a raid mirror installed on a ASUS P5K-E motherboard with a JMicron raid controller and the default Ubuntu installer seems to detect it correctly.

During the install, Ubuntu detects 2 devices that represent the 2 Seagate 1TB drives that I have.  It calles one of them /dev/hda  and the other one /dev/hdb  and it gives me the option only to install on /dev/hda   .   the /dev/hdb option is "grayed out" , which tells me that Ubuntu installer correctly recognizes it as a mirror drive.

If you want to hear about what I ended up with, just read my thread at:  [http://ubuntuforums.org/showthread.php?t=627308](http://ubuntuforums.org/showthread.php?t=627308) .

---

### Post by Pumalite on 2007-11-30
Unless you use hardware Raid the rest is a waste of time and pure headaches.

---

### Post by mozkill on 2007-11-30
I am unsure if the JMicron controller on my ASUS motherboard is a "hardware" or "software" raid.  I wish I knew, but I dont.  Tonight I am going to try the install once more.  If it doesnt work for me, I might prefer to buy a $100 "hardware raid" card than to mess around with Linux software RAID , which I dont understand.

Are you suggesting that I go ahead and try to do the linux "software RAID" mirror?

by the way, to answer the original posters question, use the option that says "auto partition and use ENTIRE drive".  It will make 2 partitions, one is ext3 and the other is a small swap.

---

### Post by Pumalite on 2007-11-30
Hardware Raid offers you real improvement in performance and is supported by Ubuntu from the word go.

---

### Post by vsiege on 2007-11-30
**Mozkill** I have the same board.
P5K-E / 2 seagate 500 / 4 ghz  RAM / IDE DVD-RAM and no other drives or speacial cards

BTW:
JMicron is the RAID controller for the external ports (page 5-42)
while
Intel ICH8R Southbridge RAID Controller is for the internal ports (page 5-34)

Im looking to use the internal ports for my RAID 1. So at this point you said just pick:
auto partition and use ENTIRE drive and I wont have to worry - it will be in the RAID 1 set by my BIOS?

should i not bother with the LVM or encrypted LVM part?

**Pumalite** Unfortunately i do not have access to a RAID card - would have been nice though.

---

### Post by siouzi on 2007-11-30
[QUOTE=vsiege]I was told software RAID was terrible b/c if something ever happened that i could not take the disk out and bring it to another machine to recover the work[/QUOTE]

No. That doesn't make sense, since you can install linux to another machine. Trying to read a disk used by a real hardware raid controller will most likely fail. RAID1 is not a backup system and you can still mess up your filesystem regardless of the raid beneath.

[QUOTE=vsiege]
Im looking to use the internal ports for my RAID 1. So at this point you said just pick:
auto partition and use ENTIRE drive and I wont have to worry - it will be in the RAID 1 set by my BIOS?
[/QUOTE]

If the installer sees only one disk instead of two, then you have real hardware raid and you don't have to worry. Two disks mean your raid is mostly software embedded in the BIOS and you can set up linux software raid. See example RAID1 setup [http://users.piuha.net/martti/comp/ubuntu/en/raid.html]("http://users.piuha.net/martti/comp/ubuntu/en/raid.html").

[QUOTE=vsiege]
should i not bother with the LVM or encrypted LVM part?
[/QUOTE]

Setting up RAID with encrypted LVM is not too difficult, but there is a bug which must be fixed at the end of the install [http://wiki.debian.org/DebianInstaller/RAIDvsCrypto]("http://wiki.debian.org/DebianInstaller/RAIDvsCrypto").

---

### Post by vsiege on 2007-11-30
> **siouzi said:**
> No. That doesn't make sense, since you can install linux to another machine. Trying to read a disk used by a real hardware raid controller will most likely fail. RAID1 is not a backup system and you can still mess up your filesystem regardless of the raid beneath.
Well, I have two 500 gb SATA drives (on SATA 1 and SATA3). I want this machine to serve as a file server as well as a LAMP test box. I had the two drives so it could be told to mirror to another - do I still have the BIOS think that its a RAID or do I set them back to IDE before i progress to my installation?



> If the installer sees only one disk instead of two, then you have real hardware raid and you don't have to worry. Two disks mean your raid is mostly software embedded in the BIOS and you can set up linux software raid. See example RAID1 setup [http://users.piuha.net/martti/comp/ubuntu/en/raid.html]("http://users.piuha.net/martti/comp/ubuntu/en/raid.html").
I finished installation but have no problem doing it again- the right way. Linux sees two drives. If my plan is to have a RAID 1 config. When I get to partiioning what do I select - which drive? 


> Setting up RAID with encrypted LVM is not too difficult, but there is a bug which must be fixed at the end of the install [http://wiki.debian.org/DebianInstaller/RAIDvsCrypto]("http://wiki.debian.org/DebianInstaller/RAIDvsCrypto").
Im not even sure what LVM is, not sure if its for me

---

### Post by siouzi on 2007-11-30
If the BIOS raid has some nice features, such as being able to tell clearly which drive failed or has the ability to rebuild the array completely before boot, I would keep the BIOS raid enabled.

Either way linux won't care and will see the drives as sda and sdb. Everything gets read from/written to md0, md1, ... software raid devices and these devices write data to both physical disks.

Using the linked tutorial as a guide you partition the drives and then combine the partitions to RAID1 (md) devices. Then set one of them to be /root and one swap. Remember to follow through the example setup carefully (set boot flags etc).

---

### Post by vsiege on 2007-11-30
I am in the process of reinstalling right now - I set both of my dives to act as IDEs in the BIOS. Now I am at the point in the installtion where I set both drives as one big partition: pri/log 500.1 gb FREE SPACE

can i start that tutorial after I have finished installation??

---

### Post by mozkill on 2007-12-01
> Mozkill I have the same board.
P5K-E / 2 seagate 500 / 4 ghz RAM / IDE DVD-RAM and no other drives or speacial cards

Hey, I also had to disable the onboard RAID on the P5K-E.  My machine was completely unbootable while the drives were in RAID mode.   For now, I am running in IDE mode.

I don't see any way that the ASUS RAID controller is going to work.  it wont even get as far as even attempting to load stage 1 of the boot loader. Its not a matter of Linux having the driver.

I need the 1TB RAID and so I went ahead and ordered the 3Ware PCIe 4-port raid card in hope that I can get a configuration that I can trust.  The reviews I read said it worked on Ubuntu and its also a pure hardware raid. its expensive but I will use the card for many years.

---

### Post by siouzi on 2007-12-01
> **vsiege said:**
> I am in the process of reinstalling right now - I set both of my dives to act as IDEs in the BIOS. Now I am at the point in the installtion where I set both drives as one big partition: pri/log 500.1 gb FREE SPACE

can i start that tutorial after I have finished installation??

The raid is set up during the install when it asks you to partition disks. You begin by selecting the FREE SPACE -line and create at least two partitions (primary type is fine). Then set the partitions' "use as" attribute to to "physical volume for raid". Repeat for the other drive.[http://users.piuha.net/martti/comp/ubuntu/en/raid.html]("http://users.piuha.net/martti/comp/ubuntu/en/raid.html")  does not have a picture for every step, you have to read carefully :)

---

