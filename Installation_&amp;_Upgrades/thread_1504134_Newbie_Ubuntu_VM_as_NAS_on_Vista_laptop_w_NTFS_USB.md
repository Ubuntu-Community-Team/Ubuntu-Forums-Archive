---
title: "Newbie: Ubuntu VM as NAS on Vista laptop w/ NTFS USB drives?"
date: 2010-06-07
forum: Installation &amp; Upgrades
---

### Post by dcan on 2010-06-07
(if this is in the wrong forum I apologize, but a search showed this may be the best spot)
 
Hi all,
 
I have what may appear an odd question. I have never installed Linux before, but I'm very impressed with the Ubuntu philosophy and this forum so I thought I'd give it a shot.
 
I have a Windows wifi network at home with three laptops: One is Windows 7 and the other two are running Vista. My wife uses the Windows 7 laptop and I am using one of the Vista boxes, with the other one currently running in a spare room. I'd like to use the Vista box as a NAS (for our photos, backups, etc) but I need to keep Vista on it for a variety of reasons. Just hooking up the USB drives to the Vista laptop and sharing them out isn't really the way I want to go, and besides it wouldn't let me install Linux... :)
 
What I'd like to do is install Ubuntu into VMWare Player or VirtualBox and have it share out the USB drives on the network. The drives are NTFS and I'd like to keep them that way, because I'd like the flexibility of being able to plug them directly into one of our laptops if need be, or access them from the Vista host OS. I understand I'll need to install SAMBA to get this shared out, and I found a tutorial for that so I can try that out.
 
I did download and play around with FreeNAS, but it has lots of issues with NTFS corruption whereas Linux has the NTFS driver for a few years now. I haven't tried an Openfiler appliance yet but that may be a plug-and-play option as well.
 
My questions are:
 
1. Has anybody done something like this? (Install Ubuntu as a Guest OS for a NAS on a Windows box in a Windows home network) If so do you have any advice on what I should/should not do, things to watch out for, etc?
 
2. NTFS read/write safety. I understand NTFS support is out-of-the-box now with Ubuntu, but searching even on Google I keep running into concerns of data corruption and stability. The most I've found so far is that it works reliably "for a few weeks" for data restoration or temprorary use. Is NTFS safe for read/write operations for the long-term, i.e. the foreseeable future? I can see changing to another filesystem when I have more experience, but for now I want "toes in the water" and this seems the easiest way. However, I don't want to risk data loss -- this will effectively be our backup location, and our media storage, with lots of (old, irreplaceable) photos that we just can't afford to lose. If this is a risk then I need to either consider another filesystem, or finding another approach.
 
3. On that note, what are the ramifications of switching to another filesystem? Any suggestions for a good filesystem that will work well in this type of environment?
 
Lots of questions, but I'd like to get this done right for future expandability. I can easily see adding on a bittorrent client and download manager, and even adding a LAMP-style development environment to play with... eventually.
 
I appreciate any help anyone can offer. Thanks!

---

### Post by pytheas22 on 2010-06-07
I've never done this, but I can offer a couple suggestions on your file-system worries.  One is to format the USB drives as ext3, which Linux can read natively, and which Windows can read if you install the drivers from [http://www.fs-driver.org/](http://www.fs-driver.org/).  (Don't format as ext4, which has read support in Windows but not write support, the last time I checked.)

The other strategy is to use trusty FAT32, which Linux can read and write without issue.  Keep in mind the limitations of FAT32, such as maximum file size being 4 gigabytes.

Also, how recent was the information you were finding about data corruption using Linux's ntfs drivers?  I remember that being an issue when those drivers first appeared several years ago, but I don't know anyone who's had problems more recently.

---

### Post by dcan on 2010-06-07
pytheas22,
 
Thanks, I'll check the ext3 info you suggested. FAT* may not be an option because of the 4gb file size limit, but I'll have to double-check. My main concern on that was the use of DVD images, but there are various formats for that as well so the 4gb limit may not be an issue.
 
Admittedly the NTFS worries were 2-3 years back for the most part, but it just bugged me that I couldn't seem to find anything other than "be careful or you might lose everything", which doesn't endear me to trying Linux... :\
 
That's also mixed in with researching FreeNAS (before looking at a general Linux approach) and finding out that running it with NTFS is basically turning on a time bomb for your data. So some of my paranoia may be misguided.
 
Thanks.

---

### Post by dcan on 2010-06-07
According to the Ext2IFS site it only recognizes ext2/3 partitions with an inode size of 128. However, according to [this other thread]("http://ubuntuforums.org/archive/index.php/t-979523.html") Ubuntu now defaults to an inode size of 256 with no apparent way to change that.

The other two bits of software are read-only. I guess I could deal with that, but according to that same thread they aren't very stable either. And Ext2IFS is the most stable of the three -- but it isn't usable with ext3 filesystems created by Ubuntu now... :(

Looks like I'm back to evaluating FAT32 then...

---

### Post by pytheas22 on 2010-06-07
That may be true.  The last time I tried the ext3 drivers on Windows was about four years ago, and I wasn't even running Ubuntu then.

However, I'm not sure this rules out ext3, because as long as you format your USB drives with ext3 and an inode size of 128, both Ubuntu and Windows should be able to read them (I'm assuming the ext3 drivers in Ubuntu can deal with inode sizes of 128, even if Ubuntu defaults to 256 when creating partitions).

The only challenge will be figuring out how to format the USB drives with the correct inode size, but that might be as easy as installing the ext3 drivers in Windows and doing the formatting there.  I'd also be shocked if there's not a way to format them from Ubuntu and specify the inode size.

---

