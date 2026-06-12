---
title: "FSTAB entries for /home using BTRFS file system"
date: 2023-05-04
forum: Installation &amp; Upgrades
---

### Post by Robbyx on 2023-05-04
Following a fresh reinstall the content of my home directory is not showing any content, even though it is on a separate partition and was not deleted. There is  40gb of data from the last  working installation that can not be accessed, because it is hidden. 

Looking at the home directory partition there are two partitions one below the other:  home and @home. I can not see the two in nuatilus. @Home/ is the one with all the data from the last working installation that is not mounted by fstab.  The Home/ that can  be seen has empty folders made by the Ubuntu installer.

Is the cause of two home directories to be found in the btrfs below wherein there is    "defaults,subvol=@home 0       2" ? 
Can I remove the @ from the home options?  

The last time I altered fstab by incorrectly changing the mount structure  command I could not load the os and had to do a fresh install. 



Here is most of the fstab as produced following the reinstall:

# /boot/efi was on /dev/nvme0n1p3 during installation
UUID=6D92-A938  /boot/efi       vfat    umask=0077      0       1
# /home was on /dev/nvme0n1p2 during installation
UUID=5bd8aa95-b627-4297-be5b-4352a09546b0 /home           btrfs   defaults,subvol=@home 0       2
# swap was on /dev/sdb7 during installation
UUID=6bbc8a5a-b488-49b6-904a-952e05463815 none            swap    sw   0       0

> 
This shows that /dev/nvme0n1p2 is mounted with content, not accessible via Nautilus 
$df -h

Filesystem      Size  Used Avail Use% Mounted on
tmpfs           1.4G  2.1M  1.4G   1% /run
/dev/nvme0n1p1   52G   11G   38G  23% /
tmpfs           6.9G     0  6.9G   0% /dev/shm
tmpfs           5.0M  4.0K  5.0M   1% /run/lock
/dev/nvme0n1p3  499M  6.1M  493M   2% /boot/efi
/dev/nvme0n1p2  106G   50G   55G  48% /home
tmpfs           1.4G  4.7M  1.4G   1% /run/user/1000
/dev/sdc1       2.0G   24M  1.9G   2% /media/robins/E0D0-35DF
robins@robins-desktop:~$ 


What option should I add in the drive listings that switches on error checking and correction?

---

### Post by Robbyx on 2023-05-04
This is very urgent for me, because I can not load any of the items stored in the home dir. So for example I can not log in to lastpass so that it shows my history of passwords stored in lastpass.

---

### Post by #&amp;thj^% on 2023-05-04
Robbyx, Please back-up your fstab first, and I'm not sure mine will work with "23.04" but should work with 22.04
```
UUID=<big long ID code> /     btrfs subvol=/@,defaults,noatime,autodefrag     0 1
UUID=<big long ID code> /home btrfs subvol=/@home,defaults,noatime,autodefrag 0 2
UUID=<big long ID code> /swap btrfs subvol=/@swap,defaults,noatime,autodefrag 0 2
/swap/swapfile          swap  swap  defaults             
```
Cross fingers, pray to Dev Gods, reboot.

---

### Post by Robbyx on 2023-05-05
When I did the last reinstall of Ubuntu at the point where I needed to set up a home directory, I specified the location of the existing /home that was kept on a separate partition (to reduce the risk of accidentally over writing it). I guess that what has happened  to my system on this occasion,  is that BTRFS created a /home partition and then added the separate partition as a branch below it. As both directories are called /home the  historical version was hidden and not accessible. I want the active home directory to be the existing /home in its own partition.  

As there is no change in the lack of content of the /home directory, next time I propose  you  pour water on the sacrificial mount and then set fire to it. . 

This is the current fstab

> # /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/nvme0n1p1 during installation
UUID=628a4fdc-399f-4f67-b598-956295288945 /               btrfs   subvol=/@,defaults,noatime,autodefrag     0 0
# /boot/efi was on /dev/nvme0n1p3 during installation
UUID=6D92-A938  /boot/efi       vfat    umask=0077      0       1
# /home was on /dev/nvme0n1p2 during installation
UUID=5bb8aa95-b657-4297-be5b-4352a09596b0       /home           btrfs   subvol=/@home,defaults,noatime,autodefrag 0 0
# swap was on /dev/sda7 during installation
UUID=6bbc8a5a-b488-49b6-904a-952e05463815 none swap sw       0 2

---

