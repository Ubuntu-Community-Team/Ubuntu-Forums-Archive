---
title: "Ubuntu grub rescue live cd problem"
date: 2011-07-02
forum: Installation &amp; Upgrades
---

### Post by Sarath1989 on 2011-07-02
I have a Pentium 4 desktop running on windows 7. Last week I installed Ubuntu along with Windows. (booted from the Ubuntu DVD and Installed. Both operating systems were working fine. Yesterday I booted into windows and while watching Youtube then Mozilla firefox as well as the PC got hanged. I waited almost 15minutes to respond. Then I pressed the Restart button. It restarted but  instead of showing the boot menu, it directly showed windows logo and ” windows is starting message”. I waited for half an hour to load. It didn’t boot. I restarted the PC several times but the same thing happened. 
  

I tried the windows recovery disk. I can boot from the DVD but it also shows the splash screen that something loading for 1 hour. There is no change.
  

I tried to install windows again but the installation stuck at windows is starting screen.
  

Then I restarted without any DVD in the drive. It says like :
  “Veryfying DMI Pool Data……….
  Bootfrom CD:
  Error: file not found.
  Grub rescue>”
  

I tried to boot from a free USB partition manager  from Parted magic.com
  It loads some files and says :
  “[136.263910] Panic occurred, switching back to text console”
  

I read the Ubuntu forums about this problem and successfully boot from live cd. Typed sudo fdisk –l in terminal.  There I see a lot of linux partitions. I don’t know what to do next. [IMG]http://imageshack.us/photo/my-images/825/110703105755.jpg/[/IMG]A picture is attached.
  
Originally there were three partitions.[IMG]http://http://imageshack.us/photo/my-images/825/110703105755.jpg/[/IMG]
  The hard disk is not dead. But I don’t know what the problem is. The HDD is Seagate 500GB. (ST3500418AS). I have a lot of music files and photos in it. I like to recover it. If there is no other way Im ready to format the hdd. Please help. How can I bring it back to normal state.

---

### Post by Rubi1200 on 2011-07-02
If you can boot with the Ubuntu CD, please do the following so we can see what is going on:

Boot the Ubuntu Live CD/USB. Choose the option "Try Ubuntu without any changes." Once the desktop loads come back here and do the following:

1. Download the boot info script which is in a zipped file. There is a link in my signature.
2. Once downloaded, move the boot info script by either copying or dragging and dropping the zipped folder onto the desktop and unzip the contents by using right-click Extract here.
3. Open the folder and copy the script to the desktop (you can also drag and drop if you like)
4. Open a terminal and run the following command

```
sudo bash ~/Desktop/boot_info_script.sh
```

This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here in a new post. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

---

### Post by Sarath1989 on 2011-07-02
I tried it several times. Booting after 30 seconds it becomes so slow. It takes more than 15 minutes to show the accesories list. The terminal is not even loading. I can see the hard drive is divided in to 60 partitions.

---

### Post by YesWeCan on 2011-07-02
Good grief - look at all those duplicate partitions!
What version of Ubuntu did you install?
It looks as if the installer, or something, ran a muck and this caused you Windows installation to run out of disk space, or something.
I can think of one immediate remedy and that is to fix the partition table of the disk.

If you can, would you boot a live CD and run:
[COLOR=DarkGreen]sudo dd if=/dev/sda bs=1 count=64 skip=446 | hexdump -C[/COLOR]
and post the output? If you are hand-copying, just post the numbers in the first and sixth columns, eg:

[FONT=Courier New][COLOR=Blue]00000000[/COLOR]  80 01 01 00 [COLOR=Blue]07[/COLOR] fe ff ff  3f 00 00 00 40 79 7d 0d  |........?...@y}.|
[COLOR=Blue]00000010[/COLOR]  00 fe ff ff [COLOR=Blue]83[/COLOR] fe ff ff  c9 ab 7d 0d 37 0c 4f 09  |..........}.7.O.|
[COLOR=Blue]00000020[/COLOR]  00 fe ff ff [COLOR=Blue]82[/COLOR] fe ff ff  00 b8 cc 16 00 38 7d 00  |.............8}.|
[COLOR=Blue]00000030[/COLOR]  00 00 00 00 [COLOR=Blue]00[/COLOR] 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040[/FONT]

---

### Post by Rubi1200 on 2011-07-02
Forget the boot script for the moment and run the command YesWeCan gave you.

Can you please tell us how this happened to the best of your knowledge?

---

### Post by Sarath1989 on 2011-07-02
The problem solved. I downloaded Dban iso to my laptop. Burned it to a cd and booted the desktop pc with it. It wiped out the entire hard disk. All my music gone. Now Im installing fresh copy of Ubuntu. :P

---

### Post by Rubi1200 on 2011-07-02
Well obviously we are pleased you managed to find a solution, but if you had waited we might have been able to help you recover those music files and other data you wanted.

In any event, good luck :)

---

### Post by Sarath1989 on 2011-07-02
I thought the only solution was to wipe the hard disk. There was a lot of music files in it. They were my favorites. I will start to make a music collection again. Anyways Thanks a lot for your help guys. Thanks a lot for you time.

---

