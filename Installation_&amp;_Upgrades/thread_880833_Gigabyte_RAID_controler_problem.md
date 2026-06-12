---
title: "Gigabyte RAID controler problem"
date: 2008-08-05
forum: Installation &amp; Upgrades
---

### Post by timbim on 2008-08-05
Sorry to post here, but I thought someone might have the answer.  I have a Gigabyte GA-MA770-DS3 mobo with onboard SATA RAID controller.  I have two 250GB Seagate Barracuda HDD's, and wish to set them up in a RAID1 setup.  I ran my Hardy Heron LiveCD before installing anything, so as to check that the system runs fully.  It did, before trying to setup the RAID from BIOS.  I set it to have the two disks in a RAID1 setup.  After doing this, the system failed to boot.  It managed its Power On Self Test, the RAID controller checked the drives, but the system then grinds to a halt, wanting to boot off a CD, but not responding to the LiveCD it previously accepted! ](*,)

Any ideas how to go on from here, or am I just going to have to forget about RAID?

---

### Post by dstew on 2008-08-05
You can install Ubuntu onto a RAID, but you have to modify the installation process a lot. That is because the Linux operating system on the Live CD in its native state does not recognize RAIDs. You can get the Live CD OS to recognize a RAID by installing (onto the running Live CD system) the **dmraid** program. After that, at least the Linux OS will be able to recognize the RAID, and you can create partitions and copy files to it. Unfortunately, the installer program itself still will not work properly, because it is written only for installing to an un-RAIDed disk. You can get around this problem by installing all the parts of Ubuntu desktop, including grub, "by hand". The instructions on how to do this are in the [FakeRAID HowTo]("https://help.ubuntu.com/community/FakeRaidHowto").

If you want to install to a software RAID instead of a partly hardware RAID like you seem to have, you can use the Alternate Install CD. It has menu items for creating and installing on a soft RAID. The one drawback is that you will have to put grub onto an un-RAIDed partition, or perhaps a mirrored RAID like RAID-1, because grub cannot see software striped RAIDs. Grub does work on a FakeRAID if installed correctly.

---

### Post by timbim on 2008-08-05
Sorry, I understood very little of that.  I have hardware RAID support, if possible I would like to use it to avoid problems caused by totally software-based RAID to avoid too much strain on my HDD's and processor.  Can I use the hardware RAID or do I need to use a workaround?

---

### Post by redraiderbum on 2008-08-05
> Sorry, I understood very little of that. I have hardware RAID support, if possible I would like to use it to avoid problems caused by totally software-based RAID to avoid too much strain on my HDD's and processor.

Unfortunately, with virtually all mobo onboard raid controllers this probably isn't true.  Most integrated raid controllers actually unload all of the processing to the cpu so they are known as 'fake raid'.  That is, the controller itself is essentially just a dedicated software raid appliance of a sort.  

IMHO, the easiest way to do a raid setup with ubuntu is to either get a stand alone hardware raid controller.  This means the OS won't even know there is more than one HDD.  Personally, I find this option too expensive, as the hardware raid controller are generally more than $100.  I suggest using either the alternate install disk or the server install disk to setup a software raid then install to that created volume.  I prefer the server install, after the server install is complete you will only have a command line so to install the full ubuntu gui you would login in and use this command:

sudo apt-get install ubuntu-desktop

Just for clarity, it is often very difficult to determine if a card you buy is actually a hardware or software raid controller until you have it in the computer.  Thing that are based on silicon images or nvraid's require drivers that run at the OS level to work.  Most mobo's are of these kinds and considering most drivers are written for windows it is difficult to use these controllers in linux.  You can, however, use them as simply extra sata ports and software raid them.

---

### Post by timbim on 2008-08-05
Could you link me to a set of instructions on how to use the alternate setup disk to recognise the array?

---

### Post by redraiderbum on 2008-08-05
I think I wasn't clear.  The alternate disk won't recognize the array through the mobo, it will allow you to make a software raid array so you can then install ubuntu to the array.  The standard install disk does not allow you to create a software raid then install ubuntu to the array.

Here is a how to if you would still like to use a 'fake raid' (that is not a disparaging comment it is just what that type of setup is called).  This will take you through the process of using the onboard controller:

[https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)

Here is the process I would use.  It runs everything through ubuntu's LVM and it is also a software raid.

[https://help.ubuntu.com/community/Installation/LVMOnRaid](https://help.ubuntu.com/community/Installation/LVMOnRaid)

Those docs might say you should use Ubuntu 6.x, just ignore that.

Here are all of the community install docs if you want more info:

[https://help.ubuntu.com/community/Installation](https://help.ubuntu.com/community/Installation)

Hope this helps.

---

### Post by dstew on 2008-08-05
You may have misunderstood me. There are two main types of RAID. There is software-assisted hardware RAID, or FakeRAID, which uses a controller with BIOS extensions like you have. Then there is pure software RAID, which does not require a RAID-enabled controller. You have to decide which type of RAID you want to use.

If you want to use FakeRAID, which is what you were talking about first, then you need to install with dmraid, as described in the HowTo. If you want to use software RAID, there is nothing to "recognise", because the array is a construct of the operating system. If you want to install to a softRAID, you need to disable the RAID setup in your BIOS, so that the controllers present the disks to the OS as plain old separate disks. Then you create the softRAID using the OS software, and manage it with the mdadm program.

[Here]("http://advosys.ca/viewpoints/2007/04/setting-up-software-raid-in-ubuntu-server/") is a tutorial that seems to be pretty good about how to install to a software RAID using the Alternate Install CD. It was written for 6.06, but I am pretty sure the same method can be used with 8.04.

---

### Post by timbim on 2008-08-05
Thanks for all the support, I was on at Gigabyte's tech support earlier, they were about as much use as a chocolate teapot, telling me that the system not booting was not their problem.  I think that I'll go with a software RAID, as fiddling in BIOS is what put me in this mess in the first place.

Once again, thanks all!

---

### Post by timbim on 2008-08-06
I have set up partitions for swap, / and /boot; and then one partiton on each device for RAID.  However, once I have installed fully, the capacity is not there.  How do I rescue the capacity?

---

### Post by timbim on 2008-08-06
Bump.  I'm not going to get a response on page 2.

---

### Post by dstew on 2008-08-06
What do you mean by "the capacity is not there"? As I remember, when I installed a softRAID system, you make a bunch of partitions the same size, and group them as a RAID. Then, you make partitions out of the RAID. The total RAID capacity is usually that of a single partition, because the RAID is redundant. If you want a big partition that is non-redundant, combining parts of many disks, you want to use Logical Volume Management (LVM) and not RAID.

---

