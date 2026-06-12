---
title: "help!! im a nwebie and dont know much"
date: 2006-10-03
forum: Installation &amp; Upgrades
---

### Post by kickenchicken on 2006-10-03
well i wanted to install linux as windows is getting me irrated. so i try to install time.language etc. etc. but then something comes up about which parition to install it on. i want to install it on my D partition as well i have windows on C:\. anyways i go to the menu and something about reforamtting or making space on IDE1. i chose manual. then something comes up with all ,y paritions i highlight D:\ which is known as HD5 and i also have a logical partition from D thats HD6. i highlight HD5 choose next and this comes up. Select which partitions you want to use for your new installation, and where you want to mount each of them.

You must mount one partition on the root file system ("/"), and you must choose at least one partition for use as swap space.  i dont understand but three selections are there /media/hda1  Parition 1 IDE/ATA1 (primary)[hd1]
then /media/hda5 partition 5 disc IDE/ATA 1 (logical)[hd5]
then /media/hda6 Parition 6 disc IDE/ATA 1 (logical)[hd6]
i have no clue what to do someone help me!!  i want member linux on the D(hd5) and i have windows on HD1 and another parition with 325 mb HD6 what do i do?  thanks

---

### Post by jISh on 2006-10-03
You need to make a partition that's, as a general rule, the size of your RAM. Set the type to linux-swap and choose that as your swap partition.

---

### Post by kickenchicken on 2006-10-03
ok so i make my 326 mb parition a swap parition by formattin it as choosing it as the swap one. then HD5 which is where i want to isntall linux what file system does it have to be? i have it  currently as EXT2 and the 326 mb one is now linux-swap. i dont know but im loving this os as im using it off the cd. its awesome.

---

### Post by randell6564 on 2006-10-03
> **kickenchicken said:**
> well i wanted to install linux as windows is getting me irrated. so i try to install time.language etc. etc. but then something comes up about which parition to install it on. i want to install it on my D partition as well i have windows on C:\. anyways i go to the menu and something about reforamtting or making space on IDE1. i chose manual. then something comes up with all ,y paritions i highlight D:\ which is known as HD5 and i also have a logical partition from D thats HD6. i highlight HD5 choose next and this comes up. Select which partitions you want to use for your new installation, and where you want to mount each of them.

You must mount one partition on the root file system ("/"), and you must choose at least one partition for use as swap space.  i dont understand but three selections are there /media/hda1  Parition 1 IDE/ATA1 (primary)[hd1]
then /media/hda5 partition 5 disc IDE/ATA 1 (logical)[hd5]
then /media/hda6 Parition 6 disc IDE/ATA 1 (logical)[hd6]
i have no clue what to do someone help me!!  i want member linux on the D(hd5) and i have windows on HD1 and another parition with 325 mb HD6 what do i do?  thanks

Hi!  Don't use the manual partitioning!  Ubuntu sees two partitions, so just tell her to "use available free space".

If you are installing on the same HD that houses Windows, then Windows will most likely be hda1 and your free partition will be hda2, so tell Ubuntu to use hda2.

If you are new to Linux then this would be the easiet way to go.

---

### Post by kickenchicken on 2006-10-03
alright i got it installed just fine on my D parition. ok now uhh how do i install my sound card as when i click on the sound icon on the toolbar this thing says: "No volume control GStreamer plugins and/or devices found." uhh dont really nknow what to do. so thanks for the help now just tp get my soud card working lol. oh yah some one told me  i can use the programs of my windows parition but wheni tried running them i got this error: "Could not open recently used document "file:///media/hda1/Program%20Files/PeerGuardian2/pg2.exe"

Details: Could not find a suitable application."

---

### Post by randell6564 on 2006-10-03
> **kickenchicken said:**
> alright i got it installed just fine on my D parition. ok now uhh how do i install my sound card as when i click on the sound icon on the toolbar this thing says: "No volume control GStreamer plugins and/or devices found." uhh dont really nknow what to do. so thanks for the help now just tp get my soud card working lol. oh yah some one told me  i can use the programs of my windows parition but wheni tried running them i got this error: "Could not open recently used document "file:///media/hda1/Program%20Files/PeerGuardian2/pg2.exe"

Details: Could not find a suitable application."

Have you enabled all your repo's in /etc/apt/sources.list?

---

### Post by kickenchicken on 2006-10-03
????? memebr im a newb i have no idea what /etc/apt/sources.list is. what is it? sorry ive NEVER used this os in my life.

---

### Post by randell6564 on 2006-10-04
> **kickenchicken said:**
> ????? memebr im a newb i have no idea what /etc/apt/sources.list is. what is it? sorry ive NEVER used this os in my life.

Sorry!  Open a terminal and type **sudo gedit /etc/apt/sources.list**

This will pull up your list of repositories. Please copy and paste it here!

Though I'm not too sure of what exactly you mean when you say, "when i click on the sound icon on toolbar...".  Do you mean the Volume Control?  BUT, the part about "Gstreamer plugins" leads me to think that you need to install 'Gstreamer"!

---

### Post by kickenchicken on 2006-10-04
this  ALSA lib confmisc.c:672:(snd_func_card_driver) cannot find card '0'
ALSA lib conf.c:3493:(_snd_config_evaluate) function snd_func_card_driver returned error: No such device
ALSA lib confmisc.c:392:(snd_func_concat) error evaluating strings
ALSA lib conf.c:3493:(_snd_config_evaluate) function snd_func_concat returned error: No such device
ALSA lib confmisc.c:1072:(snd_func_refer) error evaluating name
ALSA lib conf.c:3493:(_snd_config_evaluate) function snd_func_refer returned error: No such device
ALSA lib conf.c:3962:(snd_config_expand) Evaluate error: No such device
ALSA lib pcm.c:2102:(snd_pcm_open_noupdate) Unknown PCM default


 or this?  



deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper universe
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe

it said something like something inizialzed.

---

### Post by randell6564 on 2006-10-04
> **kickenchicken said:**
> t

or this?  
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper universe
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe


This is exactly what I wanted to see! Good Job!  This is your /etc/apt/sources.list
See the Pound Signs (#) at the beginning of each address starting with "deb"?  That # prevents you from retrieving anything from that particular site.  So.,delete it!  Delete the # and then do a **sudo apt-get update**.

Log out and then login again and tell me if you get any update notice.

---

### Post by kickenchicken on 2006-10-04
so i delete the ones with the deb's witht the # sign?

---

### Post by randell6564 on 2006-10-04
> **kickenchicken said:**
> so i delete the ones with the deb's witht the # sign?
Yes, but ONLY delete the #!  Then save your list, close it and do a **sudo apt-get update**

---

### Post by kickenchicken on 2006-10-04
yah i got two updates uhh libtag1c2a and some other one.

---

### Post by kickenchicken on 2006-10-04
now what? 
      thanks

---

### Post by randell6564 on 2006-10-04
> **kickenchicken said:**
> yah i got two updates uhh libtag1c2a and some other one.

Go to **System>Administration>Synaptic Package Manager**, and click on '**Search**'.  type in **gstreamer** and hit **Enter**.

I'm not by ANY means a pro at this, but since Gstreamer was mentioned, I would install anything Gstreamer!

---

### Post by kickenchicken on 2006-10-05
uhh nothing works anymore. i dont know if i cant install my sound card philips psc705 i might aswell unintstall linux.

---

