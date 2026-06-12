---
title: "Updated Instructions for Ubuntu RAID install needed"
date: 2012-11-21
forum: Installation &amp; Upgrades
---

### Post by divxclub on 2012-11-21
Hi there for past 3 years I had my eye on Ubuntu for my main workstation. I tried several times before and I always had errors. Let me explain.

I have Asus P6T Deluxe v1 mobo and with single drive straight or dual boot with Windows 7 it works perfectly but that's not what I want. My setup is dual SSD drives on RAID0 array. After installation on first boot it'll say OS not found, I think this is have something to do with GRUB because os install just fine from Live CD but on very first boot everything gets messed up and once again on single drive on same system all good with dual boot or single boot. Now if possible can anyone point me to right direction I want to have Windows 8 and Ubuntu together on Dual SSD RAID0 array.

Thank you.

---

### Post by darkod on 2012-11-21
For install on raid you need to use the Alternate Install CD, not the standard desktop live cd.

You still end up with the same system, but the installer is text based (not GUI) and it has better raid support.

If you use the live cd on raid, usually the last step, the grub install, fails. Like it happened to you. You can still add only grub after that and use the system, but if you are starting new it's better to use the alternate cd directly.

You are aware that raid0 doesn't give you any redundancy, right? If one disk goes, you lose all data.

---

### Post by divxclub on 2012-11-23
Thank you for your reply. I am aware of difference between RAID0 and RAID5 when with SSD there is virtually no difference in access time I do see performance bump but it's debatable a lot of people think SSD in RAID0 is a waste but for me it just works. Now about installing Dual boot with Windows 8 and Ubuntu on RAID0 Setup. I do know about this non GUI version of Ubuntu called Alternative installation CD but I never used it before. Is there a instructions on how to install on RAID0 setup or (more importantly for me) will it do correct job on last step with it configuring GRUB to use with Windows and Ubuntu on RAID0 array.

Thank you VERY much for your answer I really appreciate them.

---

### Post by darkod on 2012-11-23
I don't have a link with any instructions ready, but it's very straight forward.

You will set up your fakeraid array using the bios built in controller, and then install win8 on it. Make sure you create the partition for win8 with the size you want to allocate to it, don't let it take the whole hdd (you plan to dual boot anyway).

When you boot with the alternate cd and start the install, when reaching the partitioning step it would usually ask you if you want to activate the detected raid. Just say yes and it should show the raid array with the existing win8 partition(s) on it. You simply use the remaining unallocated space on the array to install ubuntu.

I would use the manual partitioning, gives you more control of what goes where. If it looks strange to you, not showing the array or win8 on it, abort the install to investigate.

Towards the end, installing grub should work fine, that's the point of using the alternate cd. In any case it's better to be prepared and in the partitioning step note down the device name of your array, it will be something like /dev/mapper/blah-blah...

If the grub installer tells you it can't find the target to install and asks you where to install, just use the array device name (NOT any specific partition on it), the onw you noted down. It should install grub fine.

---

### Post by divxclub on 2012-11-24
Thank you for reply but I don't think you understand I DO have raid0 setup. I have 2 physical SSD drives together in RAID0 Array for boot. I also have 3 physical Raptors as my progrms RAID0 array and I also have stand alone 1 Caviar Black for downloads and another for backups. Total of 7 Hard drives in my system. Now fakeraid is term you use for a program or ? Because my hardware Marvell controller is pretty real. Anyhow I am under Virtual conditions trying to install Ubuntu. After installation it asking me "Install the GRUB boot loader to the master boot record" ?yes or no ...if I select yes it just complete install. Again this is single boot without (this time) fake raid.

Thanks !

---

### Post by darkod on 2012-11-24
I was speaking in general, if you already have the arrays running that's big part of the job done.

I don't think you can test hardware raid in VM, not sure if it sees the hardware controller. Software raid you could test because it works on OS level anyway.

