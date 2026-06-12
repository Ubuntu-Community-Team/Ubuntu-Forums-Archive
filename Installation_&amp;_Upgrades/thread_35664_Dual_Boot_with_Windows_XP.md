---
title: "Dual Boot with Windows XP"
date: 2005-05-19
forum: Installation &amp; Upgrades
---

### Post by codecraig on 2005-05-19
Hi,
   I am brand new to Ubuntu and before I try installing it I wanted to know if someone could point me to some instructions on how I can install Ubuntu, but keep my Windows XP Pro install in tact....basically I want a dual boot setup.

Thanks.
Craig

---

### Post by smb2004 on 2005-05-19
first of all how is you hard drive partitioned?  if you havnt touched it, it is most likely that your windows partition (ntfs) fills up the entire hard drive.  you will have to resize it, which is a bit dangerous (and im not sure if you can resize an ntfs)

if you can set up you hard drive into two partitions (ntfs or fat32) for winxp and space for you linux, then the installer will install onto the free space.  the grub boot loader should automaticaly detect your windows and put that on the list.  so you will have the option of booting to winxp or linux.  

if for some reason you cant boot to winxp after, there are ways to edit grub and fix that.

**ALSO**

i hear that ubuntu has a livecd.  which is a cd that runs off the cd alone, not the hard drive, you you can download that and try it out with out doing anything to you hard drive.  it is a bit slow thouhg, but still good.

hope this helps.  there is a lot of information about this topic all over the web simply to a google search.  linux is a great OS, i have basilcly switched from windows.  its worth trying.

---

### Post by codecraig on 2005-05-19
thanks for the info.  I currently have two hard drives each having 2 partitions.  So basically I can create one empty partition (either ntfs or fat32?) ...and Ubuntu will install to that empty one?

You mentioned that after the install if windows doesnt show up in the boot list, i can edit grub....can you point me to something with how to solve that, just in case ;)

Thanks for your help....I would like to move towards Linux only...first I gotta try it, then I will slowly move my fiancee over to it as well.  I once tried Mandrake and she seemed to like it, but we didnt do much with that.

Thanks.

---

### Post by Xian on 2005-05-19
There's a wiki page on this if you're interested: [Windows Dual Boot How-To](http://www.ubuntulinux.org/wiki/WindowsDualBootHowTo)

---

### Post by JimmyBEng on 2005-05-20
having set this up myself recenty I have a couple suggestions.  First it is worth it to try out the Live CD.  If it runs well and detects most or all of your hardware in some kind of usable fashion, it means the install will probably be smoother.  Second, you said you already have two partitions so that might make repartioning easier.  If you still have to shrink an NTFS partion the Hoary installer can do it (it shrunk mine just fine), just back up important data, and defrag before you do it to get the data to the front of the partition. Also, in your partion process you probably want to have a FAT partition somewhere so you can use it to share some files between linux and windows. (I  use mine for music, T-bird profiles etc.)

---

### Post by codecraig on 2005-05-20
Thanks a lot, I just burned the Live CD so I am going to check that out.  All the suggestions will definetly help, thanks!

---

