---
title: "Somebody shoot Grub2!  How do I see what the menu is without rebooting!???"
date: 2011-02-03
forum: Installation &amp; Upgrades
---

### Post by carlos123 on 2011-02-03
Grub2 may indeed be a step up for some geeks but for geeks like me who just want to get a working system and be done with it and go on to more productive use of our computers...grub2 is an absolute pain in the butt!

I have read and read and Google and can't find an answer to a simple question. 

How in the world do I see what der Grub is producing for a menu so that I can copy and paste what is used for further debugging if the very menu used is a product of...well...grub2 running in place during a reboot?????!!  

I don't want to decipher goobly gook code to try and figure out what menu items are being used. 

Is there a simple, non-geeky, way to see what the grub2 menu in use IS?????  While running inside Ubuntu 10.10? 

Any help or input on this would be most appreciated.  

I sure don't want to start pulling the little remaining hair I have left trying to become a grub2 near expert before I get anything else done under Linux. 

Thanks. 

Carlos

---

### Post by carlos123 on 2011-02-03
Just wanted to subscribe to this thread now that I have set the no-subscribe default to instant notification. 

Sorry but I didn't want to spend even more time trying to figure out how to subscribe to a thread I wasn't subscribed to. 

Carlos

---

### Post by grahammechanical on 2011-02-03
I am not sure that I understand what you want. I do agree with you about wanting to be productive and not spend time studying things I really do not want to become an expert in.

GRUB2 seems to be designed to make life difficult for those of us who like to tinker and mess up our systems and then complain about how you need to be a geek to use Linux.

The main files for GRUB are here: /boot/grub/locale/grub.cfg   You cannot edit this file like you could with menu.lst. Instead you edit the files in /etc/grub.d/  then run update-grub2 which searches those files and updates grub.cfg.  Another file to look at is /etc/default/grub.

I hope all of this helps a little bit. Don't ask me to explain any of this. I am still awaiting my hair transplant from a recent attempt to get a image as part of the GRUB menu. It coincided with the graphic card having a nervous breakdown and I thought that I had really messed things up. I am still not over the panic it caused.

Regards.

---

### Post by carlos123 on 2011-02-03
Sorry to hear of your hair pulling troubles.  Linux is making great strides I think but the hair pulling quotient is still too high I think. 

The problem I am having is that my manual re-installation of grub is messing up my dual booting into Vista.  I restore Vista and it messes up the grub.  I restore grub2 by manually running grub-install and it messes up Vista booting. On and on it goes.  Normally I wouldn't care as I hardly ever use Windows but one of my clients needs me to do some work on Excel macros which is a Windows must.  And so I go back and forth, back and forth, back and forth and am tired of it and want to track down why my Vista partition is not booting up properly when I click on it through monsieur Grubby. 

Which means I have to copy the menu item for Vista that shows up in Grubby so that I can come here and hopefully get some input on which line in Mr. Grubby's menu is at fault. 

But...I can't quite copy said menu item when rebooting as my copy and paste hot keys don't quite work when booting up. 

But...since Monsieur Grubby generates this menu dynamically at boot time (apparently) I am stuck wondering how in the world I am going to see what that menu is????  

I mean short of looking through a bunch of Grubby gooblygook code in the various scripts that generate said Grubby menu so that I can reverse engineer the Grubby menu. 

Which is beyond anything anyone should have to do to see the...well...Grubby menu.  

I hope that makes sense as to what I am trying to do.  

I just want to see the Grubby menu in use when it boots from within a running Ubuntu instance so that I can copy and paste the Vista Grubby entry and come here and hopefully get some help.  

That's all I want to do. I don't want to study and analyze endless Grubbiness and Grub methodology to see the menu (not if I can help it).  

Carlos

---

### Post by Cavsfan on 2011-02-03
Edit this file with this command **gksu gedit /etc/default/grub** and set 
GRUB_TIMEOUT=60 (this is 60 seconds, you might want less).
That will display the menu for a period.
Also, check out the tut. in my sig.

