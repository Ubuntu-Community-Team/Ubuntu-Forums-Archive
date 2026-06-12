---
title: "I can't update kernel, I can't update from 12.04. either to 12.10 or above"
date: 2015-03-10
forum: Installation &amp; Upgrades
---

### Post by Maximilian_Muneyos on 2015-03-10
Hello,

I am a OS and Windows user who once had a linux-run machine many years ago in a partiton and decided to give it a try again. It is a very basic dell inspiron used for trivial tasks that came with Ubuntu 12.04. It is a somewhat old version I see now.

I set up the computer yesterday and it had tons of things to update, including the version 14.04. Because it would take hours to upgrade, according to what the computer said, I decided to leave the update to 14.04 for today. It doesn't appear anymore, only the 12.10 after changing the update options to show any update. But this, too, doesn't download (
Fetching the upgrade failed. There may be a network problem)

I tried to update "Firmware for Linux kernel drivers" but I have encountered many errors, including but not limited to "installArchives() failed: dpkg: error: cannot read info directory: No such file or directory Error in function:"  

It didn't work and I've found some information that it wouldn't. I think such kernel updates have been stopped starting in july, 2014. So I decided to upgrade to 14.04, however, regardless of how I try, either thru update-manager on command or thru "updates available" I can't. I have a cd with the version 14.04 LTS i386, but inserting it and expecting it to run by itself doesn't work.

I've had thousands of problems with Windows since the 3.11 version but having them from the start is very frustrating. I would appreciate any help to solve this problem. I don't mind losing everything and starting over, this computer has nothing on it. The easier the better.

Sorry about posting trivial stuff

---

### Post by Bashing-om on 2015-03-10
Maximilian_Muneyos; Hello;

If it is a fret and a worry:
> 
Sorry about posting trivial stuff

It is not a trivial matter.

Help is what we do.
OK, let's get to the bottom of this, ya want to learn ?
1st up is what are we dealing with release wise ?
Post back the outputs - Between Code Tags - of terminal commands:
```

lsb_release -a
cat /etc/issue
cat /etc/update-manager/release-upgrades

```
code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)

Release 12.04 is a  (L)ong (T)erm (S)upport release, and is supported 'till April 2017.
If it turns out that it is release 12.10 installed, it is END-Of-Life, and has no support - the software repository has been turned away; We will have to jump a hoop or so to get ya release-upgraded. That is a long hard bumpy road to get you current 12.10 ->13.04 -> 13.10 -> 14.04.
A lot of time effort and bandwidth to do the release upgrades; much faster and less fraught of error to do a clean fresh install of 14.04. The choice is yours.

[INDENT][INDENT]ain't nothing but a thing
[/INDENT][/INDENT]

---

### Post by Maximilian_Muneyos on 2015-03-10
Hello,

thank you for your help. The first line returned this:

```

No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 12.04.5 LTS
Release:	12.04
Codename:	precise

```


then this:
```

Ubuntu 12.04.5 LTS \n \l
```

and at last:

```
[DEFAULT]
# Default behavior for the release upgrader.

[DEFAULT]
# Default prompting behavior, valid options:
#
#  never  - Never check for a new release.
#  normal - Check to see if a new release is available.  If more than one new
#           release is found, the release upgrader will attempt to upgrade to
#           the release that immediately succeeds the currently-running
#           release.
#  lts    - Check to see if a new LTS release is available.  The upgrader
#           will attempt to upgrade to the first LTS release available after
#           the currently-running one.  Note that this option should not be
#           used if the currently-running release is not itself an LTS
#           release, since in that case the upgrader won't be able to
#           determine if a newer release is available.
prompt=normal

```

---

### Post by Bashing-om on 2015-03-10
Maximilian_Muneyos; Great !

