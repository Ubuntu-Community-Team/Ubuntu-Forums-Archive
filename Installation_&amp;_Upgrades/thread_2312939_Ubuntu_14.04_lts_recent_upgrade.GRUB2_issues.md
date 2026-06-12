---
title: "Ubuntu 14.04 lts recent upgrade.GRUB2 issues"
date: 2016-02-08
forum: Installation &amp; Upgrades
---

### Post by petatkinson on 2016-02-08
I've recently upgraded to the above and am experiencing constant boot problems.Details of latest bootrepair here [http://paste.ubuntu.com/14994312/](http://paste.ubuntu.com/14994312/)

---

### Post by oldfred on 2016-02-08
I do not see anything specific in Summary Report.

What issues are you having?

Your XP on sdb, thinks it is installed on first drive as its boot.ini says disk(0), and usually the grub2 drivemap command switches boot order so Windows thinks it is still first when booted from grub on sda which BIOS has labeled as hd(0) or disk(0).
Often better to keep Windows as first drive in boot order as it is more sensitive to settings. Linux seems to just work.
But you should not be using XP anymore anyway as it is not supported by Microsoft and you are not getting updates to protect it from the Internet.

---

### Post by petatkinson on 2016-02-08
Firstly XP boots off line and is used purely for legacy purposes. Updates and security are not issues here. I haven't purchased a MS product in over 10 years hence the Ubuntu question.

I've used Ubuntu lts since version 8 with XP and have not experienced this problem before. I've always done a fresh install each time and my latest install was 14.04. Previous version was 12.04.

The boot problem varies from a black screen, to "cannot write to hd0" errors. From Googling I was surprised to read that an LTS release is using a beta version of GRUB2. A little strange for a long term release.

I've repaired GRUB2 on a fair number of occasions thinking that it would resolve the problem. The pastebin link I attached was the latest repair and I was surprised to see that nothing shown up on the log.

When you say XP thinks it's on disk one is that Ubuntu thinking it or XP thinking it. The reason I ask is that I experience no problems booting into XP.

Would you have any idea how I could go about rectifying this situation. It's nearly impossible to rely on Ubuntu in it's current state on my machine.

Thanks for your input.

---

### Post by oldfred on 2016-02-08
XP thinks it is on first disk as shown in boot.ini.
If it works then the grub entry on devicemap is working to tell XP that it is on first disk, even though you booted on first disk and XP is really on second disk. 

Grub2's newer verison had so many fixes that they decided to use the beta. But it still is beta after two years? Do not know what is going on.

Have you run full fsck? 
And checked drive's Smart Status in Disks. Click on gear icon in upper right corner.

       #From liveDVD/Flash so everything is unmounted,swap off if necessary, change example shown with partition sdb1 to your partition(s)
#e2fsck is used to check the ext2/ext3/ext4 family of file systems. -p trys fixes where response not required
sudo e2fsck -C0 -p -f -v /dev/sdb1
#if errors: -y auto answers yes for fixes needing response, also see man e2fsck
sudo e2fsck -f -y -v /dev/sdb1

---

### Post by petatkinson on 2016-02-08
I have two disk drives, drive 1 is a 500gb IDE drive partitioned into two 250gb drives and disk 2 is a SATA 500gb also partitioned into two 250gb drives. I can't remember doing this but it looks like the two partitions on drive 1 are NTFS and on drive 2 the first partition is NTFS and the second partition is EXT4 and SWAP.

What I need to know is how can I tell GRUB2 this. The MBR for XP was installed on disk 1 as far as I can remember.

As far as I know I never changed this setup yet Ubuntu is struggling on boot and this only started to happen when I installed 14.04 LTS and GRUB2 which comes bundled on the Live DVD.

---

### Post by oldfred on 2016-02-08
Your sda is where grub always installs, unless you choose otherwise.

You show Windows on sdb.

It looks like Boot-Repair reinstalled grub to both drives.
With multiple drives generally better to use Boot-Repair's Advanced settings and choose one system and same drive for Boot loader. So each drive has boot loader for system installed on that drive.

---

### Post by petatkinson on 2016-02-08
I've cold booted and warm booted the system 10 times and each time Ubuntu has started normally. I am going to turn the system off overnight and attempt to reboot tomorrow. 

I am trying to rule out any hardware issues. I've seen so many postings on other forums reporting GRUB2 issues. Unfortunately most of the posters fail to report back when they manage to resolve their issues. 

I'd gladly delete XP but I need to boot to it from time to time. 

I assume that GRUB should reside alongside the XP MBR on a single disk system. As far as I knew that is how I installed it in the first place. I added the second disk at a later stage so I assume the current setup happened when I repaired the XP MBR or when I restored an XP backup.

As I said earlier I never encountered this problem before so I assume I must have been stumbling along with this problem until I installed 14.04 LTS.

Once again your input is much appreciated and I will report back on progress.

---

### Post by petatkinson on 2016-02-09
Switched on the PC today and it's booting as normal. I'm reluctant to mark this thread as solved as I didn't do anything to resolve it. I do need to sort out the conflict as to where Ubuntu days XP is located and where it physically located.

I'll run the system for another few days and if the problem doesn't persist I'll mark it as resolved.

Much appreciate your contribution Oldfred.

---

