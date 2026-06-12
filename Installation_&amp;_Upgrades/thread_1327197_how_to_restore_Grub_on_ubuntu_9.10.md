---
title: "how to restore Grub on ubuntu 9.10"
date: 2009-11-15
forum: Installation &amp; Upgrades
---

### Post by shahan on 2009-11-15
I am using 9.10 on ext4 filesystem
however..I also use Windows Xp on my PC
Yesterday I installed Windows Xp again due to some problem on XP. After that I tried to setup grub using Live CD of ubuntu 9.10. But I failed....
how I tried:
Application>Access.....>Terminal
Then..
sudo grub


find  /boot/grub/stage1
where I get  (hd0,*)   *=1,2,3,4 etc..

THen 
grub> root (hd0,*)
grub> setup (hd0)
grub>   quit

By this procedure I recovered my ubuntu 8.04.2 LTS...but it is not working on ubuntu 9.10
what to do? So far I know it is GRUB2...May be for this reason it is not working...
Waitting for reply...

---

### Post by sisco311 on 2009-11-15
You have to chroot in your 9.10 installation and reinstall grub2.

Here is a guide: [thread=1195275]Grub 2 Basics[/thread] (*Reinstalling GRUB 2 from LiveCD*).

---

### Post by shahan on 2009-11-15
> **sisco311 said:**
> You have to chroot in your 9.10 installation and reinstall grub2.

Here is a guide: [thread=1195275]Grub 2 Basics[/thread] (*Reinstalling GRUB 2 from LiveCD*).
Thank you for ur company...

I tried the method u suggest me..
but it is not working for me(may be my fault).
Is there any easy solution to make it recover(Like Graphical Solution)?

---

### Post by oldfred on 2009-11-15
The link from sisco311 should work.

several other links:
reinstall grub2 
[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202) 
[https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD](https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD) 
[http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#Re-install_GRUB_from_Live_CD](http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#Re-install_GRUB_from_Live_CD)

---

### Post by thedaver on 2010-01-19
I had this happen on a Mythbuntu 9.10 install...

I redid my grub install over and over... then I checked and found that the BIOS for my box had been adjusted so that the first HDD had somehow become THIRD in the boot order of HDDs.  Once I realized that my boot order had been altered... Well, when I fixed it, grub seemed to work really well  ;-)

---

### Post by mpande on 2010-03-14
[LIST=1]
[*]Boot from the** CD/USB** flash drive from which you installed Ubuntu
[*]Open terminal (It is there under *Accessories*)
[*]type in sudo fdisk -l
[*]then type sudo mount /dev/sdMP /mnt , where **M** is your drive and **P** is your linux partition. For instance sudo mount /dev/sda5 /mnt
[*]install GRUB again by typing this ...
[*]sudo grub-install --root-directory=/mnt /dev/sdA , where A is your drive. So you may type sda
[*]Now type sudo umount /mnt. So as to unmount the volume.
[/LIST]

---

### Post by presence1960 on 2010-03-14
> **shahan said:**
> I am using 9.10 on ext4 filesystem
however..I also use Windows Xp on my PC
Yesterday I installed Windows Xp again due to some problem on XP. After that I tried to setup grub using Live CD of ubuntu 9.10. But I failed....
how I tried:
Application>Access.....>Terminal
Then..
sudo grub


find  /boot/grub/stage1
where I get  (hd0,*)   *=1,2,3,4 etc..

THen 
grub> root (hd0,*)
grub> setup (hd0)
grub>   quit

By this procedure I recovered my ubuntu 8.04.2 LTS...but it is not working on ubuntu 9.10
what to do? So far I know it is GRUB2...May be for this reason it is not working...
Waitting for reply...

Need more info about your setup so I can give you two precise commands to run to reinstall grub. Let's get a better look at your setup & boot process. Boot the Ubuntu Live CD/USB. Choose "try ubuntu without any changes", when the desktop loads come back here and do the following:

1. Download the boot info script. There is a link in my signature.
2. Once downloaded move the boot info script to the desktop.
3. Open a terminal and run the command ```
sudo bash ~/Desktop/boot_info_script*.sh
```

  This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text. 

See [here]("http://bootinfoscript.sourceforge.net/") for more info on the boot info script.

Above link is to meierfra's Sourceforge web page.

---

### Post by Zleep-Dogg on 2010-03-29
Just had a similar problem (although a lot simpler) after adding a 9.04-install in order to use my usb-modem...

I let the MBR get overwritten, thinking this was fastest in the situation and I could always restore the 9.10 to be "primary boot" later... And after quite a bit of reading, the solution was so simple though noone wrote it directly...

If you can boot in the system from which you intend to control grub2 (eg. the 9.10 install in my case), the solution is as simple as booting into this and typing
```
sudo grub-install /dev/sdX
```
where X is of course the letter of the drive on which the MBR should be written (eg. sda to use the first harddrive)

Obviously you might want to add
```
sudo update-grub
```
in order to update the list of bootable systems

---

### Post by pritam_par on 2011-08-06
Check out this Ubuntu forum thread for step to step installation of Grub[http://ubuntuforums.org/showthread.php?p=11124764#post11124764](http://ubuntuforums.org/showthread.php?p=11124764#post11124764)
This issue is solved here.

_______________________________________________________________

[My blog on Open source]("http://opensource-sidh.blogspot.com/")

---