As you can see you are in good shape.
Release 12.04 is installed and as advised has support 'till 2017.
At this time, clarify what you want to do,
Update this install of 12.04, or upgrade to 14.04/14.10 ( 14.10 is an interim release and only supported for 9 months) .
No matter the path you choose, we need to make sure that your source(s) are valid:
Here is what caused your upgrade issue:
> 
prompt=normal
 which in essence says to release upgrade to the next release (12.10) but 12.10 is EOL and has no repository available - the update manager goes spastic on you. - In this instance what you want is that prompt set to " prompt=lts "
Settable by either a direct edit of the file, or from the check box in Software Sources .
post back the output:
```

cat -n /etc/apt/sources.list
tail -v -n +1 /etc/apt/sources.list.d/*

```
Getting ready, set, go (?)
Depending on what you want to do is what we do.

[INDENT][INDENT]ain't no step for a stepper
[/INDENT][/INDENT]

---

### Post by deadflowr on 2015-03-10
I would also recommend posting the output for
```
uname -r
```
please.
Ubuntu 12.04 still has updates for the 3.2, and 3.13 kernels series, but not for the 3.5, 3.8, or 3.11 series.

---

### Post by Maximilian_Muneyos on 2015-03-10
Thank you again !

I would like to upgrade it to 14.04 if possible. Do you have an idea of how long it would take ?

First line:

```

 1    deb cdrom:[Ubuntu 14.04.1 LTS _Trusty Tahr_ - Release i386 (20140722.2)]/ dists/trusty/restricted/binary-i386/
     2    deb cdrom:[Ubuntu 14.04.1 LTS _Trusty Tahr_ - Release i386 (20140722.2)]/ dists/trusty/restricted/binary-i386/
     3    deb cdrom:[Ubuntu 14.04.1 LTS _Trusty Tahr_ - Release i386 (20140722.2)]/ dists/trusty/restricted/binary-i386/
     4    deb cdrom:[Ubuntu 14.04.1 LTS _Trusty Tahr_ - Release i386 (20140722.2)]/ dists/trusty/restricted/binary-i386/
     5    deb cdrom:[Ubuntu 12.04 _Precise_ - Build amd64 LIVE Binary 20130203-13:50]/ precise main
     6    
     7    # See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
     8    # newer versions of the distribution.
     9    deb http://br.archive.ubuntu.com/ubuntu/ precise main restricted
    10    deb-src http://br.archive.ubuntu.com/ubuntu/ precise main restricted
    11    
    12    ## Major bug fix updates produced after the final release of the
    13    ## distribution.
    14    deb http://br.archive.ubuntu.com/ubuntu/ precise-updates main restricted
    15    deb-src http://br.archive.ubuntu.com/ubuntu/ precise-updates main restricted
    16    
    17    ## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
    18    ## team. Also, please note that software in universe WILL NOT receive any
    19    ## review or updates from the Ubuntu security team.
    20    deb http://br.archive.ubuntu.com/ubuntu/ precise universe
    21    deb-src http://br.archive.ubuntu.com/ubuntu/ precise universe
    22    deb http://br.archive.ubuntu.com/ubuntu/ precise-updates universe
    23    deb-src http://br.archive.ubuntu.com/ubuntu/ precise-updates universe
    24    
    25    ## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
    26    ## team, and may not be under a free licence. Please satisfy yourself as to 
    27    ## your rights to use the software. Also, please note that software in 
    28    ## multiverse WILL NOT receive any review or updates from the Ubuntu
    29    ## security team.
    30    deb http://br.archive.ubuntu.com/ubuntu/ precise multiverse
    31    deb-src http://br.archive.ubuntu.com/ubuntu/ precise multiverse
    32    deb http://br.archive.ubuntu.com/ubuntu/ precise-updates multiverse
    33    deb-src http://br.archive.ubuntu.com/ubuntu/ precise-updates multiverse
    34    
    35    ## N.B. software from this repository may not have been tested as
    36    ## extensively as that contained in the main release, although it includes
    37    ## newer versions of some applications which may provide useful features.
    38    ## Also, please note that software in backports WILL NOT receive any review
    39    ## or updates from the Ubuntu security team.
    40    deb http://br.archive.ubuntu.com/ubuntu/ precise-backports main restricted universe multiverse
    41    deb-src http://br.archive.ubuntu.com/ubuntu/ precise-backports main restricted universe multiverse
    42    
    43    deb http://security.ubuntu.com/ubuntu precise-security main restricted
    44    deb-src http://security.ubuntu.com/ubuntu precise-security main restricted
    45    deb http://security.ubuntu.com/ubuntu precise-security universe
    46    deb-src http://security.ubuntu.com/ubuntu precise-security universe
    47    deb http://security.ubuntu.com/ubuntu precise-security multiverse
    48    deb-src http://security.ubuntu.com/ubuntu precise-security multiverse
    49    
    50    ## Uncomment the following two lines to add software from Canonical's
    51    ## 'partner' repository.
    52    ## This software is not part of Ubuntu, but is offered by Canonical and the
    53    ## respective vendors as a service to Ubuntu users.
    54    # deb http://archive.canonical.com/ubuntu precise partner
    55    # deb-src http://archive.canonical.com/ubuntu precise partner
    56    
    57    ## Uncomment the following two lines to add software from Ubuntu's
    58    ## 'extras' repository.
    59    ## This software is not part of Ubuntu, but is offered by third-party
    60    ## developers who want to ship their latest software.
    61    # deb http://extras.ubuntu.com/ubuntu precise main
    62    # deb-src http://extras.ubuntu.com/ubuntu precise main

```

