---
title: "Wubi 9.10 + upgrade ubuntu = sh:grub&gt;"
date: 2009-11-27
forum: Installation &amp; Upgrades
---

### Post by mmlinx on 2009-11-27
after an update in Ubuntu 9.10 last night.
I always install Ubuntu beside Windows but i haven't  had this luxury on my cdrom less notebook. So i tried Wubi. Now after  three months i do an update in Ubuntu and im screwed. not so impressed  with Wubi anymore or is it a grub issue? 

"No wubildr"                       it shows this for a split second before  going to sh:grub>

Who can tell me what files i need to recover to c:\ubuntu\disks\grub (if  that is the answer..)
and how to do this with the grub command line or in Win xp?

What i allready tried: 

chkdsk /r in XP command prompt. This is the only answer the wubi faq  talks about...
This did not work for me.


After hitting tab in grub i get some options reader.rescue seems  interesting.
Who can help me out here ? 

Reinstalling Wubi doenst seem like an option to me. Seems to  Windoisch for me. 
Getting blue screen of death? just reinstall Windows and the problem  goes away... ](*,)

edit: Just booted in XP. this is how the folders look like. 
c:\ubuntu\disks\boot\grub\ (empty)
c:\wubildr.mbr
c:\wubildr (file)
c:\ubuntu\disks\swap.disk and root.disk
c:\ubuntu\disks\winboot (contains wubildr (file), wubildr.cfg and  wubildr.mbr)

---

### Post by darkod on 2009-11-27
Sorry to hear this. I can't help much with the error but just to let you know that you can install Ubuntu from usb stick too, that's how it's done on all netbooks. You can even install like that on a desktop with cdrom, doesn't matter.
Wubi is not a proper full install of ubuntu and you are aware of that. I saw another thread yesterday with the same problem. Because wubi is somehow,a combination of linux working inside windows, and is still dependent on windows, it seems doing some updates in it brakes it.
My personal opinion is that the Ubuntu team went step too far with wubi. They wanted to create easy way for windows users to try ubuntu without actually installing it, but instead they created many potential problems because it's not easy to combine linux inside windows. And these problems only give ubuntu bad name.
The CD has the Try Ubuntu option and that should have been the only and preferred option to try it without changing your computer. Not wubi.
If you like it and you feel ready for dual boot, consider removing wubi from Add/Remove programs and installing proper dual boot. That way you can add software, do updates, work with ubuntu, and most of the tutorials and help are written for such full install. Most of them won't apply for wubi.

PS. Check in C:\boot.ini if the windows bootloader has wubi at the correct path. Don't know if you can try anything else. I'm not even sure if the error is from windows bootloader or the "virtual" grub from wubi install.

---

