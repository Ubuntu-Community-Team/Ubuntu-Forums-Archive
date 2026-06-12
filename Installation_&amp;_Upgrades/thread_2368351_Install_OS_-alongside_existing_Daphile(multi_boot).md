---
title: "Install OS -alongside existing Daphile(multi boot)"
date: 2017-08-09
forum: Installation &amp; Upgrades
---

### Post by alexander46 on 2017-08-09
Hey,
there is Daphile installed on my eee Pc and i would like to dualboot this computer now with e.g. elementary OS or Kubuntu.

The Installation.pdf for Daphile mentions a section that explains a possibilty to do so, but m afraid i could use some extra help with that...

Many thanks in advance!


[could it be possible to make the MusicStorage partition shared to be seen by the upcoming OS as a shared folder?]

---

### Post by oldfred on 2017-08-10
Never heard of Daphile, but it looks like it is Linux based.
They mention both msdos & gpt partitioning and install of grub boot loader.

Download Kubuntu and install ISO to flash drive and boot to see that it works.
Then from terminal post this. (you may be able to do this from Daphile?)

sudo parted -l

---

### Post by alexander46 on 2017-08-15
Hey there,
i just installed elementary os 0.3 Freya 32-bit next to daphile on my eee pc.

I chose an installation without internet connection. While choosing custom installation i was asked to partition.
There i saw:
sda1-1.1GB 
sda2-319GB

no flags were mentioned here. (actually the sda1 is the boot partition for daphile and the sda2 is the home space)

Then i cut 20GB and called it /boot, it was designated sda5,
another 100GB was called /home and got designated sda6.

All questioned i answered with yes.

The installation was successful my netbook then only boots into elementary.
There is no gedit or kate, only scratch. 
sudo scratch /etc/default/grub didnt work.
Typing in only 'scratch' into the terminal will give: scratch is currently not installed.... (i had no internet at this point),
so i chose to go to the grub file myself and press 'open with terminal', from there i could successfully edit ***[just # the timeout] ***the grub file.
Then i did sudo update-grub.

But still grub shows me only elementary, whereas the elementary file manager shows me next to my file system another filesystem called DaphileBoot 1GB.


> sudo parted -l

1  size:1074mb type: primary ext4 flag:boot
2 size 199gb primary ext4
3 120gb extended
5 20gb type: logical ext4
6 100gb logical ext4

only 1 has a flag here


Update:
i just followed this guide but failed [https://forum.peppermintos.com/index.php?topic=3396.0](https://forum.peppermintos.com/index.php?topic=3396.0)
There is a entry called daphile in grub now, but it gives
> error: hd1 cannot get C/H/S values.
then it goes back to grub...

Edit:
Solved it, same as in the guide, the declaration was hd0,1

---

### Post by oldfred on 2017-08-15
Glad you got it working.

I normally suggest with most desktops not to have a separate /boot partition. It may be required with servers, LVM or full drive encryption. 
You cannot share a /boot, so for every install you would need another /boot and then another partition to manage space/utilization on.

---

