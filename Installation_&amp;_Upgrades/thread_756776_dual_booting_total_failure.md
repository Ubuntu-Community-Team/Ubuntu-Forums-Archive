---
title: "dual booting total failure"
date: 2008-04-16
forum: Installation &amp; Upgrades
---

### Post by tez-a on 2008-04-16
hi all, I have a maxdata pc with an intel pentiumd 945 cpu 3.40 ghz,i gig ram ddr2, a bucketfull of hard drive space about 35 gig on c 70 gig on d and 76 on e,a nvidia7300 graphics card and an old targa monitor with res up to 1200 x1040..ihave dual booted successfully before xp and xp pro 64 bit.but when it comes to ubuntu. i hit problems tried 4 ways.
1:obtained the linux disc from sourceforge.not a download.set boot agent to install from disc.inserted disk and reboot. iget the start window. click start.the kernal loads and then i get a blank screen give it a while to load but thats as far as it goes.
2:tried wubi 8.04. click on the logo. it downloads the file and then asks for a reboot. reboot and on my boot page i have 2 lines win xp and ubuntu. move to ubuntu and get kernel alive on one line and kernal direct mapping tables up to 100000000 @8000^d000. then nothing.
3: cleaned wubi out run a reg cleaner and tried wubi 7.04 again it goes through in windows reboot and click the ubuntu loader. get one screen with a load of stuff on then get a page with the following
     hd0,0
  filesystemtype is ntfs,partitiontype 0x7
[linux-bzimage,setup=0x1c00,size0x1a820c]
linux-intrd @0^1f85e000,0^7918a5by
then nothing.
4: cleaned out and downloaded ubuntu 6.10 burnt iso to disk inserted disk get the start screen then nothing.
   anyone any ideas what i am doing wrong.

---

### Post by redbob on 2008-04-16
It seems to be hardware issue, not exactly a defected hardware, but there's something in your machine Ubuntu is not recognizing... are you setting up your Ubuntu with Live or Alternate CD?

---

### Post by tez-a on 2008-04-16
its a sourceforge disk

---

### Post by dstew on 2008-04-16
> downloaded ubuntu 6.10 burnt iso to disk inserted disk get the start screen then nothing.Is it a Live CD, or an alternate install CD? What does the start screen look like? Are there menu options? Is one of them "Start or Install Ubuntu"? If so, what happens if you click on that? Did you try the CD integrity check?

---

### Post by tez-a on 2008-04-17
start or install is the first line.

---

### Post by zvacet on 2008-04-17
Download alternate CD [here.]("http://releases.ubuntu.com/7.10/")

---

### Post by hums07 on 2008-04-17
An option is that you make new partition using Windows Disk Management (right click Computer icon in Start menu -  Computer Management - Disk Management). Then try this : [https://help.ubuntu.com/community/Installation/FromWindows](https://help.ubuntu.com/community/Installation/FromWindows)

---

### Post by tez-a on 2008-04-17
to dstew tried the diskcheck and the alternate cd. my problem may be with the graphics card. the onboard card is a radeon 200 which is no longer supported so installed the nvidia 7300 gx. have been to the web site and there are drivers for linux but afraid to download them in case they throw out my xp.   tez-a

---

### Post by dstew on 2008-04-17
The Linux drivers should have no effect on your XP system, unless you try to install them on XP. You install the Linux drivers onto the Linux system.

---

### Post by tez-a on 2008-04-17
tried another way uninstaller allowed it to download then reboot when asked to click on the uni logo it goes through the motions then i get error 13. thanks for all the help so far

---

### Post by dstew on 2008-04-17
> tried another way uninstallerWhat is uninstaller?

---

### Post by zvacet on 2008-04-17
I don´t believe your problem is related with video card,because I have one of worst existing video card and never had problem installing Ubuntu with alternate Cd.Did you check [md5sum]("https://help.ubuntu.com/community/HowToMD5SUM")?Did you [burn iso]("https://help.ubuntu.com/community/BurningIsoHowto?highlight=%28iso%29") properly?Did you check Cd for errors (it is one of options when you boot)?If you find any corrupted files download same iso with torrent and point download to the folder iin which is your iso.Torrent will just check your iso and replace corrupted files.After that check md5sum again,burn iso on CD and check Cd for errors.You should be able to install.

---