### Post by mmlinx on 2009-11-27
thanks for your answer darkod
I was aware that i could install ubuntu with an USB stick. The Wubi way was just easy at the time because i did not have an usb stick @ the moment i got my notebook :( 

I really thought Wubi was stable that's why i did it that way. 
I allready installed all my favourite Linux apps.
installed and fully configured my lamp-server, tomcat6 server,  mysql databases and so on.
so im pretty upset this happened.
So that's why im trying to save everything. 

I will try to play with grub2, just found this link with allot of info on grub2:
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

if i don't get this to work ill have to save my /etc /var/lib/mysql, home/user files 
So i won't have to start @ 0 when i install ubuntu again. 

This is frustrating. Wubi makes it sound so cool to fast install Ubuntu on your system.
ill be deleting my blog praising Wubi i guess. 

ill update this post later to let others know what i did to "solve" it.

---

### Post by darkod on 2009-11-27
Sorry I couldn't help more. With all the stuff you have installed wubi was not really an option for you. Have a read about the grub2 but most of the things in that article I suspect only work with ubuntu install not so much with wubi. But look around definitely, I'm not experienced with wubi so maybe I'm wrong.

---

### Post by phillw on 2009-11-27
> **mmlinx said:**
> thanks for your answer darkod
I was aware that i could install ubuntu with an USB stick. The Wubi way was just easy at the time because i did not have an usb stick @ the moment i got my notebook :( 

I really thought Wubi was stable that's why i did it that way. 
I allready installed all my favourite Linux apps.
installed and fully configured my lamp-server, tomcat6 server,  mysql databases and so on.
so im pretty upset this happened.
So that's why im trying to save everything. 

I will try to play with grub2, just found this link with allot of info on grub2:
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

if i don't get this to work ill have to save my /etc /var/lib/mysql, home/user files 
So i won't have to start @ 0 when i install ubuntu again. 

This is frustrating. Wubi makes it sound so cool to fast install Ubuntu on your system.
ill be deleting my blog praising Wubi i guess. 

ill update this post later to let others know what i did to "solve" it.

There is a proposed work-round for wubi here --> > **Re: sh:grub > desperation** 			
 			 			 		   		 		 		[SIZE=3][COLOR=DarkRed]WUBI Installs Only[/COLOR][/SIZE]

I tried wubi when it first came out a few years ago but am no longer familiar with exactly how it works. There were enough problems recently that I rearranged my laptop's partitions so I could once again install wubi. Once I got wubi installed, I experimented until I could boot from a grub prompt. 

This is how I am able to manually boot from the Grub 2 prompt *in wubi*. My Windows partition is on [COLOR=DarkRed]**sda1**[/COLOR], which would be fairly standard.

Lines starting with a # are explanatory only. Do not type them.

 	Quote:
 	 	 		 			 				# Add the ntfs module
**[COLOR=Navy]insmod ntfs[/COLOR]**
# Set root (normally would be sda1, or hd0,1  Change as necessary
[B][COLOR=Navy]set root=(hd0,1)
loopback loop0 /ubuntu/disks/root.disk[/COLOR][/B]
# Yes, set root for a second time. I don't know why...
**[COLOR=Navy]set root=(loop0)[/COLOR]**
# Set the kernel. You can (and should) use Tab (twice) to complete entries such as the kernel when possible - type vml and then TAB twice and it will autocomplete to the point where there are two possibilities. Tab complete ensures the path/file names as typed exist. Additionally, if you suspect the new kernel is the problem, you might want to select an earlier one. vmlinuz.... should be a complete kernel entry such as "vmlinuz-2.6.31-15-generic-pae" *
**[COLOR=Navy]linux /boot/vmlinuz.... root=/dev/sda1  loop=/ubuntu/disks/root.disk ro[/COLOR]**
# Set the initrd image - complete or tab to get the full name  Example: "/boot/initrd.img-2.6.31-15-generic-pae"
[COLOR=Navy]**initrd /boot/initrd/initrd.img... **[/COLOR]
[B]# Boot.
[COLOR=Navy]boot[/COLOR][/B] 			 		 	 	 


* If this line scrolls off the screen as you type it, due to its length: To make it easier type "linux root=/dev/sda1 /ubuntu/disks/root.disk ro" and *then cursor back before "root=" to type/tab in the kernel name*.


If you successfully boot, run "sudo update-grub". Also inspect your /etc/default/grub file, which contains menu timeout and default kernel selections and determine if there is a problem with the menu.
 		                   		  		  		 		 			 				__________________
				[GRUB2]("https://help.ubuntu.com/community/Grub2") : [G2-Tweaks]("http://ubuntuforums.org/showthread.php?t=1287602") [G2-Basics]("http://ubuntuforums.org/showthread.php?t=1195275")
[G2-Tasks]("http://ubuntuforums.org/showthread.php?t=1302743") [DiskSpace]("http://help.ubuntu.com/community/RecoverLostDiskSpace")  
[Expand /]("http://ubuntuforums.org/showthread.php?t=1219270") [SUM]("http://ubuntuforums.org/showthread.php?t=818177") 			
 		 		  		  		 		 			 				 				* 					 						Last edited by drs305; 1 Hour Ago at 06:24 PM*

It may get your Wubi back running for you.
Please post how you get on.

Regards,

Phill.

---

### Post by mmlinx on 2009-11-27
thanks phillw, 

# Set root (normally would be sda1, or hd0,1  Change as necessary
[B][COLOR=Navy]set root=(hd0,1)

this is (hd0,2) for me. hd0,1 looks like the notebooks recovery dir for windows
[/COLOR][/B]
I get stuck at: 

[B][COLOR=Navy]root=/dev/sda1  loop=/ubuntu/disks/root.disk ro

[/COLOR][/B][COLOR=Navy]with tab the sda1 is not available but i see sdp1, is this one i should use?

thanks in advance. 

[/COLOR]

---

### Post by mmlinx on 2009-11-30
Just to update how i 'Solved' this. 
Tried to save the Wubi but couldn't. 
Then i Started thinking. Is Wubi something i really want? 
Ubuntu installed in Windows. It just did not sound right to me. 

So this is what i did: 

Burned a Mint7 Live cd. (on my other laptop that has a cdrom burner) I Like this more than Ubuntu because of the extras that are not standard installed in Ubuntu like compiz-manager, media codecs etc.
And i also like the green much more than the brown, im sorry if i offend people by saying this :D

I Booted from the fresh Mint Live CD.
Then i installed usb-creator with: sudo apt-get update && sudo apt-get install usb-creator.

Opened usb-creator from the menu and made an Mint 7 Live usb.

Then i used that usb stick to boot into mint7 on my acer one. 
After booting i installed Mint 7 on my acer one. 

After installation of mint7 i mounted my windows drive with:

sudo mkdir /media/windows_sucks && sudo mount /dev/sda2 /media/windows_sucks

Then i mounted the old Ubuntu Wubi root.disk file so i could copy all my files i needed from the old Wubi installation with: 

sudo mkdir /media/wubi && sudo mount -o loop /media/windows_sucks/ubuntu/disks/root.disk /media/wubi

And finally copied all the config files, mysql databases etc. i needed from that partition to my newly installed Mint installation. 

Now i'm very happy :D

My next step is to customize the mint usb stick so i can install Mint7 for all my friends when i come over and notice that their stuck on all sorts of windows :-& viruses and scare ware. Dualboot off course. So they can still choose to boot into lame windows if they want to.

---

### Post by yx2006 on 2009-12-01
Hi,[mmlinx]("http://ubuntuforums.org/member.php?u=935380")
I have the same problem with u 
I install ubuntu with wubi, and last night, I changed the grub menu list, then,when I reboot, 

= sh:grub

what I do with the grub menu list are: 

__________________________

sudo chmod 744 /boot/grub/grub.cfg
  
 sudo gedit /boot/grub/grub.cfg 



                ---------------------------


### BEGIN /etc/grub.d/00_header ###
if [ -s /boot/grub/grubenv ]; then
  have_grubenv=true
  load_env
fi
set default="1"
if [ ${prev_saved_entry} ]; then
  saved_entry=${prev_saved_entry}
  save_env saved_entry
  prev_saved_entry=
  save_env prev_saved_entry
fi
insmod ext2
set root=(hd0,8)
search --no-floppy --fs-uuid --set b9c8f0c6-f9c5-4eba-bdbb-db509bdea0bf
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
 [COLOR=Red] set timeout=10[/COLOR]
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/white
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd0,8)
    search --no-floppy --fs-uuid --set b9c8f0c6-f9c5-4eba-bdbb-db509bdea0bf
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=b9c8f0c6-f9c5-4eba-bdbb-db509bdea0bf ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-14-generic
}

