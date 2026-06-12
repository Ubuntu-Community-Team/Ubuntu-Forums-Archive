---
title: "Ubuntu &amp; Vista Dual Boot (Can't Access Vista)"
date: 2010-07-07
forum: Installation &amp; Upgrades
---

### Post by Smallwheels on 2010-07-07
I'm still new to OS manipulation. I've followed instructions and things aren't going well. I'll include some things from other threads that are pertinent to this problem.

I reinstalled Vista successfully on my HP AMD 2.3 GHz Sempron 32 bit system. I reloaded my programs and files then defragmented the computer. 

Next I installed the ISO disc and several hours later followed the instructions on the screen to partition the drive. Of the 320 GB I gave Vista 125 of which 85 plus 11.9 were in use by the computer. I set the remainder to Ubuntu. After another couple of hours I completed the instructions and told it to restart using the button that instructed me to do so.

When I did there was an error message and a gigantic litany of lines repeating the same error only with different numbers at the end. I have no idea what they mean. Here is what was on the screen:

[ 6324 . 635578 ] end_request: I/O error, dev sr0, sector 506312

As I said, that repeated over and over with just the last number changed for each line. The numbers were almost sequential. I had to turn off the computer using the power button. When it restarted with Ubuntu I entered my password and the desktop appeared. Soon afterward a message opened about updates. I loaded them and that took nearly two hours. 

The computer was restarted the next day and Ubuntu worked--sort of. When I was in Ubuntu during this set of problems I tried using Firefox to go to a site. It was so slow in getting to it I felt it might be the fault of the site. Then I went to two known sites (yahoo.com and apple.com). Both took almost a minute for Firefox to get to them (54 seconds for yahoo.com). I can't use Ubuntu if that can't be fixed. While at the Apple site I typed in the yahoo address and hit enter then the blue arrow. At the bottom of the screen the status bar kept showing more and more things loading on the Apple site. It was as if the browser didn't get the information from the address bar after I clicked enter. Eventually it did switch to the yahoo site. That is unacceptable. I know that can't be normal behavior. I'll need to get help with that later. It actually worked faster running from the live CD.

[SIZE="5"]Here's the immediate problem;[/SIZE]
I needed to get to a web form that works with IE. I tried to access Vista and couldn't. 

At the start I clicked the esc key until I had the chance to choose an OS. Before I just though one of those other choices was for loading Vista. It turns out they aren't.

I selected Windows Vista (loader) (on/dev/sda2)

Next the black screen changed to the words Windows is loading and there was a progress bar on the bottom of the screen.

There was a very brief view of the normal Vista loading progress bar and it disappeared. A blue screen opened and stayed for a while. An old style Windows dialog box opened that said Systems Recovery Options. There was just one thing to check and it was Choose a recovery tool.

The list on the next dialogue was: Startup Repair, System Restore, Windows Complete PC Restore, Windows Memory Diagnostic, Command Prompt, Recovery Manager.

I selected Startup Repair. A progress bar opened and took a few minutes to finish. After this happened I clicked finish and it restarted the computer with no change. 

I shut down the computer again after going to Ubuntu. On the next startup I didn't select anything after pressing the esc key so I could write down my choices in case someone here could tell me what they mean. When I was finished writing them I tried to select one and none of the keyboard keys worked. The arrows or enter keys had no effect. I shut it down with the power button. 

Here were my choices at the startup after pressing Esc. 

> HDD Group
T332 0813AS
>CD ROM Group
TSSTcorp CDDVDW TS-H653R

Before I would select the second one because it took me to Ubuntu. When it would open it would give me many choices of Ubuntu related to recovery or other things. I just selected the one that didn't seem like it was for repair. The last two were for Vista but I didn't even pay attention to them. I just assumed they were for loading Vista. One is for recovery and the other was for some other type of diagnostic. Neither opens Vista. 

I need to get to Vista to use IE at a web site that doesn't work with Firefox, or Safari. 