then:

```

==> /etc/apt/sources.list.d/precise-dell.list <==
deb http://dell.archive.canonical.com/updates/ precise-dell public
deb-src http://dell.archive.canonical.com/updates/ precise-dell public

==> /etc/apt/sources.list.d/precise-dell.list.distUpgrade <==
deb http://dell.archive.canonical.com/updates/ precise-dell public
deb-src http://dell.archive.canonical.com/updates/ precise-dell public

==> /etc/apt/sources.list.d/precise-dell.list.save <==
deb http://dell.archive.canonical.com/updates/ precise-dell public
deb-src http://dell.archive.canonical.com/updates/ precise-dell public

==> /etc/apt/sources.list.d/precise-oem-sp1.list <==
deb http://oem.archive.canonical.com/updates/ precise-oem-sp1 public
deb-src http://oem.archive.canonical.com/updates/ precise-oem-sp1 public

==> /etc/apt/sources.list.d/precise-oem-sp1.list.distUpgrade <==
deb http://oem.archive.canonical.com/updates/ precise-oem-sp1 public
deb-src http://oem.archive.canonical.com/updates/ precise-oem-sp1 public

==> /etc/apt/sources.list.d/precise-oem-sp1.list.save <==
deb http://oem.archive.canonical.com/updates/ precise-oem-sp1 public
deb-src http://oem.archive.canonical.com/updates/ precise-oem-sp1 public

```

uname -r
```

3.5.0-59-generic

```

---

### Post by Bashing-om on 2015-03-10
Maximilian_Muneyos;

see deadflowr's last, yes ! would be instructive to know the kernel you are presently booting.

You have the 14.04 liveDVD(USB) on-hand per the sources.list output which I understand is a great way to release-upgrade, however I have never done so and can not directly advise on that method. The medium has been verified - check disk for defects OR md5sum, yes ?
deadflowr ??

In any event;
To proceed we want the CDrom check box UNchecked in Software Sources and as well in Software Sources change the update management from 'normal' to 'lts'. And to know what kernel you are presently booting .
 
I see no fault in your sources list files, I checked the PPAs and they are supported in 'trusty' ( no support in 14.10 for the PPAs) .

That now is a set ->
[INDENT][INDENT]getting ready to go
[/INDENT][/INDENT]

---

