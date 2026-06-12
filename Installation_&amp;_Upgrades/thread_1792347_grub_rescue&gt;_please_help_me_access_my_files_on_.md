---
title: "grub rescue&gt; please help me access my files on external (failing?) drive. thx."
date: 2011-06-28
forum: Installation &amp; Upgrades
---

### Post by supermeow on 2011-06-28
hi there,

i'm a total newbie in desperate need of assistance, so i hope someone would read this and help me out.

i have an hp laptop and i had ubuntu on it for 3 years.

my hard drive started to fail a while ago (i had ubuntu 10 on it until 1 week ago) and a then it all went black...

I took the laptop to a repair shop, they told me it was the disc, so i  bought a new disc, installed it on my laptop and reinstalled the new  ubuntu 11. 
so far so good. i have now a working OS, internet connection and i can in fact type this message.

the thing is: all my files are on the old drive, which doesn't load/boot/start/read anymore.

I have tested it on some friends's pc, tried a few HD disgnostic tools, they all send the same message: "fail"

i then tried to mount my old drive (with all my precious files in it) on  my laptop as an external drive (usb) hoping that ubuntu 11 could read  it as an external usb key: it gets read by the system, but it shows no  files at all. it also shows an error message saying the drive can not be  mounted, with some "sdb1" thing. i am sorry but i'm really dumb when it  comes to tech language.

then i tried to boot it on start-up but i got the *grub rescue>* thing and nothing else, 
just a sad, blinking cursor

to recover my files,i have also tried testdisk but couldn't understand  very well how to use it, and then photorec, from which i recovered bits  and pieces of files, with no name. some of them are just parts some of  them are complete.

my problem is: i have to get access to my files, as I use them for work,  i couldn't do a back-up recently and i have some real important  deadline to meet... for which i need those files.

is there any way i could solve the grub issue and have that drive load/mount again as external usb?

thank you for your help in advance and sorry for my non-technical explanation. i hope it's understandable.

i am really not very high-tech so i hope someone would come up with simple "baby-steps" instructions

cheers

Gianluca

---

### Post by An Sanct on 2011-06-28
I personally would forget the option to boot and look in the direction of trying to mount it as a seperate, maybe external drive.

If possible, I would recommend to make it not writable or accessing it in a read-only manner, to minimize data loss. Most of all, don't plug it into a Windows machine (!) even a totally healthy EXT3/4 formatted drive is going to be treated as an empty drive...

Give it a shot, I've rescued an external *badly* failing hard drive for a friend, that windows didn't even want to hear about... So, get an appropriate external HDD case from a friend/co-worker and mount it that way. If anything can be saved, it can be under Linux (it really reads the drive as long as it is willing to respond).

If mounting it this way under Linux (Ubuntu or any other) gives the same read errors, than maybe the drive is "toast" ... but I sure hope this is not the case for you ...

PS. Make yourself happy and don't give the drive into repair out to anyone, that does not know what a "kernel" is, I have had some really bad experiences with these - "technical professionals", that think "Operating System" means Windows (only Windows)...

---

### Post by YesWeCan on 2011-06-28
With the old drive attached, what is the output of
[COLOR="DarkGreen"]sudo fdisk -l[/COLOR] and [COLOR="DarkGreen"]sudo blkid[/COLOR]?

---

### Post by supermeow on 2011-06-28
hi there and thx for your answers

**An Sanct**, thx for the reply, i am afraid am absolutely not capable of doing anything of what you mentioned (make it not writable etc) i really have no skills at all... i understood it's maybe better not trying to rebuild the grub/not re-boot the drive but use it as en external usb... which i would love to do if only i knew where to begin. i am really at zero skills. i'll appreciate any help about this remedy you suggest, but it should be written for... a total rookie. I don't know if i am able to follow complicated instructions.

**YesWeCan**: if I type those 2 commands in the terminal, it gives me the reading for dev/sda1 which is my new, current, healthy hard disk (which i am using as i write now, with a new ubuntu installed - what i need is to read the old, failing drive which i have now plugged externally). 
i don't know how to launch these commands  for my external (damaged) drive, which is /dev/sdb1. any suggestion?

