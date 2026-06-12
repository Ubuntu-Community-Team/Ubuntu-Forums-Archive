---
title: "universal usb installer?"
date: 2011-08-29
forum: Installation &amp; Upgrades
---

### Post by Matrix01 on 2011-08-29
Has anyone downloaded universal usb installer?

they said that usb installer is persistent, remembers settings and installed program...

---

### Post by Hakunka-Matata on 2011-08-29
no, but the current unetbootin program also gives the option to create a persistence liveCD.

---

### Post by Matrix01 on 2011-08-29
really?  my unetbootin, installed months ago, does not save any changes which I made in settings.

have u downloaded new unetbootin?

> **Hakunka-Matata said:**
> no, but the current unetbootin program also gives the option to create a persistence liveCD.

---

### Post by Hakunka-Matata on 2011-08-29
yes, there's a new version -549, use the link in my signature if you want to download it.

**Edit:  **Hey, that's funny.  The name now contains Universal also - is it what you were talking about to start with maybe?
**Your [UNetbootin, Universal Netboot Installer]("http://sourceforge.net/projects/unetbootin/")**

---

### Post by Matrix01 on 2011-09-03
i downloaded unetbootin, and 
click installation,
usb drive did not show up...
4 partitions from hard disk showed up..??
i formatted usb drive in FAT 32.

[ATTACH]201369[/ATTACH]

---

### Post by Hakunka-Matata on 2011-09-03
> **Matrix01 said:**
> i downloaded unetbootin, and 
click installation,
usb drive did not show up...
4 partitions from hard disk showed up..??
i formatted usb drive in FAT 32.

[ATTACH]201369[/ATTACH]

**EDIT: ** Sorry, think I missed your point.  The Pendrive 973  MB partition is the USB flash drive you have inserted.  FAT32

You booted into Ubuntu LiveCD?
And it worked, so you clicked on install ubuntu?

more detail please.
and post the output of ```
sudo fdisk -lu
``` please

OH YEAH, your drive has four primary partitions already, so there's some work to be done with the windows Diskmanager program.

---

### Post by Matrix01 on 2011-09-03
after unetbootin is installed in usb stick, can u install ubuntu in usb stick?

---

### Post by e79 on 2011-09-03
> **Matrix01 said:**
> Has anyone downloaded universal usb installer?

they said that usb installer is persistent, remembers settings and installed program...

Yes it should work without problem, used it many time for tests. Universal USB Installer and UNetbootin are meant to create a bootable Linux/Windows and you can add persistence with both. Make sure you select your USB and not your internal hard drive :P

---

### Post by Matrix01 on 2011-09-03
I selected english, time zone, keyboard.....

c hard drive showed up, but USB drive did not show up????
here's snap shot 

and it's ubuntu 10.04...
do u have 11.04?

[ATTACH]201381[/ATTACH]

---

### Post by Hakunka-Matata on 2011-09-03
OK, good you've got a good LiveCD/USB and you've started to install Ubuntu:

[LIST]
[*]Your Hard drive does not have any room availabe to make the  partitions necessary for the Ubuntu installation.  No problem, you'll  just have to do some work on the drive partitioning.
[/LIST]
I suggest you reboot into windows, using Windows disk management tools you'll have to shrink the windows partition and create some free space.   Better back up anything important before you start playing with the partitions.

---

### Post by Matrix01 on 2011-09-03
unetbootin does not have ubuntu 11.04.

---

### Post by e79 on 2011-09-05
Are you sure you have the latest Unetbootin version ? If not, remove the one you have, add the PPA repositories, update your system and reinstall it, then you should be able to create a LiveUSB with 11.04 as shown in the screenshot.

