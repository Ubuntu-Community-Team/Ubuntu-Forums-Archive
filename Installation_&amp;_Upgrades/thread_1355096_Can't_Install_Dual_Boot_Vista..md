---
title: "Can't Install Dual Boot Vista."
date: 2009-12-14
forum: Installation &amp; Upgrades
---

### Post by newbie7 on 2009-12-14
Hello,
I have been trying to install Ubuntu on a separate drive in my system from Vista:
I have a 500gb drive with windows on and an unformatted 80gb drive in the machine too.
I try to install ubuntu and when I get to the gpart bit to show the partitions, only the windows disk shows up with no mention of the 80 gb drive?

When I use the gparted util in the booted Ubuntu CD, I can see the other drive, but I cant create on it any other type of partition on it except NTFS it rejects , ex2, ex3 with an error that the drive is in use?

Gparted lets me delete the volumes on the drive, but only allows ntfs file system, I still cant install ubuntu, whatever I do to the drive and have been through the install process about a dozen times now.

I have also been back into windows and tried deleting the partition etc, no joy.

I do not have a raid array or disk striping or anything like that going on, the disks are separate.

I have also tried uninstalling the disk in windows and removed it from the bios also and still wont show in the install process.

I hope that I'm missing something really obvious, that is not obvious to a novice like me.
Any help much appreciated, thanks in advance.

---

### Post by darkod on 2009-12-14
Even though you never had raid array, boot with the ubuntu cd, Try Ubuntu option and in terminal do:
sudo apt-get remove dmraid

Then reboot again, use Install Ubuntu option and see if you can see the drive in step 4. Also make sure if there is drop down box maybe you can change from the 500GB to the 80GB there. Let us know if the problem continues.

---

### Post by newbie7 on 2009-12-15
Thank you for your response, I have tried what you said, the operation completed ok, but still no drive showing up in the install, not sure if it makes any difference but my main frive is showing as (striped) in brackets???

---

### Post by darkod on 2009-12-15
> **newbie7 said:**
> Thank you for your response, I have tried what you said, the operation completed ok, but still no drive showing up in the install, not sure if it makes any difference but my main frive is showing as (striped) in brackets???

Striped? That's a raid setting. If you are not using raid as you said, I see no reason the drive to be shown as striped. Also make sure on the 80GB you don't already have 4 primary partitions existing. In that case because new partition can't be created, ubuntu can ignore it as destination.

---

### Post by newbie7 on 2009-12-15
> **newbie7 said:**
> Hello,
I have been trying to install Ubuntu on a separate drive in my system from Vista:
I have a 500gb drive with windows on and an unformatted 80gb drive in the machine too.
I try to install ubuntu and when I get to the gpart bit to show the partitions, only the windows disk shows up with no mention of the 80 gb drive?

When I use the gparted util in the booted Ubuntu CD, I can see the other drive, but I cant create on it any other type of partition on it except NTFS it rejects , ex2, ex3 with an error that the drive is in use?

Gparted lets me delete the volumes on the drive, but only allows ntfs file system, I still cant install ubuntu, whatever I do to the drive and have been through the install process about a dozen times now.

I have also been back into windows and tried deleting the partition etc, no joy.

I do not have a raid array or disk striping or anything like that going on, the disks are separate.

I have also tried uninstalling the disk in windows and removed it from the bios also and still wont show in the install process.

I hope that I'm missing something really obvious, that is not obvious to a novice like me.
Any help much appreciated, thanks in advance.


I have tried all combinations, the 80gb drive, empty, unformatted, no partitions, and with a partition and then again with no partitions, all possible combinations.
The main drive shows as striped, I have used your command you stated to remove the raid, this did not work as you thought it would, the drive still shows as striped.
I see no reason either that the drive shows as striped, thats why I am here trying to get help!
There are no partitions on the 80gb drive, I dont know how to make it any clearer for you, but thanks for any ideas you may have.

---

