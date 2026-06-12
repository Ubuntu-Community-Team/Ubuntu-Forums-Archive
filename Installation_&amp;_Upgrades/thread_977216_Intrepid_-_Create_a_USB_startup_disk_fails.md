---
title: "Intrepid - Create a USB startup disk fails"
date: 2008-11-10
forum: Installation &amp; Upgrades
---

### Post by charonred on 2008-11-10
I've downloaded the Intrepid .iso and burnt to a CD, and just bought a 16GB Kingston USB stick to make a bootable Interpid USB stick.

I've booted the system using the Interpid CD and tried installing via 'System > Administration > Create a USB startup disk'

but after a few minutes of doing 'nothing' it fails to install. I saved the usb creator log as a text file on another drive.

Do I need to re-format the USB stick before attempting install again, and if so, how?

---

### Post by C.S.Cameron on 2008-11-10
I've had problems with "Create a USB startup disk", (usb-creator), on 4G and 8G Kingstons.
I would first suggest formating the flash drive in FAT32, some people have had success with this.
I have also found that first installing 8.10 using Unetbootin, deleting the files and reinstalling using usb-creator seems to work on larger Kingston drives.
The advantage with the U-C install over the Unetbootin install is that it is less hassle to get persistence to work.

---

### Post by cariboo on 2008-11-10
I've used the usb boot disk creator on a couple of Lexar 1Gb devices and ahd absolutely zero problems with the process. Instead of using the CD, I used the downloaded iso image, the only real advantage I could see though, was that it tokk less time than using the CD.

The reason I used the iso instead of the CD is that I always get read errors from the cdrom drive, so I thought, better safe then sorry.

Jim

---

### Post by charonred on 2008-11-10
Ok, I'll try to get it working using your above suggestions; but how exactly do I format a USB stick in Ubuntu 'Hardy' (my installed OS), or am I better off rebooting to XP to format it?

---

### Post by charonred on 2008-11-10
Ok, what I did was to use a combination of above guides; I rebooted to XP and used it to format the USB to fat32.

I then used UNetbootin in XP to install the 8.10 iso and then rebooted; unfortunately, once I was running from the USB there was no network - just wouldn't connect using existing ethernet connection ??  

So I rebooted using the 8.10 Live CD, deleted all files in USB and then used 'Create a USB startup disk' to install 8.10 from an .iso on h/drive to the  USB stick (which went without a problem this time) 

I rebooted system and ran Ubuntu from the USB stick; but again the network still wouldn't connect via existing ethernet :confused:

If I use the Intrepid Live CD (8.10), there's no connection; but using Hardy Live CD (8.04) there is - so what's wrong with 8.10 ? - maybe I should stick to using Hardy, and update it to 8.04.1 like the installed OS on my main PC.

_update_: seemed to have fixed the network connection ([see here]("http://ubuntuforums.org/showthread.php?p=6149100#post6149100"))

---

### Post by C.S.Cameron on 2008-11-10
After an Unetbootin install and deleting files, usb-creator seems to work every time.

---

### Post by lavinog on 2008-11-11
I suspect that making a usb startup disk with 4g or larger sticks might be an issue.

---

### Post by charonred on 2008-11-11
I have it running; though trying to update it is 'hit n miss' because it can't seem to update the Intrepid 'image' fully - beyond my limited skills.

But I'll keep fiddling with it cause I like my Mandriva 2008 flash-drive, and would really like to have Ubuntu setup as a 'portable PC' as well.

Any advice on how to fix the update issue of a Live image appreciated.

---

### Post by C.S.Cameron on 2008-11-11
The kernel in a persistent install is frozen as it is part of a read only image of the CD.
You can do a Full install to flash drive using the same method as to internal HDD. Boot from Live CD or Live USB and click install on the desktop.
(I suggest disabling your internal HDD first so you don't mess up it's MBR).
When you get to partitioning you can choose any of the three methods, use full disk, use remaining space or manual.
If you use remaining space or manual you can leave a little FAT32, (on the left side), so windows can see the flash drive.
For manual partitioning on a 4G drive, (minimum), 500 MB FAT32, 1 GB /home and 2.5 GB root, (/), is a good starting point and can be adjusted later using gparted.
Home and root can be formatted as ext3 or reiserfs.
This should make a flash drive that works just like a HDD install only a little slower at times.

---

### Post by charonred on 2008-11-11
Thanks, been thinking it was something like that. 

Anyhow after some updates and customisation, it only works on the PC I was using at the time (AMD SktA with Nvidia); although it won't keep some settings on next boot.

Disappointment is that it won't even boot on my main PC (AM2+ with ATI) - just hangs at *'Verifying DMI Pool Data'*, so it's not actually a portable OS in that sense - I've tried this on a couple of other PCs, and they won't boot either.

End result is the only way I can use it as a portable OS is to leave the standard 8.10 (or 8.04.1) install as it is when first 'created', with no attempt at updating, and just save docs to the home folder.

