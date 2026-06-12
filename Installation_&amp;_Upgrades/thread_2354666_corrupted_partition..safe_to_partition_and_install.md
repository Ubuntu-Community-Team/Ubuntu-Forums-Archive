---
title: "corrupted partition..safe to partition and install ubuntu alongside W7?"
date: 2017-03-05
forum: Installation &amp; Upgrades
---

### Post by ooten on 2017-03-05
Greetings and thank you for taking the time to read and hopefully respond with a solution

Experience with linux: used windows for most of my life, have been using temporary ubuntu 16.04 LTS for a couple days from my _only_ USB stick

Specs: Intel® Core™ i5 CPU M 460 @ 2.53GHz × 4 
3.7 gb memory, 64 bit OS


I would like to permanently install ubuntu alongside my pre-existing (non-functional) windows 7 64 bit. As you can see from the images attached at the bottom, my harddrive im assuming has some problem that isnt in laymans terms. I have some valuable media on that harddrive that i would like to save. I looked on youtube and DuckDuckGo to see if anyone else had solved my unique situation themselves but with no luck. _So i suppose my questions are_, how do i safely partition this error-stricken harddrive so that i can install ubuntu permanently; also how do i save my valuable media files? 

Im unable to access windows, if i boot windows it will do the chkdsk or scandisk i forget which. Basically it will run that program then restart itself, then run again and keep restarting....so windows never loads. If i choose to skip the chkdsk, it will go to the windows loading screen and then restart itself. I only have _one_ low quality 8gb USB stick from which to use a live boot with, and my roommates computer which runs windows. She will be moving out any day now, so i dont have much time left with which to use her computer to load my USB stick with anything i might need to fix my own computer. There is no public library i can go to for computer access. In the final days of my windows being usable, it was painfully slow, even firefox would hang when i tried to double click firefox. I have a suspicion that the computer memory is screwed up somehow, but if its a problem that can be fixed with software (not hardware) then theres hope. I have had to manually push the power off button on the computer probably 2 dozen times in the last week....because it keeps hanging. Even ubuntu from the live USB will hang if im using an adobe flash-intensive website. Ubuntu also hung when i tried to update the the OS in "Ubuntu Software". Whenever the computer hangs the mouse is always unresponsive, and the keyboard is semi-responsive. The computer in windows would blue screen eventually...something to do with iastor.sys. On the last day windows was working i installed the latest intel rapid storage technology driver from the intel website....that seems to have made it worse. Sorry to involve windows on the ubuntu forum but i think its related to my partitioning problem. 

What i DONT have: money (as in $0), screwdriver to open my computer. A windows 7 CD or any operating system CD. Blank CDs or blank DVDs. Recovery CDs

Thank you for any solutions, please use laymans terms im not good at this linux stuff yet :P


[IMG]https://imghost.io/images/2017/03/05/a.png[/IMG]

[IMG]https://imghost.io/images/2017/03/05/bbb.png[/IMG]

[IMG]https://imghost.io/images/2017/03/05/ccc.png[/IMG]

---

### Post by oldfred on 2017-03-05
Forcing shutdown with power switch almost always corrupts file system whether Linux or Windows.
Then fsck if ext4 formatted or chkdsk from Windows is required.

And when Windows gets slow it can be a variety of issues, best resolved immediately. And if at that point you did not have good backups, you should have.
One issue is that drive is full. Windows NTFS format really likes 30% free, at 10% free defrag can take forever as there is no working room. And that may be why chkdsk is taking so long as there is no space to copy the corrupted files or parts of files to.

You may be able to mount read only. But the Linux NTFS driver will not mount read/write NTFS that is hibernated nor if it needs chkdsk to prevent further damage.

       Manual mount read only may work to copy data
sudo mount -o ro /dev/sda2 /mnt
or
mount -t ntfs-3g -o ro /dev/sda2 /media/windows 

But with Windows, generally better to use Windows tools to repair it.

---