I took some photos (not screen shots) of most of the screens listed above. They are at this link in my Box.net account. [http://www.box.net/shared/rlx1g12vfj](http://www.box.net/shared/rlx1g12vfj) 

Ubuntu has reloaded a couple of times and Firefox is still as slow as molasses. I really want to straighten this out because Ubuntu seems like a great adventure for someone like me who knows nothing about using the command line. I really want to make the move to open source operating systems and just keep Vista around for synching my future iPad. Once there are open source programs that will synch to iPads and work with apps I'll go free. :P

Please help. Remember I'm a noobie.

Thank you.

Michael J. Beninate
[www.MySpace.com/Beninate](www.MySpace.com/Beninate)

---

### Post by snake_pliskin_x on 2010-07-07
Hmm.... I have a similar setup to yours with no problems. I have Windows XP and Ubuntu 9.10 dual booted on my Acer. It was pretty straight forward. I would wipe the hard drive and start from scratch. After that reinstall Vista as if you were just running it and not a dual boot. Then load the ubuntu up and go to setup a manual partition and adjust the hard drive to Vista and Ubuntu. The error stuff is nothing, just let the computer run untill its finished and ubuntu is loaded. Once there go to the update manager and update it which does take a while. After that everything should work good and the startup screen will look like the your SANY0039. PIC which from there you will either choose Vista or ubuntu 2.6.32-23 generic and hit enter.

---

### Post by Smallwheels on 2010-07-08
snake_pliskin_x everything you described I did already. I started with a clean install of Vista then loaded Ubuntu. Vista is not one of the choices when pressing esc. There are only recovery or loader choices for Windows. I've tried both and neither will open a version of Vista. 

Michael J. Beninate
[www.MySpace.com/Beninate](www.MySpace.com/Beninate)

---

### Post by oldfred on 2010-07-08
Post this so we can see what is installed where. You can download from liveCD.

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.

---

### Post by Smallwheels on 2010-07-14
OK it has been a few days. I got the time and followed the instructions as best as I could. For a while I couldn't get Ubuntu to connect to the internet using Firefox. I restarted the computer twice and somehow the connection was successful though infinitely slow. 

Here is a copy of the results dot txt file

#                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /boot/bcd

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   243,916,676   243,916,614   7 HPFS/NTFS
/dev/sda2         599,995,620   625,137,344    25,141,725   7 HPFS/NTFS
/dev/sda3         243,916,798   599,994,367   356,077,570   5 Extended
/dev/sda5         243,916,800   587,925,503   344,008,704  83 Linux
/dev/sda6         587,927,552   599,994,367    12,066,816  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        02F0851FF0851A55                       ntfs       HP                            
/dev/sda2        949CA48C9CA46A86                       ntfs       FACTORY_IMAGE                 
/dev/sda3: PTTYPE="dos" 
/dev/sda5        e2eac281-e91f-4d00-84fc-5dcd8a496bb7   ext4                                     
/dev/sda6        b5532d4b-1543-4f65-aae7-775d121dcb96   swap                                     
/dev/sda: PTTYPE="dos" 
error: /dev/sdb: No medium found
error: /dev/sdc: No medium found
error: /dev/sdd: No medium found
error: /dev/sde: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda5        /                        ext4       (rw,errors=remount-ro)


=========================== sda5/boot/grub/grub.cfg: ===========================

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
set root='(hd0,5)'
search --no-floppy --fs-uuid --set e2eac281-e91f-4d00-84fc-5dcd8a496bb7
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
set root='(hd0,5)'
search --no-floppy --fs-uuid --set e2eac281-e91f-4d00-84fc-5dcd8a496bb7
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
menuentry 'Ubuntu, with Linux 2.6.32-23-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set e2eac281-e91f-4d00-84fc-5dcd8a496bb7
    linux    /boot/vmlinuz-2.6.32-23-generic root=UUID=e2eac281-e91f-4d00-84fc-5dcd8a496bb7 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-23-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set e2eac281-e91f-4d00-84fc-5dcd8a496bb7
    echo    'Loading Linux 2.6.32-23-generic ...'
    linux    /boot/vmlinuz-2.6.32-23-generic root=UUID=e2eac281-e91f-4d00-84fc-5dcd8a496bb7 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set e2eac281-e91f-4d00-84fc-5dcd8a496bb7
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=e2eac281-e91f-4d00-84fc-5dcd8a496bb7 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set e2eac281-e91f-4d00-84fc-5dcd8a496bb7
    echo    'Loading Linux 2.6.32-21-generic ...'
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=e2eac281-e91f-4d00-84fc-5dcd8a496bb7 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set e2eac281-e91f-4d00-84fc-5dcd8a496bb7
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set e2eac281-e91f-4d00-84fc-5dcd8a496bb7
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Recovery Environment (loader) (on /dev/sda1)" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 02f0851ff0851a55
    drivemap -s (hd0) ${root}
    chainloader +1
}
menuentry "Windows Vista (loader) (on /dev/sda2)" {
    insmod ntfs
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set 949ca48c9ca46a86
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda5 during installation
UUID=e2eac281-e91f-4d00-84fc-5dcd8a496bb7 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=b5532d4b-1543-4f65-aae7-775d121dcb96 none            swap    sw              0       0

=================== sda5: Location of files loaded by Grub: ===================


 256.0GB: boot/grub/core.img
 273.4GB: boot/grub/grub.cfg
 256.0GB: boot/initrd.img-2.6.32-21-generic
 256.0GB: boot/initrd.img-2.6.32-23-generic
 125.5GB: boot/vmlinuz-2.6.32-21-generic
 256.0GB: boot/vmlinuz-2.6.32-23-generic
 256.0GB: initrd.img
 256.0GB: initrd.img.old
 256.0GB: vmlinuz
 125.5GB: vmlinuz.old
=======Devices which don't seem to have a corresponding hard drive==============

sdb sdc sdd sde 

===========================

I see the word error a few times and I don't know what it means. I hope it gives a clue why I can't choose Vista during the OS selection when I first turn on the computer. Does it give a clue why the internet connection is so slow?

Thanks for the help. I've been considering just going back to Vista in the short term using my recovery discs just so I can get online to a site that requires IE (Argh).

As long as someone gives me the exact things to type into the terminal I'll be able to do it. Getting this results.txt thing was my first successful Ubuntu terminal command. Yeaa!

---

### Post by oldfred on 2010-07-14
I do not see anything wrong other than it labeled the Vista and Vista recovery backwards. For some reason we have seen this a lot. Something about windows or osprober is not identifing the partitions correctly. 

If you boot the windows recovery does it boot into your normal Vista install?

---

### Post by Smallwheels on 2010-07-16
Thank you for your insight oldfred. I could have sworn that I tried each of the Vista choices at the boot startup and both took me to the recovery process. Is it possible that running that diagnostic file straightened things out?

I did select the recovery section for Vista and it did open. Is there a way to fix this incorrect labeling problem? By having these things mislabeled does that mean that the partitions are the incorrect sizes? 

Once this is handled I can say that this problem was handled successfully. 

I still have problems with Firefox loading pages or sites extremely slowly. I'll look for that fix in a different thread and if I can't find it I'll start a new one. Right now I'm using my Mac because of the slowness of Firefox. I should check to see if the same problem is happening in Vista. The Mac is connected to the same modem and there are no problems.

---

### Post by oldfred on 2010-07-16
There is not a easy way in grub2 to change descriptions.

I used drs305's command to limit ubuntu entries to two, turned off os_prober so it does not look for other systems and totally customized my 40_custom.
Copy the windows entries from this:
gedit /boot/grub/grub.cfg
Copy them to and edit :
gksudo gedit /etc/grub.d/40_custom

includes line to limit display to two
Grub 2 Title Tweaks Thread -drs305
[http://ubuntuforums.org/showpost.php...54&postcount=1](http://ubuntuforums.org/showpost.php...54&postcount=1)

I added this :
gksudo gedit /etc/default/grub:
GRUB_DISABLE_OS_PROBER=true

after all changes"
sudo update-grub

They may have changed the above command on disabling the os prober. If it does not work. Make the file not executable.

sudo chmod a-x /etc/grub.d/30_os-prober

---

### Post by Smallwheels on 2010-07-16
Oldfred I really appreciate you getting me going with Ubuntu. It is so cool to be able to start this new computing adventure. Your knowledge is impressive. My problem is I'm still in Ubuntu Linux kindergarten. I know how to read and follow instructions. Since I don't know so many of the definitions of the things in your post I'm just left doing nothing. Simpler instructions (baby steps) would be easier to follow. For instance, Open this window, click this button, type this after the words..., close that window, open this next one and hit enter. 

Stuff like that I can follow.

I suppose I could skip doing this if you could answer my other question. "By having these things mislabeled does that mean that the partitions are the incorrect sizes?" If the only thing wrong is the label then I can just click the one that works. Nobody else uses this computer so it won't be a problem for others. 

Which version of Ubuntu should I choose when starting? I have a 32 bit AMD chip. Do any of these choices make a difference? Here is a link to a photo of what is on the screen: [http://www.box.net/shared/rlx1g12vfj#/shared/rlx1g12vfj/1/46348886/463143064/1](http://www.box.net/shared/rlx1g12vfj#/shared/rlx1g12vfj/1/46348886/463143064/1) 
One is 2.6.32-23-generic and the other is 2.6.32-21-generic. Why so many choices? I understand that there are two for Vista (loader and recovery), but why four for Ubuntu?

By the way I set up the mail program with plenty of trial and error. In the FAQ for that mail program there are many people with problems using it with big issues. Is it better to just go directly to my mail.live.com account using the browser? It has fewer features but it works all the time.

---

### Post by oldfred on 2010-07-16
The steps I gave are about as simple (I did say it was not easy) as I can as you can copy and paste onto the command line to run them.

If no one else uses it and you will be be confused, you do not have to change. Eventually they will fix it but it may not be until the next release.

Your menu is normal. You should keep two kernels, the newest is on top. If ever there is an issue with a new kernel then you can boot the older one as it was the one you used before the update.

You can houseclean kernels in synaptic but do not delete the one you are using or you will not be able to reboot.

---

### Post by Smallwheels on 2010-07-21
Thanks again oldfred. I'm sure you can tell by my last reply that I really don't know what I'm doing. 

First you said I used drs305's command. I don't know what that is. I could read os_prober and guess what that is. Don't know what 40_custom is either.

There is an interesting phenomena that happens whenever someone reads a word or symbol they don't understand. They go blank. Have you ever read a paragraph in a book and stopped at the end and wondered what you had just read? That occurs when you've passed a word or symbol you don't understand. You need to get it defined before moving on, otherwise you will not understand what was written or you will probably carry on and if you are doing some type of work related to what you've just studied you will likely make errors.

Fortunately for me I've been trained in how to recognize some barriers to study and can figure my way around it by defining terms and making things clear before moving on. With computer terminology and communicating on forums I don't have that luxury. So I just do my best. Since it isn't related to work it is OK if I make mistakes until I get it right. 

Should the first thing I do is to copy and paste: gedit /boot/grub/grub.cfg ?

You next say to copy them to and edit : I don't know what that means. Do you mean that after pressing enter after pasting in the above command, THEN I should paste in: gksudo gedit /etc/grub.d/40_custom ?

Actually I should just give up doing this and get help with something that you mentioned in an earlier post. 

Today when I turned on the computer I just let it select the first boot choice and hit enter. When it did that it started and I used the mouse to click my name so I could sign in. The problem was that the keyboard didn't work! It was plugged in. 

What I had to do was restart the computer and then at the choice for boot I moved the cursor down three lines to the next choice, then hit enter. That allowed me to log in using the keyboard. Ubuntu opened.

What happened? You mentioned that it is good to keep the second kernal. Well I think that is what I chose to get it to open. 

The first choice was Ubuntu, with Linux 2.6.32-23-generic This is the one I was using until today.
The next line is the same thing labeled recovery mode.
The next choice is Ubuntu, with Linux 2.6.32-21-generic. This is the one that allowed me to open Ubuntu by turning on the keyboard. 

I was hoping to move on to fixing Firefox so it loads pages at a normal speed. I'd rather have this boot up thing handled so that I can just let the computer boot without me needing to select the third line down. Having the top line automatically selected is more convenient. That way I can just switch on the computer in the morning and walk away from it while I get ready for work. When I'm ready to come back to the computer I can just type in my password and start.

What can I do to handle this first?

Thanks for the help.

---

### Post by linux18 on 2010-07-21
For firefox, i have one question: are you using wifi? if so, check and make sure you aren't using someone else's connection. If not, check if ethernet is faster. Post the output of  " ping [www.google.com](www.google.com) " in both cases. 
Welcome to ubuntuforums and the wonderful world of linux, in a few years, you will be an expert in all areas of computing and people will come to you for help ( this happens in 99% of cases )

---

### Post by Smallwheels on 2010-07-21
Hello linux18. Thank you for your encouragement. I'm using a desktop computer and it doesn't have WiFi or Bluetooth. It connects using a USB cable to my DSL modem. 

I got the idea to download the new Opera browser and install it. That way if I needed to uninstall Firefox I would have a way to get to the web and reinstall it. Well Opera is just a bit faster than Firefox which is still slow. 

I can be on a web site and then type in a new address then hit enter. I count to at least twenty-five before the window shifts to open the next site. Often it takes longer. 

Once on a site like Yahoo it will load other pages within Yahoo a bit faster but not at a normal DSL speed. So the problem isn't with Firefox or Opera. Some other thing is causing them to be slow. What could that be? 

Just another thing to ask while on the topic of browsing while waiting to handle the boot question, What do I need to download so that quicktime videos appear on the screen? Videos on Apple.com don't play without it. I also couldn't get a video to play on Yahoo.com. They use flash but I have the latest version of flash installed. I right clicked the video that wasn't playing and somehow clicked something else that brought me to a page where it identified my flash player and said I have the latest version successfully installed.

Videos at Youtube.com play fine.

---

### Post by oldfred on 2010-07-21
Just to get you started.

Copy the windows entries from this, first copy these commands onto your terminal, the first will open a read only copy of grub.cfg
 - Applications, accessories, terminal:
```
gedit /boot/grub/grub.cfg
```  Then run this command that will open another window as sudo which gives you admin rights to work on a system file (gksudo for graphical applications) :
```
gksudo gedit /etc/grub.d/40_custom
```From the first window, Scroll down and Copy the two windows stanzas, change to the second window and paste into the file 40_custom after whatever it in it already. Edit to have the correct descriptions or anything you would like, just change the title line -nothing else.

Run this command to copy into your grub.cfg. You will then have two sets of entries. the original and your edit new versions. After you have tested that it works we can delete the other entries in you grub.cfg.

```
sudo update-grub
```As to your speed issue. You are using USB? Can you use ethernet? Sometimes they set you up with USB but ethernet is faster.

---

### Post by Smallwheels on 2010-07-25
Oldfred thank you for breaking this down for me. Here is what I did; I typed in the first command in the terminal window. When I pressed enter a new window opened. Its title on the top of the page said grub.cfg (/boot) - gedit. This window has nothing in it at all. It is just white. 

Not knowing anything about it I just continued and typed in your second command into the terminal. When I hit enter nothing happened. So when your instructions say to copy in Stanzas it can't be done because the first window is blank without a scroll bar and secondly I don't know what stanzas means in Linux speak. In music the definition is clear to me. 

I did space the text in the command correctly as I saw it. Perhaps I'll experiment with leaving out some spaces or adding spaces until I receive your next instructions. 

As an aside, the computer did boot directly from the first boot menu choice today. The keyboard did work properly. I didn't need to restart it and select the second Ubuntu kernel. I don't know why it happened but it did.

About the Firefox and Opera browsers being so slow. I do have this computer dual booted with Vista. When operating on Vista the browsers work very fast as usual. It's all the same hardware so I think this is a software problem within Ubuntu. 

I eagerly await your wisdom.

---

### Post by oldfred on 2010-07-25
Try copy & paste. I have used the commands I posted and used copy & paste and they work just fine. Stanza in this case is the group of lines that boot window

This is my windows stanza:

```
menuentry "Microsoft Windows XP Professional (on /dev/sda1)" {
    insmod ntfs
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set 04b05b70b05b6768
    drivemap -s (hd0) ${root}
    chainloader +1
}

```

The main reason we post terminal commands is that you can copy & paste them. Trying to explain gui commands is often very difficult as you have to go thru so many steps and one error gets you to a totally different place.

---

### Post by Smallwheels on 2010-07-25
I don't know why copy and paste works better than typing but I did it and made some progress. I copied and pasted the first command then pressed enter. A new window did open and it has plenty of code in it. So much code is in there that I can't recognize which stanzas to copy. I see several begin and end sections. The last one mentions Vista. I'll put them below.

I then copied and pasted the second command into the terminal and pressed enter. Nothing happened after several minutes. I did it again with no results. Without a second window to paste the command I suppose I'm stuck. 

Here is what showed up in the first window: # #
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
set root='(hd0,5)'
search --no-floppy --fs-uuid --set e2eac281-e91f-4d00-84fc-5dcd8a496bb7
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
set root='(hd0,5)'
search --no-floppy --fs-uuid --set e2eac281-e91f-4d00-84fc-5dcd8a496bb7
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
menuentry 'Ubuntu, with Linux 2.6.32-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set e2eac281-e91f-4d00-84fc-5dcd8a496bb7
    linux    /boot/vmlinuz-2.6.32-24-generic root=UUID=e2eac281-e91f-4d00-84fc-5dcd8a496bb7 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set e2eac281-e91f-4d00-84fc-5dcd8a496bb7
    echo    'Loading Linux 2.6.32-24-generic ...'
    linux    /boot/vmlinuz-2.6.32-24-generic root=UUID=e2eac281-e91f-4d00-84fc-5dcd8a496bb7 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-23-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set e2eac281-e91f-4d00-84fc-5dcd8a496bb7
    linux    /boot/vmlinuz-2.6.32-23-generic root=UUID=e2eac281-e91f-4d00-84fc-5dcd8a496bb7 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-23-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set e2eac281-e91f-4d00-84fc-5dcd8a496bb7
    echo    'Loading Linux 2.6.32-23-generic ...'
    linux    /boot/vmlinuz-2.6.32-23-generic root=UUID=e2eac281-e91f-4d00-84fc-5dcd8a496bb7 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set e2eac281-e91f-4d00-84fc-5dcd8a496bb7
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=e2eac281-e91f-4d00-84fc-5dcd8a496bb7 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set e2eac281-e91f-4d00-84fc-5dcd8a496bb7
    echo    'Loading Linux 2.6.32-21-generic ...'
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=e2eac281-e91f-4d00-84fc-5dcd8a496bb7 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set e2eac281-e91f-4d00-84fc-5dcd8a496bb7
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set e2eac281-e91f-4d00-84fc-5dcd8a496bb7
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Recovery Environment (loader) (on /dev/sda1)" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 02f0851ff0851a55
    drivemap -s (hd0) ${root}
    chainloader +1
}
menuentry "Windows Vista (loader) (on /dev/sda2)" {
    insmod ntfs
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set 949ca48c9ca46a86
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

That's it. I await your reply.

WAIT!!! When I closed the first window that opened, a new window appeared. It asked for my password to do administrative tasks. I typed it in and the second window you mentioned did open. It has lines in different colors. It is mostly blue text but there is one line of red text.

##!/bin/sh
exec tail -n +3 $0
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.

OK. What two stanzas should I copy into this page? 
After copying them should I just hit enter? 
The first window that opened is now gone. Is it still necessary? I suppose I could just copy and paste the first command into the terminal and get it back.

Let me know. Thank you.

---

### Post by Smallwheels on 2010-07-25
#michael@Michael-of-Linux:~$ gksudo gedit /etc/grub.d/40_custom

That line (minus the first #) is what I just noticed is now in the terminal window. Is it good, bad, indifferent?

---

### Post by oldfred on 2010-07-25
You can hit up arrow on the terminal and it will give you previous commands. It saves in history your commands. If you just type in history is will show you the last 500 commands you used.

You said you had issues with the names of the windows titles which are part of the windows stanzas (group of lines to boot windows). You just want to copy the two groups of commands from the bottom of the grub.cfg that contain windows vista. Paste into 40_custom and edit the title (and only the title) to what you want, save and then run 
sudo update-grub.

You will then on next reboot have 4 windows titles from the stanzas. The two original and the two new ones. If the new ones work then we can change setting to eliminated the first two that have the wrong titles.

IF you look at the panel on the very bottom of your screen it should show the screens you have started even it is is not on top.

---

### Post by Smallwheels on 2010-07-25
So this is what I will copy and paste: 
### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Recovery Environment (loader) (on /dev/sda1)" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 02f0851ff0851a55
    drivemap -s (hd0) ${root}
    chainloader +1
}
menuentry "Windows Vista (loader) (on /dev/sda2)" {
    insmod ntfs
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set 949ca48c9ca46a86
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

I will then swap the words "Windows Recovery Environment (loader)" AND "Windows Vista (loader). 

If I do that then the partitions should be named properly. Is that right?

After entering them on that 40_custom window should I press enter? Is that what makes them switch?

---

### Post by oldfred on 2010-07-25
You have to save 40_custom and then run this to update the grub.cfg. You cannot directly edit grub.cfg but edit settings or files like  40_custom and then run this to update grub.cfg
```

sudo update-grub
```On next reboot you should have 4 windows menu entries, the two mis named one's then the two corrected ones.

---

### Post by Smallwheels on 2010-07-25
I copied and pasted the changes I said I would do. If that is right then good. After doing that. I clicked the file menu and selected save. Is that what you meant when you said I had to save it first? 

After doing that I copied and pasted the command into the terminal: sudo update-grub then I pressed enter. Nothing happened. 

I can't reopen gedit /boot/grub/grub.cfg. I tried by copying and pasting and by typing it into the terminal. That page won't open. I originally tried using the arrow keys to get up to the original command but that didn't work.

---

### Post by oldfred on 2010-07-25
I do not understand terminal not responding. Did the system give some error message? If a command worked once up arrow will give exactly the same command it will work. (except those that I mistyped the first time I find still do not work:))

If you close & reopen terminal does it work?

When you close a file it usually asks if you want to save or lose changes, or you can save & then when you close it just exits.

---

### Post by Smallwheels on 2010-07-25
OK here is what happened. I put my computer into hibernate mode because I didn't know when you would respond. When I did that the computer seemed to turn off. In Vista if I hibernate the white power button turns yellow and stays that way until I press it again. With Ubuntu it turned off. I also noticed upon booting that there are now three sets of kernels for Ubuntu. I thought I saw that the last time it was turned on but wasn't sure because I wasn't focused on it.

When the computer turned back on it remembered my pages and everything was the same.
I read your last message and decided to turn off the terminal because it wasn't doing anything. I restarted it and copied and pasted the sudo update-grub command. It asked me for my password. after I typed it and hit enter plenty of things were printed. 
Here it is:

```
#Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.32-24-generic
Found initrd image: /boot/initrd.img-2.6.32.24-generic
Found linux image: /boot/vmlinuz-2.6.32-23-generic
Found initrd image: /boot/initrd.img-2.6.32-23-generic
Found linux image: /boot/vmlinuz-2.6.32-21-generic
Found linux image: /boot/initrd.img-2.6.32-21-generic
Found memtest86+ image: boot/memtest86+.bin
Found Windows Recovery Environment (loader) on /dev/sda1
Fond Windows Vista (loader) on /dev/sda2
done
```

I had to type all of that because the browsers on the Ubuntu computer now won't work. I'm using my Mac right now. The music program also can't connect to the internet.

What is to be done now? This seems like one step forward two steps backward.

Is now the time to turn off the computer and try to boot into Vista using the proper loader line?

One more thing. If I press the up or down arrows on the keyboard I get ^[[A for up and ^[[B for down. Those appear in the terminal window. I don't understand that. 

I did type in #gedit /boot/grub/grub.cfg while waiting and it did open a window with information in it. I can't tell if it is different from the original window because I closed it hours ago. That is when it first asked me for my password and then things started happening.

I decided to turn off the computer and reload Vista. I selected the loader labeled sda1 (I think) and it did load the Vista program. If I remember correctly, before I had to select the recovery section to load the Vista OS.

Next I'm going to shut down Vista and open Ubuntu. I want to see if the browsers not being allowed to connect to the internet was a temporary bug. Maybe restarting it will get it to work properly. I hope so. By the way the browsers still open fast and operate normally within Vista.

---

### Post by oldfred on 2010-07-25
I am now concerned that you did something else that corrupted something. Bowser and terminal should not have been affected. Did you paste something into terminal that it took as another command. Pasting into a text file changes nothing on the terminal nor browser.

I will be here for about another hour, then tomorrow AM for a bit.

---

### Post by Smallwheels on 2010-07-25
I rebooted into Ubuntu and the web browsers are connecting to the Internet. 

There are now three Ubuntu kernels with their corresponding recovery sections. At least that is what I think they are called. There are two for Vista. 

So the next thing to do is to remove the superfluous lines in the boot menu. After that I'll tackle the browser speed problem. 

Anybody out there know what is going on with them? It takes them a really long time to locate web sites but once they're at the site the browsers move quickly within them. Not all sites. Yahoo.com has a home page. It takes a long time to get there but once there I can click links that take me to other yahoo pages and most of them open quickly. On ubuntuforums.org it takes a long time to switch pages and to post comments. Maybe this explanation can give a clue to what's going on.

All help is welcome.

---

### Post by oldfred on 2010-07-25
Do you have 4 Vista entries? You should have your original 2 and the new two with what ever editing you did. If not, Please rerun and post a new results.txt from the boot_info_script. Please highlight and then click on the # in the panel above where you paste to put it in code tags (#). It is easier to read if in code tags.

If you have 4 entires you can prevent it from finding the two default with wrong info, please confirm that you were able to boot your copy of Vista as this will prevent it from finding the original ones:
```
sudo chmod a-x /etc/grub.d/30_os-prober
```

And then rerun sudo update-grub, (use up arrow to get to your previous entry)

---

### Post by Smallwheels on 2010-11-22
I can now boot Vista with no problem. There is a superfluous Vista entry. I did an update of Ubuntu a few months ago and just this weekend restarted the computer after the update. Now the browser windows are opening much quicker but still slower than they should be opening. 

I will be uploading a video soon with the boot menu showing. It shows FOUR different kernels now. Before that last update there were just three. Why are these growing? 

Please pause the video and see the boot loader page and help me to delete all of the ones I don't need. Are they taking up a lot of space on the drive?

Since my Ubuntu adventure began I've seen the new 10.10 LTS come out. Some people are saying they wish they would have stayed with 10.04. Should I stay with 10.04? Should I just restart my Ubuntu adventure with a new start using 10.10? 

Once this is fixed and my browsers work at normal speed, I'd like help getting video's to work and finding a way to watch Quicktime videos such as the ones on the Apple.com web site.

Smallwheels

---

### Post by carl4926 on 2010-11-22
Ubuntu keeps by default older kernels incase the new one doesn't work for you

An additional windows entry might be for a recovery partition or hidden OEM data partition

---

### Post by Smallwheels on 2010-11-24
Here is a link to a video I made of my Ubuntu 10.04 LTS opening and running browsers slowly. I have seen and heard how much faster Ubuntu or any Linux version makes old computers run fast. I've seen this and know it to be true. 

Seeing my latest version of Firefox and the 10.5 version of Opera opening pages so slowly shows me that something is wrong. I do compare it to my Apple computer and the speed difference is noticeable. The Apple computer is running a much faster processor (2.4 GHz Intel Core 2 Duo) but I've seen old Linux computers work just as fast for web browsing as this newer Mac. 

I'm using a 2.3 GHz AMD Sempron LE 1300 with 2 GB RAM.  I mistakenly typed 2.7 GHz in the video description. 

Before my last update it was taking a minimum of 54 seconds for a browser (either of them) to switch from one web site to the next one. I don't know what the update changed but the computer browsers are faster. Notice that they open windows within a web site at what is probably normal speed, but; when switching from one web site to another it takes much longer. I have a DSL connection and that isn't really a negative factor in accessing web pages. 

Would removing the extra things (kernels) make the computer run faster, or should I say, properly?

Once I get  help removing the superfluous kernels I'll open a different thread to handle the next thing for which I need help (watching DVDs). 

Here is a link to the video of my computer operating: 

[http://www.youtube.com/watch?v=j0j2j7zeQKo](http://www.youtube.com/watch?v=j0j2j7zeQKo)

---

### Post by carl4926 on 2010-11-25
You need to look at your network
Is this a wired or wireless connection and what devices and driver do you have
This will tell us much
```
lspci -nnk
```

What download speed to you expect?
Have you tested it in Firefox

---

### Post by Smallwheels on 2010-11-26
carl4926 thank you for offering a way to fix this speed thing. I'm using a modem from Qwest that has Ethernet connections to both computers. 

The speed I'm expecting is many times higher than I'm witnessing. Just yesterday I came across a Youtube video of someone using a Chromium browser on Ubuntu and it was blazing fast. Almost as soon as he hit enter the web site he wanted showed up. I know that Linux can work much faster within a computer than Windows and some Macs. I've seen it. 

My internet connection is consistently 1.2 Mbps. I would expect my Linux rig to be at least as fast as my Mac when accessing web sites. I really think it should be quicker, but; equal speed would be acceptable. 

This computer is dual booted with Vista. I can say that the Vista OS accesses and switches web sites much faster than Ubuntu using the same hardware. As I mentioned in earlier posts and on the video, originally it took a minimum of fifty-four seconds from the time I hit enter to the time a web site would appear in the browser. 

This is my first Ubuntu installation or any other OS installation. If it weren't for the knowledgeable people here I wouldn't have even tried doing this. I was wondering if all of these duplicate kernels are the source of the slowness. Since I'm not a computer programmer or engineer I can only guess at these things until I learn more. 

I did enter the command you gave to me in the terminal and here are the results:

#michael@Michael-of-Linux:~$ lspci -nnk```

00:00.0 RAM memory [0500]: nVidia Corporation MCP61 Memory Controller [10de:03ea] (rev a1)
00:01.0 ISA bridge [0601]: nVidia Corporation MCP61 LPC Bridge [10de:03e0] (rev a2)
00:01.1 SMBus [0c05]: nVidia Corporation MCP61 SMBus [10de:03eb] (rev a2)
    Kernel driver in use: nForce2_smbus
    Kernel modules: i2c-nforce2
00:01.2 RAM memory [0500]: nVidia Corporation MCP61 Memory Controller [10de:03f5] (rev a2)
00:02.0 USB Controller [0c03]: nVidia Corporation MCP61 USB Controller [10de:03f1] (rev a3)
    Kernel driver in use: ohci_hcd
00:02.1 USB Controller [0c03]: nVidia Corporation MCP61 USB Controller [10de:03f2] (rev a3)
    Kernel driver in use: ehci_hcd
00:04.0 PCI bridge [0604]: nVidia Corporation MCP61 PCI bridge [10de:03f3] (rev a1)
00:05.0 Audio device [0403]: nVidia Corporation MCP61 High Definition Audio [10de:03f0] (rev a2)
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel
00:07.0 Bridge [0680]: nVidia Corporation MCP61 Ethernet [10de:03ef] (rev a2)
    Kernel driver in use: forcedeth
    Kernel modules: forcedeth
00:08.0 IDE interface [0101]: nVidia Corporation MCP61 SATA Controller [10de:03f6] (rev a2)
    Kernel driver in use: sata_nv
    Kernel modules: sata_nv
00:08.1 IDE interface [0101]: nVidia Corporation MCP61 SATA Controller [10de:03f6] (rev a2)
    Kernel driver in use: sata_nv
    Kernel modules: sata_nv
00:09.0 PCI bridge [0604]: nVidia Corporation MCP61 PCI Express bridge [10de:03e8] (rev a2)
    Kernel driver in use: pcieport
    Kernel modules: shpchp
00:0b.0 PCI bridge [0604]: nVidia Corporation MCP61 PCI Express bridge [10de:03e9] (rev a2)
    Kernel driver in use: pcieport
    Kernel modules: shpchp
00:0c.0 PCI bridge [0604]: nVidia Corporation MCP61 PCI Express bridge [10de:03e9] (rev a2)
    Kernel driver in use: pcieport
    Kernel modules: shpchp
00:18.0 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration [1022:1100]
00:18.1 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map [1022:1101]
00:18.2 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller [1022:1102]
00:18.3 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control [1022:1103]
    Kernel driver in use: k8temp
    Kernel modules: k8temp
02:00.0 VGA compatible controller [0300]: nVidia Corporation GT218 [GeForce G210] [10de:0a60] (rev a2)
    Kernel driver in use: nouveau
    Kernel modules: nvidiafb, nouveau
02:00.1 Audio device [0403]: nVidia Corporation High Definition Audio Controller [10de:0be3] (rev a1)
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel

```
Does all of this give any clues about why the browsers operate so slowly?

All help is welcome.

Michael

---

### Post by wilee-nilee on 2010-11-26
At the least look in my signature for instructions on code tags. Then go through the thread with all your text info and tag it so it can be read with some efficiency, please, I mean pretty, pretty, please.:popcorn:

We can't help you if there isn't a standard of practice followed.;)

---

### Post by carl4926 on 2010-11-26
Earlier you said this:
> I'm using a desktop computer and it doesn't have WiFi or Bluetooth. It connects using a **USB** cable to my DSL modem. From the output you gave me, I see your ethernet device is OK
```
00:07.0 Bridge [0680]: nVidia Corporation MCP61 Ethernet [10de:03ef] (rev a2)
    Kernel driver in use: forcedeth
    Kernel modules: forcedeth

```
So are you saying your computer is not connected via the ethernet socket?

It sounds like you might be in possession of a rather rubbishy modem that ISP's throw away at you when you take up their equally rubbish service.

---

### Post by Smallwheels on 2010-11-27
> **carl4926 said:**
> Earlier you said this:
From the output you gave me, I see your ethernet device is OK
```
00:07.0 Bridge [0680]: nVidia Corporation MCP61 Ethernet [10de:03ef] (rev a2)
    Kernel driver in use: forcedeth
    Kernel modules: forcedeth

```So are you saying your computer is not connected via the ethernet socket?

It sounds like you might be in possession of a rather rubbishy modem that ISP's throw away at you when you take up their equally rubbish service.

Just last week I switched modems. It seems that they only last a year or so before they start acting up. My new one has all Ethernet connections. 

I did start this thread a while ago. It was left alone for months while I focused on getting another job. Today I've found solutions to playing DVDs and I got my headset microphone to work in Skype. I'd really like to figure out why my browsers operate so slowly. As I said before, they work much faster in Vista using the same hardware.

Carl4926 have you got any other suggestions?

---

### Post by carl4926 on 2010-11-27
Open a terminal and type:** firefox**
Hit enter

Firefox should start
But I want to see any info from the terminal

---

### Post by Smallwheels on 2010-11-27
I opened the terminal and my name and computer name appeared. Behind that I typed Firefox and hit enter. Firefox opened a few seconds later. The cursor remained on the next line in the terminal and just blinked a white box. My name and computer name didn't reappear. 

```
michael@Michael-of-Linux:~$ firefox
```

---

### Post by carl4926 on 2010-11-27
So it opened in a few seconds?

Is that quick or slow?

---

### Post by carl4926 on 2010-11-27
Have you tried a speed test from Firefox?

[http://www.speedtest.net/index.php?nojs=1](http://www.speedtest.net/index.php?nojs=1)

Does it report a good speed?

Test it in Vista. How do they compare?

-------------------------------------------------

I'm wondering if you need to configure your DNS settings manually rather than leaving it to DHCP

---

### Post by Smallwheels on 2010-11-27
I would say that the browsers open a bit slowly but not much slower than Vista. I regularly do speed tests at that site. The speeds are in the normal range for my area. They've been similar for years. 

The thing that is slow is within my computer. It takes the computer extra time to switch between web sites and web pages. I've been playing with Opera and Firefox and both open pages slowly. These are browsers that claim to run fast. I know Firefox isn't as fast as Safari or Chromium, but; Opera is supposed to be really fast yet it opens pages even slower than Firefox. 

Something changed with the last update I loaded a few months ago. I don't know what changed but instead of taking fifty-four seconds to open they now open in a few seconds. Usually it is taking around twelve seconds. 

In Vista it takes Firefox about one to six seconds to open a new page. I don't have Opera loaded on Vista. Also Vista switches pages on this forum within one second whereas on Ubuntu it takes almost ten seconds. 

Are all of those kernels (5 Ubuntu and 2 Vista) causing the computer to operate slower than it could?

---

### Post by carl4926 on 2010-11-27
Do this in a terminal
```
ping -c 6 173.194.37.104
```

Here is my result:
```
PING 173.194.37.104 (173.194.37.104) 56(84) bytes of data.
64 bytes from 173.194.37.104: icmp_seq=1 ttl=53 time=43.0 ms
64 bytes from 173.194.37.104: icmp_seq=2 ttl=53 time=45.5 ms
64 bytes from 173.194.37.104: icmp_seq=3 ttl=53 time=42.8 ms
64 bytes from 173.194.37.104: icmp_seq=4 ttl=53 time=42.6 ms
64 bytes from 173.194.37.104: icmp_seq=5 ttl=53 time=42.1 ms
64 bytes from 173.194.37.104: icmp_seq=6 ttl=53 time=42.3 ms

```

---

### Post by Smallwheels on 2010-11-27
```
PING 173.194.37.104 (173.194.37.104) 56(84) bytes of data.
64 bytes from 173.194.37.104: icmp_seq=1 ttl=52 time=171 ms
64 bytes from 173.194.37.104: icmp_seq=2 ttl=52 time=172 ms
64 bytes from 173.194.37.104: icmp_seq=3 ttl=52 time=170 ms
64 bytes from 173.194.37.104: icmp_seq=4 ttl=52 time=171 ms
64 bytes from 173.194.37.104: icmp_seq=5 ttl=52 time=171 ms
64 bytes from 173.194.37.104: icmp_seq=6 ttl=52 time=171 ms

--- 173.194.37.104 ping statistics ---
6 packets transmitted, 6 received, 0% packet loss, time 5007ms
rtt min/avg/max/mdev = 170.805/171.497/172.579/0.738 ms

```These are the results from my computer. What did it just ping? 

Will the distance to the location of the ping make a difference? Was the thing being pinged within my computer? I see my results are different from yours. If ms means milliseconds then my computer is almost four times slower than yours. 

Now that you have this information what is the next step to making my computer zippy on the internet?

---

### Post by carl4926 on 2010-11-27
It was google uk

try .com

```
ping -c 6 173.194.36.104
```

Mine is very similar to previous
```
kernelcruncher@LENOVO-G550:~> ping -c 6 173.194.36.104
PING 173.194.36.104 (173.194.36.104) 56(84) bytes of data.
64 bytes from 173.194.36.104: icmp_seq=1 ttl=53 time=43.6 ms
64 bytes from 173.194.36.104: icmp_seq=2 ttl=53 time=42.9 ms
64 bytes from 173.194.36.104: icmp_seq=3 ttl=53 time=40.7 ms
64 bytes from 173.194.36.104: icmp_seq=4 ttl=53 time=42.9 ms
64 bytes from 173.194.36.104: icmp_seq=5 ttl=53 time=42.7 ms
64 bytes from 173.194.36.104: icmp_seq=6 ttl=53 time=41.7 ms

--- 173.194.36.104 ping statistics ---
6 packets transmitted, 6 received, 0% packet loss, time 5007ms
rtt min/avg/max/mdev = 40.716/42.429/43.616/0.986 ms

```

---

### Post by carl4926 on 2010-11-27
The try this

```
sudo traceroute 173.194.36.104
```I get
```
traceroute to 173.194.36.104 (173.194.36.104), 30 hops max, 40 byte packets using UDP
 1  19.1.0.1 (19.1.0.1)  2.563 ms   2.356 ms   2.057 ms  [COLOR=DarkRed]**ROUTER**
[/COLOR]  2  lns17.inx.dsl.enta.net (18.39.1.26)  40.855 ms   42.630 ms   43.461 ms
 3  gi1-7.inx.dist.dsl.enta.net (18.9.1.25)  44.110 ms   44.532 ms   45.456 ms
 4  te2-2.interxion.dsl.enta.net (7.33.141.89)  46.374 ms   46.860 ms   47.938 ms
 5  te2-3.interxion.core.enta.net (87.127.236.209)  49.158 ms   49.615 ms   50.441 ms
 6  te5-1.gs1.core.enta.net (87.7.236.85)  51.851 ms   51.798 ms   52.602 ms
 7  te5-3.telehouse-north0.core.enta.net (87.7.236.41)  53.423 ms   53.971 ms   54.775 ms
 8  72.4.198.46 (72.4.198.46)  40.991 ms   40.922 ms   41.828 ms
 9  09.85.255.175 (09.85.255.175)  42.412 ms 209.85.252.76 (09.85.252.76)  43.436 ms   44.161 ms
10  209.85.251.62 (09.85.251.62)  45.305 ms   46.300 ms 09.85.251.56 (09.85.251.56)  46.915 ms
11  lhr14s01-in-f104.1e100.net (173.194.36.104)  47.443 ms   47.747 ms   48.385 ms  [B][COLOR=DarkRed]GOOGLE[/COLOR]
[/B] 
```Ignore the IP addresses because I edited some out, it's just showing how your ISP is routing your traffic and where it might be getting delayed

---

### Post by Smallwheels on 2010-11-27
Here is the result from the first one ```
   
ping -c 6 173.194.36.104            
``````
 PING 173.194.36.104 (173.194.36.104) 56(84) bytes of data.
64 bytes from 173.194.36.104: icmp_seq=1 ttl=52 time=172 ms
64 bytes from 173.194.36.104: icmp_seq=2 ttl=52 time=170 ms
64 bytes from 173.194.36.104: icmp_seq=3 ttl=52 time=170 ms
64 bytes from 173.194.36.104: icmp_seq=4 ttl=52 time=171 ms
64 bytes from 173.194.36.104: icmp_seq=5 ttl=52 time=172 ms
64 bytes from 173.194.36.104: icmp_seq=6 ttl=52 time=171 ms

--- 173.194.36.104 ping statistics ---
6 packets transmitted, 6 received, 0% packet loss, time 5006ms
rtt min/avg/max/mdev = 170.382/171.421/172.359/0.816 ms
    
```

---

### Post by Smallwheels on 2010-11-27
Here is the result from the second one
```
 
sudo traceroute 173.194.36.104     
``````
  sudo traceroute 173.194.36.104
sudo: traceroute: command not found
    
```The first try with this one required a password. This is the message it gave to me. I tried it a second time and it didn't ask for a password but the same result came out.

---

### Post by carl4926 on 2010-11-28
You may need to install traceroute

---

### Post by Smallwheels on 2010-11-28
I did a search in the software center and the program listed just below traceroute is installed. It is called iputils-tracepath. I was about to open the terminal in order to try duplicating your command with the word tracepath inserted where you used traceroute, when the computer froze. I can't believe it. I was accustomed to Vista or XP behaving that way but this surprised me. 

I had the terminal open, two Firefox windows, and the software center search results open when it froze. The cursor moved around fine. Nothing else worked. I turned off the computer using the power button on the tower.

I restarted it and there were no messages about being forced to shut down or about checking the system. 

Should I just type in your command using the word tracepath instead of traceroute? 

There is another installed program called mtr-tiny which is supposed to do the same as traceroute but it looks like it does much more. If I knew the proper commands I'd try these other programs that claim to be superior. What do you think?

---

### Post by Smallwheels on 2010-11-28
I tried using the input with tracepath instead of traceroute. The results were interesting. 

```
  michael@Michael-of-Linux:~$ sudo tracepath 173.194.36.104
[sudo] password for michael: 
 1:  Michael-of-Linux.local (192.168.0.3)                   0.121ms pmtu 1500
 1:  qwestmodem.domain.actdsltmp (192.168.0.1)              1.152ms 
 1:  qwestmodem.domain.actdsltmp (192.168.0.1)              0.897ms 
 2:  qwestmodem.domain.actdsltmp (192.168.0.1)              0.893ms pmtu 1492
 2:  hlna-dsl-gw08-200.hlna.qwest.net (209.181.36.200)     44.799ms 
 3:  hlna-agw1.inet.qwest.net (209.181.36.157)             47.891ms asymm  5 
 4:  hln-core-01.inet.qwest.net (205.171.156.65)           43.979ms asymm  6 
 5:  hln-core-02.inet.qwest.net (205.171.156.2)            44.490ms 
 6:  dvr-core-01.inet.qwest.net (205.171.5.74)             67.630ms 
 7:  dvr-brdr-01.inet.qwest.net (205.171.10.6)             63.954ms asymm  6 
 8:  63.146.26.138 (63.146.26.138)                         61.270ms asymm  7 
 9:  ae-31-53.ebr1.Denver1.Level3.net (4.68.107.94)        61.842ms asymm  8 
10:  ae-2-2.ebr2.Dallas1.Level3.net (4.69.132.106)         90.396ms asymm  8 
11:  ae-1-60.edge2.Dallas3.Level3.net (4.69.145.12)        80.501ms asymm  8 
12:  no reply
13:  no reply
14:  no reply
15:  no reply
16:  no reply
17:  no reply
18:  no reply
19:  no reply
20:  no reply
21:  no reply
22:  no reply
23:  no reply
24:  no reply
25:  no reply
26:  no reply
27:  no reply
28:  no reply
29:  no reply
30:  no reply
31:  no reply
     Too many hops: pmtu 1492
     Resume: pmtu 1492 
michael@Michael-of-Linux:~$ 
  
```Does this give a clue about what is going on or is this irrelevant?

---

### Post by carl4926 on 2010-11-28
Thing is I'm working from a openSUSE machine ATM and Mint 10

You can check by going here if you like:

[http://www.dnsstuff.com/](http://www.dnsstuff.com/)

Enter the IP in the traceroute 
It may give you an idea, but it's not quite the same.

Try tracepath by all means

---

### Post by carl4926 on 2010-11-28
I'd be interested to see if there is an equivalent in windows of traceroute?

I'd be asking your ISP what is going on. You can see how it's jamming up.

---

### Post by carl4926 on 2010-11-28
Oh
And you might want to start a new thread with some of this info in it, in the networking section.
You'll get better help that way. I'm no expert at it.

---

