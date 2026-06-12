---
title: "how to update linux-kernel release in gutsy?"
date: 2008-01-10
forum: Installation &amp; Upgrades
---

### Post by veeyes on 2008-01-10
I have been using ubuntu for a while, but, it was only today that i noticed that iam running an older version of kernel release (uname -r gives 2.6.20-16-386, but, I think I should be having 2.6.22-14-386, which is what i find in my /usr/src/linu-...).
I don't know why this happened. Can someone please help me upgrade to the correct kernel-release?

Thanks,
VS

---

### Post by manimal347 on 2008-01-10
Actually, unless you have an antiquarian machine (Pre-K6-2/Cyrix & early Via/ pre PII?), you should probably be running the generic kernel tree. Just "sudo apt-get install linux-image-2.6.22-14-generic"
This will be one of the few times when you'll have to give your Linux box a complete reboot to culminate the upgrade. Presumably, it should also provide a speed boost, though not as much as if Ubuntu would return to offering the tweaked K7, SMP, I686, .etc .etc kernels.

If you don't have this package, something is probably wrong with your repositories, perhaps something left over from Feisty or Edgy.

---

### Post by veeyes on 2008-01-10
Thanks for the response.
I noticed that I have 2.6.22-14 -386 and -generic already installed. But, my 'uname -r' still shows 2.6.20-16-386!!! I don't understand why. I even tried reinstalling 2.6.22-14-386 and generic, hoping it would add these to my grub list, and I could restart in these images and uninstall 2.6.20-16, but, that didn't work out.

how do I remove 2.6.20-16 and run 2.6.22-14?

VS

---

### Post by PmDematagoda on 2008-01-10
Could you post the result of:-
```
cat /etc/apt/sources.list
```

---

### Post by zvacet on 2008-01-10
Something is not right here.Please post output of 

```
lsb_release -a
```

---

### Post by veeyes on 2008-01-10
/etc/apt/sources.list
```
# deb cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/ dapper main restricted


## Uncomment the following two lines to fetch updated software from the network
# deb cdrom:[Ubuntu 7.04 _Feisty Fawn_ - Release i386 (20070415)]/ gutsy main restricted
deb http://us.archive.ubuntu.com/ubuntu/ gutsy main restricted multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb http://us.archive.ubuntu.com/ubuntu/ gutsy-updates main restricted multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://us.archive.ubuntu.com/ubuntu/ gutsy universe restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse

deb http://us.archive.ubuntu.com/ubuntu/ gutsy-security main restricted multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy-security main restricted

deb http://us.archive.ubuntu.com/ubuntu/ gutsy-security universe
deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy-security universe
# deb http://ftp.debian.org sarge main

# Google Picasa for Linux repository
# deb http://dl.google.com/linux/deb stable non-free

# Thunderbird

deb http://us.archive.ubuntu.com/ubuntu/ gutsy-proposed restricted main multiverse universe

```

lsb_release -a
```

LSB Version:    core-2.0-noarch:core-3.0-noarch:core-3.1-noarch:core-2.0-ia32:core-3.0-ia32:core-3.1-ia32
Distributor ID: Ubuntu
Description:    Ubuntu 7.10
Release:        7.10
Codename:       gutsy
```

---

### Post by zvacet on 2008-01-10
Source list looking good and according to **lsb_release -a** you have Gutsy installed.Still you don´t have it´s kernel.Very odd.Did you try direct upgrade from Breezy to Gutsy (because I see one Breezy line in your source list)?

---

### Post by veeyes on 2008-01-10
No, I upgraded from Feisty to Gutsy, but, had to change the sources.list file manually. So, left the commented line in there!
I don't understand why I am not able to reinstall 2.6.22-14 and get it in my boot options. I thought that way I could boot into 2.6.22-14, and then remove 2.6.20-16. I have lots of data in this machine that I cannot clear the disk and reinstall Ubuntu on it now. :(
Is there anything else I can try?

Thanks for the suggestions!
VS

---

### Post by zvacet on 2008-01-10
Look in synaptic for **linux-image2.6.22-14-generic** and install it.I still don´t understand how comes that is not installed during upgrade.

---

### Post by veeyes on 2008-01-10
I checked that. linux-image2.6.22-14-generic is already installed. But, it does not show up as an option for me to boot into. At boot-up, I only have the 2.6.20-16-386 kernel which I can boot into. And, obviously, I can't uninstall this :(

Thanks again,
VS

---

### Post by PmDematagoda on 2008-01-10
Try:-
```
sudo update-grub
```

---

