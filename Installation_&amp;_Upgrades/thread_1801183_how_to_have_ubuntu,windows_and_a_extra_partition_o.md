---
title: "how to have ubuntu,windows and a extra partition on the same hard drive"
date: 2011-07-10
forum: Installation &amp; Upgrades
---

### Post by vigeek on 2011-07-10
**guys, i want to install windows 7 and ubuntu studio on the same hard drive(dual boot) but that is not a problem for me.....since ill be using both i want a third partition to store all music images etc from both the OS's.i think the 3rd partition should be fat32 so that both windows and ubuntu can access it.but windows needs a system reserved partition nowadays and ubuntu a swap....so that makes a total of four partitions.So how can i make my fat32 partition?**

---

### Post by Bucky Ball on 2011-07-10
Make it NTFS. Both OSs read and write to that and faster.

Put Win on a primary partition (install first) and leave the rest of the drive as free space. During the install of Ubuntu you will get to the partitioning section. Choose 'Manual' and create an extended partition the size of the free space (you will see the Win NTFS partition there so just leave that alone).

Inside that extended partition make logical partitions so you end up with the drive looking something like this:

Win Install = NTFS

Inside extended partition:

/ = EXT4 (20Gb heaps)
/home = EXT4 (choose size)
/shared = NTFS (choose size)
/swap = size of your RAM (leave room for this at end of drive).

You would have your recovery partition in there somewhere also, of course, but you don't need to create or alter that.

You can theoretically have as many logical partitions as you want inside and extended. I have Win7, 10.04, 10.10, 11.04, /home, NTFS share partition, two Toshiba recovery partitions, and /swap on one laptop HDD. Not an issue. 

Just remember; you can only have four primary partitions on one physical HDD but inside an extended partition you can have as many as you like. 

(e.g. You could have three primary partitions and the fourth and extended partition - inside the extended you could then have 99 logical partitions - machine sees that as still four partitions on the HDD).

Good luck. ;)

---

### Post by vigeek on 2011-07-10
Inside extended partition:

/ = EXT4 (20Gb heaps)
/home = EXT4 (choose size)
/shared = NTFS (choose size)
/swap = size of your RAM (leave room for this at end of drive).



dude,i dint understand the above part,and ill be insatllin ubuntu studio..and which is the partition i will use to store data? and ubuntu wont mount ntfs automatically on startup?

---

### Post by Bucky Ball on 2011-07-10
> **vigeek said:**
> Inside extended partition:

/ = EXT4 (20Gb heaps)
/home = EXT4 (choose size)
/shared = NTFS (choose size)
/swap = size of your RAM (leave room for this at end of drive).



dude,i dint understand the above part,and ill be insatllin ubuntu studio..and which is the partition i will use to store data? and ubuntu wont mount ntfs automatically on startup?

/shared is your Win/Ubuntu shared partition (NTFS) and yes, Ubuntu will read/write NTFS. Ubuntu Studio? It is Ubuntu with the rt (real time) kernel and extra packages for AV, that is all (so bigger and you need to burn a DVD of it rather than an install CD). You can install Ubuntu Studio in regular Ubuntu by searching for ubuntustudio-desktop in Synaptic Package Manager. That will drag in all UStudio apps and rt kernel.

---

### Post by vigeek on 2011-07-10
1 last question-what will be the size of /home ?? same as / ????

---

### Post by Bucky Ball on 2011-07-10
Size of /home as big as you like. That is where directories like /video, /music, /documents, /downloads and all other personal data (and settings) will live so you want to make it pretty big. All your applications are installed to / (root partition).

I have:

/ = 15Gb
/home = 150Gb
/misc (NTFS shared partition for Win and Ubuntu) = 40Gb
/swap = 4Gb (size of my RAM).

Hope that helps.

---

### Post by vigeek on 2011-07-10
Here it is..i tried instalin usin ubuntu studio cd..i have 3 primary partitions windows,windows system reserved,and for /

