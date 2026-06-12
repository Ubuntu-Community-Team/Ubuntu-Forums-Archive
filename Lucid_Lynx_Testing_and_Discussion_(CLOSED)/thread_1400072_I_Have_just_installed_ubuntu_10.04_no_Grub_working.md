---
title: "I Have just installed ubuntu 10.04 no Grub working"
date: 2010-02-06
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by aviramof on 2010-02-06
i have just installed it and i get grub 1.5 error 15 how can i fix the grub now no menu.lst no [I]grub.cfg nothing how can i fix the problem via live cd?

thanks in advance.
[/I]

---

### Post by phenest on 2010-02-06
Check [here]("https://wiki.ubuntu.com/Grub2") under section 7.

---

### Post by aviramof on 2010-02-06
Thank you for the help but i think i'm about to gave up on ubuntu at all till version 10 will go out i have worked here for hours trying to install this version and no luck first
i installed it via the option install ubuntu in the cd and got error 15 so i said why not 
reinstall from live cd including updating the installer and etc so i again formated and 
tried to install installer got stuck in 85%.
 
so i tried again formated again to make sure no problems would happen from perviouse installation again got stuck in 80% even that i left it working for two hours nothing again i restarted the computer went into install ubuntu option formated again but here i had another problem my computer is
connected via dvi hdmi to my tv the live cd must have noticed that so he extended the
screen and all the options went there i said ok switch to the hdmi channel and so nothing but pink ha ha ha the hall screen was pink barely could see the options there.
 
but i'v managed to run the installer any way and install but i already knew i would get error 15 from before so i shut down the tv after it had finished installing and the next time i ran the live cd it did not extend the screen and by the way loading the live cd here takes a hugh amount of time something like five minutes or something like this. 
 
after entering live cd again i tried all sort of methods describe here 
[https://wiki.ubuntu.com/Grub2](https://wiki.ubuntu.com/Grub2) and here [https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD](https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD) to install grub 2 and etc but still no luck still grub 1.5.
 
eventually i tried the last solution i could think of i'v removed grub completly enterd windows 7 cd botrec.exe /fix boot botrec.exe /fixmbr grub vanished windows 7 up so far so good restaretd enterd live cd again mounted the partition via some of the commands from here [https://wiki.ubuntu.com/Grub2#Recover](https://wiki.ubuntu.com/Grub2#Recover) Grub 2 via LiveCD all 
the way to  chroot and extually now that i think about it might be the reason it didn't
worked  maybe you should add to the guide how to mount from live cd any way tried to install grub again restatred the system nothing happen meaing windows 7 started alone no grub no nothing so just consider all of this problems in your final version.
 
and now i'm going to do what i just thought of reinstall grub 2 via noraml mount option and see how it works wish me luck.:):):)

---

### Post by aviramof on 2010-02-06
one more problem i have just noticed you installed firefox 3.5.7 but all the addons you 
installed are for 3.5.4 meaing not compatible and there for doesn't work and also there 
is no hebrew in this list how could you forget hebrew???:):):)

and one more thing if i press restart in live cd nothing happen it said wait 60 seconds i said no 
restart now and nothing happen.

---

### Post by aviramof on 2010-02-07
you know what forget about it if even removing grub and then reinstall the system again doesn't create grub which is what i just did then nothing will.
 
however version 10 does have potential so i might try her again in a few months unless i'll install other linux version like fedora or suse or what ever it called.
 
thanks for all your help.

---

### Post by ranch hand on 2010-02-07
Did you read the the warning in bold print at the top of the index page for this forum?  Did you read the warning on the first page of the installer on the LiveCD?  If so believe them and expect breakage.

That is what we are here for.  To have it not work so that it can be fixed.

If you want to take your doll and go home, fine.  You do not need to be cranky about it.  You were warned.

It sounds as though you are installing this on a production machine.  The warnings recommend against this too so all I can say is sorry about your luck with Win JerryLewis Pro.

You are asking folks that are here to help and all I can see is complaints.