### Post by grahammechanical on 2015-03-10
If you changed Software Sources to notify you of any new version of Ubuntu, that will explain why you are being offered 12.10 which you cannot upgrade to, Not any more. At least not without complications such as 12.10 being end of life and the release following (13.04) being end of life also. As is 13.10.

So, I suggest that you reset Software Sources to only notify you of LTS releases. Then you should get an offer to upgrade to 14.04. You should not leave an upgrade unattended as you may be needed to give some user input. How long it will take will depend in part on the data transfer rate of your internet connection. How long does a fresh install take? The upgrade will not be quicker than a fresh install.

Regards.

---

### Post by Maximilian_Muneyos on 2015-03-11
Hello,

I seem to running in circles here. I checked only "Canonical-supported" and "Source code" under the tab Ubuntu software in Software sources. Under updates I have only the first two items ticked, that is, "Important security updates" and "Recommend updates".

The 14.04 option appeared again, I've clicked on it, it seems like it has updated but it starts all over again as if it hadn't updated anything. it says that "not all updates can be installed." my only option is partial upgrade that brings me nowhere. 

And I haven't found where I can change the update management from normal to lts.

Edit: upon trying to run:

```
sudo apt-get update
```

W: Duplicate sources.list entry [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) trusty-security/main amd64 Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_trusty-security_main_binary-amd64_Packages)
W: Duplicate sources.list entry [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) trusty-security/main i386 Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_trusty-security_main_binary-i386_Packages)
W: You may want to run apt-get update to correct these problems

and

```
sudo apt-get upgrade
```

Preconfiguring packages ...
dpkg: error: cannot read info directory: No such file or directory
E: Sub-process /usr/bin/dpkg returned an error code (2)



Sorry again.

---

### Post by yancek on 2015-03-11
> And I haven't found where I can change the update management from normal to lts.

The file was indicated in post#2 above.  Run the following and it should be there.  Make the change and save the file:

> sudo gedit /etc/update-manager/release-upgrades

---

### Post by Maximilian_Muneyos on 2015-03-11
I've done that already. but it still doesn't work.


```

# Default behavior for the release upgrader.

[DEFAULT]
# Default prompting behavior, valid options:
#
#  never  - Never check for a new release.
#  normal - Check to see if a new release is available.  If more than one new
#           release is found, the release upgrader will attempt to upgrade to
#           the release that immediately succeeds the currently-running
#           release.
#  lts    - Check to see if a new LTS release is available.  The upgrader
#           will attempt to upgrade to the first LTS release available after
#           the currently-running one.  Note that this option should not be
#           used if the currently-running release is not itself an LTS
#           release, since in that case the upgrader won't be able to
#           determine if a newer release is available.
prompt=lts

```

---

### Post by Bashing-om on 2015-03-11
Maximilian_Muneyos; Well, looks fair;

But, I fail to see the source of the duplication. maybe look at an updated sources.list(s) files .
```

cat -n /etc/apt/sources.list
tail -v -n +1 /etc/apt/sources.list.d/*

```
Still failing to see that duplication, next is to disable the 3rd party PPAs one by one, running 'sudo apt-get update' trying to isolate the problem source fetch, after each disablement..
Not a bad idea to leave all the 3rd party PPAs disabled until the release upgrade is completed to 14.04; then see about re-enabling them under the new upgrade.

Also make sure that there is no screensaver active when doing the upgrade <====

[INDENT]round pegs in round holes
[/INDENT]

---

### Post by Maximilian_Muneyos on 2015-03-12
Hello,

I got this. Maybe a problem occurred during update, I guess.