meanwhile, trying to play with it, i came across this post:
[http://ubuntuforums.org/showthread.php?t=1245536&highlight=bad+superblock](http://ubuntuforums.org/showthread.php?t=1245536&highlight=bad+superblock)

and simply (probably stupid ...) i just copied this line into the terminal:
sudo e2fsck -f -b 32768 -y /dev/sdb1 
all i got after hours of my terminal running like crazy is my external drive, still mounted externally into a case, plugged into a usb port, which has... only one folder now, called "lost and found" which takes pretty much all the space i used for my files (around 100 Gb) but it's unreadable, meaning, now it mounts, for a few minutes, i click on "properties" for this "lost and found" folder and it says that the folder has zero items and it has "unreadable content"....

i hope i haven't ruined it for good... i am really desperate now..

thx for your help

Cheers

---

### Post by supermeow on 2011-06-28
btw, for **Yes We can**

 this is what i got from the terminal:

this is the output for sudo fdisk


Usage:
 fdisk [options] <disk>    change partition table
 fdisk [options] -l <disk> list partition table(s)
 fdisk -s <partition>      give partition size(s) in blocks

Options:
 -b <size>                 sector size (512, 1024, 2048 or 4096)
 -c                        switch off DOS-compatible mode
 -h                        print help
 -u <size>                 give sizes in sectors instead of cylinders
 -v                        print version
 -C <number>               specify the number of cylinders
 -H <number>               specify the number of heads
 -S <number>               specify the number of sectors per track

and this is the output for sudo blkid
/dev/sda1: UUID="c20f10cf-cfd2-46e6-bdd5-63e970c25183" TYPE="ext4" 
/dev/sda5: UUID="edabda11-42da-4ef5-b8c0-6cb1c6dcf75c" TYPE="swap" 
/dev/sdb1: UUID="544f194a-c240-4819-a427-9e99cbf099c1" TYPE="ext4" 
supermiao@supermeow2011:~$ 


my external drive, the one i am trying to save files from, is sdb1. my new drive, current in use inside the laptop is sda1... and i have no clue what sda5 would be

hope i typed the right stuff in.

thx again

---

### Post by supermeow on 2011-06-28
also, if i click on that lost/found folder in my external drive, i get the message:

 - You do not have the permissions necessary to view the contents of "lost+found". - 

i am pretty sure my stuff is in that lost+found folder but... how do i open it?

thx

---

### Post by An Sanct on 2011-06-28
> [COLOR=DarkGreen]sudo fdisk -l[/COLOR] and [COLOR=DarkGreen]sudo blkid[/COLOR]?Should list all drives attached to the machine
copy and paste this into the terminal
```
[COLOR=Black]sudo fdisk -l
[/COLOR][COLOR=Black]sudo blkid[/COLOR]

```note, that to paste into the terminal, you have to use CTRL+**SHIFT**+V and to copy the response use CTRL+**SHIFT**+C, so we can see what is happening with your disks.

edit: PS. sorry :) I seem to be a bit slow here ...

---

### Post by An Sanct on 2011-06-28
go to terminal and enter
```

sudo nautilus
```
provide the password and browse to the lost+found folder, you will have administrator rights that way.

---

### Post by supermeow on 2011-06-28
thx, man

now i can in fact access it but still... can't see what's in it: my laptop fan went skyrocket, CPU is going up and up...even my external drive is getting hotter... i hope this thing doesn't explode... the mouse cursor went from arrow to this spinning circle, like it's reading the content of the external drive but it takes forever and overheats like crazy...

---

### Post by An Sanct on 2011-06-28
What about if you run "palimpsest" 
(the disk utility accessible under System -> Administration -> Disk Utility)
From there you can inspect the S.M.A.R.T. data (if present)

Well, laptops and disks can handle heat pretty good, you just have to make sure the laptop's ventilator can pump fresh air into the unit and it will be okay. So, don't use it on your bed, your lap, soft surfaces ... I think you know what I mean.

PS. Sorry, I don't know if this disk tool I mentioned is present in a clean Ubuntu install.

---

### Post by YesWeCan on 2011-06-28
> **supermeow said:**
> btw, for **Yes We can**

 this is what i got from the terminal:

this is the output for sudo fdisk
You left off the -l (as in minus small letter L). It stands for list. This should list all drives attached that the OS can see and their partitions and sizes.

> and this is the output for sudo blkid
/dev/sda1: UUID="c20f10cf-cfd2-46e6-bdd5-63e970c25183" TYPE="ext4" 
/dev/sda5: UUID="edabda11-42da-4ef5-b8c0-6cb1c6dcf75c" TYPE="swap" 
/dev/sdb1: UUID="544f194a-c240-4819-a427-9e99cbf099c1" TYPE="ext4" 
Ok.

---

