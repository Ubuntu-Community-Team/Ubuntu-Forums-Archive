---
title: "Creating RAID-1 with only 2 Drives"
date: 2010-06-27
forum: Installation &amp; Upgrades
---

### Post by deba on 2010-06-27
Hi,

I have recently installed a Asus M4A77TD Pro system board which supports raid.

I have 2 x 320gb sata drives I would like to setup raid-1 on.
so far i have configured the bios to raid-1 for drives, but when installing Ubuntu 10.04 from the cd it detects the raid configuration but fails to format.

When I re-set all bios settings to standard sata drives ubuntu installs and works as normal but i have just 2 x drives without any raid options. I had this working in my previous setup but thats because i had the o/s on a sepreate drive from the raid and was able to do this within Ubuntu. 

I suspect the problem is one related to drivers?

---

### Post by zuuul on 2010-06-28
Hello deba, you will need the alternate ubuntu install disk for setting up raid during installation. In the partition manager, there is an option of linux software raid, which is what you want. Its a little tricky first time, but there are manuals to be found about setting it up.

Also, you should not use the bios raid, because linux doesn't use it, as far as i know. The disks should just be in normal ide or ahci mode.

Hope it helps you some of the way.

---

### Post by darkod on 2010-06-28
> **zuuul said:**
> Hello deba, you will need the alternate ubuntu install disk for setting up raid during installation. In the partition manager, there is an option of linux software raid, which is what you want. Its a little tricky first time, but there are manuals to be found about setting it up.

Also, you should not use the bios raid, because linux doesn't use it, as far as i know. The disks should just be in normal ide or ahci mode.

Hope it helps you some of the way.

If you plan to dual boot on the raid1, you have to use the fakeraid function (the mobo BIOS raid). In that case you still use the alternate install cd but that is NOT software raid.

If you plan to use only ubuntu, disable raid in BIOS and again use the alternate install cd and set up software raid, it has better performance according to some.

---

### Post by ronparent on 2010-06-28
deba: You don't say which version of Ubuntu you are using. I have found gparted useless in partitioning a raid in 10.04. And although the partitioner in the 10.04 desktop installer will recognize a raid, it doesn't appear capable of formatting a raid drive! I have experienced partitioning failures in trying to prepare a raid partition as a target within the install. However when I prepared a blank formatted raid partition with a pre 10.04 version and selected it as the target for / without formating during installation everything proceeded without error (and I am now using it). I've stated this before and no one is listening so problems are continuing.

Whatever version you use prior to 10.04, dmraid must be installed to either an install or the live cd session. Within gparted you must select the raid(1,2,5,etc) array withing which you want to create the intended target partition in whichever format you intend to use for the install. When you run the install, you must select the target you created for / and deselect the format box (you could have added additional partitions for /home, /boot, etc.). Swap is not a problem because it is not formatted. Lastly, if you intend to boot from the raid, in the step 8 install screen, select the advanced block, and within that pop up write in the symbolic link for your entire raid array (not any of the individual partitions) - written in the format '/dev/mapper/<YourRaidRootArray>'. Remember it from the partitioning step above -it is the raid drive wihtin which you created the target partition above in this post. Presuming you are installing the 10.04 desktop, follow these instructions exactly and you should have no problems.

---