### Post by #&amp;thj^% on 2023-05-05
I'm guessing Ubuntu always wants to use subvolumes, if you use btrfs for the root partition you will automatically get two subvolumes, "@/" and "@home/" (see the Ubuntu wiki btrfs entry for more info on this), and it might set up the "@home/" subvolume just for the sake of consistency.
[https://help.ubuntu.com/community/btrfs#Ubuntu-specific_subvolume_layout_in_11.04_and_later](https://help.ubuntu.com/community/btrfs#Ubuntu-specific_subvolume_layout_in_11.04_and_later)

---

### Post by Robbyx on 2023-05-05
Thank you for the reference to the help file. I am beginning to understand what BTRFS  can do, but I find it complex because I am not really clear about the concept and what the system could usefully do for me with my stand-alone  desktop ubuntu. Following your ref I found a helpful youtube explaining how to set up btrfs in Ubuntu.

[https://www.youtube.com/watch?v=_sLSiL3oynk](https://www.youtube.com/watch?v=_sLSiL3oynk)

Unfortunately the instructions are not set out in separate file. so it may be difficult to follow it in practice. I am going to try, otherwise I can see myself never being able to use Ubuntu with the benefits of BTRFS.

At this point I am hoping the advice will cause the correct home directory to become visible and useable. I might be on the path to having  a system that works again. I am still surprised that I have had this problem with the home directory because I have done previous live installs and had no such difficulties with the home directory. 

Thanks again

---

### Post by #&amp;thj^% on 2023-05-05
> **Robbyx said:**
> Thank you for the reference to the help file. I am beginning to understand what BTRFS  can do, but I find it complex because I am not really clear about the concept and what the system could usefully do for me with my stand-alone  desktop ubuntu. Following your ref I found a helpful youtube explaining how to set up btrfs in Ubuntu.

[https://www.youtube.com/watch?v=_sLSiL3oynk](https://www.youtube.com/watch?v=_sLSiL3oynk)

Unfortunately the instructions are not set out in separate file. so it may be difficult to follow it in practice. I am going to try, otherwise I can see myself never being able to use Ubuntu with the benefits of BTRFS.

At this point I am hoping the advice will cause the correct home directory to become visible and useable. I might be on the path to having  a system that works again. I am still surprised that I have had this problem with the home directory because I have done previous live installs and had no such difficulties with the home directory. 

Thanks again
Kind of remember your first encounter with Linux and or Ubuntu, was it clear then? ;)
If you hang in there, and put some time into it you'll grow to love it...I Promise.:o
I've not shown mine as yet to help in not confusing you more:
```
cat /etc/fstab
# /dev/nvme1n1p3
UUID=c7dd4ddd-4530-449f-9aef-3ed578612123	/         	btrfs     	rw,relatime,ssd,discard=async,space_cache=v2,subvolid=5,subvol=/	0 0

# /dev/nvme1n1p1
UUID=500E-1B9B      	/boot     	vfat      	rw,relatime,fmask=0022,dmask=0022,codepage=437,iocharset=ascii,shortname=mixed,utf8,errors=remount-ro	0 2

# /dev/nvme1n1p3
UUID=c7dd4ddd-4530-449f-9aef-3ed578612123	/home     	btrfs     	rw,relatime,ssd,discard=async,space_cache=v2,subvolid=5,subvol=/	0 0

# /dev/nvme1n1p2
UUID=13149704-7ccc-4f3d-b335-6426bb04cc89	none      	swap      	defaults  	0 0


```
I hope I'm not coming across snobbish and this took me a beat or two to grasp, but zfs and btrfs are the only systems I use now.
And yes I lost my religion a time or two.:lolflag:

---

### Post by Robbyx on 2023-05-05
I agree it took me quite some time to having a working knowledge of Ubuntu. 

I think I accidentally gave your the wrong link. The right video from the same author is:

[https://www.youtube.com/watch?v=_sLSiL3oynk](https://www.youtube.com/watch?v=_sLSiL3oynk)

I am a bit concerned about the device options  for home that he suggests should be added to the btrfs set up file at 8.38. His home_options are 

subvol=@home, naotime,space_cache,compress=zstd,discard=async

My existing data in the old home directory is not compressed with zstd. Can I assume that BTRFS / ubuntu will notice the data is uncompressed and proceed to compress it? Likewise with any of the other home_options that clash with the previous settings?

---

### Post by Robbyx on 2023-05-06
I have spent the last night and today trying and failing at making the correct home directory show in the 2204 installation. The you tube video I referred to above did not work, although it has for others.  When I ran ubiquity during the course of the repair a load of error messages was all it could offer. I am going back to 20.04 and hoping I can have a workable system.  Thank you for the time you have given in trying to help me.

---

### Post by #&amp;thj^% on 2023-05-06
I know that guy from Arch in the link you show, but.....
Robbyx this is kind of a nuclear approach, It looks like you can safely remove the @home subvolume. It is not mounted anywhere on boot.
```
btrfs subvolume delete /@home
```[B]
**Please be sure to have your back-up /home**[/B] just in case.
When I first started with BTRFS I ran into the same situation as you now have, and the above worked for me.
Good Luck

---

### Post by Robbyx on 2023-05-06
Is there a way to change the order of the volumes so that the empty one is no longer at a ranking of 5?

I do not know how to back it up, if I can not indicate to a file copy program  a handle that it can use to move it.  

 Is this of help:

$sudo btrfs filesystem show /home
Label: none  uuid: 5bb8aa95-b657-4297-be5b-4352a09596b0
	Total devices 1 FS bytes used 49.31GiB
	devid    1 size 105.53GiB used 57.05GiB path /dev/nvme0n1p

This is the same as blkid is showing:

/dev/nvme0n1p2: UUID="5bb8aa95-b657-4297-be5b-4352a09596b0" UUID_SUB="12d8a1ae-9e45-4467-99d1-bae0e01b1c53" BLOCK_SIZE="4096" TYPE="btrfs" PARTUUID="36bdb116-02"

This makes me think that the second hidden one will be using the same UUID as the one that shows up, because we are dealing with BTRFS volumes not directories. 








sudo blkid does not show two homes.

At one time I did find a way of showing both. One was /home and the other @home. I no longer remember how I found that two. 

One home is full of years of data and the other empty. Only the empty one appears as the home when I look under Nautilus. I assume the other home is hidden.

---

### Post by #&amp;thj^% on 2023-05-06
Robbyx can you please confirm Lubuntu or Ubuntu
Thread Title reads[COLOR="#FF0000"] [lubuntu] FSTAB entries for /home using BTRFS file system[/COLOR]
Now you mention nautilus< I'll need correct information to correctly offer suggestions.
> **Robbyx said:**
> Is there a way to change the order of the volumes so that the empty one is no longer at a ranking of 5?

I do not know how to back it up, if I can not indicate to a file copy program  a handle that it can use to move it.  

How did you move your older home then??

---

### Post by Robbyx on 2023-05-06
> **1fallen said:**
> Robbyx can you please confirm Lubuntu or Ubuntu
Thread Title reads[COLOR="#FF0000"] [lubuntu] FSTAB entries for /home using BTRFS file system[/COLOR]
Now you mention nautilus< I'll need correct information to correctly offer suggestions.

How did you move your older home then??

I confirm I am using  Ubuntu, but I use nautilus for its  admin powers. It comes with ubuntu but is called files. 

Older Home
I did an install with the built in installation procedure that I install onto a usb stick using the create a USB installer disk program.

I had previously done many fresh installs and not had this problem. For example I was using 20.04 with btrfs and the correct home directory showed up the file manager.

---

### Post by #&amp;thj^% on 2023-05-06
> **Robbyx said:**
> I confirm I am using  Ubuntu, but I use nautilus for its  admin powers. It comes with ubuntu but is called files. 
Please understand I'm not trying to be/sound offensive, but again to be *Sure* I'm going to assume Ubuntu which comes with Nautilus/Files
Lubuntu would need to install nautilus.
> **Robbyx said:**
> 
Older Home
I did an install with the built in installation procedure that I install onto a usb stick using the create a USB installer disk program.
Ahh Ha Now i'm on to something.
Something did not set right then... nor have I used USB installer disk program for anything.

Ok before we get crazy here may I suggest this GUI_Tool: [btrfs-assistant]("https://gitlab.com/btrfs-assistant/btrfs-assistant")
You may find where your real home lives now, please take your time reading up on it.
I'll put a couple of screenshots for proof of concept.
Also have you looked in "/" it just might be there.
```
cd / && ls
bin   dev  home  lib64  mnt  pool3  root  sbin  sys  usr
boot  etc  lib   me     opt  proc   run   srv   tmp  var
&#9484;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;>
&#9474;/&#65533;&#65533; 

```
My user is named "me"
via cli
```
&#9484;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;>
&#9474;/&#65533;&#65533; 
&#9492;&#9472;> stat /home
  File: /home
  Size: 136       	Blocks: 32         IO Block: 4096   directory
Device: 0,23	Inode: 256         Links: 1
Access: (0755/drwxr-xr-x)  Uid: (    0/    root)   Gid: (    0/    root)
Access: 2023-05-05 16:49:35.026227961 -0600
Modify: 2023-05-04 16:09:26.817773522 -0600
Change: 2023-05-04 16:09:26.817773522 -0600
 Birth: 2023-05-04 08:45:42.000000000 -0600
&#9484;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;>
&#9474;/&#65533;&#65533; 
&#9492;&#9472;> stat /me
  File: /me
  Size: 724       	Blocks: 0          IO Block: 4096   directory
Device: 0,23	Inode: 244240      Links: 1
Access: (0700/drwx------)  Uid: ( 1000/      me)   Gid: (  984/   users)
Access: 2023-05-06 15:20:17.076361694 -0600
Modify: 2023-05-06 15:19:35.453256765 -0600
Change: 2023-05-06 15:19:35.453256765 -0600
 Birth: 2023-05-04 09:18:44.100222964 -0600

```
See the difference in size

---

### Post by Robbyx on 2023-05-07
Appologies for asking a basic question: I am getting nowhere installing btrfs-assistant. I have followed the commands in the readme. How do I run btrfs-assistant?  

These are the installation steps from the readme.md that btrfs-assistant supplies:
#### Debian/Ubuntu
1. Install the prerequisites: `sudo apt install git cmake qtbase5-dev qttools5-dev fonts-noto libqt5svg5 libqt5core5a g++ libbtrfs-dev libbtrfsutil-dev`
2. Download the tar.gz from the latest version [here]([https://gitlab.com/btrfs-assistant/btrfs-assistant/-/tags](https://gitlab.com/btrfs-assistant/btrfs-assistant/-/tags))
3. Untar the archive and cd into the directory
4. `cmake -B build -S . -DCMAKE_INSTALL_PREFIX=/usr -DCMAKE_BUILD_TYPE='Release'`
 `make -C build`
 `sudo make -C build install`
5. Optionally install Snapper - `sudo apt install snapper`

NB all 1-5 done. 


Copy of Terminal output after applying the above:

:~/Downloads/btrfs-assistant-1.8$ cmake -B build -S . -DCMAKE_INSTALL_PREFIX=/usr -DCMAKE_BUILD_TYPE='Release
> make -C build
> sudo apt install snapper
> exit
> clear

No error messages show but I can not find the app to run it. I am wondering if I have installed it.

---

### Post by #&amp;thj^% on 2023-05-07
Post any return back from:
```
sudo  btrfs-assistant
```
it needs elevated privileges.
And before you run that show the output of:
```
cd / && ls
```

---

### Post by Robbyx on 2023-05-07
robins@robins-desktop:~$ sudo  btrfs-assistant
[sudo] password for robins: 
sudo: btrfs-assistant: command not found

robins@robins-desktop:~$ cd / && ls
bin   cdrom  etc   lib    lib64   media  opt   root  sbin  srv   sys  usr
boot  dev    home  lib32  libx32  mnt    proc  run   snap  swap  tmp  var
robins@robins-desktop:/$

---

### Post by Robbyx on 2023-05-07
I have it working. I did a reinstall of the program. This time the make worked by display feedback.

---

### Post by #&amp;thj^% on 2023-05-07
I'm going to move slowly here, and i already know you are a patient poster. ;)
```
cd /home && ls
```
mine shows in the /home directory "me" so 
```
cd me && ls
```
And now shows;
```
$ ls
balenaEtcher-1.13.1-x64.AppImage  Music     system-info.tar.gz
Desktop                           Pictures  system-info.txt
Documents                         Public    Templates
Downloads                         snap      Videos

```
check for the right home with:
```
stat '/home/me' 
  File: /home/me
  Size: 45        	Blocks: 18         IO Block: 3072   directory
Device: 0,40	Inode: 34          Links: 26
Access: (0750/drwxr-x---)  Uid: ( 1000/      me)   Gid: ( 1000/      me)
Access: 2023-05-07 12:40:19.872715054 -0600
Modify: 2023-05-07 12:39:15.613439402 -0600
Change: 2023-05-07 12:39:15.613439402 -0600
 Birth: 2022-12-30 08:05:27.640895071 -0700

```
Also I led you wrong on the command it is:
```
sudo btrfs-assistant-launcher

```

---

### Post by Robbyx on 2023-05-07
Overview in Btfs-assistant
:
Files system size: 31.64gib, allocated 16.02gib , used 11.61gib , free estimated 34.62gib

Subvols:
@ 0.00 exclusive 000
home:
@home Created 3/5/2023  FS: UUID: 5bb8aa95 etc  size 1.24 gib exclusive 1.24Gib
home    Created 17/6/2019  Same FS UUID               size 48.2 gib  excl  48.20Gib

As proposed by you I should delete the empty home ie @home
Right clicking on @home gives the options

Create snapshot
Browse sub
Set read only flag
**Delete **

Deleting would leave just one home. Good but will the absence of a home directory not called @home make any difference to the system working properly or future reinstalls?

I can see it is almost solved! At last!

---

### Post by #&amp;thj^% on 2023-05-07
> **Robbyx said:**
> I have it working. I did a reinstall of the program. This time the make worked by display feedback.

great good work, I'm leaving for a couple of hours i'll be back to check your progress.
```
btrfs-assistant --version
Btrfs Assistant 1.8

```

---

### Post by #&amp;thj^% on 2023-05-07
> **Robbyx said:**
> 
Deleting would leave just one home. Good but will the absence of a home directory not called @home make any difference to the system working properly or future reinstalls?

I can see it is almost solved! At last!
No DO NOT delete, it will have bad results...we need to mount and create the new /Home.
I really hate leaving you at this point but I need to leave for a few short hours, I'll be back. (So don't touch anything while I'm gone please)
Thanks

---

### Post by Robbyx on 2023-05-07
I have been looking at this  entry in fstab
UUID=5bb8aa95-b657-4297-be5b-4352a09596b0       /home           btrfs   subvol=/**@**home,defaults,noatime,autodefrag 0 0

If I rebooted after removing  the @ from home so it became :
UUID=5bb8aa95-b657-4297-be5b-4352a09596b0       /home           btrfs   subvol=/home,defaults,noatime,autodefrag 0 0

Would the system reboot safely and show the correct /home. I could then delete the @home subvol via btrfs assistant.

---

### Post by #&amp;thj^% on 2023-05-09
Sorry for the Delay Life happens. Ok Robbyx i need to see where everything is:
```
btrfs filesystem show /mount/point/
btrfs filesystem show /dev/DEVICE
btrfs filesystem show /dev/sda
btrfs filesystem show 
```
All the above commands will need elevated privileges.

---

### Post by Robbyx on 2023-05-09
Thank you for returning to this problem of mine. I thought you might have been taken ill, hence the email. 

I have made some progress in understanding what needs to be done. 

[https://unix.stackexchange.com/questions/400327/change-btrfs-default-subvolume-in-order-to-delete-snapshot]("https://unix.stackexchange.com/questions/400327/change-btrfs-default-subvolume-in-order-to-delete-snapshot")

I know it is possible to do the change of default subvol, but I am not dealing with subvol. They are directories. So it gets more complex.


I have been thinking that I should switch to OpenSuse's Leap. They have some very useful tools to ensure that  the installation is likely to work well.  Their yast installer looks particularly apposite and I have been hoping that it would not make the same mistake of Ubuntu by picking up the wrong /home. 

I have not yet switched, but to have 10 days without email, no access to lastpass passwords because I can not change the existing password, threats from Companies House requiring me to file a doc but I can not login, and a blank /home which means that there is no history for say Thunderbird. All very unsettling. I am hoping that another version of linux might just clear up my problems without us both being ground down. .

Do you think I should go down that route? I assume that if it fails then I can come back to this thread and try to correct the /home with your help.

---

### Post by #&amp;thj^% on 2023-05-09
Robbin all this is a personal choice that sadly I just can't make for you.
Al I know for sure is this a first time I've seen a problem like you have now. ???
But I would just have to think that the new Install from another OS (Suse) will overwrite what you have now.(Basically like a new fresh install)
Anyway while you decide which choice you want to take, I have obligations to fulfill so I'll check back again when I can.
But return the info I asked to see if you decide to push forward with what you have now.
Kind Regards

---

### Post by Robbyx on 2023-05-09
Thank you for your help throughout this difficult time I have had with my computer. I hope your other obligations are not too overwhelming for you and you have enough strength to deal with them.  

I will come back if I need to go back to Ubuntu. As far as I can tell,  both systems work similarly in that they look to the home/ directory for settings, and history. So yes I will have to reinstall the programs I use but I should then l be able to I view and use previous settings, history, addons, etc. I shall see.

---

### Post by #&amp;thj^% on 2023-05-10
I wish you the best of luck here.
Just to help you look:
```
sudo btrfs filesystem show
Label: none  uuid: 21269c49-4ab1-4987-94d3-8153e101e5bc
	Total devices 1 FS bytes used 11.64GiB
	devid    1 size 457.15GiB used 15.02GiB path /dev/nvme0n1p3

```
```
sudo btrfs filesystem show /home
Label: none  uuid: 21269c49-4ab1-4987-94d3-8153e101e5bc
	Total devices 1 FS bytes used 11.64GiB
	devid    1 size 457.15GiB used 15.02GiB path /dev/nvme0n1p3

```
```
sudo btrfs filesystem show /dev/nvme0n1p3
Label: none  uuid: 21269c49-4ab1-4987-94d3-8153e101e5bc
	Total devices 1 FS bytes used 11.64GiB
	devid    1 size 457.15GiB used 15.02GiB path /dev/nvme0n1p3

```

---

### Post by Robbyx on 2023-05-22
I have been completely locked out of my account until now. In brief I was not able to log into my lastpass password holder and so could not access email, and all my other passworded activities. I have noticed that gmail and others insist on emailing a confirmation code, and they will not accept a change in the email account. So I could not pick up the confirmation codes. It has been very difficult for me as in effect  I have not been able to read any incoming mail  for at least 2 weeks. I have obtained the relevant passwords from a previous password manager that I was able to open today. 

I looked at Arch Linux and found that to make it understandable needs a disproportionate amount of study and research.  I found it lacking in standard sensible intelligent  menus that change according  to previous answers. The installer has only one option of a keyboard layout. To choose another layout means installing it after starting the installer with in my case a dvorak keyboard and there was a lot more like this so I gave up on it.  Suse Linux had a simple installer which did not appear to deal with my situatio. So I looked at their complex version and could not understand how to apply it to me. 

I would have come back earlier but for my inability to log in to this  forum. 

I have resolved a lot in the meantime. I now know for certain that the Efi partition is working properly.  I believe that previously it was not working and so Ub was defaulting to a Bios installation. I have found the set up advice for the EFI partition is lacking. It was quite hard to correctly  set up that partition. 

What is now left is solving as to why the @home is not being mounted to /home.  I think it is something to do with the home partition being different from the root.

I have found advice at 

[https://jtuto.com/ubuntu/solved-ubuntu-22-04-server-installer-does-not-create-btrfs-subvolumes/]("https://jtuto.com/ubuntu/solved-ubuntu-22-04-server-installer-does-not-create-btrfs-subvolumes/")

Although I am using a desktop and not a server I can see the solution  will apply to my situation. 

I have applied  with success the advice up to the 2nd line of the "Then run:" but can not get the 3rd line to work and so have stopped at that point.   Can you please look at that solution and suggest a way I can get to the end of it? Of course if you consider that the advice can be bettered please let me know.

---

### Post by #&amp;thj^% on 2023-05-22
> **Robbyx said:**
> 
I have found advice at 

[https://jtuto.com/ubuntu/solved-ubuntu-22-04-server-installer-does-not-create-btrfs-subvolumes/]("https://jtuto.com/ubuntu/solved-ubuntu-22-04-server-installer-does-not-create-btrfs-subvolumes/")

Although I am using a desktop and not a server I can see the solution  will apply to my situation. 

I have applied  with success the advice up to the 2nd line of the "Then run:" but can not get the 3rd line to work and so have stopped at that point.   Can you please look at that solution and suggest a way I can get to the end of it? Of course if you consider that the advice can be bettered please let me know.

Robbyx can you really believe I know what the heck your doing now???
We have jumped through so many suggestions and links and I've not even thought about this post till now.

Please refresh me on what you have done up to current state.
Yours won't look like mine but is a reference to "**/home **"
```
 /etc/fstab
# /dev/nvme0n1p3
UUID=7f33692e-9da0-40e1-865c-24ba862bd0fb	/         	btrfs     	rw,relatime,ssd,discard=async,space_cache=v2,subvolid=256,subvol=/root	0 0

# /dev/nvme0n1p1
UUID=FBF8-D9F6      	/boot     	vfat      	rw,relatime,fmask=0022,dmask=0022,codepage=437,iocharset=ascii,shortname=mixed,utf8,errors=remount-ro	0 2

# /dev/nvme0n1p3
UUID=7f33692e-9da0-40e1-865c-24ba862bd0fb	/home     	btrfs     	rw,relatime,ssd,discard=async,space_cache=v2,subvolid=256,subvol=/root	0 0

# /dev/nvme0n1p2
UUID=942477e9-2663-4c7a-a3f1-78850f5965e7	none      	swap      	defaults  	0 0

```
EDIT:2 if you read this>>"It is a standard setup for a btrfs file system with @ and @home subvolumes.

@ is mounted to / and @home is mounted to /home."
Then show me where it errors out:
Was it from 
```
sudo mv /mnt/home/* /mnt/@home
```
Show me that much please.

---

### Post by Robbyx on 2023-05-22
I have been thinking about virtually nothing else, but about the problem I have with the /home directory as we discussed. I have spent all the days and 
much of the night trying to find a solution, because I was locked out of my password manager, locked out of emails in or out, unable to 
login to any sites including this forum, unable to log in to my bank accounts, etc. 

 I am sorry for not making myself clear. I hope the following is useful and be assured I am grateful for your help:


This is how far I got with the instructions referred to in my previous post:

> sudo mount /dev/nvme0n1p4 /mnt

Run sudo nano /mnt/etc/fstab, remove this line

 /dev/disk/by-uuid/4466d07c-a9a8-452b-a970-667f55eff17a / btrfs defaults 0 1

and add these lines:

/dev/disk/by-uuid/4466d07c-a9a8-452b-a970-667f55eff17a / btrfs subvol=@ 0 0
/dev/disk/by-uuid/4466d07c-a9a8-452b-a970-667f55eff17a /home btrfs subvol=@home 0 0

Then run (in terminal, line by line):

sudo btrfs sub create /mnt/@
sudo btrfs sub create /mnt/@home
sudo mv /mnt/home/* /mnt/@home 

when the > sudo mv /mnt/home/* /mnt/@home[ was run the error message was

> no such file or directory


---

### Post by #&amp;thj^% on 2023-05-22
Is the path your using correct, if it is something is horribly wrong...yuck.
what dose your current fstab now read?

---

### Post by Robbyx on 2023-05-22
This is my current fstab. I have yet to add the further drives and mount command options:

```
# / was on /dev/nvme0n1p1 during installation
UUID=25f25728-d984-4438-aa0b-6cce43268fed /               btrfs   subvol=@ 0       0
# /boot/efi was on /dev/nvme0n1p3 during installation
UUID=BD0A-F1F2  /boot/efi       vfat    umask=0077      0       0
# /home was on /dev/nvme0n1p2 during installation
UUID=5bb8aa95-b657-4297-be5b-4352a09596b0 /home           btrfs   subvol=@home 0       0
# swap was on /dev/sdb7 during installation
UUID=6bbc8a5a-b488-49b6-904a-952e05463815 none            swap    sw              0       0
```

To remind myself what is happening:

The /home does not show the historically full version. Instead it shows the one that came from the last reinstallation which leaves out loads of  data such as thunderbird's retained posts and structure.

---

### Post by Robbyx on 2023-05-23
Btrfs assistant, shows the following sub vols have been created as of today (includes Container subvols):

```
@          
Size: 0.00  

@home
Size:  5.77Gib

@home/rob/snap-copy-one
size: 232kiB

home
size: 4820GiB
```

Here is the output from lsblk:

> NAME        MAJ:MIN RM   SIZE RO TYPE MOUNTPOINTS
loop0         7:0    0  63.5M  1 loop /snap/core20/1891
loop1         7:1    0  73.1M  1 loop /snap/core22/634
loop2         7:2    0  63.3M  1 loop /snap/core20/1822
loop3         7:3    0     4K  1 loop /snap/bare/5
loop4         7:4    0   242M  1 loop /snap/firefox/2667
loop5         7:5    0 240.6M  1 loop /snap/firefox/2356
loop6         7:6    0 346.3M  1 loop /snap/gnome-3-38-2004/119
loop7         7:7    0 460.6M  1 loop /snap/gnome-42-2204/102
loop8         7:8    0  91.7M  1 loop /snap/gtk-common-themes/1535
loop9         7:9    0 349.7M  1 loop /snap/gnome-3-38-2004/140
loop10        7:10   0  49.8M  1 loop /snap/snapd/18357
loop11        7:11   0  12.3M  1 loop /snap/snap-store/959
loop12        7:12   0  53.2M  1 loop /snap/snapd/19122
loop13        7:13   0   452K  1 loop /snap/snapd-desktop-integration/83
loop14        7:14   0  45.9M  1 loop /snap/snap-store/638
loop15        7:15   0   304K  1 loop /snap/snapd-desktop-integration/49
sda           8:0    0 465.8G  0 disk 
&#9492;&#9472;sda1        8:1    0 465.8G  0 part 
sdb           8:16   0 232.9G  0 disk 
&#9500;&#9472;sdb4        8:20   0     1K  0 part 
&#9500;&#9472;sdb5        8:21   0  88.4G  0 part 
&#9500;&#9472;sdb6        8:22   0   105G  0 part 
&#9492;&#9472;sdb7        8:23   0  39.5G  0 part [SWAP]
sdc           8:32   0 698.6G  0 disk 
&#9500;&#9472;sdc1        8:33   0 645.1G  0 part 
&#9492;&#9472;sdc2        8:34   0  53.6G  0 part 
sr0          11:0    1  1024M  0 rom  
nvme0n1     259:0    0 894.3G  0 disk 
&#9500;&#9472;nvme0n1p1 259:1    0  51.2G  0 part /var/snap/firefox/common/host-hunspell
&#9474;                                     /
&#9500;&#9472;nvme0n1p2 259:2    0 199.1G  0 part /home
&#9500;&#9472;nvme0n1p3 259:3    0   999M  0 part /boot/efi
&#9492;&#9472;nvme0n1p4 259:4    0   643G  0 part 


I hope it helps us find a solution.> 

---

### Post by Robbyx on 2023-05-23
I do not understand why two versions of /home exist, but the empty @home gets mounted in pref to the older full  version. I assume one is a snap.

Is it possible to insist that  the full old version be mounted instead of the smaller empty version?

Would specifying the uuid of  the sub vol force the correct version to be mounted?

**Another similar solution:**

I make a current snapshot of the older version. Looking at SnapperGUI ---> New --->create configuration,  there seems to be a possibility of using Snapper to do it. Will it work the way I want? I am not yet used to the system.

---

### Post by #&amp;thj^% on 2023-05-23
> **Robbyx said:**
> I do not understand why two versions of /home exist, but the empty @home gets mounted in pref to the older full  version. I assume one is a snap.
It's a bug in the new installer, they are working on it. And More info on this, 

The new filesystem (/home) is mounted over the directory (/home) on the original filesystem. So the files are still there, but they are hidden from simple access.

To avoid this, you would need to add some steps to your process.

Namely, rename the** /home** directory after creating a copy of the content. **Then, create a new empty directory /home as the new mount point. Then when you mount the** /home** filesystem it's being mounted over an empty directory and you can still get to the** /oldhome directory** (or whatever you called it).
You may in the future want to keep your /home on /root less problems until you get the gist of btrfs.


> **Robbyx said:**
> 
Would specifying the uuid of  the sub vol force the correct version to be mounted?
Yes it should. (But that's only a proven on my end)
> **Robbyx said:**
> **Another similar solution:**

I make a current snapshot of the older version. Looking at SnapperGUI ---> New --->create configuration,  there seems to be a possibility of using Snapper to do it. Will it work the way I want? I am not yet used to the system.
You are all over the place here slow down relax cool heads prevail, panic and hurry lead to disaster.
Robbin you have yet to show me anything that I can in good standing recommend for you.
you want **something** like this:

```
sudo mkdir /mnt/old
sudo mkdir /mnt/new
sudo mount /dev/sda2 /mnt/old -o subvolid=5
sudo mount /dev/sdb1 /mnt/new -o subvolid=5
```

Now, you need to find your home subvol using btrfs, you can see all the subvols with:

```
sudo btrfs subvolume list /mnt/old
sudo btrfs subvolume list /mnt/new
```

If you share the output of those last commands we ?should? be able to fix it.

---

### Post by MAFoElffen on 2023-05-23
Just been following from the sidelines, and wishing you both well with this.

Would these two queries help you two to share info?
```

mount | grep 'btrfs' | grep -v 'snap'
findmnt | grep 'btrfs\|TARGET' | grep -v 'snap'

```
Back to watching...

---

### Post by Robbyx on 2023-05-24
The old (correct) version of /home, being hidden,  is not currently mounted on sda2 in the  working installation.  

Can you please suggest  the syntax to mount the subvol **home** to the /mnt/old mount point. 

This comes from the man pages, but I am unsure if it is applicable to me:

[I]One can also remount a single file (on a single file). It&#8217;s also possible to use a bind mount to create a mountpoint from a regular directory, for example:

          mount --bind foo foo

       The bind mount call attaches only (part of) a single filesystem, not possible submounts. The entire file hierarchy including submounts can be attached a second place by using:

          mount --rbind olddir newdir
[/I]



Currently, I only see the old home  via the live usb or  btrfs assistant:

**Btrrfs assistant shows that  under the home directory ** 
(UUID="5bb8aa95-b657-4297-be5b-4352a09596b0") there are three subvols;

@home, @home/robins/snap-copy-one,  **home**

I assume it is the plain **home** that should be mounted into the /mnt/old 

[B]Further stats;
[/B]
```
robins@robins-desktop:~$ sudo lsblk
[sudo] password for robins: 
NAME        MAJ:MIN RM   SIZE RO TYPE MOUNTPOINTS
loop0         7:0    0  63.5M  1 loop /snap/core20/1891
loop1         7:1    0  73.1M  1 loop /snap/core22/634
loop2         7:2    0     4K  1 loop /snap/bare/5
loop4         7:4    0  63.3M  1 loop /snap/core20/1822
loop5         7:5    0 346.3M  1 loop /snap/gnome-3-38-2004/119
loop6         7:6    0 349.7M  1 loop /snap/gnome-3-38-2004/140
loop7         7:7    0   242M  1 loop /snap/firefox/2667
loop8         7:8    0  91.7M  1 loop /snap/gtk-common-themes/1535
loop9         7:9    0 460.6M  1 loop /snap/gnome-42-2204/102
loop10        7:10   0  45.9M  1 loop /snap/snap-store/638
loop11        7:11   0  53.2M  1 loop /snap/snapd/19122
loop12        7:12   0  49.8M  1 loop /snap/snapd/18357
loop13        7:13   0   304K  1 loop /snap/snapd-desktop-integration/49
loop14        7:14   0  12.3M  1 loop /snap/snap-store/959
loop15        7:15   0   452K  1 loop /snap/snapd-desktop-integration/83
loop16        7:16   0 242.9M  1 loop /snap/firefox/2710
sda           8:0    0 465.8G  0 disk 
&#9492;&#9472;sda1        8:1    0 465.8G  0 part 
sdb           8:16   0 232.9G  0 disk 
&#9500;&#9472;sdb4        8:20   0     1K  0 part 
&#9500;&#9472;sdb5        8:21   0  88.4G  0 part 
&#9500;&#9472;sdb6        8:22   0   105G  0 part 
&#9492;&#9472;sdb7        8:23   0  39.5G  0 part [SWAP]
sdc           8:32   0 698.6G  0 disk 
&#9500;&#9472;sdc1        8:33   0 645.1G  0 part 
&#9492;&#9472;sdc2        8:34   0  53.6G  0 part 
sr0          11:0    1  1024M  0 rom  
nvme0n1     259:0    0 894.3G  0 disk 
&#9500;&#9472;nvme0n1p1 259:1    0  51.2G  0 part /var/snap/firefox/common/host-hunspell
&#9474;                                     /
&#9500;&#9472;nvme0n1p2 259:2    0 199.1G  0 part /home
&#9500;&#9472;nvme0n1p3 259:3    0   999M  0 part /boot/efi
&#9492;&#9472;nvme0n1p4 259:4    0   643G  0 part 


robins@robins-desktop:~$ sudo btrfs subvolume  list 
btrfs subvolume list: exactly 1 argument expected, 0 given
robins@robins-desktop:~$ sudo blkid
/dev/nvme0n1p3: UUID="BD0A-F1F2" BLOCK_SIZE="512" TYPE="vfat" PARTUUID="36bdb116-03"
/dev/nvme0n1p1: UUID="25f25728-d984-4438-aa0b-6cce43268fed" UUID_SUB="78db2336-a96c-4a70-b975-b064b5762ebe" BLOCK_SIZE="4096" TYPE="btrfs" PARTUUID="36bdb116-01"
/dev/nvme0n1p4: LABEL="Data" UUID="f5ab46ce-b3da-4e59-8f18-3418fe272a09" UUID_SUB="62eb831e-e336-455d-9804-afed243f3c28" BLOCK_SIZE="4096" TYPE="btrfs" PARTUUID="36bdb116-04"
/dev/nvme0n1p2: UUID="5bb8aa95-b657-4297-be5b-4352a09596b0" UUID_SUB="12d8a1ae-9e45-4467-99d1-bae0e01b1c53" BLOCK_SIZE="4096" TYPE="btrfs" PARTUUID="36bdb116-02"
/dev/sdb7: UUID="6bbc8a5a-b488-49b6-904a-952e05463815" TYPE="swap" PARTUUID="00083267-07"
/dev/sdb5: LABEL="mydocs" UUID="8d99bfc8-90ab-4488-b7da-87e7676aff19" BLOCK_SIZE="4096" TYPE="ext4" PARTUUID="00083267-05"
/dev/sdb6: LABEL="Data inc AV" UUID="1a2e8d10-7b93-4de1-b551-31db6a621276" BLOCK_SIZE="4096" TYPE="ext4" PARTUUID="00083267-06"
/dev/sdc2: LABEL="Deju_dup_backup" UUID="c79b648e-48c5-45db-949f-a835928f3816" BLOCK_SIZE="4096" TYPE="ext4" PARTUUID="0008ffd0-02"
/dev/sdc1: LABEL="hitachi 750gb" UUID="3c4f4688-4bd7-4262-a2b8-86f71bbd6d0b" BLOCK_SIZE="4096" TYPE="ext4" PARTUUID="0008ffd0-01"
/dev/sda1: UUID="32677e49-0894-4d3f-8cc4-7e27b74ac6f0" BLOCK_SIZE="4096" TYPE="ext4" PARTUUID="4950cc35-01"
/dev/loop1: TYPE="squashfs"

([I]balance of loops removed from copy) 
[/I]

```

---

### Post by #&amp;thj^% on 2023-05-25
Robbyx I'm up to my neck in my daily workloads very sorry I can't give you proper support in a timely fashion.
MAFoElffen can help you if you don't mind and I wouldn't think you would.
Best of luck, I'll keep checking in when I can.

---

### Post by MAFoElffen on 2023-05-25
Okay. 1fallen PM'ed me and says he is burried in work. You asked me if I could help in his absense...

You have a partition for your /home. You have a btrfs subvol called @home You created two folder under /mnt as /mnt/new & /mnt/old...

In the 'system-info' script, when I try to show subvolumes, I use this format:
- Indentify all volumes with 'btrfs" as a filesystem type... Save the partition names
- Use the partition names to list the sub volumes, like this:
```

sudo lsblk -o name,mountpoint,size,fstype | grep 'btrfs' | awk '{print $1 "  " $2}' | sed 's/var.*//g' | sed 's/^[\|,`]-/\|_/g'
mount | grep -v 'snap' | grep 'btrfs' | awk '{print $3}'

```
From the second command, I take that output as array of names
```

        btdev_vols=$(mount | \
            grep -v 'snap' | \
            grep 'btrfs' | \
            awk '{print $3}' )
            
        for vol in ${btdev_vols}
        do
            echo "Properties of BTRFS Volume: $vol"
            sudo btrfs property get $vol
            nl
        done
            
            if [ -z "$SubVolName" ]
            then
                echo -e "BTRFS filesystem present on $vol, but no BTRFS SubVolumes there."
                nl
            else
                sudo btrfs subvol show -h $vol
                nl
            fi
        done

```
Lets see the output from those please, wrapped within CODE Tags, like this:
[noparse][CODE}
Paste your output in here...
After typing the code tags.
[/CODE][/noparse]

---

### Post by Robbyx on 2023-05-25
1fallen, thank you for all that you have done for me in this thread. As I have commented more than once, I really do appreciate your help and support so far. I feel as a result I am near to resolving what for me is a problem for which I can not see a solution.  

Thank you for agreeing to keep an occasional  watch on the progress of my thread. 

With my best wishes and thanks, Robin.

PS
I am anxious to get my system to work and so I am happy for MAFoElffen to step in. I look forward to his further help.

---

### Post by MAFoElffen on 2023-05-25
Patiently waiting.

I have to go to work in about 2-1/2 hours.

---

### Post by Robbyx on 2023-05-25
Thank you for your two segments  of code. I assumed that both segments should go into a bash file as is!:

```
This is the content of the Bash file:

sudo lsblk -o name,mountpoint,size,fstype | grep 'btrfs' | awk '{print $1 "  " $2}' | sed 's/var.*//g' | sed 's/^[\|,`]-/\|_/g'
mount | grep -v 'snap' | grep 'btrfs' | awk '{print $3}'

btdev_vols=$(mount | \
            grep -v 'snap' | \
            grep 'btrfs' | \
            awk '{print $3}' )
            
        for vol in ${btdev_vols}
        do
            echo "Properties of BTRFS Volume: $vol"
            sudo btrfs property get $vol
            nl
        done
            
            if [ -z "$SubVolName" ]
            then
                echo -e "BTRFS filesystem present on $vol, but no BTRFS SubVolumes there."
                nl
            else
                sudo btrfs subvol show -h $vol
                nl
            fi
        done

```


This produced only the following response
```

robins@robins-desktop:~/scripts$ bash home_2486578_#34.sh
[sudo] password for robins: 
&#9500;&#9472;nvme0n1p1  /
&#9500;&#9472;nvme0n1p2  /home
&#9492;&#9472;nvme0n1p4  643G
/
/home
Properties of BTRFS Volume: /
ro=false
label=


```

I would be very surprised if I have handled your code correctly. If you adjust my bash file as quoted above,  I will then send you its revised output.

Robin

---

### Post by MAFoElffen on 2023-05-25
Here you go:
```

#!/bin/bash

function GetBtrfs()
{
    echo -e "${setansi}----------  BTRFS Information:$ransi"
    # Show BTRFS dev's and their mounts
    bt_lsblk=$(sudo lsblk -o name,mountpoint,size,fstype,UUID | \
        grep 'btrfs' | \
        awk '{print $1 "  " $2}' | \
        sed 's/var.*//g' | \
        sed 's/^[\|,`]-/\|_/g' )
        
    # echo "Debug -- bt_lsblk: $bt_lsblk"

    if [ -z "$bt_lsblk" ]
    then 
        echo -e "There are no BTRFS vdev's present."
        nl
    else
        echo -e "There are BTRFS vdev's present: "
        nl
        echo -e "BT_VDEV    MOUNT "
        echo -e "$bt_lsblk"
        nl
        btrfs_detail=0 # Set flag for BTRFS present
        GetBtrfsInfo
    fi
}

function GetBtrfsInfo()
{
    if [ $btrfs_detail -eq 0 ]
    then
        sudo btrfs filesystem show
        nl

        # Get for BTRFS volume names
        btdev_vols=$(mount | \
            grep -v 'snap' | \
            grep 'btrfs' | \
            awk '{print $3}' )
            
        for vol in ${btdev_vols}
        do
            echo "Properties of BTRFS Volume: $vol"
            sudo btrfs property get $vol
            nl
        done
            
        # echo "Debug -- btdev_vols :"
        # echo "$btdev_vols" # DEBUG

        for vol in ${btdev_vols[@]}
        do
            # echo "Debug -- vol: $vol"
            
            FsName=$()
            
            SubVolName=$(sudo btrfs subvol list $vol | \
                awk '{print $9} ' )
    
            # echo "Debug -- SubVolName: $SubVolName"
            
            if [ -z "$SubVolName" ]
            then
                echo -e "BTRFS filesystem present on $vol, but no BTRFS SubVolumes there."
                nl
            else
                sudo btrfs subvol show -h $vol
                nl
            fi
        done
    fi
}

GetBtrfs

```

---

### Post by MAFoElffen on 2023-05-25
Waiting for that so we can see the mountpoint and subvolid of @home...

---

### Post by Robbyx on 2023-05-25
with the new script I now get;

> robins@robins-desktop:~/scripts$ bash home_2486578_#34.sh
----------  BTRFS Information:
There are BTRFS vdev's present: 


---

### Post by Robbyx on 2023-05-25
BTW I used Nano to edit the original sh. I have checked it again on the screen it is the same as your amended version.

---

### Post by MAFoElffen on 2023-05-25
Also, there may be home & @home, both as subvolumes, both mounted at the same point... If so, then we can delete @home and rename subvolume home (if that exists as an object)... Do you see that 'that' condition is possible?

Otherwise, we handle that differently...

---

### Post by MAFoElffen on 2023-05-25
Do this then and choose to upload the script to a pastebin. Post the URL where it gets uploaded to:
```

wget -N -t 5 -T 10 https://github.com/UbuntuForums/system-info/raw/main/system-info && \
chmod +x system-info && \
./system-info --details

```
That way we can get around any typo's. LOL Much easier.

---

### Post by Robbyx on 2023-05-25
> **MAFoElffen said:**
> Also, there may be home & @home, both as subvolumes, both mounted at the same point... If so, then we can delete @home and rename subvolume home (if that exists as an object)... Do you see that 'that' condition is possible?

Otherwise, we handle that differently...

I believe  there is home & @home. Here is my evidence taken from a previous post in this thread #31 and also another which contained;

```
Btrfs assistant, shows the following sub vols have been created as of today (includes Container subvols):

Code:

@          
Size: 0.00  

@home
Size:  5.77Gib

@home/rob/snap-copy-one
size: 232kiB

home
size: 4820GiB

```


Also I can see them if I load the USB installer but can not see all in nautilus.

---

### Post by MAFoElffen on 2023-05-25
And @home you created later right? And has nothing in it except subvol @home/rob/snap-copy-one? Please answer quickly. Only have 1-1/2 hours...

---

### Post by MAFoElffen on 2023-05-25
If so... delete subvol @home, rename subvol home to @home... Need instructions for that?

---

### Post by Robbyx on 2023-05-25
I have made a copy of of /home (30GiB) Relying on copies in this situation is scary. What command line should I have used  to copy the full partition? To speed things up can you give me the syntax for a compare to ensure it has copied everything?

---

### Post by Robbyx on 2023-05-25
> **MAFoElffen said:**
> If so... delete subvol @home, rename subvol home to @home... Need instructions for that?

It wouldn't hurt. How do I get to the subvol when they are hidden?

I have just looked again at Btrfs assistant:

@home 5.96
home 48.20

It has the option to delete a subvol. but not an option to rename. I wonder if it deletes the filesystem.

Both are in the same UUID.

---

### Post by Robbyx on 2023-05-25
Should I create a snapshot of /home.

I notice that btrfs assist allows me to make /home read only. That may prevent an unexpected deletion of /home

---

### Post by MAFoElffen on 2023-05-25
To rename, you just use the 'mv' command...

Is it still mounted as /home?

If so, then do
```

sudo mv @/home @/@home

```
It will rename it in the BTRFS tree.

Then do
```

echo "/dev/disk/by-uuid/$(blkid -s UUID -o value /dev/nvme0n1p2) /home btrfs defaults,subvol=@home 0 2" >> /etc/fstab

```
And ensure your fstab entry for the home mount matches that... commenting out the old entry.

EDIT:
Alternately, you could do
```

echo "UUID=$(blkid -s UUID -o value /dev/nvme0n1p2) /home btrfs defaults,subvol=@home 0 2" >> /etc/fstab

```

---

### Post by Robbyx on 2023-05-25
Maybe tthe best way to delete the @home and rename /home to @home is to do it within  the  usb installer if it allows it.  I can not exactly  recall what it shows or allows without logging in via the usb installer which I do not want to do while you are currently under time pressure.

---

### Post by MAFoElffen on 2023-05-25
Sorry for the edits. Trying to do this in a hurry...

---

### Post by MAFoElffen on 2023-05-25
Better to do it on the installed system. If done from the LiveUSB, you would have to chroot into the installed system from the LiveUSB first... to do that.

EDIT: I mean, you could do that, then just have to cut an paste the commands between. Would be easier that way... Would just take more time.

---

### Post by Robbyx on 2023-05-25
> **MAFoElffen said:**
> To rename, you just use the 'mv' command...

Is it still mounted as /home?

If so, then do
```

sudo mv @/home @/@home

```
It will rename it in the BTRFS tree.

Then do
```

echo "/dev/disk/by-uuid/$(blkid -s UUID -o value /dev/nvme0n1p2) /home btrfs defaults,subvol=@home 0 2"

```
And ensure your fstab entry for the home mount matches that...

EDIT:
Alternately, you could do
```

echo "UUID=$(blkid -s UUID -o value /dev/nvme0n1p2) /home btrfs defaults,subvol=@home 0 2"

```

I think it shows in a directory off nautilus. I do not think it shows '/'home but just home. 

The uuid is the same for both directories. Reading the commands you suggest that should not be a problem. Please comment if it is.

---

### Post by Robbyx on 2023-05-25
As home, and @home have the same uuid, i think i need to ask you to quickly check that none of the instructions will delete the full uuid

---

### Post by Robbyx on 2023-05-25
I have just checked btrfs assist by deleting an unneeded  .stapshot. It workded without damaging the uuid of the filesystem it was in.

---

### Post by MAFoElffen on 2023-05-25
Yes. Using from man btrfs:
```

usage: btrfs subvolume delete [options] <subvolume> [<subvolume>...]
       btrfs subvolume delete [options] -i|--subvolid <subvolid> <path>

```
If you want to be granular, then use the subvolid (from the second one there) to be sure that is only that one...

Be advised that that will prune that branch of the tree and remove anything you created within that specific subvol after you created that...

---

### Post by Robbyx on 2023-05-25
Thanks. Have a good day.

---

### Post by MAFoElffen on 2023-05-25
Did it work? I have about 50 minutes before leaving...

---

### Post by MAFoElffen on 2023-05-25
Getting ready to leave for work. Will check this again later when I am on a break.

---

### Post by Robbyx on 2023-05-25
Preliminary to making the changes I decided to make a snapshot of home (not @home). Btrfs assist failed to create it for two different locations.

I refer you to post #30 and #31 of this thread where I tried a similar approach to swapping the /home over, but it failed for no obvious reason and so I asked 1fallon why it was failing.  I refer you also to the link in #30 that has a very  similar approach to yours which I tried in vain to follow. I do note your suggestion is different in that you propose the use of the mv command. 

There are two relevant subvols that need adjusting:

home and  @home

I have been going over your advice, for which I thank you, in order to follow it exactly and prepare and think about the changes you propose.

Your proposal  is for me to make the relevant changes to fstab following the successful implementation of:

sudo mv @/home @/@home 

Can you confirm that the above cmd  will end up with home becoming @home which  in turn will be translated by btrfs to  /home, with  the  current home disappearing because it is over written by "home"?
Can you  confirm that you have used this approach at other times and it has worked,  if not I suggest I try to test it first.  How do you suggest I do it. Alternatively as you suggested the live CD might make it much less likely to go wrong, but it did not work in the implementation referred to in #31. 


Robin

---

### Post by MAFoElffen on 2023-05-26
I got home from work about 2am. Went through posts 30 & 31. Now I'm not sure it would work that way.

I tested some things last night, then got some sleep and tested some other things... There is a simpler way.

You still have both subvolumes of home and @home right?

If not recreate @home on /dev/nvme0n1p4...

Then we are going to do this, treat both btrfs /subvol's as separate objects and mount them in different places...
```

sudo mkdir /mnt/home
sudo mkdir /mnt/@home
sudo mount /dev/nvme0n1p4 -o subvol=home /mnt/home
sudo mount /dev/nvme0n1p4 -o subvol=@home /mnt/@home
ls /mnt/home
ls /mnt/@home

```
At this point, you should be able to verify that you have files in your original, old home subvolume... Back that data up now 'somewhere'...

Then we are going to copy it over to @home
```

rsync -avxHAX --progress /mnt/home/ /mnt/@home
ls /mnt/@home

```
Verfify that you have copied everything over...
```

diff -r -q /mnt/home /mnt/@home

```
Then unmount those two subvols from /mnt
```

sudo umount /mnt/home
sudo umount /mnt/@home

```
Change the line in the /etc/fstab over to the @home subvol and reboot...

Test everything is working...

If it is working, then do btrfs subvol delete with the subvolid of the original subvol=home to remove that subvol...

---

### Post by Robbyx on 2023-05-26
Everything has gone wrong and  I have been spending the day and much of last night trying to restore normality.

I decided to go ahead using the the USB start disk  to access the SDDE to delete the new and rename the old home directories. I was able to do it and it seemed to be a success. 

Next I rebooted having forgotten to check/ change the fstab. I used the USB stick to get in and alter the fstab, but the machine would not boot. I started up the grub repair usb disk, did some checking and changing but I found that I could not boot into the HD drive's  Ubuntu, it did not load. Gparted showed me that all the partitions on the drive  were lost and there was apparently no data (no partitons, nothing!).  I looked again at grub repair. it reports that there is an unrecognised disk label on the SDDE drive.  Loading grub repair in safe mode reports a Kernel panic- not syncing  with an exit code.  

I am now considering what to do next. I do not know how to recover all the missing portions on the SDDE drive so I am considering reformating it and restoring from my backups and hope they work.

I thank you for your help. I would have liked to thank you before now but I was fire fighting. Please accept my apologies for not following up your latest posting. I have only just known about it. I am writing this note using the live USB. 

Robin

---

### Post by Robbyx on 2023-05-27
I am very loath to use my backups because from a long period of trials with computers  I have found backups are seldom as good as my intentions.  I would like to retrieve my existing partitions for which  I have some evidence that they are still on the SDDE  but not being normally seen.

This specialized forum seems the most appropriate.  Can I continue with this thread as it is not a material  change of subject?

---

### Post by MAFoElffen on 2023-05-27
> **Robbyx said:**
> I am very loath to use my backups because from a long period of trials with computers  I have found backups are seldom as good as my intentions.  I would like to retrieve my existing partitions for which  I have some evidence that they are still on the SDDE  but not being normally seen.

This specialized forum seems the most appropriate.  Can I continue with this thread as it is not a material  change of subject?

Yes. Of course. You are still trying to recover from this issue.

Sorry for my confusion, but... What is the "SDDE drive" you are referring to? I am not familiar with that term.

And how has your partitions changed? Maybe post the results of
```

sud lsblk -o name,mountpoint,fstype,label,UUID -e7

```

---

### Post by MAFoElffen on 2023-05-27
1fallen and I have talked about this...

Please do this from a terminal session, booted from a LiveUSB:
```

wget -N -t 5 -T 10 https://github.com/UbuntuForums/system-info/raw/main/system-info && \
chmod +x system-info && \
./system-info --details

```
At the end of the run, select to upload the report to a pastebin. Copy the URL of where it uploads to, and post it.

Then we can see what is going on, and if you can recover from whatever is going on.

---

### Post by Robbyx on 2023-05-27
**gparted** 

Gparted  is only picking up on nvme0n1.  subvols: p1-p4 have become invisible.  Same for Nautilus and disks. 

See Screenshot from 2023-05-27 20-53-03.png

**fdisk  -l  /dev/nvme0n1**

Note p3 is***_ ee GPT._*** I think this is  the cause of the disappearances of the subvols. I was having problems retaining the efi status of 1p3. I think it was Gparted that offered me either dos32 ? or gpt. I chose GPT. There after the subvols disappeared. 

I have run some basic tools to get the results  quoted below   but they are not specific to  BTRFS. I do not know which equivalent tools are needed for  BTRFS::

t
```
buntu@ubuntu:~$ sudo fdisk  -l  /dev/nvme0n1
Disk /dev/nvme0n1: 894.25 GiB, 960197124096 bytes, 1875385008 sectors
Disk model: Force MP510                             
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x36bdb116

Device         Boot     Start        End    Sectors   Size Id Type
/dev/nvme0n1p1        2048000  109320191  107272192  51.2G 83 Linux
/dev/nvme0n1p2      109320192  526884863  417564672 199.1G 83 Linux
/dev/nvme0n1p3 *         2048    2047999    2045952   999M ee GPT
/dev/nvme0n1p4      526884864 1875384319 1348499456   643G 83 Linux

Partition table entries are not in disk order.
```

**sudo e2label /dev/nvmeon1**
```


$ sudo e2label /dev/nvmeon1
$ sudo e2label /dev/nvmeon1p1-4

Both the above result in:
e2label: No such file or directory while trying to open /dev/nvmeon1
Couldn't find valid filesystem superblock.
```
[B]
Further notes[/B]

*What is the "SDDE drive" you are referring to? I am not familiar with that term. *
Perhaps I should not be familiar with it as well. I am referring to a solid state drive. Presumably SSD

**sudo lsblk -o name,mountpoint,fstype,label,UUID -e7**

```

ubuntu@ubuntu:~$ sudo lsblk -o name,mountpoint,fstype,label,UUID -e7

NAME MOUNTPOINT FSTYPE LABEL                UUID
sda                                         
&#9492;&#9472;sda1
                ext4                        32677e49-0894-4d3f-8cc4-7e27b74ac6f0
sdb                                         
&#9500;&#9472;sdb4
&#9474;                                           
&#9500;&#9472;sdb5
&#9474;               ext4   mydocs               8d99bfc8-90ab-4488-b7da-87e7676aff19
&#9500;&#9472;sdb6
&#9474;               ext4   Data inc AV          1a2e8d10-7b93-4de1-b551-31db6a621276
&#9492;&#9472;sdb7
     [SWAP]     swap                        6bbc8a5a-b488-49b6-904a-952e05463815
sdc                                         
&#9500;&#9472;sdc1
&#9474;               ext4   hitachi 750gb        3c4f4688-4bd7-4262-a2b8-86f71bbd6d0b
&#9492;&#9472;sdc2
                ext4   Deju_dup_backup      c79b648e-48c5-45db-949f-a835928f3816
sdd             iso966 Ubuntu 22.04.2 LTS amd64
&#9474;                                           2023-02-23-04-13-44-00
&#9500;&#9472;sdd1
&#9474;    /cdrom     iso966 Ubuntu 22.04.2 LTS amd64
&#9474;                                           2023-02-23-04-13-44-00
&#9500;&#9472;sdd2
&#9474;               vfat   ESP                  F7DB-4D56
&#9500;&#9472;sdd3
&#9474;                                           
&#9492;&#9472;sdd4
     /var/crash ext4   writable             905adf7a-fc06-11ed-9cef-47d5bd1c42f6
sde                                         
&#9492;&#9472;sde1
     /media/ubu vfat                        E0D0-35DF
sr0                                         
nvme0n1

```

---

### Post by Robbyx on 2023-05-27
I have just noticed I have not run your code properly (the one that should have gone to the pastebin. I am doing it now.

---

### Post by Robbyx on 2023-05-27
I am struggling with the detailed report for the pastebin.

1. There was no url ref as to where it is stored.
2. IIt does not allow me to block the whole report.I can not block and copy more than one page at a time. 

Assuming it has not been automatically sent to you. I will now copy each page into a libreoffice file and send the file to your internal mail account if I can find one. 
I tried to send you the file by internal email but it is blocked to me. 

Robin

---

### Post by Robbyx on 2023-05-27
I finding it taking a long time. Is there a specific part you need? I think my problem is that I can not copy the full output in one go. I am up to 566 lines copied so far. I do not know how many lines are in the full report

---

### Post by Robbyx on 2023-05-27
I am struggling with the detailed report for the pastebin.

1. There was no url ref as to where it is stored.
2. IIt does not allow me to block the whole report.I can not block and copy more than one page at a time. 

Assuming it has not been automatically sent to you. I will now copy each page into a libreoffice file and send the file to your internal mail account if I can find one. 
I have tried a second terminal emulator. It too will not allow me to copy the whole file in one go. There is not mention of a pastebin. I can  not effectively search the file. It does not work. Maybe to do with live usb stick. 

Robin

---

### Post by Robbyx on 2023-05-28
It seems I need some help to post the detailed report in a safe way.

I have just tried to copy the full report in line with [https://wiki.ubuntu.com/Pastebin](https://wiki.ubuntu.com/Pastebin). I find that  only one page of the report is copied with one CTRL C

If there is any specific part of the report you would like me to post please ask.

---

### Post by MAFoElffen on 2023-05-28
The report is also generated and stored at ~/system-info.txt. You could open the report in Gedit, copy the whole thing... Log in to paste.ubuntu.com to create a blank pastebin, to paste it into...

We have tested that extensively, especially the upload part of it. Did it not have a Network connection to the internet?

It looks like you rste your EFI partiton to an invalid type for what it was. It should be type code ef00, not ee00... Wow.

---

### Post by Robbyx on 2023-05-28
[http://termbin.com/gnj41]("http://termbin.com/gnj")

---

### Post by Robbyx on 2023-05-28
I managed to get the report submitted to the bin,  only by clicking q at the end of it. The instructions did not make it clear at all.

Pastebinit was reported as missing at the start of the report process, but there was also advice that it was not important. I could not find the source of pastebinit.

R

---

### Post by MAFoElffen on 2023-05-28
Look at the file ~/system-info-link.log, and copy the URL from that log, to correct the link you posted. I think there was a typo, as that link is broken.

---

### Post by Robbyx on 2023-05-28
Try this:

[https://termbin.com/gnj41](https://termbin.com/gnj41)

---

### Post by Robbyx on 2023-05-28
I have been considering what to do next.  

Do you agree there is a chance that if I was able to correct the   EFI  file type recorded in the EFI partition table for nvme0n1p3 the hidden partitions might  reappear? 

/dev/nvme0n1p3 *         2048    2047999    2045952   999M ee GPT  

Would a hex editor help with the correction?



Robin

---

### Post by MAFoElffen on 2023-05-28
Looking at the report...

If it were me, I would make an image backup of /dev/nvme0n1 first, then do
```

sudo gdisk /dev/nvme0n1

```
Then while in gdisk, do

option: l
type:ef00
option: w

To change the partition type back from ee00 to ef00... That would only change the partiton type, without changing any of the contents of it. You did not foramt that partition did you? If so, then you would need to re-mount it in the fstab with the newly formed/changed UUID, and re-install grub to it.

---

### Post by Robbyx on 2023-05-28
I will follow your suggestion re gdisk

I assume that I cannot make an image backup without it appearing in  Nautilus on similar. At present nvme0n1 and its sub vols are not shown at all. 

Hopefully for the next stage how do I create an  image backup of p1? What tool is appropriate?

What do you think about this: 

> sudo gdisk /dev/nvme0n1
GPT fdisk (gdisk) version 1.0.8

Partition table scan:
  MBR: hybrid
  BSD: not present
  APM: not present
  GPT: not present


***************************************************************
Found invalid GPT and valid MBR; converting MBR to GPT format
in memory. THIS OPERATION IS POTENTIALLY DESTRUCTIVE! Exit by
typing 'q' if you don't want to convert your MBR partitions
to GPT format!
***************************************************************
I exited via Q

PS
No option showing.


As an alternative have you considered sfdisk?   it can backup and replicate a disk's partition tables. It can also restore a partition table from  file. Would it work with the likes of /dev/nvme0n1 etc?
I wondered if the inability to see the partitions in Nautilus is due to them not being mounted, but Blkid run from the live usb stick does not show /dev/nvme0n1 etc.

I just ran sudo blkid and notice that /dev/nvme0n1:  does appear with: PTTYPE="PMBR". Hardly something that could be mounted in that form

R

---

### Post by MAFoElffen on 2023-05-29
No. You edited the partition and it blew out...
> 
EE : -- Indicates a GPT Protective MBR followed by a GPT/EFI Header. Used to define a fake partition covering the entire disk.

More:
> 
A single partition of type EEh, encompassing the entire GPT drive (where "entire" actually means as much of the drive as can be represented in an MBR), is indicated and identifies it as GPT. Operating systems and tools which cannot read GPT disks will generally recognize the disk as containing one partition of unknown type and no empty space, and will typically refuse to modify the disk unless the user explicitly requests and confirms the deletion of this partition. This minimizes accidental erasures.[11] Furthermore, GPT-aware OSes may check the protective MBR and if the enclosed partition type is not of type EEh or if there are multiple partitions defined on the target device, the OS may refuse to manipulate the partition table.[12]

I don't see a good outcome of trying to repair it.

You could try sgdisk or fdisk... I don't believe you could really hurt it any more than it is already.

I mean 'sudo fdisk -l' sees it as:
```

Disk /dev/nvme0n1: 894.25 GiB, 960197124096 bytes, 1875385008 sectors
Disk model: Force MP510                             
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x36bdb116

Device         Boot     Start        End    Sectors   Size Id Type
/dev/nvme0n1p1        2048000  109320191  107272192  51.2G 83 Linux
/dev/nvme0n1p2      109320192  526884863  417564672 199.1G 83 Linux
/dev/nvme0n1p3 *         2048    2047999    2045952   999M ee GPT
/dev/nvme0n1p4      526884864 1875384319 1348499456   643G 83 Linux

```

If it were me, and I knew I had good backups... It would create a new GPT partition table and restore from backups.

---

### Post by Robbyx on 2023-05-29
I was worried that my backups were not comprehensive enough. I had carefully checked  and there was a high probability that  the current backups were in the Data partition of the SSD drive ie hidden. There were some backups on other drives but I wanted the latest if possible. 

 I am still writing to you in USB live mode because I have not rebooted  yet, but I have recovered all the data on my hidden drives 1p1 to 1p4. I can see the file contents of the previously hidden directories, using Nautilus from the Live USB.  

I followed advice  to use the TestDisk and rewrote the efi partition: 

>  
Creating a new partition with GParted will allocate a new, empty FAT, so it won&#8217;t recover anything, right? In fact if it wasn&#8217;t the case it would be likely to create corrupted partitions when allocating over previously existing space. testdisk however can just resurrect the previously existing partition. &#8211; 
Didier L

Mar 1, 2022 at 16:37
I do not use GParted anymore, but if I remember it correctly, creating a FAT partition without formatting it (I am sure that GParted allows that), the FAT is not allocated (= formatted), but only a msdos partition table (&#8220;MBR&#8221;) entry or GPT partition record is created. When you set the same parameters (start and end sector, the type and with GPT also the UUID), you get your partition back in unchanged state. (I am doing this usually using fdisk, which I prefer.) testdisk tries to do the same thing, but only guesses the correct parameters. &#8211; 
jiwopene
Mar 13, 2022 at 12:44

[https://askubuntu.com/questions/1394708/accidentally-deleted-efi-partition-system-is-still-running](https://askubuntu.com/questions/1394708/accidentally-deleted-efi-partition-system-is-still-running)



So I have to thank you gratefully for your patience and help. It has been a pleasure to deal with you and I have appreciated your thoroughness in trying to address the root cause of my problems.  I may come back if I have a problem with the home directory being hidden as per my original query. I note you gave me some really good instructions to deal with that, and I hope that will avoid the need to ask for further advice.  I shall see after the reboot.

---

