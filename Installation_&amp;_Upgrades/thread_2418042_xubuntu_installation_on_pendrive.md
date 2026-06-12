---
title: "xubuntu installation on pendrive"
date: 2019-04-30
forum: Installation &amp; Upgrades
---

### Post by takto416 on 2019-04-30
Hello everybody. 
I've a problem with installing xubuntu 19.04 on pendrive. I installed the system through second pendrive made in rufus. When I boot from pendrive grub menu appears with windows 7 from my normal disk and some new ubuntu which doesn't work (scr[IMG]https://mega.nz/#!X8Bg1QQA!tw5GAmtQQYpSUlEHWTMjUgIFbRKHPGSm4bSC0oCmpEw[/IMG]eenshot).
[https://drive.google.com/open?id=10oG5yplCrn9_3U2gCsr9T24MEUDy6llq](https://drive.google.com/open?id=10oG5yplCrn9_3U2gCsr9T24MEUDy6llq)
[IMG]https://ibb.co/8NQ2GcH[/IMG]
 I think that only xubuntu should appears. Am I right?
Pendrive has 2 partitions. One of them has about 20gb and is FAT32. Other one has about 10gb ext4 and is for the xubuntu. When I try to open partition with the system on live linux from other pendrive error appears: 
Failed to open directory "4f89c498-555f-40e7-aedd-23a9594cd8fd".
Error when getting information from file "/media/xubuntu/4f89c498-555f-40e7-aedd-23a9594cd8fd/srv": Structure needs cleaning.
I please for help.

---

### Post by oldfred on 2019-04-30
Do not run auto fix, unless someone has  reviewed report. You may need to use advanced mode to correctly repair it.

May be best to see details, use ppa version with your live installer or any working install,  not older Boot-Repair ISO:
Please copy & paste link to the Boot-info summary report ( do not post report), the auto fix sometimes can create more issues.
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair) & 
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

You also may need fsck on that Linux partition. 10GB is not particularly large for a full install, but should work. 

#From liveDVD/Flash so everything is unmounted,swap off if necessary, change example shown with partition sdb1 to your partition(s)
#e2fsck is used to check the ext2/ext3/ext4 family of file systems. -p tries fixes where response not required
sudo e2fsck -C0 -p -f -v /dev/sdb1
# -y auto answers yes for fixes needing response, also see man e2fsck
sudo e2fsck -f -y -v /dev/sdb1

---

### Post by takto416 on 2019-05-01
Here is the raport: [http://paste.ubuntu.com/p/Gy9yf7dCsw/](http://paste.ubuntu.com/p/Gy9yf7dCsw/)
The next part of the instructions I am trying to figure out yet.

---

### Post by takto416 on 2019-05-01
To be honest I don't understand what have I done but It worked. Now I am trying to understand that. Anyway I typed those 2 commends which you sent me. As a result that the partition is normally accesible in file manager.

---

### Post by takto416 on 2019-05-01
I want to add yet that I installed the xubuntu 19.04 on a computer with ubuntu 19.04 and windows 10. Maybe becouse that ubuntu 19.04 is in [COLOR=#000000]Boot-info summary report. Then before you told me to not do that I did auto fix on the pendrive on a computer with windows 7.[/COLOR]

---

### Post by oldfred on 2019-05-01
If you miss saying that Ubuntu is in external flash drive, Boot-Repair installs grub to every drive. But you want to keep Windows boot loader in MBR of Windows drive.
But if it now works that is great.

---

### Post by takto416 on 2019-05-01
It doesn't work yet. When I choose boot from pendrive GRUB appears and I can choose Ubuntu or Windows 7. When I choose ubuntu error appears which I made photo and uploaded to first post (on that computer there is no ubuntu). There is supposed to be only xubuntu but there isn't at all.

---

### Post by oldfred on 2019-05-01
All flavors of Ubuntu will say Ubuntu in boot entries. You can change that if you desire.

If fsck is fixing it but then it still has issues, your flash drive may not be reliable. Flash drives have a much shorter life than SSDs or HDDs.

---

### Post by takto416 on 2019-05-01
The pendrive has few days and few days ago I was checking is there anh bad sector and there wasn't so I don't think so that there can be any problem. 
Then what can I do next?

---

### Post by oldfred on 2019-05-01
When you install to external drive in BIOS mode, it is seen as sdb or sdc, or in grub hd1 or hd2.
But when you directly boot flash drive, it will be sda or hd0.

See if from grub menu, changing the entry you use to boot from hd1 to hd0 in all places in that one boot stanza.
If it then works, run this to update all entries.
sudo update-grub

---

