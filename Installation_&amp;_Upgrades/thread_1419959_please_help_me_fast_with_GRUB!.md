---
title: "please help me fast with GRUB!"
date: 2010-03-02
forum: Installation &amp; Upgrades
---

### Post by Durduman on 2010-03-02
Hello all! Noob here. I have this problem: after installing ubuntu 9.10 on external HDD I cannot boot vista if external usb is unplugged(where ubuntu is installed). it says grub loading and after that recover grub ( i think that is what is says ... not certain in this moment ) anyway hope you get my dilemma. If you need more information I'll be glad to provide it. Thank you in advance!

---

### Post by darkod on 2010-03-02
Plug the ext, boot into ubuntu and in terminal run:

sudo fdisk -l

Post the results. The fix is easy, just show us the partitions as reported by fdisk.

---

### Post by Durduman on 2010-03-02
isk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x8e538e53

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        5992    48128000    7  HPFS/NTFS
/dev/sda2            5992       38914   264440832    7  HPFS/NTFS

Disk /dev/sdb: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x5b6ac646

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       37784   303499948+  83  Linux
/dev/sdb2           37785       38913     9068692+   5  Extended
/dev/sdb5           37785       38913     9068661   82  Linux swap / Solaris

---

### Post by presence1960 on 2010-03-02
> **Durduman said:**
> isk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x8e538e53

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        5992    48128000    7  HPFS/NTFS
/dev/sda2            5992       38914   264440832    7  HPFS/NTFS

Disk /dev/sdb: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x5b6ac646

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       37784   303499948+  83  Linux
/dev/sdb2           37785       38913     9068692+   5  Extended
/dev/sdb5           37785       38913     9068661   82  Linux swap / Solaris

Boot with the external plugged in. boot into Ubuntu @ the GRUB menu. Open a terminal when the desktop loads and run ```
sudo dpkg-reconfigure grub-pc
```Hit enter at each window until the last where you will choose sdb. Use your arrow keys to navigate to sdb and the space bar to select sdb. 

Now to fix the MBR of the internal disk. Run in terminal ```
sudo apt-get install lilo
```Then in terminal run ```
sudo lilo -M /dev/sda mbr
```

You will now be good to go, you just need to set the external to boot before the internal in BIOS. When you boot without the external windows will boot. when you boot with the external plugged in GRUB will take over and you can boot into ubuntu
That will fix MBR of the internal disk so it boots right to windows.

---

### Post by meierfra. on 2010-03-02
> Use your arrow keys to navigate to sdb and the space bar to select sdb. 
Just to clarify: You also need to deselect sda.

---

### Post by Durduman on 2010-03-02
[FONT=monospace] sudo apt-get install lilo
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package lilo is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package lilo has no installation candidate

[/FONT]

---

### Post by Durduman on 2010-03-02
installed lilo :D

---

