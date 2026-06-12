---
title: "XP/linux SSD transfer etc."
date: 2012-09-17
forum: Installation &amp; Upgrades
---

### Post by Newuser901 on 2012-09-17
Anyone good with this?

I'm trying to get xp and ubuntu onto a new 90gb SSD.

Current setup:
windows xp 32bit 10GB partition(NTFS)
Ubuntu 11.10 64bit 240gb partition(ext 4) I can change this to any version. I pulled back from 12.04 to try to get SWTOR and other games working in Wine.
AMD 1100t phenom 2 6xcore
GA-970A-D3 Mobo
8GB 1600mhz ram(possibly 1866)
1x 90GB OCZ agility 3 (Raw completely fresh!)
1x 250GB Seagate 7200rpm HDD 8 or 16mb (OSes currently on this disk.)
2x 250GB Western Digital Caviar 7200 RPM 8mb (labeled Games and Games2) (1xNTFS, 1x? or NTFS)

(I will likely be keeping the XP at 10GB and bring Linux down to 20GB and make the rest for holding games I want to run fast. I'll probably Raid the other three HDDs later so that the Seagate is the backup and the WD HDDs are the pull outs, since they are older, so I can replace them when and if they die.)

Can anyone help me with this. I've attempted to follow some sites about getting AHCI working in XP and they all cause blue screens on the load screen. I lost which sites specifically.

Remembered so far:
[http://forums.pcper.com/showthread.php?t=444831](http://forums.pcper.com/showthread.php?t=444831)
......

I currently have to set my SATA to IDE mode to run windows. Can't get drives to work. The rest I'm completely unfamiliar with. Anyone give me some solid starts. Or any help at all. The guides aren't helping me. they all seem too specific. I've tried one with Intel storage matrix and putting it in system 32 and using a reg entry but I still get a blue screen on load. Do I need something specific to my hardware?

I know I can do a new boot or slipstream them into xp. Not sure if I can do that for F6 entry with a USB thumbnail. I have no working floppy drive atm. Not sure what is the ideal way. I was reading you should afterwords get your ram to act as an HDD for off stuff for xp. I thought I'd do that unless that is not ideal. Since XP can only use 4 I figured the other 4 would be good for XP as long as it only works while XP is loaded. since i don't want to jip linux. I keep all xp software I can in the games partitions on the other drives. I'm also trying to get Firefox on both XP and linus to be the same peice of software. Same cookies same bookmarks same downloads(downloads was easy) so when I use one it changes all the important things for the other etc that can be. But, anyway....

Any help would be appreciated. What do I need to do to get it to work and be compatible with the SSD. Will microsoft be making XP compatible with trim etc to be nice to us XP users or no. 8p Even if i did a fresh XP install I'm not sure if I could or would know what to do to get it working the best it can. What do I need to be careful about. I don't want to wear the drive out early or kill the performance.

---

### Post by oldfred on 2012-09-17
XP & SSDs are not a good mix. I have XP on another rotating  drive and finally stopped using my XP as you have to have AHCI for trim to work on SSD. 
Also gpt partitioning is recommended for SSDs, but unless booting with UEFI (XP will never work with UEFI) you cannot use gpt with Windows.

I still have my Firefox profile, Thunderbird profile & all photos for Picasa in my shared NTFS data partition on a rotating drive. I did not always have exactly the same versions of software in XP and Ubuntu but tried to keep them close in versions. But never had any issues. Been essentially the same for 5 years. I did change from FAT32 to NTFS on a new drive about 3 years ago.  I just edit profile.ini to find the new path to a shared NTFS data partition already mounted via fstab. I can post details if you want, general info here:

[http://kb.mozillazine.org/Moving_your_profile_folder](http://kb.mozillazine.org/Moving_your_profile_folder)
[http://support.mozillamessaging.com/en-US/kb/Profiles](http://support.mozillamessaging.com/en-US/kb/Profiles)
[http://www.mozilla.org/support/thunderbird/profile](http://www.mozilla.org/support/thunderbird/profile)

---

### Post by Newuser901 on 2012-09-18
If I installed Linux on the SSD and xp on the HDD and stored the games on the SSD with xp accessing would it cause the same problems? Or could that be worked around?

---

### Post by oldfred on 2012-09-18
Did you find a working way to install the AHCI drivers to XP. I had found some sites on how but it looked complicated on an existing install and I was ready to stop using XP.

If you can get XP to work with AHCI then you have to partition SSD in MBR which is ok. 

Do not know enough of the details of how trim works. I know it works in Windows 7 and Linux but with a data partition I am not sure.

---