### Post by darkod on 2009-12-15
I know it's a dumb question, but are you absolutely sure there is not any raid setting enabled in BIOS? Double check. It might mark the disk as raid member even if it isn't.
I have no other ideas, sorry. This is weird. :(

---

### Post by oldfred on 2009-12-15
From the live CD run this just so we can see what partitions Ubuntu sees:
ls /dev/disk/* -l

Also is the hard drive formatted as "dynamic"? That is a windows proprietary format alternative to standard MBR which they used in a few cases.

---

### Post by PRC09 on 2009-12-15
Double check in the bios settings,in mine it was under Advanced but yours maybe different for the setting called SATA and it should give you a choice of SATA or IDE.Select IDE and it should work after that.I have had this happen on systems with mixed drive types.It only seemes to happen with 9.10  (9.04 was fine with either setting).Assuming this is 9.10 and the 500gb is SATA.

---

### Post by newbie7 on 2009-12-16
There are no RAID settings, set in the bios.
Oldfred, the disks show up in gparted and in the disk viewer thing.
In the bios it is set to IDE.
Both drives are 'basic'

When in the bios, if i disable sata, the pc wont boot, not even from the dvd drive.
When I get into Ubuntu booted from the CD, I can see both drives in the disk manager and gparted.

I can delete the partitions from the 80gb with out a problem and it becomes unallocated space.

I can also format the 80gb drive to ntfs, but it will not accept any other format from the list, ex2,ex3 etc,etc.  Will only format as NTFS, hope thats clear.

I am not messing with my windows drive in any way shape or form.

In the disk manager I can look at the drive, tels me what it is and information about it, it will also in there not let me do anything except format the drive as NTFS, if I try to do anything else to the drive, it says it is busy, and in use.

I have even tried removing/uninstalling the drive from the bios, so it is not there anymore and I go back into Ubuntu and it still acts the same as I have described now many times.

I would like to use Ubuntu but this is getting to be way too much hastle for me, I need some effective help if at all possible.

---

### Post by presence1960 on 2009-12-16
Also there is a bug in 9.10 that mounts raid arrays that you have deleted.  To fix it first turn off raid in your BIOS.  Then load up the 9.10 Live CD and open gparted.  If you get a drive with a funny name like nvidia_ahahdhjdfsjkf then you have mounted a raid drive that you don't want.

To get rid of it, Open a terminal and type ```
dmraid -E -r /dev/name_of_your_disk
```  
Note you want the disk name not the partition name.  You can see your disk names in gparted i.e. sda, sdb, sdc, etc.

Once you have erased the raid meta data you should see the funny named disk disappear after restarting gparted.

Also for formatting and setting up partitions try gparted Live CD/USB, get it [here]("http://gparted.sourceforge.net/livecd.php").

---

### Post by newbie7 on 2009-12-16
Thank you very much, I will try that and get back to you.

---

### Post by newbie7 on 2009-12-16
Hello,
I have tried as you stated and that didn't work either.
In gparted, the name was there as you suggested as:
dev/mapper/pdc_fcgdcdhbi

When I ran the command in the terminal it said no raid with than name found?
I double checked my typing still no joy?

I tried the commands with the mapper bit and without it neither command worked.

---

### Post by darkod on 2009-12-16
In this command Presence quoted you used /dev/mapper/etc or /dev/sdb (if it's called sdb)? I think you need to use /dev/sdb even though the name shows as /dev/mapper/etc.
Try it again like that too.

---

### Post by newbie7 on 2009-12-16
Hello, I added in the sda, still nothing

ubuntu@ubuntu:~$ sudo dmraid -E -r /dev/sda/mapper/pdc_fcgdcdhbi
no raid disks and with names: "/dev/sda/mapper/pdc_fcgdcdhbi"
ubuntu@ubuntu:~$ sudo dmraid -E -r /dev/sda/pdc_fcgdcdhbi
no raid disks and with names: "/dev/sda/pdc_fcgdcdhbi"
ubuntu@ubuntu:~$

no raid disks and with names: "/dev/sda/mapper/pdc_fcgdcdhbi"

---

### Post by darkod on 2009-12-16
> **newbie7 said:**
> Hello, I added in the sda, still nothing

ubuntu@ubuntu:~$ sudo dmraid -E -r /dev/sda/mapper/pdc_fcgdcdhbi
no raid disks and with names: "/dev/sda/mapper/pdc_fcgdcdhbi"
ubuntu@ubuntu:~$ sudo dmraid -E -r /dev/sda/pdc_fcgdcdhbi
no raid disks and with names: "/dev/sda/pdc_fcgdcdhbi"
ubuntu@ubuntu:~$

no raid disks and with names: "/dev/sda/mapper/pdc_fcgdcdhbi"

No, not /dev/sda/mapper... but only /dev/sda without the mapper/blabla.
And why /dev/sda, isn't it /dev/sdb? Isn't your 500GB disk /dev/sda? You are trying to remove the raid data from the 80GB correct?

---

### Post by newbie7 on 2009-12-16
yes I am, thanks hang on ill try that

---

### Post by newbie7 on 2009-12-16
No that didnt work either, the command didnt give an error this time, when I tried the install got to step 4, and still not showing the drive, except this time it says there are no operating systems on this computer:confused:

getting very fed up with all this, thought Ubuntu was easy and bug free, unlike windows:lolflag:

---

### Post by darkod on 2009-12-16
And opening Gparted like previously doesn't show the /dev/mapper/blabla device now?

---

### Post by newbie7 on 2009-12-16
that is correct

---

### Post by darkod on 2009-12-16
> **newbie7 said:**
> that is correct

Well, what can I say. Sorry to tell you but your computer has ghosts. :)
There is either some basic piece of info we've missed, or all of this is very, very weird...

---

### Post by newbie7 on 2009-12-16
Here are some screenshots in case missed anything

---

### Post by newbie7 on 2009-12-16
Here is a screenshot of step4, still the 80gb drive isnt showing but I can now format it with other formats other than ntfs, have formated it as EX3, it also says in gparted that 1.37gb is used??

---

### Post by newbie7 on 2009-12-16
screengrab

---

### Post by newbie7 on 2009-12-16
gparted

---

### Post by darkod on 2009-12-16
> **newbie7 said:**
> screengrab

If you select the option Erase and use entire disk, will it allow you to use sdb in the dropdown box? That's what you want, right? 9.10 on whole of sdb.

---

### Post by newbie7 on 2009-12-16
No no, I dont want to erase the 500gb disk, that has my windows on it but is being falsely reported as having no OS on it.
I do want ubuntu on the second drive, the 80gb one, but as you can see from the screenshot its not there, in the screenshot it says sda1 not sdb.
Sorry, ive got it, feel a bit stupid, thank you

---

### Post by darkod on 2009-12-16
> **newbie7 said:**
> No no, I dont want to erase the 500gb disk, that has my windows on it but is being falsely reported as having no OS on it.
I do want ubuntu on the second drive, the 80gb one, but as you can see from the screenshot its not there, in the screenshot it says sda1 not sdb.

Yes, but you do not have the Erase use whole disk option selected. If you select it, the drop down box under it will become active and in that box you can choose the disk /dev/sdb, not /dev/sda currently showing in the inactive box.
Don't worry, you can always click the Quit button. Select the Erase use whole disk option and see if it will allow to select /dev/sdb under it.

PS. No need to feel stupid. :) Give it a go.

---

### Post by newbie7 on 2009-12-16
Thank you very much for your help and contributions especially darkod for hangin in there with me, here is a much happier screenshot:guitar:

Merry xmas all, once again very grateful

---

### Post by darkod on 2009-12-16
Hope it works out well. Not seeing the vista on /dev/sda is getting me worried, even if ubuntu installs ok on /dev/sdb, if it can't see vista it will not add it to grub menu.
But lets see how the install goes first, and what will happen.

---

### Post by presence1960 on 2009-12-16
> **newbie7 said:**
> screengrab

That screenshot in that post says no operating system is because in the middle of that screen in the drop down box you have selected sdb. If you select sda it will show what is on that device. Note the top graph-underneath it says sdb.

here is a [link]("http://ubuntuforums.org/showthread.php?t=1339631") to a thread I started about this very subject. Actually where it says this computer has no operating system it should really say this hard disk or this device has no operating system because it is only showing one hard disk in the graph (in your case sdb) To have the top graph show what is on other disks you must select other disks from the drop down box by clicking erase and use entire disk, choose sda from drop down box then make your choice again on how to install. When you choose sda from the drop down box the graph at top will change to reflect your sda disk.

Don't believe me? Boot the Live CD and try it. You can cancel after that point without installing again or changing anything on your disks.

---

### Post by darkod on 2009-12-16
> **presence1960 said:**
> That screenshot in that post says no operating system is because in the middle of that screen in the drop down box you have selected sdb. If you select sda it will show what is on that device. Note the top graph-underneath it says sdb.

here is a [link]("http://ubuntuforums.org/showthread.php?t=1339631") to a thread I started about this very subject. Actually where it says this computer has no operating system it should really say this hard disk or this device has no operating system because it is only showing one hard disk in the graph (in your case sdb)

There is screenshot of sda in post #23 and again it says no OS. That's why I said it's getting me worried because I don't expect it to "see" vista even if it installs fine. Hope I'm wrong, otherwise he'll have no vista entry in grub menu.

---

### Post by presence1960 on 2009-12-16
> **darkod said:**
> There is screenshot of sda in post #23 and again it says no OS. That's why I said it's getting me worried because I don't expect it to "see" vista even if it installs fine. Hope I'm wrong, otherwise he'll have no vista entry in grub menu.

Thanks Darko didn't see that one! Good catch, thanks. But nevertheless there seems to be some problems with the installer detecting OSs that need to be addressed. It will only be addressed if the ones who experience the problem report it as a bug. Unfortunately I have not experienced it. Maybe this OP can take the initiative and do so. As you are well aware this is not the first time we have seen this problem. It will continue to go unresolved if no one reports it as a bug because if a problem is not reported and made known then the devs have no idea it even exists.

---

### Post by newbie7 on 2009-12-16
Yes, The OP will take up the batton gladly if he can get his machine to boot ok following the install above, sorry guys, 
just got it all installed and got to the point where it said loading Grub, then got this error, no windows or ubuntu, had to boot from CD to be on here, thanks for any ideas, maybe I should check the threads as well, the error message below:

Error - biodisk write error, failed to boot default entries, press any key to continue.

I will do a thread search, just now.

---

### Post by presence1960 on 2009-12-16
> **newbie7 said:**
> Yes, The OP will take up the batton gladly if he can get his machine to boot ok following the install above, sorry guys, 
just got it all installed and got to the point where it said loading Grub, then got this error, no windows or ubuntu, had to boot from CD to be on here, thanks for any ideas, maybe I should check the threads as well, the error message below:

Error - biodisk write error, failed to boot default entries, press any key to continue.

I will do a thread search, just now.

I feel for you. It really isn't your fault. This has been going on here and there for a while. But I don't think any one afffected has bothered to report it as a bug. Once you get a chance if you can do so it would be greatly appreciated.

---

### Post by newbie7 on 2009-12-16
Any ideas why I cant get my machine to boot up, from a hard drive now???
My machine aint workin? cant boot into windows or ubuntu except from the boot cd???

---

### Post by darkod on 2009-12-16
> **newbie7 said:**
> Yes, The OP will take up the batton gladly if he can get his machine to boot ok following the install above, sorry guys, 
just got it all installed and got to the point where it said loading Grub, then got this error, no windows or ubuntu, had to boot from CD to be on here, thanks for any ideas, maybe I should check the threads as well, the error message below:

Error - biodisk write error, failed to boot default entries, press any key to continue.

I will do a thread search, just now.

Sorry, we should have probably mentioned to check before clicking Install, in the Advanced button where will ubuntu install grub2. It should have been /dev/sdb and not touch your vista drive.
In case the vista MBR is overwritten by grub2, there are instructions how to restore it here:
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

If you don't have vista dvd you can get repair image here (small, fits on cd too):
[http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/](http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/)

---

### Post by newbie7 on 2009-12-16
I followed the instructions to restore the grub bootloader, at the link posted, but still dosn't boot properly, I have posted screenshots, of what i did, substituting where it says sda5, I put sdb1, it gave a message about checking, I said yes and re-booted but still the same error, no choice of os.
sorry if i'm being thick or something
I will try and restore vista bootloader

---

### Post by darkod on 2009-12-16
Just to confirm, you used /dev/sdb1 in the mount command, but /dev/sdb in grub-install command right? Because it needs to install on the MBR of sdb, that's /dev/sdb.
Also, don't forget that your 500GB drive might be first in boot options in BIOS. You reinstalled grub2 on the MBR of the 80GB disk but until you tell BIOS to try to boot from it first, it might still call "wrong" grub2 from /dev/sda.

PS. Slight modification of the command to reinstall grub2 can be used. Yours should be like:
sudo mount /dev/sdb1 /mnt
sudo grub-install --root-directory=/mnt/ /dev/sdb

And you would need to set the 80GB as first boot choice.

---

### Post by presence1960 on 2009-12-16
I have gone back and read from the beginning and I have to admit I did not do what I usually do with boot problems- I did not ask for the boot info script to be run. We had you make a whole bunch of modifications to your setup without actually seeing what it looks like or what the boot process looks like. You are probably thinking does that really matter? Yes it does. In my experience here a lot of times what the OPs say they have on their machine and what the boot info script reveals they actually have are not the same. This is usually not intentional on the OP's part but nevertheless it happens. 

Now that you have made all sorts of changes it is even more important that we see exactly what you have on your rig. Do this please and I apologize for not asking you to run the script earlier.

Let's get a better look at your setup & boot process. Boot the Ubuntu Live CD/USB. Choose "try ubuntu without any changes", when the desktop loads come back here and use the link in my signature to download the Boot Info Script to the desktop. Once on desktop open a terminal (Applications > Accessories > Terminal) and run this command ```
sudo bash ~/Desktop/boot_info_script*.sh
``` This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

---

### Post by newbie7 on 2009-12-17
Ok, thanks for the feedback, here is where I am right now, I repaired vista, and booted into it ok.. all well with windows.

I booted ubuntu CD and re-installed ubuntu, erasing the 80gb disk, and making sure, in the 'advanced' tab that the grub was put on to the sdb drive, the non vista drive, 
I now boot up and it goes straight into windows, no choice of OS, all fine.

What I need to know is how to make my system give me the choice of Ubuntu or Vista?
I understand how to change the boot device priority in my bios to have the 80gb drive (ubuntu)1st and the 500gb drive(vista) second. I can grasp that ok, 

What I dont understand is how to change anything if at all, in the ubuntu side (grub) to give me the choice, in very simple and plain english please, 
I am not to hot at all this and surprised my machine still works, and am very grateful for all your help, I feel I am very close to having the machine how I want, but dont want to mess up anything again, thank you.

ps I havnt yet booted off the hard drive install, will have a go in the am, have to sleep now

---

### Post by presence1960 on 2009-12-17
> **newbie7 said:**
> Ok, thanks for the feedback, here is where I am right now, I repaired vista, and booted into it ok.. all well with windows.

I booted ubuntu CD and re-installed ubuntu, erasing the 80gb disk, and making sure, in the 'advanced' tab that the grub was put on to the sdb drive, the non vista drive, 
I now boot up and it goes straight into windows, no choice of OS, all fine.

What I need to know is how to make my system give me the choice of Ubuntu or Vista?
I understand how to change the boot device priority in my bios to have the 80gb drive (ubuntu)1st and the 500gb drive(vista) second. I can grasp that ok, 

What I dont understand is how to change anything if at all, in the ubuntu side (grub) to give me the choice, in very simple and plain english please, 
I am not to hot at all this and surprised my machine still works, and am very grateful for all your help, I feel I am very close to having the machine how I want, but dont want to mess up anything again, thank you.

ps I havnt yet booted off the hard drive install, will have a go in the am, have to sleep now

Run the script or since I can't see EXACTLY your setup & boot process I won't attempt to help.

---

### Post by darkod on 2009-12-18
> **newbie7 said:**
> Ok, thanks for the feedback, here is where I am right now, I repaired vista, and booted into it ok.. all well with windows.

I booted ubuntu CD and re-installed ubuntu, erasing the 80gb disk, and making sure, in the 'advanced' tab that the grub was put on to the sdb drive, the non vista drive, 
I now boot up and it goes straight into windows, no choice of OS, all fine.

What I need to know is how to make my system give me the choice of Ubuntu or Vista?
I understand how to change the boot device priority in my bios to have the 80gb drive (ubuntu)1st and the 500gb drive(vista) second. I can grasp that ok, 

What I dont understand is how to change anything if at all, in the ubuntu side (grub) to give me the choice, in very simple and plain english please, 
I am not to hot at all this and surprised my machine still works, and am very grateful for all your help, I feel I am very close to having the machine how I want, but dont want to mess up anything again, thank you.

ps I havnt yet booted off the hard drive install, will have a go in the am, have to sleep now

Run the script like Presence said. It's much easier to help. Like this we are sort of guessing ourselves.
Also, you say you haven't tried booting off the 80GB after the latest install and still you are asking how grub to give you options for ubuntu and vista. It should already be there, the choice. Try booting off the 80GB first and if it doesn't work, report it here.

---

### Post by newbie7 on 2009-12-18
Hi, when booting from the 80gb drive, we are back to this error:

Error - biodisk write error, failed to boot default entries, press any key to continue.

The text output you wanted:

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => Grub 1.97 is installed in the MBR of /dev/sdb and looks on the same drive 
    in partition #1 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe /grldr

sdb1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xc2d4c2d4

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048   976,771,071   976,769,024   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 82.0 GB, 81964302336 bytes
255 heads, 63 sectors/track, 9964 cylinders, total 160086528 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x000f0341

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63   153,468,944   153,468,882  83 Linux
/dev/sdb2         153,468,945   160,071,659     6,602,715   5 Extended
/dev/sdb5         153,469,008   160,071,659     6,602,652  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

/dev/loop0: TYPE="squashfs" 
/dev/sda1: UUID="38645E9A645E5AA8" TYPE="ntfs" 
/dev/sdb1: UUID="f7e026e2-7297-4de9-92d1-c07bb42354bf" TYPE="ext4" 
/dev/sdb5: UUID="bd40526c-8369-4e84-a82e-f073213311ce" TYPE="swap" 

=============================== "mount" output: ===============================

aufs on / type aufs (rw)
none on /proc type proc (rw,noexec,nosuid,nodev)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
udev on /dev type tmpfs (rw,mode=0755)
/dev/sr0 on /cdrom type iso9660 (rw)
/dev/loop0 on /rofs type squashfs (rw)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
none on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ubuntu)


=========================== sdb1/boot/grub/grub.cfg: ===========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s /boot/grub/grubenv ]; then
  have_grubenv=true
  load_env
fi
set default="0"
if [ ${prev_saved_entry} ]; then
  saved_entry=${prev_saved_entry}
  save_env saved_entry
  prev_saved_entry=
  save_env prev_saved_entry
fi
insmod ext2
set root=(hd1,1)
search --no-floppy --fs-uuid --set f7e026e2-7297-4de9-92d1-c07bb42354bf
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  insmod gfxterm
  insmod vbe
  if terminal_output gfxterm ; then true ; else
    # For backward compatibility with versions of terminal.mod that don't
    # understand terminal_output
    terminal gfxterm
  fi
fi
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/white
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry "Ubuntu, Linux 2.6.31-15-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd1,1)
    search --no-floppy --fs-uuid --set f7e026e2-7297-4de9-92d1-c07bb42354bf
    linux    /boot/vmlinuz-2.6.31-15-generic root=UUID=f7e026e2-7297-4de9-92d1-c07bb42354bf ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-15-generic
}
menuentry "Ubuntu, Linux 2.6.31-15-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd1,1)
    search --no-floppy --fs-uuid --set f7e026e2-7297-4de9-92d1-c07bb42354bf
    linux    /boot/vmlinuz-2.6.31-15-generic root=UUID=f7e026e2-7297-4de9-92d1-c07bb42354bf ro single 
    initrd    /boot/initrd.img-2.6.31-15-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd1,1)
    search --no-floppy --fs-uuid --set f7e026e2-7297-4de9-92d1-c07bb42354bf
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=f7e026e2-7297-4de9-92d1-c07bb42354bf ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd1,1)
    search --no-floppy --fs-uuid --set f7e026e2-7297-4de9-92d1-c07bb42354bf
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=f7e026e2-7297-4de9-92d1-c07bb42354bf ro single 
    initrd    /boot/initrd.img-2.6.31-14-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
if [ ${timeout} != -1 ]; then
  if keystatus; then
    if keystatus --shift; then
      set timeout=-1
    else
      set timeout=0
    fi
  else
    if sleep --interruptible 3 ; then
      set timeout=0
    fi
  fi
fi
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sdb1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sdb1 during installation
UUID=f7e026e2-7297-4de9-92d1-c07bb42354bf /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb5 during installation
UUID=bd40526c-8369-4e84-a82e-f073213311ce none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sdb1: Location of files loaded by Grub: ===================


    .0GB: boot/grub/grub.cfg
    .0GB: boot/initrd.img-2.6.31-14-generic
    .0GB: boot/initrd.img-2.6.31-15-generic
    .0GB: boot/vmlinuz-2.6.31-14-generic
    .0GB: boot/vmlinuz-2.6.31-15-generic
    .0GB: initrd.img
    .0GB: initrd.img.old
    .0GB: vmlinuz

---

### Post by oldfred on 2009-12-18
I do not see anything obvious from you boot info script. You did have grub4dos boot loader in your windows /grldr but if Vista boots ok its not a problem.

If you boot from the liveCD can you select start system on hard drive when sdb is set as the first drive. It should not be any different but is something to try. 

Your grub has not yet found the windows and grub2 is usually very good about finding other operating systems. But we need to get you booting first. Usually once you can boot an update-grub command will find windows if it did not find it the first time.

---

### Post by newbie7 on 2009-12-18
Thank you,

When I change the boot device priority in the bios, (80gb ubuntu drive first) I get the error as stated in the last post at the top, the PC is also not able to boot from the CD drive either, so I cant start the live CD in order to make the choice of 'boot from first hard drive'

If I change the bood device priority back to my windows drive as first, it only allows me that windows drive, a cd rom, and a floppy drive, It will not allow me to put the second 80gb drive in the priority list.

only by disabling the 500gb vista drive in boot settings am I able to get the 80gb drive in to the priority list at all.

As you can probably figure out I am in a catch 22 situation.

I think if I did what you said and go for a sucessful boot from the live CD with my windows vista disk as the first drive, I surely wouldnt want to boot from that as the first hard drive.

What I am trying to say in short is that the bios wont let me have the 2 hard drives in the boot priority list.

---

### Post by oldfred on 2009-12-18
Maybe I missed it but are these IDE (pata) drives or Sata drives or mixed. If pata you probably have to set boot priority by changing jumpers on the hard drive or the order on the ide cable, if the cable has 3 different color connectors.  The middle connect is slave and the end is master. The Bios will not let you have two masters.

---

### Post by darkod on 2009-12-18
> **newbie7 said:**
> Thank you,

When I change the boot device priority in the bios, (80gb ubuntu drive first) I get the error as stated in the last post at the top, the PC is also not able to boot from the CD drive either, so I cant start the live CD in order to make the choice of 'boot from first hard drive'

If I change the bood device priority back to my windows drive as first, it only allows me that windows drive, a cd rom, and a floppy drive, It will not allow me to put the second 80gb drive in the priority list.

only by disabling the 500gb vista drive in boot settings am I able to get the 80gb drive in to the priority list at all.

As you can probably figure out I am in a catch 22 situation.

I think if I did what you said and go for a sucessful boot from the live CD with my windows vista disk as the first drive, I surely wouldnt want to boot from that as the first hard drive.

What I am trying to say in short is that the bios wont let me have the 2 hard drives in the boot priority list.

Look around in BIOS options. One type of setting is just the devices, for example, CD, HDD, USB. And there can be another setting which lists all your hard drives and there you can move them up/down in the order. You will never see 2 or 3 hard drives together in the list with CD, USB, etc. It will only say HDD probably, but on most newer BIOSes there is separate setting just for the hard drives order.

---

### Post by newbie7 on 2009-12-19
Ok, I have got the bios to let me boot from the live CD, with the 80gb drive second, floppy third.

When I choose boot from first hard drive it reports the same error:
Error - biodisk write error, failed to boot default entries, press any key to continue.

I am on here from the live CD.

They are both sata drives, connected with a red cable

---

### Post by newbie7 on 2009-12-19
Does anybody know what this error means:
Error - biodisk write error, failed to boot default entries, press any key to continue.

---

### Post by darkod on 2009-12-19
> **newbie7 said:**
> Does anybody know what this error means:
Error - biodisk write error, failed to boot default entries, press any key to continue.

No, I've never heard about it. Is it possible that your 80GB drive has broken down?
As far as I understand the computer is working fine without it.

PS. You can also try TestDisk on it.
[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

---

### Post by newbie7 on 2009-12-19
The 80gb drive was fine untill I tried installing Ubuntu on it

---

### Post by darkod on 2009-12-19
When booted from the cd in terminal run the filesystem check:
sudo fsck /dev/sdb1

Also run the TestDisk from the link I provided in last post. I don't have any other ideas how to check the disk about that error.

---

### Post by chillyomi on 2009-12-19
Try formatting your disk

---

### Post by oldfred on 2009-12-19
It looks like someone else had a similar problem but he only found a temporary one time fix.

[http://ubuntuforums.org/archive/index.php/t-1308154.html](http://ubuntuforums.org/archive/index.php/t-1308154.html)

---

### Post by newbie7 on 2009-12-20
Wiped the disk, completely clean WIPED, not formatted.

Re-installed, got the menu choice this time of vista or ubuntu etc, 
was very excited at this point, then chose Ubuntu to boot from my new install on the hard disk, gues what:

ERROR BIOSDISK WRITE ERROR, FAILED TO BOOT DEFAULT ENTRIES, PRESS ANY KEY TO CONTINUE.

I can get in to Vista from the 'grub' menu though, WOW, aint Ubuntu great software

:lolflag::lolflag::lolflag::lolflag::lolflag::lolflag:

---

### Post by newbie7 on 2010-01-17
Hello again, I'm back after doing some research, I found out that this may be a grub problem as I have found that if I delete:

grubenv from boot/grub

I can then boot into Ubuntu ok, the problem is that this file is created every time
you boot up so once you have been in once you have to load a live disk and delete the file again.

Is this a known problem and is there a permanent fix or workaround for this that anybody knows of, thanks

I tried this:
Solved it temporarily using following commands in recovery shell
# cd /boot/grub
# rm grubenv
# grub-editenv grubenv create
# grub-editenv grubenv set default=0
# grub-editenv grubenv list
default=0

All that did was add default=0 into the file and didn't boot up/fix the problem

---

### Post by meierfra. on 2010-01-19
Try this:

Open a terminal and then open the file "10_linux" via

```
gksudo gedit /etc/grub.d/10_linux
```

Look for

```
menuentry "$1" {
        recordfail=1
        if  [ -n \${have_grubenv} ]; then save_env recordfail; fi
EOF

```

(should be around line 60) and  add a "#" in front of "if"

```
menuentry "$1" {
        recordfail=1
      [COLOR="Red"]# [/COLOR]if [ -n \${have_grubenv} ]; then save_env recordfail; fi
EOF

```

Save the file. Then back in the terminal:

```
sudo update-grub2
```

---