and 3 logical as /home,swap and the 3rd one is the extra drive i need..thr is no option to use as ntfs so i used fat32 instead ..and mount point as /shared or /misc but its unable to mount.

---

### Post by Bucky Ball on 2011-07-10
You have all Ubuntu partitions inside an extended partition?

You have three primary partitions already (all Win related) and therefore can *only* add ONE more, the extended partition (which is the fourth primary), in which, on *logical* partitions, should reside your;

/
/home
/shared (NTFS)
/swap

/, /home and /swap are default mount points in the manual partitioning section (you just need to choose them), /shared you need to create (formatting as NTFS), but that's straightforward. ;)

Not sure why you didn't get NTFS option. Should be there. If you were attempting to create more than four primary partitions that could have been the issue. Make sure you have set the NEW partitions to format (making sure you have NOT set the three existing Windows primary partitions to format, that is!!!). 

Grub will pick up your Windows install, incidentally, and add it to your menu list at boot. Also, as UbuntuStudio is primarily a production install, I would strongly advise going for a production release, 10.04 LTS, supported until 2013 and stable. (if you are attempting 11.04 that could also be causing your install issues).

---

### Post by vigeek on 2011-07-10
here is the screensot....using ubuntu studio 11.04 ,windows being already installed

---

### Post by Bucky Ball on 2011-07-10
If #1 and #2 are your existing Windows partitions, looks good. Are you sure you can't make /misc NTFS? Also, why is it so big? Not to worry, you can always resize later. Just remember, your personal data is going to go into /home so that 14Gb might fill up quickly.

But as I say, you can always resize, and you might want to put most of your personal stuff in /misc to share with Win anyhow.

---

### Post by vigeek on 2011-07-10
no i tried with ubuntu 10.10 cd also....ntfs option is not there......actually ill store all my files like music and pics on a common drive so its big(ntfs or fat) which m not able to make since it says cant mount since its not ext4....

---

### Post by Bucky Ball on 2011-07-10
Again, fat and NTFS will mount in Ubuntu. If NTFS doesn't automagically it is really easy to get it to. That is not an issue ... ;)

Other thing you can do is try to reformat the shared drive to NTFS once you have installed the OS and have everything up and running. You can do this with Gparted from a LiveCD (or from the running install when the partition is unmounted).

---

### Post by vigeek on 2011-07-10
no u didnt understand..i mnot talkin abt the mounting after ubuntu startup but while installation ..when i make the partition as fat since ntfs option is not there the installation wont proceed showin error"cant mount fat since its uncompatible with unix file system,go back to change the partition settings or the partition cannot be used"

---

### Post by vigeek on 2011-07-10
u mean in the primary partition ext 4 for ubuntu there can be a ntfs logical partition?mounted as /misc or /shared right?

---

### Post by vigeek on 2011-07-10
**hey,thanx **it worked i had to install a partition manager on windows and get the logical ntfs partition......but in ubuntu disk utility it show the ntfs drive mounted at /shared but i cannot find in computers?

---

### Post by Bucky Ball on 2011-07-10
Which computers are you looking in? You mean you can't see it in Windows? It is mounted in Ubuntu okay?

In Ubuntu, open System>Administration>Gparted. It is there? If so, you can right click, unmount it, label it (if it is not already labelled), and then see if it appears in Windows, if that is your problem ...

---

### Post by vigeek on 2011-07-10
no i where can i access it in file manager in ubuntu?

---

### Post by Bucky Ball on 2011-07-10
Okay. In Ubuntu, open System>Administration>Synaptics, search for and install 'ntfs-config' and 'ntfs-3g'.

Now, in System>Admin you should find 'NTFS Configuration tool' (or called something like that). Run that and you will be able to set up your NTFS partitions to mount when you boot.

---

### Post by vigeek on 2011-07-10
but its already mounted when it starts as disk utility program shows....i just dont get where that is

