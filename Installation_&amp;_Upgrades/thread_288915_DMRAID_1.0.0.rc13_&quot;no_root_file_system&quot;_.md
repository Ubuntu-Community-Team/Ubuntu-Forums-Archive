---
title: "DMRAID 1.0.0.rc13 &quot;no root file system&quot; error. The suggested fix doesn't work."
date: 2006-10-30
forum: Installation &amp; Upgrades
---

### Post by _Eleazar_ on 2006-10-30
The posted fix for this error [https://launchpad.net/bugs/67130](https://launchpad.net/bugs/67130) does not work. I have ICH6 Intel fakeraid. 

Partition 1 NTFS
Partition 2 EXT Partition linked to partition 5
Partition 3 Linux Reiserfs5 
Partition 4 SWAP
Partition 5 Logical NTFS linked to partition 2

There are some oddities I notice. When I install DMRAID none of my partitions are showing up in GPARTED's advanced partition editor (manual editing). They do show up in ubiquity for the automatic list. Which I don't need because I setup my partitions using ntfsresize, fdisk, mkreiserfs, mkswap, and swapon. Two things I have already tried is changing the Reiserfs5 to EXT2 and EXT3 with no success. This partition was never a root partition to begin with because this is the first time I have even installed Linux on this particular machine. I also know this partition has not been flagged as a root partition because I checked it out in parted. So what the heck is up?

I thought about using the alternate text install, but there is no way for me to get DMRAID on it. If there is then their definitely isn't a way to get the version I need on it. The only DMRAID in the universe right now is 1.0.0.rc9 which won't work with EDGY. I need 1.0.0.rc13 which can only be downloaded from the devs ftp site. 

Please help me out here, I am stumped.

EDIT: One thing I wanted to mention is that other people using DMRAID 1.0.0.rc13 have been able to use ubiquity and install Unbuntu EDGY without any problems. I wanted to say this just in case someone thought DMRAID was the problem.

---

### Post by _Eleazar_ on 2006-10-30
Does anyone have any ideas?

---

### Post by _Eleazar_ on 2006-11-01
Bump. 

If anyone has any ideas that would be great.

---

### Post by keithy on 2006-11-01
Sorry,

I don't know how to fix your problem.  I would love to know how to get DMRAID 1.0.0.rc13 into edgy install however??

Thanks

---

### Post by _Eleazar_ on 2006-11-01
If you follow these instructions you will be able to get it installed. Here is a copy of another one of my posts:

----------------------------------------------------------------------------
You need to use DMRAID it sounds like. Though if you are a new user to Linux I wouldn't suggest it. The documentation is terrible for a new user and only is really good for people who already have some sort of knowledge about Linux. Here is a howto for Dapper Drake 6.06, with some 6.10 tips.
[https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)

You will most likely need to get the latest version of DMRAID from here
[http://librarian.launchpad.net/4934470/dmraid_0.9.9%2B1.0.0.rc13.source.tgz](http://librarian.launchpad.net/4934470/dmraid_0.9.9%2B1.0.0.rc13.source.tgz)

You are going to have to build it yourself. To build it you are going to have to go to the directory you extracted the dmraid folder. For me it was the Desktop. You first have to download all the dependency libraries from the Synaptic Package Manager, which are:

Build-essential
libdevmapper-dev
libklibc-dev
libselinux1-dev
zlib1g-dev
automake (download the -dev too if it exists, it may not)
autoconf (download the -dev too if it exists, it may not)

So I:
cd ~/Desktop
cd /dmraid
cd /1.0.0.rc13

I then,

./configure
make
sudo make install

That should get it installed for you. Then from there follow the documentation. I would like to reiterate that I would not recommend this for someone who is still rather new to Linux. The guide just leaves some things out that really should be told to a new user. For instance, how to find out the end sector location of 60GB on your hard drive. This is necessary if you are going to be using ntfsresize for your NTFS partition. There are other things muddled throughout the guide it just assumes you know, that a new user wouldn't know. Make sure you read it first if your going to give it a go.

EDIT:
Some people say they have had more success with this guide:
[http://www.ubuntu-in.org/wiki/SATA_RAID_Howto](http://www.ubuntu-in.org/wiki/SATA_RAID_Howto)
-----------------------------------------------------------------------------------------------------------------------------

---

### Post by rmjb on 2006-11-01
Hi, great that you've posted that how to on getting Edgy installed on dmraid. However, you don't have to compile it yourself if you're using x86 or amd64, there are already packages for these architectures here:
x86: [http://librarian.launchpad.net/4930804/dmraid_0.9.9%2B1.0.0.rc13-0ubuntu1_i386.deb](http://librarian.launchpad.net/4930804/dmraid_0.9.9%2B1.0.0.rc13-0ubuntu1_i386.deb)
amd64: [http://librarian.launchpad.net/4939660/dmraid_0.9.9%2B1.0.0.rc13-0ubuntu1_amd64.deb](http://librarian.launchpad.net/4939660/dmraid_0.9.9%2B1.0.0.rc13-0ubuntu1_amd64.deb)

On to your main problem, I was not successful in getting gparted and ubiquity to work with my dmraid partitions. In fact I packaged up a new version of gparted to install in the live cd session so I could repartition. I've attached that i386 deb to this post.

Once you repartition with that updated gparted you should run *sudo dmraid -ay* again then start ubiquity. I'm learning more about this as I go along, but doing that *might* allow ubiquity to format your new partitions properly and continue with the installation.

When you're finished with the installation however, before you reboot you might need to mount your newly installed filesystem on /target with the /dev, /proc and /sys as shown in the two howtos you linked to, chroot into it and install dmraid rc13 since it wont be installed in your newly installed system, and that might cause a problem on reboot.

I myself am going to test this process later today so I'll let you know how it goes.

- rmjb

---

### Post by rmjb on 2006-11-01
The method I came up with in my last post does not work. Even though installing the new gparted allows it to work with the fakeraid device ubiquity still cannot, and the new gparted apparently is not patched to work with ubiquity.

For now install the new dmraid, use the new gparted if you want it for partitioning. After your repartition, but before you format make sure you run dmraid -ay again. And follow one of the howtos.

I'm doing this process now.

- rmjb

---

### Post by _Eleazar_ on 2006-11-01
Ok,I am going to try it now and let you know how everything goes. I just wanted to post something for anyone else that might be trying this using the unbuntu-in guide. There are changes you will need in order to get it to work.

This is directly under INSTALL BASE SYSTEM
DONT USE:
debootstrap dapper /target
USE:
debootstrap edgy /target [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu)


This was taken directly from debootstrap's manual, with a minor adaptation to be consistent with the posted guide.

This is right after you chroot
DONT USE:
apt-get install ubuntu-base linux-386 ubuntu-desktop dmraid grub
USE:
apt-get install ubuntu-standard linux-386 ubuntu-desktop grub
OR
apt-get install ubuntu-minimal linux-386 ubuntu-desktop grub

You will now have to either compile DMRAID like I did to get it installed or download it from the links in rmjb's post. If you apt-get the dmraid it will be rc9 and it will not work. 

Everything else in that guide should be gold. These adaptations should hopefully work; I haven't had the chance to test them yet. I am going to give it a try now.

EDIT:
Um, the apt-get install statements are now actually correct. The only change is taking out dmraid, not grub as well. For some stupid reason I forget how to read and was reading grub as gparted. Yeah, don't ask.
EDIT AGAIN:
ubuntu-base is incorrect for EDGY. You will have to change this to ubuntu-standard or ubuntu-minimal

---

### Post by _Eleazar_ on 2006-11-01
Ok I have everything installed and everything seemed to go perfectly. I reboot my machine and I hit ESC to load Linux. I hit enter to load Linux and the WHAM I get like 6-8

buffer i/o error on device sda3, logical block blahblahblah

Everything seems to just stop there. There are some things I would like to note but am unsure if they mean anything.

1. I never configured fstab.
2. After I chroot I installed DMRAID by opening the dmraid deb package and clicking reinstall. I was hoping this would install DMRAID on to the root I changed to.
3. I didn't change anything with the init
4. I didn't do a base-config new because it doesn't seem to even exist.

I will be needing help with fstab if that needs to be done.

isw_cigbaiabcj_RAID_Volume02 is my /
isw_cigbaiabcj_RAID_Volume03 is my swap

So what exactly should be fstab look like. I tried doing to: 

cat /etc/mtab

But it didn't show any of my RAID partitions. Which is what makes me think maybe I didn't install DMRAID correctly when I chroot. Or maybe it is something else entirely.

---

### Post by _Eleazar_ on 2006-11-02
Any suggestions? What did I do wrong? What can I do to correct this?

---

### Post by rmjb on 2006-11-03
Okay, I have a modified version of the HOWTOs that worked for me yesterday.

1st, when you chrooted then double clicked on the dmraid package, it re-installed dmraid into your live session. When you chroot only the command prompt you're on chroots.

*** Supplemental Steps***

Follow the HOWTOs up until they tell you to install debootstrap. Don't do that step.
At that point you should have your dmraid partitioned, formatted and mounted on /target.
Now, copy the contents of /rofs into /target. You should be able to do this with:
```
# cp -av /rofs/* /target
```

This is how the installer works, it copies the contents of /rofs to /target. This way you don't have to re-download everything.

Next, to do the base configuration, type python at the command prompt.
At the python prompt paste the following lines:
```

import sys
import os
import errno
import shutil
import syslog
import atexit

sys.path.insert (0, '/usr/lib/ubiquity')

from ubiquity import misc

targetdb = '/target/var/cache/debconf/config.dat'
for q in ('^console-setup/'):
    misc.ex ('debconf-copydb', 'configdb', 'targetdb', '-p', q,
        '--config=Name:targetdb', '--config=Driver:File',
        '--config=Filename:%s' % targetdb)

```

This is the config code out of the installer. To exit python hit Ctrl-D.

Now, you have to continue with the steps in the HOWTO from here:
[https://help.ubuntu.com/community/FakeRaidHowto#head-b40f74375e725eb35189a50fbb6f31b5f840fb6e](https://help.ubuntu.com/community/FakeRaidHowto#head-b40f74375e725eb35189a50fbb6f31b5f840fb6e)

Before you reboot there are still a few things that need to be done. Copy the rc13 dmraid into your /target somewhere then chroot into your /target and cd to where you have the dmraid rc13 deb and enter ```
# dpkg -i dmraid_0.9.9+1.0.0.rc13-0_i386.deb
``` to ensure your /target has dmraid installed.

Also you'll need to create a user. The user you create here should not be the one you plan to use, this should just be a seed user to complete the configuration after you reboot. This is because this user does not get set up properly.

First, create the user:
```
# adduser user
```

Next, you'll need to create the admin group and add the user to it:
```
# addgroup --system admin
# adduser user admin
```

Next use the **visudo** command to add the following lines to sudoers:
```
# Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL
```


Finally, ensure that your fstab is set up properly, this is a necessity to boot your system.

Modify the following example to suit your system:
```

# file system                       mount point   type    options                  dump pass
/dev/mapper/nvidia_fdkiauw2         /             ext3    defaults                 0    1
/dev/mapper/nvidia_fdkiauw1         /boot         ext3    defaults                 0    2
/dev/mapper/nvidia_fdkiauw3         none          swap    sw                       0    0
proc                                /proc         proc    defaults                 0    0
sys                                 /sys          sysfs   defaults                 0    0
```

Now you can reboot.

When the freshly installed system comes up, you need to log on as the seed user and do the final configurations:
- Create the proper users that you need
- Go to System -> Maladministration -> Language Support and remove the languages you do not need. A lot of them will be the check box with a dash ( - ) in it.
- Right click on your time in the top panel and select your time zone and set your time.
- Go to System -> Administration -> Networking and set your hostname in the General tab.

Now do one final reboot and you can log on as your regular user.

Hopefully Feisty will support dmraid devices in the installer.

Let me know how this works for you, if it works well I'll add it to the wiki.

- rmjb

---

### Post by thockin on 2006-11-06
I've been trying to get this going on a new board with nvraid.  A Wasted day, so far.

Does anyone plan to produce a hacked Edgy install CD with dmraid support fully implemented?  I'll kick in some cash to whoever has the time and know-how to do this.  Surely, someone who knows the installer can accomplish this in a day or two.

Could be quick cash.

---

### Post by zaubara on 2006-11-19
I just managed to install Edgy on my dmraid, aswell - working fine in dual boot with WinXP.

What i basically did was booting up the 6.10 Ubuntu desktop LiveCD, installing dmraid (i uploaded the files I used temporarily at [http://bitshare.de/download.php?file=388560](http://bitshare.de/download.php?file=388560) so I always had them at hand after rebooting/reformating etc. - afair I got those from the official Debian archive), and followed rmjb's HOWTO for most of the time.

After I was finished with the HOWTO part, sound didn't work for me at first, and after I did a reboot, I couldn't log in anymore aswell.
The login problem was easily solved by adding the lo interface to the autostart script (located at /etc/network/interfaces).

Sound was already well configured, but for some reason it just wouldn't work - I had to add my new user to the sound group (located at /etc/group).
To be honest, I dont know if this is the "clean" way to solve that, but it still works ;)

After that, I used automatix2 to install graphics drivers and that kind of stuff.

Thanks, rmjb!

edit:
One thing I forgot to mention: repartitioning my old Linux partition (I had it at /dev/mapper/nvidia_bcbgebdc6) to a smaller bcbgebdc6 and a swap partition at bcbgebdc7 using the gparted in my tar.gz nearly killed all my data!
Deleting #6 worked fine, but recreating #6 and #7 didn't work out as expected - it has overwritten my main partition completely with one huge 300gb reiser one!
Luckily, I could reactivate my partitions with TestDisk and reformat those partitions in Windows with PartitionMagic...

- Martin

---

### Post by tormod on 2006-11-23
> **_Eleazar_ said:**
> 
I thought about using the alternate text install, but there is no way for me to get DMRAID on it. If there is then their definitely isn't a way to get the version I need on it. The only DMRAID in the universe right now is 1.0.0.rc9 which won't work with EDGY. I need 1.0.0.rc13 which can only be downloaded from the devs ftp site.
I wrote up my way of installing Ubuntu 6.10 onto an Intel fakeraid, using the Alternate installer: [https://wiki.ubuntu.com/FakeRaidEdgy](https://wiki.ubuntu.com/FakeRaidEdgy)
It explains how to get dmraid into the installer run-time.

---

