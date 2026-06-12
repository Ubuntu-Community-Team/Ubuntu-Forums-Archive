---
title: "Can't boot from USB&gt; GRUB error 15&gt; Insert bootable device"
date: 2010-02-23
forum: Installation &amp; Upgrades
---

### Post by italinux on 2010-02-23
Greetings,

I wish only to start over. I have been using Ubuntu for almost a year now, and have installed it on multiple computers different ways. I have had to use the Terminal quite a bit through this time.

Now I can't even get to normal command line. Only GRUB command line. I remember setting it up, but haven't had to mess with it. Now that I have deleted some files, I fear it is finished. I try the root, setup (hdx,y)  commands all different ways and to no avail. After running them successfully on some partitions, a find /boot/grub/make.lst returns no file. I just want to start anew, not fix anything...
So I try to boot USB Karmic NBR by forcing it...
At the BIOS I select "Not Installed" under the IDE Master and Slave selectors
I also select USB key as boot choice, with no other options...
So this brings me to the only other outcome I can get other than a grub> command prompt. 
It says "reboot and select proper boot device or insert boot media in selected boot device"
Does this mean I just haven't gotten the USB drive written right?
I use DVORAK keyboard layout, and when it goes to the GRUB prompt it is off. It is very difficult to imagine reworking the computer via GRUB.
 
Please tell me to go back to formatting USB keys on my Mac.
I hope I just need a better img than the ones I've been converting.
Then I won't have to worry! I can figure that out pretty easy.

I have never asked for help, but was always able to learn from others' posts. This time I have spent days trying to figure this out and I have to ask. 

Thanks for your time!
-Italinux

---

### Post by decjedrek on 2010-02-23
Based on what You said:

>> It says "reboot and select proper boot device or insert boot media in selected boot device"

I assume You have something wrong with boot sector on Your USB drive. During the installation process (partitioning to be exact), have You selected the root partition (mount point /) to be bootable? If not- You can ```
cfdisk /dev/sd...
``` this partition and set bootable flag on.

Hope this helps :)

---

### Post by darkod on 2010-02-23
Also, you might be able to bring back to life your install quite easy, depending. I guess /boot/grub/menu.lst doesn't exist because you have clean install of 9.10 which uses the new grub2 and the config file is /boot/grub/grub.cfg but it's not meant to be edited directly as menu.lst.

I guess just reinstalling grub2 with a 9.10 live cd will sort it out. You can also install it from 9.10 live usb once you get it created correctly.

The boot message does sound like the usb is not created correctly.

---

### Post by italinux on 2010-02-24
decjedrec and darkod,

Thanks so much for the responses.
I have made progress, but no solution still.

I used Unetbootin on a friend's Windows computer to create a bootable USB drive with a 9.10 .iso.
I still however can not get it to boot. 

My new result is a line preceding the "reboot or insert proper boot medium" 
It now says "Missing operating system".

I have now read many pages on running Syslinux or copying it to the USB drive.
I see Syslinux on the drive.
It has ubninit and ubnkern files, as well as isolinux folder
should there be a /boot folder on the usb drive? Is that what it's looking for?
I am working on a Mac making these usb drives. As I said before, I have had to make multiple attemps in the past at installing Ubuntu or Eeebuntu from a usb stick. Does anyone know how to do this on a mac successfully?
It seems like the USB drive just isn't set to bootable...
Another clue: When I partitioned FAT, wrote an .img to the drive and then tried to fdisk> f 1 , the USB drive, before the Unetbootin attempts, there was an error pertaining to no MBR folder.
Now I am running back into mentions of MBR on the USB key and wondering how to get that done. It seems to look for a /usr/standalone/i386/boot0, no such file or directory...
And oh yeah, yesterday I was able to format the disk in Disk Utility in OSX to be Master Boot Record. It showed up in diskutil list as non-GUI formatted drive. Now it shows up as GUI formatted, but the first partition is Microsoft basic data.
I hit a lot of dead-ends trying to use "restore" in disk utility to put ISOs on the USB drive. I either couldn't drag the IMG or ISO into the Source field, or once I did (With an IMG or mounted ISO) It would say error 254 or "couldn't verify source" "couldn't scan, needs to be imagescanned" -> Then I go up to the menu and select Images>Scan/ Verify Image, and it says"Unable to scan "ubuntu_.." (Invalid argument)...