### Post by supermeow on 2011-06-28
i stopped trying to read the content cuz my laptop was boiling down. i changed the properties so now i can read it anytime without running natuilus (i figured this was an ok thing to do) and after a while i restarted and clicked on "properties" for my drive (now mounted and visible on my desktop)

 got another error message:
 - an error occurred while performing an operation on "241 GB Filesystem (partition 1 of FUJITSU MHZ2250BH G2): the device is busy - 

 which in the details says: 
- Device is mounted and no online capability in fsck tool for file system -

any idea?

thx a lot

---

### Post by supermeow on 2011-06-28
**Thanks, YesWeCan:**

sorry i did forget that here is the correct output i guess:

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0004a6ac

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       60418   485306368   83  Linux
/dev/sda2           60419       60802     3077121    5  Extended
/dev/sda5           60419       60802     3077120   82  Linux swap / Solaris

Disk /dev/sdb: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000a8fc3

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       29295   235312056   83  Linux
supermiao@supermeow2011:~$ 


so, my messed drive is the second, sdb1...

---

### Post by YesWeCan on 2011-06-28
> **supermeow said:**
> i stopped trying to read the content cuz my laptop was boiling down. i changed the properties so now i can read it anytime without running natuilus (i figured this was an ok thing to do) and after a while i restarted and clicked on "properties" for my drive (now mounted and visible on my desktop)

 got another error message:
 - an error occurred while performing an operation on "241 GB Filesystem (partition 1 of FUJITSU MHZ2250BH G2): the device is busy - 

 which in the details says: 
- Device is mounted and no online capability in fsck tool for file system -

any idea?

thx a lot
I don't know what those errors mean. Can you do anything with the mounted drive? Can you copy files off it?

---

### Post by supermeow on 2011-06-29
--> yes we can:

no, man, i can't do anything with it. not read it, not open it and sure not get any file out of it (this is what i need to do, btw, just get my damn files out of there, after that i can throw the damn drive off a cliff)

I have no idea what the f**k is wrong with my laptop or my system.

my fan keeps boiling, that bloody external drive still shows that "lost and found" folder and anytime i try to open it, my system goes on crash, it keeps saying the device is busy, or it is not correctly the CPU is like 150%..

plus this is the result anytime i run sudo nautilus in the terminal:
-------------------------------------------------------------------------------------------------------------------------------------

Initializing nautilus-gdu extension

** (nautilus:1818): WARNING **: Failed to get the current CK session: GDBus.Error:org.freedesktop.ConsoleKit.Manager.GeneralError: Unable to lookup session information for process '1818'

(nautilus:1818): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(nautilus:1818): Gtk-WARNING **: Attempting to store changes into `/root/.local/share/recently-used.xbel', but failed: Failed to create file '/root/.local/share/recently-used.xbel.FZDSXV': No such file or directory

(nautilus:1818): Gtk-WARNING **: Attempting to set the permissions of `/root/.local/share/recently-used.xbel', but failed: No such file or directory

(gedit:1873): Gtk-WARNING **: Attempting to store changes into `/root/.local/share/recently-used.xbel', but failed: Failed to create file '/root/.local/share/recently-used.xbel.KFWIXV': No such file or directory

(gedit:1873): Gtk-WARNING **: Attempting to set the permissions of `/root/.local/share/recently-used.xbel', but failed: No such file or directory

(gedit:1873): Gtk-WARNING **: Attempting to store changes into `/root/.local/share/recently-used.xbel', but failed: Failed to create file '/root/.local/share/recently-used.xbel.G89PXV': No such file or directory

(gedit:1873): Gtk-WARNING **: Attempting to set the permissions of `/root/.local/share/recently-used.xbel', but failed: No such file or directory
----------------------------------------------------------------------------------------------------------------

if i try to close the terminal at this point, it warns me that it would kill the running process. if  let it be and wait for it to do something.... well, lst time it stayed like that for hours and absolutely nothing happened.

i have installed ubuntu 11 on a brand new hard drive yesterday and it feels like the system is already sluggish, slow and compromised.

as i write, the bloody fan keeps going on and on.... so i have to shut down and let it cool again.

it didn't do any of this yesterday when i first put the new hard drive in and installed ubuntu 11.

i am really ready to destroy this ******* machine with a hammer... :-( 

super sad and frustrated

---

### Post by YesWeCan on 2011-06-30
Sorry, I have no idea. The only thing I can think of doing is removing the disk and trying it in another computer. But if it's the disk then you may need to get some pro help to recover the data.

---

