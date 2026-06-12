---
title: "&quot;Updates failing ,Nvidia 183 crashs,upgrade to 10.4LTS problemsproblems10.4"
date: 2010-05-04
forum: Installation &amp; Upgrades
---

### Post by eGelor on 2010-05-04
7 months using Linux , 2 months in this Forum.
I'm searching for answers too long. 

My vga card crashes to a black screen with 178 and 183 drivers 
searching and executing threads for this problem does not fix nada.


 > 01:00.0 VGA compatible controller: nVidia Corporation G98 [GeForce 9200M GS] (rev a1)

Problem with update 2.6.31-21 gives 
> W: Failed to fetch [http://ppa.launchpad.net/user/ppa/ubuntu/dists/karmic/main/binary-i386/Packages.gz](http://ppa.launchpad.net/user/ppa/ubuntu/dists/karmic/main/binary-i386/Packages.gz)  404  Not Found


My upgrade gives:
> Failed to fetch [http://archive.ubuntu.com/ubuntu/poo...buntu1_all.deb](http://archive.ubuntu.com/ubuntu/poo...buntu1_all.deb) Could not resolve 'archive.ubuntu.com'
Failed to fetch [http://archive.ubuntu.com/ubuntu/poo...1.0-4_i386.deb](http://archive.ubuntu.com/ubuntu/poo...1.0-4_i386.deb) Could not resolve 'archive.ubuntu.com'
Failed to fetch [http://archive.ubuntu.com/ubuntu/poo...buntu1_all.deb](http://archive.ubuntu.com/ubuntu/poo...buntu1_all.deb) Could not resolve 'archive.ubuntu.com'
Failed to fetch [http://archive.ubuntu.com/ubuntu/poo...untu6_i386.deb](http://archive.ubuntu.com/ubuntu/poo...untu6_i386.deb) Could not resolve 'archive.ubuntu.com'
Failed to fetch [http://archive.ubuntu.com/ubuntu/poo...buntu6_all.deb](http://archive.ubuntu.com/ubuntu/poo...buntu6_all.deb) Could not resolve 'archive.ubuntu.com'
Failed to fetch [http://archive.ubuntu.com/ubuntu/poo...buntu1_all.deb](http://archive.ubuntu.com/ubuntu/poo...buntu1_all.deb) Could not resolve 'archive.ubuntu.com'

Please Help.
With Appreciation
Eugene Trifonides.:confused:
19/05/2010 Update, upgrade ok! test 2.6.32.22 and 32.21 with my nvidia faild.
i check all vesa,nv,nvdia into xorg.conf
nada

---

### Post by cavh on 2010-05-04
For the Nvidia issue:

Download the Nvidia driver here (you cannot get the Nvidia driver through the Ubuntu repositories as it's not open source):

[http://www.nvidia.com/Download/index5.aspx?lang=en-us]("http://www.nvidia.com/Download/index5.aspx?lang=en-us")

You will see a pop-up when you download - see screenshot below. Save the file. Make a note of where you saved it, and the name of the file.

Next, move into console mode by pressing the CTRL+ALT+F1 keys together (you can get back to the desktop by pressing CTRL+ALT+F7). Log in using your Ubuntu username and password.

Then navigate to the directory containing the downloaded driver .run file, then type ```
sudo sh NVIDIA-Linux-x86-195.36.24-pkg1.run
``` (change the file name to suit the name of your file, this is just an example!) and enter your password. Follow the prompts, and say 'yes' when the install asks whether you want to run the Nvidia settings process. This will write the xorg.conf file you need.

Then exit console mode by pressing CTRL+ALT+F7, and log out and back in again (you may need to restart the machine if the display doesn't auto-adjust itself).

This process has to be followed each time you upgrade the kernel, but you don't need to download the driver each time - just start at CTRL+ALT+F1 point.

Suggestion - don't post on multiple issues within the same post, unless you're sure they're codependent. People might know the answer to one question but not both, and end up not answering you at all :)

---

### Post by eGelor on 2010-05-04
i did what you just told me .

sudo gdm stop

run the Nvidia drivers with 
sudo sh (e.t.c).run

And i take a message that i got to be at level 3
and currently i'm on level 1.

i would be pleased if you can post me the answer of how to go at level 3.

i fill that my problem will be the nvidia-settings
with 183 that Hardware suggest me has easy.


i'll be waiting your response.
With Appreciation.
Eugene

---

### Post by eGelor on 2010-05-04
i find to run level 3 by typing 
init 3 through my terminal.

no good news.
1. I get this error 

can't find :
/usr/lib/nvidia/libglx.so.xserver-xorg-core 

NVIDIA crash into a black screen. 

i replace the xorg.conf file and now
i start my gdm by 
sudo gdm start
 my screen now is separated in two .

Please Help.
sudo sh (nvidia_drivers) --uninstall

---

### Post by cavh on 2010-05-05
It sounds to me that the Nividia driver is not loaded. Your last post doesn't make it clear whether you ran this code when your machine was at run level 3? If not, please do so and let us know what the result is.
```

sudo sh (package name).run
```

---

### Post by dino99 on 2010-05-05
your errors are because you have used and mixed the drivers and libs, result in a general mess. If ubuntu devs fine tuned drivers its not for nothing  :lolflag:

check your repo into synaptic and only use genuine lucid repo ( no ppa), then update and : 

sudo rm -f /etc/X11/xorg.conf

remove/purge all graphic drivers installed, then install : nvidia-current, nvidia-current-modaliases, nvidia-common, nvidia-settings

reboot

---

### Post by eGelor on 2010-05-05
i run at level 3 from my tty 1 ctrl+Alt+F1
without gdm . For sure the problem is the mess that my nvidia drivers in .
 Give me some time and stay toned with me .
with many Appreciation 
Eugene

---

### Post by eGelor on 2010-05-05
I did remove from my synactic nvidia driver 
i remove my xorg.conf
i did :
sudo apt-get nvidia-current, nvidia-current-modaliases, nvidia-common, nvidia-settings

nada.

---

### Post by cavh on 2010-05-06
Update your repository information first

```
sudo apt-get update
```

then run

```
sudo apt-get install nvidia-current
```

again

---

### Post by eGelor on 2010-05-06
i did sudo apt-get update and i take this error:
> Fetched 239kB in 1s (123kB/s)   
W: Failed to fetch [http://ppa.launchpad.net/user/ppa/ubuntu/dists/karmic/main/binary-i386/Packages.gz](http://ppa.launchpad.net/user/ppa/ubuntu/dists/karmic/main/binary-i386/Packages.gz)  404  Not Found

E: Some index files failed to download, they have been ignored, or old ones used instead.


Upgrade 10.4 (ok) update  2.6.32.22 tested-faild 32.21 tested-faild.

---

### Post by eGelor on 2010-05-06
sudo apt-get install nvidia-current

E: Couldn't find package nvidia-current

---

### Post by cavh on 2010-05-07
That's strange. Please post the output of this command:

```
cat /etc/apt/sources.list
```

This lists the repositories your system searches for packages.

---

### Post by eGelor on 2010-05-08
the outpou of the command,
car /etc/apt/source.list
is :> # deb cdrom:[Ubuntu 9.10 _Karmic Koala_ - Release i386 (20091028.5)]/ karmic main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://c.archive.ubuntu.com/ubuntu/](http://c.archive.ubuntu.com/ubuntu/) karmic restricted main
deb-src [http://c.archive.ubuntu.com/ubuntu/](http://c.archive.ubuntu.com/ubuntu/) karmic restricted multiverse universe main #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://c.archive.ubuntu.com/ubuntu/](http://c.archive.ubuntu.com/ubuntu/) karmic-updates restricted main
deb-src [http://c.archive.ubuntu.com/ubuntu/](http://c.archive.ubuntu.com/ubuntu/) karmic-updates restricted multiverse universe main #Added by software-properties

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://c.archive.ubuntu.com/ubuntu/](http://c.archive.ubuntu.com/ubuntu/) karmic universe
deb [http://c.archive.ubuntu.com/ubuntu/](http://c.archive.ubuntu.com/ubuntu/) karmic-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://c.archive.ubuntu.com/ubuntu/](http://c.archive.ubuntu.com/ubuntu/) karmic multiverse
deb [http://c.archive.ubuntu.com/ubuntu/](http://c.archive.ubuntu.com/ubuntu/) karmic-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://gr.archive.ubuntu.com/ubuntu/](http://gr.archive.ubuntu.com/ubuntu/) karmic-backports main restricted universe multiverse
# deb-src [http://gr.archive.ubuntu.com/ubuntu/](http://gr.archive.ubuntu.com/ubuntu/) karmic-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) karmic partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) karmic partner

deb [http://c.archive.ubuntu.com/ubuntu/](http://c.archive.ubuntu.com/ubuntu/) karmic-security restricted main
deb-src [http://c.archive.ubuntu.com/ubuntu/](http://c.archive.ubuntu.com/ubuntu/) karmic-security restricted multiverse universe main #Added by software-properties
deb [http://c.archive.ubuntu.com/ubuntu/](http://c.archive.ubuntu.com/ubuntu/) karmic-security universe
deb [http://c.archive.ubuntu.com/ubuntu/](http://c.archive.ubuntu.com/ubuntu/) karmic-security multiverse


---

### Post by eGelor on 2010-05-17
I solve the problem with update and upgrade.
the problem was the bad internet connection.
Now my problem is that No keyboard after upgrade, i use graphic keyboard to log in and then what ??
pls post back.
Keybord solved this this: 
 Solution was to first upgrade dpkg (apt-get install dpkg) then run a full upgrade (aptitude full-upgrade). This caused the util-linux error to go away and full-upgrade to hum along like normal.
I fix my problem today.

Now i'm going to test nvidia with 2.6.32.21 & 32.22 >> & check my drivers again. I don't want the nvidia an more i got study to do.

---

