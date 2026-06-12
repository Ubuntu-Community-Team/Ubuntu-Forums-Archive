---
title: "After Creating Partition and Installing"
date: 2011-07-06
forum: Installation &amp; Upgrades
---

### Post by kjelljs on 2011-07-06
Let's say you have three hard drives that Windows was using (Windows was installed on one of them however *used* all three). After you install ubunto from booting cd, you install alongsided windows and give Ubunto 5 gigs of partition.
 
After installed and running Ubuntu, can you store files and use the other hard drives (as well as the windows partition on primary hard drive)?

---

### Post by oldfred on 2011-07-06
Sure. Ubuntu now comes standard with a driver for NTFS formated partitions. Have you tried the liveCD to test that it works with your system?

Is this a standard install with separate partition or wubi which is just a file inside the windows NTFS partition.

I generally suggest a shared NTFS partition as windows does not seem to like other systems writing lots of data into its system partition. But if you have lots of NTFS data partitions you already have shared data partitions. You can set the mount of the windows system partition as read only if you do want to read something from it. Ubuntu does not hide the windows system files & folders and it is often too easy to accidentally move something essential to windows.

Only 5GB is a little small. I suggest 10-20GB to give lots of room to work with. I have installed lots of programs in Ubuntu and have used about 6GB, but it also depends on what data you save in Ubuntu and what data you save to the NTFS partition.

Also instructions for CD or USB
[http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)
[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

Installing Ubuntu in Hard Disk Two (or more) internal or external 
Maverick screens shown, other versions have slight difference in screens but process is the same.
[http://members.iinet.net.au/~herman546/p24.html](http://members.iinet.net.au/~herman546/p24.html)
Install with separate /home from aysiu
[http://www.psychocats.net/ubuntu/installseparatehome](http://www.psychocats.net/ubuntu/installseparatehome)

---

### Post by kjelljs on 2011-07-06
Thank you for your response. Here is what happened with me. I downloaded installed Ubuntu yesterday from boot cd "alongside windows" onto an external hard drive previously only used for storage. Now when I start my cpu it is a bios/dos screen that says GRUB something but it is not like the OS select screen that I have seen in the tutorials. I am at work and don't recall but it says GRUB "something" and has a blank cursor apparantly for commands or something? Dunno what to do.

---

### Post by ajgreeny on 2011-07-06
If you installed to an external disk, but let the system put grub on the default, which is sda, ie your internal hard disk, you will get a <grub repair> prompt when you boot without the external disk attached.  This is bacause grub (the program) is on sda, but all the configuration files for grub are on the external disk.

If that is your situation, you need to restore the windows MBR to the main disk sda, and then install grub to the external disk.

---

### Post by kjelljs on 2011-07-06
I am sure it did that *with* the external disk attached though

---

### Post by oldfred on 2011-07-06
With multiple drives it is best to run this so we can see what is where. From liveCD:

Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste contents of results.txt in a New Reply, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the New Reply Edit toolbar and then paste the contents between the generated [ code] paste here [ /code] tags.
V60 has improved formating and requires code tags to make it legible. New Version is a zip file that you have to extract to get .sh to run.

---

