---
title: "Booting Stalls at 'mounting root' Solutions Detail Thread"
date: 2006-07-10
forum: Installation &amp; Upgrades
---

### Post by dtragcoen on 2006-07-10
**This thread specifically covers issues with the Installation from CD freezing or getting stuck for a time while attempting to mount the root filesystem!**

Do not post solutions related to the drives being incorrectly recognized (and therefore freezing at normal boot) after an upgrade from a previous linux environment. That problem is covered already with multiple solutions. Refer to [http://www.ubuntuforums.org/showthread.php?t=187656](http://www.ubuntuforums.org/showthread.php?t=187656)
under the section 'booting stalls during "mounting root filesystem"? for some of those solutions.

This post is extended from the thread located here:
[http://www.ubuntuforums.org/showthread.php?t=186115](http://www.ubuntuforums.org/showthread.php?t=186115) as of the post [http://www.ubuntuforums.org/showpost.php?p=1237241&postcount=155](http://www.ubuntuforums.org/showpost.php?p=1237241&postcount=155)
Go there to ask questions about the issue or about similar issues.
The most thorough post detailing solutions to this problem is here:
[http://www.ubuntuforums.org/showpost.php?p=1088366&postcount=11](http://www.ubuntuforums.org/showpost.php?p=1088366&postcount=11)

Go to
[http://www.ubuntuforums.org/showthread.php?t=187656](http://www.ubuntuforums.org/showthread.php?t=187656)
under the section 'booting stalls during "mounting root filesystem"?'
for information relating to solving this and similar issues.

Post solution data for the Desktop BootCD hanging at 'mounting root filesystem' only!

[SIZE="3"]**DO NOT**[/SIZE] post questions about your problem here, UNLESS you solve it. This thread was created to reduce the amount of reading through the original thread in order to make analysing the problems and the correct solutions easier for those who haven't yet solved it.

If you do solve it
--------------
Then please come back and post as much of the following info as you can-
Specific hardware info as stated here: [http://www.ubuntuforums.org/showthread.php?p=1086319](http://www.ubuntuforums.org/showthread.php?p=1086319)
Especially relating to ALL drives and drive controllers including USB flash and optical drives connected. Also post all USB devices - some contain hidden flash drives and other mechanisms that you don't see, but linux might. My usb mouse contains an onboard flash drive for firmware, for example.

Also, plz mark the numbers below corresponding to any degree of success when taking the notes in order to speed up compilation of the results.

0. If waiting solved the problem, note that down. It seems that sometimes the problem can sort itself out over time.

1. If you have media devices connected via USB (hard drives, cd-drives, usb-flash drives, etc) and have the issue, post whether disconnecting those media devices solved it.

2. If otherwise and disabling USB2.0 or all USB devices solved it, post that information. - Many of you may have a spare PS2 keyboard or mouse somewhere, don't feel afraid to use that for the install. Afterward, you should be able to switch back completely.

3. If changing the cd/dvd drive you installed the media from solved the problem, please mention this. Also, I reiterate, if you know them, post the models of the drives, both the one that worked and didn't, and where they were located (hdc, hdd, hda, etc)

4. If special boot options solved your problem (refer to suggested ideas in Adament's post - link above) Note down which boot options AND I reiterate the hardware configuration at the time. The following boot options are noted in Adament's post:
irqpoll
noapic
nolapic
acpi=off pci=noacpi noacpi
ide=nodma

5. If none of the above worked, but patrick's solution worked, note that.

6. If you used the Alternate Install CD instead, please note that. At least we can see the hardware that prevented you from successfully using the Desktop Install CD.

X. Lastly, if none of these worked, it's probably a different issue, but leave a post with details about it. You may have a new problem, or lead to a new solution.

Thank you for your contribution.

---------------------------------------------------

Note to Mods. Due to the length of this thread and the prevalence of the issue I started this thread for solution responses solely to this issue. Because all of the solutions to this will be gathered from different sources, (different users) it should make updates to Adament's post simpler. However, it would be impractical to try placing this all in multiple posts in the installation solutions thread at [http://www.ubuntuforums.org/showthread.php?p=1086319](http://www.ubuntuforums.org/showthread.php?p=1086319). It's already becoming disjointed with bits and pieces relating to similar issues. I intend the results of this to be compiled as one post from time to time, rather than thrown together haphazardly.

Also, this way the questions and solutions don't get continually rehashed one-upon-the-other as much. It should make your job much easier.

---

### Post by ubuntu_demon on 2006-07-13
I've added a link to this thread here :

Having problems with installing or upgrading to Dapper? Here are some fixes 
[http://www.ubuntuforums.org/showthread.php?t=187656](http://www.ubuntuforums.org/showthread.php?t=187656)

The devs know about this bug and we might see a dapper-update someday. See this thread :
[http://www.ubuntuforums.org/showthread.php?t=208207](http://www.ubuntuforums.org/showthread.php?t=208207)

The bug is definetely related to udev enumeration. Some percentage of people with certain hardhare and/or certain combinations will have this problem. So it's probably quite hard (or undo-able) to make a list of when you will have problems and when not. I'm not sure whether this will help the devs because they have already pinpointed the problem.

---

### Post by ubuntu_demon on 2006-07-14
**Everyone please test this general workaround :**

[https://launchpad.net/distros/ubuntu/+source/udev/+bug/6367/comments/69](https://launchpad.net/distros/ubuntu/+source/udev/+bug/6367/comments/69)

[quote=Paul Sladen]
For those still wondering; The workaround for this issue involves specifying the partition to boot from by ID, rather than the transient location:

  1. Boot a desktop/LiveCD.
  2. Run sudo /sbin/dumpe2fs /dev/sdX | grep UUID
  3. tell 'grub' or 'lilo' to boot with that ID:

     linux ... root=UUID=d4c51a2a-d93f-4dc1-8717-9c3cdb4d41ce

and also adjust this in:

  /boot/grub/menu.lst
[/quote]

Replace sdX for sda, sdb, sdc, sdd, hda,hdb,hdc,hdd or whatever gparted on the livecd tells you it is.

You can post results either on launchpad here :
[https://launchpad.net/distros/ubuntu/+source/udev/+bug/6367/](https://launchpad.net/distros/ubuntu/+source/udev/+bug/6367/)
Or in this thread :
[http://ubuntuforums.org/showthread.php?p=1257154](http://ubuntuforums.org/showthread.php?p=1257154)

---

### Post by ubuntu_demon on 2006-08-17
From [https://launchpad.net/distros/ubuntu/+source/udev/+bug/6367/](https://launchpad.net/distros/ubuntu/+source/udev/+bug/6367/) :

[quote=Scott James Remnant]
Officially marking as Rejected for dapper.

Here is the reasoning:

- We applied the &#8220;fix&#8221;, as planned, to the udev in Edgy Eft.

- While the fix corrected the problem described here, it caused new problems. Because it was a fundamental change to device ordering, it changed the order of other devices where more than one existed in the system &#8212; including other disks

- For Edgy this was not a problem, as the upgrade makes other changes that make device order non-important anyway

- These changes are too invasive for backporting to dapper

- This bug has a known workaround, which can be applied by the minority of users affected by it

- That workaround is preferable to causing far more working systems to cease functioning.
[/quote]

---

### Post by Lord Erik on 2006-08-18
"- These changes are too invasive for backporting to dapper

- This bug has a known workaround, which can be applied by the minority of users affected by it:

It would be helpful if it specified what the workaround was.  I've tried several now and none work.  I'm getting to the point where I might have to go buy a copy of windows so I can use my computer.

---

### Post by ubuntu_demon on 2006-08-22
Here are workarounds (which need testing) :
[http://ubuntuforums.org/showthread.php?p=1257154](http://ubuntuforums.org/showthread.php?p=1257154)
[https://launchpad.net/distros/ubuntu/+source/udev/+bug/6367/comments/83](https://launchpad.net/distros/ubuntu/+source/udev/+bug/6367/comments/83)

---

### Post by rpradeep on 2006-11-28
I am using a HP visualize X Class 1GHz workstation and Samsung SH-D162C DVDROM.

Firstly My computer halt at mounting root filesystem and refused to go further. Then I changed the Firmware of DVDROM from TS04 to TS01 then it worked after several Buffer I/O error (ie only delayed the booting)

This also make delays in openning the DVD drive when new CD is inserted on Ubuntu desktop (after installation).

Recently I changed back my Firmware and changed the BIOS settings as follows.

In that i changed the IDE for my cdrom setting from AUTO to CDROM
and disabled UDMA.

Now it's working fine for me.

---

