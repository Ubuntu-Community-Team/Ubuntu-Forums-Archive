---
title: "Botched Hardy-Lucid Upgrade on Dual-boot XP-Hardy Machine"
date: 2010-05-20
forum: Installation &amp; Upgrades
---

### Post by mlnease on 2010-05-20
Hello All,

I've posted this on the 'Share with the community" thread, so I hope I'm not overstepping by posting it here too.

I'm now upgrading my SO's machine from Hardy to Lucid and I've run into a  couple of problems.  It's a bit complicated; hope it's OK to post them  here.

Problem 1:  My SO's machine is--or was--set up to dual boot XP and  Hardy.  When she decided she wanted an upgrade, she downloaded the .iso  and installed it, thinking that she was upgrading.  Aside from some  serious graphic problems with this installation, it didn't--of  course--import any of her data.  She thought she'd lost her old settings  and a few unbacked up files but instead she'd  installed--apparently--Lucid alongside Hardy *and* XP.  Attached is  what her GRUB screen looks like now (apologies for the image quality).

I am entirely ignorant of partitions/partitioning so I decided to first do a proper  upgrade via update-manager --devel-release, which has been going fine  for the last fifteen hours (by way of Comcast's blistering 0.24 Mbps  cable DSL), then deal with the extra install.  With a little over an hour to go, I ran across this, while  researching how to get rid of the extra (and faulty) Lucid:

"Warning: Ubuntu Desktop edition installer no longer allows a  custom  installation of GRUB, and it now uses GRUB2 (which allows very  little  customization). DO NOT USE the Lucid Lynx Desktop edition if you  use a  boot partition, use multiple OS (more than 2), or chainload   bootloaders. The Ubuntu installer will overwrite your Master Boot Record   and you will later be forced to recreate it manually. This is a  serious  flaw in both Karmic Koala and Lucid Lynx. Use the Ubuntu Server  edition  instead (and then later add the ubuntu-desktop).  GRUB2 has  caused major problems in installation -- be sure to  research the issue  before upgrading to Lucid Lynx."

 [http://ubuntuguide.org/wiki/Ubuntu:Lucid](http://ubuntuguide.org/wiki/Ubuntu:Lucid)

Problem 2:  So now I have the problem of "multiple OS (more than 2)" and  am researching the issue before finishing the upgrade.  What I would  like to do, of course, is delete the unwanted Lucid(s?) and use the  space(?) for the proper Hardy-Lucid upgrade.  Assuming I'm able to  delete? uninstall? the superflous Lucid(s), should I go ahead with the  upgrade despite the 'serious flaw' with GRUB2?  I am at a loss as to how  to proceed.  Any advice would be greatly appreciated.

Thanks in Advance,

mike

p.s.  It's very important to my SO to keep the MS OS, unfortunately.

---

### Post by labinnsw on 2010-05-22
I actually managed to successfully upgrade from Hardy to Lucid but after the upgrade, though everything worked, almost nothing worked as it should.

I do regular backups, so since there were so many things to fix, I simply reinstalled Lucid overwriting the upgrade, restored my home directory, and re-installed my favorite applications. It took me a lot less time than it would have taken to work through the issues.

This is not the usual way to fix stuff but, considering the wide precipice between Hardy and Lucid, I believe this is one time when this option should get some serious consideration.

Since you already have Lucid installed, you can just copy Hardy home to the Lucid, then after carefully checking that it all went well, use the live cd and Gparted to make Lucid partition larger and delete the Hardy partition.

I always stress, backing up never hurts, but after performing similar operations (both on Windows and Linux) using the live cd and Gparted I have never encountered a hitch.

---

### Post by mlnease on 2010-05-22
Thanks for this.  There's nothing in Hardy we can't live without, but at present the Lucid install is pretty much useless--open/close buttons don't work etc.  

I can search for Gparted tutorials and probably figure out how to expand the Lucid partition and delete the Hardy.  But I think at the moment the important thing is to first get rid of the bad Lucid, taking great care not to disturb the user's MS partition.  Did you have a look at my screenshot?  Is this something I should be able to figure out using Gparted?

Thanks again for your reply and for your invite to the Gnome user's group--see ye there.

mike

---

### Post by kansasnoob on 2010-05-22
So, the upgraded Hardy to Lucid and XP are both working well?

If yes please post a screenshot of Gparted. If installed it's in System > Administration, but it's not installed by default. You can install either using Synaptic or from Terminal run:

```
sudo apt-get install gparted
```

The screenshot tool is in Accessories and you can use the paper clip thingy in these reply windows to attach it.

NOTE: Do not try to use the "installed" version of Gparted for repartitioning! You'll want to use Gparted from the Live CD for that.

---

### Post by labinnsw on 2010-05-22
> **mlnease said:**
> Thanks for this.  There's nothing in Hardy we can't live without, but at present the Lucid install is pretty much useless--open/close buttons don't work etc. 

In that case insert the live cd and reboot. Then do a fresh Lucid install.

When you get to the partitioning portion of the install process, select manually partition. From there it will be easy to figure out which partitions are Windows and swap. Delete the other partitions and use the freed up space to install Lucid.

> **mlnease said:**
> I can search for Gparted tutorials and probably figure out how to expand the Lucid partition and delete the Hardy.Gparted is extremely user friendly and you will most likely not need to do any reading to figure it out. [I did post something on Youtube]("http://www.youtube.com/watch?v=NefYp80dUkY") that you can have a look at but it does not cover all the areas that you will be applying. You can maybe find some others.

> **mlnease said:**
> But I think at the moment the important thing is to first get rid of the bad Lucid, taking great care not to disturb the user's MS partition.  Did you have a look at my screenshot?Yes
  
> **mlnease said:**
> Is this something I should be able to figure out using Gparted?Yes

One more thing, when you have installed Lucid, install Start up manager. Use start up manager to set you default OS.

---

### Post by mlnease on 2010-05-22
Thanks for the reply, KN:
> **kansasnoob said:**
> So, the upgraded Hardy to Lucid and XP are both working well?

If yes please post a screenshot of Gparted. If installed it's in System > Administration, but it's not installed by default. You can install either using Synaptic or from Terminal run:

```
sudo apt-get install gparted
```The screenshot tool is in Accessories and you can use the paper clip thingy in these reply windows to attach it.

NOTE: Do not try to use the "installed" version of Gparted for repartitioning! You'll want to use Gparted from the Live CD for that.
 
No, actually Lucid is useless--open/close buttons don't work, cursor is misplaced, screen reso is wrong etc.

Thanks, I have Gparted and of course Screenshot.  I took a screenshot on the affected computer but lost the transfer thanks to the faulty GUI.  I'll give it another try and get back to you when my inamorata relinquishes her machine again.  I did use the Gparted from the Live CD; this also has major GUI problems, interestingly, though not so major as those on the faulty installs.

Thanks again for your attention and patience, I will get back to you.

mike

---

### Post by mlnease on 2010-05-22
> **kansasnoob said:**
> So, the upgraded Hardy to Lucid and XP are both working well?

If yes please post a screenshot of Gparted. If installed it's in System > Administration, but it's not installed by default. You can install either using Synaptic or from Terminal run:

```
sudo apt-get install gparted
```The screenshot tool is in Accessories and you can use the paper clip thingy in these reply windows to attach it.

NOTE: Do not try to use the "installed" version of Gparted for repartitioning! You'll want to use Gparted from the Live CD for that.
OK KSN,

Here's the screenshot--thanks again.

---

### Post by mlnease on 2010-05-22
> **labinnsw said:**
> In that case insert the live cd and reboot. Then do a fresh Lucid install.
OK--
> When you get to the partitioning portion of the install process, select manually partition. From there it will be easy to figure out which partitions are Windows and swap. Delete the other partitions and use the freed up space to install Lucid.OK--
> Gparted is extremely user friendly and you will most likely not need to do any reading to figure it out. [I did post something on Youtube]("http://www.youtube.com/watch?v=NefYp80dUkY") that you can have a look at but it does not cover all the areas that you will be applying. You can maybe find some others.I'm downloading your Youtube video as I type.  Looking forward to it.
> Yes  Great--
> YesGreat--
> One more thing, when you have installed Lucid, install Start up manager. Use start up manager to set you default OS.Interesting--I didn't know I could select the default OS in StartUp-Manager.  Thanks for the tip and for all your help.

I'll let ye know how it all works out.

mike

p.s.  Great Youtube tutorial, thanks again.

---

### Post by mlnease on 2010-05-23
So, according to my GParted screenshot, partitions /dev/sda1 and /dev/sda2 contain MS OS, and /dev/sda3 contains Hardy?  Is this correct?  So I should be able to delete /dev/sda4 and use the freed up space to (re)install Lucid?  If I do this before deleting /dev/sda3 (I'd like to do it in this order in order to copy Home from Hardy to  Lucid and make sure Lucid's up and running before deleting the Hardy  sector.), do I need to worry about the GRUB2 problem described at [http://ubuntuguide.org/wiki/Ubuntu:Lucid](http://ubuntuguide.org/wiki/Ubuntu:Lucid)?  I'm definitely not ready to overwrite--and later be forced to recreate--my Master Boot Record manually.

Thanks again for your time and patience.

mike

---

### Post by labinnsw on 2010-05-24
> **mlnease said:**
> So, according to my GParted screenshot, partitions /dev/sda1 and /dev/sda2 contain MS OS, and /dev/sda3 contains Hardy?  Is this correct?  So I should be able to delete /dev/sda4 and use the freed up space to (re)install Lucid?All correct. You can also delete one of the swap partitions. Any Linux system you install will use the remaining swap partition. 

> **mlnease said:**
> If I do this before deleting /dev/sda3 (I'd like to do it in this order in order to copy Home from Hardy to  Lucid and make sure Lucid's up and running before deleting the Hardy  sector.), do I need to worry about the GRUB2 problem described at [http://ubuntuguide.org/wiki/Ubuntu:Lucid](http://ubuntuguide.org/wiki/Ubuntu:Lucid)?  I'm definitely not ready to overwrite--and later be forced to recreate--my Master Boot Record manually.This is a legitimate concern. According to the article installing Lucid will overwrite the MBR. That has already been done. If it has not been done, (eg. If Lucid install did not get to that stage yet) it will be when you install Lucid. I still recommend 
1. backing up the Home directory or Entire Hardy to an external device. 
2. If things go Hay-wire, use the live cd to reformat your linux partition to ext3
3. Reinstall hardy and restore the Home or the entire Hardy system.

I have attached my backup instructions. (Which can also be used to back up Windows)

---

### Post by mlnease on 2010-05-24
> **labinnsw said:**
> All correct. You can also delete one of the swap partitions. Any Linux system you install will use the remaining swap partition. 

This is a legitimate concern. According to the article installing Lucid will overwrite the MBR. That has already been done. If it has not been done, (eg. If Lucid install did not get to that stage yet) it will be when you install Lucid. I still recommend 
1. backing up the Home directory or Entire Hardy to an external device. 
2. If things go Hay-wire, use the live cd to reformat your linux partition to ext3
3. Reinstall hardy and restore the Home or the entire Hardy system.

I have attached my backup instructions. (Which can also be used to back up Windows)
Thanks as always, especially for the excellent backup instructions.  I doubt that the user will OK the upgrade until she has been able to backup her MSOS, for which I think she presently lacks the necessary hardware.  When/if she gives the go-ahead, I'll follow your instructions and post the results here.

I can't thank you enough for your time and attention.

---

