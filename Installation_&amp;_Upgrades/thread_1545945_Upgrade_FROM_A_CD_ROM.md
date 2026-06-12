---
title: "Upgrade FROM A CD ROM"
date: 2010-08-04
forum: Installation &amp; Upgrades
---

### Post by Cremator on 2010-08-04
Does anyone know how this is done?

I tried looking it up but all I keep on encountering is the "alternate" method from an ISO image.

I have an image burned to CD and need the CD ROM to be the source for the upgrade data.

I currently have 8.04LTS which does not support the USB stick modem I now have. So an offline upgrade is needed and as I have the CD, I need to use it but it won't upgrade, it only wants to install.

I had asked in a previous thread, couldn't find it, unfortunately it did not do the job and all I get is a 3 pages of erros spewing out of the terminal about the command given.

The media when in the DVD ROM drive shows up as ...

[FONT=monospace]**/media/Ubuntu 9.10 i386**

As the drive is readily accessible, how to I issue a command to say I want to upgrade and not install?

The situation with Ubuntu is that bad that I had to go out and buy a netbook to get internet access. It would appear that 8.04 is falling apart at the seams and is in desperate need of upgrading to something that I hope will play ball and not pose any more problems.

HELP!


*I forgot to mention that I nolonger have the original .ISO file, they are disposed of as soon as burned to disc.
[/FONT]

---

### Post by davidmohammed on 2010-08-04
instructions are [here]("https://help.ubuntu.com/community/LucidUpgrades") - look for "Upgrading Using the Alternate CD/DVD"

---

### Post by snowpine on 2010-08-04
You need the Ubuntu "Alternate CD", not the "Live CD."

Complete and official instructions for upgrading to 8.04 to 10.04: [https://help.ubuntu.com/community/LucidUpgrades](https://help.ubuntu.com/community/LucidUpgrades)

---

### Post by Cremator on 2010-08-04
Thanks for the guidance.

I was hoping that this would be a painless way but it seems that the people who release Ubuntu have neglected this side of upgrading and yet again I have to waste premium wireless (mobile internet) broadband on downloading yet another ISO file.

A completely dumb A question... does or has someone got a whizzo widget that can do likewise with a regular version ISO or CD image, it is possible to make an ISO if needed from the CD.

In leymans terms, if I was able to download the "Differential" files for this to work, is it possible?

---

### Post by snowpine on 2010-08-04
> **Cremator said:**
> Thanks for the guidance.

I was hoping that this would be a painless way but it seems that the people who release Ubuntu have neglected this side of upgrading and yet again I have to waste premium wireless (mobile internet) broadband on downloading yet another ISO file.

You're welcome! And not to be mean :) but if you had read the instructions and downloaded the correct CD in the first place, you would not be complaining about wasting bandwidth. ;) I am not sure why Ubuntu has 2 separate CDs but there is probably some legitimate technical reason that's over my head...

---

### Post by Cremator on 2010-08-04
> **snowpine said:**
> You need the Ubuntu "Alternate CD", not the "Live CD."

Complete and official instructions for upgrading to 8.04 to 10.04: [https://help.ubuntu.com/community/LucidUpgrades](https://help.ubuntu.com/community/LucidUpgrades)


Erm... I got as far as ...

1. Start System/Administration/Update Manager.

and have to say that this will not work... one of the problems I am encountering is with the update manager not working properly, it often throws an error and crashes.

This is the other reason why I need to upgrade.

---

### Post by snowpine on 2010-08-04
> **Cremator said:**
> one of the problems I am encountering is with the update manager not working properly, it often throws an error and crashes.


What is the error?

If you feel your system is totally broken, maybe consider a fresh reinstall? :)

---

### Post by Cremator on 2010-08-04
> **snowpine said:**
> You're welcome! And not to be mean :) but if you had read the instructions and downloaded the correct CD in the first place, you would not be complaining about wasting bandwidth. ;) I am not sure why Ubuntu has 2 separate CDs but there is probably some legitimate technical reason that's over my head...

Tell me about it.

Part of the problem is understanding what is needed, you find yourself herded towards the live CD version more than anything. 

Why they can not provide additional modules to add these tweaks or make the thing more modular, if that was to happen, then IMHO it would be more benefit to everyone.

Still, horses & water...

---

### Post by Cremator on 2010-08-04
> **snowpine said:**
> What is the error?

If you feel your system is totally broken, maybe consider a fresh reinstall? :)

The error is the result of an update from ubuntu. The file ... its error is moaning about a cpp file.

I tried to invoke the error, as I am not on-line, it won't appear and seeing as my old dongle that did work with this machine went to modem heaven, the new one is not recognised, replicating the issue is not possible.

I can say that one of the errors is to do with broken package from ubuntu and the other being a cpp file throwing an error.

Broken, it might be, possibly explains why Ubuntu thinks the 20GB drive is 30GB and why I have 0bytes space left... Physically impossible when 2 Gigs is being occuied as a Swap for Linux and the rest is given up to the files and OS, I fail to see why disk space was being mis reported and the other odd thing was that drive space has been disapearing because I have 9 Gigs of files on the drive which means I should have at the minimum, accounting for the Swap drive, atleast 8 Gigs of drive space which has completely vanished and find that the 20 Gig drive is a Tardis and has some how found an additional 50% in drive space.

The email (sendmail) does not work and still 2 years on theirs about 140 cron jobs trying to send the original test emails and can I kill the processes? 

Still, I and friends have raised issues in the past about these things that I have had issues with and its possibly why they all went back to Winblows and the buggy programs still exist and as far as I am aware, never been updated as this system has been maintained on a regular basis.

It sounds extreme but I had to buy a netbook that only came with windows so that the modem would work and I could get on here to access help in fixing ubuntu.

Broken it possibly is, it still runs and I want to upgrade to retain the data on that drive as I have no way of backing it up at present. The USB 320 HDD is currently full and the other 128 Gigs of flash drives are also full. I would contemplate using a DVD to back up the data but I am in the problem of not enough disk space...

Stuck between a hard place and something harder than the hard place...

---

### Post by ajgreeny on 2010-08-04
Have a look at this thread started by me some time ago.
[http://ubuntuforums.org/showthread.php?t=1117604](http://ubuntuforums.org/showthread.php?t=1117604)
As you see I wanted to have a separate /home partition but did not have any simple way to backup all my home folder.

So using the live CD, shrink the old root partition to give you room for the new root partition without removing any of the home files.  Just the old /root operating system files are deleted using the live CD, but use Shift+Del or they end up in the live CD trash and take valuable memory from the running live CD.

Now you will have your old home files still in a folder called /*username* and you will need to move them all to the root of what will become the new /home partition, perhaps folder by folder depending on the free space you have.

Having done that and got all your old home contents (don't forget hidden files and folders; Ctrl+H to see them) into the folder that will be your new /home, use the Live CD to install but use manual partitioning at that stage and make sure the new /home is not formatted.  See [http://www.psychocats.net/ubuntu/installseparatehome](http://www.psychocats.net/ubuntu/installseparatehome) for info on making a separate /home when installing.

I hope that helps you.  Sorry if it seems very complicated but it is a possible way out of your dilemma.

---