### Post by veeyes on 2008-01-10
I did a 'sudo update-grub', and now I can only get into my system using the Ubuntu Feisty CD :(
I don't know how to backup the data either!!

Still, thanks for all the suggestions, let me know if there is anything I can try now!

VS

---

### Post by zvacet on 2008-01-11
```
 cat /boot/grub/menu.lst

```

Post it here.

---

### Post by veeyes on 2008-01-11
Sorry for the delayed response. BUt, I am not even able to take a look at that hard-disk partition now. At boot-time, it says Partition Table invalid or corrupt!!!
I have no clue what to do now. I try to use GParted to delete that partition, and I can't do that either!!

---

### Post by veeyes on 2008-01-12
Thanks for all the help. I just reinstalled feisty on the disk.

VS

---

### Post by zvacet on 2008-01-12
If you,in future,feel like you want to upgrade to Gutsy do it with alternate CD.in that case you will allways have CD if something goes wrong(but it shouldn´t).

---

### Post by veeyes on 2008-01-13
Thank you very much for the response. But, even if i had the gutsy CD, I'd have to reinstall the OS after removing/backing-up all my data, right?
It would be awesome if there was a way to repair an existing installation! I couldn't find that option using the CD either!!
Although, I have been a big fan of Ubuntu, this issue has made me think about all that I have told people about Ubuntu :(

Thanks again,
VS

---

### Post by zvacet on 2008-01-13
> But, even if i had the gutsy CD, I'd have to reinstall the OS after removing/backing-up all my data, right?

If you think of upgrade answer is no,you don´t have to reinstall (back up date is allways O.K.).

> It would be awesome if there was a way to repair an existing installation! I couldn't find that option using the CD either!!

When you boot CD one of options is **Recover a broken system**.

---

### Post by veeyes on 2008-01-13
I didn't see a recover option!! Don't know why.
But, this time I am even more irritated. I reinstalled Feisty from scratch, and upgraded it to gutsy. Again, the problem remains. I am running ```
veeyes@vs-ubuntu:~$ uname -r
2.6.20-16-generic
```!!!
How on earth do I get rid of this problem?
I am sure this is going to come back and hurt me sometime later.
I did an upgrade using Synaptic and did NOT skip/change _anything_ there!

---

### Post by veeyes on 2008-01-13
Sorry to be so grumpy, but, I really can't understand this.
The only source I can see in my /usr/src/ is :
```
veeyes@vs-ubuntu:~$ ls /usr/src/
linux-headers-2.6.22-14  linux-headers-2.6.22-14-generic
```
But, when I boot, I _HAVE_ to boot only into 2.6.20-16!!!! What could be happening? I see that my grub's boot menu.lst has Ubuntu 7.10, kernel 2.6.22-14-generic! But, I don't see this at boot time!!!!
I am totally perplexed :(

---

### Post by zvacet on 2008-01-13
```
sudo gedit /boot/grub/menu.lst
```

Lok does this lines in your menu.lst looks like 

> ## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
# array will desync and will not let you boot your system.
default		0

and 

> ## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

If not change it.After that

```
sudo update grub
```

---

### Post by veeyes on 2008-01-13
Ahhh.. .After spending the whole night with it, I discovered just now that the grub menu.lst found in this partition is NOT the menu that shows up at boot-time!!! Have no idea why this is so. So, I just moved the menu.lst from this (Ubuntu Gutsy) partition to the other partition which has Ubuntu feisty on it, and now, it all seems to be fine.
But, that brings back the problem as to, should I manually copy the menu.lst file after every kernel upgrade? Why are there 2 versions of menu.lst? What did I do wrong???

Thanks a lot for all the help zvacet. I haven't looked up your last post, do you still want me to do that?

Thanks,
VS

---

### Post by zvacet on 2008-01-13
You can look,but no need to post if you solved your problem.Glad you are back.

---

### Post by veeyes on 2008-01-13
Just checked them, they are the exact same (upto that point atleast).
The big concern is why the grub menu.lst files are different in the 2 partitions I have. Should they not be the same???

Still, thank you very much for all the suggestions.

VS

---

### Post by doobydave on 2008-02-18
I think I have same problem.

No Gutsy kernel available within GRUB on boot.

Menu.lst seems updated in my gutsy partition, yet grub seems to be using one from a different partition (ubuntustudio install) which doesn't reflect the Feisty-Gutsy upgrade.

Is the bug documented on launchpad?

---

### Post by doobydave on 2008-02-21
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/grub/+bug/193098](https://bugs.launchpad.net/ubuntu/+source/grub/+bug/193098) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				I reckon I am probably talking to myself again but..............I have opened up a bug on launchpad about this.

[https://bugs.launchpad.net/ubuntu/+source/grub/+bug/193098](https://bugs.launchpad.net/ubuntu/+source/grub/+bug/193098)


Enjoy.

---