I just want a working computer... Any OS. It needs to be from a USB drive created/ written on a mac. The Disk Utility program looked promising, but just more error messages and no progress. I was exited to see there is  a MBR option on the partition of drives, but does me no good if it won't verify or Scan the .img files!
I got the idea of using the disk utility from this unlikely video...
he also goes into terminal and flags the partitions.

[http://www.youtube.com/watch?v=akc1Db2KXwo](http://www.youtube.com/watch?v=akc1Db2KXwo)

I figured since I asked for help, then tried your suggestions, looked further and rushed home from work to work on this yesterday, have spent the past 2 entire days not to mention the whole week before that on this problem. Persistence and research pay off usually but I can't believe this isn't solved yet. By far the biggest snarl in my Linux experience. I know there will be more and more Mac users trying to save their friend's or their own old PC's, experiment with cheap netbooks etc. that there will be a demand for a way to make bootable USB drives.

  
Thanks for your attention and any input or help you can provide.

---

### Post by darkod on 2010-02-24
Sorry but I have absolutely no idea about Mac. I can only offer the official page:
[https://help.ubuntu.com/community/Installation/FromImgFiles#Mac%20OS%20X](https://help.ubuntu.com/community/Installation/FromImgFiles#Mac%20OS%20X)

Note in the instructions that they use .img file and the downloads for 9.10 are all .iso files (even the UNR version). But you could try those instructions.

The unetbootin created stick should have worked. Usually I format it as FAT32 before I start, and get rid of the unetbootin menu after, but it should work even with keeping the menu. What I do to enable the standard ubuntu menu is:

1. Create the stick with the Disk Image option, ignore the question to reboot after done, just close unetbootin.
2. Open the stick and rename the file syslinux.cfg to syslinux.old
3. Open the isolinux folder and find and rename isolinux.bin to syslinux.bin, isolinux.cfg to syslinux.cfg
4. Go back and rename the whole folder isolinux to syslinux

The usb stick is finished.

---

### Post by italinux on 2010-02-25
Another 4 or 5 attempts later...

I have reformatted 2 usb sticks both FAT32 and AppleGUI, Then sudo dd the .img

"please insert proper boot medium" blah..
no "missing operating system this time.

Tried to partition in FAT32 and then write to that partition, didn't work.
Doesn't work like this:
/dev/disk2
   #:                       TYPE NAME                    SIZE       IDENTIFIER
   0:                            Ubuntu-Netbook-R       *2.0 GB     disk2

when I take this:
/dev/disk2
   #:                       TYPE NAME                    SIZE       IDENTIFIER
   0:     FDisk_partition_scheme                        *2.0 GB     disk2
   1:                 DOS_FAT_32 UNTITLED1               2.0 GB     disk2s1

and then do :
Computer: $ sudo dd if=/ubuntu-9.10-netbook-remix-i386.img of=/dev/disk2s1 bs=1m

I get this:
   #:                       TYPE NAME                    SIZE       IDENTIFIER
   0:      GUID_partition_scheme                        *2.0 GB     disk2
   1:       Microsoft Basic Data UNTITLED 1              2.0 GB     disk2s1

If I leave out the s1 part it just looks like the first table example, writing over with no partitions/ Looks like no file system style not GUI nor FDisk/ FAT ? 
Just noticed that- It has no TYPE displayed in that column when I run diskutil list after 
Computer: $ sudo dd if=/ubuntu-9.10-netbook-remix-i386.img  of=/dev/disk2s1 bs=1m

How can I retain a FAT formatting and write the .img?
It would be really cool if Disk Utility worked for this.

Thanks for the help. 

-italinux

---

### Post by italinux on 2010-02-25
WHOA!

I have an OS now!
Thank you so much for the help!
Even though the solution was just to try 9.04 instead of 9.10...
It was good to have some interaction on here to motivate me.

I think the instructions they give on the Ubuntu website about converting the .iso to .img in terminal are not 100% reliable. The IMG of 9.04 works though...

I think I will use it to create a 9.10 usb stick and keep playing.

---

