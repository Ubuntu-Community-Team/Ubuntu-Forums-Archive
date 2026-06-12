---
title: "Grub Errro with PATA Drive"
date: 2007-07-19
forum: Installation &amp; Upgrades
---

### Post by lokeey on 2007-07-19
Hey all, I'm wondering if anyone knows what jumper setttings to use when adding/installing a PATA drive with SATA. I currently have 2 SATA drives; one with XP the other with Edgy. I want to install the PATA as additional storage, but when I boot up I'm getting GRUB ERROR 17.

Thoughts?

---

### Post by dabl on 2007-07-19
Is that PATA drive empty, or does it have a bootable partition on it?  Sounds like maybe your PC is trying to boot from it, and Grub is saying "tilt!".

---

### Post by lokeey on 2007-07-19
Dang! Good question. I'm not really sure. Someone gave me the drive.

---

### Post by dabl on 2007-07-19
Download the ISO and make yourself a GParted Live CD -- get the ISO here: [http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=173828](http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=173828)

Boot the Gparted Live CD, and use that to examine your new drive.  Delete any partitions and make it one big partition, with no boot flag set (unless you want to make several partitions -- that's OK too).

:)

---

### Post by lokeey on 2007-07-19
Dang! Didn't think about doing that! I could've probably used the Kubuntu Live CD, too, right?

coulda, woulda, shoulda!

Oh well! I appreciate the help.

Thanks!

---

### Post by lokeey on 2007-07-19
DANG! Okay, so that didn't go so well. I was able to wipe the drive, but when I rebooted, I got Error 22.

Thoughts?

---

### Post by rbmorse on 2007-07-19
Check your BIOS settings and verify that the hard drive  in the boot device precedence list is correct. It sounds the addition of the PATA drive changed the way the BIOS enumerates the hard drives and GRUB can't find the correct boot partition. 

If the correct hard drive is listed in the BIOS' boot device precedence list,  you need to setup GRUB again. 

Boot from the liveCD and open a terminal window.  Do:
```
sudo grub
```
That should change the prompt to "grub".  Then the following:

```
 find /boot/grub/stage1                     <  the "1" is the number one
```
That will return a value that looks like 

(hdX,Y)

where X and Y are numbers.  Remember the values. Then:

```
root (hdX,Y)
```   where X and Y are the values returned by the find command. This  tells GRUB where the boot partition of your linux installation is now located. Then:
```
setup (hd0)                 < the "0" is the number zero.
```  
This writes the  updated GRUB stub loader (now with the correct boot partition location) to the MBR (first 512 bytes) of the current boot drive. 

```
quit
``` to exit the grub terminal, ```
exit
``` to close the terminal window, and reboot.

---

### Post by lokeey on 2007-07-19
okay, i checked my bios settings and this is what it shows.

1. ch2 - xp drive (master)
2. ch3 - linux drive (master)
3. ch1 - spare (slave)

i followed the steps you laid out for grub and it showed...

grub> find /boot/grub/stage1
 (hd2,0)

grub> root (hd2,0)

grub> setup (hd0)
 Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/e2fs_stage1_5" exists... yes
 Running "embed /boot/grub/e2fs_stage1_5 (hd0)"...  15 sectors are embedded.
succeeded
 Running "install /boot/grub/stage1 d (hd0) (hd0)1+15 p (hd2,0)/boot/grub/stage
2 /boot/grub/menu.lst"... succeeded
Done.

I quit and reboote and I got ERROR 22 again.

---

### Post by rbmorse on 2007-07-19
Ok...do the same drill again, but this time when you get to the instruction
```
setup (hd0)
```
try instead
```
setup (hd1)
```
GRUB can be inconsistent about the way it identifies disks. Sometimes you just have to keep trying different ones until you find the one that works.

---

### Post by lokeey on 2007-07-19
heheheh...I was going to ask that, but wasn't sure, that's why i made sure to post all that info.

thanks again!

---

### Post by lokeey on 2007-07-19
okay...that worked, but now i'm not able to boot into linux. says my partition not found.

i get the grub loader, i see my kubuntu and xp...when i chose kubuntu, partition not found, BUT i can boot into xp just fine.

so what i do wrong?

---

### Post by rbmorse on 2007-07-20
You're probably not doing anything wrong.  We just haven't discovered the right majicks. 

Reboot to the grub menu. Highlight the windows entry and press the "e" key. What are it's values in the part where it says root(hdX,Y)?  Remember them.  

Now, go back to the menu and highlight the kubuntu entry that doesn't work. Press the "e" key, and then press the "e" key again.  Now you can edit the menu entry. Find the part that says root (hdX,Y) and look at X (Y should be 0 if Kubuntu is the only partition on that drive. If it is not, you will have to change the "Y" value to match the location of the partition to which Kubuntu is installed.  Just remember that GRUB starts numbering things at zero, so the first partition is 0, the second partition is "1", etc. ).  

The possible values for X here are 0,1,2.  Look at the "X" value for the windows entry and make this X value something else (If X is 1, then try 2, but it could be 0).  Make the change, I think you hit <enter> here to make it "take" and then hit the "b" key to boot the machine from that entry.  

If it works, you're not finished so don't go away quite yet.  If it doesn't, go back to the kubuntu menu entry and try the remaining value in the root (hdX,Y) -- and check again to make sure your syntax is correct and all of the commas are really commas and not periods, and that no extra spaces have been inadvertently entered. 

I will assume that Kubuntu now boots, but you have to make the change permanent before you're done. 

Navigate to the file:

/boot/grub/menu.lst

If you're in konqueror right click on the file and select "edit as root," otherwise from the start menu select "run a command" and then enter 

kdesu kate 

into the dialog box and then <enter>  Provide your password when prompted, and in kate open the file /boot/grub/menu.lst. 

Many, many lines.  Scroll down about halfway down the file, until you get to the lines that do not start with a "#" character. Look familiar?   Each operating system has a five line section that starts with the line "title"  Find the one for Kubuntu, then within that section find the line that reads

root      (hdX,Y)

and change X here to whatever value worked for X before. Again the "Y" should be zero unless there is more than one partition on this drive and Kubuntu is not installed to the first partition.  Do the same for the next section (recovery mode) and for the memtest86 entry as well. 

save the file.

One more little thing.  Use the find function of the editor to locate the line

#groot=(hdX,Y)

It's about 1/4 of the way from the top of the file.  Make sure that the X and Y values are the same as for the kubuntu entry below. 

Save the file again, close the editor and you should be done.

---

### Post by lokeey on 2007-07-20
by any chance do i need to place jumpers on my pata drive and if so do i set the jumper to SLAVE or MASTER?

---

### Post by rbmorse on 2007-07-21
If it is the only PATA device in the system, it should be connected to the end of the cable (not the middle connector) and jumpered as either "master" or "C/S"

---

