---
title: "gparted ?"
date: 2012-10-24
forum: Installation &amp; Upgrades
---

### Post by offgridguy on 2012-10-24
I am reading all i can find on partitions in prep for another install. I downloaded gparted
and have read the info there in the help section.  So a couple of questions along the 
first things first line.  First gparted seems to be _the_ tool for working with partitions in
linux like windows task manager is in windows {correct]?
      
   Second, I can only use it  by booting from a live cd with gparted installed, or from a
download, burned to cd.  I can't do it from the ubuntu version currently installed and
running.    Am I understanding this correctly to this point ?

---

### Post by jerrrys on 2012-10-24
GParted can be used in two ways: while booted in an operating system or from a live CD. The recommended way of         using GParted is from the live environment. Why, you ask? This is because partitioning operations need to be         done on hard disks when they are not in use, to avoid data corruption. Partitions         that are in use cannot be modified. They are locked by the operating system that uses them.

[http://www.dedoimedo.com/computers/gparted.html#mozTocId661277](http://www.dedoimedo.com/computers/gparted.html#mozTocId661277)

Got multiple HDD's?  Put a copy of gparted on each.

---

### Post by Herman on 2012-10-24
> First gparted seems to be _the_ tool for working with partitions in
linux like windows task manager is in windows {correct]?Yeah that's basically right but the Windows tool is only useful for working with partitions containing file systems Windows recognizes, where GParted works with a wide variety of file systems including the ones used by Windows. 
> Second, I can only use it  by booting from a live cd with gparted installed, or from a
download, burned to cd.  I can't do it from the ubuntu version currently installed and
running.    Am I understanding this correctly to this point ?     Correct, or at least from a different partition in the same hard disk or a different disk. The partition needs to be unmounted before working on it with GParted.
The Windows tool does not require unmounting and can be run from a Windows system while the system is running, whoever it has the limitation of only being able to resize Windows to about half the original size of the file system due to what Windows calls 'immovable files'.
GParted can shrink a Windows partition and the file system inside it to as small as one wants, or at least until it's stopped by the space occupied by the files inside it.
With Windows tools they say you have to defrag first, I'm not sure if there's any truth in it, but that's the popular superstition. GParted does not require defragging a Windows partition before resizing, but it does like a clean file system. I always run CHKDSK /R  once or twice first, and again afterwards. 
GParted is the best tool for shrinking Windows if you're primarily a Gnu/Linux user and want to shrink Windows to less than half of its original size, and if you want to be able to work on all kinds of file systems, (not just Windows ones). 
Use the Windows tools if you are not too sure about Gnu/Linux and only want to shrink Windows a little bit.
Personally I have been using GParted for years now and I find it excellent for all partition and file system work.

---

### Post by offgridguy on 2012-10-25
Thank you jerrys; Okay  thats what i was thinking ,thank you for the confirmation.

Thank you Herman, for the informative reply,  I actually only have ubuntu 12.04 on this computer as the only OS.  So i don't have to worry about windows.
I want to install Kubuntu and i am not real worried about losing ubuntu in the process, but
for the sake of my own learning experience, I want to try to keep it at least for now.

I do have the original live cd for ubuntu and I am assuming it must have gparted on it
as it set up the partitions i have now.
Eventually I want to put Lubuntu and xubuntu on here as well, and i am wondering how that works when i can only have a maximum of 4 partitions?

If i can figure out how to get a thumbnail of a screenshot, i will put  that on here, so you
know what I have now. :)

---

### Post by oldfred on 2012-10-25
Of the 4 primary partitions, one can be the extended partition which is just a container for logical partitions. Then you can have as many partitions as you want. Windows has to boot from a primary, but Ubuntu and most Linux work from logical partitions just fine.

An alternative if reformatting a drive and not using Windows is gpt partitioning. It is required for drives over 2TB, UEFI boot systems and recommended for SSDs. It is optional otherwise but the new system. I have gpt on two drives and MBR on two drives.

Some go berserk with partitions. :)

---

### Post by offgridguy on 2012-10-25
Thank you oldfred, looking at the screen shot WOW!!

---

### Post by Herman on 2012-10-25
:) Yeah, that's cool oldfred!

@ offgridguy
Another thing that might be worth mentioning about partitions which contain Gnu/Linux file systems is the fact that the starting sectors of these file systems are not so easy to move around on the hard drive.  These file systems can easily be resized from the left, but not so easily from the right. It can be done with GParted now but it's quite a slow process. It's quicker to copy and paste the partition to another part of the disc, (if it's small enough and there's room somewhere to copy it to).
For that reason you can possibly save yourself some time by  planning ahead if you intend to dual or multi boot more than one flavor of Ubuntu and/or other  Gnu/Linux OSes.
  > I actually only have ubuntu 12.04 on this computer as the only OS.
:) That's what we like to hear, (or read), somebody who's a real Gnu/Linux user! 12.04 is my main OS too, in an OCZ SSD with some HDDs for storage. It used to boot in under 3 seconds when I kept it tuned for fast booting, but now it boots in about 5 or 6 seconds or so probably. (Pretty slow eh?)

---

### Post by offgridguy on 2012-10-25
> **Herman said:**
> 
For that reason you can possibly save yourself some time by  planning ahead if you intend to dual or multi boot more than one flavor of Ubuntu and/or other  Gnu/Linux OSes.
  

Thanks Herman; Yeah I'm trying to get as much of a handle on this as I can before I go
ahead , otherwise I will be back here looking for help to fix my mistakes.:)

---

