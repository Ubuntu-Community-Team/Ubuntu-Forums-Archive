---
title: "extended partitions"
date: 2021-10-26
forum: Installation &amp; Upgrades
---

### Post by leol1126 on 2021-10-26
gonna install ubuntu to my hdd but toshiba in 2009 partitioned it into 4 making it so i cant make a fifth bootable one. i heard of extended partitions but how do i make them (with windows because i dont have any acess to linux) and install ubuntu to one
idk which ubuntu i will install but it will be supported and modern. i would have done 20.10 or 16.04.7 lts because i already made installers for them but i gave those to someone and they havent given them back yet. if there are any good distros i would like a link. (needs to be able to be installed on a dvd)

---

### Post by Impavidus on 2021-10-26
16.04 isn't modern. It still has extended security maintenance, but standard support has ended. Support for 20.10 has ended too. So I suggest either 20.04 or 21.10.

Is there a different OS installed on that computer that you want to keep? Like Windows 8 or 10? But that computer seems a bit old for those Windows versions. If there's nothing you want to keep, just wipe the harddrive and install Ubuntu. Actually, better to use a light flavour, as that computer isn't very powerful, I assume. Lubuntu, maybe.

---

### Post by leol1126 on 2021-10-27
it has windows 10 also too late i alrady installed 16.04.7 lts because i am too lazy to download another iso

---

### Post by yancek on 2021-10-27
>   lts because i am too lazy to download another iso                 

Which contradicts the statement in your original post of installing a supported and modern distro. This is somewhat equivalent to people using unsupported windows systems such as windows 7 and earlier which jeopardizes other users  on the internet and gives opportunity to spammers and hackers to take advantage of other users.  You might take a look at the link below which explains the Extended Security Maintenance for Ubuntu mentioned in post 2.



[https://ubuntu.com/security/esm](https://ubuntu.com/security/esm)

---

### Post by grahammechanical on 2021-10-27
How did you install 16.04.7 when the four primary partitions were already used by the manufacturer? Your actions make this thread pointless. But just for those who are wondering. This is the method.

1) Use Windows tools to manage Windows file systems and partitions. Use a Windows tool to defrag the drive. Make sure Windows loads correctly. Use a Windows partition manager to delete one of the primary partitions and also shrink the other primary partitions to create sufficient free space for Ubuntu.

Then use Linux tools to create an Extended partition in the free space and in that Extended partition create at least one Linux partition for Ubuntu. It must have the Ext4 format.

The Ubuntu live session has an application called GParted that will do the Linux part for you. My final advice is to research the internet to understand the Master Boot Record (MBR) partition table and Primary, Extended and Logical partitions and also study the GParted manual. It is online.

Regards

---

### Post by oldfred on 2021-10-27
Did you not understand this?
[https://ubuntuforums.org/showthread.php?t=2468334](https://ubuntuforums.org/showthread.php?t=2468334)

---

### Post by QIII on 2021-10-27
You have been asked twice by forum Admins to stop asking for support for an EOL release, advice which is only allowed in rare instances such as when a LAN admin is attempting to keep production servers running as they migrate to a new release.

Let me say this for a third time:  *Stop asking for support for un-supported releases.*

Closed.

---