Where are the specs for your box?  Did you run md5sum check on the ISO?  Did you test the integrity of the CD?  Do you believe folks are mind readers?

---

### Post by VMC on 2010-02-07
> **aviramof said:**
> i have just installed it and i get grub 1.5 error 15 how can i fix the grub now no menu.lst no [I]grub.cfg nothing how can i fix the problem via live cd?

thanks in advance.
[/I]

The best recommendation I can give you , is to run **boot-info-script**(see my signature for location). 
That way we can see all the boot info in one place. Maybe we can advise you on a solution.

---

### Post by aviramof on 2010-02-07
RANCH HAND first of all i downloaded the file from here so i guess it should be ok
[http://cdimage.ubuntu.com/dvd/current/](http://cdimage.ubuntu.com/dvd/current/) 
 
my spec is pentium d 820 2GB 800mhz the HD i'm trying to install it on him is 80GB IDE but that should not be a problem because 8.10 worked very well there and what do you mean a production machine it a personal computer and i am fully aware that
it's alpah or beta or what ever but i think that the minimum requiermet for any software is to be able to install it and if it's not possible to do that then you don't need to let anyone download it.
 
and by the way this version doesn't even recognize i have windows 7 not in the partition windows but amazingly in the import window it does.
 
VMC how exceclly can i use this script can i run it via live cd?and what is the command line by the way if i need one.

---

### Post by ranch hand on 2010-02-07
> **aviramof said:**
> RANCH HAND first of all i downloaded the file from here so i guess it should be ok
[http://cdimage.ubuntu.com/dvd/current/](http://cdimage.ubuntu.com/dvd/current/) 
 
my spec is pentium d 820 2GB 800mhz the HD i'm trying to install it on him is 80GB IDE but that should not be a problem because 8.10 worked very well there and what do you mean a production machine it a personal computer and i am fully aware that
it's alpah or beta or what ever but i think that the minimum requiermet for any software is to be able to install it and if it's not possible to do that then you don't need to let anyone download it.
 
and by the way this version doesn't even recognize i have windows 7 not in the partition windows but amazingly in the import window it does.
 
VMC how exceclly can i use this script can i run it via live cd?and what is the command line by the way if i need one.
If you have ever wondered why 8.10, for instance, works it is because for 6 months folks downloaded it and attempted t oget it to run on their hardware.

Building an OS that works is not a fast or simple thing.  Building a Live CD is another thing that is not easy.  There have been problems.

This is not software, this is an OS.  It is not generally available because it is not finished.  If you want some thing that works try the current STABLE version - 9.10 or even 9.04 (9.04 is quite a change from 8.10).  This OS (10.04) is not, at this point supposed to work completely as it is not close to finished.  Check the sticky on the release schedule.

What is your video card or controller?  Some of the changes being put into 10.04 are big changes for a number of cards.  These seem to be the big problem right now.

Run the boot script from the LiveCD and get on the forums from there and post the results text that should show up on the desktop.  This will give all the information on grub and other boot loaders on your box.  That with the information you can provide on your box will, hopefully, point to a solution.

---

### Post by aviramof on 2010-02-07
i used the script given in a previous reply i'm using 8.10 live cd right now this would give some informatoin about my computer:
```
============================= Boot Info Summary: ==============================
 
 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for /boot/grub.
 => Windows is installed in the MBR of /dev/sdb
sda1: _________________________________________________________________________
 
    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   
 
sda2: _________________________________________________________________________
 
    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   
 
sdb1: _________________________________________________________________________
 
    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /grub/grub.cfg /bootmgr /Boot/BCD 
                       /Windows/System32/winload.exe /grldr /grub/core.img
 
sdb2: _________________________________________________________________________
 
    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   
 
sdb3: _________________________________________________________________________
 
    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   
 
=========================== Drive/Partition Info: =============================
 
Drive: sda ___________________ _____________________________________________________
 
Disk /dev/sda: 82.3 GB, 82348277760 bytes
255 heads, 63 sectors/track, 10011 cylinders, total 160836480 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x90d490d4
 
Partition  Boot         Start           End          Size  Id System
 
/dev/sda1               2,048    80,416,767    80,414,720   7 HPFS/NTFS
/dev/sda2          80,416,768   160,831,487    80,414,720   7 HPFS/NTFS
 
 
Drive: sdb ___________________ _____________________________________________________
 
Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x26ff26fe
 
Partition  Boot         Start           End          Size  Id System
 
/dev/sdb1    *             63    78,156,224    78,156,162   7 HPFS/NTFS
/dev/sdb2          78,157,824   162,043,903    83,886,080   7 HPFS/NTFS
/dev/sdb3         162,043,904   312,577,499   150,533,596   7 HPFS/NTFS
 
 
blkid -c /dev/null: ____________________________________________________________
 
Device           UUID                                   TYPE       LABEL                         
 
/dev/loop0                                              squashfs                                 
/dev/sda1        AE60A1B660A18625                       ntfs       Log1 sda1 sda2 sdb1 sdb2 sdb3 BLKID Trash
/dev/sda1        AE60A1B660A18625                       ntfs       ???? Trash                    
/dev/sda2        BA38BB8538BB3F67                       ntfs       Log1 sda1 sda2 sdb1 sdb2 sdb3 BLKID Trash
/dev/sda2        BA38BB8538BB3F67                       ntfs       sda1 BLKID Trash              
/dev/sdb1        C44451F64451EC24                       ntfs       Windows 7                     
/dev/sdb2        58544AAE544A8F26                       ntfs       Log1 sda1 sda2 sdb1 BLKID Trash
/dev/sdb2        58544AAE544A8F26                       ntfs       Log1 sda1 sda2 sdb1 sdb2 sdb3 BLKID Trash
/dev/sdb3        EA9635979635656B                       ntfs       Log1 sda1 sda2 sdb1 sdb2 BLKID Trash
/dev/sdb3        EA9635979635656B                       ntfs       Log1 sda1 sda2 sdb1 sdb2 sdb3 BLKID Trash
 
============================ "mount | grep ^/dev  output: ===========================
 
Device           Mount_Point              Type       Options
 
rootfs           /                        rootfs     (rw)
/dev/scd0        /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdb1        /media/Windows 7         fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096)
 
 
============================= sdb1/grub/grub.cfg: =============================
 
#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#
 
### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  load_env
fi
set default="1"
if [ ${prev_saved_entry} ]; then
  set saved_entry=${prev_saved_entry}
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi
 
function savedefault {
  if [ -z ${boot_once} ]; then
    saved_entry=${chosen}
    save_env saved_entry
  fi
}
 
function recordfail {
  set recordfail=1
  if [ -n ${have_grubenv} ]; then if [ -z ${boot_once} ]; then save_env recordfail; fi; fi
}
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
### END /etc/grub.d/10_linux ###
 
### BEGIN /etc/grub.d/20_memtest86+ ###
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
 
=================== sdb1: Location of files loaded by Grub: ===================
 
 
   2.4GB: grub/core.img
   6.7GB: grub/grub.cfg
```and here from 10.04 livecd
```
============================= Boot Info Summary: ==============================
 
 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for /boot/grub.
 => Windows is installed in the MBR of /dev/sdb
sda1: _________________________________________________________________________
 
    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   
 
sda2: _________________________________________________________________________
 
    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   
 
sdb1: _________________________________________________________________________
 
    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /grub/grub.cfg /bootmgr /Boot/BCD 
                       /Windows/System32/winload.exe /grldr /grub/core.img
 
sdb2: _________________________________________________________________________
 
    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   
 
sdb3: _________________________________________________________________________
 
    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   
 
=========================== Drive/Partition Info: =============================
 
Drive: sda ___________________ _____________________________________________________
 
Disk /dev/sda: 82.3 GB, 82348277760 bytes
255 heads, 63 sectors/track, 10011 cylinders, total 160836480 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x90d490d4
 
Partition  Boot         Start           End          Size  Id System
 
/dev/sda1               2,048    80,416,767    80,414,720   7 HPFS/NTFS
/dev/sda2          80,416,768   160,831,487    80,414,720   7 HPFS/NTFS
 
 
Drive: sdb ___________________ _____________________________________________________
 
Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x26ff26fe
 
Partition  Boot         Start           End          Size  Id System
 
/dev/sdb1    *             63    78,156,224    78,156,162   7 HPFS/NTFS
/dev/sdb2          78,157,824   162,043,903    83,886,080   7 HPFS/NTFS
/dev/sdb3         162,043,904   312,577,499   150,533,596   7 HPFS/NTFS
 
 
blkid -c /dev/null: ____________________________________________________________
 
Device           UUID                                   TYPE       LABEL                         
 
/dev/loop0                                              squashfs                                 
/dev/sda1        AE60A1B660A18625                       ntfs       Log1 sda1 sda2 sdb1 sdb2 sdb3 BLKID Trash
/dev/sda1        AE60A1B660A18625                       ntfs       ???? Trash                    
/dev/sda2        BA38BB8538BB3F67                       ntfs       Log1 sda1 sda2 sdb1 sdb2 sdb3 BLKID Trash
/dev/sda2        BA38BB8538BB3F67                       ntfs       sda1 BLKID Trash              
/dev/sdb1        C44451F64451EC24                       ntfs       Windows 7                     
/dev/sdb2        58544AAE544A8F26                       ntfs       Log1 sda1 sda2 sdb1 BLKID Trash
/dev/sdb2        58544AAE544A8F26                       ntfs       Log1 sda1 sda2 sdb1 sdb2 sdb3 BLKID Trash
/dev/sdb3        EA9635979635656B                       ntfs       Log1 sda1 sda2 sdb1 sdb2 BLKID Trash
/dev/sdb3        EA9635979635656B                       ntfs       Log1 sda1 sda2 sdb1 sdb2 sdb3 BLKID Trash
 
============================ "mount | grep ^/dev  output: ===========================
 
Device           Mount_Point              Type       Options
 
aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdb1        /media/Windows 7         fuseblk    (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)
 
 
============================= sdb1/grub/grub.cfg: =============================
 
#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#
 
### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  load_env
fi
set default="1"
if [ ${prev_saved_entry} ]; then
  set saved_entry=${prev_saved_entry}
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi
 
function savedefault {
  if [ -z ${boot_once} ]; then
    saved_entry=${chosen}
    save_env saved_entry
  fi
}
 
function recordfail {
  set recordfail=1
  if [ -n ${have_grubenv} ]; then if [ -z ${boot_once} ]; then save_env recordfail; fi; fi
}
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
### END /etc/grub.d/10_linux ###
 
### BEGIN /etc/grub.d/20_memtest86+ ###
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
 
=================== sdb1: Location of files loaded by Grub: ===================
 
 
    .0GB: grub/core.img
    .0GB: grub/grub.cfg
```
 
at the moment i have no ubuntu installed on my IDE drive which is recognize as SDA

---

### Post by ranch hand on 2010-02-07
That is an interesting result.

Where in flideration is your linux installation?  Acording to that you are trying to run grub from a ntfs Win7 boot sector.

WTF?  Did you just install grub somehow?

---

### Post by aviramof on 2010-02-07
no i did not not long ago i'v removed grub using windows 7 cd then reinstall ubuntu at the moment i have no ubuntu installed on my second hd but i did not removed grub so it still should be there it's as if ubuntu installion does not change the MBR on my first HD which is sdb i'll try to install it again now on my second HD which is sda for some unknown reason in bote ubuntu version and then run the script again from the live cd and will see if it changes anything.
 
but maybe first i would remove grub completly again to make sure it want cause any problems.

---

### Post by aviramof on 2010-02-07
ok now i have a grub free computer so before i try to install tell me do you it might had something to do with ext3/4 partition and can install 10.04 on ext3 file system and if do that would it have an inpact on his performance?
 
just to clear out now i have a completly free grub and ubuntu computer what should i do to install it on my second hd i'll explaine everything i do
 
1.restart the computer press install ubuntu i don't do that via live cd because this heavy version always get stuck somewhere in the 80%.
 
2.i go to manual partition although i did tried erase all drive and install side by side before the big problem is that it doesn't detect windows 7 loader for some reason but when i get to the import windows it does.
 
3.i choose sda1 or an empty space change it to ext4 mark format and add the / sign in that partition after that create say 3GB swap partition then choose or it's automaticly choose sad at the top now on this drive i have three partition 1 ext4 one swap and one ntfs although i also tried with no ntfs partition and full disk and everythin so far so good?
 
4.basicly that it that is what i did with ubuntu 8.10 and it worked anything eles i should do? maybe choose /boot instead of /?maybe ext3 and not 4?
 
thanks in advance.

---

### Post by cariboo on 2010-02-07
I haven't re-installed since alpha 1 came out, but there was a problem with the formatting portion of the install, I wouldn't let me create a / and home partition, I had to install everything on one partition. That may be part of the problem, but formatting as ext4 wasn't a problem.

---

### Post by VMC on 2010-02-07
I just did a zsync of the current daily-live Ubuntu 10.04 , and ubiquity works again, but alternate doesn't?! Just reversed from a couple of weeks ago.

Anyway, it should now work, but something is really messed up your partitions. I've never seen anything that looks like that before. Look at all the label names.

Why not just erase the entire hard drive if your going to start over. Nothing is on there, correct? Unless I misread something.

If your going to put Windows on one of the partitions then do that first and install Ubuntu last. But even so that can be dealt with later.

---

### Post by aviramof on 2010-02-08
the label names? let me explaine it again i have two Hard drives one is sata 1 one is IDE not the newest or the strongest computer i know but it should do in the sate theres is three partitions c f g c label is Window 7 g label is Local Disk in Hebrew and
g partition is the same but this partitions has nothing to do with ubuntu.
 
on my ide drive i have one partition called d her lable is again local disk in hebrew 
and at the moment 38GB of unalloacted space i can erase d as well this HD is completly empty all my files and my windows 7 os is stored on my sata HD and there
is not much i can do about this.
 
now if i install ubuntu 8.10 on my ide hd everything is fine there is grub 1 version 10.04 however does not create dual boot in fact i don't think she even recognize 
the windows 7 except in the import page in the partition page it said at the top no 
operating system are install on this drive or computer or what ever i'm using hebrew
in the installer not english maybe i should try the english but i didn't have any problem with that before.

---

### Post by ranch hand on 2010-02-08
I would go with the ext4.  I know some do not agree but I have no trouble wit hit and the OS is designed for it.

I would do all formating and partitioning before installing just to be safe.  Then all the installer has to do is put the stuff where you want it.  I do know that the last time I installed it did insist on formating the / partition that was pre-made and formatted to ext4.

I would not go with a separate boot partition (some do).

As VMC says I would format the whole drive and plan carefully what you want to do with the drive first.  Also as he says, install Win JerryLewis Pro first.  No MS OS plays nice unless it goes on first.

---

### Post by aviramof on 2010-02-08
what do you mean formating the whole drive with all do respect i have no intention of formating my windows 7 partition or other partition on that HD however i could try to create the partitions on my ide drive via Gparted and by the way is there a newer 
version of ubuntu 10.04 then what i have downloaded from here:
[http://cdimage.ubuntu.com/dvd/current/](http://cdimage.ubuntu.com/dvd/current/)
 
i have downloaded [lucid-dvd-i386.iso]("http://cdimage.ubuntu.com/dvd/current/lucid-dvd-i386.iso")  19-Jan-2010 13:38  3.8G

---

### Post by ranch hand on 2010-02-08
I am sorry, from the way it looked there may not have been anything on there except remnants.  By all means do not format anything you want to keep.

What you have downloaded is as new as it gets, until tomorrow and a new build.

---

### Post by aviramof on 2010-02-08
when can we expect a new build of ubuntu 10.04?

---

### Post by aviramof on 2010-02-08
if i install 8.10 again is there a way to upgrade directly to 10.04 because 9.04 and 9.10 don't want to connect to my internet for some reason via pppoe but 8.10 and 10.04 don't have that problem.
[]("http://cdimage.ubuntu.com/releases/lucid/alpha-2/")

---

### Post by ranch hand on 2010-02-08
No you can't upgrade from 8.10 to 10.04 in one jump.

You can, with a lot of care, go from 8.04.4 (the newest version of the last LTS) TO 10.04 (the new LTS).  I would not add any thing to the base install and remove/purge Firefox before trying it.  The testing of that upgrade just started on the 4th so it is early days.

There is a new build of 10.04 everyday (unless there is a real problem).  I like to wait until late in the day (GMT) to down load it.  That is so anyone that got it and had a problem has time to put it on the forum here.  Some build are just rough.  Some are just rough on certain hardware.

I really like RW disks so that you can try the buggers and over write the mthe next day if they are screwy.  Always check the md5sum.  Always burn at the lowest speed you can.

I use my external Memorex DVDrom to burn with as it will go slower  than the internal or the external Memorex CDrom.

---

### Post by aviramof on 2010-02-08
i did wanderd about the daily build here but if that is so then why all the dates here are jan 19?
 
[http://cdimage.ubuntu.com/dvd/current/](http://cdimage.ubuntu.com/dvd/current/)
 
if i download from there again it would diffrent then the previous version i have?
 
i can't check MD5 now because i no longer have the original ISO.

---

### Post by ranch hand on 2010-02-08
Wow, that threw me.

That is for the DVD.

Try the one;

[http://cdimage.ubuntu.com/daily-live/current/](http://cdimage.ubuntu.com/daily-live/current/)

It is up to Feb. 7.

---

### Post by aviramof on 2010-02-08
thank you added to favorits and someone should really update the dvd site and the cd version site that is in the release note that is in the dvd version the link there is from jan 14.
 
and one last thing before i download and install again does the feb 7 version get's update from the feb 8/9/10 and etc versions?

---

### Post by ranch hand on 2010-02-08
Basically the daily build is the same as my first 10.04 that was installed back at the start o november.  It has been upgraded and is current.  It also has a bunch of little hacks that have collected along the way.  The daily will not have those.  If you check that site tomorrow the date will be Feb. 8.

Each daily is a snapshot of the development of the OS that will become 10.04.

The DVD will stuff will probably be updated at A3 time.  The alpha and beta numbered releases are also just snapshots of the development put out at set times and with set goals to reach by that time.

If you search for it (the link is in my bookmarks on the other drive) you can find the "blueprint" for lucid.  You can see there what they are doing and what they are trying to get to work at anytime.

Right now we are still working on the foundation.  If you check the sticky on this forum for the schedule you will see that the feature freeze is the 25th when alpha3 is due.  And the first artwork drop.   And the user interface freeze.

Should get interesting then.

---

### Post by aviramof on 2010-02-08
thanks for the info i will to find all this information but for now i'm going to start to install latest cd version let's hope i would have a dual boot after that.:):):)
 
and by the way it would be great if you don't forget to update the ati driver on the
reposetory including the catalyst or develop something smiler in the os itself with some basic options better then what 8.10 had at least 
i didn't liked the way it looked on the 8.10 version there was hardly any option to control the dual view and considering the fact that my
computer is like the media center of the house connected via hdmi and dvi and rca and 
etc to two full hd lcd tv's and two screens that is important for me.:)

---

### Post by aviramof on 2010-02-08
ok i don't know what is going on with this version but it doesn't create dual boot infact it doesn't even recognize that there is windows 7 installed maybe i'll try going back to grub 1 maybe then it would work.

---

### Post by ranch hand on 2010-02-08
Be sure that you have grub installed on the mbr of the first drive (you can install it on all of them).

If you go back to grub-legacy use these directions;

[http://ubuntuforums.org/showthread.php?t=1298932](http://ubuntuforums.org/showthread.php?t=1298932)

---

