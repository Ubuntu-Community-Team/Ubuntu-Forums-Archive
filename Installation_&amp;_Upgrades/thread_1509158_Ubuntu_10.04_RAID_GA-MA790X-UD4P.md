---
title: "Ubuntu 10.04 RAID GA-MA790X-UD4P"
date: 2010-06-13
forum: Installation &amp; Upgrades
---

### Post by sparks13 on 2010-06-13
My girlfriend has been fighting her computer since the day she built it to get it working with RAID. It has a Gigabyte GA-MA790X-UD4P motherboard with two separate built-in RAID controllers. She was able to eventually get RAID 1 working in Ubuntu 9.04. The upgrade to Karmic degraded her array.

10.04 has not helped things any. It recognizes she has a RAID array, but then has nothing listed at all when she attempts to partition the drives. It is as if she had no drives in at all. 

Ideally, she would be using RAID 5, but is willing to work with RAID 1. Google has been little help. Has anyone else had problems with a similar board? Any suggestions or ideas?

---

### Post by ronparent on 2010-06-15
First off for 10.04, it appears that at this stage, gparted will not be usable in partitioning a raid (ie the 10.04 live cd will be useless). Although for the installer, the partitioner will recognize raid partitions, I chose to use a prior version to prepare raid partitions for the install. At that point I was able to run a normal install with no problems. Be aware though that you will have to be careful in step 8 to select the 'advanced' box if you want to boot off the raid. Instead od a device (/dev/sda etc) you have to designate the raid root as the install point for the grub2 MBR. It will be a symbolic link found in /dev/mapper/ among the raid partitions. The root will be the one named without the ending partition numbers - ie /dev/mapper/<yourRaidArrayName> as opposed to /dev/mapper/<yourRaidArrayName>##.

Post if you have more questions. Although the so called fakeraid implementation is still problematic on 10.04, it can be set up and will work fine - especially on that Gigabyte board.

---

### Post by sparks13 on 2010-06-15
So I used the Jaunty alternate disc to partition the discs. I let it finish its install of jaunty rather than interrupting it. I then booted into the lucid alternate disc. It asks if I want to enable RAID and I say yes. Then it has no partitions/disks listed. My options are simply "Undo changes to partitions" and "Complete and write changes to disk" or something to that effect.

Thoughts or suggestions?

---

### Post by ronparent on 2010-06-15
My comments applied to using the 10.04 desktop version for installation. If anything, the alternate cd should be easier to work with?

I'm not familiar with the alternate cd partitioning scheme. In the desktop cd I would select manual partitioning and that is what would be most expedient if available. With manual partitioning you simply select the existing partition to install to - with formatting. As a matter of fact, if you have nothing on the raid disk you want to salvage you are basically working with a blank disk and can let it proceed using the entire disk to write to. 

However you proceed you need to remember to install the grub to the MBR of the root array if you have the 1st drive of the array selected as boot in bios. I probably need to know more about your drives and how you plan to use them and whether or not there is existing data you are trying to protect.

---

### Post by sparks13 on 2010-06-15
We are having an interesting issue with the LiveCD. When I boot her pc with it in, the first thing it does is give this error: "The installer encountered an unrecoverable error. A desktop session will now be run so that you may investigate the problem or try install again." I click ok and it boots the desktop/live version.

If I try to install then from the desktop, I get to the portion that I believe is where the partitioning normally goes and it gives this error:
"ubi-partman failed with exit code 10. Further information may be found in /var/log/syslog. Do you want to try running this step again before continuing? If you do not, your installation may fail entirely or may be broken." If I click "try again" the installer just hangs. If I click "continue anyways" it moves on to the user setup. Eventually I can try to set the disk the bootloader installs on, but the raid array is not an option. If I type it in manually, it will not let me continue.

This same cd works just fine in another machine.

---

### Post by ronparent on 2010-06-16
I have the almost identical model MB (GA-MA790GP-UDH4) and was apparently fortunate to have encountered none of that! The primary difference is that my MB has an on board ati graphics processor, which, I am not using. Have you tried running the live cd? It is good practice so that if for some reason your specific board requires a special boot parameter for it to boot you can apply it to enable a live cd session and install from there. Also what are your graphics processor and raid chipset? 

Unpleasant though it may seem, it may be necessary to sort through what is needed to successfully run Ubuntu 10.04 on your setup before you even think about running raid. I am sure that if that can be sorted out you should be able to install to a raid.

---

### Post by darkod on 2010-06-16
Can it be that Lucid alternate cd is not recognizing the controller properly (drivers)?

Even for 10.04, the recommendation to use alternate cd for RAID installation remained as far as I know. So the best shot is using the alternate cd.

It's strange not giving you options to partition the disks. What if you select complete and write changes to disk?

Another note, will you be using windows on that raid also? Because only in that case you need to use the fakeraid of the board. For using only ubuntu, it's much better to disable the board raid and use the alternate cd and set up software raid.

---

### Post by ronparent on 2010-06-16
I should have thought of this before, except I didn't need it for 10.04. Look at this: [https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)

That reference will guide you through either the desktop or alternate install.

---

### Post by sparks13 on 2010-06-16
ronparent:
If you read my last post, you'll notice I did try the LiveCD. Also, Ubuntu 10.04 works just fine if you don't use RAID. I have referenced the FakeRaidHowto documentation. Which RAID controller are you using on your motherboard? We have been trying both the AMD SB750 controller and the Gigabyte controller.

darkod:
I am used to the alternate cd being the better installer of the two. It recognizes there should be RAID, but definitely is not seeing it correctly. When I tried the "complete and write changes to disk", it simply hangs at a blank screen. This is intended to be a dual-boot system.

I think that answers everything.

---