```

1    deb cdrom:[Ubuntu 14.04.1 LTS _Trusty Tahr_ - Release i386 (20140722.2)]/ dists/trusty/restricted/binary-i386/
     2    # deb cdrom:[Ubuntu 14.04.1 LTS _Trusty Tahr_ - Release i386 (20140722.2)]/ dists/trusty/restricted/binary-i386/
     3    # deb cdrom:[Ubuntu 14.04.1 LTS _Trusty Tahr_ - Release i386 (20140722.2)]/ dists/trusty/restricted/binary-i386/
     4    # deb cdrom:[Ubuntu 14.04.1 LTS _Trusty Tahr_ - Release i386 (20140722.2)]/ dists/trusty/restricted/binary-i386/
     5    # deb cdrom:[Ubuntu 14.04.1 LTS _Trusty Tahr_ - Release i386 (20140722.2)]/ dists/trusty/restricted/binary-i386/
     6    # deb cdrom:[Ubuntu 12.04 _Precise_ - Build amd64 LIVE Binary 20130203-13:50]/ precise main
     7    
     8    # See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
     9    # newer versions of the distribution.
    10    deb http://br.archive.ubuntu.com/ubuntu/ trusty main restricted
    11    
    12    ## Major bug fix updates produced after the final release of the
    13    ## distribution.
    14    deb http://br.archive.ubuntu.com/ubuntu/ trusty-updates main restricted
    15    
    16    ## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
    17    ## team. Also, please note that software in universe WILL NOT receive any
    18    ## review or updates from the Ubuntu security team.
    19    deb http://br.archive.ubuntu.com/ubuntu/ trusty universe
    20    deb http://br.archive.ubuntu.com/ubuntu/ trusty-updates universe
    21    
    22    ## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
    23    ## team, and may not be under a free licence. Please satisfy yourself as to 
    24    ## your rights to use the software. Also, please note that software in 
    25    ## multiverse WILL NOT receive any review or updates from the Ubuntu
    26    ## security team.
    27    deb http://br.archive.ubuntu.com/ubuntu/ trusty multiverse
    28    deb http://br.archive.ubuntu.com/ubuntu/ trusty-updates multiverse
    29    
    30    ## N.B. software from this repository may not have been tested as
    31    ## extensively as that contained in the main release, although it includes
    32    ## newer versions of some applications which may provide useful features.
    33    ## Also, please note that software in backports WILL NOT receive any review
    34    ## or updates from the Ubuntu security team.
    35    
    36    deb http://security.ubuntu.com/ubuntu trusty-security main restricted
    37    deb http://security.ubuntu.com/ubuntu trusty-security universe
    38    deb http://security.ubuntu.com/ubuntu trusty-security multiverse
    39    
    40    ## Uncomment the following two lines to add software from Canonical's
    41    ## 'partner' repository.
    42    ## This software is not part of Ubuntu, but is offered by Canonical and the
    43    ## respective vendors as a service to Ubuntu users.
    44    # deb http://archive.canonical.com/ubuntu precise partner
    45    # deb-src http://archive.canonical.com/ubuntu precise partner
    46    
    47    ## Uncomment the following two lines to add software from Ubuntu's
    48    ## 'extras' repository.
    49    ## This software is not part of Ubuntu, but is offered by third-party
    50    ## developers who want to ship their latest software.
    51    # deb http://extras.ubuntu.com/ubuntu precise main
    52    # deb-src http://extras.ubuntu.com/ubuntu precise main
    53    deb http://archive.ubuntu.com/ubuntu trusty main
    54    deb-src http://archive.ubuntu.com/ubuntu trusty main #Added by software-properties
    55    deb http://security.ubuntu.com/ubuntu/ trusty-security main
    56    deb http://archive.ubuntu.com/ubuntu trusty-updates main

```

