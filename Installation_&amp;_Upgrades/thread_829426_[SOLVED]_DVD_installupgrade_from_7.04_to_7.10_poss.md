---
title: "[SOLVED] DVD install/upgrade from 7.04 to 7.10 possible?"
date: 2008-06-14
forum: Installation &amp; Upgrades
---

### Post by upchucky on 2008-06-14
I have 7.04 on i386 pc, i want to know if i can upgrade to 7.10 using the dvd from Linux magazine instead of downloading from repositories.

Can i set ubuntu to look to the dvd for the files, and if so what commands would i need to use.

if i cant do that, is it ok to just install 7.10 as if linux was not even on the pc?

---

### Post by Pumalite on 2008-06-14
To upgrade you need the Alternate CD:
[http://www.ubuntu.com/getubuntu/upgrading](http://www.ubuntu.com/getubuntu/upgrading)

---

### Post by upchucky on 2008-06-14
dang I was afraid someone was gonna say that, i am trying to find a way to not do the downloads, my download file size is restricted by my isp.

what i really want to do is find a way to upgrade/install 7.10 from the Dvd without messing up my beryl and display settings.

---

### Post by Pumalite on 2008-06-14
If you have a separate /home partition; you can do it. And if you don't have one; you can make one:
[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

You need to backup everything prior to the operation.

---

### Post by upchucky on 2008-06-14
I do have a /home/electric partition, and the file "electric" has all my personal data on it.

so if i understand right i can just install using the 7.10 dvd and it should not mess my settings or files?

do i do custom install and not let it create a home partition since i have one already? how does it know to use my existing home partition?

---

### Post by avtolle on 2008-06-14
I agree; create a separate /home partition using the guide Pumalite has linked. Careful, and be sure to back up before beginning. If this is successful, then and only then, use the DVD you have to do a fresh install (be aware it is the Live version, I don't recall if this was a problem before). When it gets to partitioning, use the manual option, and (what I do) format the / partition to clean it up, and then install the OS to that partition (it is fairly self-explanatory). If everything works, you will have a 7.10 install with your settings saved. Beware of a problem with 7.10; it did not recognize IDE drives correctly, and you may need to do some tweaking of the boot paramaeters to get booted (F6, add "all-generic-ide" without the quotation marks, then b for boot). Try without this first, of course. I think you will have a potful of updates to contend with, so to download them, again set the alarm.

---

### Post by avtolle on 2008-06-14
In the installation process, don't touch your /home partition (nor your existing /swap partition); the system will know to use the existing ones.

---

### Post by upchucky on 2008-06-15
tis a sad day, I am using win xp to get onto the forums to type this.

I did get upgraded to 7.10 using the dvd, hadda do it twice tho, for some reason the upgrade ejected the dvd halfway through the first time. but the second time it went very well, no errors.

the only way to get the dvd to do the upgrade was to boot the pc then put the dvd in the drive and hunt down a dist upgrade script that only shows up this way, if u use the dvd as a live boot/then try to install, it wants to do a clean install instead of a upgrade.

the upgrade borked my beryl install tho, but i can live without that.

now the reason i am using win xp to type this is because after the upgrade, when i use firefox to go on forums and type something, everytime i press the spacebar, the period, the backspace, or the return keys. firefox shuts down.

so far this is only happening in firefox on the ubuntu forums i will try another forum and post the results.

typing in office or other medium is fine.

---

### Post by upchucky on 2008-06-15
very nice, I did the update packages again, (not the upgrade dist) and now everything seems to be ok, except for beryl, someday when i feel really energetic and dont have a root canal to get done i will redo beryl.

Many thanks to everyone that offered help, i will pass on knowledge when i can.

---

