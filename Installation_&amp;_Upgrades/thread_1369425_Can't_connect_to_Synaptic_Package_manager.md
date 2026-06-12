---
title: "Can't connect to Synaptic Package manager"
date: 2009-12-31
forum: Installation &amp; Upgrades
---

### Post by GaryS1953 on 2009-12-31
Hi- Have a new Dell Vostro A90 that came with 8.04 and I have installed 9.10 from a CD that was mailed to me.  I can connect to the internet with a wired connection, but I cannot connect wirelessly.  When I've tried to install the broadcom driver by going to Synaptic Package Manager and hitting reload, I get a message that 1 of 15 packages is downloading, but nothing downloads and I get a failed message for each of the jobs.  Any clues as to how to proceed from here?  I am very new to Ubuntu.  Any help really appreciated.

---

### Post by hansdown on 2010-01-01
Hi GaryS1953.

The broadcom driver should be there.

Click system> administration> hardware drivers.

See if you have an option to activate.

Could you please post the error message?

---

### Post by GaryS1953 on 2010-01-01
Hi, and thanks for your reply.  The driver is not there, and nothing downloads.  Also, though [I]i do have wired internet access on the mini, I am unable to connect to the forum.  I can get to Ubuntu.com and the support pages, but it refuses to go to the forum page.  Weird.  Any way, I am retyping part of the error message here using my Macbook.

An error occurred
The following details are provided:
W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/karmic/](http://us.archive.ubuntu.com/ubuntu/dists/karmic/)
Release.gpg  Could not connect to us.archive.ubuntu.com:8
(159.102.255.127), connection timed out.

Any ideas?  Thanks!
[/I]

---

### Post by hansdown on 2010-01-01
Could you please post your /etc/apt/sources.list?

Applications -> Accessories -> Terminal

Copy and paste this.

```
cat /etc/apt/sources.list
```

---

### Post by GaryS1953 on 2010-01-01
Ok, here it is.  Thanks!

Version:1.0 StartHTML:0000000159 EndHTML:0000010924 StartFragment:0000003412 EndFragment:0000010888 SourceURL:file:///Volumes/NO%20NAME/Untitled%201.doc                   # deb cdrom:[Ubuntu 9.10 _Karmic Koala_ - Release i386 (20091028.5)]/ karmic main restricted
  
  # See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
  
  # newer versions of the distribution.
  
   
   
  deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic main restricted
  
  deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic main restricted
  
   
   
  ## Major bug fix updates produced after the final release of the
  
  ## distribution.
  
  deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-updates main restricted
  
  deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-updates main restricted
  
   
   
  ## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
  
  ## team. Also, please note that software in universe WILL NOT receive any
  
  ## review or updates from the Ubuntu security team.
  
  deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic universe
  
  deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic universe
  
  deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-updates universe
  
  deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-updates universe
  
   
   
  ## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
  
  ## team, and may not be under a free licence. Please satisfy yourself as to 
  
  ## your rights to use the software. Also, please note that software in 
  
  ## multiverse WILL NOT receive any review or updates from the Ubuntu
  
  ## security team.
  
  deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic multiverse
  
  deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic multiverse
  
  deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-updates multiverse
  
  deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-updates multiverse
  
   
   
  ## Uncomment the following two lines to add software from the 'backports'
  
  ## repository.
  
  ## N.B. software from this repository may not have been tested as
  
  ## extensively as that contained in the main release, although it includes
  
  ## newer versions of some applications which may provide useful features.
  
  ## Also, please note that software in backports WILL NOT receive any review
  
  ## or updates from the Ubuntu security team.
  
  # deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-backports main restricted universe multiverse
  
  # deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-backports main restricted universe multiverse
  
   
   
  ## Uncomment the following two lines to add software from Canonical's
  
  ## 'partner' repository.
  
  ## This software is not part of Ubuntu, but is offered by Canonical and the
  
  ## respective vendors as a service to Ubuntu users.
  
  # deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) karmic partner
  
  # deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) karmic partner
  
   
   
  deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-security main restricted
  
  deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-security main restricted
  
  deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-security universe
  
  deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-security universe
  [FONT=Times][/FONT]
  deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-security multiverse
  
  deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) karmic-security multiverse
  
  gary@gary-Dell-Mini:~$

---

### Post by hansdown on 2010-01-01
Thank you GaryS1953.

Generally fresh installs work better than upgrades.

Fear not, I don't judge.

Could you paste 

```
Sudo apt-get update-f 

```
In the terminal?

---

### Post by GaryS1953 on 2010-01-01
Maybe I'm mis-understanding, but this was a fresh install from a CD that was mailed to me.  I completely wiped the 8.04 and all settings off the ssd and installed 9.10.  

Your command results in the following:
Invalid operation update -f

---

### Post by hansdown on 2010-01-01
My apologies GaryS1953.

I am the one who is mis-understanding.

---

### Post by hansdown on 2010-01-01
O.K.

This seems to be a problem with this machine.

A quick fix is here.

[http://www.ubuntumini.com/2009/11/broadcom-wireless-driver-fix-in-karmic.html](http://www.ubuntumini.com/2009/11/broadcom-wireless-driver-fix-in-karmic.html)

---

### Post by GaryS1953 on 2010-01-01
Happy New Year Hansdown,

The fix you pointed me to is what started this.  When I try to download the broadcom wirless driver using the synaptic package manager I get the error message that I typed in earlier in the thread.

I'm thinking it's related to my internet connection or the machine itself.  I have no problem with my macbook, buy with my Dell I seem to have limited internet access over ethernet.  I've got it connected directly to my router, and I've tried both of my ethernet cables in case one was bad, but both give the same results.  For example, I can do a google search and get plenty of results, but when I actually click on the links the Dell refuses to go to them.  When I click on them from the Macbook I have no problems.  Also, this forum, I can get to it from the Macbook, but when I try with the Dell I can't go to the forum, only to the main Ubuntu page, and the support pages, and it doesn't make a difference whether I click on the links on the support page to get to the forum, or if I enter the address directly in the browser, I still can't get to the forum with the Dell, which is the ubuntu system.

I did download the driver with my Macbook and then transferred it to my dell with a usb stick, but I'm not sure what to do with it now that it's there.  Any thoughts as to WHERE I should put it and what commands I should issue to install it?

Thanks so much!

---

### Post by GaryS1953 on 2010-01-01
OK, gave up on 9.10 for now and installed 9.04.  Everything working great now.  I'll wait for the next stable release before upgrading again.

---

### Post by hansdown on 2010-01-01
9.04 seems to work very well with the atom processors.

Hopefully the next release will address the driver issue.

---

