---
title: "installing ubuntu studio without dvd drive:please help"
date: 2008-05-19
forum: Installation &amp; Upgrades
---

### Post by saidinesh5 on 2008-05-19
hello friends,
 i wanted to install ubuntu studion on my pc, n i have this antique pc of myne where in it doesnt have a DVD drive... i finally managed to download the ubuntu studio after a hellish experience on this slow internet of myne so , apart from the suggestions like download ubuntu and den install ubuntu studio aver it , or using virtual box, is there any way how to install it on my PC?

i have tried it using wubi, but it failed...wubi doesnt detect the iso when i placed it in the same folder, n it didnt evn detect whn i mounted the iso using daemon tools..

n i was checking out the net and came across a thread tht says that, grub can b installed on windows and then you can mount an image instead of booting into windows or sth like that....so can anyone help me with this problem of myne?

thanks in advance...

---

### Post by logos34 on 2008-05-19
Try this method:
[https://wiki.ubuntu.com/Installation/FromWindows](https://wiki.ubuntu.com/Installation/FromWindows)
(-->'CD image approach')

Haven't tried it with ubuntustudio so not sure if it will work.

How old is this pc (system specs)? Might want to take a look [here]("https://help.ubuntu.com/community/Installation/LowMemorySystems").
Ubuntustudio uses gnome desktop, which might be a prob depending on how much ram you have

---

### Post by saidinesh5 on 2008-05-19
thx dude i will b checking your post...
well its a HCL PC,
it had 256MB RAM , i ve upgraded it to 1Gig abt a week ago,
it uses AMD Athlon 64,2Ghz processor
n it has 40GB hard disk...

---

### Post by logos34 on 2008-05-19
> **saidinesh5 said:**
> i ve upgraded it to 1Gig abt a week ago,
it uses AMD Athlon 64,2Ghz processor
n it has 40GB hard disk...

jeez, you call that 'antique'?  No dvd and a small hard disk is a hindrance, but otherwise you'll be just fine--you could even run x64 ubuntustudio like me.

---

### Post by saidinesh5 on 2008-05-19
but sadly it dint work, i tried out that Automatic thing,n actually dis ubuntustudio is an alternate disk type iso, so it failed, n then i tried out the CD image approach, it initially kinda worked but then, it wasnt able to do the partition thing on my disks, so can you help me out again...it simply was unable to format and mount the root file system on my hard disk,it just says failed..n yes, the page u gave was quite interesting n thx for tht...

n the main reason i call this PC "antique" is that nothing works properly on this!it has gt a cd RW drive tht doesnt open once it closes..evry tyme i need to keep a cd in it or,use that hole method to open it! n its gt a floppy drive that doesnt work!(well i quit using floppies abt 5 yrs ago bt still need to point out rite!)... it runs damn slow..dont kno why but a 1GB file transfer frm 1 partition to the other takes about 22minutes!!n previously whn i had ubuntu(i ve gotten the cds from my friend),it was like a HELL for me..it has this ATI card i think thts wht causes the problem..every time i try switching on the desktop effects it goes into an infinite loop with the login screen..i cudnt even configure the internet on it..i have this static ip cable connection,n it was set properly but still the net wasnt working...i finally had to free up that 10 GB for my recording purposes(i wish i didnt do that.. cuz i dont evn have those cds available!), well it cudnt evn update frm the ubuntu cds!it says install the ubuntu cd even when its there!it seriously freaked me out!

so try solving as many problems as u can dude, i will b grateful..

---

### Post by saidinesh5 on 2008-05-19
n also,many ppl warned me against 64-bit editions, saying that the software support is really poor, wht do you say?

---

### Post by logos34 on 2008-05-19
> **saidinesh5 said:**
> n also,many ppl warned me against 64-bit editions, saying that the software support is really poor, wht do you say?

that's disinfo.  read the stickies over in the x64 forum
> 
i tried out the CD image approach, it initially kinda worked but then, it wasnt able to do the partition thing on my disks, so can you help me out again...it simply was unable to format and mount the root file system on my hard disk,it just says failed

then I guess then that leaves this method:

> like download ubuntu and den install ubuntu studio aver it

more here:
[https://help.ubuntu.com/community/UbuntuStudio/UpgradingFromHardy?highlight=%28UbuntuStudio%2FUpgradingFrom%29](https://help.ubuntu.com/community/UbuntuStudio/UpgradingFromHardy?highlight=%28UbuntuStudio%2FUpgradingFrom%29)
> 
well it cudnt evn update frm the ubuntu cds!it says install the ubuntu cd even when its there!it seriously freaked me out!

you can only upgrade from the alternate cd--live cd won't work.
[https://help.ubuntu.com/community/HardyUpgrades?highlight=%28upgrade%29#head-7311a7de9fdf1ca310c6937460c0a9d33f54279d](https://help.ubuntu.com/community/HardyUpgrades?highlight=%28upgrade%29#head-7311a7de9fdf1ca310c6937460c0a9d33f54279d)

> it runs damn slow..dont kno why but a 1GB file transfer frm 1 partition to the other takes about 22minutes!!

sounds like you're stuck in PIO mode or using an old 40-wire ide cable (vs. 80)

sudo hdparm -i -v /dev/hd? 

is the command you would use to check

I feel your pain about the cd drive--my tray is failing too, won't close properly and I think dvd-r burning is dying (can't burn at 16X like ai used too, only 4x). Too bad about your graphics and network

---

### Post by saidinesh5 on 2008-05-20
well thanks again dude,i have tried ubuntu 64bit 8.04 from its live cd...gt d cd frm ma friend, again the same old problems, infinite loop with the login screen until i chose to load fail safe gnome... and then networking , it gave me the same problem,evn after setting the ips...

"n i tried to update."
that thing in my previous post mean that i tried to install build-essential n other such stuff from that cd , but it says insert ubuntu cd...
n 1 more problem i faced d last tyme was i tried to set that option of automatic log in...n evn tried to change the login theme, but evn they dint seem to change...i mean 1ce i restart its the same old login screen tht used to cum up!n i chk the settings , they magically seem to be back to the defaults!

so i guess i m stuck wid dis "anti linux PC" for now!
thanks neways!

---

### Post by saidinesh5 on 2008-06-20
hey ....magically that networking problem solved itself....whn i ve installed ubuntu hardy amd64 version.......and still that infinite loop problem persisted........ but that problem was solved when i have tried to get into ubuntu in fail safe mode and installed the graphics card drivers........apparently tht was what causing the problem....i hav an ATI Radeon graphics card and whn i ve installed drivers, the performance has increased a lott..thnx neways

---

