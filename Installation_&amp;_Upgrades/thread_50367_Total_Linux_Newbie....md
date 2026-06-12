---
title: "Total Linux Newbie..."
date: 2005-07-20
forum: Installation &amp; Upgrades
---

### Post by RyanW67 on 2005-07-20
Hey Guys, Warn you first, I am a total newbie to linux. Looking to install Ubuntu onto an old system I have got, spec is 200mhz, 98mb ram, 4gb hd with Windows 95 currently running.. On instructions simply says "put cd in and turn on/restart computer..." guessing this is ok for computers which boot from cd but mine doesn't... is there anyway to configure the system to boot from the cd, or could you tell me how to make a floppy boot?

Thanks!

Ryan.

---

### Post by WildTangent on 2005-07-20
installing on that system is a little iffy to begin with. i dont think youll have much luck with the default install. but if you want to try, this is how to enable boot from CD. when your computer is booting, repeatedly press the Delete key, thats the key used by most computers to get into the bios. search around here, to find where the boot order options are, and change it so the cd drive boots before the hard drive.

-Wild

---

### Post by Teroedni on 2005-07-20
if not del works you can try from F1 to F10 one of them most work

I think it should be possible to make it work
I have installed on a pentium 2 350 with an ati 3dcard and it worked.
didnt hack:)

---

### Post by RyanW67 on 2005-07-20
Thanks! yeah, didn't think bout bios settings. Just tried going in, but must have set a password.... seeing as Haven't used it for good 5 years.... best find that screwdriver.. lol.

---

### Post by WildTangent on 2005-07-20
ya, youll have to reset the CMOS if youve set a password. the easist way is to take the battery out, and put it back in. be careful you dont break the retention clip its in

-Wild

---

### Post by RyanW67 on 2005-07-20
Took battery out... left out for good 30 minutes, put it back in but password still there... :???:

---

### Post by WildTangent on 2005-07-20
do you know where the cmos jumper is? what it is, is 3 pins, with a jumper connecting  2 of em, when that jumper is moved over, it shorts the CMOS. it should be labelled on the mobo. dont do it unless youre sure its the cmos :P oh, and the board needs to be powered while you do it i think. short it for about 5 seconds, that should do the trick. someone correct me if im wrong, dont want the guy frying his mobo ;)

-Wild

---

### Post by mingus on 2005-07-20
First, resetting CMOS on the mobo is not always done the same way, although with an  old board the chances are the jumper technique was used.  I would google the mobo to find the manual.  Break something, may not be able to fix it.

However, unless I missed something, this all assumes that once you get into the BIOS you can change the boot sequence to include the CD-ROM.  On old systems, not necessarily.  In particular, laptops.  If you can boot from the floppy, there is another alternative:  Several diff pgms can do this, my pref is Smart Boot Manager.  You'll find it easily with google.  It is an assembler pgm that can chain-load to any bootable media on any device recognized by the BIOS.  When you boot SBM, you would see a menu with the CD-ROM, and since the Ubuntu CD has a boot sector, it will boot from the CD.

And btw, one of my boxes is older than yours; only 133Mhz.  Fortunately, another stick of RAM was cheap, and that made a big difference.  Gnome is still rather slow, but not impossibly so as long as I don't run a lot at the same time.  I use this as a test box.  If I were gonna use it for production, I would use Windowmaker instead.  (I don't like fluxbox and xfce doesn't seem to improve perf very much.)  I also added a larger HDD; if you consider doing that, you'll need to learn how to work around the 1024 cylinder limitation in the BIOS.

---

