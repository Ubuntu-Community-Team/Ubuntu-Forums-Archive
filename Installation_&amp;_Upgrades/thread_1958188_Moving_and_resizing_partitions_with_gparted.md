---
title: "Moving and resizing partitions with gparted"
date: 2012-04-13
forum: Installation &amp; Upgrades
---

### Post by ray field on 2012-04-13
Trying to add a couple of partitions to my laptop so I can still use Lucid while I'm trying out the Precise on it. 

Under Windows 7 I shrank the ntfs partition I was using to share stuff between Ubuntu and 'doze -- /dev/sda5 or "dozedat" in the screenshot below, giving myself 30GB free. I'd like to shift all my Lucid-related partitions over to the left so that I can install Precise, as well as a new /home partition -- will probably also shrink /dev/sda6 by 10GB as well.

However, I can't figure out how to shift the partitions over -- when I try to move the extended partition /dev/sda 3 over to the left where I've freed up the space, gparted gives me a big scary message saying Ubuntu may no longer boot if I do so. What should I do?

---

### Post by Quackers on 2012-04-13
Yes it does that. It's possible that moving data can cause losses, but I've only ever experienced it once. 
Alternatively you can install whatever you want in the unallocated space. The partition numbers may change though, but the order doesn't really matter afaik.

---

### Post by Herman on 2012-04-14
It's also possible to use the copy and paste functions in GParted to move an operating system partition.

Normally it is necessary to remove files first in order to be able to resize the partition to a small enough size to fit in the free space first. 
If you're creating a backup before using the partitioning software as is recommended, that's not a big problem. It's important to double check that the files you really want to keep are definitely included in the backup though. Then once you're sure, you can delete your user files from the operating system. Then resize the operating system as small as you can. 

When GParted copies and pastes the partition, it will give the file system UUID to the new copy of the file system in the new partition and give the old file system a different UUID.
That means the old partition can be deleted and the new one should boot as normal, I don't think you'll even need to re-install GRUB.

EDIT: Then of course you can resize the partition larger and restore the user files.

Although you might at first think this way is more work, in the long run it turns out to be faster, or at least it seems that way to me.

---

### Post by agillator on 2012-04-14
The primary problem with booting after moving partitions is that the partition numbers may change and GRUB then is looking for the wrong partition. If you boot from, say, sda7 normally and that becomes sda5 after moving partitions, GRUB won't be able to boot. So, part of any partition change should be a planned reinstallation of GRUB. Instructions for that may be found here: [https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2) and here: [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows) and other places. A Google search may help with your specific situation.

---

### Post by Herman on 2012-04-14
Doesn't the of use file system UUID numbers solve that problem?

---

### Post by Quackers on 2012-04-14
I think all later versions of grub use UUID's rather than device designation. I know my etc/fstab is out of date in terms of partition numbering, but the system still boots fine.

---

### Post by Herman on 2012-04-14
Well now that I'm reminded, there may be some Ubuntu derivatives, Mint to name one example, which hadn't yet adopted UUID numbers the last time I tried it out. That was quite a while ago now and I wonder if they have changed or not. It could be that GParted's warning message is meant for users of distros that don't agree with the use of file system UUID numbers.

---

### Post by ray field on 2012-04-14
worked just fine -- in fact the reason I wanted to shift everything over "to the left" was so I didn't have to be concerned with borking the old Lucid install. I did have everything backed up, and also took one step at a time, rebooting after each change, just to be sure. thanks all.

---

### Post by Quackers on 2012-04-14
Glad to hear that :-)

Please mark the thread as solved using thread tools near the top of the page.

---

### Post by ray field on 2012-04-15
just for the archives:

1) tried to install using the DVD I burned because I couldn't be bothered looking up how to put the bootable image onto a memory stick but that was a very rocky road, so after three or four aborted attempts, I gave it up. stick worked the first time -- I came across something in the release notes that seemed to suggest that this is the preferred way, though I'm not sure how many users are going to take this.

2) 12.04 so far is absolutely brilliant on the Lenovo S100. this unit did pretty well with Lucid but 12.04 looks better -- and performs much snappier and more efficiently. the AR9285 wireless chip which has been problematic for some users is much more robust for me under Precise than Lucid: previously wifi would almost never return after the netbook went into suspend, now it always seems to.

3) after years of using wicd I decided to see how the much-despised Network Manager would do. so far, it's great, & I don't really mind that it doesn't require much brainpower to use.

---