### END /etc/grub.d/10_linux ###
__________________________


[COLOR=Black]I setted " timeout = 10[/COLOR] " to "timeout = 3" ,  then I saved the file.
After reboot , I got the problem .


__________________________


I will try this 



____-
Quote:
 	 	 		 			 				# Add the ntfs module
**[COLOR=Navy]insmod ntfs[/COLOR]**
# Set root (normally would be sda1, or hd0,1  Change as necessary
[B][COLOR=Navy]set root=(hd0,1)
loopback loop0 /ubuntu/disks/root.disk[/COLOR][/B]
# Yes, set root for a second time. I don't know why...
**[COLOR=Navy]set root=(loop0)[/COLOR]**
# Set the kernel. You can (and should) use Tab (twice) to complete entries such as the kernel when possible - type vml and then TAB twice and it will autocomplete to the point where there are two possibilities. Tab complete ensures the path/file names as typed exist. Additionally, if you suspect the new kernel is the problem, you might want to select an earlier one. vmlinuz.... should be a complete kernel entry such as "vmlinuz-2.6.31-15-generic-pae" *
**[COLOR=Navy]linux /boot/vmlinuz.... root=/dev/sda1  loop=/ubuntu/disks/root.disk ro[/COLOR]**
# Set the initrd image - complete or tab to get the full name  Example: "/boot/initrd.img-2.6.31-15-generic-pae"
[COLOR=Navy]**initrd /boot/initrd/initrd.img... **[/COLOR]
[B]# Boot.
[COLOR=Navy]boot[/COLOR][/B] 

______

---

### Post by robau on 2009-12-04
Looks like you have the ext4 - grub4 loopback bug:

See:

[https://bugs.launchpad.net/wubi/+bug/443107](https://bugs.launchpad.net/wubi/+bug/443107)

---

### Post by Dead Pixel on 2009-12-05
I just had this problem too, and solved it. Maybe this is a double post for a solution but I want to clarify it. 

[B]Solution for Windows ME/XP:
[/B] 
```
sh:grub>set root=(loop0)
sh:grub>linux /boot/vmlinuz-2.6.31-14-generic root=/dev/sda1 loop=/ubuntu/disks/root.disk ro
sh:grub>initrd /boot/initrd.img-26.31-14-generic
sh:grub>boot
```Open the prompt and type "sudo update-grub2"*[2] after a successful boot. This will solve the problem. 
 
[B]Solution for Windows Vista/7:

[/B]```
sh:grub>set root=(loop0)
sh:grub>linux /boot/vmlinuz-2.6.31-14-generic root=/dev/sda2*[1] loop=/ubuntu/disks/root.disk ro
sh:grub>initrd /boot/initrd.img-2.6.31-14-generic
sh:grub>boot
```Open the prompt and type "sudo update-grub2"*[2] after a successful boot. This will solve the problem. 


*[1]Notice the change **sda2**. Because **sda1 **is used as boot partition under Windows Vista/7.
*[2]Without quotes

---

### Post by darkod on 2009-12-05
> **Dead Pixel said:**
> 
*[1]Notice the change **sda2**. Because **sda1 **is used as boot partition under Windows Vista/7.
*[2]Without quotes

Just one small remark. Vista does not create the 100MB boot partition, only win7. And it doesn't create it always, only when partitions are created by the win7 installer on unpartitioned drive. If you install onto ex-Vista partition for example, the 100MB won't be created. So you should try both /dev/sda1 and /dev/sda2 depending what works for you.

---

### Post by andy_p on 2009-12-05
I had this problem and Dark Pixel's advice solved it - although I have Vista and had to use sda1 rather than sda2. Thanks!

---

### Post by Ubu_newbie on 2009-12-05
I also had this problem:  Installing Ubuntu using wubi.exe, all worked fine until upgrading, after which I always got dumped to the sh:grub prompt.

My solution was to do all the upgrades using the Upgrade Manager, EXCEPT the two grub updates.  Now everything works fine.:p

---

### Post by thinhhanh on 2009-12-05
Quote:
                                                 # Add the ntfs module
**[COLOR=Navy]insmod ntfs[/COLOR]**
# Set root (normally would be sda1, or hd0,1  Change as necessary
[B][COLOR=Navy]set root=(hd0,1)
loopback loop0 /ubuntu/disks/root.disk[/COLOR][/B]
# Yes, set root for a second time. I don't know why...
**[COLOR=Navy]set root=(loop0)[/COLOR]**
# Set the kernel. You can (and should) use Tab (twice) to complete entries such as the kernel when possible - type vml and then TAB twice and it will autocomplete to the point where there are two possibilities. Tab complete ensures the path/file names as typed exist. Additionally, if you suspect the new kernel is the problem, you might want to select an earlier one. vmlinuz.... should be a complete kernel entry such as "vmlinuz-2.6.31-15-generic-pae" *
**[COLOR=Navy]linux /boot/vmlinuz.... root=/dev/sda1  loop=/ubuntu/disks/root.disk ro[/COLOR]**
# Set the initrd image - complete or tab to get the full name  Example: "/boot/initrd.img-2.6.31-15-generic-pae"
[COLOR=Navy]**initrd /boot/initrd/initrd.img... **[/COLOR]
[B]# Boot.
[COLOR=Navy]boot[/COLOR][/B] 

______[/quote]

These instructions worked for me after a few tries.  Hit <TAB> only on the last two lines before running boot.

linux /boot/vmlinux <TAB> and select the old version you have, then keep typing the rest of the line.

initrd /boot/initrd.img <TAB> and select the same version you selected above.  Note that the image is under the /boot directory (maybe some other installation has it under /boot/initrd/).

Thanks very much guys for helping. :P

---

### Post by robinst on 2009-12-05
Hi all,

I seem to have an additional problem which makes that i can't follow the solutions provided above: my /dev/ for some reason doesn't have any sdX or hdX entries. Grub seems to recognize the physical devices, but doesn't translate them into logical devices.

The command
 ```
ls (hd0,3)/ubuntu
```shows me the stuff one would expect, being the disks/ install/ winboot/ directories as well as Ubuntu.ico and uninstall-wubi.exe. However i don't see hd0,3 as a logical device listed in /dev/.

My entire ls /dev/ output (just in case i really missed something, sorry for the flood):
```
fd pts/ shm/ agpgart apm_bios audio audio1
audio2 audio3 audioctl console core dsp dsp1 dsp2 dsp3 full i2c-0 i2c-1 i2c-2
i2c-3 i2c-4 i2c-5 i2c-6 i2c-7 kmem loop0 loop1 loop2 loop3 loop4 loop5 loop6
loop 7 mem midi0 midi00 midi01 midi02 midi03 midi1 midi2 midi3 mixer mixer1
mixer2 mixer3 mpu401data mpu401stat null port ptmx ram ram0 ram 1 ram 10 ram
11 ram 12 ram 13 ram 14 ram15 ram16 ram 2 ram 3 ram4 ram5 ram6 ram7 ram8 ram9
random rmidi0 rmidi1 rmidi2 rmidi3 sequencer smpte0 smpte1 smpte2 smpte3
sndstat stderr stdin stdout tty tty0 tty1 tty2 tty3 tty4 tty5 tty6 tty7 tty8
tty9 urandom zero
```I used wubi from a fresh windows7 home premium 64bits installation.

Does anybody have any advice for me which would make grub recognize the physical devices as logical devices, so i can return to the solutions already provided for making wubi work?

Thanks in advance,
Robin

---

### Post by 4ndris on 2009-12-06
It worked for me. :) But then, how sould I fix GRUB. I tried update, but still get the "** sh:grub>**" when I restart ubuntu. It seems the problem is the "2.6.31-16..".

