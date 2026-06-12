---
title: "Installing Ubuntu alongisde Windows 8"
date: 2012-11-28
forum: Installation &amp; Upgrades
---

### Post by shresthanator on 2012-11-28
My old HD died on me so I installed new HD on my desktop PC. My old setup was Windows 7 with ubuntu 12.10 dual-boot. 

I recently got windows 8. I first installed windows 8 into one partition of the new HD. I tried installing ubuntu alongside windows 8. 

Everything ran as expected, and I get to the point where I have to restart my machine. However, when it boots up, I do not get to the GRUB boot-loader it goes straight back to windows 8. 

I've tried to delete ubuntu 12.10 and reinstall it. However, it hasn't worked.  

Can any of you help me? Should I try to manually install GRUB boot loader?

---

### Post by Bigneil on 2012-11-28
I recently had a similar issue, you should try a program called "boot-repair" which is great for fixing issues with grub. It might solve it for you, but I'm only drawing from what worked for me.

[https://help.ubuntu.com/community/Boot-Info]("https://help.ubuntu.com/community/Boot-Info")

---

### Post by shresthanator on 2012-11-28
> **Bigneil said:**
> I recently had a similar issue, you should try a program called "boot-repair" which is great for fixing issues with grub. It might solve it for you, but I'm only drawing from what worked for me.

[https://help.ubuntu.com/community/Boot-Info]("https://help.ubuntu.com/community/Boot-Info")

Yea so I have used this program before- I have had to run Ubuntu from live cd and repair grub. But for some reason when I try this now, the boot repair runs and it says scanning hd but it takes forever. I let it run for like an hr and it is still scanning. Before when I did this it just took like several minutes. Any other alternatives?

---

### Post by oldfred on 2012-11-28
That sometimes happens with Bootinfoscript when it cannot open a partition. Are you getting any partition errors?

Post this to see partitions:

       sudo parted /dev/sda unit s print

---

### Post by shresthanator on 2012-12-02
> **oldfred said:**
> That sometimes happens with Bootinfoscript when it cannot open a partition. Are you getting any partition errors?

Post this to see partitions:

       sudo parted /dev/sda unit s print

so this is the result of that when I start ubuntu with the live cd: 
 
[http://i.imgur.com/PDEfM.jpg](http://i.imgur.com/PDEfM.jpg)


I do not think I am getting any partition errors? I am not sure?

---

### Post by oldfred on 2012-12-02
You can just copy & paste text output to your message. If longer or formated use code tags. You can hightlight & click # in edit panel above message to auto create code tags.

Without seeing what partition is not mounting it is hard to know. It could be chkdsk is needed on the NTFS partition. After resize NTFS partitions always run chkdsk if booted, but if not yet run it just may need that from a Windows repairCD or flash drive.
It also could be fsck is needed on ext4 Linux partition.

From LiveCD open gparted. It often shows a yellow or red warning icon on a partition it sees as an issue and if you click (right click?) on icon it may tell more.

---

### Post by shresthanator on 2012-12-02
hmm....when I try to run gparted from the live cd it just says scanning and it scans like forever. I let it run for an hour, and it still wasn't done. I've run gparted from the live cd before, but before it only took like several minutes. Anyways I will try to run chkdsk

---

### Post by oldfred on 2012-12-02
That gparted will not load it also says there is an error.

If not chkdsk from Windows on NTFS partition,  try this on ext4 LInux partition.

       #From liveCD so everything is unmounted,swap off if necessary, change example shown with partition sda6 to your partition(s)
#e2fsck is used to check the ext2/ext3/ext4 family of file systems. -p trys fixes where response not required
sudo e2fsck -C0 -p -f -v /dev/sda6
#if errors: -y auto answers yes for fixes needing response see man e2fsck
sudo e2fsck -f -y -v /dev/sda6

---

