---
title: "Another Grub Error22/ Mulitboot Issue"
date: 2008-03-01
forum: Installation &amp; Upgrades
---

### Post by Spotta on 2008-03-01
Hi

I'll start from the beginning in the hope that someone might be able to help me out.
Before I started 'mucking about' I had XP and Vista x64 dual booting on a raid array. The raid array is the first boot device in my BIOS. I imaged this array before starting.
I decided to add OSX to the mix and succeeded in installing this on a separate 320Gb SATA drive (it didn't recognise my RAID array) and had it triple booting all 3 OS's using Acronis Operating system Selector.
I then tried to install Ubuntu - which I have used before. I had nothing but trouble with the live CD which after a bit of research I discovered was due to my 8800GT. I downloaded the alternate CD (x64) and decided to install with that instead. I figured it would install GRUB, but I have sorted out multi booting before so I wasn't too worried. However - after I had installed Ubuntu - to a partition and swap file on the same SATA drive as OSX - I can't boot it.

If I boot up and do nothing I get
Grub loading stage1.5
Grub loading, please wait
Error 22.

I thought this was a boot device issue after a bit of reading, but no matter what hdd is the first boot device I get this error (1 actually gives me win error ntdr missing instead)
If I boot to the Acronis rescue CD I created from the BIOS boot menu, and then choose Windows (which on acronis means boot from 1st hdd) then I get the Acronis OSS and from there I can boot XP, Vista and OSX fine.
However if I choose Ubuntu from AOSS - I get the same Grub error 22.
I tried to remove GRUB by booting from the XP Disc (fixboot/fixmbr/etc) and also the vista disc (bootrec/etc) but I still got the GRUB error. 
I tried removing using the superGrubDisk - but it was still the same (prolly did something wrong!). Restoring my RAID array from my image taken yesterday gets rid of GRUB and AOSS starts working fine - but I cannot make it see my Ubuntu Install and add it to the options.

I don't mind which method I use of booting as long as I can boot all 4 OS's easily
Can anyone help?

Thanks
Spotta

---

### Post by dstew on 2008-03-01
I believe the answer will be to re-install grub to the Ubuntu partition boot sector. The trick will be to pick the correct root value to give grub when it re-installs. Then you will be able to boot Ubuntu using Acronis.

From the behavior of your system, it seems that grub is installed into the boot sector of the Ubuntu parition, because (I assume) Acronis acts by selecting a partition, and not a disk. So, if there were not grub on the partition, you would get a Acronis error like "No OS available". So, grub stage1 and stage1.5 must be there, or you would get no error message from grub. However, grub stage1.5 is pointing to the wrong partition trying to gets its stage2 and menu.

The partition that contains stage2 can be found using a Live CD, or a Supergrub disk, running grub from the command line. Boot a live CD, and enter```
sudo grub
```That will get you the grub command line with the grub> prompt. You can also select grub command line from the supergrub disk menu. At the grub> prompt enter```
find /boot/grub/stage2
```Hopefully it will return a single value, like (hd0,5). Use this as the root and as the argument for the setup command:```
root (hd0,5)
setup (hd0,5)
quit
```Quit the Live CD session and reboot. You should be able to boot grub from the Acronis menu (might have to configure Acronis to select the Ubuntu parition). If you get a grub menu, good. If the menu doesn't work properly, that can be fixed by editing /boot/grub/menu.lst

---

### Post by Spotta on 2008-03-02
Hi

Thanks for the help. I cant boot from the Live CD (8800GT) When booting from the Supergrubdisk, If I go Boot Gnu/Linux it finds my ubuntu at hd2,5 - If I try and boot it I got error 22 no such partition found hd4,5. find /boot/grub/stage2 - gives me a seconds hdd activity but no reply no matter how long I leave it - and I have to reboot from the cd.

I am going to install Ubuntu again - is there a way to configure GRUB to install to the Partition during the installation from the Alternate CD?

Spotta

---

### Post by dstew on 2008-03-02
Yes. When it gets to the Install Grub screen, I think there is an Advanced button. There, you can direct it to install to the Ubuntu partition. You would need to use a partition name, like (hd2,5) instead of a disk name like (hd0). But you need to know which partition it is. You might consider not installing grub during the installation, and install it later when you can more carefully work out the correct partition name to install to.

---

### Post by Spotta on 2008-03-02
Hi

Thanks for the help, I seem to remember last time GRUB was just installed automatically and I did not get a chance to enter a Advanced section. I'll have a go later on or in the morning and have a look
Thanks again

Spotta

---

### Post by Spotta on 2008-03-03
Hi
I've just installed again. I chose a preformated swap partition (2Gb) and a preformatted 20Gb Data partition, which I set to be bootable and as a mount point for /.
While I was watching the installer, I saw installing GRUB flash up on the screen, at no point could I interupt and set up manually.

Anyway, it is reinstalled, I removed GRUB from mbr of raid by using image, it now boots to AOSS as standard, just need to add GRUB stages to the 20Gb Ubuntu partition - correct?

---

### Post by Trondern on 2008-03-03
> **Spotta said:**
> Hi

 When booting from the Supergrubdisk, If I go Boot Gnu/Linux it finds my ubuntu at hd2,5 - If I try and boot it I got error 22 no such partition found hd4,5. find /boot/grub/stage2 - gives me a seconds hdd activity but no reply no matter how long I leave it - and I have to reboot from the cd.
Spotta

Just a quick note on using Supergrubdisk..If used from a USB drive it adds itself as hd0 so your old hd0 will be hd1 and so on so you have to take that into consideration. I dont know if this is the case if you use it from a floppy or cdr aswell?

---

### Post by dstew on 2008-03-03
> just need to add GRUB stages to the 20Gb Ubuntu partition - correct?Yes, that is correct. But you might have a bit of trouble finding you how grub is reading your system. See the post from Trondem.

You can usually figure out the proper grub-name of the Ubuntu partition by doing some work from the grub command line. If you are installing grub from the supergrub disk, get a grub command line and enter **find /boot/grub/stage1**. That will give you the name of the root partition in grub-language, with the supergrub disk in place. You can use that name as the root in the commands to install grub. Lets say it gives you (hd3,0). Then setup grub to boot in that partition like this:```
root (hd3,0)
setup (hd3,0)
quit
```Quit supergrub, and remove the disk. Reboot, and try to boot with Acronis. You should at least get the grub menu. The menu items might not work properly, but that is another thing that is easy to fix by editing /boot/grub/menu.lst.

---

### Post by Spotta on 2008-03-03
Hi

It found it at (hd3,5) I typed in all commands, all seemed successful, all other 3 OS's boot - not ubuntu - AOSS cannot find it either when I tell it to look in the same partition

Spotta

---

### Post by dstew on 2008-03-03
> AOSS cannot find it either when I tell it to look in the same partitionI don't know much about Acronis. Do you need to set the boot flag in the partition in order for Acronis to recognize it as bootable? You can set the flag with gparted I believe.

Can you boot the Ubuntu partition using the supergrub disk? Can you set your BIOS to boot the Ubuntu partition? Just to see if it indeed is bootable...

---

### Post by Spotta on 2008-03-03
Hi

If I boot from supergrub disk and choose Boot GNU/Linux its finds
6 hdd6 sdd6 (hd3,5) ext2fs Ubuntu 7.10 \n \l
When I choose it, it gives me memtest, recover or ubuntu - then gives an error saying 
Booting 'Ubuntu 7.10, kernel 2.6.22-14-generic'
root (hd4,5)
Error 21: Selected disk does not exist.

I notice the different hd number - how do I fix this?

Spotta

---

### Post by dstew on 2008-03-03
This is actually good news. It means that the partition is being booted, and the only problem left is to configure the grub menu.lst file. To edit this file, you just need a text editor.

Before we can edit /boot/grub/menu.lst, you have to be able to access it. Since Windows probably cannot read the Ubuntu partition, we will have to edit the file from the Live CD system. And, in order to edit the file on the Live CD system, we will have to mount the hard disk Ubuntu onto the Live CD file system. And, in order to that we need to know the name of the partition in Linux. We are done with grub.

To get the name of the partition in Linux, boot the Live CD, open a terminal window, and enter the command```
sudo fdisk -l
```That will list all the partitions that Linux can see. My guess is that it will call the hard disk Ubuntu /dev/sdd6 (or maybe hdd6). If /dev/sdd6 is the partition name, you mount it to the Live CD file system like this. First, you need to create a mount point, which is just a directory in the file system:```
sudo mkdir /mnt/sdd6
```Then, mount the Ubuntu partition to the mount point:```
sudo mount -t ext3 /dev/sdd6 /mnt/sdd6
```Now you can open and edit the menu.lst file using a text editor like gedit:```
gksudo gedit /mnt/sdd6/boot/grub/menu.lst
```Look at the bottom of the file. Change the root statements from (hd4,5) to (hd3,5). Also, at the top of the file, find #groot and change that also. (Leave the # in front, it is not a comment.) Then save the file, quit gedit and quit the Live CD. Reboot and see if it works now.

Sorry, it is a long explanation. If you want to take it one step at a time let me know and I can go slower.

---

### Post by Spotta on 2008-03-03
Hi

Thats a perfect explanation, explaining exactly what needs to be done. My only problem is that I can not boot from the Live CD due to my 8800GT graphics card. its the only reason I had to use the alternate CD.

Is there a way of doing this via supergrubdisk or gparted or another text based Live CD?
if not, I can borrow my old 7900GT back from my m8 who bought it....

Spotta

---

### Post by dstew on 2008-03-03
I don't think that either the supergrub disk, nor gparted has a text-editor program. There is a Live CD called Knoppix that many people use as a kind of rescue CD when the Ubuntu Live CD won't work. Check it out [here]("http://www.knopper.net/knoppix-info/index-en.html").

---

### Post by Spotta on 2008-03-03
Hi

I'm downloading Knoppix now, I'll try to run the commands you suggest and let you know how I get on.
Thanks for the help

Spotta

---

### Post by Spotta on 2008-03-03
Hi

Knoppix cd booted up fine.

> **dstew said:**
> 
To get the name of the partition in Linux, boot the Live CD, open a terminal window, and enter the command```
sudo fdisk -l
```That will list all the partitions that Linux can see. 

gets result
' Unable to seek on /dev/sda' -  I take it /dev/sda is the cd - how do get it to look elsewhere?

Spotta

---

### Post by dstew on 2008-03-03
Not being familiar with Knoppix, I don't really know. BUT on my way home I realized I kind of led you astray (forgive me). You did not need to download Knoppix after all. You can edit your /boot/grub/menu.lst from your own Ubuntu install! Here's how:

Go ahead and boot the hard disk Ubuntu system. You get the grub menu with the three choices. Now, instead of pressing enter to try to boot Ubuntu, just highlight it (which it probably already is) and press 'e'. This allows you to edit the boot statements in the menu.lst file temporarily. Now, highlight the root statement and press 'e' again. This will let you edit the line. Change the root argument from (hd4,5) to (hd3,5). Press enter. Now press 'b' to boot. Now Ubuntu should boot. Once Ubuntu has booted, edit the /boot/grub/menu.lst file using gedit. You do not have to mount the partition, since it is the root partition of the Ubuntu system and already mounted. So your gedit command will be just```
gksudo gedit /boot/grub/menu.lst
```Edit and save as in my post above, and you should be all set.

---

### Post by Spotta on 2008-03-04
Done it! I am now successfully quad booting all 4 OS's!
Without people like yourself helping out on the forums, taking time to go through and explain problems half of the people using Ubuntu probably wouldn't be! thanks for the great help

Now I start trying to get my 8800GT working properly and hopefully my 8600GTS as well, so I can get all three screens active as in Win =]

Spotta

---

### Post by dstew on 2008-03-04
Thanks, and best wishes.

---