---

### Post by mantaor on 2009-12-06
Hi 4ndris,
I have your problem (just like a lot of wubi users). Do you mean that you have already tried the past fix procedure with 2.6.31-16 and you have [B]sh:grub>? 
Why do ubuntu team continues to release kernel that works so bad with wubi?
sorry for bold: it's my firefox live 
[/B]

---

### Post by replikanxxl on 2009-12-07
are we sure that this problem is about wubi ? cause i had the same problem like 13 hours ago and after 12 hours of struggle , now i installed ubuntu from an old disk i had . now its version is 8.1 . and im hella scared to update anything at all . cause im forced to use linux and i have to set up some "really headache" platfrom to do some project . i still wanna try to update if i get a satisfactory answer . or just wait till saturday to try my chance on this no-turn-back thing . nice day everyone

---

### Post by Paperwings310 on 2009-12-07
I had the same problem and used Dead Pixel way of doing it my set up was windows 7 with wubi heres how i fixed it
[http://ecefun.com/forum/viewtopic.php?f=18&t=19](http://ecefun.com/forum/viewtopic.php?f=18&t=19)

---

### Post by bstankie on 2009-12-07
I too have done an install on a new laptop (Acer Aspire) using Windows 7 with the same issue ... not able to find the /dev/sda**.  Any help would be appreciated.  I would be willing to install using something other than Wubi if that is giving the problem. It has been about 2 years since I have done an install ... no Wubi at that time.

---

### Post by bstankie on 2009-12-08
> **bstankie said:**
> I too have done an install on a new laptop (Acer Aspire) using Windows 7 with the same issue ... not able to find the /dev/sda**.  Any help would be appreciated.  I would be willing to install using something other than Wubi if that is giving the problem. It has been about 2 years since I have done an install ... no Wubi at that time.

OK. I found a fix ... not optimal but this worked for me.  I re-installed Ubuntu (I just installed it so there was not anything there that I really needed).  

1. sudo aptitude update
2. Using the Update manager I updated all of the items with the exception of Grub.
    - The system the rebooted itself.
3. Logged back into Ubuntu (it worked this time).
4. Went to the Update manager and updated to the Grub items.
5. ran sudo aptitude update-grub (see [http://ecefun.com/forum/viewtopic.php?f=18&t=19](http://ecefun.com/forum/viewtopic.php?f=18&t=19)).

Now it seems to work fine.

---

### Post by donothingman on 2009-12-09
> **robinst said:**
> 
I seem to have an additional problem which makes that i can't follow the solutions provided above: my /dev/ for some reason doesn't have any sdX or hdX entries. Grub seems to recognize the physical devices, but doesn't translate them into logical devices.


I had this same problem, but using /dev/sda1 worked anyway. At first I wasn't sure which partition to use (sda1 or sda2?). When I looked closely at the error message I was getting, I saw that near the top of the screen it was listing all of the hard drive devices it found (/dev/sda1, /dev/sda2 ...) along with their sizes. Since I knew the size of the Windows partition where I had installed wubi, I was able to figure out which one to use. 

Hope this helps!

---

### Post by hhh81 on 2009-12-09
should be the bug explained here :
[https://bugs.launchpad.net/ubuntu/+source/lupin/+bug/477169?comments=all](https://bugs.launchpad.net/ubuntu/+source/lupin/+bug/477169?comments=all)

---

### Post by aiiee on 2009-12-11
> **Dead Pixel said:**
> I just had this problem too, and solved it. Maybe this is a double post for a solution but I want to clarify it. 

[B]Solution for Windows ME/XP:
[/B] 
```
sh:grub>set root=(loop0)
sh:grub>linux /boot/vmlinuz-2.6.31-14-generic root=/dev/sda1 loop=/ubuntu/disks/root.disk ro
sh:grub>initrd /boot/initrd.img-26.31-14-generic
sh:grub>boot
```Open the prompt and type "sudo update-grub2"*[2] after a successful boot. This will solve the problem. 
 
[B]Solution for Windows Vista/7:

[/B]```
sh:grub>set root=(loop0)
sh:grub>linux /boot/vmlinuz-2.6.31-14-generic root=/dev/sda2*[1] loop=/ubuntu/disks/root.disk ro
sh:grub>initrd /boot/initrd.img-2.6.31-14-generic
sh:grub>boot
```Open the prompt and type "sudo update-grub2"*[2] after a successful boot. This will solve the problem. 


*[1]Notice the change **sda2**. Because **sda1 **is used as boot partition under Windows Vista/7.
*[2]Without quotes

I appreciate the help folx, but PLEASE watch the typos.

---

### Post by centaure on 2010-01-06
I had the same problem after performing a ubuntu update today. I am running wubi on Windows 7. 

Once you login to windows, performing the following should suffice  (from [https://bugs.launchpad.net/ubuntu/+source/lupin/+bug/477169?comments=all)]("https://bugs.launchpad.net/ubuntu/+source/lupin/+bug/477169?comments=all%29;") ; the following is the pertinent part of the bug discussion hhh81 above refers to :-

**(note that in my case, I did not need to perform the steps indicated in B) below )

[Agostino Russo]("https://launchpad.net/%7Eago")             wrote             on 2009-12-23:                                                             [ #210]("https://bugs.launchpad.net/ubuntu/+source/lupin/+bug/477169/comments/210")                                                        For a patch/workaround:
 A) get the wubildr in [https://bugs.edge.launchpad.net/ubuntu/+source/grub2/+bug/477104/comments/90](https://bugs.edge.launchpad.net/ubuntu/+source/grub2/+bug/477104/comments/90) and copy it over C:\wubildr
B) ensure that when you boot there is no command "insmod ntfs". Press "e" at the grub boot menu to edit the relevant entry and remove "insmod ntfs" before proceeding
 New ubuntu/wubi installations do not contain the patch yet. The patch will only be applied once there is a clear confirmation (from you) that it actually solves the problem. Hence your feedback is appreciated.

---

### Post by Samutheus on 2010-01-08
> **centaure said:**
> [Agostino Russo]("https://launchpad.net/%7Eago")             wrote             on 2009-12-23:                                                             [ #210]("https://bugs.launchpad.net/ubuntu/+source/lupin/+bug/477169/comments/210")                                                        For a patch/workaround:
 A) get the wubildr in [https://bugs.edge.launchpad.net/ubuntu/+source/grub2/+bug/477104/comments/90](https://bugs.edge.launchpad.net/ubuntu/+source/grub2/+bug/477104/comments/90) and copy it over C:\wubildr

Thanks, I'm running wubi on Windows XP, and the simple step of A) solved all my problems instantly.

---

### Post by redrac on 2010-01-08
> **Samutheus said:**
> Thanks, I'm running wubi on Windows XP, and the simple step of A) solved all my problems instantly.

this solved mine also

---

### Post by Stupendous man on 2010-01-09
> **Dead Pixel said:**
> I just had this problem too, and solved it. Maybe this is a double post for a solution but I want to clarify it. 

[B]Solution for Windows Vista/7:

[/B]```
sh:grub>set root=(loop0)
sh:grub>linux /boot/vmlinuz-2.6.31-14-generic root=/dev/sda2*[1] loop=/ubuntu/disks/root.disk ro
sh:grub>initrd /boot/initrd.img-2.6.31-14-generic
sh:grub>boot
```Open the prompt and type "sudo update-grub2"*[2] after a successful boot. This will solve the problem. 




Oh my god, finally a solution that worked. 
I too had to change it to SDA1, but other than that, perfection.

One thing that was weird was that after downloading and installing all of the post-install updates, it happened again.
But I just went through the above one more time, and it fixed it.:o:D

Thanks man.

---

### Post by mzykster on 2010-01-28
> **Ubu_newbie said:**
> I also had this problem:  Installing Ubuntu using wubi.exe, all worked fine until upgrading, after which I always got dumped to the sh:grub prompt.

My solution was to do all the upgrades using the Upgrade Manager, EXCEPT the two grub updates.  Now everything works fine.:p

I did the same, new installation and unchecked Gnu Grub updates, works perfect. Hope there will be no problems, it's my first adventure with Ubuntu ;)

---

### Post by meierfra. on 2010-01-28
For anybody inflected by this problem: 

[SIZE="4"]The solution in post 10 is  not a permanent fix. [/SIZE]

 The problem can reoccur after any kernel or grub update. Please follow the advice from post 25.  For more details on the problem and the solution see

[https://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Wubi_9.10](https://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Wubi_9.10)

---

### Post by anur.bhargav on 2010-02-06
> **centaure said:**
> I had the same problem after performing a ubuntu update today. I am running wubi on Windows 7. 

Once you login to windows, performing the following should suffice  (from [https://bugs.launchpad.net/ubuntu/+source/lupin/+bug/477169?comments=all)]("https://bugs.launchpad.net/ubuntu/+source/lupin/+bug/477169?comments=all%29;") ; the following is the pertinent part of the bug discussion hhh81 above refers to :-

**(note that in my case, I did not need to perform the steps indicated in B) below )

[Agostino Russo]("https://launchpad.net/%7Eago")             wrote             on 2009-12-23:                                                             [ #210]("https://bugs.launchpad.net/ubuntu/+source/lupin/+bug/477169/comments/210")                                                        For a patch/workaround:
 A) get the wubildr in [https://bugs.edge.launchpad.net/ubuntu/+source/grub2/+bug/477104/comments/90](https://bugs.edge.launchpad.net/ubuntu/+source/grub2/+bug/477104/comments/90) and copy it over C:\wubildr
B) ensure that when you boot there is no command "insmod ntfs". Press "e" at the grub boot menu to edit the relevant entry and remove "insmod ntfs" before proceeding
 New ubuntu/wubi installations do not contain the patch yet. The patch will only be applied once there is a clear confirmation (from you) that it actually solves the problem. Hence your feedback is appreciated.
Thank you very much it worked perfect... the method is also very simple

---

### Post by bonusG on 2010-02-06
> **centaure said:**
> I had the same problem after performing a ubuntu update today. I am running wubi on Windows 7. 

Once you login to windows, performing the following should suffice  (from [https://bugs.launchpad.net/ubuntu/+source/lupin/+bug/477169?comments=all)]("https://bugs.launchpad.net/ubuntu/+source/lupin/+bug/477169?comments=all%29;") ; the following is the pertinent part of the bug discussion hhh81 above refers to :-

**(note that in my case, I did not need to perform the steps indicated in B) below )

[Agostino Russo]("https://launchpad.net/%7Eago")             wrote             on 2009-12-23:                                                             [ #210]("https://bugs.launchpad.net/ubuntu/+source/lupin/+bug/477169/comments/210")                                                        For a patch/workaround:
 A) get the wubildr in [https://bugs.edge.launchpad.net/ubuntu/+source/grub2/+bug/477104/comments/90](https://bugs.edge.launchpad.net/ubuntu/+source/grub2/+bug/477104/comments/90) and copy it over C:\wubildr
B) ensure that when you boot there is no command "insmod ntfs". Press "e" at the grub boot menu to edit the relevant entry and remove "insmod ntfs" before proceeding
 New ubuntu/wubi installations do not contain the patch yet. The patch will only be applied once there is a clear confirmation (from you) that it actually solves the problem. Hence your feedback is appreciated.


That worked for me too...!!! At last... it was the third time tha happened to me...!!!

---

### Post by adityagnet on 2010-02-06
Hey,
I installed ubuntu 9.10 inside windows 7 using wubi. Now I want to remove it temporarily from my computer. How do I do it? Please help me!

---

### Post by anur.bhargav on 2010-02-06
> **adityagnet said:**
> Hey,
I installed ubuntu 9.10 inside windows 7 using wubi. Now I want to remove it temporarily from my computer. How do I do it? Please help me!
a

---

### Post by anur.bhargav on 2010-02-06
> **adityagnet said:**
> Hey,
I installed ubuntu 9.10 inside windows 7 using wubi. Now I want to remove it temporarily from my computer. How do I do it? Please help me!
Hello,
Please Goto Control Panel---> Uninstall a Program,Search for ubuntu And uninstall it.That's that,it should be done.

---

### Post by wiebeest on 2010-02-07
> **Samutheus said:**
> Thanks, I'm running wubi on Windows XP, and the simple step of A) solved all my problems instantly.

Yeps, instant success overhere too with a windows XP install and 9.10 wubi.
With just doing step A (replacing the wubildr file). Works like a charm again.

But...this is the 3rd time I got the sh:grub> error with reboot after updating with 9.10 wubi and grub2. 
Never once had this with 9.04 wubi. This grub2 bug is serious and I think this should be fixed _**ASAP**_.

---

### Post by TriadHonor on 2010-02-07
I post a guide on this, the solution is very simply and can be doen directly from Windows.

Read it here: [http://ubuntuforums.org/showthread.php?t=1400608](http://ubuntuforums.org/showthread.php?t=1400608)

Also SourceForge explain this solution.

---

### Post by kidtty on 2010-02-07
HELP!!!! I've tried absolutely everything including the new wubildr and also the instructions from post #24 for Vista. Everything matches my problem from what I hear of everybody else. I installed some updates and all was asked to restart, so I did. Then i came up with the GNU GRUB screen showing the sh:grub>      Nothing has worked so far. Did I do something wrong? Can someone bring me through this step by step? I'm not sure if it means anything but when I performed the step from post #24 after I typed boot and it went through the process. It stopped and then said that /dev/sda2*[1] does not exist. does it exist as something else? I also had checked my partitions using disk management and it showed 10GB unallocated and the rest was under Windows. There is no separate partition for Ubuntu. Bad?

---

### Post by meierfra. on 2010-02-07
kidtty:  Sounds like your problem is different.  I suggest to start a new thread. Also follow  these [instructions]("http://bootinfoscript.sourceforge.net/") to run the boot info script and post RESULTS.txt in the new thread. Feel free to send me a PM with a link to your new thread.

---

### Post by kidtty on 2010-02-07
SUCCESS. I did some more researching and found my solution! Exact same problem, different fix. At least cosmetically it seemed like the exact same problem. I love Ubuntu and I was not willing to give up on it. I'm 16 and I downloaded Ubuntu for the first time last night and I have conquered the toughest challenge I have faced when it comes to computers. BOO YA! Terminal is my fav.

---

### Post by 1reginald on 2010-02-11
Came to this thread because I used Wubi to download and install Ubuntu to my Windows Vista System.  I tried all the recommendations detailed here including the concise last entry.  Got an error on the 2nd line saying no such disk. It did not like the SDA2 entry.
So I used Partition Commander to take a look at my hard drive.
One partition was NTFS for Vista.  The other half the drive was Free. Not formated.
I reasoned that all the Ubuntu files I downloaded were imbedded in Vista. (They are).
I then used Partition Commander to format the free space as a Linux partition.
After doing that I rebooted my system.  I selected Ubuntu from the Dual Boot menu and the system took off to do a complete Ubuntu install using the Files in Vista. I had no CD in the CD Drive.
It may be that the problem with Wubi was that it could not find a Linux formated partition so it defaulted to sh:grub within Vista.  When I set up the Linux Partition, Wubi took off and did it's thing like it was supposed to.
Hopes this helps someone. It sure worked nice for me. I am not a geek, so there may be other problems associated with my procedure that I have not noticed.
Unbuntu 9.10 is amazing once it installs. Printer, internet access, everything one could want.

---

### Post by duke_ on 2010-02-15
Same problem here after 2.6.31-19 kernel upgrade.   At first I had enduring trouble and great pain booting manually, and I wanted to share the instructions that worked for my system.  

The greatest point of confusion for me was that there were no /dev/sd... entries listed via "ls /dev" from the grub command prompt.  Despite this, my manual boot succeeded when I used "root=/dev/sda2". in my "linux ..." command.  Also, my host (vista) partition was not mounted properly, so I could not "ls /ubuntu".  Yet despite that I was able to successfully specify "loop=/ubuntu/disks/root.disk" in my linux command.

System details:
hardware: lenovo r61i laptop (probably not relevant)
host OS: Windows Vista
wubi version: ? (probably not relevant)
ubuntu version: 9.10

Manual boot instructions:
set root=(loop0)
linux /boot/vmlinuz-2.6.31-16-generic root=/dev/sda2 loop=/ubuntu/disks/root.disk ro
initrd /boot/initrd.img-2.6.31-16-generic
boot

In Ubuntu after manual root:
"sudo update-grub" ("sudo update-grub2" is equivalent?)

Notes:
You may have to change /dev/sda2 to /dev/sda1.  You need to pick the device that corresponds to the windows partition that stores your wubi installation. I think I simply used "ls" from the grub command prompt and got info that suggested I needed to use sda2. (I think the first partition was the windows boot partition).

---

### Post by meierfra. on 2010-02-15
It seems I have to repeat  my post #30:

For anybody inflected by this problem: 

[SIZE="4"]The solution presented in posts  10 and 42  is  not a permanent fix. [/SIZE]

and only works in some cases.

The problem can reoccur after any kernel or grub update.   For more details on the problem and a permanent solution see

[https://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Wubi_9.10](https://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Wubi_9.10)

---

### Post by fiklein on 2010-03-02
There is a wubildr patch, but I would suggest you back up the original wubildr version before using the patch. On a computer that was working with Jaunty 9.04 with the previous "defective" wubildr, I installed the patch before trying to upgrade to Karmic 9.10. The patch made Ubuntu unbootable, so I reverted to the previous wubildr and was up and going again. I do not know if the patch is compatible with 9.04. For now, I am just not upgrading until the solution is certain.

---

### Post by meierfra. on 2010-03-02
> do not know if the patch is compatible with 9.04. 
It's not. The wubildr for Wubi 9.10 is based on Grub2, the one for Wubi 9.04 or older on Grub4Dos

If you upgrade from Wubi 9.04 to 9.10, you will use the old wubildr and won't be effected by this bug.  So upgrading should be save.  

Thanks for  the warning. I will add it to my HowTo.

---

### Post by alexlpfeil on 2010-07-12
> **meierfra. said:**
> It seems I have to repeat my post #30:
 
For anybody inflected by this problem: 
 
[SIZE=4]The solution presented in posts 10 and 42 is not a permanent fix. [/SIZE]
 
and only works in some cases.
 
The problem can reoccur after any kernel or grub update. For more details on the problem and a permanent solution see
 
[https://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Wubi_9.10](https://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Wubi_9.10)
 
 
THIS WORKED FOR ME!!!!!!!!!!!!!!!!
Thanks,
Alex

---

