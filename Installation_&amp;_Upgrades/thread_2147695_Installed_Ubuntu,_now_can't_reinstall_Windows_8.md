---
title: "Installed Ubuntu, now can't reinstall Windows 8"
date: 2013-05-22
forum: Installation &amp; Upgrades
---

### Post by David Matthew on 2013-05-22
Hi guys,

I installed Ubuntu 13.04 on a Lenovo Ideapad Z580 which had been running Windows 8. In retrospect I should have gone with a dual-boot, because I now need Windows 8 back. Don't worry, I'm not turning my back on Ubuntu - I'm writing this on a Macbook running Ubuntu 12.10 without any problems. :-)

I have the Lenovo recovery cds, but the problem is that when I select to boot from the DVD drive, it goes straight to the GRUB screen. It won't boot from the recovery disks, so I don't know how I'll manage to get Windows 8 back up and running.

Any help would be really appreciated.

---

### Post by ubu_dynamite on 2013-05-22
If you wiped the complete drive there is nothing to recover you will need a windows 8 install disk.

---

### Post by fantab on 2013-05-22
Contact Lenovo and tell them that you want your laptop restored to factory settings and install.

---

### Post by aravindev on 2013-05-23
Do you mean that you cant see the windows 8 boot in option??
in that case try installing the grub once again by using a Ubuntu live installation CD/USB

---

### Post by David Matthew on 2013-05-23
Hi guys,

Thanks for the replies.

Just to clarify - I'm aware that Windows 8 is nowhere to be found on my machine. This is why I'm using the recovery disks to try to reinstall it.

The Lenovo recovery cds = Windows 8 OEM + Lenovo Bloatware. Lenovo don't provide just a Windows 8 dvd. 

In terms of it getting reset to the factory state, that's exactly what I'm trying to achieve, and to that end, I had to actually purchase these recovery cds from Lenovo, which are created for exactly that purpose.

The problem is this: I have the first of the recovery cds in the drive, I shut down and restart. I press f12 and this gets me to the boot menu. From there I can select the DVD drive. However, when I do, it loads for a second before going straight on to the GRUB screen.

My question is, why isn't it allowing me to boot from DVD? How can I fix this?

Thanks a mill for your input.

---

### Post by ubu_dynamite on 2013-05-23
Think the recovery cds work like the windows upgrade cds it only lets you recover or upgrade when it finds a preexisting windows install.
But i could be wrong.

---

### Post by fantab on 2013-05-23
> **David Matthew said:**
> Hi guys,

Thanks for the replies.

Just to clarify - I'm aware that Windows 8 is nowhere to be found on my machine. This is why I'm using the recovery disks to try to reinstall it.

The Lenovo recovery cds = Windows 8 OEM + Lenovo Bloatware. Lenovo don't provide just a Windows 8 dvd. 

In terms of it getting reset to the factory state, that's exactly what I'm trying to achieve, and to that end, I had to actually purchase these recovery cds from Lenovo, which are created for exactly that purpose.

The problem is this: I have the first of the recovery cds in the drive, I shut down and restart. I press f12 and this gets me to the boot menu. From there I can select the DVD drive. However, when I do, it loads for a second before going straight on to the GRUB screen.

My question is, why isn't it allowing me to boot from DVD? How can I fix this?

Thanks a mill for your input.

I am not really acquainted with OEM recoveries. However, you can wipe your HDD clean, meaning delete all partitions, leave only 'unallocated' space and try the recovery. That ways windows don't have to deal with ext4 partitions, which it can't anyways.

If you intend to install Ubuntu again then before doing so Read: [http://ubuntuforums.org/showthread.php?t=2145558&p=12650379#post12650379](http://ubuntuforums.org/showthread.php?t=2145558&p=12650379#post12650379)

---

### Post by groggin on 2013-05-23
sounds like you need to enter your machine's **BIOS** and set things to boot from the optical drive. start/reboot, tap [del] while it's turning on, you should enter a DOS-like environment where you can use the arrow keys to make changes.

   set the first boot device to CD/DVD drive, the second device should be the drive you will install windows on, or another removable, like usb, but be sure the windows destination drive is on the list

after you install windows, re-install ubuntu in dual-boot config and you're done  :P

just re-read it and saw this:
> The problem is this: I have the first of the recovery cds in the drive, I shut down and restart. I press f12 and this gets me to the boot menu. From there I can select the DVD drive. However, when I do, it loads for a second before going straight on to the GRUB screen.

 that is a **one time** entry, i believe; whereas the instructions i gave you will enable a 'permanent' change. may make the difference

---

### Post by David Matthew on 2013-05-23
> **groggin said:**
> sounds like you need to enter your machine's **BIOS** and set things to boot from the optical drive. start/reboot, tap [del] while it's turning on, you should enter a DOS-like environment where you can use the arrow keys to make changes.

   set the first boot device to CD/DVD drive, the second device should be the drive you will install windows on, or another removable, like usb, but be sure the windows destination drive is on the list


Thanks groggin, I managed to get into the BIOS and rearranged the boot priority as advised. Unfortunately when it tries to boot the recovery cd still isn't doing anything, and I'm being brought to the same GRUB screen as before.

[QUOTE=ubu_dynamite]Think the recovery cds work like the windows upgrade cds it only lets  you recover or upgrade when it finds a preexisting windows install.[/QUOTE]

I'm starting to think this too.

[QUOTE=fantab]However, you can wipe your HDD clean, meaning delete all partitions,  leave only 'unallocated' space and try the recovery. That ways windows  don't have to deal with ext4 partitions, which it can't anyways.[/QUOTE]

How would I go about wiping clean the HDD? Can this be done from within the BIOS? Or would I need to try to reinstall Ubuntu selecting the 'something else' option and wiping the partitions from there?

Thanks again guys, these forums are very helpful places. Nice that it's all in-keeping with the underlying ubuntu philosophy of 'humanity to others'. :)

---

### Post by ubu_dynamite on 2013-05-23
You could run the ubuntu livecd and use gparted or any other partitioning program to wipe the drive.

Try ubuntu without installing option.

---

### Post by Mark Phelps on 2013-05-23
It could be that it reads the first disk, then scans the drive -- and when it sees the Linux partitions, gets all confused and stops the recovery process.  IF this is true, then removing all the partitions from the drive should work.

If that doesn't work, then it could be trying to read the first disk, and when that fails, it's falling back to reading the hard drive.

If you get this second problem, I would suggest you contact Lenovo support (where you got the CDs) and ask them about the problem. You paid for their disks, they should work!

---

### Post by David Matthew on 2013-05-23
I'm currently have GParted open via the 13.04 LiveCD. I've deleted two partitions: a fat32 (94MB) and an ext4 (923.56GB), but one partition remains which GParted isn't allowing me to delete: linux-swap (7.86GB).

Is there a way to delete this, or should I leave it?

---

### Post by groggin on 2013-05-23
> How would I go about wiping clean the HDD? Can this be done from within the BIOS? Or would I need to try to reinstall Ubuntu selecting the 'something else' option and wiping the partitions from there?

 that's it - 'something else', then delete the partitions one by one,  create a partition big enough for windows + any software you'll install, format,  install windows. that done, reboot w/ubuntu in the drive and wish you good luck. just be sure you install windows first

  i just recently re-installed vista on a lappie from the recovery CDs i made from windows, it all went well and is dual booting w/ubuntu (artistx) and ya, spent about an hour removing the bloatware   ;)

