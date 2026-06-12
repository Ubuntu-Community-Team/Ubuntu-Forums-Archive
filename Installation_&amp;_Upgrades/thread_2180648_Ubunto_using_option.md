---
title: "Ubunto using option"
date: 2013-10-14
forum: Installation &amp; Upgrades
---

### Post by Muhammad_Mudassir on 2013-10-14
I am new one user of ubuntu. i have installed now ubuntu 12-04 LTS in a dual boot (already installed win 7 professional) in a new volume of total space about 25 GB.
but problem ocurring is that when it has finalized installing. it asked me to restart. i restared.
when my laptop restarted.It directly goes to starting windows. it has not given me option either i want to use window or ubuntu.
Any one expert can answer my question.??What's the problem is??

---

### Post by Lars Noodén on 2013-10-14
You might need to restore Grub in order to dual boot:
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

### Post by heir4c on 2013-10-14
You used Windows to made the partitions?
And where is your Ubuntu installed? On the 24,41GB partition of on .....?

---

### Post by fantab on 2013-10-15
I don't think you installed Ubuntu if you installed it on your 1st partition of 24.41GB, because it has 100% free space.

Try the install again. At the 'Installation Type' dialog choose 'Something Else', select your partition where you want to install ubuntu and hit 'Change'. At the following screen select/chek Format, Mountpoint=/, Use As=Ext4 and proceed.

---

### Post by heir4c on 2013-10-15
He says it is on a partitions of about 25GB so,...


Muhammad_Mudassir what is on the 2 Logical partitions?

---

### Post by fantab on 2013-10-16
The two logcial partitions are NTFS formatted; Ubuntu can't be there.

---

### Post by mastablasta on 2013-10-16
> **fantab said:**
> The two logcial partitions are NTFS formatted; Ubuntu can't be there.

unless it's a wubi install.

aside form / you might also want to create /swap in the size of your ram.

---

### Post by Muhammad_Mudassir on 2013-10-19
yes i used windows.
in 24gb partition

---

### Post by Muhammad_Mudassir on 2013-10-19
[ 						 							 						 					]("http://ubuntuforums.org/member.php?u=1275004") 				 				 					 						[ 						 							**[COLOR=#000000]dear fantab and [/COLOR]**]("http://ubuntuforums.org/member.php?u=1275004")[**[COLOR=#000000]mastablasta[/COLOR]**]("http://ubuntuforums.org/member.php?u=964486")[URL="http://ubuntuforums.org/member.php?u=1275004"][B][COLOR=#000000]yes

yor are right it is showing 100% free space. but i have installed.
before installing ubuntu i hav formatted volume d with ntfs.
but during ubuntu installation i again formatted it with ext4

dear [/COLOR][/B][/URL][URL="http://ubuntuforums.org/member.php?u=739011"][B][COLOR=#000000]heir4c
 here i installed ubuntu in volume (D)[/COLOR][/B][/URL][URL="http://ubuntuforums.org/member.php?u=1275004"][B][COLOR=#000000]
[/COLOR][/B][/URL][**[COLOR=#000000][/COLOR]**]("http://ubuntuforums.org/member.php?u=1275004")[URL="http://ubuntuforums.org/member.php?u=1275004"]**[COLOR=#000000][/COLOR]**
[/URL]

---

### Post by fantab on 2013-10-19
In that case you Ubuntu didn't install at all. Because the all the space in 'D' is 100% free. Try again and re-install. You have to install to Hard Disk and don't use WUBI.exe.  If you are sure that you have installed Ubuntu then Check Windows - Add Remove Software- and see if you have Ubuntu there. If it is there then just remove it, for detailed info Read Here: [https://wiki.ubuntu.com/WubiGuide#Uninstallation](https://wiki.ubuntu.com/WubiGuide#Uninstallation)

---

### Post by Muhammad_Mudassir on 2013-10-19
to fantab

then give me another way how can i install ubunto as you said i should uninstall ubunto

---

### Post by heir4c on 2013-10-19
Use a live-dvd/usb of Ubuntu and boot it up.
Open gParted (Partition manager)
Look for the empty space. How he see it? as free space or unallocated?
Post here a screenshot of gParted, so we can see what you see.

---

### Post by Muhammad_Mudassir on 2013-10-19
I have done the same. but again the problem is same. it has not given option either to chose window or Ubuntu.
in disk management it is showing 100% free space. I can,t understand what the problem is??

---

### Post by fantab on 2013-10-19
You will need to create another partiton of atleast 1GB-4GB for SWAP. Create a Logical partiton after G.

Alright.. lets start from the start.

1. Download the Ubuntu.iso from: [http://www.ubuntu.com/download/desktop](http://www.ubuntu.com/download/desktop) . I would say do a torrent download, as it is safer: [http://www.ubuntu.com/download/alternative-downloads](http://www.ubuntu.com/download/alternative-downloads). 
2. Do a MD5Sum Check on the downloaded .iso : [https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM). This will tell us if the downloaded .iso is good for install.
3. Burn the downloaded .iso to a either [DVD]("http://www.ubuntu.com/download/desktop/burn-a-dvd-on-windows") or [USB]("http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-windows").
4. Boot Ubuntu DVD/USB and 'Try Ubuntu without Installing' option.
5. Establish connection to internet.
6. Install Ubuntu from Desktop- follow this guide: ht[tp://www.psychocats.net/ubuntu/installing]("http://www.psychocats.net/ubuntu/installing") 
7. At the screen that follows select the 24Gb partition and hit Change. Choose Mountpoint=/ and USE As=Ext4 and select format. Ok/Apply
8. Select the Partition you've created for SWAP and hit Change. Choose USE As= Linux SWAP or SWAP and select format. Ok/Apply.
9. continue with install.

Remember you will have to choose 'SOMETHING ELSE' option at the 'Installation type' dialog to manually install Ubuntu to the partition you want.

---

### Post by Muhammad_Mudassir on 2013-10-19
now whats the problem. I do not know. I have done the same.
but again there is no option of either to use ubunto or windows:confused:. I have also created swap disk of 1.86GB

---

### Post by fantab on 2013-10-19
Boot with Ubuntu DVD/USB, open Terminal [Ctrl+Alt+T] and post the output of:

```
sudo fdisk -l
sudo parted -l
```

---

### Post by Muhammad_Mudassir on 2013-10-19
finally i solved the problem by repairing boot info. below.anyone other has the same problem he should install boot repair. link is below.


[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

---