Add the PPA from:
[https://launchpad.net/~gezakovacs/+archive/ppa]("https://launchpad.net/%7Egezakovacs/+archive/ppa")

Then:
```
sudo apt-get update && sudo apt-get install unetbootin
```

Hope this helps

---

### Post by Matrix01 on 2011-09-05
I have downloaded unetbootin from this website:

[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

and installation started like this:

[ATTACH]201542[/ATTACH]

---

### Post by Matrix01 on 2011-09-05
i visited website:
[https://launchpad.net/~gezakovacs/+archive/ppa](https://launchpad.net/~gezakovacs/+archive/ppa)

will you tell me how to use code?


> **e79 said:**
> Are you sure you have the latest Unetbootin version ? If not, remove the one you have, add the PPA repositories, update your system and reinstall it, then you should be able to create a LiveUSB with 11.04 as shown in the screenshot.

Add the PPA from:
[https://launchpad.net/~gezakovacs/+archive/ppa]("https://launchpad.net/%7Egezakovacs/+archive/ppa")

Then:
```
sudo apt-get update && sudo apt-get install unetbootin
```

Hope this helps

---

### Post by Hakunka-Matata on 2011-09-05
If it's persistence as part of unetbootin that you want to know about:  

[LIST]
[*] Near the bottom of unetbootin's gui, there is an area to allocate space for a persistence build.
[*]I've entered 7,000 MB as an example.
[/LIST]
Please tell us what you are trying to do. 

[LIST]
[*]Are you using a Windows, or Linux/Ubuntu computer now?
[*]I think you want to install Ubuntu, where?,
[LIST]
[*]to a Windows machine? A Wubi install?
[*]separate Linux partition on your hard drive?
[/LIST]
 
[/LIST]
>  will you tell me how to use code?```
sudo apt-get update && sudo apt-get install unetbootin
```

If that's the *code *you are asking about, you enter that code in a Terminal on a Linux/Ubuntu machine.
It will fetch and install unetbootin.  You've already downloaded and installed unetbootin, haven't you?

---

### Post by e79 on 2011-09-05
Well if you installed it straight from the website (the latest version I presume) , can't you just scroll down the box where it say 10.04_Live and choose 11.04_Live ?

BTW the PPA repositories are meant to keep UNetbootin updated at its latest version. To add this PPA to your Ubuntu configuration, simply do these steps :

1. Open the Ubuntu Software Center
2. Go to the Menu called 'Edit' and then 'Software Sources'
3. Now go to the 'Other Softwares' tab 
4. Click on 'Add'
5. Now, depending on which Ubuntu version you have at the moment (installed on your PC), copy/paste the following :

For Ubuntu 10.04 : 
```
deb [http://ppa.launchpad.net/gezakovacs/ppa/ubuntu](http://ppa.launchpad.net/gezakovacs/ppa/ubuntu) lucid main
```

For Ubuntu 10.10 : 
```
deb [http://ppa.launchpad.net/gezakovacs/ppa/ubuntu](http://ppa.launchpad.net/gezakovacs/ppa/ubuntu) maverick main
```

For Ubuntu 11.04 : 
```
deb [http://ppa.launchpad.net/gezakovacs/ppa/ubuntu](http://ppa.launchpad.net/gezakovacs/ppa/ubuntu) natty main
```

The result should appear like on the screen shot attached.

Now every time the developers pushes a new version of Unetbootin, you would get it in your softwares updates :

```
sudo apt-get update && sudo apt-get dist-upgrade
```

Hope this helps

---

### Post by Matrix01 on 2011-09-06
my fault...
i did not know that i can scroll down and choose version from drop down menu.

I'm not sure which 11.04 i download from many.

Is 11.04_live the one i want to download?

[ATTACH]201639[/ATTACH]

---

### Post by Hakunka-Matata on 2011-09-06
[http://mirror.yellowfiber.net/ubuntu/](http://mirror.yellowfiber.net/ubuntu/)

Download any ubuntu you want from there, using a torrent file works fastest.

---

### Post by Matrix01 on 2011-09-08
Is 11.10 the latest version?

---

### Post by Hakunka-Matata on 2011-09-08
11.10 beta1, so no, i would not choose that one. 10.10 (stable) is a good one. 
11.10 is in beta now, due to be released some time soon, couple of months?, I don't recall.
 When you want to give 11.10 a try, make another / (root) partition of maybe 15GB, and install 11.10 to it.
 Evey time you boot up you can choose whether you want to play, or get stuff done.

---

### Post by Matrix01 on 2011-09-09
I am on netbook, HP mini which has no CD drive.

Can this 'ubuntu-11.04-alternate-i386.iso.torrent' be installled in USB pendrive?

---

### Post by Matrix01 on 2011-09-18
I am on HP mini net book, and 

I do not know which versions of 11.04 I get.

11.04 netinstall, 11.04 HD media, or 11.04 live?

32 0r 64

[ATTACH]202442[/ATTACH]

---

### Post by Matrix01 on 2011-09-18
Hello,
I choosed 11.04 Netinstall from unetbootin.
and
booted from USB.
In installation process, selected language and keyboard,
and
network configuration failed.
message goes like this "not using DHCP protocol...alternatively network hardware not working."

do you know how to fix this?


> **e79 said:**
> Well if you installed it straight from the website (the latest version I presume) , can't you just scroll down the box where it say 10.04_Live and choose 11.04_Live ?

BTW the PPA repositories are meant to keep UNetbootin updated at its latest version. To add this PPA to your Ubuntu configuration, simply do these steps :

1. Open the Ubuntu Software Center
2. Go to the Menu called 'Edit' and then 'Software Sources'
3. Now go to the 'Other Softwares' tab 
4. Click on 'Add'
5. Now, depending on which Ubuntu version you have at the moment (installed on your PC), copy/paste the following :

For Ubuntu 10.04 : 
```
deb [http://ppa.launchpad.net/gezakovacs/ppa/ubuntu](http://ppa.launchpad.net/gezakovacs/ppa/ubuntu) lucid main
```

For Ubuntu 10.10 : 
```
deb [http://ppa.launchpad.net/gezakovacs/ppa/ubuntu](http://ppa.launchpad.net/gezakovacs/ppa/ubuntu) maverick main
```

For Ubuntu 11.04 : 
```
deb [http://ppa.launchpad.net/gezakovacs/ppa/ubuntu](http://ppa.launchpad.net/gezakovacs/ppa/ubuntu) natty main
```

The result should appear like on the screen shot attached.

Now every time the developers pushes a new version of Unetbootin, you would get it in your softwares updates :

```
sudo apt-get update && sudo apt-get dist-upgrade
```

Hope this helps

---

### Post by Hakunka-Matata on 2011-09-18
Download the correct .iso from [http://mirror.yellowfiber.net/ubuntu/11.04/](http://mirror.yellowfiber.net/ubuntu/11.04/).  I would choose
[ubuntu-11.04-desktop-i386.iso]("http://mirror.yellowfiber.net/ubuntu/11.04/ubuntu-11.04-desktop-i386.iso")  You do not want the netinstall .iso.  It's faster and easier to download your .iso file to your hard drive, then when you start unetbootin, tick the "**Disk_i_mage"** box, and then click on the right hand side in the box with 4 .... dots in it, to point to the directory (Where you saved the downloaded 1104.iso, usually Downloads/) and .iso file you want to use to load the USB stick with.

---

### Post by Matrix01 on 2011-09-22
I downloaded ubuntu-11.04-desktop-i386.iso in hard drive,
 
started unetbootin, downloading took for a while.
and
booted from USB srick,

so
how can i make persistent Ubuntu in USB stick?

---

### Post by Hakunka-Matata on 2011-09-22
[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

or download the latest UNetbootin, it has a persistence option.  You'll want an 8GB flashdirve, minimum.

---

### Post by Matrix01 on 2011-09-22
I downloaded unetbootin from this.
Is this the latest one that can make persistent USB?

[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

---

### Post by Hakunka-Matata on 2011-09-22
Yes, that's the place, the latest version is 555, right?  You have to mark it executable in order to run it.

---

### Post by Matrix01 on 2011-09-22
my bad..
i had unetbootin 549....
have to download 555.

[ATTACH]202748[/ATTACH]

---

### Post by Matrix01 on 2011-09-24
does unetbootin need to be downloaded in USB drive or in hard drive?

---

### Post by Hakunka-Matata on 2011-09-24
download unetbootin to your HDD, 
right click on the file
click on **properties**
click on **permissions** tab
tick box that says, [B]allow executing file as program.
[/B]
After all that, double click the unetbootin icon again, and it will start the program that will create your live installation flash drive.

---

### Post by Matrix01 on 2011-09-24
where does this; ubuntu-11.04-desktop-i386.iso, need to be downloaded?

---

### Post by Hakunka-Matata on 2011-09-24
download your ubuntu iso anywhere convenient, usually to the Downloads folder.  You'll have to know the location so you can browse to it when using unetbootin to build your flash drive.  Rather than letting unetbootin download an iso for you (too slow), you download it first, and then simply point unetbootin to it.

---

### Post by Matrix01 on 2011-09-24
which file system does usb drive need to be?

[ATTACH]202884[/ATTACH]

---

### Post by Matrix01 on 2011-09-25
how to download unetbootin in hard disk drive?

[ATTACH]202885[/ATTACH]

---

### Post by Matrix01 on 2011-09-25
im on win7 starter.


> **Hakunka-Matata said:**
> download unetbootin to your HDD, 
right click on the file
click on **properties**
click on **permissions** tab
tick box that says, [B]allow executing file as program.
[/B]
After all that, double click the unetbootin icon again, and it will start the program that will create your live installation flash drive.

---

### Post by Hakunka-Matata on 2011-09-25
sorry, I don't use win7, cannot help, someone else will help out.

---

### Post by Matrix01 on 2011-09-25
amazingly, 
there're many methods or applications that will install ubuntu in usb drive:

virtual clone drive, 7zip, Plopbootmanager, Grub4dos, unetbootin, or install ubuntu directly in usb or external source.

any comment or voice on each of them?
I am not sure which one to pick.

[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

---

### Post by Hakunka-Matata on 2011-09-25
unetbootin always works for me.

---

### Post by Matrix01 on 2011-09-26
well,
i downloaded iso file,
and attached iso file in unetbootin,
did not work.

[ATTACH]202951[/ATTACH]

---

### Post by Hakunka-Matata on 2011-09-26
"it didn't work"
Can you say more about how or why or what didn't work?

---

### Post by Matrix01 on 2011-09-27
ran unetbootin with iso file,
and
when installation completed,
rebooted netbook,
there's window7
i did not see ubuntu.

I guess,
my web browser have to be run as administrator...
i am new to win7,

---

### Post by Hakunka-Matata on 2011-09-27
and you have the netbook BIOS set to boot from usb first?

---

### Post by Matrix01 on 2011-09-28
i checked boot order.
usb drive is the first one.


> **Hakunka-Matata said:**
> and you have the netbook BIOS set to boot from usb first?

---

### Post by Matrix01 on 2011-10-02
do i need to enter any number in box where; 'space used to preserve................'?
[ATTACH]203379[/ATTACH]

---

### Post by Matrix01 on 2011-10-16
I downloaded unetbootin 555, and iso file; ubuntu-11.04-desktop-i386.iso,

and installed ubuntu 11.04 in 8G HP USB Flash drive.

booted 11.04 from USB flash drive, select set ups,
now,
how do i make 11.04 persistent in USB flash drive?

---

### Post by Hakunka-Matata on 2011-10-16
> **Matrix01 said:**
> do i need to enter any number in box where; 'space used to preserve................'?
[ATTACH]203379[/ATTACH]

Yes, that's where you allocate the space for persistence....

---

### Post by Matrix01 on 2011-10-16
In installation process, I saw 4 partitions in HDD,
but
I did not see USB drive persistant option or any.
How do I make persistent ubuntu in USB flash drive?

---

### Post by Hakunka-Matata on 2011-10-16
> **Matrix01 said:**
> In installation process, I saw 4 partitions in HDD,
but
I did not see USB drive persistant option or any.
How do I make persistent ubuntu in USB flash drive?

When preparing the USB drive in Unetbootin, you have to allocate space for **preserving files across reboots (ubuntu only).  **You posted the picture a couple of posts ago.  You have to do it before you start installing the .iso to the USB drive.

---

### Post by Matrix01 on 2011-10-16
I think i know what you are talking aobut now...I saw that ubuntu only....
well..
i have to go back to unetbootin.

what number do i need in box?


> **Hakunka-Matata said:**
> When preparing the USB drive in Unetbootin, you have to allocate space for **preserving files across reboots (ubuntu only).  **You posted the picture a couple of posts ago.  You have to do it before you start installing the .iso to the USB drive.

---

### Post by Hakunka-Matata on 2011-10-16
I'm told 8GiB is a minimum of sorts.  Mind you, I'm a novice with persistent live drives.

---

### Post by Matrix01 on 2011-10-16
does ubuntu get installed in this space?

On unetbootin, unit is MB,
8GB is 8192MB.

[ATTACH]204583[/ATTACH]

---

### Post by Hakunka-Matata on 2011-10-16
[http://www.google.com/#sclient=psy-ab&hl=en&source=hp&q=unetbootin%20persistent%20ubuntu&pbx=1&oq=unetbootin%20per&aq=2&aqi=g3g-m1&aql=1&gs_sm=sc&gs_upl=0l0l1l3102l0l0l0l0l0l0l0l0ll0l0&bav=on.2,or.r_gc.r_pw.,cf.osb&fp=bd638b897581bb57&biw=1022&bih=753&pf=p&pdl=300](http://www.google.com/#sclient=psy-ab&hl=en&source=hp&q=unetbootin%20persistent%20ubuntu&pbx=1&oq=unetbootin%20per&aq=2&aqi=g3g-m1&aql=1&gs_sm=sc&gs_upl=0l0l1l3102l0l0l0l0l0l0l0l0ll0l0&bav=on.2,or.r_gc.r_pw.,cf.osb&fp=bd638b897581bb57&biw=1022&bih=753&pf=p&pdl=300)

---

### Post by Matrix01 on 2011-10-19
thank you for helping me out.
finally,
persistent 11.04 is installed in USB stick.

by the way,
network icon disappeared, it was on top left when I booted 11.04 after installation.
do i need to reinstall 11.04?   


> **Hakunka-Matata said:**
> [http://www.google.com/#sclient=psy-ab&hl=en&source=hp&q=unetbootin%20persistent%20ubuntu&pbx=1&oq=unetbootin%20per&aq=2&aqi=g3g-m1&aql=1&gs_sm=sc&gs_upl=0l0l1l3102l0l0l0l0l0l0l0l0ll0l0&bav=on.2,or.r_gc.r_pw.,cf.osb&fp=bd638b897581bb57&biw=1022&bih=753&pf=p&pdl=300](http://www.google.com/#sclient=psy-ab&hl=en&source=hp&q=unetbootin%20persistent%20ubuntu&pbx=1&oq=unetbootin%20per&aq=2&aqi=g3g-m1&aql=1&gs_sm=sc&gs_upl=0l0l1l3102l0l0l0l0l0l0l0l0ll0l0&bav=on.2,or.r_gc.r_pw.,cf.osb&fp=bd638b897581bb57&biw=1022&bih=753&pf=p&pdl=300)

---

### Post by Hakunka-Matata on 2011-10-19
OK Matrix01, glad to hear you have it going.  Now you can reload your USB stick with whatever .iso you want to try out, doesn't take long to download and install to USB, easy way to test other distros.

---