---

### Post by carlos123 on 2011-02-03
Thanks Cavsfan but that does not solve my problem. 

I mean I can change the time out easily enough but for that matter I can simply press 'e' and have the Vista grub commands appear on the screen in vivid black and white for as long as I can to stare at them. So...increasing the time out of Grub does me no good with respect to easily being able to copy and paste them. 

I mean I can just copy them by pen and paper (I have a computer for goodness sakes...I shouldn't have to do that anymore!), reboot, enter into Ubuntu, open up the browser, start a new thread, enter them in manually one line at a time, and get the help I need that way but....

Can't anybody tell me if there is a way to see the menu grub uses and it's entries from within Ubuntu such that I can simply copy and paste the Vista entries that I need to get help with???

I mean didn't the powers that be who created that wonder known as Grub2 make provision for somebody wanting to "see" said menu entries without having to reboot endlessly so as to copy them down by pen and paper one line at a time????

Carlos

---

### Post by Cavsfan on 2011-02-03
Look in the tut in my sig. All of the files used by grub are in there:

```
grep menuentry /boot/grub/grub.cfg | cut -b 1-11 --complement | cut -d "'" -f1 | cut -d "\"" -f 1 | nl --starting-line-number=0
```That command will list the entries that you have.
And all of the files are in **/etc/grub.d/**

```
cavsfan@cavsfan-desktop:~$ cd /etc/grub.d/
cavsfan@cavsfan-desktop:/etc/grub.d$ ls -l
total 44
-rwxr-xr-x 1 root root 4444 2010-07-01 17:26 00_header
-rwxr-xr-x 1 root root 1550 2011-01-14 13:03 05_debian_theme
-rwxr-xr-x 1 root root  808 2011-01-12 21:51 06_custom
-rw-r--r-- 1 root root 4843 2010-11-23 16:38 10_linux
-rw-r--r-- 1 root root  918 2010-03-23 05:40 20_memtest86+
-rw-r--r-- 1 root root 6605 2010-07-01 17:26 30_os-prober
-rw-r--r-- 1 root root  214 2011-01-12 22:01 40_custom
-rw-r--r-- 1 root root  483 2010-07-01 17:26 README
cavsfan@cavsfan-desktop:/etc/grub.d$ 
```This is what my GRUB screen currently looks like. I don't have memtest and some other stuff displaying right now.

[[IMG]http://ompldr.org/tNzV0cQ[/IMG]]("http://ompldr.org/vNzV0cQ")

---

### Post by oldfred on 2011-02-03
I have done this:

I used drs305's command to limit ubuntu entries to two, turned off os_prober so it does not look for other systems and totally customized my 40_custom.
includes line to limit display to two, also hiding of windows recovery partition
Grub 2 Title Tweaks Thread -drs305
[http://ubuntuforums.org/showthread.php?t=1287602](http://ubuntuforums.org/showthread.php?t=1287602)
In /etc/default/grub I added this:
gksudo gedit /etc/default/grub
GRUB_DISABLE_OS_PROBER=true
or
sudo chmod a-x /etc/grub.d/30_os-prober

One way to fix the descriptions is to move the windows entries to 40_custom and edit at will.

[COLOR=DarkRed]#Copy the windows entries from this:
gedit /boot/grub/grub.cfg
#Copy them to and edit title:
gksudo gedit /etc/grub.d/40_custom
#Then do:
sudo update-grub[/COLOR]

---

### Post by JOHNNYG713 on 2011-02-03
You can try Grub Customizer, And see if that will give you what you want !
```
sudo add-apt-repository ppa:danielrichter2007/grub-customizer
sudo apt-get update
sudo apt-get install grub-customizer
```

---

### Post by Cavsfan on 2011-02-03
> **oldfred said:**
> I have done this:

I used drs305's command to limit ubuntu entries to two, turned off os_prober so it does not look for other systems and totally customized my 40_custom.
includes line to limit display to two, also hiding of windows recovery partition
Grub 2 Title Tweaks Thread -drs305
[http://ubuntuforums.org/showthread.php?t=1287602](http://ubuntuforums.org/showthread.php?t=1287602)
In /etc/default/grub I added this:
gksudo gedit /etc/default/grub
GRUB_DISABLE_OS_PROBER=true
or
sudo chmod a-x /etc/grub.d/30_os-prober

One way to fix the descriptions is to move the windows entries to 40_custom and edit at will.

[COLOR=DarkRed]#Copy the windows entries from this:
gedit /boot/grub/grub.cfg
#Copy them to and edit title:
gksudo gedit /etc/grub.d/40_custom
#Then do:
sudo update-grub[/COLOR]

This is basically what my tutorial does and it is listed in **drs305**'s GRUB2 Tutorial.
See the pic above: all I list are the most current kernel, recovery for that kernel and windows 7.

---

### Post by kansasnoob on 2011-02-03
> **grahammechanical said:**
> **[COLOR="Red"]I am not sure that I understand what you want.[/COLOR]** I do agree with you about wanting to be productive and not spend time studying things I really do not want to become an expert in.

GRUB2 seems to be designed to make life difficult for those of us who like to tinker and mess up our systems and then complain about how you need to be a geek to use Linux.

The main files for GRUB are here: /boot/grub/locale/grub.cfg   You cannot edit this file like you could with menu.lst. Instead you edit the files in /etc/grub.d/  then run update-grub2 which searches those files and updates grub.cfg.  Another file to look at is /etc/default/grub.

I hope all of this helps a little bit. Don't ask me to explain any of this. I am still awaiting my hair transplant from a recent attempt to get a image as part of the GRUB menu. It coincided with the graphic card having a nervous breakdown and I thought that I had really messed things up. I am still not over the panic it caused.

Regards.

Nor am I!

Rants seldom receive a problem solving response.

There are many different facets of any boot-loader.

Nowadays grub 2 gained a friend:

[http://ubuntuforums.org/showthread.php?p=10340183#post10340183](http://ubuntuforums.org/showthread.php?p=10340183#post10340183)

In combination with Startup Manager very few "manual" tweaks are needed.

However, if you truly yearn for legacy grub you can still revert:

[http://ubuntuforums.org/showthread.php?t=1298932](http://ubuntuforums.org/showthread.php?t=1298932)

Or do so the "official way":

[https://help.ubuntu.com/community/Grub2#Reverting%20to%20GRUB%20Legacy](https://help.ubuntu.com/community/Grub2#Reverting%20to%20GRUB%20Legacy)

How hard is that?

---

### Post by Cavsfan on 2011-02-03
Sorry **oldfred**, I didn't realize that was you! :redface:

---

### Post by Cavsfan on 2011-02-03
> **kansasnoob said:**
> Nor am I!

Rants seldom receive a problem solving response.

There are many different facets of any boot-loader.

Nowadays grub 2 gained a friend:

[http://ubuntuforums.org/showthread.php?p=10340183#post10340183](http://ubuntuforums.org/showthread.php?p=10340183#post10340183)

In combination with Startup Manager very few "manual" tweaks are needed.

However, if you truly yearn for legacy grub you can still revert:

[http://ubuntuforums.org/showthread.php?t=1298932](http://ubuntuforums.org/showthread.php?t=1298932)

Or do so the "official way":

[https://help.ubuntu.com/community/Grub2#Reverting%20to%20GRUB%20Legacy](https://help.ubuntu.com/community/Grub2#Reverting%20to%20GRUB%20Legacy)

How hard is that?

You definitely do not want to go back to grub legacy....

---

### Post by carlos123 on 2011-02-03
Thanks for the code cavsfan.  Much appreciated.  I would have never figured that one out in a million hours.  

```
grep menuentry /boot/grub/grub.cfg | cut -b 1-11 --complement | cut -d "'" -f1 | cut -d "\"" -f 1 | nl --starting-line-number=0
```That command will list the entries that you have.
And all of the files are in **/etc/grub.d/**
[CODE]

Carlos

---

### Post by carlos123 on 2011-02-03
> **kansasnoob said:**
> 
Rants seldom receive a problem solving response.


True enough but you will have to forgive me for airing what I was feeling and thinking about the new super "improved" Monsieur Grubby.  It's tough to speak without expressing something of what fills my heart about a subject especially when one is very frustrated and set back by a supposedly new and improved something or other that in fact makes things worse for what I am trying to do.  

Carlos

---

### Post by Cavsfan on 2011-02-04
> **carlos123 said:**
> Thanks for the code cavsfan.  Much appreciated.  I would have never figured that one out in a million hours.  

```
grep menuentry /boot/grub/grub.cfg | cut -b 1-11 --complement | cut -d "'" -f1 | cut -d "\"" -f 1 | nl --starting-line-number=0
```That command will list the entries that you have.
And all of the files are in **/etc/grub.d/**

Carlos

Glad to help! That is not my code though. I copied it from drs305. He knows GRUB2. If you ever need help in the future,
just look for his guides and tutorials on GRUB2.

That command only lists the menu entries that are currently executable. For example if you made **/etc/grub.d/20_memtest86+** unexecutable and ran **sudo update-grub**, 
The menu entries for memtest86 would not be listed in the output of that command nor would they appear at bootup.

Also, if you feel this issue is solved, please mark the thread as solved in Thread tools at the top.

Peace! :)