```

==> /etc/apt/sources.list.d/precise-dell.list <==
# deb http://dell.archive.canonical.com/updates/ precise-dell public # disabled on upgrade to trusty
# deb-src http://dell.archive.canonical.com/updates/ precise-dell public # disabled on upgrade to trusty

==> /etc/apt/sources.list.d/precise-dell.list.distUpgrade <==
# deb http://dell.archive.canonical.com/updates/ precise-dell public # disabled on upgrade to trusty
# deb-src http://dell.archive.canonical.com/updates/ precise-dell public # disabled on upgrade to trusty

==> /etc/apt/sources.list.d/precise-dell.list.save <==
# deb http://dell.archive.canonical.com/updates/ precise-dell public # disabled on upgrade to trusty
# deb-src http://dell.archive.canonical.com/updates/ precise-dell public # disabled on upgrade to trusty

==> /etc/apt/sources.list.d/precise-oem-sp1.list <==
# deb http://oem.archive.canonical.com/updates/ precise-oem-sp1 public # disabled on upgrade to trusty
# deb-src http://oem.archive.canonical.com/updates/ precise-oem-sp1 public # disabled on upgrade to trusty

==> /etc/apt/sources.list.d/precise-oem-sp1.list.distUpgrade <==
# deb http://oem.archive.canonical.com/updates/ precise-oem-sp1 public # disabled on upgrade to trusty
# deb-src http://oem.archive.canonical.com/updates/ precise-oem-sp1 public # disabled on upgrade to trusty

==> /etc/apt/sources.list.d/precise-oem-sp1.list.save <==
# deb http://oem.archive.canonical.com/updates/ precise-oem-sp1 public # disabled on upgrade to trusty
# deb-src http://oem.archive.canonical.com/updates/ precise-oem-sp1 public # disabled on upgrade to trusty


```

Thank you for your patience

---

### Post by Bashing-om on 2015-03-12
Maximilian_Muneyos; Hey !

This time I do see it, where those dupes are:
> 
53    deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) trusty main
    54    deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) trusty main #Added by software-properties
    55    deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) trusty-security main
    56    deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) trusty-updates main

line 53 duplicates the fetch from line 10
line 54 is a "source" that you as a 'normal' user do not require
line 55 is a duplication of line 36
line 56  is a duplication of line 14

I do suggest making sure a backup of the current file does exist, and then remove lines 53, 54,55, and 56.

Then let's try again:
```

sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade

```
Then perhaps we are ready to do that release upgrade to 14.04 .

[INDENT][INDENT]Hey, it could happen now
[/INDENT][/INDENT]

---

### Post by Maximilian_Muneyos on 2015-03-12
Ok. And what is the best way to remove them ?

```
sed
``` would cut it ?

thank you.

---

### Post by Bashing-om on 2015-03-12
Maximilian_Muneyos; Hey;
In this instance:
> 
And what is the best way to remove them ?

I would do so with a file editor .
```

sudo cp /etc/apt/sources.list /etc/apt/sources.list-03mar2015
gksudo gedit /etc/apt/sources.list 

```
Remove those lines ( or comment them out - '#' character at the start of the line );
save the file and exit.
Now what results:
```

sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade

```

[INDENT][INDENT]another step forward
[/INDENT][/INDENT]

---

### Post by Maximilian_Muneyos on 2015-03-13
The first line apparently did nothing. Then I used the second and deleted the four lines that were duplicate. Yet it didn't work. 



Then I decided to create a new source file:

```

###### Ubuntu Main Repos
deb http://br.archive.ubuntu.com/ubuntu/ trusty main

###### Ubuntu Update Repos
deb http://br.archive.ubuntu.com/ubuntu/ trusty-security main
deb http://br.archive.ubuntu.com/ubuntu/ trusty-updates main

###### Ubuntu Partner Repo
deb http://archive.canonical.com/ubuntu trusty partner
deb-src http://archive.canonical.com/ubuntu trusty partner

```

Only the upgrade appeared as an option, but:

```

715 upgraded, 0 newly installed, 0 to remove and 593 not upgraded.
Need to get 0 B/196 MB of archives.
After this operation, 81.4 MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Extracting templates from packages: 100%
Preconfiguring packages ...
dpkg: error: cannot read info directory: No such file or directory
E: Sub-process /usr/bin/dpkg returned an error code (2)

```

Is reinstalling it much difficult ? I already miss the the format button from windows.

---