### Post by Durduman on 2010-03-02
:(( cannot see HDD. I can only use vista for the moment :(((((((      i cant even see the hdd in vista anymore :((((

---

### Post by darkod on 2010-03-02
> **Durduman said:**
> :(( cannot see HDD. I can only use vista for the moment :(((((((      i cant even see the hdd in vista anymore :((((

The linux partitions don't show in Computer. If you open Disk Management can you see both disks there?

---

### Post by Durduman on 2010-03-02
yes they are seen in vista. I've put booting order : 1st ubuntu (external usb hdd) 2nd vista (normal hdd)

---

### Post by darkod on 2010-03-02
> **Durduman said:**
> yes they are seen in vista. I've put booting order : 1st ubuntu (external usb hdd) 2nd vista (normal hdd)

And that still boots vista directly? I guess you don't have grub2 on the ext hdd MBR.

The external hdd is also 320GB, the one called /dev/sdb in your results file with the ubuntu partitions on it, right?

If this is right, boot again from the ubuntu cd into the live desktop, with the ext hdd connected, and run:

sudo mount /dev/sdb1 /mnt
sudo grub-install --root-directory=/mnt/ /dev/sdb

Restart without the cd and see if that will boot grub2 from the ext hdd.

---

### Post by Durduman on 2010-03-02
now... even if I can boot from external it starts vista... what to do ?

---

### Post by darkod on 2010-03-02
> **Durduman said:**
> now... even if I can boot from external it starts vista... what to do ?

It can't be, not if the computer is capable of booting from usb.

Boot again the live desktop and follow these instructions to run the script. Post the content of your results file, just to make sue everything is in place.
[http://ubuntuforums.org/showpost.php?p=8844901&postcount=4](http://ubuntuforums.org/showpost.php?p=8844901&postcount=4)

---

### Post by meierfra. on 2010-03-02
> Device Boot Start End Blocks Id System
/dev/sdb1 1 37784 303499948+ 83 Linux
/dev/sdb2 37785 38913 9068692+ 5 Extended
/dev/sdb5 37785 38913 9068661 82 Linux swap / Solaris


You don't have a boot flag anywhere on /dev/sdb. That sometimes prevents booting from that drive. So boot from the LiveCD and run

```
sudo sfdisk -A1 /dev/sdb
```

Then reboot.

---

### Post by Durduman on 2010-03-04
hm... well tried to sudo sfdisk -1 /dev/sdb and then restart .. and nothing...
... btw... when I restart computer and then enter F8 to see boot order, I don't always see external HDD tough it is connected. ( evan when I see it I cannot boot linux from it just to make it clear).

---

### Post by Durduman on 2010-03-04
I'll reinstal linux... and come back to my 1st problem, easier this way. now if I see the external and try to boot from him... it says "missing operating system". Awaiting answers to my 1st problem regarding how to automatically start vista when external hdd not plugged in :).

---

### Post by Durduman on 2010-03-04
:(( din't solve anything.... crappy stuff ... tried to reinstall linux.... I did, but now i have the same problem.. if I boot external HDD it boots vista :((

---

### Post by darkod on 2010-03-04
> **Durduman said:**
> hm... well tried to sudo sfdisk -1 /dev/sdb and then restart .. and nothing...
... btw... when I restart computer and then enter F8 to see boot order, I don't always see external HDD tough it is connected. ( evan when I see it I cannot boot linux from it just to make it clear).

If you can't always see the usb hdd, that might point to connectivity issue. If it's not working properly, no surprise if it doesn't boot from it.

Have you checked in BIOS for USB Legacy or similar setting? I'm not sure whether that has to be enabled for the BIOS to see the usb hdd while it still hasn't started loading windows.

Also, are you sure you can boot from usb? I guess you have the USB HDD option in boot devices in BIOS.

---

### Post by Durduman on 2010-03-04
new installation this day :) this time i installed grub from that option.. instal boot progr.... or smt...  anyway.. this time... it boots just fine and I dont have connectivity problem with usb ( never had ) and nothing else indicates this. Anyway... my ubuntu starst just fine now when I choose it from grub. now going back to earlier problem .... if I don't plug in my external HDD is says 
GRUB loading
errorL no such disk
grubrescue>

so how do I overcome this... I may not always have external at me ... and I need vista as well as I need Ubuntu. Please Help Me Still! :D

---

### Post by darkod on 2010-03-04
> **Durduman said:**
> new installation this day :) this time i installed grub from that option.. instal boot progr.... or smt...  anyway.. this time... it boots just fine and I dont have connectivity problem with usb ( never had ) and nothing else indicates this. Anyway... my ubuntu starst just fine now when I choose it from grub. now going back to earlier problem .... if I don't plug in my external HDD is says 
GRUB loading
errorL no such disk
grubrescue>

so how do I overcome this... I may not always have external at me ... and I need vista as well as I need Ubuntu. Please Help Me Still! :D

You're back where you started. Grub2 is on your internal hdd, and BIOS can find it just fine. But grub config files are on your ubuntu partition on the external, and without it it doesn't work.

One solution that I wanted to suggest is: make a small /boot partition on the internal hdd, the boot files will be in it. Pur grub2 again on your int hdd as it is now. But because it will be able to find the boot files even without the ext hdd, you can boot without it. Of course, you can boot vista without it, not ubuntu because it's installed on th ext hdd.

If you want to try this and have further questions, just ask.

---

### Post by Durduman on 2010-03-04
sounds like a good idea. but making a small partition on my internal is against my prehistoric problem ..... not formatting any partition :)). I would be interested in how to put some program that can do the booting directly from internal without partitioning. ( just making this clear, i want to know how to boot vista without external. if that is possible ).

---

### Post by Durduman on 2010-03-04
again...I dont want to format, cand I make a new partition without formatting? and how do i get grub on it?

---

### Post by darkod on 2010-03-04
> **Durduman said:**
> again...I dont want to format, cand I make a new partition without formatting? and how do i get grub on it?

You can shrink small amount of the existing partition(s), you need only about 200MB-250MB. Leave that space as unallocated.

I don't know another way except reinstalling ubuntu and you would have to use the manual partitioning option to specify that 200MB space as ext4 /boot, then on your external your large / partition and small swap partition.

But note that in this case you will not be able to boot the ext hdd on another computer, because the grub files will be on your int hdd. If that's what you planned, to have the hdd to move around, that won't work.

---

### Post by presence1960 on 2010-03-04
> **Durduman said:**
> hm... well tried to **_sudo sfdisk -1 /dev/sdb_** and then restart .. and nothing...
... btw... when I restart computer and then enter F8 to see boot order, I don't always see external HDD tough it is connected. ( evan when I see it I cannot boot linux from it just to make it clear).

you got the command wrong it is ```
sudo sfdisk -**A1** /dev/sdb
```

---

### Post by presence1960 on 2010-03-04
> **Durduman said:**
> **_sounds like a good idea. but making a small partition on my internal is against my prehistoric problem ..... not formatting any partition :))._** I would be interested in how to put some program that can do the booting directly from internal without partitioning. ( just making this clear, i want to know how to boot vista without external. if that is possible ).

you may have to give up on that condition. Out of curiosity why are you against formatting/creating a partition?

---

### Post by Durduman on 2010-03-04
d: ...photoes music videos.. and all of that... c: vista and progr....  lazy nes nes nes nes

---

### Post by Durduman on 2010-03-04
I think when I typed it in it was with A1
if you think that is my sollution i willl repeat the steps from the earlier posts and then do this A1 stuff


 	Code:
 	sudo dpkg-reconfigure grub-pc

 Now to fix the MBR of the internal disk. Run in terminal  	Code:
 	sudo apt-get install lilo 
Then in terminal run  	Code:
 	sudo lilo -M /dev/sda mbr

---

### Post by darkod on 2010-03-04
> **presence1960 said:**
> you may have to give up on that condition. Out of curiosity why are you against formatting/creating a partition?

I believe it's misunderstanding. I guess the OP means he doesn't want to format the whole disk.

Shrinking one partition and creating a small partition from that space would not require deleting all data on your disk. :)

However, it's always wise to have backup before any partitioning operations.

---

### Post by Durduman on 2010-03-04
:D thats it! I odnt want to loose all the data! thank you!!!!!!!!  :D so... what are the steps I need to follow?

---

### Post by meierfra. on 2010-03-04
It should be enough to just create a   grub folder on the Windows partition rather than creating a boot partition:


```
sudo mount /dev/sda1 /mnt
cd /mnt
sudo mv [Bb][Oo][Oo][Tt] boot
```

The last command renames your Boot folder  to "boot" . Which is necessary to avoid confusion between a  "Boot" and "boot" folder.  

```
sudo grub-install --recheck --root-directory=/mnt /dev/sda
sudo cp /boot/grub/grub.cfg /mnt/boot/grub 
```

Reboot with the external drive detached. You should get the Grub menu and be able to boot into Vista from the Grub menu.

---

### Post by Durduman on 2010-03-05
done and... done ! :D I just want to thank all of you out there... mom... god... and of course ubuntu-forums users :D ( this was the 1st thing solved on forums by me ) .... so happy ... really now... thanks alll maneget to install grub on internal drive and it works just fine ! Thank you!

---

### Post by meierfra. on 2010-03-05
> managed to install grub on internal drive and it works just fine 
Great.  Enjoy Vista and Ubuntu.

---

