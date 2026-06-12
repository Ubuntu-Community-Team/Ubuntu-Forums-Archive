---
title: "Can't update or install"
date: 2011-03-04
forum: Installation &amp; Upgrades
---

### Post by Coco999 on 2011-03-04
I have Ubuntu 10.04. Somehow it seems to have gone haywire. I can use it, but can't either update or install anything. I attach captured images of the various error messages I get. How can I fix it?

---

### Post by Hakunka-Matata on 2011-03-04
```
sudo apt-get install -f
```

Have you run that code in a Terminal yet?

If you run the code, don't have synaptic open when you issue the command.

---

### Post by Frogs Hair on 2011-03-04
Did you try running the command in the third screen-shot ?```
sudo apt-get install -f
``` It is a bit late now but if you're offered the option of a partial upgrade I would not use it.

---

### Post by Coco999 on 2011-03-04
> **Hakunka-Matata said:**
> ```
sudo apt-get install -f
```

Have you run that code in a Terminal yet?

If you run the code, don't have synaptic open when you issue the command.

I did try, but it offers me a choice where to install Grub. As a matter of fact, I have it already installed and working properly. I choose the highlighted choice and then I get
> You chose not to install GRUB to any devices.  If you continue, the boot  &#9474; 
 &#9474; loader may not be properly configured, and when your computer next        &#9474; 
 &#9474; starts up it will use whatever was previously in the boot sector.  If     &#9474; 
 &#9474; there is an earlier version of GRUB 2 in the boot sector, it may be       &#9474; 
 &#9474; unable to load modules or handle the current configuration file.          &#9474; 
 &#9474;                                                                           &#9474; 
 &#9474; If you are already running a different boot loader and want to carry on   &#9474; 
 &#9474; doing so, or if this is a special environment where you do not need a     &#9474; 
 &#9474; boot loader, then you should continue anyway.  Otherwise, you should      &#9474; 
 &#9474; install GRUB somewhere.                                                   &#9474; 
 &#9474;                                                                           &#9474; 
 &#9474; Continue without installing GRUB?                                         &#9474; 
 &#9474;                                                                           &#9474; 
 &#9474;                    <Yes>                       <No> 

I am afraid to say yes and disrupting the Grub I have, but if I say no, it all stops there.

Probably it would be better to re-install Ubuntu, but I do not know how to do it without disturbing the files and installed programs I have.

Thank you for your help.

---

### Post by Hakunka-Matata on 2011-03-04
I would first open synaptic and check for broken packages.  If you have brokens package attempt to fix them.

---

### Post by Frogs Hair on 2011-03-05
Try System > Administration > Synaptic Package Manager > Custom Filters > Broken. Then use the Edit Tab and select fix all broken packages.

---

### Post by Coco999 on 2011-03-05
> **Frogs Hair said:**
> Try System > Administration > Synaptic Package Manager > Custom Filters > Broken. Then use the Edit Tab and select fix all broken packages.

Thank you for your help. I have tried but failed.
After System > Administration > Synaptic Package Manager I get the following error message:

> An error occurred

The following details are provided:

E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

Then I tried as suggested  sudo dpkg --configure -a   I get:

> dpkg: need an action option

Type dpkg --help for help about installing and deinstalling packages [*];
Use `dselect' or `aptitude' for user-friendly package management;
Type dpkg -Dhelp for a list of dpkg debug flag values;
Type dpkg --force-help for a list of forcing options;
Type dpkg-deb --help for help about manipulating *.deb files;
Type dpkg --license for copyright license and lack of warranty (GNU GPL) [*].

Options marked [*] produce a lot of output - pipe it through `less' or `more' !
coco@coco-desktop:~$ 

I tried 'aptitude' and it opens a very wide scope. I have to choose a way and don't know for sure what I must do. I'm afraid to disrupt the functionality I have now. The system looks to me as powerful but a little fragile. I don't know whether I did something wrong and now I need an expertise I don't posses to fix it. Please do help me.

---

### Post by Frogs Hair on 2011-03-05
Try this out  .```
**sudo dpkg-reconfigure -phigh -a**
```

---

### Post by Coco999 on 2011-03-05
> **Frogs Hair said:**
> Try this out  .```
**sudo dpkg-reconfigure -phigh -a**
```

This started a long process at the end of which I still could not run Synaptic Packing Manager.

---