Why don't you try doing the install and you will soon see if it recognizes the raid in the partitioning step, and continue the install. As already mentioned, grub usually installs OK on raid with the alternate cd. Now you only need to try.

---

### Post by divxclub on 2012-12-02
Once again thank you for your answer and to be honest with you I really hate to lose current installation of Windows 8. What I will do I'll do exact backup image of my Windows 8 installation and I will try to install Ubuntu after. From what I remember last time finding correct array was not the problem even regular Live CD could find correct RAID0 array and install Ubuntu without errors. Only on last step if once again I remember correctly it asked me some weird question , something like where would you like to install Grub or what partition to use to install boot mark ....something like that ...and after boot I got "System not found" error. And I consider myself an expert in PCs however I never learned how to properly edit boot.ini file to manually just reconfigure it at will and no matter what happen I can always redo it and boot in to system no matter what.

P.S. (kinda remembering something warm and close to me)

On similar subject I just want to say remember when to install Windows 95 from CD (not floppy version) you had to first enable CD drive in MS-DOS so it accessible and it had to be done manually at first. Only later with Windows 98 they came out with function to create Bootable floppy so MS-DOS "knows" about CD drive ...well anyhow that manual configuration of system boot files always been topic of something I always wanted to do and learn yet never actually did it .....well one day I may come back and emulate dos to practice :D

---

### Post by divxclub on 2012-12-02
I think Ubuntu is playing with me ....... never had problem with crc stuff on flash card now I just tried to install Ubuntu and on screen after keyboard detection it's saying that CD-ROM not detected ... I mean doesn't it knows it is flash media and no longer CD or DVD and how da hell it happened I use official ISO and Ubuntu recommended usb creator ....anyhow check picture below ...
Also because I saw some interesting menus I decided to select some like detect network device. How come it didn't detect any I mean on live cd it see my Ethernet card without any problem ...not here. Guys I almost at the point of not worth effort line here.....I'll do format of my flash card ..not quick a long one and will redo iso image on it will try again ...if not ...well c ya in another 3 years ....
[IMG]http://i386.photobucket.com/albums/oo309/divxclub/Public%20Stuff/IMG_20121202_0351231.jpg[/IMG]

---

### Post by darkod on 2012-12-02
Well, if it says the checksum failed, I guess it failed. Maybe the file got corrupted while copying to the flash card, or the ISO during download. Or the card has developed a fault on some sectors, that's a possibility too.

As far as the grub2 bootloader location you mention it asked you last time, that's what we are discussing all the time. The live cd does not install the bootloader correctly on fakeraid / hardware raid.

You either have to add it manually after the install, or use the alternate cd.

---

### Post by divxclub on 2012-12-02
Understood.

Yeah it looks like flash card is bad. So what I did is got diffirent card and put image there. I am still getting can't mount CD error ....yes checksum is okay no problem found. It almost looks like it's trying to load files from CD instead of flash card. So once again MD5 checked out yet setup saying can't mount. I guess I have to go get CD and burn one ... I don't even have ImgBurn anymore on my system :D

Look:
[IMG]http://i386.photobucket.com/albums/oo309/divxclub/Public%20Stuff/IMG_20121202_0450031.jpg[/IMG]

Any other suggestions other than simple CD burning

---

### Post by darkod on 2012-12-03
Yeah, it does the same when you are trying to install the server version from usb stick. It actually wants the cd to be present.

If you have enough space on the card to add the ISO (the whole file, not extracted) without deleting any of the extracted files on the card, I have used this procedure to go around this procedure. I used it for the server ISO but it should work for the alternate too. Just make sure you get the ISO name correctly:
[http://ubuntuforums.org/showpost.php?p=9705738&postcount=2](http://ubuntuforums.org/showpost.php?p=9705738&postcount=2)

---

### Post by divxclub on 2012-12-03
Thank you for advice ! I'll let you know how did I do .......

---