I 'spose at sometime there might be an actual flash drive that can be updated etc like the Mandriva 2008 Flash, but creating one is beyond my skills.

---

### Post by david@reid-iba.com on 2008-11-13
I'm having a similar but slightly different issue. 

I'm using a 16GB USB stick. No files. Empty.
I select the CDROM as source and load a burned CDROM from the .ISO image. (I've also pointed directly to the .ISO as the source.
The process says that it is STARTING UP and then it just hangs there for eternity. No error message. Just infinite nothingness.

I'll try with a 1GB stick and get back with the results.

---

### Post by david@reid-iba.com on 2008-11-13
> **david@reid-iba.com said:**
> I'm having a similar but slightly different issue. 

I'm using a 16GB USB stick. No files. Empty.
I select the CDROM as source and load a burned CDROM from the .ISO image. (I've also pointed directly to the .ISO as the source.
The process says that it is STARTING UP and then it just hangs there for eternity. No error message. Just infinite nothingness.

I'll try with a 1GB stick and get back with the results.

------------

Confirmed. I used a 1 GB stick and it works fine. There seems to be some issue with size.

---

### Post by charonred on 2008-11-13
as per earlier post; I did it this way and it got the 16 GB working - just don't try any updating; run as is (updates will mess the image and then it won't boot on any other PCs)
> **charonred said:**
> Ok, what I did was to use a combination of above guides; I rebooted to XP and used it to format the USB to fat32.

I then used UNetbootin in XP to install the 8.10 iso and then rebooted; unfortunately, once I was running from the USB there was no network - just wouldn't connect using existing ethernet connection ??  

So I rebooted using the 8.10 Live CD, deleted all files in USB and then used 'Create a USB startup disk' to install 8.10 from an .iso on h/drive to the  USB stick (which went without a problem this time) 

I rebooted system and ran Ubuntu from the USB stick; but again the network still wouldn't connect via existing ethernet :confused:

If I use the Intrepid Live CD (8.10), there's no connection; but using Hardy Live CD (8.04) there is - so what's wrong with 8.10 ? - maybe I should stick to using Hardy, and update it to 8.04.1 like the installed OS on my main PC.

[Download Unetbootin from here]("http://unetbootin.sourceforge.net/")

_update_: seemed to have fixed the network connection ([see here]("http://ubuntuforums.org/showthread.php?p=6149100#post6149100"))

---

### Post by C.S.Cameron on 2008-11-13
When all else fails the above method using a unebootin pre-install gets larger flash drives working for me also.

---

### Post by powel212 on 2008-11-21
More info about installing Ubuntu 8.10 on a USB pen drive.

I have now run tests with 
1G
2G
4G and
8G USB drives

Here are the results

Any one of them will do but 

1G is only big enough for install and firefox bookmarks. You can not run updates or install additional software without running out of space really fast.

2G is better if you install a couple of extra apps and Firefox pluggins you will be fine with 2G but still can not run all updates. Will run out of space.

4G can run all the updates and install a a number of programs. But, after I installed Chinese language support I ran out of space again. I guess most people don't need Chinese Support so 4G should be fine for most folks.

8G my current setup. I created a second 1G partition for my files, I find it more convenient to have my personal files on a separate partition.

note:
Please be aware that throughout these tests I have found that if you install and uninstall programs you do not regain much space. that is to say I have found if I install a 25m program and then uninstall it i only get back about 5m after the uninstall. So don't install anything you aren't sure you need. Also language support takes up huge amounts of space so only use what you need.

I also had a problem with the 8G - That is to say I could not install onto an 8G flash drive. I need to get another flash drive to test and see if this is a bug or just the drive i was using, but I solved the problem by creating a second 1G partition and installing the system to the 6.7G remaining.

Also

Be sure to enable universe and multiverse repositories.
I find this tool indispensable
apt-get install compizconfig-settings-manager
it's a GUI for compiz. 

Also need this deb if you want the Open office 3 update
deb [http://ppa.launchpad.net/openoffice-pkgs/ubuntu](http://ppa.launchpad.net/openoffice-pkgs/ubuntu) intrepid main

Love running ibex off my USB. Everybody at work is envious of my slick portable system. Can also be used in conjunction with your ipod. ipod can store data, movies, music and rythmbox allows you to play your itunes playlists from within the ipod. Awesome.

enjoy. Powel

---

### Post by powel212 on 2008-11-22
Have now tested with 16G flash drive. 

Successful configuration: first partition 10G for install and second partition 6G for Data
Installed from the live CD without incident.

However
several attempts using varying partition configurations trying to install from non Live CD, From my Ubuntu 8.10 desktop install. Fail, fail fail...every time the installation hits 4.69G and crashes during final stage.

Conclusion: Only use live CD to install persistent USB over 3G

Powel

---

### Post by DJ_Peng on 2008-11-23
I've tried it with a 2GB flash disk formatted to FAT32 but when I try to boot from it I get a black screen with just one thing on it
> jHas anyone else seen this behavior?

---

### Post by stephenrees on 2008-11-25
I have followed this thread with interest as I too have been unable to put a workable live version of Intrepid onto a USB thumb drive.

I was first intrigued by the suggestion that the drive needs to be formatted into FAT32 - because the drive(s) I have are in that format from new. But I followed along anyway. Formatted brand new empty 2GB FAT32 drive into FAT32 using Windows XP

Tried again - no change. A window called "Installing" opens and it says "starting up" but the progress bar never fills

Next got hold of UNetbootin from sourceforge. By the way there is a Linux version but I got the Windows XP one and installed Ubuntu onto the reformatted drive easily. It just didn't work. "Boot Error"

So I got back into Ubuntu again, moved the contents of the USB drive to the recycle bin and tried another "System/Administration/Create a USB start up disk" and I am still getting as far as I did before I did all this. Exactly nowhere. I am still looking at a blank progress bar.

Why is the reformat necessary?
What is wrong with UNetbootin?
Why does Ubuntu not do what it says it will do?

---

### Post by stephenrees on 2008-11-26
> **stephenrees said:**
> I have followed this thread with interest as I too have been unable to put a workable live version of Intrepid onto a USB thumb drive.

I was first intrigued by the suggestion that the drive needs to be formatted into FAT32 - because the drive(s) I have are in that format from new. But I followed along anyway. Formatted brand new empty 2GB FAT32 drive into FAT32 using Windows XP

Tried again - no change. A window called "Installing" opens and it says "starting up" but the progress bar never fills

Next got hold of UNetbootin from sourceforge. By the way there is a Linux version but I got the Windows XP one and installed Ubuntu onto the reformatted drive easily. It just didn't work. "Boot Error"

So I got back into Ubuntu again, moved the contents of the USB drive to the recycle bin and tried another "System/Administration/Create a USB start up disk" and I am still getting as far as I did before I did all this. Exactly nowhere. I am still looking at a blank progress bar.

Why is the reformat necessary?
What is wrong with UNetbootin?
Why does Ubuntu not do what it says it will do?

Answering myself: there is nothing wrong with UNetbootin. This is a good alternative for those who cannot get the built in "Create USB start up disk" to work. 

I used Unetbootin to load a desktop ISO of 8.10 and it is now running as a live disc on my Eeepc. 

The reformat is NOT necessary
There is nothing wrong with Unetbootin
The last question remains unanswered.

---

### Post by powel212 on 2008-11-27
I would try running the live cd from a different computer. I have had mixed results with different boxes,(computers). Try a different box and be advised 4G is the maximum persistence file size. Do not tell the usb creator to make a persistence larger than this.

Good luck

Powel

---

### Post by nwadams on 2008-11-27
hmm, interesting. My issue is not with the creation of the image. But when i try to boot to the usb stick image (created with the 8.10 creater. I get some error, i cant exactly remember it but its as if the image is bootable but will not boot

---

### Post by DJ_Peng on 2008-11-27
That sounds like what I get, although I don't even get an error, just that lonely "j".

---

### Post by cmay on 2008-11-27
> **DJ_Peng said:**
> I've tried it with a 2GB flash disk formatted to FAT32 but when I try to boot from it I get a black screen with just one thing on it
Has anyone else seen this behavior?
yes thats all i got out of it up to now. 
i installed belenix instead on my 2 gigabyte flashdrive when i could not find a way to resolve this.

---

### Post by cmay on 2008-11-28
i managed to get a standard debian install cd on a one gigabyte usb stick and jaunty jackalope on a two gigabyte usb stick just by formating the sticks to fat32 instead of fat16. it saves me the trouble of burning installaltions cd and is pretty handy. it works with ohter iso images than ubuntu cd for me. i think this is something that we will start to see included as standard in many linux distributions so good job well done to the developers.

---

### Post by kornelix on 2008-12-18
I also had this problem:
usb-creator starts up and sits there forever and does nothing. Apparently this happens when usb-creator is not happy with the USB stick (I could think of a better response).

I got it working as follows without resorting to Windows to format the USB.
```

$ cat /proc/mounts             # note the device ID of the USB stick (sdg)
[FONT=Fixedsys]$ sudo sfdisk /dev/sdg << EOF        # make one big partition
,,L,*
EOF
$ sudo umount /dev/sdg1                # defeat auto-mount
$ sudo mkfs -t vfat /dev/sdg1          # format fat32
$ sudo sync                                   # flush cache
$ usb-creator                                 # copy .iso file to USB[/FONT]

```

---

### Post by kornelix on 2008-12-18
Previous post is wrong. My apologies. 

usb-create completes writing the .iso file and says that all is OK, but the resulting USB stick fails to boot. It blinks a few times and stops with a blank screen.

---