### Post by Hakunka-Matata on 2011-03-06
[http://ubuntuforums.org/showthread.php?t=558887]("http://ubuntuforums.org/showthread.php?t=558887")

searching on Google for ```
_cache->open() failed, please report.
``` provides a lot of clues, maybe you can try that.  The above thread is one result

---

### Post by Coco999 on 2011-03-06
> **Hakunka-Matata said:**
> [http://ubuntuforums.org/showthread.php?t=558887]("http://ubuntuforums.org/showthread.php?t=558887")

searching on Google for ```
_cache->open() failed, please report.
``` provides a lot of clues, maybe you can try that.  The above thread is one result

In fact, too many clues. To sort them out requires an expertise I don't have. I'll try to delve into a problem that seemed to be simple. I'll give myself one month. If I can't find a solution when version 11.4 becomes available, I'll back up all my files, reformat and reinstall.

But at least I would like to know what did I do wrong, to avoid it in the future.

---

### Post by Frogs Hair on 2011-03-06
> **Coco999 said:**
> This started a long process at the end of which I still could not run Synaptic Packing Manager.

That was a command that worked for someone with the same problem and you already tried the other suggestion on the thread where I found it. I have not found anything more that you have not tried.

---

### Post by Hakunka-Matata on 2011-03-07
> In fact, too many clues. To sort them out requires an expertise I don't have. I'll try to delve into a problem that seemed to be simple. I'll give myself one month. If I can't find a solution when version 11.4 becomes available, I'll back up all my files, reformat and reinstall.

[COLOR="Magenta"]But at least I would like to know what did I do wrong, to avoid it in the future.[/COLOR]
Coco999 is offline Report Post   	Reply With Quote

It looks as though an update got interrupted before it finished, somehow?  The following thread appears to deal with exactly your condition. [http://ubuntuforums.org/showthread.php?t=1532208]("http://ubuntuforums.org/showthread.php?t=1532208") Pay attention to the cautions.  It appears to be valid in that it is dated July, 2,010.[COLOR="Magenta"][/COLOR]

---

### Post by Hakunka-Matata on 2011-03-07
Run ```
sudo dpkg --configure -a
``` and post results if in doubt @ that point.

---

### Post by Coco999 on 2011-03-07
> **Hakunka-Matata said:**
> Run ```
sudo dpkg --configure -a
``` and post results if in doubt @ that point.

This takes me to Configuring grub-pc  and is full of warnings I do not understand. It is as well fruitless.

The more I think about it, the more I think this is a frailty of a system, otherwise robust and reliable. I'm a mere user, I'm not supposed to be an expert in the inner workings of the thing.

Nearer to April 15, when 11.04 is available, I'll reinstall everything, but previously I'll try the suggestions in your other post and or any other wild procedure I don't understand. Of course, before I'll have to back up my files.

Thank you for your help.

---

### Post by Frogs Hair on 2011-03-07
When you receive a partial update or upgrade it is best not to use, It indicates that all the packages need to complete the process are not present and then you get breakage as know first hand .

If you see this again decline the partial update/grade and wait until all the packages are present in the update manager . You will know if all packages are present because you will not see partial update/grade message.

---

### Post by Hakunka-Matata on 2011-03-07
Let's see if you have any files hanging out in /var/lib/dpkg/updates.  They would be named with a sequential numbering scheme, see Thumbnail.

```
cd /var/lib/dpkg/updates && sudo ls
```

If the directory /var/lib/dpkg/updates is indeed populated with any files at all, it means your machine has attempted but not completed an update.  First things first, are there any files there?

---

### Post by Coco999 on 2011-03-07
> **Hakunka-Matata said:**
> Let's see if you have any files hanging out in /var/lib/dpkg/updates.  They would be named with a sequential numbering scheme, see Thumbnail.

```
cd /var/lib/dpkg/updates && sudo ls
```

If the directory /var/lib/dpkg/updates is indeed populated with any files at all, it means your machine has attempted but not completed an update.  First things first, are there any files there?

This is what I got:

```
coco@coco-desktop:~$ cd /var/lib/dpkg/updates && sudo ls
[sudo] password for coco: 
0000  0001  0002  0003	0004  0005  tmp.i
coco@coco-desktop:/var/lib/dpkg/updates$ 
```

No doubt you know a lot, but I am a mere user. What do I do now?
Thank you.

---

### Post by Hakunka-Matata on 2011-03-07
Ok, that's the first solid clue we have, you definitely have a partial update situation going on.  It's late now, and time to sleep, but I'll get back to this thread tomorrow.  Thanks for carrying on with this,

---

### Post by Coco999 on 2011-03-07
> **Hakunka-Matata said:**
> Ok, that's the first solid clue we have, you definitely have a partial update situation going on.  It's late now, and time to sleep, but I'll get back to this thread tomorrow.  Thanks for carrying on with this,

Thank you so much. It's late for me too. I'll be back tomorrow.

---

### Post by Hakunka-Matata on 2011-03-08
couple of choices:
[LIST=1]
[*]you attempt to look at the files with gedit to see if they contain the word "padding"
[*]you send me a copy of the files and I'll look inside to see what's to learn
[*]you follow a different solution posted earlier in this thread, I know where it is
[*]we make our own procedure and see if it works
[/LIST]

It would be naive to assume there is no danger of breaking the OS if we get it all wrong, and just deleting those files seems like a HEAVY hammer to be using on the update system.  But it is in fact what one poster says solved the problem for him.  So it's possible it would work for you.

The caveat is of course losing important Data you have on the installation.  Is the drive built with a separate /home partition where all your data is stored?
Are you backed up to your satisfaction?
Are you willing to re-install the system if the procedure leaves your installation all 'pear shaped'?

Let me know what you think.  As a minimum I'd like to be able to examine the files so I can understand better what state the installer was left in.  Attach the files with your reply, if that's ok with you.

---

### Post by Hakunka-Matata on 2011-03-08
the attached file shows a couple of posts on how other people have fixed a similar situation to yours.

I've just re-read this thread and notice post #4 as being interesting.  Your first post Thumbnails tell you to run```
sudo apt-get install -f
``` and post #4 tells you what to do to resolve the problem.  Are we missing something here?  I suggest you run the "bootinfoscript" script listed in my signature and post the results so we can see what your Grub configuration is.

It may be something simple, as you know, the solution often turns out to be something simple!

---

### Post by Coco999 on 2011-03-08
> **Hakunka-Matata said:**
> couple of choices:
[LIST=1]
[*]you attempt to look at the files with gedit to see if they contain the word "padding"
[*]you send me a copy of the files and I'll look inside to see what's to learn
[*]you follow a different solution posted earlier in this thread, I know where it is
[*]we make our own procedure and see if it works
[/LIST]

It would be naive to assume there is no danger of breaking the OS if we get it all wrong, and just deleting those files seems like a HEAVY hammer to be using on the update system.  But it is in fact what one poster says solved the problem for him.  So it's possible it would work for you.

The caveat is of course losing important Data you have on the installation.  Is the drive built with a separate /home partition. where all your data is stored?
Are you backed up to your satisfaction?
Are you willing to re-install the system if the procedure leaves your installation all 'pear shaped'?

Let me know what you think.  As a minimum I'd like to be able to examine the files so I can understand better what state the installer was left in.  Attach the files with your reply, if that's ok with you.

First of all, let me thank you for your continued and intensive help, that I appreciate deeply.

I saw the files. The numbered ones refer to Python and Grub. File tmp.i consists of 512 identical lines that say   **#padding**

Regarding loss of data, I have not a separate partition for home. This sounds as a clever idea, but I didn't know it was possible. I just left a partition of about 20 GB for Ubuntu and used the CD for installation.

I accept the idea that eventually I may have to reformat this partition and reinstall Ubuntu and the many programs that I use, or like to have. But 1, I want to wait until 11.04 is available, and 2, I have to back up all the data I have.

Let's assume all goes wrong, can I access my data by booting with an UBUNTU CD, using it as a live one?

Please tell me if you still would like to see the files.

---

### Post by Hakunka-Matata on 2011-03-08
> **Coco999 said:**
> First of all, let me thank you for your continued and intensive help, that I appreciate deeply.

I saw the files. The numbered ones refer to Python and Grub. File tmp.i consists of 512 identical lines that say   **#padding**

Regarding loss of data, I have not a separate partition for home. This sounds as a clever idea, but I didn't know it was possible. I just left a partition of about 20 GB for Ubuntu and used the CD for installation.

I accept the idea that eventually I may have to reformat this partition and reinstall Ubuntu and the many programs that I use, or like to have. But 1, I want to wait until 11.04 is available, and 2, I have to back up all the data I have.

Let's assume all goes wrong, can I access my data by booting with an UBUNTU CD, using it as a live one?

Please tell me if you still would like to see the files.

Yes, I would like to see the files.  I cannot promise for SURE, but it is most likely your files will be accessible using the LiveCd.  We're not dealing with any partitioning schemes, so I don't see the likelihood of a partition being deleted or overwritten. If we can proceed slowly and carefully all the better.  Do you have any room, or another partition where you could copy Data over to now, and feel safer?

---

### Post by Hakunka-Matata on 2011-03-08
Coco999, please check contents of this directory too.  Any files there?

```
/var/cache/apt/archives/partial$
```

---

### Post by Coco999 on 2011-03-08
> **Hakunka-Matata said:**
> Yes, I would like to see the files.  I cannot promise for SURE, but it is most likely your files will be accessible using the LiveCd.  We're not dealing with any partitioning schemes, so I don't see the likelihood of a partition being deleted or overwritten. If we can proceed slowly and carefully all the better.  Do you have any room, or another partition where you could copy Data over to now, and feel safer?

I attach a zip file with all the update files in it. I have added .txt to all the names, I thought I had to do it because the attachment manager had rejected them. I used Gedit to open and re-save the files.

I have plenty of room, in other partitions, but they are FAT32.

I'll run the script and send you the results.

In one of your replies you mention an attachment that I did not find.

---

### Post by Coco999 on 2011-03-08
I attach the results of the script.

---

### Post by Hakunka-Matata on 2011-03-08
Thanks for sending the Data. 

> **Coco999 said:**
> I attach a zip file with all the update files in it. I have added .txt to all the names, I thought I had to do it because the attachment manager had rejected them. I used Gedit to open and re-save the files.

I have plenty of room, in other partitions, but they are FAT32.

I'll run the script and send you the results.

[COLOR="Red"]In one of your replies you mention an attachment that I did not find.[/COLOR]

[LIST]
[COLOR="Red"][*]Yes, in  post #13: the hyperlink that ends with "1532208".[/COLOR]
[*]Your Disc partitioning seems a bit messy, using FAT32 no less.  And Grub2 is installed so many times, all over the place.  Is this a Wubi installation?
[*]Anyway, I think you can read your FAT32 partitions with nautilus file browser, can you?
[*]If you can, can you simply copy your important Data to one of those FAT32 partitions?  I don't use FAT32 in dual boot mode, so I don't know.
[*]  Normally when I have a WindowsXP & Ubuntu dual boot drive, XP is installed on a NTFS partition, and when it is that way, it's very good as a shared Data Partition.  Both XP and Ubuntu can access it with no problem.
[*]Also, have you tried to open the Update Manager in System > Administration menu, and if so what happens?  Does it say your system is messed up or OK?
[*]I'm ready to try fixing the partial upgrade problem, but you have to decide what you're going to do about backup before we proceed.
[*]Can you use a liveCD and see if you can read data in the FAT32 partitions?
[/LIST]

The OS i'm using right now is a fresh 10.04-2 Desktop i386 build, and I copied the 0000, 0001, etc files into the same directory where you have them, then went for update manager, it gave me similar error messages but when I ran the "sudo dpkg-reconfigure -phigh -a" command it ran right through everything and fixed everything, emptied that updates/directory of all the 0000, 00001, tmp.i, files and everything.  funny

let me know our next step.

I've asked for a lot of data from you, thanks for sending it.  I'll ask for another thing, a snapshot/Thumbnail of a GParted picture of your drive.

---

### Post by Hakunka-Matata on 2011-03-08
I'm testing how to attach your Results.txt file, for myself, I forgot sort of...that's how it works when I open the Results.txt file, Ctrl-A, and copy complete contents, then paste it in between code # tags.  For future reference

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #6 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows XP: Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda2 and 
                       looks at sector 270609898 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. According to the info in the boot sector, 
                       sda2 starts at sector 0. But according to the info 
                       from fdisk, sda2 starts at sector 61432686.
    Operating System:  
    Boot files/dirs:   

sda3: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda3 and 
                       looks at sector 270609898 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. According to the info in the boot sector, 
                       sda3 starts at sector 0. But according to the info 
                       from fdisk, sda3 starts at sector 112631715.
    Operating System:  
    Boot files/dirs:   

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda5 and 
                       looks at sector 270612338 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. According to the info in the boot sector, 
                       sda5 starts at sector 0. But according to the info 
                       from fdisk, sda5 starts at sector 174064338.
    Operating System:  
    Boot files/dirs:   /ubuntu/winboot/wubildr /ubuntu/winboot/wubildr.mbr

sda6: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda6 and 
                       looks at sector 271234562 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location.
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda7: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    61,432,559    61,432,497   c W95 FAT32 (LBA)
/dev/sda2          61,432,686   112,631,714    51,199,029   b W95 FAT32
/dev/sda3         112,631,715   174,064,274    61,432,560   b W95 FAT32
/dev/sda4         174,064,275   312,576,704   138,512,430   5 Extended
/dev/sda5         174,064,338   270,325,754    96,261,417   b W95 FAT32
/dev/sda6         270,325,818   310,729,229    40,403,412  83 Linux
/dev/sda7         310,729,293   312,576,704     1,847,412  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        7C95-1978                              vfat       WDC1                          
/dev/sda2        5141-E757                              vfat       WDC2                          
/dev/sda3        508C-CCA4                              vfat       WDC3                          
/dev/sda4: PTTYPE="dos" 
/dev/sda5        50E6-B14E                              vfat       WDC4                          
/dev/sda6        b79c4293-976a-4962-a852-2e0fae9f084d   ext4                                     
/dev/sda7        df72390c-4ec3-421e-a16a-f0bc4417cacb   swap                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda6        /                        ext4       (rw,errors=remount-ro)


================================ sda1/boot.ini: ================================

[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect


=========================== sda6/boot/grub/grub.cfg: ===========================

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
set default="0"
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
insmod ext2
set root='(hd0,6)'
search --no-floppy --fs-uuid --set b79c4293-976a-4962-a852-2e0fae9f084d
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
insmod ext2
set root='(hd0,6)'
search --no-floppy --fs-uuid --set b79c4293-976a-4962-a852-2e0fae9f084d
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, with Linux 2.6.32-26-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set b79c4293-976a-4962-a852-2e0fae9f084d
	linux	/boot/vmlinuz-2.6.32-26-generic root=UUID=b79c4293-976a-4962-a852-2e0fae9f084d ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-26-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-26-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set b79c4293-976a-4962-a852-2e0fae9f084d
	echo	'Loading Linux 2.6.32-26-generic ...'
	linux	/boot/vmlinuz-2.6.32-26-generic root=UUID=b79c4293-976a-4962-a852-2e0fae9f084d ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-26-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-25-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set b79c4293-976a-4962-a852-2e0fae9f084d
	linux	/boot/vmlinuz-2.6.32-25-generic root=UUID=b79c4293-976a-4962-a852-2e0fae9f084d ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-25-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set b79c4293-976a-4962-a852-2e0fae9f084d
	echo	'Loading Linux 2.6.32-25-generic ...'
	linux	/boot/vmlinuz-2.6.32-25-generic root=UUID=b79c4293-976a-4962-a852-2e0fae9f084d ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set b79c4293-976a-4962-a852-2e0fae9f084d
	linux	/boot/vmlinuz-2.6.32-24-generic root=UUID=b79c4293-976a-4962-a852-2e0fae9f084d ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set b79c4293-976a-4962-a852-2e0fae9f084d
	echo	'Loading Linux 2.6.32-24-generic ...'
	linux	/boot/vmlinuz-2.6.32-24-generic root=UUID=b79c4293-976a-4962-a852-2e0fae9f084d ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-23-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set b79c4293-976a-4962-a852-2e0fae9f084d
	linux	/boot/vmlinuz-2.6.32-23-generic root=UUID=b79c4293-976a-4962-a852-2e0fae9f084d ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-23-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set b79c4293-976a-4962-a852-2e0fae9f084d
	echo	'Loading Linux 2.6.32-23-generic ...'
	linux	/boot/vmlinuz-2.6.32-23-generic root=UUID=b79c4293-976a-4962-a852-2e0fae9f084d ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set b79c4293-976a-4962-a852-2e0fae9f084d
	linux	/boot/vmlinuz-2.6.32-22-generic root=UUID=b79c4293-976a-4962-a852-2e0fae9f084d ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set b79c4293-976a-4962-a852-2e0fae9f084d
	echo	'Loading Linux 2.6.32-22-generic ...'
	linux	/boot/vmlinuz-2.6.32-22-generic root=UUID=b79c4293-976a-4962-a852-2e0fae9f084d ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set b79c4293-976a-4962-a852-2e0fae9f084d
	linux	/boot/vmlinuz-2.6.32-21-generic root=UUID=b79c4293-976a-4962-a852-2e0fae9f084d ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set b79c4293-976a-4962-a852-2e0fae9f084d
	echo	'Loading Linux 2.6.32-21-generic ...'
	linux	/boot/vmlinuz-2.6.32-21-generic root=UUID=b79c4293-976a-4962-a852-2e0fae9f084d ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set b79c4293-976a-4962-a852-2e0fae9f084d
	linux	/boot/vmlinuz-2.6.31-21-generic root=UUID=b79c4293-976a-4962-a852-2e0fae9f084d ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.31-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set b79c4293-976a-4962-a852-2e0fae9f084d
	echo	'Loading Linux 2.6.31-21-generic ...'
	linux	/boot/vmlinuz-2.6.31-21-generic root=UUID=b79c4293-976a-4962-a852-2e0fae9f084d ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.31-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set b79c4293-976a-4962-a852-2e0fae9f084d
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root='(hd0,6)'
	search --no-floppy --fs-uuid --set b79c4293-976a-4962-a852-2e0fae9f084d
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sda1)" {
	insmod fat
	set root='(hd0,1)'
	search --no-floppy --fs-uuid --set 7c95-1978
	drivemap -s (hd0) ${root}
	chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda6/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda6 during installation
UUID=b79c4293-976a-4962-a852-2e0fae9f084d /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda7 during installation
UUID=df72390c-4ec3-421e-a16a-f0bc4417cacb none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda6: Location of files loaded by Grub: ===================


 138.8GB: boot/grub/core.img
 143.7GB: boot/grub/grub.cfg
 149.1GB: boot/initrd.img-2.6.31-21-generic
 147.4GB: boot/initrd.img-2.6.32-21-generic
 148.1GB: boot/initrd.img-2.6.32-22-generic
 149.2GB: boot/initrd.img-2.6.32-23-generic
 155.4GB: boot/initrd.img-2.6.32-24-generic
 155.0GB: boot/initrd.img-2.6.32-25-generic
 156.6GB: boot/initrd.img-2.6.32-26-generic
 146.0GB: boot/vmlinuz-2.6.31-21-generic
 149.1GB: boot/vmlinuz-2.6.32-21-generic
 147.7GB: boot/vmlinuz-2.6.32-22-generic
 151.8GB: boot/vmlinuz-2.6.32-23-generic
 153.3GB: boot/vmlinuz-2.6.32-24-generic
 154.3GB: boot/vmlinuz-2.6.32-25-generic
 155.1GB: boot/vmlinuz-2.6.32-26-generic
 156.6GB: initrd.img
 155.0GB: initrd.img.old
 155.1GB: vmlinuz
 154.3GB: vmlinuz.old
```

---

### Post by Coco999 on 2011-03-08
Thank you, Hakunka-Matata, for your help and your concern. Now it is a little late. Tomorrow I will teply.

---

### Post by Hakunka-Matata on 2011-03-09
[http://ubuntuforums.org/showthread.php?t=1703381]("http://ubuntuforums.org/showthread.php?t=1703381") Post #2 is very good information!

Coco, the above Thread explains succinctly how to:
[LIST]
[*]create a list of your installed programs/apps and save the list to a .txt file ```
dpkg --get-selections > installed-packages.txt
```
[*]after backing up, rebuilding or upgrading to later Ubuntu-Release, then re-partitioning your HDD(s), and installing OSs
[*]quickly re-install all the apps automatically using your saved .txt list.```
sudo dpkg --set-selections < installed-packages.txt && sudo apt-get dselect-upgrade
```
[/LIST]
Brilliant-Thanks forum member 'wizard10000'

Why do I share it with you?  Your HDD partitioning is pretty messed up I think.  Now might be the time to redo the complete HDD's partitioning scheme.  You say you want to install Natty 11.04?, and that's fine.  But new releases usually have a few problems, 10.04 is really solid now so you could install both Releases on your new HDD, in separate partitions of course.  Also partition for a separate /home partition, so you could start either 10.04 or 11.04, use the same /home partition for data, install the same apps from your saved Apps.txt file.  All on a nice clean disc.

---

### Post by Coco999 on 2011-03-09
> **Hakunka-Matata said:**
> [http://ubuntuforums.org/showthread.php?t=1703381]("http://ubuntuforums.org/showthread.php?t=1703381") Post #2 is very good information!

Coco, the above Thread explains succinctly how to:
[LIST]
[*]create a list of your installed programs/apps and save the list to a .txt file ```
dpkg --get-selections > installed-packages.txt
```
[*]after backing up, rebuilding or upgrading to later Ubuntu-Release, then re-partitioning your HDD(s), and installing OSs
[*]quickly re-install all the apps automatically using your saved .txt list.```
sudo dpkg --set-selections < installed-packages.txt && sudo apt-get dselect-upgrade
```
[/LIST]
Brilliant-Thanks forum member 'wizard10000'

Why do I share it with you?  Your HDD partitioning is pretty messed up I think.  Now might be the time to redo the complete HDD's partitioning scheme.  You say you want to install Natty 11.04?, and that's fine.  But new releases usually have a few problems, 10.04 is really solid now so you could install both Releases on your new HDD, in separate partitions of course.  Also partition for a separate /home partition, so you could start either 10.04 or 11.04, use the same /home partition for data, install the same apps from your saved Apps.txt file.  All on a nice clean disc.

Thanks again. I have to assimilate all of your suggestions and think it over, and decide what to do. But today I just have no time to do it. I'm busy elsewhere. I'll have to wait until tomorrow, I'm afraid.

---

### Post by Hakunka-Matata on 2011-03-09
understood & definitely no problem.  later

---

### Post by haudace on 2011-03-09
> **Hakunka-Matata said:**
> Run ```
sudo dpkg --configure -a
``` and post results if in doubt @ that point.
 
I had the same problem as the fellow who started this thread. I fixed it by entering this command in the terminal.

---

### Post by Hakunka-Matata on 2011-03-09
see post #15

---

### Post by Coco999 on 2011-03-10
> **Hakunka-Matata said:**
> Thanks for sending the Data. 



[LIST]
[COLOR="Red"][*]Yes, in  post #13: the hyperlink that ends with "1532208".[/COLOR]
[*]Your Disc partitioning seems a bit messy, using FAT32 no less.  And Grub2 is installed so many times, all over the place.  Is this a Wubi installation?
[*]Anyway, I think you can read your FAT32 partitions with nautilus file browser, can you?
[*]If you can, can you simply copy your important Data to one of those FAT32 partitions?  I don't use FAT32 in dual boot mode, so I don't know.
[*]  Normally when I have a WindowsXP & Ubuntu dual boot drive, XP is installed on a NTFS partition, and when it is that way, it's very good as a shared Data Partition.  Both XP and Ubuntu can access it with no problem.
[*]Also, have you tried to open the Update Manager in System > Administration menu, and if so what happens?  Does it say your system is messed up or OK?
[*]I'm ready to try fixing the partial upgrade problem, but you have to decide what you're going to do about backup before we proceed.
[*]Can you use a liveCD and see if you can read data in the FAT32 partitions?
[/LIST]

The OS i'm using right now is a fresh 10.04-2 Desktop i386 build, and I copied the 0000, 0001, etc files into the same directory where you have them, then went for update manager, it gave me similar error messages but when I ran the "sudo dpkg-reconfigure -phigh -a" command it ran right through everything and fixed everything, emptied that updates/directory of all the 0000, 00001, tmp.i, files and everything.  funny

let me know our next step.

I've asked for a lot of data from you, thanks for sending it.  I'll ask for another thing, a snapshot/Thumbnail of a GParted picture of your drive.

a

---

### Post by Coco999 on 2011-03-10
Sorry, my last reply was sent in error, without completing. I just sent the Gparted results showing my partition scheme. It could be improved, mainly allowing more room for Ubuntu, but I would not think it is messy.

Yes, I can freely both write and read FAT32 files with my existing ubuntu. This allows me to backup easily. But in normal operation, Ubuntu uses its own partition only.

XP is in sda1 (WDC1). I also own a USB external hard disk, having about 250 GB, not connected now, that has plenty of room for storage.

I have been thinking about the whole thing, and am ready to go as deep as necessary to fix the problem, even at the risk of having to reinstall everything. In one of your replies there is a valuable information, how to make a list of programs to automatically reinstall them in the future. But I wish to go slowly and trying to understand all steps

---

### Post by Hakunka-Matata on 2011-03-10
> **Coco999 said:**
> Sorry, my last reply was sent in error, without completing. I just sent the Gparted results showing my partition scheme. It could be improved, mainly allowing more room for Ubuntu, but I would not think it is messy.

Yes, I can freely both write and read FAT32 files with my existing ubuntu. This allows me to backup easily. But in normal operation, Ubuntu uses its own partition only.

XP is in sda1 (WDC1). I also own a USB external hard disk, having about 250 GB, not connected now, that has plenty of room for storage.

I have been thinking about the whole thing, and am ready to go as deep as necessary to fix the problem, even at the risk of having to reinstall everything. In one of your replies there is a valuable information, how to make a list of programs to automatically reinstall them in the future. But I wish to go slowly and trying to understand all steps

Thanks for the Thumbnail from GParted, that makes it easy to understand. That is good.  I do not mean to criticize when I say your partitioning is 
"messed" up.  I say that only because there are FAT32 partitions on the drive, those partitions could all be NTFS partitions instead.  [http://www.techrepublic.com/forum/questions/101-311728]("http://www.techrepublic.com/forum/questions/101-311728")  I will send you a picture of one of my hard drives that has WindowsXP and Ubuntu installed.  It is your decision how to partition your hard drives, but most people use NTFS for Windows instead of FAT32.

---

### Post by Hakunka-Matata on 2011-03-10
I had to shutdown and switch drives around:  So here's a Thumbnail of a 80GB /dev/sdb

The root partition mounted on / is big, because I have lots of data there, I will change that to a separate /home partition when I get time here soon.  I have the swap file 'about 2 x my RAM (2GB)' and it's located at the very end of the disc, for fastest access.  

next I'll show you my other drive with WinXP and ubuntu on it, it looks something like yours would look after reworking it, probably.

---

### Post by Hakunka-Matata on 2011-03-10
I Sent the wrong Thumbnail.

---

### Post by Coco999 on 2011-03-10
> **Hakunka-Matata said:**
> Thanks for the Thumbnail from GParted, that makes it easy to understand. That is good.  I do not mean to criticize when I say your partitioning is 
"messed" up.  I say that only because there are FAT32 partitions on the drive, those partitions could all be NTFS partitions instead.  [http://www.techrepublic.com/forum/questions/101-311728]("http://www.techrepublic.com/forum/questions/101-311728")  I will send you a picture of one of my hard drives that has WindowsXP and Ubuntu installed.  It is your decision how to partition your hard drives, but most people use NTFS for Windows instead of FAT32.

Had I known this previously, I might have used NTFS. Ubuntu only recently can read NTFS. At the time I partitioned this disk, 2 or 3 years ago, I preferred to be on the safe side and thus used FAT32. I understand that NTFS is vastly superior. Next time I'll use it, but for the time being I think I will leave things as they are. My concern now is to clean up the Ubuntu I have to accept updates and new installations.
I still think this is a kind of bug. A small error ought not to have such implications, difficult to understand and almost impossible to fix.

---

### Post by Hakunka-Matata on 2011-03-10
> **Coco999 said:**
> Had I known this previously, I might have used NTFS. Ubuntu only recently can read NTFS. At the time I partitioned this disk, 2 or 3 years ago, I preferred to be on the safe side and thus used FAT32. I understand that NTFS is vastly superior. Next time I'll use it, but for the time being I think I will leave things as they are. My concern now is to clean up the Ubuntu I have to accept updates and new installations.
I still think this is a kind of bug. A small error ought not to have such implications, difficult to understand and almost impossible to fix.
Yes, 2 or 3 years in the computing world makes a big difference.  I've had the same thing happen with update getting broken midstream, and I've always been able to fix it.  But it can be confusing.  If you have all your data backed up, and you have the list of programs/apps saved off to a safe place, then you could try to fix the update problem and without fear.  Try some things we know might work, if they break the system completely, well, time to reinstall, with clean partitioning etc. etc. etc.  And if you can fix the update cache, all the better, something learned.

---

### Post by Hakunka-Matata on 2011-03-10
250GB sda drive

[LIST]
[*]/dev/sda1: ntfs - WinXP OS - root / - [COLOR="Red"]primary partition[/COLOR]  No.1
[*]/dev/sda2: ext4 - Ubuntu10.10 OS - root / - [COLOR="Red"]primary partition[/COLOR] No.2
[*]/dev/sda4: ext4 - /home Data (shared) - [COLOR="Red"]primary partition[/COLOR] No.3
[*]/dev/sda3: extended - (container for lots of logical partitions) - [COLOR="Red"]primary partiton[/COLOR] No.4 (max 4 primary partitions allowed)
[*]unallocated:  free space for more [COLOR="Blue"]logical partitions - logical partition[/COLOR]
[*]/dev/sda5: linux-swap - shared - size ~2xRAM - [COLOR="Blue"]logical partition[/COLOR]
[/LIST]

Left hand side Thumbnail = Drive is not active - not mounted = No Mount points listed
Right hand side Thumbnail = Drive active (booted from) - all partitions mounted and therefore locked (with the key icon) all partitions have mount point listed

---

### Post by Coco999 on 2011-03-10
> **Hakunka-Matata said:**
> Yes, 2 or 3 years in the computing world makes a big difference.  I've had the same thing happen with update getting broken midstream, and I've always been able to fix it.  But it can be confusing.  If you have all your data backed up, and you have the list of programs/apps saved off to a safe place, then you could try to fix the update problem and without fear.  Try some things we know might work, if they break the system completely, well, time to reinstall, with clean partitioning etc. etc. etc.  And if you can fix the update cache, all the better, something learned.

I fully agree, except about "clean partitioning". If I keep this HD, I would only reformat my sda6 (ext4) and sda7 (linux swap. The rest remains as it is. Perhaps in the near future, I may buy a new hard disk and then make a new partition from scratch.

Thank you for your help. I'll let you know when I have finished backing up.

---

### Post by Hakunka-Matata on 2011-03-11
Hey Coco, I understand what you're saying about waiting to get another drive.  After looking at your partitioning again, except for the fact I don't like FAT32, it's setup just right IMHO.

and lookie here, [http://ubuntuforums.org/showthread.php?t=780531]("http://ubuntuforums.org/showthread.php?t=780531") maybe your answer?

---

### Post by Coco999 on 2011-03-11
I have now copied in one of the FAT32 partitions almost the complete "home" information. I think all my data is here. But I wonder whether I need something else, as well.

---

### Post by Hakunka-Matata on 2011-03-11
something else, as well?  

```
dpkg -l > installed_packages
``` that?

What's your plan of attack?

---

### Post by leeshaub on 2011-03-11
i had the same thing a year ago look for software sources in ubuntu software center

---

### Post by Coco999 on 2011-03-11
> **Hakunka-Matata said:**
> something else, as well?  

```
dpkg -l > installed_packages
``` that?

What's your plan of attack?

You don't tell me whether I need to backup something else. Then I will reread the whole thread and decide what to do. Perhaps I will follow those ways that were full ow warnings about what could happen to me. Any suggestions?

---

### Post by Hakunka-Matata on 2011-03-11
I wanted to know if you are backed up to your satisfaction.  Having your data copied to another partition is good but it's still on the same drive.  What happens if this whole drive gets corrupted?  Better safe than sorry?

---

### Post by Coco999 on 2011-03-11
> **Hakunka-Matata said:**
> I wanted to know if you are backed up to your satisfaction.  Having your data copied to another partition is good but it's still on the same drive.  What happens if this whole drive gets corrupted?  Better safe than sorry?

I did not think this could happen at all. If this is so I have to think the whole thing again.

---

### Post by Coco999 on 2011-03-12
This is what I think I will do. I will buy a new drive of about 320 GB. I will copy my existing 160 GB drive into it. Then I may use the wildest procedures to try and fix my problem. If all fails, I will start anew with the 320 GB disk. My project of partitions is like this

1. 40 GB for Windows - NTFS
2. 70 GB - NTFS
3. 70 GB - NTFS
4. 70 GB - NTFS
5. 10 GB - FAT32
6. 60 GB - unallocated, to receive UBUNTU

Please notice that I need at least one small FAT32 because I do a couple of things with MS DOS, that can not read NTFS.

Any suggestions?

---

### Post by Hakunka-Matata on 2011-03-12
Great idea, get a new drive, they are very inexpensive now.  I buy from tigerdirect.com, where do you buy from?

You can have a maximum of four (4) primary partitons on a drive, now days. So you make 3 primaries, if you need 3, then the 4th one you make as an Extended partition.  Extended partitions count as a primary.  Then within the Extended you make many logical partitons.  Ubuntu can be installed in a logical, Windows cannot.

Look at the two Thumbnails in post # 43, shows Primary, Extended, and Logical partitions.

---

### Post by Coco999 on 2011-03-12
> **Hakunka-Matata said:**
> Great idea, get a new drive, they are very inexpensive now.  I buy from tigerdirect.com, where do you buy from?

You can have a maximum of four (4) primary partitons on a drive, now days. So you make 3 primaries, if you need 3, then the 4th one you make as an Extended partition.  Extended partitions count as a primary.  Then within the Extended you make many logical partitons.  Ubuntu can be installed in a logical, Windows cannot.

Look at the two Thumbnails in post # 43, shows Primary, Extended, and Logical partitions.

I buy from a local supplier, RS Computación, I'm located at Rosario, Argentina, but your reference is useful to check the prices and specs. Here we pay about 15 % more including tax.

I have tried to understand your scheme of partitions. Why do you have 2 ext4 partitions and such a large unallocated space? Where does Ubuntu reside?

---

### Post by Hakunka-Matata on 2011-03-12
[LIST]
[*]sda2: mount point /         (system partition)
[*]sda4: mount point /home     (separate home [Data] partition)
[/LIST]

Whenever you see / for a mount point, that's the system partition, Ubuntu Operating system (or any Linux OS)

/home is a separate home partition, it's a data partition that is mounted separately from the system partition.  So you could have several different Ubuntu linux OSes you use and boot to, and they could all use the same data partition /home.

also you can upgrade your system and not wipe out your data, OS and Data on separate partitions.

Extra unallocated, because I'm always changing thing around, testing.

---

### Post by Hakunka-Matata on 2011-03-12
Another drive with more partitions, which partition is the system partition right now?

---

### Post by Hakunka-Matata on 2011-03-12
Coco, tengo sueño, ya me voy a dormir.  See you later

---

### Post by Coco999 on 2011-03-12
> **Hakunka-Matata said:**
> [LIST]
[*]sda2: mount point /         (system partition)
[*]sda4: mount point /home     (separate home [Data] partition)
[/LIST]

Whenever you see / for a mount point, that's the system partition, Ubuntu Operating system (or any Linux OS)

/home is a separate home partition, it's a data partition that is mounted separately from the system partition.  So you could have several different Ubuntu linux OSes you use and boot to, and they could all use the same data partition /home.

also you can upgrade your system and not wipe out your data, OS and Data on separate partitions.

Extra unallocated, because I'm always changing thing around, testing.

Me parece muy ingenioso tener el sistema operativo en una partición y los datos en otra. ¿Pero cómo se logra? Hasta donde yo sé (o sabía), el disco de instalación de UBUNTU lo hace todo y ubica los datos en la misma partición.

Necesito tener un sistema dual, W XP y UBUNTU. También en XP sería interesante tener el SO en una partición y los programas de las aplicaciones en otra, dado que XP necesita frecuentes reinstalaciones porque se degrada fácilmente. Pero en este caso no sé cómo opera el registro de Windows

---

### Post by Coco999 on 2011-03-12
> **Hakunka-Matata said:**
> Another drive with more partitions, which partition is the system partition right now?

/dev/sdc1
Es la única suficientemente ocupada como para albergar el sist. op.

---

### Post by Coco999 on 2011-03-12
> **Hakunka-Matata said:**
> Coco, tengo sueño, ya me voy a dormir.  See you later

¿Qué castellano es el tuyo?

---

### Post by Hakunka-Matata on 2011-03-12
[https://help.ubuntu.com/community/Partitioning/Home/Moving]("https://help.ubuntu.com/community/Partitioning/Home/Moving")

Check that URL for separate /home partition.

I've worked for long periods in several different Spanish speaking countries, your's being one of them.  1,974-76 Moreno Radar station, West of Buenos Aires.

Very late, I'll see you later, good luck.

---

### Post by Hakunka-Matata on 2011-03-12
> **Coco999 said:**
> /dev/sdc1
Es la única suficientemente ocupada como para albergar el sist. op.

Yes, if you're not storing /home data there, it's enough for the OS.

---

### Post by Coco999 on 2011-03-13
> **Hakunka-Matata said:**
> [https://help.ubuntu.com/community/Partitioning/Home/Moving]("https://help.ubuntu.com/community/Partitioning/Home/Moving")

Check that URL for separate /home partition.

I've worked for long periods in several different Spanish speaking countries, your's being one of them.  1,974-76 Moreno Radar station, West of Buenos Aires.

Very late, I'll see you later, good luck.

I just wanted to send you a private message, but it seems you have blocked out that possibility. If you would kindly send me one stating your e-mail address, we could exchange some personal information without cluttering the forum.

---

### Post by Hakunka-Matata on 2011-03-13
Coco999, Usted está en mi lista de contactos ahora. Así que usted puede enviarme un mensaje privado ahora. Si quiere.  CIAO Andrés

---

### Post by Coco999 on 2011-03-15
> **Hakunka-Matata said:**
> [https://help.ubuntu.com/community/Partitioning/Home/Moving]("https://help.ubuntu.com/community/Partitioning/Home/Moving")

Check that URL for separate /home partition.

I've worked for long periods in several different Spanish speaking countries, your's being one of them.  1,974-76 Moreno Radar station, West of Buenos Aires.

Very late, I'll see you later, good luck.

I have now ordered the 320 GB drive, but it was not delivered yet. I am thinking about the partition. my revised partition project looks like this.

1. 40 GB NTFS to receive W XP
2. 50 GB NTFS
3. 50 GB NTFS
4. 50 GB NTFS
5. 10 GB FAT32 to be able to use MS DOS
6. 20 GB ext3 (or 4, please advise) for UBUNTU OS
7. 80 GB ext3 (or 4, please advise) for UBUNTU home files
8. 20 GB unallocared space

The mentioned document deals with moving home to another partition and the procedure is rather elaborate, even intricate. In this case I would be starting a new installation from scratch and then it ought to be simpler, but I dont know if the choice is available for new installations.

---

### Post by Hakunka-Matata on 2011-03-17
> 1. 40 GB NTFS to receive W XP
2. 50 GB NTFS
3. 50 GB NTFS
4. 50 GB NTFS
5. 10 GB FAT32 to be able to use MS DOS
6. 20 GB ext3 (or 4, please advise) for UBUNTU OS
7. 80 GB ext3 (or 4, please advise) for UBUNTU home files
8. 20 GB unallocared space 
The mentioned document deals with moving home to another partition and  the procedure is rather elaborate, even intricate. In this case I would  be starting a new installation from scratch and then it ought to be  simpler, but I dont know if the choice is available for new  installations.320GB is a lot of disk space.  You most likely already know there is no one "right way" to partition the drive.  It's a personal choice except for some distinct absolute requirements.  [[COLOR=Navy]_This_[/COLOR]]("https://help.ubuntu.com/community/HowtoPartition") website should help.  

With the experience I have (intermediate level user I guess, but still LOTS more to learn) I feel comfortable recommending a few details.  This forum is an excellent place to resolve problems and learn, but the official Ubuntu website usually explains all the angles of any given theme, I go there if I get too many different suggestions here in the forums.

[LIST]
[*]#1 - Primary NTFS - OK - WinXP MUST be installed on a Primary Partition, with boot flag set
[*]#2 - Primary - ext4 Ubuntu OS System Partition   /  Primary (although it does not need to be Primary, it can just as well be a logical partition)
[*]#3 - Extended partition
[*]#**5** - Logical - ext4 (maybe NTFS) Ubuntu /home (Data) partition *_**(CORRECTION: THE FIRST LOGICAL PARTITION IS ALWAYS NAMED /DEV/SDX5)**_*
[*]#**6** - Logical - NTFS Shared Data between WinXP & /LinuxUbuntu - unless you choose to make your separate /home Data partition NTFS, in which case WinXP could Read/write/execute/delete in it.
[*]#**7** - Logical NTFS? FAT32? - MS DOS (I'm not sure if this can be a logical or not, ntfs is better if it works on MS DOS partition, I don't know)
[*]#**8** Logical - Swap - [[COLOR=Navy]_See here_[/COLOR]]("https://help.ubuntu.com/community/SwapFaq")
[*]El resto - unallocated
[/LIST]
Setting up the separate /home or /Data partition is not difficult.  It can be done after you've successfully installed the system.  That way you'll have all the Linux/Ubuntu tools and be able to work on it with your new OS.


Primary partitons  = 3 (extended counts as a primary) (LIMIT of 4)
That reserves one unused Primary partition for future use.
Logical partiton limit = minimum 15, and more depending on type of drive, version & release # of OS.
Another excellent Ubuntu Official website [[COLOR=Blue]_Partitioning Basics website_[/COLOR]]("https://help.ubuntu.com/community/HowtoPartition/PartitioningBasics")

---

### Post by Coco999 on 2011-03-17
> **Hakunka-Matata said:**
> 320GB is a lot of disk space.  You most likely already know there is no one "right way" to partition the drive.  It's a personal choice except for some distinct absolute requirements.  [[COLOR=Navy]_This_[/COLOR]]("https://help.ubuntu.com/community/HowtoPartition") website should help.  

With the experience I have (intermediate level user I guess, but still LOTS more to learn) I feel comfortable recommending a few details.  This forum is an excellent place to resolve problems and learn, but the official Ubuntu website usually explains all the angles of any given theme, I go there if I get too many different suggestions here in the forums.

[LIST]
[*]#1 - Primary NTFS - OK - WinXP MUST be installed on a Primary Partition, with boot flag set
[*]#2 - Primary - ext4 Ubuntu OS System Partition   /  Primary (although it does not need to be Primary, it can just as well be a logical partition)
[*]#3 - Extended partition
[*]#4 - Logical - ext4 (maybe NTFS) Ubuntu /home (Data) partition
[*]#5 - Logical - NTFS Shared Data between WinXP & /LinuxUbuntu - unless you choose to make your separate /home Data partition NTFS, in which case WinXP could Read/write/execute/delete in it.
[*]#6 - Logical NTFS? FAT32? - MS DOS (I'm not sure if this can be a logical or not, ntfs is better if it works on MS DOS partition, I don't know)
[*]#7 Logical - Swap - [[COLOR=Navy]_See here_[/COLOR]]("https://help.ubuntu.com/community/SwapFaq")
[*]El resto - unallocated
[/LIST]
Setting up the separate /home or /Data partition is not difficult.  It can be done after you've successfully installed the system.  That way you'll have all the Linux/Ubuntu tools and be able to work on it with your new OS.


Primary partitons  = 3 (extended counts as a primary) (LIMIT of 4)
That reserves one unused Primary partition for future use.
Logical partiton limit = minimum 15, and more depending on type of drive, version & release # of OS.
Another excellent Ubuntu Official website [[COLOR=Blue]_Partitioning Basics website_[/COLOR]]("https://help.ubuntu.com/community/HowtoPartition/PartitioningBasics")

Thank you for your recommendations regarding partitions, they are very useful to me, but I must think the whole thing over. 

I didn't know the home separate partition could be NTFS. Then it can be accessed as well by WinXP, a definite advantage. But I insist. If I'm doing a fresh installation from scratch, there ought to be possible to force this during original installation. I'll look into the documentation to see if I can find something.

And now a philosophical doubt. I failed one way or other in all of my attempts to correct my problem of wrong updates. Perhaps I must start the computer in "recovery mode" to try and fix it.

---

### Post by Coco999 on 2011-03-17
> **Coco999 said:**
> If I'm doing a fresh installation from scratch, there ought to be possible to force this during original installation. I'll look into the documentation to see if I can find something.

I now saw a tutorial titled "Creating a separate home partition in Ubuntu during installation" All the secret is to specify the mounting point of the separate partition as  /home  and if it is formated as NTFS, hopefully I very easily achieve all that I want. Also I learned that ext4 is a later and better version of ext3. I wonder where do the programs stay.

---

### Post by Coco999 on 2011-04-04
Now my problem is fixed. I had already purchased a new 320 GB drive and copied all of my existing drive, just in case. But I didn't use it any further. This is what I did. I started the computer in Recovery Mood. I got a short menu with a few choices. I picked up dpkg Repair broken packages. This launched an extensive console operation with perhaps hundreds of pages on the screen, that were impossible to follow properly. However, it seemed that it was fetching information from the web. This process lasted for more than an hour with occasional choices I had to do. At the end of it I got the usual console prompt and I had to enter sudo halt to stop the machine and start again in the regular way. It had performed by itself all the necessary updates. It would now accept any new installations.

I wish to thank all the help I received, especially from Hakunka-Matata. I will wait a couple of days for any additional comments and then I will close the thread as solved

---

### Post by Dutch70 on 2011-04-04
Buen trabajo a los dos. 

¿No es un gran traductor Google ;)

---

### Post by Coco999 on 2011-04-04
> **Dutch70 said:**
> Buen trabajo a los dos. 

¿No es un gran traductor Google ;)

Gracias por el elogio. Pero si yo escribo en inglés como si Google me lo hubiera traducido, me gustaría saberlo. Pensaba que lo hacía un poco mejor.

---

### Post by Hakunka-Matata on 2011-04-05
> **Coco999 said:**
> Gracias por el elogio. Pero si yo escribo en inglés como si Google me lo hubiera traducido, me gustaría saberlo. Pensaba que lo hacía un poco mejor.

De Acuerdo Coco999, ¿llegerás algun Dia a los 1,000? Me alegro che, que ya estas corriendo con El pingüino loco. (Cambio de tema) -->  Estoy por comprar un terreno en el estado, Baja-California-Sur, Mexico, ciudad=Mulegé. No puedo decirle que fuerte son las ganas que tengo lograr el compro, hace muchisimos años que hay estado deseando un terreno en Mexico. A la edad mia, me pongo de menudo a veces frio mientras los inviernos, y la casa mia, aqui en el estado California, EE.UU. hace frio y mucho nieve (al altura de approximadamente los 4,640 pies) a los setenta millas Sur-Sur Oeste de Lago Tahoe.
Bueno, fue un placer communicar con otro que trabaja la electronica, Suerte, Adios, Vayasecon DIOS.

---