---

### Post by Blasphemist on 2011-07-10
Could you take a screen shot in GParted and post that? Also, please download this script and run it as shown on the linked page. It will create a results.txt file in the directory it is run from. Please copy that results.txt and paste it in between code tags in your response. [http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

What you are describing is very unusual and I think we can get to the bottom of this if you pass back this information.

---

### Post by vigeek on 2011-07-10
**here is the screen shot from disk utility of ubuntu and the results of the script**



```
                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos2)/boot/grub on this drive.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1             206,848    61,442,047    61,235,200   7 NTFS / exFAT / HPFS
/dev/sda2    *     61,442,048    91,521,023    30,078,976  83 Linux
/dev/sda3          91,523,070   625,141,759   533,618,690   f W95 Extended (LBA)
/dev/sda5         116,953,263   616,831,739   499,878,477   7 NTFS / exFAT / HPFS
/dev/sda6         616,833,024   625,141,759     8,308,736  82 Linux swap / Solaris
/dev/sda7          91,523,072   116,953,087    25,430,016  83 Linux


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        1A1EF0741EF04A71                       ntfs       
/dev/sda2        50119a3f-fe98-4ec2-87ec-54e901fd93d0   ext4       
/dev/sda5        01CC3F3BA0298E00                       ntfs       
/dev/sda6        d079877c-39f1-4378-b750-0dda810846a4   swap       
/dev/sda7        424dcc06-b4c0-43ae-874a-07e16e6fb907   ext4       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda1        /media/1A1EF0741EF04A71  fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sda2        /                        ext4       (rw,errors=remount-ro,commit=0)
/dev/sda5        /shared                  fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sda7        /home                    ext4       (rw,commit=0)


========================== sda1/grldr embedded menu: ===========================

--------------------------------------------------------------------------------

=============================== StdErr Messages: ===============================

unlzma: Decoder error
/home/vishal/Desktop/boot_info_script.sh: line 1888: (  / 2 ) + 16 : syntax error: operand expected (error token is "/ 2 ) + 16 ")

```

---

### Post by vigeek on 2011-07-10
ss

---

### Post by Blasphemist on 2011-07-10
The MBR looks good. You have 2 primary partitions, windows (sda1) and ubuntu(sda2), and an extended partition (sda3) which is also primary. All good. Since you don't have a 4th primary partition there is no sda4. 15 GB is big enough for / (root) in sda2.

In the extended partition there is logical partition /shared in sda5 that is 256 GB. The swap is sda6 at the end of the drive. The other logical partition is sda7 which is /home. 

I can't see exactly what I wanted since you gave me a shot of the disc utility instead of GParted. I can't see if the mount points of everything is just right. But what you did provide shows that your shared drive is mounted at /shared as desired. That shared partition is unlabeled and you should label it Shared or something but that isn't causing your problem. 

Here is a link that describes creating a folder to mount this to. Following this will cause it to show up in nautilus as a folder in your file system. [http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux)

When you get the UUID you can copy it to the clipboard and paste it into the UUID= command. You can also use this command instead of her use of nano if you are not familiar with the nano editor. 
```
gksudo gedit /etc/fstab
```
Just as she does I use the UUID as I could make partition changes that could change the /dev name.

---

### Post by Bucky Ball on 2011-07-11
Yes, shot from Gparted (Partition Editor in System>Administration once again!), please.

---

### Post by vigeek on 2011-07-14
new problem popped up! things were working fine but now the "/shared" folder is marked with a cross n wen i try to open it says u dont have permission to open it:(

---

### Post by Blasphemist on 2011-07-14
This last part from the psychocats link about should fix the permission issue.
> Now I need to give it the proper permissions. Let's just assume, for this example, that my username is jessica.
```
sudo chown -R jessica:jessica /storage
sudo chmod -R 755 /storage
```
Now the partition is mounted in the /storage folder and is ready for use!

---