---

### Post by arpanaut on 2013-05-23
To be able to remove the swap partition you will need to unmount the swap with gparted.
right click the swap part. and select swapoff then you should be able to delete that part.

Edit: also I think that windows 8 can only be installed with eufi and secure boot enabled in bios set up.
I'm not positive but remember reading that somewhere.

---

### Post by Arny006 on 2013-05-23
> **arpanaut said:**
> To be able to remove the swap partition you will need to unmount the swap with gparted.
right click the swap part. and select swapoff then you should be able to delete that part.

Edit: also I think that windows 8 can only be installed with eufi and secure boot enabled in bios set up.
I'm not positive but remember reading that somewhere.

   Absolutely correct.
 

 Since you had wiped the HDD/SSD you have now a RAW-HDD/SSD, hence you need to install Win 8 and Linux from Scratch.

 

 **Notes 1:** Assure you disable (after the installation) „Win 8“-„Quick-Start“. This new Microsoft-feature allow Win to start quick indeed copy all needed files in the RAM. In fact here is not a „start“ but a „restart“ from a „deep-sleep-modus“.

 If you start Linux after this apparently „Win-shutdown“ and afterwards start „Win“ again, the result is a corrupted „Win“
 

 **Notes 2:** Since „Win 7“ and EFI/UEFI all 64 Bit OSs use GPT instead of MBR partition-table and specifics UUID for the GUID. The installation is done not more on one unique Partition like in „Win XP“ and „Vista“ 32 Bit but on different partitions. For more information see: [http://de.wikipedia.org/wiki/GUID_Partition_Table](http://de.wikipedia.org/wiki/GUID_Partition_Table) [http://technet.microsoft.com/en-us/library/hh824839.aspx](http://technet.microsoft.com/en-us/library/hh824839.aspx) and [http://technet.microsoft.com/en-us/library/hh825686.aspx](http://technet.microsoft.com/en-us/library/hh825686.aspx)

 

 **Reccomandations:**  

 **1)** Use „Win PE“/“Win RE“-“DiskPart“ to make the partitions for „Win 8“ indeed you follow the how to from here [http://technet.microsoft.com/en-us/library/hh825686.aspx](http://technet.microsoft.com/en-us/library/hh825686.aspx)

  and **double the size of EFI-partition** in order to can host also „Grub2“ later on.

 **2)** Let enough unpartitioned places for the two Linux-partitions „swap“ and „/“=“root“=Linux-data-partition.

 **3)** Use „GParted-Live“ or „gparted“ to make the Linux-partitions. If you want not waste a CD for „GParted-Live“ install „gparted“ on the Live-DVD/USB with following terminal-command: "sudo apt-get -y install gparted" (without the two quotes " ")

 

 **Plan:**

 **1)** Make the Win-partitions following the recommendations in the link above.

 **2)** Install „Win 8“ and disable „Quick-Start“ in the „System-settings“ afterwards.

 **3)** Make the „Linux-partitions“ with „gparted

 **4)** Install Linux by assigning the „swap“ and „/“=root-“Linux-data-partition“

 

 Enjoy

---

### Post by David Matthew on 2013-05-28
Thanks for all the help.

I managed to get Windows 8 installed again using the recovery cds. I had used GParted to wipe clean the HDD, but still the cds wouldn't boot. I then tried booting with legacy mode enabled in the bios, and then they finally started loading. I hadn't thought to do that before.

---

### Post by Mark Phelps on 2013-05-28
Glad to see you got it working.

Once you have your system setup with all the apps installed, consider using the free version of Macrium Reflect (windows app) to image off the install to an external drive.

Also use the option to create and burn a Linux Boot CD.

That way, if you run into problems again, you'll have an easy way to restore a working system.

---