---

### Post by Quackers on 2011-02-04
If installing grub "messes up" your vista boot, then something is wrong. If you are inclined to find out you could go to the site below and download the boot script to your DESKTOP and then open up a terminal (Applications > Accessories > terminal) and run
```

sudo bash ~/Desktop/boot_info_script*.sh
```

This will produce a results.txt file on your desktop. Please copy the contents of that file and paste them in your next post between CODE tags. For CODE tags click on New Reply (not quick reply)and then click on the # symbol in the toolbar.
This will give a full overview of your current system.
Thanks.

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

BTW
```
cat /boot/grub/grub.cfg | grep menuentry
```

always worked well for me, for viewing what the grub menu will include (another one of drs305's :-) )

---

### Post by carlos123 on 2011-02-04
Thanks Cavsfan but I finally had a chance to run your code and that doesn't work for me.  Likewise none of the other code here does either. 

While that shows me what is on the menu what I am looking for is a way to see what commands are being run when a particular Grub menu item is executed.  Underneath. And furthermore to view them in such a way that I can copy them while being inside a running Ubuntu. 

Commands like chainloader +1, set root='(hd0,msdos1)' that type of stuff.  

So this issue is not solved yet.  

I do appreciate the input though. 

Carlos

---

### Post by carlos123 on 2011-02-04
Now THAT is what I was looking for!! Thanks Quackers!  

Here is the listing (including the menu item commands...in the context of a bunch of other stuff but at least I can see them and copy and paste them to my hearts content).  

I did manage to boot up Vista by the way.  I got frustrated, did an 'e' to edit the Vista menu item and changed hd0 to hd1 and it booted for some reason.  Weird. 

Anyway here is the code produced by that script.  

```

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for (,msdos5)/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /boot/bcd /Windows/System32/winload.exe

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr

sda3: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   /grub/grub.cfg /grub/core.img /boot/grub/core.img

sda6: _________________________________________________________________________

    File system:       reiserfs
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /etc/fstab

sda7: _________________________________________________________________________

    File system:       reiserfs
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048   149,626,871   149,624,824   7 HPFS/NTFS
/dev/sda2         290,852,864   309,532,663    18,679,800   7 HPFS/NTFS
/dev/sda3         309,532,672   312,580,095     3,047,424  82 Linux swap / Solaris
/dev/sda4         149,628,926   290,852,863   141,223,938   5 Extended
/dev/sda5         149,628,928   150,650,879     1,021,952  83 Linux
/dev/sda6         150,652,928   209,020,927    58,368,000  83 Linux
/dev/sda7         209,022,976   290,852,863    81,829,888  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        C21869311869259F                       ntfs                                     
/dev/sda2        784C9E514C9E0A50                       ntfs       RECOVERY                      
/dev/sda3        afab7820-d00e-452f-b3d1-58d9b3081490   swap                                     
/dev/sda4: PTTYPE="dos" 
/dev/sda5        5caf90fd-b7ff-465c-a448-47aa65b16651   ext4                                     
/dev/sda6        b5580f6f-a82b-40f5-94ff-a62e6c18fcb2   reiserfs                                 
/dev/sda7        1b635ec3-685a-4fb5-981d-e000472089cd   reiserfs                                 
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda6        /                        reiserfs   (rw)
/dev/sda5        /boot                    ext4       (rw,commit=0)
/dev/sda7        /home                    reiserfs   (rw)


============================= sda5/grub/grub.cfg: =============================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  set have_grubenv=true
  load_env
fi
set default="0"
if [ "${prev_saved_entry}" ]; then
  set saved_entry="${prev_saved_entry}"
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z "${boot_once}" ]; then
    saved_entry="${chosen}"
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n "${have_grubenv}" ]; then if [ -z "${boot_once}" ]; then save_env recordfail; fi; fi
}

function load_video {
  insmod vbe
  insmod vga
}

insmod part_msdos
insmod reiserfs
set root='(hd0,msdos6)'
search --no-floppy --fs-uuid --set b5580f6f-a82b-40f5-94ff-a62e6c18fcb2
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos5)'
search --no-floppy --fs-uuid --set 5caf90fd-b7ff-465c-a448-47aa65b16651
set locale_dir=($root)/grub/locale
set lang=en
insmod gettext
if [ "${recordfail}" = 1 ]; then
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
menuentry 'Ubuntu, with Linux 2.6.35-25-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set 5caf90fd-b7ff-465c-a448-47aa65b16651
	linux	/vmlinuz-2.6.35-25-generic root=UUID=b5580f6f-a82b-40f5-94ff-a62e6c18fcb2 ro   quiet splash
	initrd	/initrd.img-2.6.35-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-25-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set 5caf90fd-b7ff-465c-a448-47aa65b16651
	echo	'Loading Linux 2.6.35-25-generic ...'
	linux	/vmlinuz-2.6.35-25-generic root=UUID=b5580f6f-a82b-40f5-94ff-a62e6c18fcb2 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/initrd.img-2.6.35-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set 5caf90fd-b7ff-465c-a448-47aa65b16651
	linux	/vmlinuz-2.6.35-24-generic root=UUID=b5580f6f-a82b-40f5-94ff-a62e6c18fcb2 ro   quiet splash
	initrd	/initrd.img-2.6.35-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set 5caf90fd-b7ff-465c-a448-47aa65b16651
	echo	'Loading Linux 2.6.35-24-generic ...'
	linux	/vmlinuz-2.6.35-24-generic root=UUID=b5580f6f-a82b-40f5-94ff-a62e6c18fcb2 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/initrd.img-2.6.35-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set 5caf90fd-b7ff-465c-a448-47aa65b16651
	linux	/vmlinuz-2.6.35-22-generic root=UUID=b5580f6f-a82b-40f5-94ff-a62e6c18fcb2 ro   quiet splash
	initrd	/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set 5caf90fd-b7ff-465c-a448-47aa65b16651
	echo	'Loading Linux 2.6.35-22-generic ...'
	linux	/vmlinuz-2.6.35-22-generic root=UUID=b5580f6f-a82b-40f5-94ff-a62e6c18fcb2 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/initrd.img-2.6.35-22-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set 5caf90fd-b7ff-465c-a448-47aa65b16651
	linux16	/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos5)'
	search --no-floppy --fs-uuid --set 5caf90fd-b7ff-465c-a448-47aa65b16651
	linux16	/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Vista (loader) (on /dev/sda1)" {
	insmod part_msdos
	insmod ntfs
	set root='(hd0,msdos1)'
	search --no-floppy --fs-uuid --set c21869311869259f
	chainloader +1
}
menuentry "Windows Vista (loader) (on /dev/sda2)" {
	insmod part_msdos
	insmod ntfs
	set root='(hd0,msdos2)'
	search --no-floppy --fs-uuid --set 784c9e514c9e0a50
	chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

### BEGIN /etc/grub.d/41_custom ###
if [ -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###

=================== sda5: Location of files loaded by Grub: ===================


  76.7GB: boot/grub/core.img
  76.8GB: grub/core.img
  76.8GB: grub/grub.cfg
  76.6GB: initrd.img-2.6.35-22-generic
  76.6GB: initrd.img-2.6.35-24-generic
  76.6GB: initrd.img-2.6.35-25-generic
  76.6GB: vmlinuz-2.6.35-22-generic
  76.6GB: vmlinuz-2.6.35-24-generic
  76.6GB: vmlinuz-2.6.35-25-generic

=============================== sda6/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda6 during installation
UUID=b5580f6f-a82b-40f5-94ff-a62e6c18fcb2 /               reiserfs defaults        0       1
# /boot was on /dev/sda5 during installation
UUID=5caf90fd-b7ff-465c-a448-47aa65b16651 /boot           ext4    defaults        0       2
# /home was on /dev/sda7 during installation
UUID=1b635ec3-685a-4fb5-981d-e000472089cd /home           reiserfs defaults        0       2
# swap was on /dev/sda3 during installation
UUID=afab7820-d00e-452f-b3d1-58d9b3081490 none            swap    sw              0       0

=================== sda6: Location of files loaded by Grub: ===================


  77.2GB: initrd.img
  77.2GB: initrd.img.old
  77.1GB: vmlinuz
  77.1GB: vmlinuz.old

```

And here is the code I use to reinstall Grub2 manually after I restore Vista booting using the Vista Recovery CD.

----------------------------------------------------------
$ sudo mount /dev/sda6 /mnt 
$ sudo mount /dev/sda5 /mnt/boot
$ sudo grub-install --root-directory=/mnt/ /dev/sda
----------------------------------------------------------

When I run the above code to restore Grub2 to the MBR it messes up the ability to get into Vista from Grub2. 

The reason I am running that code is that something got messed up to begin with and I needed to restore Vista booting which of course messes up Grub2 and not wanting to reinstall Ubuntu and wipe out what I had already installed there...I Googled around and found the above commands. 

/dev/sda6 corresponds to my / mount point. 
/dev/sda5 corresponds to a separate /boot mount point (which is also a separate partition...don't remember why I did it that way but I always have). 

Any insight anyone might care to share with me as to why changing hd0 to hd1 in the above Grub2 menu commands for Vista causes it to boot while leaving it at hd0 does not would be appreciated.  

Is there something wrong with my manual reinstallation of Grub2 commands such that the wrong partition is indicated in the resulting menu commands for Vista?

Carlos

---

### Post by vidtek on 2011-02-04
> When I run the above code to restore Grub2 to the MBR it messes up the ability to get into Vista from Grub2. 

The reason I am running that code is that something got messed up to begin with and I needed to restore Vista booting which of course messes up Grub2 and not wanting to reinstall Ubuntu and wipe out what I had already installed there...I Googled around and found the above commands. 

/dev/sda6 corresponds to my / mount point. 
/dev/sda5 corresponds to a separate /boot mount point (which is also a separate partition...don't remember why I did it that way but I always have). 

Any insight anyone might care to share with me as to why changing hd0 to hd1 in the above Grub2 menu commands for Vista causes it to boot while leaving it at hd0 does not would be appreciated.  

Is there something wrong with my manual reinstallation of Grub2 commands such that the wrong partition is indicated in the resulting menu commands for Vista?

Carlos

Carlos-

I share your pain with Grub2, I simlpy gave up and installed LILO and hey presto, my hair is back.

I think the reason behind Grub2 was to allow the UUID system to operate automatically which in theory is really good.
Unfortunately for most of us the implementation just screwed with our heads.

IMHO they really should not have included it in major distributions until it was easy enough for simpletons like myself to change and mess with it.

There are 3rd party apps which make it easier to use, but they really should not have been necessary, these should have been part of the package.

It's easy to criticise these decisions after the event, and see where they went wrong, but the chasm between the developers point of view and the average user's is so great that it's not surprising these things happen.

One of the major problems is that there are several different naming conventions for hard discs.

**Bios:** hd0,hd1,hd2 etc
**Windows:** Location 0 (Channel 0, Target 0, Lun 0)and c: d: e: etc.
**Linux:** sda,sdb,sdc etc

When you try to mix os's and multi-boot it all gets too complicated, which is why UUID's arrived on the scene, so no matter which sata channel or ide channel, each partition will be recognised by it's own unique UUID and is able to be booted from that partition.

(this is the way I understand it, if anyone knows better, please correct me!!)


Best of luck Tony.

---

### Post by oldfred on 2011-02-05
The boot script parses boot.ini from XP, so we can see which drive windows is booting from. But with Vista/7 it does not parse the BCD hive to see what Vista thinks it is booting from. Did  you originally install Vista to a second drive? You may need to reset Vista's BCD or other boot parameters so it knows it is one drive 0.

Use BCDedit to review entries.

[http://www.sevenforums.com/tutorials/2676-bcdedit-how-use.html](http://www.sevenforums.com/tutorials/2676-bcdedit-how-use.html)

Some advanced BCD rebuild, Vista post #17 on:
[http://ubuntuforums.org/showthread.php?t=1426103](http://ubuntuforums.org/showthread.php?t=1426103)
[http://neosmart.net/wiki/display/EBCD/Recovering+the+Vista+Bootloader+from+the+DVD](http://neosmart.net/wiki/display/EBCD/Recovering+the+Vista+Bootloader+from+the+DVD)

---

### Post by carlos123 on 2011-02-05
Hi Olfred, 

> **oldfred said:**
> The boot script parses boot.ini from XP, so we can see which drive windows is booting from. But with Vista/7 it does not parse the BCD hive to see what Vista thinks it is booting from. Did  you originally install Vista to a second drive? You may need to reset Vista's BCD or other boot parameters so it knows it is one drive 0.


Your talking Greek to me Olfred :).  I do not know anything about boot.ini, BCD hive, or boot parameters.  As for my Vista...it came that way from the factory.  To be sure I have restored Vista from the recovery partition once and perhaps the original owner (who only had the laptop for about a month) also did the same to wipe it clean before selling it to me but other than that...it has not been istalled to a second hard drive. 

> 
Use BCDedit to review entries.

[http://www.sevenforums.com/tutorials/2676-bcdedit-how-use.html](http://www.sevenforums.com/tutorials/2676-bcdedit-how-use.html)

Some advanced BCD rebuild, Vista post #17 on:
[http://ubuntuforums.org/showthread.php?t=1426103](http://ubuntuforums.org/showthread.php?t=1426103)
[http://neosmart.net/wiki/display/EBCD/Recovering+the+Vista+Bootloader+from+the+DVD](http://neosmart.net/wiki/display/EBCD/Recovering+the+Vista+Bootloader+from+the+DVD)

I will certainly play around with BCDedit as you suggest Olfred.  Thanks very much for the added tip!

Carlos

---