### Post by Bashing-om on 2015-03-13
Maximilian_Muneyos; Yuk ....
With:
> 
0 to remove and 593 not upgraded.
&&
dpkg: error: cannot read info directory: No such file or directory


The better thing in this case is a fresh clean install, in my opinion.
Once your data is backed up it is a matter of about 20 minutes - with a good internet connection - to be back up and running 14.04 .

[INDENT][INDENT]just what I think
[/INDENT][/INDENT]

---

### Post by Maximilian_Muneyos on 2015-03-13
As I said, I have nothing on this PC. If you could tell me how to proceed, I would be glad.

---

### Post by Elfy on 2015-03-13
> **Maximilian_Muneyos said:**
> As I said, I have nothing on this PC. If you could tell me how to proceed, I would be glad.

> **Bashing-om said:**
> Maximilian_Muneyos; Yuk ....
With:


The better thing in this case is a fresh clean install, in my opinion.
Once your data is backed up it is a matter of about 20 minutes - with a good internet connection - to be back up and running 14.04 .

[INDENT][INDENT]just what I think
[/INDENT][/INDENT]

I read the first post - and these last 2.

Frankly, if the machine has been that long without being used - is there actually anything on it you need to keep? 

If the answer to that is no - then just grab a copy of the 14.04 download and install it.

---

### Post by Maximilian_Muneyos on 2015-03-13
I inserted the CD and it automatically opened that thing (sorry, the PC with Linux is off now) that is made for downloading;/installing software. I tried to run it from there but to no avail. Then I opened the CD folder and clicked everything. Nothing. I will try again with a pen drive, but most likely I will switch to Windows. I don't like it either, but at least I can use it and solve whatever problem that arises rather smoothly. It is my first go with this version of Ubuntu and I am yet to fully use my computer. It is frustrating and I didn't find the experience very intuitive to say the least.

---

### Post by Bashing-om on 2015-03-13
Maximilian_Muneyos; Well.

One uses the tools one uses best.
If it is your desire to use ubuntu, we can help.
Whatever it takes.

[INDENT][INDENT]you have to have the want to
[/INDENT][/INDENT]

---

### Post by Maximilian_Muneyos on 2015-03-16
After successfully reinstalling Yosemite on my Mac yesterday, I thought, hey why not have another go with that ubuntu. What can go wrong ?


I tried reinstalling it with that CD I mentioned. It opens the Ubuntu software center, what do I do then ?

I downloaded Ubuntu 14.04 and it is now inside a fresh pen drive. I turn my PC on with it but nothing. The same with the CD, it opens the Ubuntu software center. 

I would really appreciate it if someone could tell me the magic spell that undoes the curse put on this very PC.

---

### Post by dino99 on 2015-03-16
you might want to glance at that thread  [http://ubuntuforums.org/showthread.php?t=1958688](http://ubuntuforums.org/showthread.php?t=1958688)

---

### Post by Maximilian_Muneyos on 2015-03-16
It is done. I got my frustration out of the way, manage to think clearly and it was rather easy. 

Thank you for your time and tons of patience. (I have to improve on that myself)

---

### Post by Elfy on 2015-03-16
That's good.

So what did you do? 

Other's might happen on this thread and wonder - that's what the forum is for.

---

### Post by Maximilian_Muneyos on 2015-03-16
I restarted my PC, pushed F12 and changed "boot" to "pendrive". It didn't work. I did the same thing and changed this time for "CD". It restarted with another CD I've burnt (that one wasn't runnning ok, I think). And the rest the computer did itself. Updates are working fine and I have Ubuntu 14.04. Why it didn't work with the pendrive or the other CD I don't know. By the way it was much faster than the Mac Yosemite that takes hours to download.

---

### Post by Elfy on 2015-03-16
Oh - so clean install?

---

### Post by Maximilian_Muneyos on 2015-03-16
Yes. My computer had nothing, as I wrote in my first post. After cleaning up the source list and yet not solving the problem, it was the way to go. But there must be an alternative out there.

---

