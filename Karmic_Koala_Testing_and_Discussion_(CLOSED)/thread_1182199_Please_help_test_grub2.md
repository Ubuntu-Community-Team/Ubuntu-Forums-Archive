---
title: "Please help test grub2"
date: 2009-06-08
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by castrojo on 2009-06-08
Please see: [https://lists.ubuntu.com/archives/ubuntu-devel-announce/2009-June/000573.html](https://lists.ubuntu.com/archives/ubuntu-devel-announce/2009-June/000573.html)
and [https://wiki.ubuntu.com/KernelTeam/Grub2Testing](https://wiki.ubuntu.com/KernelTeam/Grub2Testing)

My laptop passed!

**Don't just post here; please add your results to the wiki page, and report failures as bug reports using **```
ubuntu-bug -p grub2
```.

---

### Post by super.rad on 2009-06-08
Will test it now, glad to see grub2 will finally be default
EDIT: The instructions say to install grub2 which will set it up in parallel to grub-legacy but apt is saying it needs to remove grub to install grub2

---

### Post by Timon&amp;Pumba on 2009-06-08
A 3-year old Dell latitude works also without problems.
Due to the lack of real issues, we may resort to discussing and ranting about how grub2 should be themed ;)

---

### Post by castrojo on 2009-06-08
Don't forget to add your hardware to the wiki page!

---

### Post by MacUntu on 2009-06-08
Done (passed). :)

---

### Post by super.rad on 2009-06-08
Am I the only one who is being told that grub will be removed to install grub2?

---

### Post by MacUntu on 2009-06-08
Grub2 depends on grub-pc which replaces grub, so that's ok (I guess :D).

---

### Post by super.rad on 2009-06-08
oh well i'll give it a go an find out, if the worst happens i'll reinstall tomorrow (which will have grub2 anyway haha)
EDIT: All went fine, also detected and added my arch and foresight installs (something grub-legacy has never done)

---

### Post by ronacc on 2009-06-08
failed miserbably on my gigabyte ga-m55plus-s3g   MOBO desktop (multiboot) , didn't find all of my installs, only added karmic to the menu ,won't boot, file not found error ,booted live cd , found that grub2 had written the wrong uuid for my karmic install , copied the correct boot stanza from my backup menu.lst, won't chainload but atleast I can get back into karmic . continuing to troubleshoot .

edit : copied correct uuid to the chainloader line and now it chainloads , seems slower that the old grub and even thoug it found ( the installer said it did) 2 of my other 3 installs it did not add them to the boot list .

---

### Post by inportb on 2009-06-08
Yarrrgh, passed and posted.

---

### Post by cariboo on 2009-06-08
Using the chainloader it passed, but after running:

```
sudo upgrade-from-grub-legacy
```

I get a grub error 15

---

### Post by autocrosser on 2009-06-08
Worked well--detected all 5 of my installs---chainloaded correctly & replaced grub without problems--I7-920--Gigabyte GA-EX58-UD4P w/6G ram & 1.5TB worth of drives---I think it's a win!!!! :D

---

### Post by inportb on 2009-06-08
Yeah, but there's one fail so far.

Oh yeah, I'd be interested in theming this thing as well... lol.

---

### Post by syko21 on 2009-06-08
passed and posted on the wiki page

---

### Post by ranch hand on 2009-06-08
Is this going to be used in 9.10alpha2?  Or is this just for daily builds for now?

I will be glad to try it but I want to use it for real and right now I am on alpha1-32.  I intend to install alpha2-64 when it comes out.

Grub is one thing I am a fan of so if I need to go back to the daily build I will just to try it out.

---

### Post by geojorg on 2009-06-08
Just try it out, and it did work OK on Dell Inspiron 1420 with ext4, already in the wiki. Now i would try it out on HP DV6000

---

### Post by ghindo on 2009-06-09
> **geojorg said:**
> Just try it out, and it did work OK on Dell Inspiron 1420 with ext4, already in the wiki.Sweet, that's my exact setup.  I'll give it a go when I get some free time. :KS

**EDIT:**  Tried it with my Dell Inspiron 1420 64-bit Karmic installation on ext4, everything works great!

Now I just gotta figure out how to reduce the timeout...

---

### Post by davideotape on 2009-06-09
Time for a ```
sudo remastersys backup
```, just incase everything fails :D

---

### Post by davideotape on 2009-06-09
Chainloaded grub 2, but it said it was going into recovery mode. Then, after a wait of about 15 seconds, the menu came up and everything worked fine. One feature I do miss is using the right arrow key to boot. I'm so used to it that I thought something was wrong when it did nothing :(

---

### Post by twigusa on 2009-06-09
My machine (IBM Thinkcentre A50) passed fine. However (and this may be unrelated) the machine is now constantly trying to access the floppy drive. Haven't rebooted it for a while and it may be another issue causing this but thought I ought to mention it.

---

### Post by gnomeuser on 2009-06-09
installed and ran the upgrade script.. nothing blew up. kinda anticlimatic really.

---

### Post by meeples on 2009-06-09
done. passed. and added to the wiki :D

---

### Post by davideotape on 2009-06-09
After chainloading grub2 fine, replacing legacy with 2 did not work. Does anyone know how I can go about reinstalling legacy back onto the hard drive from a liveCD?

---

### Post by inportb on 2009-06-09
> **davideotape said:**
> After chainloading grub2 fine, replacing legacy with 2 did not work. Does anyone know how I can go about reinstalling legacy back onto the hard drive from a liveCD?

Hmm... found this thread: [http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

---

### Post by zika on 2009-06-09
what are the rules of changing settings now with grub2? what do I have to do to change order, timeout etc. that was done in /boot/grub/menu.lst ...? is there a new version of Start-UpManager ... ?

---

### Post by sisco311 on 2009-06-09
> **zika said:**
> what are the rules of changing settings now with grub2? what do I have to do to change order, timeout etc. that was done in /boot/grub/menu.lst ...? is there a new version of Start-UpManager ... ?

[s]/boot/grub/grub.cfg[/s] 

[s]and[/s] you can change settings with StartUp-Manager, unfortunately some features are not implemented yet. 

[https://bugs.launchpad.net/startup-manager/+bug/312933]("https://bugs.launchpad.net/startup-manager/+bug/312933")

---

### Post by taavikko on 2009-06-09
Added my 0.02$ worth.
Asus P6T dlx V2 and hp dv-5 (laptop) both works.

Now just let the devs tweak it to the maximum...

---

### Post by cecilpierce on 2009-06-09
i cant even boot from a cd to reinstall grub, all i have now is win xp, bummer! any ideas ?

---

### Post by MacUntu on 2009-06-09
> **sisco311 said:**
> /boot/grub/grub.cfg
That's a read only file telling you NOT to edit it directly. ):P

Configuration is done via the templates in /etc/grub.d/ and the defaults in /etc/defaults/grub.

I liked the old way much more... feels kinda over-engineered now.

---

### Post by pferraro on 2009-06-09
> **sisco311 said:**
> /boot/grub/grub.cfg

This is an auto-generated file.  Don't edit this file - you'll loose your changes the next time update-grub is run (e.g. after kernel update).  Instead, your configuration changes belong in: /etc/default/grub

---

### Post by zika on 2009-06-09
> **pferraro said:**
> This is an auto-generated file.  Don't edit this file - you'll loose your changes the next time update-grub is run (e.g. after kernel update).  Instead, your configuration changes belong in: /etc/default/grub
Thank You. I found out that for myself. But there is a problem: StartUp-Manager pretends it knows how to work with grub2 ... and in real life it does not. I had problems with vga modes for splash and text and I somehow got that in order ...
So:
1. edit /etc/default/grub
2. sudo update-grub

(I needed that because I use rootflags=data=ordered on ext4 to prevent (as much as possible) data-loss.

What is the difference between lines:
GRUB_CMDLINE_LINUX_DEFAULT=(defoptions?)
and
GRUB_CMDLINE_LINUX=(=altoptions?)
?

---

### Post by sisco311 on 2009-06-09
> **MacUntu said:**
> That's a read only file telling you NOT to edit it directly. ):P

Configuration is done via the templates in /etc/grub.d/ and the defaults in /etc/defaults/grub.

I liked the old way much more... feels kinda over-engineered now.

> **pferraro said:**
> This is an auto-generated file.  Don't edit this file - you'll loose your changes the next time update-grub is run (e.g. after kernel update).  Instead, your configuration changes belong in: /etc/default/grub

Thanks for the info. (I'm new to grub2.) :)

---

### Post by Gourgi on 2009-06-09
> If one can boot from grub2 successfully, one can then install grub2 onto the system as the main boot loader using the command:

```
sudo upgrade-from-grub-legacy
```
the above command installs grub2 to the wrong partition for me
(i want it installed in sdc but it installed it in sda)
 and after that sda gives me an 'error 15' while sdc gives legacy chainload again :roll:

does this means native grub2 install fails ?

---

### Post by davideotape on 2009-06-09
> **Gourgi said:**
> the above command installs grub2 to the wrong partition for me
(i want it installed in sdc but it installed it in sda)
 and after that sda gives me an 'error 15' while sdc gives legacy chainload again :roll:

does this means native grub2 install fails ?

That's exactly the same problem I ran into. However, my sdc grub legacy complained because grub2 did something with menu.lst. I would file a bugreport on this, but I'm on my iPod touch and 1. ubuntu-bug won't work for some reason and 2. Trying to use launchpad on this device is like trying to use vista (clunky, slow and generally horrible ;) )

---

### Post by afv on 2009-06-09
> **super.rad said:**
> 
…
EDIT: The instructions say to install grub2 which will set it up in parallel to grub-legacy but apt is saying it needs to remove grub to install grub2


It will "remove" grub but it will be there when you reboot. :)

Wiki updated. Asus F3Jc passed.

---

### Post by ronacc on 2009-06-09
use my bug [https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/385021](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/385021)  , I installed grub2 from my karmic install on sdd1 it actualy installed to sda1 resulting in a file not found error due to writing the uuid for sda1 into both the chainloader and the bootstanzas , editing to correct the uuid allowed me to boot .

---

### Post by super.rad on 2009-06-09
Just did a fresh install from todays daily image, installing grub2 failed giving an error about "not able to install grub to /target/" tried repeating that step a few times but didn't work so had to install grub-legacy instead. Will try running the update script now (should work fine as I did it last night and wen't ok)
EDIT: Upgrade script ran fine (details are already on wiki page)

---

### Post by super.rad on 2009-06-09
Next question, grub2 is currently installed to the MBR but I want to reinstall it to sda5 (ubuntu's root).
Usually I would do:
```
sudo grub
root (hd0,4)
setup (hd0,4)
```
but doing that now gives me
```
sudo: grub: command not found
```

---

### Post by knarf on 2009-06-09
> **twigusa said:**
> My machine (IBM Thinkcentre A50) passed fine. However (and this may be unrelated) the machine is now constantly trying to access the floppy drive

That is caused by a bug in devkit-disks which insists on polling a non-existing floppy drive. A workaround exists: edit /etc/modprobe.d/blacklist.conf and add the line ```
blacklist floppy
``` Save the file and update the ramdisks:```
sudo update-initramfs -u
``` The bug should be gone on the next boot. If you don't want to reboot just to get rid of those messages you can kill *devkit-disks-daemon*...

---

### Post by pferraro on 2009-06-09
> **zika said:**
> Thank You. I found out that for myself. But there is a problem: StartUp-Manager pretends it knows how to work with grub2 ... and in real life it does not. I had problems with vga modes for splash and text and I somehow got that in order ...
So:
1. edit /etc/default/grub
2. sudo update-grub

(I needed that because I use rootflags=data=ordered on ext4 to prevent (as much as possible) data-loss.

What is the difference between lines:
GRUB_CMDLINE_LINUX_DEFAULT=(defoptions?)
and
GRUB_CMDLINE_LINUX=(=altoptions?)
?

The GRUB_CMDLINE_LINUX variable contains values you want to add to your linux command line for both normal boot, and recovery boot (i.e. single user mode).
The GRUB_CMDLINE_LINUX_DEFAULT variable contains values you want to add to your linux command line for normal boot only.

e.g.
If my /etc/default/grub contains:
GRUB_CMDLINE_LINUX="quiet"
GRUB_CMDLINE_LINUX_DEFAULT="splash vga=873"

this will generate the following in /boot/grub/grub.cfg:

menuentry "Ubuntu GNU/Linux, linux 2.6.30-8-generic" {
	set root=(hd0,1)
	search --fs-uuid --set fe94dc8b-c46a-4513-b3a8-df6ce5ebf206
	linux	/boot/vmlinuz-2.6.30-8-generic root=UUID=fe94dc8b-c46a-4513-b3a8-df6ce5ebf206 ro quiet splash vga=873 
	initrd	/boot/initrd.img-2.6.30-8-generic
}
menuentry "Ubuntu GNU/Linux, linux 2.6.30-8-generic (recovery mode)" {
	set root=(hd0,1)
	search --fs-uuid --set fe94dc8b-c46a-4513-b3a8-df6ce5ebf206
	linux	/boot/vmlinuz-2.6.30-8-generic root=UUID=fe94dc8b-c46a-4513-b3a8-df6ce5ebf206 ro single quiet
	initrd	/boot/initrd.img-2.6.30-8-generic
}

---

### Post by Gourgi on 2009-06-09
> **davideotape said:**
> That's exactly the same problem I ran into. However, my sdc grub legacy complained because grub2 did something with menu.lst. I would file a bugreport on this, but I'm on my iPod touch and 1. ubuntu-bug won't work for some reason and 2. Trying to use launchpad on this device is like trying to use vista (clunky, slow and generally horrible ;) )

```
sudo grub-install /dev/sdc 
```
did the trick here.
no other errors occured 
also all others distros recognised fine by grub2
i'm going to update the wiki

---

### Post by super.rad on 2009-06-09
> **Gourgi said:**
> ```
sudo grub-install /dev/sdc 
```did the trick here.
no other errors occured 
also all others distros recognised fine by grub2
i'm going to update the wiki

thanks that solved my question aswell.

---

### Post by ronacc on 2009-06-09
I think what is happening is that grub2 is picking up the uuid of the first bootable drive on your system rather than the drive it was installed from if you don't specify which drive to use .

---

### Post by zika on 2009-06-10
With Grub2 the infamous message (soft reset failed ...) is gone ... :) I feel relieved cause that message made me wonder all the time is it a bug or is it a HDD ... :)

---

### Post by Incognito-Here on 2009-06-10
Doesn't work for me, shows ERROR 15 and stop.

---

### Post by autocrosser on 2009-06-10
Well-I first reported that everything passed, but I didn't check deep enough--I went to one of my alternate installs & got an error message "kernel needed to be loaded first"---upon further checking, I found that my alternate installs had been assigned wrong id #'s--a very hard thing to change I am finding out.....Bug posted:

[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/385500](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/385500)

---

### Post by Slug71 on 2009-06-10
Is Grub2 default in the daily builds yet?

---

### Post by inportb on 2009-06-10
I should think so, reading the linked page.

---

### Post by whoop on 2009-06-10
> **Slug71 said:**
> Is Grub2 default in the daily builds yet?

Yes it is...

---

### Post by zika on 2009-06-10
Should:```
Warning: update-grub_lib is deprecated, use grub-mkconfig_lib instead
``` in output when running **update-grub** make me worried ...?

---

### Post by whoop on 2009-06-10
I get "Error 11: Unrecognized device string \n Press any key to continue" After installing grub2 (chainloaded) on jaunty in a vmware guest.. It does seem to go well after I press any key...

---

### Post by Slug71 on 2009-06-10
> **whoop said:**
> Yes it is...

Thanks:)

---

### Post by whoop on 2009-06-10
> **davideotape said:**
> One feature I do miss is using the right arrow key to boot. I'm so used to it that I thought something was wrong when it did nothing :(

This does work for me in grub2 (didn't check when I was still chainloading).

I use this too.

---

### Post by Slug71 on 2009-06-10
Installed the Daily Build and Grub failed to install to MBR, tried reverting to Grub Legacy and that to failed. Had to get going with LILO.

---

### Post by super.rad on 2009-06-10
> **Slug71 said:**
> Installed the Daily Build and Grub failed to install to MBR, tried reverting to Grub Legacy and that to failed. Had to get going with LILO.

So you're back with ubuntu then, what happened to foresight? :p
Grub2 failed with me on the daily image yesterday, managed to install grub-legacy though and then update it but then screwed up something trying to reinstall it to another partition, gonna wait till alpha 2 tomorrow then try installing again

---

### Post by Slug71 on 2009-06-10
> **super.rad said:**
> So you're back with ubuntu then, what happened to foresight? :p
Grub2 failed with me on the daily image yesterday, managed to install grub-legacy though and then update it but then screwed up something trying to reinstall it to another partition, gonna wait till alpha 2 tomorrow then try installing again

Yeh my wireless wasnt working in Foresight and some other things with GDM werent either. The DVD iso finished with errors though and figured i may as well wait till it has EXT4. Good OS none the less.

Will test with Grub2 for a while and then who knows.

---

### Post by super.rad on 2009-06-10
> **Slug71 said:**
> Yeh my wireless wasnt working in Foresight and some other things with GDM werent either. The DVD iso finished with errors though and figured i may as well wait till it has EXT4. Good OS none the less.

Will test with Grub2 for a while and then who knows.

Yeah the lack of EXT4 is annoying, also the forums are dead.

---

### Post by Slug71 on 2009-06-10
> **super.rad said:**
> Yeah the lack of EXT4 is annoying, also the forums are dead.

VERY dead. :)

---

### Post by Slug71 on 2009-06-10
> **Slug71 said:**
> Installed the Daily Build and Grub failed to install to MBR, tried reverting to Grub Legacy and that to failed. Had to get going with LILO.

I probably forgot to do something but i uninstalled LILO, installed Grub Legacy, rebooted and it still booted with LILO.

Then went and installed Grub2 and ran

```
sudo os-prober

sudo update-grub
```

picked up my Vista partition, rebooted and wham, Grub2 is in action and both OSs boot. :popcorn:

---

### Post by djuliette on 2009-06-10
changing root to uuid works when chainloading.  Does this mean it is ok to install, or is there something else to do to permanently change 'root' to 'uuid'?

Also in the future if I install a new kernel will it automatically update the grub2 menu?

---

### Post by whoop on 2009-06-10
> **djuliette said:**
> changing root to uuid works when chainloading.  Does this mean it is ok to install, or is there something else to do to permanently change 'root' to 'uuid'?

Also in the future if I install a new kernel will it automatically update the grub2 menu?

Worst case scenario you'll have to sudo update-grub

---

### Post by djuliette on 2009-06-10
Went ahead and did it, works perfectly on an aspire 5735, will update the wiki.

---

### Post by lonniehenry on 2009-06-10
worked on HP DV9005US with no problem.  Added to wiki.

---

### Post by djuliette on 2009-06-10
OK, it installed and boots perfectly, but how do I configure it?

Startup Manager did allow me to set the default os to boot, but is it possible to change the text description and the order of the operating systems?

And is it possible to add a background image (by adding a line to /etc/default/grub maybe?)

---

### Post by autocrosser on 2009-06-10
Look at my thread about Grub2 theming..... [http://ubuntuforums.org/showthread.php?t=1182436](http://ubuntuforums.org/showthread.php?t=1182436)

We have some ideas & I have contacted the dev that is doing gfxmenu for Grub2 about it.....

---

### Post by djuliette on 2009-06-10
> **autocrosser said:**
> Look at my thread about Grub2 theming..... [http://ubuntuforums.org/showthread.php?t=1182436](http://ubuntuforums.org/showthread.php?t=1182436)

We have some ideas & I have contacted the dev that is doing gfxmenu for Grub2 about it.....

Thanks autocrosser, I've got a background image now!

---

### Post by ricsi-pontaz on 2009-06-11
My Acer Aspire 3055 passed and i added to the wiki!

---

### Post by durand on 2009-06-11
Is the root filesystem the one with the kernels or the one that ubuntu is on? I have 8 OSs installed and the installer detected 6 of them, missing out gentoo and sabayon.

---

### Post by taavikko on 2009-06-11
Anybody else having these on "dmesg" after grub-update is been runned?
```
[22769.495849] SGI XFS with ACLs, security attributes, realtime, large block/inode numbers, no debug enabled                                                                                                        
[22769.496896] SGI XFS Quota Management subsystem                                                         
[22769.521918] JFS: nTxBlock = 8192, nTxLock = 65536                                                      
[22769.559584] NTFS driver 2.1.29 [Flags: R/O MODULE].                                                    
[22769.608041] QNX4 filesystem 0.2.3 registered.                                                          
[22769.792180] attempt to access beyond end of device                                                     
[22769.792184] sda3: rw=0, want=4, limit=2                                                                
[22769.792187] EXT3-fs: unable to read superblock                                                         
[22769.813928] attempt to access beyond end of device                                                     
[22769.813932] sda3: rw=0, want=4, limit=2                                                                
[22769.813935] EXT2-fs: unable to read superblock                                                         
[22769.816181] attempt to access beyond end of device                                                     
[22769.816185] sda3: rw=0, want=4, limit=2                                                                
[22769.816188] EXT4-fs: unable to read superblock                                                         
[22769.818445] cramfs: wrong magic                                                                        
[22769.904734] attempt to access beyond end of device                                                     
[22769.904738] sda3: rw=0, want=18, limit=2                                                               
[22769.904743] REISERFS warning (device sda3): sh-2006 read_super_block: bread failed (dev sda3, block 8, size 1024)                                                                                                
[22769.904748] attempt to access beyond end of device                                                     
[22769.904751] sda3: rw=0, want=130, limit=2                                                              
[22769.904755] REISERFS warning (device sda3): sh-2006 read_super_block: bread failed (dev sda3, block 64, size 1024)                                                                                               
[22769.904758] REISERFS warning (device sda3): sh-2021 reiserfs_fill_super: can not find reiserfs on sda3 
[22769.907056] attempt to access beyond end of device                                                     
[22769.907060] sda3: rw=0, want=8, limit=2                                                                
[22769.907065] XFS: SB read failed                                                                        
[22769.911545] attempt to access beyond end of device                                                     
[22769.911549] sda3: rw=0, want=72, limit=2                                                               
[22769.911553] attempt to access beyond end of device                                                     
[22769.911556] sda3: rw=0, want=128, limit=2                                                              
[22769.914049] FAT: bogus number of reserved sectors                                                      
[22769.914053] VFS: Can't find a valid FAT filesystem on dev sda3.                                        
[22769.916559] FAT: bogus number of reserved sectors                                                      
[22769.916562] VFS: Can't find a valid FAT filesystem on dev sda3.                                        
[22769.923577] attempt to access beyond end of device                                                     
[22769.923580] sda3: rw=0, want=4, limit=2                                                                
[22769.923583] MINIX-fs: unable to read superblock                                                        
[22769.947563] attempt to access beyond end of device                                                     
[22769.947567] sda3: rw=0, want=3, limit=2                                                                
[22769.947570] hfs: unable to find HFS+ superblock                                                        
[22769.950095] qnx4: wrong fsid in superblock.                                                            
[22769.952359] You didn't specify the type of your ufs filesystem                                         
[22769.952361]                                                                                            
[22769.952362] mount -t ufs -o ufstype=sun|sunx86|44bsd|ufs2|5xbsd|old|hp|nextstep|nextstep-cd|openstep ...                                                                                                         
[22769.952363]                                                                                            
[22769.952364] >>>WARNING<<< Wrong ufstype may corrupt your filesystem, default is ufstype=old            
[22769.952372] attempt to access beyond end of device                                                     
[22769.952375] sda3: rw=0, want=18, limit=2                                                               
[22769.954606] attempt to access beyond end of device                                                     
[22769.954610] sda3: rw=0, want=3, limit=2                                                                
[22769.954613] hfs: can't find a HFS filesystem on dev sda3.                                              
[176379.695528] attempt to access beyond end of device                                                    
[176379.695532] sda3: rw=0, want=4, limit=2                                                               
[176379.695535] EXT3-fs: unable to read superblock                                                        
[176379.697862] attempt to access beyond end of device                                                    
[176379.697866] sda3: rw=0, want=4, limit=2                                                               
[176379.697868] EXT2-fs: unable to read superblock                                                        
[176379.700158] attempt to access beyond end of device                                                    
[176379.700162] sda3: rw=0, want=4, limit=2                                                               
[176379.700165] EXT4-fs: unable to read superblock                                                        
[176379.702427] cramfs: wrong magic                                                                       
[176379.806786] attempt to access beyond end of device                                                    
[176379.806790] sda3: rw=0, want=18, limit=2                                                              
[176379.806796] REISERFS warning (device sda3): sh-2006 read_super_block: bread failed (dev sda3, block 8, size 1024)                                                                                               
[176379.806801] attempt to access beyond end of device                                                    
[176379.806804] sda3: rw=0, want=130, limit=2                                                             
[176379.806808] REISERFS warning (device sda3): sh-2006 read_super_block: bread failed (dev sda3, block 64, size 1024)                                                                                              
[176379.806811] REISERFS warning (device sda3): sh-2021 reiserfs_fill_super: can not find reiserfs on sda3
[176379.809250] attempt to access beyond end of device                                                    
[176379.809254] sda3: rw=0, want=8, limit=2                                                               
[176379.809259] XFS: SB read failed                                                                       
[176379.814306] attempt to access beyond end of device                                                    
[176379.814310] sda3: rw=0, want=72, limit=2                                                              
[176379.814314] attempt to access beyond end of device                                                    
[176379.814317] sda3: rw=0, want=128, limit=2                                                             
[176379.817353] FAT: bogus number of reserved sectors                                                     
[176379.817357] VFS: Can't find a valid FAT filesystem on dev sda3.                                       
[176379.819882] FAT: bogus number of reserved sectors                                                     
[176379.819887] VFS: Can't find a valid FAT filesystem on dev sda3.                                       
[176379.827284] attempt to access beyond end of device                                                    
[176379.827288] sda3: rw=0, want=4, limit=2                                                               
[176379.827290] MINIX-fs: unable to read superblock                                                       
[176379.829578] attempt to access beyond end of device                                                    
[176379.829582] sda3: rw=0, want=3, limit=2                                                               
[176379.829585] hfs: unable to find HFS+ superblock                                                       
[176379.832754] qnx4: wrong fsid in superblock.                                                           
[176379.835012] You didn't specify the type of your ufs filesystem                                        
[176379.835013]                                                                                           
[176379.835014] mount -t ufs -o ufstype=sun|sunx86|44bsd|ufs2|5xbsd|old|hp|nextstep|nextstep-cd|openstep ...                                                                                                        
[176379.835016]                                                                                           
[176379.835016] >>>WARNING<<< Wrong ufstype may corrupt your filesystem, default is ufstype=old           
[176379.835025] attempt to access beyond end of device                                                    
[176379.835028] sda3: rw=0, want=18, limit=2                                                              
[176379.837297] attempt to access beyond end of device                                                    
[176379.837301] sda3: rw=0, want=3, limit=2                                                               
[176379.837304] hfs: can't find a HFS filesystem on dev sda3.                                             
[199029.673009] attempt to access beyond end of device                                                    
[199029.673014] sda3: rw=0, want=4, limit=2                                                               
[199029.673016] EXT3-fs: unable to read superblock                                                        
[199029.692904] attempt to access beyond end of device                                                    
[199029.692908] sda3: rw=0, want=4, limit=2                                                               
[199029.692911] EXT2-fs: unable to read superblock                                                        
[199029.695202] attempt to access beyond end of device                                                    
[199029.695206] sda3: rw=0, want=4, limit=2                                                               
[199029.695209] EXT4-fs: unable to read superblock                                                        
[199029.697476] cramfs: wrong magic                                                                       
[199029.754347] attempt to access beyond end of device
[199029.754351] sda3: rw=0, want=18, limit=2
[199029.754357] REISERFS warning (device sda3): sh-2006 read_super_block: bread failed (dev sda3, block 8, size 1024)
[199029.754362] attempt to access beyond end of device
[199029.754365] sda3: rw=0, want=130, limit=2
[199029.754369] REISERFS warning (device sda3): sh-2006 read_super_block: bread failed (dev sda3, block 64, size 1024)
[199029.754373] REISERFS warning (device sda3): sh-2021 reiserfs_fill_super: can not find reiserfs on sda3
[199029.756901] attempt to access beyond end of device
[199029.756906] sda3: rw=0, want=8, limit=2
[199029.756910] XFS: SB read failed
[199029.762361] attempt to access beyond end of device
[199029.762365] sda3: rw=0, want=72, limit=2
[199029.762369] attempt to access beyond end of device
[199029.762372] sda3: rw=0, want=128, limit=2
[199029.764914] FAT: bogus number of reserved sectors
[199029.764918] VFS: Can't find a valid FAT filesystem on dev sda3.
[199029.767435] FAT: bogus number of reserved sectors
[199029.767439] VFS: Can't find a valid FAT filesystem on dev sda3.
[199029.774421] attempt to access beyond end of device
[199029.774425] sda3: rw=0, want=4, limit=2
[199029.774428] MINIX-fs: unable to read superblock
[199029.776690] attempt to access beyond end of device
[199029.776694] sda3: rw=0, want=3, limit=2
[199029.776697] hfs: unable to find HFS+ superblock
[199029.779198] qnx4: wrong fsid in superblock.
[199029.781455] You didn't specify the type of your ufs filesystem
[199029.781457]
[199029.781458] mount -t ufs -o ufstype=sun|sunx86|44bsd|ufs2|5xbsd|old|hp|nextstep|nextstep-cd|openstep ...
[199029.781459]
[199029.781460] >>>WARNING<<< Wrong ufstype may corrupt your filesystem, default is ufstype=old
[199029.781468] attempt to access beyond end of device
[199029.781471] sda3: rw=0, want=18, limit=2
[199029.783773] attempt to access beyond end of device
[199029.783777] sda3: rw=0, want=3, limit=2
[199029.783780] hfs: can't find a HFS filesystem on dev sda3.
```

Older kernel removal or something else that requires grub-update...

---

### Post by jerrylamos on 2009-06-11
Grub2 (1.96, really) doesn't find ANY of my other partitions!  They've got jaunty, karmic, ... on them.  They're still there, just Grub2 doesn't find them.

sudo update-grub didn't do diddly.

The old reliable /boot/grub/menu.lst is gone, replaced by a file they say not to edit, and DO NOT GIVE ANY ALTERNATIVES.

Any ideas?

Thanks, jerry

---

### Post by taavikko on 2009-06-11
> **jerrylamos said:**
> Grub2 (1.96, really) doesn't find ANY of my other partitions!  They've got jaunty, karmic, ... on them.  They're still there, just Grub2 doesn't find them.

sudo update-grub didn't do diddly.

The old reliable /boot/grub/menu.lst is gone, replaced by a file they say not to edit, and DO NOT GIVE ANY ALTERNATIVES.

Any ideas?

Thanks, jerry

grub2 is edited by modifying /etc/default/grub file and the running
upgrade-grub / grub-mkconfig

---

### Post by Slug71 on 2009-06-11
> **jerrylamos said:**
> Grub2 (1.96, really) doesn't find ANY of my other partitions!  They've got jaunty, karmic, ... on them.  They're still there, just Grub2 doesn't find them.

sudo update-grub didn't do diddly.

The old reliable /boot/grub/menu.lst is gone, replaced by a file they say not to edit, and DO NOT GIVE ANY ALTERNATIVES.

Any ideas?

Thanks, jerry

```
sudo os-prober

sudo update-grub
```

---

### Post by pulpo69 on 2009-06-11
worked with an asus M4A79T-motherboard (self build box) with AMD phenom II X4 810.
i couldn't enter the wiki for some reasons so please someone can put in this information there, if not i'll will try it again in a few days.

---

### Post by Kow on 2009-06-11
Update from grub1 Works fine in virtualbox guest on Linux host (Ubuntu jaunty) with 1 hdd and 2 partitions (/ and swap).

---

### Post by LKjell on 2009-06-11
This question may have been answered many times but why do you want to update your grub when grub1 just work for you? When I installed grub2 there were a lot of files in /boot most of them I have no clue what is. I am convinced grub2 take more space too. There is the annoying blue color and 5 sec waiting time to boot, which are easily changable after you find which file to edit in the stack of files in /boot.

---

### Post by autocrosser on 2009-06-11
Hey guys---look in my Grub2 theming thread--you can carefully edit the .cfg file (remembering that it's a temp solution)--to get things right--I have a 5 install system & OS Prober really mucked it up--looks like prober can't understand UUID---so I did labels for all my installs & it all works again........

And as about the move from Grub to Grub2---Grub is VERY long in the tooth & is being replaced with Grub2---so like it or not--Grub2 will be in the future & Grub will be gone....There is always a period from one system to another that is not easy---but WE are Alpha testing after all ;) ;)

---

### Post by autocrosser on 2009-06-11
> **jerrylamos said:**
> Grub2 (1.96, really) doesn't find ANY of my other partitions!  They've got jaunty, karmic, ... on them.  They're still there, just Grub2 doesn't find them.

sudo update-grub didn't do diddly.

The old reliable /boot/grub/menu.lst is gone, replaced by a file they say not to edit, and DO NOT GIVE ANY ALTERNATIVES.

Any ideas?

Thanks, jerry

Jerry---look in my theming thread......;)

And if anyone is having problems with a multi-boot system--look,add to & "me too" this bug report: [https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/385500](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/385500)

---

### Post by super.rad on 2009-06-11
anyone know how to chainload grub2 from grub? Fedora 11 is my main OS so have grub installed to the MBR, Ubuntu is installed on /dev/sda5 and grub2 is installed there. My menu.lst has the following entry
```
title     Ubuntu
root (hd0,4)
chainloader +1
```but when i try to boot I get 
```
Invalid or unsupported executable format
```I also have openSUSE installed on a different partition and can have exactly the same in my menu.lst (obviously different partition) and it works fine so guessing it must be something to do with grub2

EDIT: Also tried
```
title Ubuntu
root (hd0,4)
kernel /boot/grub/core.img
```
but didn't work either, can't remember the exact error (too tired so forgot to right it down) but it was something about it not existing or grub couldn't find it.
Anyony know how I can chainload grub2 from grub or how to reinstall grub2 to the MBR from in Fedora (would prefer the first option)

---

### Post by Slug71 on 2009-06-12
> **super.rad said:**
> anyone know how to chainload grub2 from grub? Fedora 11 is my main OS so have grub installed to the MBR, Ubuntu is installed on /dev/sda5 and grub2 is installed there. My menu.lst has the following entry
```
title     Ubuntu
root (hd0,4)
chainloader +1
```but when i try to boot I get 
```
Invalid or unsupported executable format
```I also have openSUSE installed on a different partition and can have exactly the same in my menu.lst (obviously different partition) and it works fine so guessing it must be something to do with grub2

EDIT: Also tried
```
title Ubuntu
root (hd0,4)
kernel /boot/grub/core.img
```
but didn't work either, can't remember the exact error (too tired so forgot to right it down) but it was something about it not existing or grub couldn't find it.
Anyony know how I can chainload grub2 from grub or how to reinstall grub2 to the MBR from in Fedora (would prefer the first option)

I would uninstall Grub Legacy in Synaptic and then install Grub2 in there too.
During the installation it will ask you if you want to install to the MBR(will have a check box with your MBR drive).

Then run

```
sudo os-prober

sudo update-grub
```

Reboot.

---

### Post by super.rad on 2009-06-12
Found the problem, installer keeps crashing while trying to install grub 2, tried the alpha 2 disc a few times (checked disc and there are no errors) and keeps doing the same, tried todays daily image aswell which does the same and also gives an error if I try to install grub-legacy instead so at the moment I have a fully installed ubuntu that I can't get into

---

### Post by Slug71 on 2009-06-12
> **super.rad said:**
> Found the problem, installer keeps crashing while trying to install grub 2, tried the alpha 2 disc a few times (checked disc and there are no errors) and keeps doing the same, tried todays daily image aswell which does the same and also gives an error if I try to install grub-legacy instead so at the moment I have a fully installed ubuntu that I can't get into

Dont know if you read my post earlier but i had the same problem. I installed LILO and that worked. Then once in, i uninstalled LILO in Synaptic and and made sure Grub and Grub2 was uninstalled and then installed Grub2 from Synaptic and then it worked. Will give you the option during installation to install Grub2 to the MBR. Then if you have any other OSs id run the codes above in Terminal,

```
sudo os-prober

sudo update-grub
```

Reboot.

---

### Post by super.rad on 2009-06-12
managed to install and setup grub2 using the "rescue a broken system" on todays image, it installed to the MBR but hasn't detected fedora or suse, running sudo os-prober gives:
```
mapdevfs: error while loading shared libraries: libdebian-installer.so.4: cannot open shared object file: No such file or directory
mapdevfs: error while loading shared libraries: libdebian-installer.so.4: cannot open shared object file: No such file or directory
mapdevfs: error while loading shared libraries: libdebian-installer.so.4: cannot open shared object file: No such file or directory
mapdevfs: error while loading shared libraries: libdebian-installer.so.4: cannot open shared object file: No such file or directory
mapdevfs: error while loading shared libraries: libdebian-installer.so.4: cannot open shared object file: No such file or directory
mapdevfs: error while loading shared libraries: libdebian-installer.so.4: cannot open shared object file: No such file or directory
mapdevfs: error while loading shared libraries: libdebian-installer.so.4: cannot open shared object file: No such file or directory
mapdevfs: error while loading shared libraries: libdebian-installer.so.4: cannot open shared object file: No such file or directory
mapdevfs: error while loading shared libraries: libdebian-installer.so.4: cannot open shared object file: No such file or directory
mapdevfs: error while loading shared libraries: libdebian-installer.so.4: cannot open shared object file: No such file or directory
mapdevfs: error while loading shared libraries: libdebian-installer.so.4: cannot open shared object file: No such file or directory
```
Is there a file I can edit to manually add fedora and opensuse? Tried /boot/grub/grub.cfg but it wouldnt let me save even as root

---

### Post by ranch hand on 2009-06-12
I installed alpha2, 8.04 and 2 9.04 veriants (SuperOS and Stoner Edition 1.0) were not detected.

Ran "sudo os-prober";
```

kernal@kern-desktop:~$ sudo os-prober
[sudo] password for kernal: 
mapdevfs: error while loading shared libraries: libdebian-installer.so.4: cannot open shared object file: No such file or directory
mapdevfs: error while loading shared libraries: libdebian-installer.so.4: cannot open shared object file: No such file or directory
mapdevfs: error while loading shared libraries: libdebian-installer.so.4: cannot open shared object file: No such file or directory
mapdevfs: error while loading shared libraries: libdebian-installer.so.4: cannot open shared object file: No such file or directory
mapdevfs: error while loading shared libraries: libdebian-installer.so.4: cannot open shared object file: No such file or directory
mapdevfs: error while loading shared libraries: libdebian-installer.so.4: cannot open shared object file: No such file or directory
mapdevfs: error while loading shared libraries: libdebian-installer.so.4: cannot open shared object file: No such file or directory
mapdevfs: error while loading shared libraries: libdebian-installer.so.4: cannot open shared object file: No such file or directory
mapdevfs: error while loading shared libraries: libdebian-installer.so.4: cannot open shared object file: No such file or directory
mapdevfs: error while loading shared libraries: libdebian-installer.so.4: cannot open shared object file: No such file or directory
mapdevfs: error while loading shared libraries: libdebian-installer.so.4: cannot open shared object file: No such file or directory
mapdevfs: error while loading shared libraries: libdebian-installer.so.4: cannot open shared object file: No such file or directory
mapdevfs: error while loading shared libraries: libdebian-installer.so.4: cannot open shared object file: No such file or directory
kernal@kern-desktop:~$ 

```
So this must not be an uncomon problem.

---

### Post by super.rad on 2009-06-12
just got an update for debian-installer so will see if that fixes it
EDIT: Nope same thing still

---

### Post by ranch hand on 2009-06-12
I had some problems with some preferenses and rebooted recovery and then it seemed ok.

Got updates.

Now when I try to boot, normal or recovery, I just get the message that I need to load the kernal first.

I am on another partition (9.04) and just checked the 9.10alpha-2 root partition and everything looks fine.

I edited /etc/default/grub to read'
```
 
GRUB_DISABLE_LINUX_UUID=true

```
as I heard that may be a problem.

I am going to recomment the line as it made no difference.

There must be another place to edit this version of grub so that you can add other OSs.  It is mentioned in the readme in /etc/grub.d but where is this menu?

---

### Post by autocrosser on 2009-06-12
> **ranch hand said:**
> I had some problems with some preferenses and rebooted recovery and then it seemed ok.

Got updates.

Now when I try to boot, normal or recovery, I just get the message that I need to load the kernal first.

I am on another partition (9.04) and just checked the 9.10alpha-2 root partition and everything looks fine.

I edited /etc/default/grub to read'
```
 
GRUB_DISABLE_LINUX_UUID=true

```as I heard that may be a problem.

I am going to recomment the line as it made no difference.

There must be another place to edit this version of grub so that you can add other OSs.  It is mentioned in the readme in /etc/grub.d but where is this menu?



Ranch-hand, that is the problem that I have been working with---you most likely have a motherboard like I do that changes drive order at random intervals---If you look at your grub.cfg, you will most likely find that your main OS is called by UUID & all other OS on your system are called by /dev/sdx.

OS-Prober AT THIS TIME can only work with /dev/sdx, so if your system shifts location of drives---you will get a "kernel needs to be loaded first" error message....Please look at the multi-boot grub2 thread & my grub2 themes thread or the main grub2 thread....I have posted my bug report link & it looks like you need to add to it.....


My comment about only editing the grub.cfg  has this reasoning---there is a commit in the works (saw the commit last night on grub2-developers-list) so OS-Prober can use UUID, but it most likely will not show up for a month or so....by just updating the grub.cfg, you are not modifying any of the main grub2 files...you can just sub in a backup grub.cfg with needed mods until the "fix" comes thru. There is no black magic about the grub.cfg file---I can post my "fixed" file so people can look at it......

---

### Post by ranch hand on 2009-06-12
Actually I have stable drive names (see sig for box).

I had trouble with trying to install anothe OS and someone told me to use VB.  Haven't ever used it.

So I installed Jaunty on the same external (dual SATA - no raid) / on one drive and /home on the other (can only boot from the 1st).  This is the way that 9.10alpha2 is installed.  Jaunty detected all OSs and boots 9.10 (kinky kitten) just fine.

Got the kernal update and updated, booted back into Kinky and edited the Jaunty /boot/grub/menu.lst (changed 3 8s to 3 9s) and rebooted right into the right kernal and everything.

We need to have a good Ubuntu doc on how to use this new grub.  The old one I can do in my sleep (about).  I am sure they will get this one there too.

I haven't read every link that has been posted here yet, I need to but it is on the OS I use the most and I am not there now, later tonight I will do some studying.

At least now I can get to Kinky with no problem and see what else is different than alpha1 (alpha2 is 64, I have alpha1 on another drive in 32).

---

### Post by autocrosser on 2009-06-12
> **ranch hand said:**
> Actually I have stable drive names (see sig for box).

I had trouble with trying to install anothe OS and someone told me to use VB.  Haven't ever used it.

So I installed Jaunty on the same external (dual SATA - no raid) / on one drive and /home on the other (can only boot from the 1st).  This is the way that 9.10alpha2 is installed.  Jaunty detected all OSs and boots 9.10 (kinky kitten) just fine.

Got the kernal update and updated, booted back into Kinky and edited the Jaunty /boot/grub/menu.lst (changed 3 8s to 3 9s) and rebooted right into the right kernal and everything.

We need to have a good Ubuntu doc on how to use this new grub.  The old one I can do in my sleep (about).  I am sure they will get this one there too.

I haven't read every link that has been posted here yet, I need to but it is on the OS I use the most and I am not there now, later tonight I will do some studying.

At least now I can get to Kinky with no problem and see what else is different than alpha1 (alpha2 is 64, I have alpha1 on another drive in 32).


Yes--I can hear that--I remember editing grub 6/7 years ago & X86free vid files--was that fun or what?  I've been doing UNIX (30+ years) & Linux for 7 now---was a mac-man in between------

---

### Post by ronacc on 2009-06-12
yeah it looks like we've got a new learning curve here :lolflag:

---

### Post by Slug71 on 2009-06-13
> **ranch hand said:**
> I installed alpha2, 8.04 and 2 9.04 veriants (SuperOS and Stoner Edition 1.0) were not detected.

Ran "sudo os-prober";
```

kernal@kern-desktop:~$ sudo os-prober
[sudo] password for kernal: 
mapdevfs: error while loading shared libraries: libdebian-installer.so.4: cannot open shared object file: No such file or directory
mapdevfs: error while loading shared libraries: libdebian-installer.so.4: cannot open shared object file: No such file or directory
mapdevfs: error while loading shared libraries: libdebian-installer.so.4: cannot open shared object file: No such file or directory
mapdevfs: error while loading shared libraries: libdebian-installer.so.4: cannot open shared object file: No such file or directory
mapdevfs: error while loading shared libraries: libdebian-installer.so.4: cannot open shared object file: No such file or directory
mapdevfs: error while loading shared libraries: libdebian-installer.so.4: cannot open shared object file: No such file or directory
mapdevfs: error while loading shared libraries: libdebian-installer.so.4: cannot open shared object file: No such file or directory
mapdevfs: error while loading shared libraries: libdebian-installer.so.4: cannot open shared object file: No such file or directory
mapdevfs: error while loading shared libraries: libdebian-installer.so.4: cannot open shared object file: No such file or directory
mapdevfs: error while loading shared libraries: libdebian-installer.so.4: cannot open shared object file: No such file or directory
mapdevfs: error while loading shared libraries: libdebian-installer.so.4: cannot open shared object file: No such file or directory
mapdevfs: error while loading shared libraries: libdebian-installer.so.4: cannot open shared object file: No such file or directory
mapdevfs: error while loading shared libraries: libdebian-installer.so.4: cannot open shared object file: No such file or directory
kernal@kern-desktop:~$ 

```
So this must not be an uncomon problem.

Check if os-prober is installed. Kinda seems like it isnt.

to install, i think its

sudo apt-get install os-prober

---

### Post by _oOMOo_ on 2009-06-13
This fixed it for me

```

sudo apt-get install --reinstall libdebian-installer4
sudo os-prober
sudo update-grub

```

---

### Post by ranch hand on 2009-06-13
_oOMOo_
```

kernal@kern-desktop:~$ sudo apt-get install --reinstall libdebian-installer4
[sudo] password for kernal: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.30-8 linux-headers-2.6.30-8-generic
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 0 not upgraded.
Need to get 30.2kB of archives.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/main libdebian-installer4 0.62ubuntu1 [30.2kB]
Fetched 30.2kB in 1s (28.5kB/s)              
(Reading database ... 123953 files and directories currently installed.)
Preparing to replace libdebian-installer4 0.62ubuntu1 (using .../libdebian-installer4_0.62ubuntu1_amd64.deb) ...
Unpacking replacement libdebian-installer4 ...
Setting up libdebian-installer4 (0.62ubuntu1) ...

Processing triggers for libc6 ...
ldconfig deferred processing now taking place
kernal@kern-desktop:~$ sudo os-prober
/dev/sda1:Ubuntu 8.04.2 (8.04):Ubuntu:linux
/dev/sda6:Ubuntu 9.04 (9.04):Ubuntu1:linux
/dev/sda7:Ubuntu 9.04 (9.04):Ubuntu2:linux
/dev/sda9:Ubuntu 9.04 (9.04):Ubuntu3:linux
kernal@kern-desktop:~$ sudo update-grub
error: cannot open `/dev/sdf' while attempting to get disk size
error: cannot open `/dev/sdf' while attempting to get disk size
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.30-9-generic
Found initrd image: /boot/initrd.img-2.6.30-9-generic
error: cannot open `/dev/sdf' while attempting to get disk size
error: cannot open `/dev/sdf' while attempting to get disk size
grub-probe: error: Cannot find a GRUB drive for /dev/sda8.  Check your device.map.

error: cannot open `/dev/sdf' while attempting to get disk size
error: cannot open `/dev/sdf' while attempting to get disk size
grub-probe: error: Cannot find a GRUB drive for /dev/sda8.  Check your device.map.

Found linux image: /boot/vmlinuz-2.6.30-8-generic
Found initrd image: /boot/initrd.img-2.6.30-8-generic
error: cannot open `/dev/sdf' while attempting to get disk size
error: cannot open `/dev/sdf' while attempting to get disk size
grub-probe: error: Cannot find a GRUB drive for /dev/sda8.  Check your device.map.

error: cannot open `/dev/sdf' while attempting to get disk size
error: cannot open `/dev/sdf' while attempting to get disk size
grub-probe: error: Cannot find a GRUB drive for /dev/sda8.  Check your device.map.

Warning: update-grub_lib is deprecated, use grub-mkconfig_lib instead
Found memtest86+ image: /boot/memtest86+.bin
Found Ubuntu 8.04.2 (8.04) on /dev/sda1
kernal@kern-desktop:~$ 

```
I don't think this is going to work in multi boot for a while yet.  I think i better look at this grub-mkconfig_lib too.

---

### Post by shakaran on 2009-06-13
Toshiba Satellite M60-126 tested & passed. Added to wiki.

I can't wait for themes on grub2 ;)

---

### Post by jerrylamos on 2009-06-13
> **_oOMOo_ said:**
> This fixed it for me

```

sudo apt-get install --reinstall libdebian-installer4
sudo os-prober
sudo update-grub

```

Worked for me on one of my pc's, Thinkpad T40, will try on Compaq Presario as soon as I get the chance.

Usual bunch of messages which I read and ignored.  My other OS's are jaunty & karmic just in case an update screws one of the images.  Happens.

How do we get the word out?

Jerry

---

### Post by autocrosser on 2009-06-13
> **shakaran said:**
> Toshiba Satellite M60-126 tested & passed. Added to wiki.

I can't wait for themes on grub2 ;)

Take a look at my theme thread----http://ubuntuforums.org/showthread.php?t=1182436

---

### Post by shakaran on 2009-06-13
> **autocrosser said:**
> Take a look at my theme thread----http://ubuntuforums.org/showthread.php?t=1182436

Thanks, I had seen it, and I asked for some .debs ;)

---

### Post by autocrosser on 2009-06-13
> **shakaran said:**
> Thanks, I had seen it, and I asked for some .debs ;)

Cool--We will just have to wait---Talking with the GFXMenu developer--there "should" be a commit soon to make things look much better......

---

### Post by linux6994 on 2009-06-14
IBM T40 Passed and tested

---

### Post by tad1073 on 2009-06-14
I successfully installed grub2, now what file do I need to edit to change "timeout=5 t" so it will not select after 5 seconds , add vga=795 and change the colors of the text and the box around the text.

---

### Post by autocrosser on 2009-06-14
> **tad1073 said:**
> I successfully installed grub2, now what file do I need to edit to change "timeout=5 t" so it will not select after 5 seconds , add vga=795 and change the colors of the text and the box around the text.

Take a look at my theme thread----http://ubuntuforums.org/showthread.php?t=1182436

You will find some, but not all answers there--remember, Grub2 is a "work in progress"

---

### Post by tad1073 on 2009-06-14
> **autocrosser said:**
> Take a look at my theme thread----http://ubuntuforums.org/showthread.php?t=1182436

You will find some, but not all answers there--remember, Grub2 is a "work in progress"
got vga=795 set, but when I commented out timeout=5, it didn't work

---

### Post by autocrosser on 2009-06-14
I guess that we will have to wait for SUM to be updated to really work with it......

---

### Post by freeman2000 on 2009-06-14
Works so far on an HP dv6000t laptop, dual-booting Karmic & Win Vista SP2. 
Unable to update wiki as you requested.

---

### Post by davideotape on 2009-06-14
> **Gourgi said:**
> ```
sudo grub-install /dev/sdc 
```
did the trick here.
no other errors occured 
also all others distros recognised fine by grub2
i'm going to update the wiki

Thank you very much for that, solved all of my grub problems :D

---

### Post by SoCalChris on 2009-06-15
I'm still running Jaunty, but tried installing Grub2 using the directions on the wiki. I had to change the string in the menu.list file from root to uuid before I was able to boot into any of the existing kernels with grub.

When I try to chainload into grub2, I get an error message that is displayed for a split second, and them am dumped to a grub command prompt. The error flashes by before I can even attempt to read it, so I have no idea what it is saying.

sda1 is formatted as ext4, and contains everything except my home directory. sda3 is my home directory, and is formatted as XFS.

This is the chainloader section of my menu.lst.

```
title		Chainload into GRUB 2
uuid		4a61e2e1-9fc1-4eb4-a347-ccdb6f60db6c
kernel		/boot/grub/core.img

```

Any suggestions? Thanks

---

### Post by dino99 on 2009-06-15
with jaunty, i got this error "alloc magic is broken" on one of my partition, can't find a workaround. Do you think i can use grub-pc & os-prober from karmic or sid with jaunty ?

---

### Post by Gourgi on 2009-06-15
> **SoCalChris said:**
> 
This is the chainloader section of my menu.lst.

```
title		Chainload into GRUB 2
uuid		4a61e2e1-9fc1-4eb4-a347-ccdb6f60db6c
kernel		/boot/grub/core.img

```

Any suggestions? Thanks
chainload works here as you posted
try to pause the screen in order to read the error message

---

### Post by Phreaker on 2009-06-16
I can report perfect execution on my system
Mainboard is Gigabyte P35-DS4 rev. 1.0
BIOS version: F13
running ext4 as main root partition

---

### Post by excogitation on 2009-06-17
Tried it on Jaunty on a MSI Wind U100 - ran into these (known) problems (or annoyances):

[LIST]
[*]no savedefault [#216178]("https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/216178")
[*]different timeout than in grub [#386789]("https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/386789")
[*]root/uuid [#376879]("https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/376879")
[*]no entry for OS X in Jaunty[#388135]("https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/388135") (trying if it works in Karmic atm)
[/LIST]

Also on an Abit IL-90MV I can only get Karmic to boot
(bootloader on /sda Karmic on /sda2 (hd0,1))
but not Windows Server 2003 (on /sdc3 (hd3,2)) which might be bios related though (IDE/SATA problem?).

---

### Post by Regenweald on 2009-06-17
Did a blind upgrade, no chainload test, rebooted and got an error 15. Simple problem though, used live cd to edit menu.lst and change default root drive from hd0,0 to hd2,0. Not grub2's fault, I just need to properly re-organise my drives.
On boot i get a message about a BIOS update involving PowerNow. Will look into it further and see if dell has any updates waiting for me.

Edit: No updates available, I'm on the latest BIOS they have :( not a major problem though, I still boot fine.

---

### Post by dino99 on 2009-08-10
hi,
I have this problem, like yours, have you found a solution? I can't find on the net: it's an Karmic grub-pc/os-prober menu on multiboot & jaunty is complaining (of course no ufs partition at all)

> **taavikko said:**
> Anybody else having these on "dmesg" after grub-update is been runned?
```
[22769.495849] SGI XFS with ACLs, security attributes, realtime, large block/inode numbers, no debug enabled                                                                                                        
[22769.496896] SGI XFS Quota Management subsystem                                                         
[22769.521918] JFS: nTxBlock = 8192, nTxLock = 65536                                                      
[22769.559584] NTFS driver 2.1.29 [Flags: R/O MODULE].                                                    
[22769.608041] QNX4 filesystem 0.2.3 registered.                                                          
[22769.792180] attempt to access beyond end of device                                                     
[22769.792184] sda3: rw=0, want=4, limit=2                                                                
[22769.792187] EXT3-fs: unable to read superblock                                                         
[22769.813928] attempt to access beyond end of device                                                     
[22769.813932] sda3: rw=0, want=4, limit=2                                                                
[22769.813935] EXT2-fs: unable to read superblock                                                         
[22769.816181] attempt to access beyond end of device                                                     
[22769.816185] sda3: rw=0, want=4, limit=2                                                                
[22769.816188] EXT4-fs: unable to read superblock                                                         
[22769.818445] cramfs: wrong magic                                                                        
[22769.904734] attempt to access beyond end of device                                                     
[22769.904738] sda3: rw=0, want=18, limit=2                                                               
[22769.904743] REISERFS warning (device sda3): sh-2006 read_super_block: bread failed (dev sda3, block 8, size 1024)                                                                                                
[22769.904748] attempt to access beyond end of device                                                     
[22769.904751] sda3: rw=0, want=130, limit=2                                                              
[22769.904755] REISERFS warning (device sda3): sh-2006 read_super_block: bread failed (dev sda3, block 64, size 1024)                                                                                               
[22769.904758] REISERFS warning (device sda3): sh-2021 reiserfs_fill_super: can not find reiserfs on sda3 
[22769.907056] attempt to access beyond end of device                                                     
[22769.907060] sda3: rw=0, want=8, limit=2                                                                
[22769.907065] XFS: SB read failed                                                                        
[22769.911545] attempt to access beyond end of device                                                     
[22769.911549] sda3: rw=0, want=72, limit=2                                                               
[22769.911553] attempt to access beyond end of device                                                     
[22769.911556] sda3: rw=0, want=128, limit=2                                                              
[22769.914049] FAT: bogus number of reserved sectors                                                      
[22769.914053] VFS: Can't find a valid FAT filesystem on dev sda3.                                        
[22769.916559] FAT: bogus number of reserved sectors                                                      
[22769.916562] VFS: Can't find a valid FAT filesystem on dev sda3.                                        
[22769.923577] attempt to access beyond end of device                                                     
[22769.923580] sda3: rw=0, want=4, limit=2                                                                
[22769.923583] MINIX-fs: unable to read superblock                                                        
[22769.947563] attempt to access beyond end of device                                                     
[22769.947567] sda3: rw=0, want=3, limit=2                                                                
[22769.947570] hfs: unable to find HFS+ superblock                                                        
[22769.950095] qnx4: wrong fsid in superblock.                                                            
[22769.952359] You didn't specify the type of your ufs filesystem                                         
[22769.952361]                                                                                            
[22769.952362] mount -t ufs -o ufstype=sun|sunx86|44bsd|ufs2|5xbsd|old|hp|nextstep|nextstep-cd|openstep ...                                                                                                         
[22769.952363]                                                                                            
[22769.952364] >>>WARNING<<< Wrong ufstype may corrupt your filesystem, default is ufstype=old            
[22769.952372] attempt to access beyond end of device                                                     
[22769.952375] sda3: rw=0, want=18, limit=2                                                               
[22769.954606] attempt to access beyond end of device                                                     
[22769.954610] sda3: rw=0, want=3, limit=2                                                                
[22769.954613] hfs: can't find a HFS filesystem on dev sda3.                                              
[176379.695528] attempt to access beyond end of device                                                    
[176379.695532] sda3: rw=0, want=4, limit=2                                                               
[176379.695535] EXT3-fs: unable to read superblock                                                        
[176379.697862] attempt to access beyond end of device                                                    
[176379.697866] sda3: rw=0, want=4, limit=2                                                               
[176379.697868] EXT2-fs: unable to read superblock                                                        
[176379.700158] attempt to access beyond end of device                                                    
[176379.700162] sda3: rw=0, want=4, limit=2                                                               
[176379.700165] EXT4-fs: unable to read superblock                                                        
[176379.702427] cramfs: wrong magic                                                                       
[176379.806786] attempt to access beyond end of device                                                    
[176379.806790] sda3: rw=0, want=18, limit=2                                                              
[176379.806796] REISERFS warning (device sda3): sh-2006 read_super_block: bread failed (dev sda3, block 8, size 1024)                                                                                               
[176379.806801] attempt to access beyond end of device                                                    
[176379.806804] sda3: rw=0, want=130, limit=2                                                             
[176379.806808] REISERFS warning (device sda3): sh-2006 read_super_block: bread failed (dev sda3, block 64, size 1024)                                                                                              
[176379.806811] REISERFS warning (device sda3): sh-2021 reiserfs_fill_super: can not find reiserfs on sda3
[176379.809250] attempt to access beyond end of device                                                    
[176379.809254] sda3: rw=0, want=8, limit=2                                                               
[176379.809259] XFS: SB read failed                                                                       
[176379.814306] attempt to access beyond end of device                                                    
[176379.814310] sda3: rw=0, want=72, limit=2                                                              
[176379.814314] attempt to access beyond end of device                                                    
[176379.814317] sda3: rw=0, want=128, limit=2                                                             
[176379.817353] FAT: bogus number of reserved sectors                                                     
[176379.817357] VFS: Can't find a valid FAT filesystem on dev sda3.                                       
[176379.819882] FAT: bogus number of reserved sectors                                                     
[176379.819887] VFS: Can't find a valid FAT filesystem on dev sda3.                                       
[176379.827284] attempt to access beyond end of device                                                    
[176379.827288] sda3: rw=0, want=4, limit=2                                                               
[176379.827290] MINIX-fs: unable to read superblock                                                       
[176379.829578] attempt to access beyond end of device                                                    
[176379.829582] sda3: rw=0, want=3, limit=2                                                               
[176379.829585] hfs: unable to find HFS+ superblock                                                       
[176379.832754] qnx4: wrong fsid in superblock.                                                           
[176379.835012] You didn't specify the type of your ufs filesystem                                        
[176379.835013]                                                                                           
[176379.835014] mount -t ufs -o ufstype=sun|sunx86|44bsd|ufs2|5xbsd|old|hp|nextstep|nextstep-cd|openstep ...                                                                                                        
[176379.835016]                                                                                           
[176379.835016] >>>WARNING<<< Wrong ufstype may corrupt your filesystem, default is ufstype=old           
[176379.835025] attempt to access beyond end of device                                                    
[176379.835028] sda3: rw=0, want=18, limit=2                                                              
[176379.837297] attempt to access beyond end of device                                                    
[176379.837301] sda3: rw=0, want=3, limit=2                                                               
[176379.837304] hfs: can't find a HFS filesystem on dev sda3.                                             
[199029.673009] attempt to access beyond end of device                                                    
[199029.673014] sda3: rw=0, want=4, limit=2                                                               
[199029.673016] EXT3-fs: unable to read superblock                                                        
[199029.692904] attempt to access beyond end of device                                                    
[199029.692908] sda3: rw=0, want=4, limit=2                                                               
[199029.692911] EXT2-fs: unable to read superblock                                                        
[199029.695202] attempt to access beyond end of device                                                    
[199029.695206] sda3: rw=0, want=4, limit=2                                                               
[199029.695209] EXT4-fs: unable to read superblock                                                        
[199029.697476] cramfs: wrong magic                                                                       
[199029.754347] attempt to access beyond end of device
[199029.754351] sda3: rw=0, want=18, limit=2
[199029.754357] REISERFS warning (device sda3): sh-2006 read_super_block: bread failed (dev sda3, block 8, size 1024)
[199029.754362] attempt to access beyond end of device
[199029.754365] sda3: rw=0, want=130, limit=2
[199029.754369] REISERFS warning (device sda3): sh-2006 read_super_block: bread failed (dev sda3, block 64, size 1024)
[199029.754373] REISERFS warning (device sda3): sh-2021 reiserfs_fill_super: can not find reiserfs on sda3
[199029.756901] attempt to access beyond end of device
[199029.756906] sda3: rw=0, want=8, limit=2
[199029.756910] XFS: SB read failed
[199029.762361] attempt to access beyond end of device
[199029.762365] sda3: rw=0, want=72, limit=2
[199029.762369] attempt to access beyond end of device
[199029.762372] sda3: rw=0, want=128, limit=2
[199029.764914] FAT: bogus number of reserved sectors
[199029.764918] VFS: Can't find a valid FAT filesystem on dev sda3.
[199029.767435] FAT: bogus number of reserved sectors
[199029.767439] VFS: Can't find a valid FAT filesystem on dev sda3.
[199029.774421] attempt to access beyond end of device
[199029.774425] sda3: rw=0, want=4, limit=2
[199029.774428] MINIX-fs: unable to read superblock
[199029.776690] attempt to access beyond end of device
[199029.776694] sda3: rw=0, want=3, limit=2
[199029.776697] hfs: unable to find HFS+ superblock
[199029.779198] qnx4: wrong fsid in superblock.
[199029.781455] You didn't specify the type of your ufs filesystem
[199029.781457]
[199029.781458] mount -t ufs -o ufstype=sun|sunx86|44bsd|ufs2|5xbsd|old|hp|nextstep|nextstep-cd|openstep ...
[199029.781459]
[199029.781460] >>>WARNING<<< Wrong ufstype may corrupt your filesystem, default is ufstype=old
[199029.781468] attempt to access beyond end of device
[199029.781471] sda3: rw=0, want=18, limit=2
[199029.783773] attempt to access beyond end of device
[199029.783777] sda3: rw=0, want=3, limit=2
[199029.783780] hfs: can't find a HFS filesystem on dev sda3.
```

Older kernel removal or something else that requires grub-update...

---

### Post by plun on 2009-08-10
New version

Note "Esc"....:)

> grub2 (1.96+20090725-1ubuntu2) karmic; urgency=low

  * 950_hidden_timeout.diff: New patch. Add GRUB_HIDDEN_TIMEOUT support.
    Move the timeout setting to the end so that the sleep comes after
    terminal setup.
  * debian/default/grub: [B]Default to hiding the menu with a three-second
    timeout. Pressing Escape during this time will show the menu.
    grub-installer will unhide it if other operating systems are installed.[/B]
  * debian/grub.d/05_debian_theme: Set a monochromatic theme for Ubuntu.
  * 951_gfxpayload_keep.diff: New patch. If gfxpayload starts with "keep" or
    if GRUB_ASSUME_LINUX_HAS_FB_SUPPORT is defined, then tell Linux to use
    the current video mode.

[https://lists.ubuntu.com/archives/karmic-changes/2009-August/005911.html](https://lists.ubuntu.com/archives/karmic-changes/2009-August/005911.html)



---

### Post by phenest on 2009-08-10
Woah! The hidden menu works, and my background appears, but for like, 1 second!

---

### Post by fjosh on 2009-08-10
Karmic Alpha 3
Grub2 works for me with a little fiddling.

Initially it didn't display XP SP3 as an option until I ran osprober and updated Grub2

---

### Post by wayne_cat on 2009-08-10
Is there a command that I can use after booting to list the VBE modes of my system?

something like this (painful slow) grub2 command:

[http://www.gnu.org/software/grub/manual/html_node/vbeprobe.html](http://www.gnu.org/software/grub/manual/html_node/vbeprobe.html)

---

### Post by phenest on 2009-08-10
> **wayne_cat said:**
> Is there a command that I can use after booting to list the VBE modes of my system?

something like this (painful slow) grub2 command:

[http://www.gnu.org/software/grub/manual/html_node/vbeprobe.html](http://www.gnu.org/software/grub/manual/html_node/vbeprobe.html)

vbeinfo but only at a grub prompt

---

### Post by biasquez on 2009-08-11
hi, i'm testing grub2.into my old grub, i have 2 kernel linux + entry for windows vista.installing grub2,  when i choose "chainload into grub 2", i can't choose kernel/vista entry from menu but pc starts fine with first kernel in old menu entries...so i want to know this it's normal and if grub2 works fine o not...

---

### Post by phenest on 2009-08-11
> **biasquez said:**
> hi, i'm testing grub2.into my old grub, i have 2 kernel linux + entry for windows vista.installing grub2,  when i choose "chainload into grub 2", i can't choose kernel/vista entry from menu but pc starts fine with first kernel in old menu entries...so i want to know this it's normal and if grub2 works fine o not...

Have you run the command:
```
sudo upgrade-from-grub-legacy
```

---

### Post by biasquez on 2009-08-11
> **phenest said:**
> Have you run the command:
```
sudo upgrade-from-grub-legacy
```

Thanks! works fine!

---

### Post by vs8 on 2009-09-20
Acer Aspire 5050-5410 passed!

When I boot Alpha 6 it boots slower than Jaunty and Xplash doesn't start at the beginning. Is this normal?

This is not a fresh installation I came from Alpha 5. When I boot it gives me this strange error:

Sep 20 15:55:38 melvin-laptop kernel: [   23.014044] acerhdf: unknown (unsupported) BIOS version Acer, inc./Aspire 5050     /v1.3103, please report, aborting!

Where can I report this?

---

### Post by durand on 2009-09-20
> **vs8 said:**
> Acer Aspire 5050-5410 passed!

When I boot Alpha 6 it boots slower than Jaunty and Xplash doesn't start at the beginning. Is this normal?

This is not a fresh installation I came from Alpha 5. When I boot it gives me this strange error:

Sep 20 15:55:38 melvin-laptop kernel: [   23.014044] acerhdf: unknown (unsupported) BIOS version Acer, inc./Aspire 5050     /v1.3103, please report, aborting!

Where can I report this?

Same thing happens for me. With the latest updates, I've stopped getting a usplash as well..

---

### Post by zeimusu on 2009-09-20
I find that grub2, installed with Karmic, Takes a long time on the "GRUB Loading" screen, before the menu appears. By "a long time" I mean about 30 seconds from when the bios screen is replaced by a blank screen with "GRUB loading" to the menu appearing. 

I have WinXP on one disk, and Jaunty and Karmic on the second and third partition of the second. Legacy grub was much faster. Any thoughts on what it is doing for those 30 seconds?

---

### Post by autocrosser on 2009-09-20
> **zeimusu said:**
> I find that grub2, installed with Karmic, Takes a long time on the "GRUB Loading" screen, before the menu appears. By "a long time" I mean about 30 seconds from when the bios screen is replaced by a blank screen with "GRUB loading" to the menu appearing. 

I have WinXP on one disk, and Jaunty and Karmic on the second and third partition of the second. Legacy grub was much faster. Any thoughts on what it is doing for those 30 seconds?

Please report in my bug report--Current grub-pc takes several minutes to show menu: 
[https://bugs.launchpad.net/bugs/420933](https://bugs.launchpad.net/bugs/420933)

The problem is that Grub2 is installed on the MBR & /boot is on another drive. The "work-around" is to switch drives & have the MBR & /boot on the same drive--I can't do that due to several drives & OS installs.

---

### Post by autocrosser on 2009-09-20
> **durand said:**
> Same thing happens for me. With the latest updates, I've stopped getting a usplash as well..

Usplash is a "work in progress"--it is being "replaced"--the developers are trying to boot fast enough that it is not required, so all you see right now is a couple of lines of text before xsplash starts.

---

### Post by Slug71 on 2009-09-23
Hmm.. just installed Ubuntu on my spare box which already has ReactOS and PC-BSD on and Grub2 didnt detect them.

Ran 'sudo os-prober' in Terminal and nada. :confused:

---

### Post by VMC on 2009-09-23
> **Slug71 said:**
> Hmm.. just installed Ubuntu on my spare box which already has ReactOS and PC-BSD on and Grub2 didnt detect them.

Ran 'sudo os-prober' in Terminal and nada. :confused:

BSD is a different animal. It uses something in this order:
kernel /boot/loader
 Grub2 doesn't know how to handle it. Maybe edit 10_linux file. Same with ReactOS. It's a hack of XP, right?

---

### Post by Slug71 on 2009-09-24
> **VMC said:**
> BSD is a different animal. It uses something in this order:
kernel /boot/loader
 Grub2 doesn't know how to handle it. Maybe edit 10_linux file. Same with ReactOS. It's a hack of XP, right?

Yeh i think it is.

Will have a play with it later.

---

### Post by Kazade on 2009-09-24
> **VMC said:**
> Same with ReactOS. It's a hack of XP, right?

Er.. not really. It's a ground-up GPL Windows NT clone.

---

### Post by Slug71 on 2009-09-24
> **Slug71 said:**
> Hmm.. just installed Ubuntu on my spare box which already has ReactOS and PC-BSD on and Grub2 didnt detect them.

Ran 'sudo os-prober' in Terminal and nada. :confused:


Just filed a bug on os-prober for this, #436298.

---

### Post by ranch hand on 2009-09-24
Os-prober is not what you want to run.  Just try "sudo update-grub".  Yes I know, it ran when you installed.  Try it again, it may not work but if you are going to get anywhere that is what you need to do.

I have only had that problem (not picking up other installs) once and update-grub fixed it.  A number of others have too.

If it picks the buggers up, I would not expect what it generates to work though, at least on the BSD.

You will need to create an file (06_custom) modeled on the 40_custom file to put in menu entries that will work.  By making you own file with a low number name, those entries will be on the top of the menu you see on screen.  You will have to run update-grub to get that on your menu.  that is how the grub.cfg file is generated.

---

### Post by Slug71 on 2009-09-24
> **ranch hand said:**
> Os-prober is not what you want to run.  Just try "sudo update-grub".  Yes I know, it ran when you installed.  Try it again, it may not work but if you are going to get anywhere that is what you need to do.

I have only had that problem (not picking up other installs) once and update-grub fixed it.  A number of others have too.

If it picks the buggers up, I would not expect what it generates to work though, at least on the BSD.

You will need to create an file (06_custom) modeled on the 40_custom file to put in menu entries that will work.  By making you own file with a low number name, those entries will be on the top of the menu you see on screen.  You will have to run update-grub to get that on your menu.  that is how the grub.cfg file is generated.

Tried 'sudo update-grub' and still doesnt work. Gets Kubuntu and Ubuntu.

This wiki says how to add ReactOS to grub2 or at least what the entry should look like but im not sure exactly where to add it in grub.cfg.

[http://www.reactos.org/wiki/HOWTO/boot_FreeLoader_from_GRUB](http://www.reactos.org/wiki/HOWTO/boot_FreeLoader_from_GRUB)

---

### Post by Slug71 on 2009-09-25
Used that wiki and made it my first entry in grub.cfg and it works! :) :guitar:

Thats ReactOS out the way.

---

### Post by ranch hand on 2009-09-25
If you put that same entry in a custom file in grub.d it will not be over written the next time you run, or the installer runs, update grub.

For instance, my Mandriva installs are picked up but the generated menu entry does not do the job at all.  So I have this entry in /etc/grub.d/01_custom;
```

echo "Adding Mandriva2009-1-Gnome on sda12" >&2
cat << EOF
menuentry "Mandriva 2009 Gnome sda12" {
linux (hd0,12)/boot/vmlinuz
initrd (hd0,12)/boot/initrd.img
}
EOF

```
This OS was on this drive before any 9.10 installs were.  Since A2, when grub2 was introduced, update-grub has been run 100s of times.  It runs at least twice everytime you get a kernal update.  Anything that you put in grub.cfg is over written by the scripts in grub.d.

When you have the custom entries they are written in at the same time and then my grub.cfg looks like this;
```

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
load_env
set default="0"
if [ ${prev_saved_entry} ]; then
  saved_entry=${prev_saved_entry}
  save_env saved_entry
  prev_saved_entry=
  save_env prev_saved_entry
fi
insmod ext2
set root=(hd0,10)
search --no-floppy --fs-uuid --set 2a9c6ddd-4422-4fc5-a7ed-613cf3430b8c
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
set timeout=100
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/01_Custom ###
menuentry " Adding Kinky Stoner1.0 on sda102.6.31-9-generic" {
    set root=(hd0,10)
    search --no-floppy --fs-uuid --set 2a9c6ddd-4422-4fc5-a7ed-613cf3430b8c
    linux    /boot/vmlinuz-2.6.31-9-generic root=UUID=2a9c6ddd-4422-4fc5-a7ed-613cf3430b8c ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-9-generic
}
menuentry "Kinky Stoner1.0 on sda10 2.6.31-10-generic" {
    set quiet=1
    insmod ext2
    set root=(hd0,10)
    search --no-floppy --fs-uuid --set 2a9c6ddd-4422-4fc5-a7ed-613cf3430b8c
    linux    /boot/vmlinuz-2.6.31-10-generic root=UUID=2a9c6ddd-4422-4fc5-a7ed-613cf3430b8c ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-10-generic
}
menuentry "Kinky Stoner1.0 on sda10 2.6.31-10-generic (recovery mode)" {
    insmod ext2
    set root=(hd0,10)
    search --no-floppy --fs-uuid --set 2a9c6ddd-4422-4fc5-a7ed-613cf3430b8c
    linux    /boot/vmlinuz-2.6.31-10-generic root=UUID=2a9c6ddd-4422-4fc5-a7ed-613cf3430b8c ro single 
    initrd    /boot/initrd.img-2.6.31-10-generic
}
menuentry "KinkyA1, kernel 2.6.31-9-generic (on /dev/sda16)" {
    set root=(hd0,16)
    search --no-floppy --fs-uuid --set 037e8099-d605-4315-b637-f60c6ff692ed
    linux /boot/vmlinuz-2.6.31-9-generic root=UUID=037e8099-d605-4315-b637-f60c6ff692ed ro quiet splash
    initrd /boot/initrd.img-2.6.31-9-generic
}
menuentry " KinkyA4 2.6.31-9-generic(sda20)" {
    set root=(hd0,20)
    search --no-floppy --fs-uuid --set ec4ef79d-36b7-4821-b358-188953ec8d7a
    linux    /boot/vmlinuz-2.6.31-9-generic root=UUID=ec4ef79d-36b7-4821-b358-188953ec8d7a ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-9-generic
}
menuentry "KinkyStoner1.0 (on /dev/sda6)" {
    set root=(hd0,6)
    search --no-floppy --fs-uuid --set 8eee83de-573f-48dd-b8e9-80aa29887979
    linux /boot/vmlinuz-2.6.31-9-generic root=/dev/sda6
    initrd /boot/initrd.img-2.6.31-9-generic
}
menuentry "Jaunty 9.04, kernel 2.6.28-14-generic (on /dev/sda8)" {
        set root=(hd0,8)
        search --no-floppy --fs-uuid --set 79e9dc92-8346-44a9-b74a-97b4a76c560e
        linux /boot/vmlinuz-2.6.28-14-generic root=UUID=79e9dc92-8346-44a9-b74a-97b4a76c560e ro quiet splash
        initrd /boot/initrd.img-2.6.28-14-generic
}
menuentry "Stoner1.1, kernel 2.6.28-14-generic (on /dev/sda18)" {
    set root=(hd0,18)
    search --no-floppy --fs-uuid --set 0810f840-b2dc-4223-9132-d6d30103787e
    linux /boot/vmlinuz-2.6.28-14-generic root=UUID=0810f840-b2dc-4223-9132-d6d30103787e ro quiet splash
    initrd /boot/initrd.img-2.6.28-14-generic
}
menuentry "Mandriva 2009 Gnome sda12" {
linux (hd0,12)/boot/vmlinuz
initrd (hd0,12)/boot/initrd.img
}
menuentry "Mandriva 2009 KDE sda14" {
linux (hd0,14)/boot/vmlinuz
initrd (hd0,14)/boot/initrd.img
}
### END /etc/grub.d/01_Custom ###

### BEGIN /etc/grub.d/05_debian_theme ###
insmod ext2
set root=(hd0,10)
search --no-floppy --fs-uuid --set 2a9c6ddd-4422-4fc5-a7ed-613cf3430b8c
insmod png
if background_image /usr/share/images/desktop-base/bad-fruit.png ; then
  set color_normal=white/black
  set color_highlight=green/black
else
  set menu_color_normal=white/black
  set menu_color_highlight=black/white
fi
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry "Ubuntu, Linux 2.6.31-10-generic" {
    set quiet=1
    insmod ext2
    set root=(hd0,10)
    search --no-floppy --fs-uuid --set 2a9c6ddd-4422-4fc5-a7ed-613cf3430b8c
    linux    /boot/vmlinuz-2.6.31-10-generic root=UUID=2a9c6ddd-4422-4fc5-a7ed-613cf3430b8c ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-10-generic
}
menuentry "Ubuntu, Linux 2.6.31-10-generic (recovery mode)" {
    insmod ext2
    set root=(hd0,10)
    search --no-floppy --fs-uuid --set 2a9c6ddd-4422-4fc5-a7ed-613cf3430b8c
    linux    /boot/vmlinuz-2.6.31-10-generic root=UUID=2a9c6ddd-4422-4fc5-a7ed-613cf3430b8c ro single 
    initrd    /boot/initrd.img-2.6.31-10-generic
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
menuentry "linux (on /dev/sda12)" {
    insmod ext2
    set root=(hd0,12)
    search --no-floppy --fs-uuid --set c23ad2ca-67a5-4a42-8fcc-3baa6d8e454e
    linux /boot/vmlinuz BOOT_IMAGE=linux root=UUID=c23ad2ca-67a5-4a42-8fcc-3baa6d8e454e resume=UUID=59fe476e-6d4f-e390-ced9-f29328538dfc splash=silent vga=788
    initrd (hd0,11)/boot/initrd.img
}
menuentry "linux-nonfb (on /dev/sda12)" {
    insmod ext2
    set root=(hd0,12)
    search --no-floppy --fs-uuid --set c23ad2ca-67a5-4a42-8fcc-3baa6d8e454e
    linux /boot/vmlinuz BOOT_IMAGE=linux-nonfb root=UUID=c23ad2ca-67a5-4a42-8fcc-3baa6d8e454e resume=UUID=59fe476e-6d4f-e390-ced9-f29328538dfc
    initrd (hd0,11)/boot/initrd.img
}
menuentry "failsafe (on /dev/sda12)" {
    insmod ext2
    set root=(hd0,12)
    search --no-floppy --fs-uuid --set c23ad2ca-67a5-4a42-8fcc-3baa6d8e454e
    linux /boot/vmlinuz BOOT_IMAGE=failsafe root=UUID=c23ad2ca-67a5-4a42-8fcc-3baa6d8e454e failsafe
    initrd (hd0,11)/boot/initrd.img
}
menuentry "2.6.27-desktop586rc8-2mnb (on /dev/sda12)" {
    insmod ext2
    set root=(hd0,12)
    search --no-floppy --fs-uuid --set c23ad2ca-67a5-4a42-8fcc-3baa6d8e454e
    linux /boot/vmlinuz-2.6.27-desktop586-0.rc8.2mnb BOOT_IMAGE=2.6.27-desktop586rc8-2mnb root=UUID=c23ad2ca-67a5-4a42-8fcc-3baa6d8e454e resume=UUID=59fe476e-6d4f-e390-ced9-f29328538dfc splash=silent vga=788
    initrd (hd0,11)/boot/initrd-2.6.27-desktop586-0.rc8.2mnb.img
}
menuentry "desktop586 2.6.27.19-1mnb (on /dev/sda12)" {
    insmod ext2
    set root=(hd0,12)
    search --no-floppy --fs-uuid --set c23ad2ca-67a5-4a42-8fcc-3baa6d8e454e
    linux /boot/vmlinuz-2.6.27.19-desktop586-1mnb BOOT_IMAGE=desktop586_2.6.27.19-1mnb root=UUID=c23ad2ca-67a5-4a42-8fcc-3baa6d8e454e resume=UUID=59fe476e-6d4f-e390-ced9-f29328538dfc splash=silent vga=788
    initrd (hd0,11)/boot/initrd-2.6.27.19-desktop586-1mnb.img
}
menuentry "desktop586 2.6.27.14-1mnb (on /dev/sda12)" {
    insmod ext2
    set root=(hd0,12)
    search --no-floppy --fs-uuid --set c23ad2ca-67a5-4a42-8fcc-3baa6d8e454e
    linux /boot/vmlinuz-2.6.27.14-desktop586-1mnb BOOT_IMAGE=desktop586_2.6.27.14-1mnb root=UUID=c23ad2ca-67a5-4a42-8fcc-3baa6d8e454e resume=UUID=59fe476e-6d4f-e390-ced9-f29328538dfc splash=silent vga=788
    initrd (hd0,11)/boot/initrd-2.6.27.14-desktop586-1mnb.img
}
menuentry "desktop586 2.6.27.21-1mnb (on /dev/sda12)" {
    insmod ext2
    set root=(hd0,12)
    search --no-floppy --fs-uuid --set c23ad2ca-67a5-4a42-8fcc-3baa6d8e454e
    linux /boot/vmlinuz-2.6.27.21-desktop586-1mnb BOOT_IMAGE=desktop586_2.6.27.21-1mnb root=UUID=c23ad2ca-67a5-4a42-8fcc-3baa6d8e454e resume=UUID=59fe476e-6d4f-e390-ced9-f29328538dfc splash=silent vga=788
    initrd (hd0,11)/boot/initrd-2.6.27.21-desktop586-1mnb.img
}
menuentry "desktop586 2.6.27.24-1mnb (on /dev/sda12)" {
    insmod ext2
    set root=(hd0,12)
    search --no-floppy --fs-uuid --set c23ad2ca-67a5-4a42-8fcc-3baa6d8e454e
    linux /boot/vmlinuz-2.6.27.24-desktop586-1mnb BOOT_IMAGE=desktop586_2.6.27.24-1mnb root=UUID=c23ad2ca-67a5-4a42-8fcc-3baa6d8e454e resume=UUID=59fe476e-6d4f-e390-ced9-f29328538dfc splash=silent vga=788
    initrd (hd0,11)/boot/initrd-2.6.27.24-desktop586-1mnb.img
}
menuentry "desktop586 2.6.27.24-2mnb (on /dev/sda12)" {
    insmod ext2
    set root=(hd0,12)
    search --no-floppy --fs-uuid --set c23ad2ca-67a5-4a42-8fcc-3baa6d8e454e
    linux /boot/vmlinuz-2.6.27.24-desktop586-2mnb BOOT_IMAGE=desktop586_2.6.27.24-2mnb root=UUID=c23ad2ca-67a5-4a42-8fcc-3baa6d8e454e resume=UUID=59fe476e-6d4f-e390-ced9-f29328538dfc splash=silent vga=788
    initrd (hd0,11)/boot/initrd-2.6.27.24-desktop586-2mnb.img
}
menuentry "linux (on /dev/sda14)" {
    insmod ext2
    set root=(hd0,14)
    search --no-floppy --fs-uuid --set 7be62a2a-eb6e-43f3-8712-87abbf7182a9
    linux /boot/vmlinuz BOOT_IMAGE=linux root=UUID=7be62a2a-eb6e-43f3-8712-87abbf7182a9 resume=UUID=59fe476e-6d4f-e390-ced9-f29328538dfc splash=silent vga=788
    initrd (hd0,13)/boot/initrd.img
}
menuentry "linux-nonfb (on /dev/sda14)" {
    insmod ext2
    set root=(hd0,14)
    search --no-floppy --fs-uuid --set 7be62a2a-eb6e-43f3-8712-87abbf7182a9
    linux /boot/vmlinuz BOOT_IMAGE=linux-nonfb root=UUID=7be62a2a-eb6e-43f3-8712-87abbf7182a9 resume=UUID=59fe476e-6d4f-e390-ced9-f29328538dfc
    initrd (hd0,13)/boot/initrd.img
}
menuentry "failsafe (on /dev/sda14)" {
    insmod ext2
    set root=(hd0,14)
    search --no-floppy --fs-uuid --set 7be62a2a-eb6e-43f3-8712-87abbf7182a9
    linux /boot/vmlinuz BOOT_IMAGE=failsafe root=UUID=7be62a2a-eb6e-43f3-8712-87abbf7182a9 failsafe
    initrd (hd0,13)/boot/initrd.img
}
menuentry "2.6.27-desktop586rc8-2mnb (on /dev/sda14)" {
    insmod ext2
    set root=(hd0,14)
    search --no-floppy --fs-uuid --set 7be62a2a-eb6e-43f3-8712-87abbf7182a9
    linux /boot/vmlinuz-2.6.27-desktop586-0.rc8.2mnb BOOT_IMAGE=2.6.27-desktop586rc8-2mnb root=UUID=7be62a2a-eb6e-43f3-8712-87abbf7182a9 resume=UUID=59fe476e-6d4f-e390-ced9-f29328538dfc splash=silent vga=788
    initrd (hd0,13)/boot/initrd-2.6.27-desktop586-0.rc8.2mnb.img
}
menuentry "desktop586 2.6.27.19-1mnb (on /dev/sda14)" {
    insmod ext2
    set root=(hd0,14)
    search --no-floppy --fs-uuid --set 7be62a2a-eb6e-43f3-8712-87abbf7182a9
    linux /boot/vmlinuz-2.6.27.19-desktop586-1mnb BOOT_IMAGE=desktop586_2.6.27.19-1mnb root=UUID=7be62a2a-eb6e-43f3-8712-87abbf7182a9 resume=UUID=59fe476e-6d4f-e390-ced9-f29328538dfc splash=silent vga=788
    initrd (hd0,13)/boot/initrd-2.6.27.19-desktop586-1mnb.img
}
menuentry "desktop586 2.6.27.21-1mnb (on /dev/sda14)" {
    insmod ext2
    set root=(hd0,14)
    search --no-floppy --fs-uuid --set 7be62a2a-eb6e-43f3-8712-87abbf7182a9
    linux /boot/vmlinuz-2.6.27.21-desktop586-1mnb BOOT_IMAGE=desktop586_2.6.27.21-1mnb root=UUID=7be62a2a-eb6e-43f3-8712-87abbf7182a9 resume=UUID=59fe476e-6d4f-e390-ced9-f29328538dfc splash=silent vga=788
    initrd (hd0,13)/boot/initrd-2.6.27.21-desktop586-1mnb.img
}
menuentry "desktop586 2.6.27.24-1mnb (on /dev/sda14)" {
    insmod ext2
    set root=(hd0,14)
    search --no-floppy --fs-uuid --set 7be62a2a-eb6e-43f3-8712-87abbf7182a9
    linux /boot/vmlinuz-2.6.27.24-desktop586-1mnb BOOT_IMAGE=desktop586_2.6.27.24-1mnb root=UUID=7be62a2a-eb6e-43f3-8712-87abbf7182a9 resume=UUID=59fe476e-6d4f-e390-ced9-f29328538dfc splash=silent vga=788
    initrd (hd0,13)/boot/initrd-2.6.27.24-desktop586-1mnb.img
}
menuentry "desktop586 2.6.27.24-2mnb (on /dev/sda14)" {
    insmod ext2
    set root=(hd0,14)
    search --no-floppy --fs-uuid --set 7be62a2a-eb6e-43f3-8712-87abbf7182a9
    linux /boot/vmlinuz-2.6.27.24-desktop586-2mnb BOOT_IMAGE=desktop586_2.6.27.24-2mnb root=UUID=7be62a2a-eb6e-43f3-8712-87abbf7182a9 resume=UUID=59fe476e-6d4f-e390-ced9-f29328538dfc splash=silent vga=788
    initrd (hd0,13)/boot/initrd-2.6.27.24-desktop586-2mnb.img
}
menuentry "KinkyA1 on sda16 2.6.31-10-generic (on /dev/sda16)" {
    insmod ext2
    set root=(hd0,16)
    search --no-floppy --fs-uuid --set 593f6939-f51c-496d-a90a-c7cb942a22af
    linux /boot/vmlinuz-2.6.31-10-generic root=UUID=593f6939-f51c-496d-a90a-c7cb942a22af ro quiet splash
    initrd /boot/initrd.img-2.6.31-10-generic
}
menuentry "KinkyA4 on sda20 2.6.31-10-generic (on /dev/sda16)" {
    insmod ext2
    set root=(hd0,16)
    search --no-floppy --fs-uuid --set 593f6939-f51c-496d-a90a-c7cb942a22af
    linux /boot/vmlinuz-2.6.31-10-generic root=UUID=ec4ef79d-36b7-4821-b358-188953ec8d7a ro quiet splash
    initrd /boot/initrd.img-2.6.31-10-generic
}
menuentry "Kinky Stoner1.0 on sda10 2.6.31-10-generic (on /dev/sda16)" {
    insmod ext2
    set root=(hd0,16)
    search --no-floppy --fs-uuid --set 593f6939-f51c-496d-a90a-c7cb942a22af
    linux /boot/vmlinuz-2.6.31-10-generic root=UUID=2a9c6ddd-4422-4fc5-a7ed-613cf3430b8c ro quiet splash
    initrd /boot/initrd.img-2.6.31-10-generic
}
menuentry "KinkyStoner1.0 on sda6 2.6.31-10-generic (on /dev/sda16)" {
    insmod ext2
    set root=(hd0,16)
    search --no-floppy --fs-uuid --set 593f6939-f51c-496d-a90a-c7cb942a22af
    linux /boot/vmlinuz-2.6.31-10-generic root=UUID=8eee83de-573f-48dd-b8e9-80aa29887979 ro y y
    initrd /boot/initrd.img-2.6.31-10-generic
}
menuentry "Ubuntu, Linux 2.6.31-10-generic (on /dev/sda16)" {
    insmod ext2
    set root=(hd0,16)
    search --no-floppy --fs-uuid --set 593f6939-f51c-496d-a90a-c7cb942a22af
    linux /boot/vmlinuz-2.6.31-10-generic root=UUID=593f6939-f51c-496d-a90a-c7cb942a22af ro quiet splash
    initrd /boot/initrd.img-2.6.31-10-generic
}
menuentry "Ubuntu, Linux 2.6.31-10-generic (recovery mode) (on /dev/sda16)" {
    insmod ext2
    set root=(hd0,16)
    search --no-floppy --fs-uuid --set 593f6939-f51c-496d-a90a-c7cb942a22af
    linux /boot/vmlinuz-2.6.31-10-generic root=UUID=593f6939-f51c-496d-a90a-c7cb942a22af ro single
    initrd /boot/initrd.img-2.6.31-10-generic
}
menuentry "Ubuntu 9.04, kernel 2.6.28-15-generic (on /dev/sda18)" {
    insmod ext2
    set root=(hd0,18)
    search --no-floppy --fs-uuid --set 0810f840-b2dc-4223-9132-d6d30103787e
    linux /boot/vmlinuz-2.6.28-15-generic root=UUID=0810f840-b2dc-4223-9132-d6d30103787e ro quiet splash
    initrd /boot/initrd.img-2.6.28-15-generic
}
menuentry "Ubuntu 9.04, kernel 2.6.28-15-generic (recovery mode) (on /dev/sda18)" {
    insmod ext2
    set root=(hd0,18)
    search --no-floppy --fs-uuid --set 0810f840-b2dc-4223-9132-d6d30103787e
    linux /boot/vmlinuz-2.6.28-15-generic root=UUID=0810f840-b2dc-4223-9132-d6d30103787e ro single
    initrd /boot/initrd.img-2.6.28-15-generic
}
menuentry "Ubuntu 9.04, kernel 2.6.28-14-generic (on /dev/sda18)" {
    insmod ext2
    set root=(hd0,18)
    search --no-floppy --fs-uuid --set 0810f840-b2dc-4223-9132-d6d30103787e
    linux /boot/vmlinuz-2.6.28-14-generic root=UUID=0810f840-b2dc-4223-9132-d6d30103787e ro quiet splash
    initrd /boot/initrd.img-2.6.28-14-generic
}
menuentry "Ubuntu 9.04, kernel 2.6.28-14-generic (recovery mode) (on /dev/sda18)" {
    insmod ext2
    set root=(hd0,18)
    search --no-floppy --fs-uuid --set 0810f840-b2dc-4223-9132-d6d30103787e
    linux /boot/vmlinuz-2.6.28-14-generic root=UUID=0810f840-b2dc-4223-9132-d6d30103787e ro single
    initrd /boot/initrd.img-2.6.28-14-generic
}
menuentry "Ubuntu 9.04, kernel 2.6.28-13-generic (on /dev/sda18)" {
    insmod ext2
    set root=(hd0,18)
    search --no-floppy --fs-uuid --set 0810f840-b2dc-4223-9132-d6d30103787e
    linux /boot/vmlinuz-2.6.28-13-generic root=UUID=0810f840-b2dc-4223-9132-d6d30103787e ro quiet splash
    initrd /boot/initrd.img-2.6.28-13-generic
}
menuentry "Ubuntu 9.04, kernel 2.6.28-13-generic (recovery mode) (on /dev/sda18)" {
    insmod ext2
    set root=(hd0,18)
    search --no-floppy --fs-uuid --set 0810f840-b2dc-4223-9132-d6d30103787e
    linux /boot/vmlinuz-2.6.28-13-generic root=UUID=0810f840-b2dc-4223-9132-d6d30103787e ro single
    initrd /boot/initrd.img-2.6.28-13-generic
}
menuentry "Ubuntu 9.04, memtest86+ (on /dev/sda18)" {
    insmod ext2
    set root=(hd0,18)
    search --no-floppy --fs-uuid --set 0810f840-b2dc-4223-9132-d6d30103787e
    linux /boot/memtest86+.bin 
}
menuentry "Ubuntu 9.04, kernel 2.6.28-13-generic (on /dev/sda10) (Stoner1.0-32) (on /dev/sda18)" {
    insmod ext2
    set root=(hd0,18)
    search --no-floppy --fs-uuid --set 0810f840-b2dc-4223-9132-d6d30103787e
    linux /boot/vmlinuz-2.6.28-13-generic root=UUID=2a9c6ddd-4422-4fc5-a7ed-613cf3430b8c ro quiet splash
    initrd /boot/initrd.img-2.6.28-13-generic
}
menuentry "Ubuntu 9.04, kernel 2.6.28-13-generic (on /dev/sda8) (Jaunty-32) (on /dev/sda18)" {
    insmod ext2
    set root=(hd0,18)
    search --no-floppy --fs-uuid --set 0810f840-b2dc-4223-9132-d6d30103787e
    linux /boot/vmlinuz-2.6.28-13-generic root=UUID=79e9dc92-8346-44a9-b74a-97b4a76c560e ro quiet splash
    initrd /boot/initrd.img-2.6.28-13-generic
}
menuentry "KinkyA4 on sda20 2.6.31-10-generic (on /dev/sda20)" {
    insmod ext2
    set root=(hd0,20)
    search --no-floppy --fs-uuid --set ec4ef79d-36b7-4821-b358-188953ec8d7a
    linux /boot/vmlinuz-2.6.31-10-generic root=UUID=ec4ef79d-36b7-4821-b358-188953ec8d7a ro quiet splash
    initrd /boot/initrd.img-2.6.31-10-generic
}
menuentry "KinkyA4 on sda20 2.6.31-10-generic (recovery mode) (on /dev/sda20)" {
    insmod ext2
    set root=(hd0,20)
    search --no-floppy --fs-uuid --set ec4ef79d-36b7-4821-b358-188953ec8d7a
    linux /boot/vmlinuz-2.6.31-10-generic root=UUID=ec4ef79d-36b7-4821-b358-188953ec8d7a ro single
    initrd /boot/initrd.img-2.6.31-10-generic
}
menuentry "Kinky Stoner1.0 on sda10 2.6.31-10-generic (on /dev/sda20)" {
    insmod ext2
    set root=(hd0,20)
    search --no-floppy --fs-uuid --set ec4ef79d-36b7-4821-b358-188953ec8d7a
    linux /boot/vmlinuz-2.6.31-10-generic root=UUID=2a9c6ddd-4422-4fc5-a7ed-613cf3430b8c ro quiet splash
    initrd /boot/initrd.img-2.6.31-10-generic
}
menuentry "KinkyStoner1.0 on sda6 2.6.31-10-generic (on /dev/sda20)" {
    insmod ext2
    set root=(hd0,20)
    search --no-floppy --fs-uuid --set ec4ef79d-36b7-4821-b358-188953ec8d7a
    linux /boot/vmlinuz-2.6.31-10-generic root=UUID=8eee83de-573f-48dd-b8e9-80aa29887979 ro y y
    initrd /boot/initrd.img-2.6.31-10-generic
}
menuentry "Ubuntu, Linux 2.6.31-10-generic (on /dev/sda20)" {
    insmod ext2
    set root=(hd0,20)
    search --no-floppy --fs-uuid --set ec4ef79d-36b7-4821-b358-188953ec8d7a
    linux /boot/vmlinuz-2.6.31-10-generic root=UUID=ec4ef79d-36b7-4821-b358-188953ec8d7a ro quiet splash
    initrd /boot/initrd.img-2.6.31-10-generic
}
menuentry "Ubuntu, Linux 2.6.31-10-generic (recovery mode) (on /dev/sda20)" {
    insmod ext2
    set root=(hd0,20)
    search --no-floppy --fs-uuid --set ec4ef79d-36b7-4821-b358-188953ec8d7a
    linux /boot/vmlinuz-2.6.31-10-generic root=UUID=ec4ef79d-36b7-4821-b358-188953ec8d7a ro single
    initrd /boot/initrd.img-2.6.31-10-generic
}
menuentry "KinkyStoner1.0 on sda6 (2.6.31-10-generic) (on /dev/sda6)" {
    insmod ext2
    set root=(hd0,6)
    search --no-floppy --fs-uuid --set 8eee83de-573f-48dd-b8e9-80aa29887979
    linux /boot/vmlinuz-2.6.31-10-generic root=UUID=8eee83de-573f-48dd-b8e9-80aa29887979 ro y y
    initrd /boot/initrd.img-2.6.31-10-generic
}
menuentry "KinkyStoner1.0 on sda6 2.6.31-10-generic (recovery mode) (on /dev/sda6)" {
    insmod ext2
    set root=(hd0,6)
    search --no-floppy --fs-uuid --set 8eee83de-573f-48dd-b8e9-80aa29887979
    linux /boot/vmlinuz-2.6.31-10-generic root=UUID=8eee83de-573f-48dd-b8e9-80aa29887979 ro single y
    initrd /boot/initrd.img-2.6.31-10-generic
}
menuentry "Kinky Stoner1.0 on sda10 (2.6.31-10-generic) (on /dev/sda6)" {
    insmod ext2
    set root=(hd0,6)
    search --no-floppy --fs-uuid --set 8eee83de-573f-48dd-b8e9-80aa29887979
    linux /boot/vmlinuz-2.6.31-10-generic root=UUID=2a9c6ddd-4422-4fc5-a7ed-613cf3430b8c ro quiet splash
    initrd /boot/initrd.img-2.6.31-10-generic
}
menuentry "KinkyA1 on sda16 (2.6.31-10-generic) (on /dev/sda6)" {
    insmod ext2
    set root=(hd0,6)
    search --no-floppy --fs-uuid --set 8eee83de-573f-48dd-b8e9-80aa29887979
    linux /boot/vmlinuz-2.6.31-10-generic root=UUID=593f6939-f51c-496d-a90a-c7cb942a22af ro quiet splash
    initrd /boot/initrd.img-2.6.31-10-generic
}
menuentry "KinkyA4 on sda20 2.6.31-10-generic (on /dev/sda6)" {
    insmod ext2
    set root=(hd0,6)
    search --no-floppy --fs-uuid --set 8eee83de-573f-48dd-b8e9-80aa29887979
    linux /boot/vmlinuz-2.6.31-10-generic root=UUID=ec4ef79d-36b7-4821-b358-188953ec8d7a ro quiet splash
    initrd /boot/initrd.img-2.6.31-10-generic
}
menuentry "Ubuntu, Linux 2.6.31-10-generic (on /dev/sda6)" {
    insmod ext2
    set root=(hd0,6)
    search --no-floppy --fs-uuid --set 8eee83de-573f-48dd-b8e9-80aa29887979
    linux /boot/vmlinuz-2.6.31-10-generic root=UUID=8eee83de-573f-48dd-b8e9-80aa29887979 ro y y
    initrd /boot/initrd.img-2.6.31-10-generic
}
menuentry "Ubuntu, Linux 2.6.31-10-generic (recovery mode) (on /dev/sda6)" {
    insmod ext2
    set root=(hd0,6)
    search --no-floppy --fs-uuid --set 8eee83de-573f-48dd-b8e9-80aa29887979
    linux /boot/vmlinuz-2.6.31-10-generic root=UUID=8eee83de-573f-48dd-b8e9-80aa29887979 ro single y
    initrd /boot/initrd.img-2.6.31-10-generic
}
menuentry "Ubuntu 9.04, kernel 2.6.28-15-generic (on /dev/sda8)" {
    insmod ext2
    set root=(hd0,8)
    search --no-floppy --fs-uuid --set 79e9dc92-8346-44a9-b74a-97b4a76c560e
    linux /boot/vmlinuz-2.6.28-15-generic root=UUID=79e9dc92-8346-44a9-b74a-97b4a76c560e ro quiet splash
    initrd /boot/initrd.img-2.6.28-15-generic
}
menuentry "Ubuntu 9.04, kernel 2.6.28-15-generic (recovery mode) (on /dev/sda8)" {
    insmod ext2
    set root=(hd0,8)
    search --no-floppy --fs-uuid --set 79e9dc92-8346-44a9-b74a-97b4a76c560e
    linux /boot/vmlinuz-2.6.28-15-generic root=UUID=79e9dc92-8346-44a9-b74a-97b4a76c560e ro single
    initrd /boot/initrd.img-2.6.28-15-generic
}
menuentry "Ubuntu 9.04, memtest86+ (on /dev/sda8)" {
    insmod ext2
    set root=(hd0,8)
    search --no-floppy --fs-uuid --set 79e9dc92-8346-44a9-b74a-97b4a76c560e
    linux /boot/memtest86+.bin 
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

```
Note that it is better to have a file with a name after 05_debian-theme just so that it is read before your custom file.  I have had no trouble with the 01-custom file and you can see where my custom background for the menu is found after the custom entries are loaded.

You can also see the menu items generated by os-prober for my 2 mandriva installs are.  None of them will do anything productive.

This is the way to perminantly edit your /boot/grub/grub.cfg file.

---

### Post by Slug71 on 2009-09-25
> **ranch hand said:**
> If you put that same entry in a custom file in grub.d it will not be over written the next time you run, or the installer runs, update grub.

For instance, my Mandriva installs are picked up but the generated menu entry does not do the job at all.  So I have this entry in /etc/grub.d/01_custom;
```

echo "Adding Mandriva2009-1-Gnome on sda12" >&2
cat << EOF
menuentry "Mandriva 2009 Gnome sda12" {
linux (hd0,12)/boot/vmlinuz
initrd (hd0,12)/boot/initrd.img
}
EOF

```
This OS was on this drive before any 9.10 installs were.  Since A2, when grub2 was introduced, update-grub has been run 100s of times.  It runs at least twice everytime you get a kernal update.  Anything that you put in grub.cfg is over written by the scripts in grub.d.

When you have the custom entries they are written in at the same time and then my grub.cfg looks like this;
```

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
load_env
set default="0"
if [ ${prev_saved_entry} ]; then
  saved_entry=${prev_saved_entry}
  save_env saved_entry
  prev_saved_entry=
  save_env prev_saved_entry
fi
insmod ext2
set root=(hd0,10)
search --no-floppy --fs-uuid --set 2a9c6ddd-4422-4fc5-a7ed-613cf3430b8c
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
set timeout=100
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/01_Custom ###
menuentry " Adding Kinky Stoner1.0 on sda102.6.31-9-generic" {
    set root=(hd0,10)
    search --no-floppy --fs-uuid --set 2a9c6ddd-4422-4fc5-a7ed-613cf3430b8c
    linux    /boot/vmlinuz-2.6.31-9-generic root=UUID=2a9c6ddd-4422-4fc5-a7ed-613cf3430b8c ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-9-generic
}
menuentry "Kinky Stoner1.0 on sda10 2.6.31-10-generic" {
    set quiet=1
    insmod ext2
    set root=(hd0,10)
    search --no-floppy --fs-uuid --set 2a9c6ddd-4422-4fc5-a7ed-613cf3430b8c
    linux    /boot/vmlinuz-2.6.31-10-generic root=UUID=2a9c6ddd-4422-4fc5-a7ed-613cf3430b8c ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-10-generic
}
menuentry "Kinky Stoner1.0 on sda10 2.6.31-10-generic (recovery mode)" {
    insmod ext2
    set root=(hd0,10)
    search --no-floppy --fs-uuid --set 2a9c6ddd-4422-4fc5-a7ed-613cf3430b8c
    linux    /boot/vmlinuz-2.6.31-10-generic root=UUID=2a9c6ddd-4422-4fc5-a7ed-613cf3430b8c ro single 
    initrd    /boot/initrd.img-2.6.31-10-generic
}
menuentry "KinkyA1, kernel 2.6.31-9-generic (on /dev/sda16)" {
    set root=(hd0,16)
    search --no-floppy --fs-uuid --set 037e8099-d605-4315-b637-f60c6ff692ed
    linux /boot/vmlinuz-2.6.31-9-generic root=UUID=037e8099-d605-4315-b637-f60c6ff692ed ro quiet splash
    initrd /boot/initrd.img-2.6.31-9-generic
}
menuentry " KinkyA4 2.6.31-9-generic(sda20)" {
    set root=(hd0,20)
    search --no-floppy --fs-uuid --set ec4ef79d-36b7-4821-b358-188953ec8d7a
    linux    /boot/vmlinuz-2.6.31-9-generic root=UUID=ec4ef79d-36b7-4821-b358-188953ec8d7a ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-9-generic
}
menuentry "KinkyStoner1.0 (on /dev/sda6)" {
    set root=(hd0,6)
    search --no-floppy --fs-uuid --set 8eee83de-573f-48dd-b8e9-80aa29887979
    linux /boot/vmlinuz-2.6.31-9-generic root=/dev/sda6
    initrd /boot/initrd.img-2.6.31-9-generic
}
menuentry "Jaunty 9.04, kernel 2.6.28-14-generic (on /dev/sda8)" {
        set root=(hd0,8)
        search --no-floppy --fs-uuid --set 79e9dc92-8346-44a9-b74a-97b4a76c560e
        linux /boot/vmlinuz-2.6.28-14-generic root=UUID=79e9dc92-8346-44a9-b74a-97b4a76c560e ro quiet splash
        initrd /boot/initrd.img-2.6.28-14-generic
}
menuentry "Stoner1.1, kernel 2.6.28-14-generic (on /dev/sda18)" {
    set root=(hd0,18)
    search --no-floppy --fs-uuid --set 0810f840-b2dc-4223-9132-d6d30103787e
    linux /boot/vmlinuz-2.6.28-14-generic root=UUID=0810f840-b2dc-4223-9132-d6d30103787e ro quiet splash
    initrd /boot/initrd.img-2.6.28-14-generic
}
menuentry "Mandriva 2009 Gnome sda12" {
linux (hd0,12)/boot/vmlinuz
initrd (hd0,12)/boot/initrd.img
}
menuentry "Mandriva 2009 KDE sda14" {
linux (hd0,14)/boot/vmlinuz
initrd (hd0,14)/boot/initrd.img
}
### END /etc/grub.d/01_Custom ###

### BEGIN /etc/grub.d/05_debian_theme ###
insmod ext2
set root=(hd0,10)
search --no-floppy --fs-uuid --set 2a9c6ddd-4422-4fc5-a7ed-613cf3430b8c
insmod png
if background_image /usr/share/images/desktop-base/bad-fruit.png ; then
  set color_normal=white/black
  set color_highlight=green/black
else
  set menu_color_normal=white/black
  set menu_color_highlight=black/white
fi
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry "Ubuntu, Linux 2.6.31-10-generic" {
    set quiet=1
    insmod ext2
    set root=(hd0,10)
    search --no-floppy --fs-uuid --set 2a9c6ddd-4422-4fc5-a7ed-613cf3430b8c
    linux    /boot/vmlinuz-2.6.31-10-generic root=UUID=2a9c6ddd-4422-4fc5-a7ed-613cf3430b8c ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-10-generic
}
menuentry "Ubuntu, Linux 2.6.31-10-generic (recovery mode)" {
    insmod ext2
    set root=(hd0,10)
    search --no-floppy --fs-uuid --set 2a9c6ddd-4422-4fc5-a7ed-613cf3430b8c
    linux    /boot/vmlinuz-2.6.31-10-generic root=UUID=2a9c6ddd-4422-4fc5-a7ed-613cf3430b8c ro single 
    initrd    /boot/initrd.img-2.6.31-10-generic
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
menuentry "linux (on /dev/sda12)" {
    insmod ext2
    set root=(hd0,12)
    search --no-floppy --fs-uuid --set c23ad2ca-67a5-4a42-8fcc-3baa6d8e454e
    linux /boot/vmlinuz BOOT_IMAGE=linux root=UUID=c23ad2ca-67a5-4a42-8fcc-3baa6d8e454e resume=UUID=59fe476e-6d4f-e390-ced9-f29328538dfc splash=silent vga=788
    initrd (hd0,11)/boot/initrd.img
}
menuentry "linux-nonfb (on /dev/sda12)" {
    insmod ext2
    set root=(hd0,12)
    search --no-floppy --fs-uuid --set c23ad2ca-67a5-4a42-8fcc-3baa6d8e454e
    linux /boot/vmlinuz BOOT_IMAGE=linux-nonfb root=UUID=c23ad2ca-67a5-4a42-8fcc-3baa6d8e454e resume=UUID=59fe476e-6d4f-e390-ced9-f29328538dfc
    initrd (hd0,11)/boot/initrd.img
}
menuentry "failsafe (on /dev/sda12)" {
    insmod ext2
    set root=(hd0,12)
    search --no-floppy --fs-uuid --set c23ad2ca-67a5-4a42-8fcc-3baa6d8e454e
    linux /boot/vmlinuz BOOT_IMAGE=failsafe root=UUID=c23ad2ca-67a5-4a42-8fcc-3baa6d8e454e failsafe
    initrd (hd0,11)/boot/initrd.img
}
menuentry "2.6.27-desktop586rc8-2mnb (on /dev/sda12)" {
    insmod ext2
    set root=(hd0,12)
    search --no-floppy --fs-uuid --set c23ad2ca-67a5-4a42-8fcc-3baa6d8e454e
    linux /boot/vmlinuz-2.6.27-desktop586-0.rc8.2mnb BOOT_IMAGE=2.6.27-desktop586rc8-2mnb root=UUID=c23ad2ca-67a5-4a42-8fcc-3baa6d8e454e resume=UUID=59fe476e-6d4f-e390-ced9-f29328538dfc splash=silent vga=788
    initrd (hd0,11)/boot/initrd-2.6.27-desktop586-0.rc8.2mnb.img
}
menuentry "desktop586 2.6.27.19-1mnb (on /dev/sda12)" {
    insmod ext2
    set root=(hd0,12)
    search --no-floppy --fs-uuid --set c23ad2ca-67a5-4a42-8fcc-3baa6d8e454e
    linux /boot/vmlinuz-2.6.27.19-desktop586-1mnb BOOT_IMAGE=desktop586_2.6.27.19-1mnb root=UUID=c23ad2ca-67a5-4a42-8fcc-3baa6d8e454e resume=UUID=59fe476e-6d4f-e390-ced9-f29328538dfc splash=silent vga=788
    initrd (hd0,11)/boot/initrd-2.6.27.19-desktop586-1mnb.img
}
menuentry "desktop586 2.6.27.14-1mnb (on /dev/sda12)" {
    insmod ext2
    set root=(hd0,12)
    search --no-floppy --fs-uuid --set c23ad2ca-67a5-4a42-8fcc-3baa6d8e454e
    linux /boot/vmlinuz-2.6.27.14-desktop586-1mnb BOOT_IMAGE=desktop586_2.6.27.14-1mnb root=UUID=c23ad2ca-67a5-4a42-8fcc-3baa6d8e454e resume=UUID=59fe476e-6d4f-e390-ced9-f29328538dfc splash=silent vga=788
    initrd (hd0,11)/boot/initrd-2.6.27.14-desktop586-1mnb.img
}
menuentry "desktop586 2.6.27.21-1mnb (on /dev/sda12)" {
    insmod ext2
    set root=(hd0,12)
    search --no-floppy --fs-uuid --set c23ad2ca-67a5-4a42-8fcc-3baa6d8e454e
    linux /boot/vmlinuz-2.6.27.21-desktop586-1mnb BOOT_IMAGE=desktop586_2.6.27.21-1mnb root=UUID=c23ad2ca-67a5-4a42-8fcc-3baa6d8e454e resume=UUID=59fe476e-6d4f-e390-ced9-f29328538dfc splash=silent vga=788
    initrd (hd0,11)/boot/initrd-2.6.27.21-desktop586-1mnb.img
}
menuentry "desktop586 2.6.27.24-1mnb (on /dev/sda12)" {
    insmod ext2
    set root=(hd0,12)
    search --no-floppy --fs-uuid --set c23ad2ca-67a5-4a42-8fcc-3baa6d8e454e
    linux /boot/vmlinuz-2.6.27.24-desktop586-1mnb BOOT_IMAGE=desktop586_2.6.27.24-1mnb root=UUID=c23ad2ca-67a5-4a42-8fcc-3baa6d8e454e resume=UUID=59fe476e-6d4f-e390-ced9-f29328538dfc splash=silent vga=788
    initrd (hd0,11)/boot/initrd-2.6.27.24-desktop586-1mnb.img
}
menuentry "desktop586 2.6.27.24-2mnb (on /dev/sda12)" {
    insmod ext2
    set root=(hd0,12)
    search --no-floppy --fs-uuid --set c23ad2ca-67a5-4a42-8fcc-3baa6d8e454e
    linux /boot/vmlinuz-2.6.27.24-desktop586-2mnb BOOT_IMAGE=desktop586_2.6.27.24-2mnb root=UUID=c23ad2ca-67a5-4a42-8fcc-3baa6d8e454e resume=UUID=59fe476e-6d4f-e390-ced9-f29328538dfc splash=silent vga=788
    initrd (hd0,11)/boot/initrd-2.6.27.24-desktop586-2mnb.img
}
menuentry "linux (on /dev/sda14)" {
    insmod ext2
    set root=(hd0,14)
    search --no-floppy --fs-uuid --set 7be62a2a-eb6e-43f3-8712-87abbf7182a9
    linux /boot/vmlinuz BOOT_IMAGE=linux root=UUID=7be62a2a-eb6e-43f3-8712-87abbf7182a9 resume=UUID=59fe476e-6d4f-e390-ced9-f29328538dfc splash=silent vga=788
    initrd (hd0,13)/boot/initrd.img
}
menuentry "linux-nonfb (on /dev/sda14)" {
    insmod ext2
    set root=(hd0,14)
    search --no-floppy --fs-uuid --set 7be62a2a-eb6e-43f3-8712-87abbf7182a9
    linux /boot/vmlinuz BOOT_IMAGE=linux-nonfb root=UUID=7be62a2a-eb6e-43f3-8712-87abbf7182a9 resume=UUID=59fe476e-6d4f-e390-ced9-f29328538dfc
    initrd (hd0,13)/boot/initrd.img
}
menuentry "failsafe (on /dev/sda14)" {
    insmod ext2
    set root=(hd0,14)
    search --no-floppy --fs-uuid --set 7be62a2a-eb6e-43f3-8712-87abbf7182a9
    linux /boot/vmlinuz BOOT_IMAGE=failsafe root=UUID=7be62a2a-eb6e-43f3-8712-87abbf7182a9 failsafe
    initrd (hd0,13)/boot/initrd.img
}
menuentry "2.6.27-desktop586rc8-2mnb (on /dev/sda14)" {
    insmod ext2
    set root=(hd0,14)
    search --no-floppy --fs-uuid --set 7be62a2a-eb6e-43f3-8712-87abbf7182a9
    linux /boot/vmlinuz-2.6.27-desktop586-0.rc8.2mnb BOOT_IMAGE=2.6.27-desktop586rc8-2mnb root=UUID=7be62a2a-eb6e-43f3-8712-87abbf7182a9 resume=UUID=59fe476e-6d4f-e390-ced9-f29328538dfc splash=silent vga=788
    initrd (hd0,13)/boot/initrd-2.6.27-desktop586-0.rc8.2mnb.img
}
menuentry "desktop586 2.6.27.19-1mnb (on /dev/sda14)" {
    insmod ext2
    set root=(hd0,14)
    search --no-floppy --fs-uuid --set 7be62a2a-eb6e-43f3-8712-87abbf7182a9
    linux /boot/vmlinuz-2.6.27.19-desktop586-1mnb BOOT_IMAGE=desktop586_2.6.27.19-1mnb root=UUID=7be62a2a-eb6e-43f3-8712-87abbf7182a9 resume=UUID=59fe476e-6d4f-e390-ced9-f29328538dfc splash=silent vga=788
    initrd (hd0,13)/boot/initrd-2.6.27.19-desktop586-1mnb.img
}
menuentry "desktop586 2.6.27.21-1mnb (on /dev/sda14)" {
    insmod ext2
    set root=(hd0,14)
    search --no-floppy --fs-uuid --set 7be62a2a-eb6e-43f3-8712-87abbf7182a9
    linux /boot/vmlinuz-2.6.27.21-desktop586-1mnb BOOT_IMAGE=desktop586_2.6.27.21-1mnb root=UUID=7be62a2a-eb6e-43f3-8712-87abbf7182a9 resume=UUID=59fe476e-6d4f-e390-ced9-f29328538dfc splash=silent vga=788
    initrd (hd0,13)/boot/initrd-2.6.27.21-desktop586-1mnb.img
}
menuentry "desktop586 2.6.27.24-1mnb (on /dev/sda14)" {
    insmod ext2
    set root=(hd0,14)
    search --no-floppy --fs-uuid --set 7be62a2a-eb6e-43f3-8712-87abbf7182a9
    linux /boot/vmlinuz-2.6.27.24-desktop586-1mnb BOOT_IMAGE=desktop586_2.6.27.24-1mnb root=UUID=7be62a2a-eb6e-43f3-8712-87abbf7182a9 resume=UUID=59fe476e-6d4f-e390-ced9-f29328538dfc splash=silent vga=788
    initrd (hd0,13)/boot/initrd-2.6.27.24-desktop586-1mnb.img
}
menuentry "desktop586 2.6.27.24-2mnb (on /dev/sda14)" {
    insmod ext2
    set root=(hd0,14)
    search --no-floppy --fs-uuid --set 7be62a2a-eb6e-43f3-8712-87abbf7182a9
    linux /boot/vmlinuz-2.6.27.24-desktop586-2mnb BOOT_IMAGE=desktop586_2.6.27.24-2mnb root=UUID=7be62a2a-eb6e-43f3-8712-87abbf7182a9 resume=UUID=59fe476e-6d4f-e390-ced9-f29328538dfc splash=silent vga=788
    initrd (hd0,13)/boot/initrd-2.6.27.24-desktop586-2mnb.img
}
menuentry "KinkyA1 on sda16 2.6.31-10-generic (on /dev/sda16)" {
    insmod ext2
    set root=(hd0,16)
    search --no-floppy --fs-uuid --set 593f6939-f51c-496d-a90a-c7cb942a22af
    linux /boot/vmlinuz-2.6.31-10-generic root=UUID=593f6939-f51c-496d-a90a-c7cb942a22af ro quiet splash
    initrd /boot/initrd.img-2.6.31-10-generic
}
menuentry "KinkyA4 on sda20 2.6.31-10-generic (on /dev/sda16)" {
    insmod ext2
    set root=(hd0,16)
    search --no-floppy --fs-uuid --set 593f6939-f51c-496d-a90a-c7cb942a22af
    linux /boot/vmlinuz-2.6.31-10-generic root=UUID=ec4ef79d-36b7-4821-b358-188953ec8d7a ro quiet splash
    initrd /boot/initrd.img-2.6.31-10-generic
}
menuentry "Kinky Stoner1.0 on sda10 2.6.31-10-generic (on /dev/sda16)" {
    insmod ext2
    set root=(hd0,16)
    search --no-floppy --fs-uuid --set 593f6939-f51c-496d-a90a-c7cb942a22af
    linux /boot/vmlinuz-2.6.31-10-generic root=UUID=2a9c6ddd-4422-4fc5-a7ed-613cf3430b8c ro quiet splash
    initrd /boot/initrd.img-2.6.31-10-generic
}
menuentry "KinkyStoner1.0 on sda6 2.6.31-10-generic (on /dev/sda16)" {
    insmod ext2
    set root=(hd0,16)
    search --no-floppy --fs-uuid --set 593f6939-f51c-496d-a90a-c7cb942a22af
    linux /boot/vmlinuz-2.6.31-10-generic root=UUID=8eee83de-573f-48dd-b8e9-80aa29887979 ro y y
    initrd /boot/initrd.img-2.6.31-10-generic
}
menuentry "Ubuntu, Linux 2.6.31-10-generic (on /dev/sda16)" {
    insmod ext2
    set root=(hd0,16)
    search --no-floppy --fs-uuid --set 593f6939-f51c-496d-a90a-c7cb942a22af
    linux /boot/vmlinuz-2.6.31-10-generic root=UUID=593f6939-f51c-496d-a90a-c7cb942a22af ro quiet splash
    initrd /boot/initrd.img-2.6.31-10-generic
}
menuentry "Ubuntu, Linux 2.6.31-10-generic (recovery mode) (on /dev/sda16)" {
    insmod ext2
    set root=(hd0,16)
    search --no-floppy --fs-uuid --set 593f6939-f51c-496d-a90a-c7cb942a22af
    linux /boot/vmlinuz-2.6.31-10-generic root=UUID=593f6939-f51c-496d-a90a-c7cb942a22af ro single
    initrd /boot/initrd.img-2.6.31-10-generic
}
menuentry "Ubuntu 9.04, kernel 2.6.28-15-generic (on /dev/sda18)" {
    insmod ext2
    set root=(hd0,18)
    search --no-floppy --fs-uuid --set 0810f840-b2dc-4223-9132-d6d30103787e
    linux /boot/vmlinuz-2.6.28-15-generic root=UUID=0810f840-b2dc-4223-9132-d6d30103787e ro quiet splash
    initrd /boot/initrd.img-2.6.28-15-generic
}
menuentry "Ubuntu 9.04, kernel 2.6.28-15-generic (recovery mode) (on /dev/sda18)" {
    insmod ext2
    set root=(hd0,18)
    search --no-floppy --fs-uuid --set 0810f840-b2dc-4223-9132-d6d30103787e
    linux /boot/vmlinuz-2.6.28-15-generic root=UUID=0810f840-b2dc-4223-9132-d6d30103787e ro single
    initrd /boot/initrd.img-2.6.28-15-generic
}
menuentry "Ubuntu 9.04, kernel 2.6.28-14-generic (on /dev/sda18)" {
    insmod ext2
    set root=(hd0,18)
    search --no-floppy --fs-uuid --set 0810f840-b2dc-4223-9132-d6d30103787e
    linux /boot/vmlinuz-2.6.28-14-generic root=UUID=0810f840-b2dc-4223-9132-d6d30103787e ro quiet splash
    initrd /boot/initrd.img-2.6.28-14-generic
}
menuentry "Ubuntu 9.04, kernel 2.6.28-14-generic (recovery mode) (on /dev/sda18)" {
    insmod ext2
    set root=(hd0,18)
    search --no-floppy --fs-uuid --set 0810f840-b2dc-4223-9132-d6d30103787e
    linux /boot/vmlinuz-2.6.28-14-generic root=UUID=0810f840-b2dc-4223-9132-d6d30103787e ro single
    initrd /boot/initrd.img-2.6.28-14-generic
}
menuentry "Ubuntu 9.04, kernel 2.6.28-13-generic (on /dev/sda18)" {
    insmod ext2
    set root=(hd0,18)
    search --no-floppy --fs-uuid --set 0810f840-b2dc-4223-9132-d6d30103787e
    linux /boot/vmlinuz-2.6.28-13-generic root=UUID=0810f840-b2dc-4223-9132-d6d30103787e ro quiet splash
    initrd /boot/initrd.img-2.6.28-13-generic
}
menuentry "Ubuntu 9.04, kernel 2.6.28-13-generic (recovery mode) (on /dev/sda18)" {
    insmod ext2
    set root=(hd0,18)
    search --no-floppy --fs-uuid --set 0810f840-b2dc-4223-9132-d6d30103787e
    linux /boot/vmlinuz-2.6.28-13-generic root=UUID=0810f840-b2dc-4223-9132-d6d30103787e ro single
    initrd /boot/initrd.img-2.6.28-13-generic
}
menuentry "Ubuntu 9.04, memtest86+ (on /dev/sda18)" {
    insmod ext2
    set root=(hd0,18)
    search --no-floppy --fs-uuid --set 0810f840-b2dc-4223-9132-d6d30103787e
    linux /boot/memtest86+.bin 
}
menuentry "Ubuntu 9.04, kernel 2.6.28-13-generic (on /dev/sda10) (Stoner1.0-32) (on /dev/sda18)" {
    insmod ext2
    set root=(hd0,18)
    search --no-floppy --fs-uuid --set 0810f840-b2dc-4223-9132-d6d30103787e
    linux /boot/vmlinuz-2.6.28-13-generic root=UUID=2a9c6ddd-4422-4fc5-a7ed-613cf3430b8c ro quiet splash
    initrd /boot/initrd.img-2.6.28-13-generic
}
menuentry "Ubuntu 9.04, kernel 2.6.28-13-generic (on /dev/sda8) (Jaunty-32) (on /dev/sda18)" {
    insmod ext2
    set root=(hd0,18)
    search --no-floppy --fs-uuid --set 0810f840-b2dc-4223-9132-d6d30103787e
    linux /boot/vmlinuz-2.6.28-13-generic root=UUID=79e9dc92-8346-44a9-b74a-97b4a76c560e ro quiet splash
    initrd /boot/initrd.img-2.6.28-13-generic
}
menuentry "KinkyA4 on sda20 2.6.31-10-generic (on /dev/sda20)" {
    insmod ext2
    set root=(hd0,20)
    search --no-floppy --fs-uuid --set ec4ef79d-36b7-4821-b358-188953ec8d7a
    linux /boot/vmlinuz-2.6.31-10-generic root=UUID=ec4ef79d-36b7-4821-b358-188953ec8d7a ro quiet splash
    initrd /boot/initrd.img-2.6.31-10-generic
}
menuentry "KinkyA4 on sda20 2.6.31-10-generic (recovery mode) (on /dev/sda20)" {
    insmod ext2
    set root=(hd0,20)
    search --no-floppy --fs-uuid --set ec4ef79d-36b7-4821-b358-188953ec8d7a
    linux /boot/vmlinuz-2.6.31-10-generic root=UUID=ec4ef79d-36b7-4821-b358-188953ec8d7a ro single
    initrd /boot/initrd.img-2.6.31-10-generic
}
menuentry "Kinky Stoner1.0 on sda10 2.6.31-10-generic (on /dev/sda20)" {
    insmod ext2
    set root=(hd0,20)
    search --no-floppy --fs-uuid --set ec4ef79d-36b7-4821-b358-188953ec8d7a
    linux /boot/vmlinuz-2.6.31-10-generic root=UUID=2a9c6ddd-4422-4fc5-a7ed-613cf3430b8c ro quiet splash
    initrd /boot/initrd.img-2.6.31-10-generic
}
menuentry "KinkyStoner1.0 on sda6 2.6.31-10-generic (on /dev/sda20)" {
    insmod ext2
    set root=(hd0,20)
    search --no-floppy --fs-uuid --set ec4ef79d-36b7-4821-b358-188953ec8d7a
    linux /boot/vmlinuz-2.6.31-10-generic root=UUID=8eee83de-573f-48dd-b8e9-80aa29887979 ro y y
    initrd /boot/initrd.img-2.6.31-10-generic
}
menuentry "Ubuntu, Linux 2.6.31-10-generic (on /dev/sda20)" {
    insmod ext2
    set root=(hd0,20)
    search --no-floppy --fs-uuid --set ec4ef79d-36b7-4821-b358-188953ec8d7a
    linux /boot/vmlinuz-2.6.31-10-generic root=UUID=ec4ef79d-36b7-4821-b358-188953ec8d7a ro quiet splash
    initrd /boot/initrd.img-2.6.31-10-generic
}
menuentry "Ubuntu, Linux 2.6.31-10-generic (recovery mode) (on /dev/sda20)" {
    insmod ext2
    set root=(hd0,20)
    search --no-floppy --fs-uuid --set ec4ef79d-36b7-4821-b358-188953ec8d7a
    linux /boot/vmlinuz-2.6.31-10-generic root=UUID=ec4ef79d-36b7-4821-b358-188953ec8d7a ro single
    initrd /boot/initrd.img-2.6.31-10-generic
}
menuentry "KinkyStoner1.0 on sda6 (2.6.31-10-generic) (on /dev/sda6)" {
    insmod ext2
    set root=(hd0,6)
    search --no-floppy --fs-uuid --set 8eee83de-573f-48dd-b8e9-80aa29887979
    linux /boot/vmlinuz-2.6.31-10-generic root=UUID=8eee83de-573f-48dd-b8e9-80aa29887979 ro y y
    initrd /boot/initrd.img-2.6.31-10-generic
}
menuentry "KinkyStoner1.0 on sda6 2.6.31-10-generic (recovery mode) (on /dev/sda6)" {
    insmod ext2
    set root=(hd0,6)
    search --no-floppy --fs-uuid --set 8eee83de-573f-48dd-b8e9-80aa29887979
    linux /boot/vmlinuz-2.6.31-10-generic root=UUID=8eee83de-573f-48dd-b8e9-80aa29887979 ro single y
    initrd /boot/initrd.img-2.6.31-10-generic
}
menuentry "Kinky Stoner1.0 on sda10 (2.6.31-10-generic) (on /dev/sda6)" {
    insmod ext2
    set root=(hd0,6)
    search --no-floppy --fs-uuid --set 8eee83de-573f-48dd-b8e9-80aa29887979
    linux /boot/vmlinuz-2.6.31-10-generic root=UUID=2a9c6ddd-4422-4fc5-a7ed-613cf3430b8c ro quiet splash
    initrd /boot/initrd.img-2.6.31-10-generic
}
menuentry "KinkyA1 on sda16 (2.6.31-10-generic) (on /dev/sda6)" {
    insmod ext2
    set root=(hd0,6)
    search --no-floppy --fs-uuid --set 8eee83de-573f-48dd-b8e9-80aa29887979
    linux /boot/vmlinuz-2.6.31-10-generic root=UUID=593f6939-f51c-496d-a90a-c7cb942a22af ro quiet splash
    initrd /boot/initrd.img-2.6.31-10-generic
}
menuentry "KinkyA4 on sda20 2.6.31-10-generic (on /dev/sda6)" {
    insmod ext2
    set root=(hd0,6)
    search --no-floppy --fs-uuid --set 8eee83de-573f-48dd-b8e9-80aa29887979
    linux /boot/vmlinuz-2.6.31-10-generic root=UUID=ec4ef79d-36b7-4821-b358-188953ec8d7a ro quiet splash
    initrd /boot/initrd.img-2.6.31-10-generic
}
menuentry "Ubuntu, Linux 2.6.31-10-generic (on /dev/sda6)" {
    insmod ext2
    set root=(hd0,6)
    search --no-floppy --fs-uuid --set 8eee83de-573f-48dd-b8e9-80aa29887979
    linux /boot/vmlinuz-2.6.31-10-generic root=UUID=8eee83de-573f-48dd-b8e9-80aa29887979 ro y y
    initrd /boot/initrd.img-2.6.31-10-generic
}
menuentry "Ubuntu, Linux 2.6.31-10-generic (recovery mode) (on /dev/sda6)" {
    insmod ext2
    set root=(hd0,6)
    search --no-floppy --fs-uuid --set 8eee83de-573f-48dd-b8e9-80aa29887979
    linux /boot/vmlinuz-2.6.31-10-generic root=UUID=8eee83de-573f-48dd-b8e9-80aa29887979 ro single y
    initrd /boot/initrd.img-2.6.31-10-generic
}
menuentry "Ubuntu 9.04, kernel 2.6.28-15-generic (on /dev/sda8)" {
    insmod ext2
    set root=(hd0,8)
    search --no-floppy --fs-uuid --set 79e9dc92-8346-44a9-b74a-97b4a76c560e
    linux /boot/vmlinuz-2.6.28-15-generic root=UUID=79e9dc92-8346-44a9-b74a-97b4a76c560e ro quiet splash
    initrd /boot/initrd.img-2.6.28-15-generic
}
menuentry "Ubuntu 9.04, kernel 2.6.28-15-generic (recovery mode) (on /dev/sda8)" {
    insmod ext2
    set root=(hd0,8)
    search --no-floppy --fs-uuid --set 79e9dc92-8346-44a9-b74a-97b4a76c560e
    linux /boot/vmlinuz-2.6.28-15-generic root=UUID=79e9dc92-8346-44a9-b74a-97b4a76c560e ro single
    initrd /boot/initrd.img-2.6.28-15-generic
}
menuentry "Ubuntu 9.04, memtest86+ (on /dev/sda8)" {
    insmod ext2
    set root=(hd0,8)
    search --no-floppy --fs-uuid --set 79e9dc92-8346-44a9-b74a-97b4a76c560e
    linux /boot/memtest86+.bin 
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

```
Note that it is better to have a file with a name after 05_debian-theme just so that it is read before your custom file.  I have had no trouble with the 01-custom file and you can see where my custom background for the menu is found after the custom entries are loaded.

You can also see the menu items generated by os-prober for my 2 mandriva installs are.  None of them will do anything productive.

This is the way to perminantly edit your /boot/grub/grub.cfg file.

Youre the man ranch hand! Thanks for that. :)

---

### Post by mickie.kext on 2009-09-25
Did someon test it on GPT disk? Or I will be the first one... if I dare to risk Snow Leopard install, that is.

---

### Post by prattmd on 2009-09-25
Ok, need some help with grub2
I have 3 partitions, one with moblin, one with fedora, and one with karmic.  Karmic installed last.  grub2 is not recognizing moblin or f12, even after running sudo update-grub

Any ideas?
How can I insert the correct statements to load?

---

### Post by Gina on 2009-09-25
I presume there is a reason for this complicated way of doing things :lolflag:

---

### Post by VMC on 2009-09-25
> **prattmd said:**
> Ok, need some help with grub2
I have 3 partitions, one with moblin, one with fedora, and one with karmic.  Karmic installed last.  grub2 is not recognizing moblin or f12, even after running sudo update-grub

Any ideas?
How can I insert the correct statements to load?

What's the output of the update-grub? I have Fedora11 and there's a problem in that grub2 doesn't insert the initrd line. I have to do that manually.

---

### Post by ranch hand on 2009-09-25
> **Slug71 said:**
> Youre the man ranch hand! Thanks for that. :)
I am glad that it is working.  I hope you put your custom file above the debian-theme file.

While I have had no trouble with that, it does seem that the theme needs to be loaded first.

There is another type of entry that I have not gotten to work until recently.  I am only using it on one 9.10 variation.  It has been working for a few days, one of the grub updates got it working.  This is basically the same as my Mandriva entries and it is supposed to work with all OS'.

It has seemed to wori for every thing but Ubuntu.  It does not define the kernal  at all, just boots to the most up to date kernal.

I just updated my 64bit stuff and sure enough the bugger booted me up and into 2.6.31-11.

I am not going to post my 64bit grub.cfg.  It is pretty large.  But here is the entry to the one that is using the type of entry that you really need for all your OS' (if it works);
```

echo "Adding KinkyStonerA2 on sda8 (2.6.31-10-generic)" >&2 
cat << EOF 
menuentry "KinkyStonerA2 on sda8 2.6.31-10-generic" {
        set root=(hd0,8)
        linux /vmlinuz root=/dev/sda8 so quiet splash
        initrd /initrd.img
}
EOF

```
I  know, it says "KinkyStonerA2 on sda8 2.6.31-10-generic".  I did not change the 10 to 11.  I will be dropping the the kernal designation altogether the next time I am on the 64bit test drive and on the OS that I am using for boot/root.

I am going to change all my entries to that type on that menu.

Note that there is no uuid or anything just "set root" and "root=" to define the partition.  Neat.  You need to remember that while the "hd0" part is still numbered as in grub-legacy, the "8" is the same as gparted in grub2 ( in grub-legacy this would have been (hd0,7)) it is kind of hard to remember that for me.

---

### Post by ranch hand on 2009-09-25
> **Gina said:**
> I presume there is a reason for this complicated way of doing things :lolflag:
I am not sure that this comment is aimed at me, if not, I am sorry for wasting time.

This is not really any different than editing your old /boot/grub/menu.lst, nor is it any harder although you really want to create the lower named custom file so that the buggers are on top of the menu you see on screen.

The real change in grub2 is that it is completely script driven.  With all the new media that you can boot from, and all the new file systems that folks are using, grub-legacy was just going to go down hill as it became bloated with patches.  Grub2 on the other hand will just need scripts updated or added.

It is a new thing and still kind of rough but I think it is going to be very good.  I think that having people that upgrade stay with grub-legacy is a good idea too.  I do not see all the bugs being out of grub2 by the 9.10 release date.  Os-prober is the problem.

I think wee are going to see a lot of pissing and moaning, mainly by those of us who have come to know and love grub-legacy.  By the time that 10.04 comes out and the thing is working (I am sure) the noobs will love it and grumpy geezers (like me) will still be groaning.

The complicated way to do this is to edit your /boot/grub/grub.cfg file.  Change the permissions, edit, redo it EVERY time update grub is run, such as with the kernal update today.

---

### Post by Slug71 on 2009-09-26
This is what my grub.cfg looks like. Its below the Debian theme and above my Ubuntu(sda3) install. sda10 is Kubuntu. The FreeBSD(PC-BSD) entry doesnt load. Get a unknown filesystem error.
Everything else boots fine though.


> #
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
load_env
set default="0"
if [ ${prev_saved_entry} ]; then
  saved_entry=${prev_saved_entry}
  save_env saved_entry
  prev_saved_entry=
  save_env prev_saved_entry
fi
insmod ext2
set root=(hd0,3)
search --no-floppy --fs-uuid --set 600c3888-b971-404d-9512-c41ca6330290
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
set timeout=10
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/white
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/01_Custom ###
menuentry "ReactOS" {
        set root=(hd0,1)
        multiboot /freeldr.sys
}
menuentry "freebsd" {
	set root=(hd0,2,a)
       freebsd	/boot/loader 
}
### END /etc/grub.d/01_Custom ###

### BEGIN /etc/grub.d/10_linux ###
menuentry "Ubuntu, Linux 2.6.31-10-generic" {
	set quiet=1
	insmod ext2
	set root=(hd0,3)
	search --no-floppy --fs-uuid --set 600c3888-b971-404d-9512-c41ca6330290
	linux	/boot/vmlinuz-2.6.31-10-generic root=UUID=600c3888-b971-404d-9512-c41ca6330290 ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-10-generic
}
menuentry "Ubuntu, Linux 2.6.31-10-generic (recovery mode)" {
	insmod ext2
	set root=(hd0,3)
	search --no-floppy --fs-uuid --set 600c3888-b971-404d-9512-c41ca6330290
	linux	/boot/vmlinuz-2.6.31-10-generic root=UUID=600c3888-b971-404d-9512-c41ca6330290 ro single 
	initrd	/boot/initrd.img-2.6.31-10-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Ubuntu, Linux 2.6.31-10-generic (on /dev/sda10)" {
	insmod ext2
	set root=(hd0,10)
	search --no-floppy --fs-uuid --set 439cf7ba-0519-41c9-8593-3b92374c4fde
	linux /boot/vmlinuz-2.6.31-10-generic root=UUID=439cf7ba-0519-41c9-8593-3b92374c4fde ro quiet splash
	initrd /boot/initrd.img-2.6.31-10-generic
}
menuentry "Ubuntu, Linux 2.6.31-10-generic (recovery mode) (on /dev/sda10)" {
	insmod ext2
	set root=(hd0,10)
	search --no-floppy --fs-uuid --set 439cf7ba-0519-41c9-8593-3b92374c4fde
	linux /boot/vmlinuz-2.6.31-10-generic root=UUID=439cf7ba-0519-41c9-8593-3b92374c4fde ro single
	initrd /boot/initrd.img-2.6.31-10-generic
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

---

### Post by ranch hand on 2009-09-26
> **Slug71 said:**
> This is what my grub.cfg looks like. Its below the Debian theme and above my Ubuntu(sda3) install. sda10 is Kubuntu. The FreeBSD(PC-BSD) entry doesnt load. Get a unknown filesystem error.
Everything else boots fine though.
Wow, I never heard of ReactOS.  BSD is a closed book to me, have never tried it.

I thinks it would be good to start another thread for BSD and grub2.  Someone out there is doing this.

I have been working to get going on grub2 since A2 came out with it and have collected a number of links.  Some are more useful than others but they may contain a hint that you may recognize as useful;
> 
[http://grub.enbug.org/](http://grub.enbug.org/)

[http://grub.enbug.org/Manual](http://grub.enbug.org/Manual)

[http://grub.enbug.org/CommandList](http://grub.enbug.org/CommandList)

[http://www.gnu.org/software/grub/](http://www.gnu.org/software/grub/)

[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

[https://wiki.ubuntu.com/Grub2#Adding%20Entries%20to%20Grub%202](https://wiki.ubuntu.com/Grub2#Adding%20Entries%20to%20Grub%202)

[http://members.iinet.net/~herman546/p20.html](http://members.iinet.net/~herman546/p20.html)

[http://members.iinet.net/~herman546/p20/GRUB2%20CLI%20Mode%20Commands.html#cli_loopback](http://members.iinet.net/~herman546/p20/GRUB2%20CLI%20Mode%20Commands.html#cli_loopback)

If you (I hope you do) start a thread on this, I would be really happy if you would post a link here to it.

There is an awful lot to learn in a short time if there are going to be enough of us to help folks when this is released.

---

### Post by moviemaniac on 2009-09-26
A comment on Grub2 from me: I was excited when I saw it detected OSX but it doesn't wanna boot it. When I select OSX from Grub's menu, it goes to a blank screen and reboots the machine after a few seconds.

Here's my config:

> #
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
load_env
set default="0"
if [ ${prev_saved_entry} ]; then
  saved_entry=${prev_saved_entry}
  save_env saved_entry
  prev_saved_entry=
  save_env prev_saved_entry
fi
insmod ext2
set root=(hd0,3)
search --no-floppy --fs-uuid --set 4f27142f-4f67-41ff-9458-941c0ff0dafe
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
set timeout=10
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/white
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry "Ubuntu, Linux 2.6.31-11-generic" {
	set quiet=1
	insmod ext2
	set root=(hd0,3)
	search --no-floppy --fs-uuid --set 4f27142f-4f67-41ff-9458-941c0ff0dafe
	linux	/boot/vmlinuz-2.6.31-11-generic root=UUID=4f27142f-4f67-41ff-9458-941c0ff0dafe ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-11-generic
}
menuentry "Ubuntu, Linux 2.6.31-11-generic (recovery mode)" {
	insmod ext2
	set root=(hd0,3)
	search --no-floppy --fs-uuid --set 4f27142f-4f67-41ff-9458-941c0ff0dafe
	linux	/boot/vmlinuz-2.6.31-11-generic root=UUID=4f27142f-4f67-41ff-9458-941c0ff0dafe ro single 
	initrd	/boot/initrd.img-2.6.31-11-generic
}
menuentry "Ubuntu, Linux 2.6.31-10-generic" {
	set quiet=1
	insmod ext2
	set root=(hd0,3)
	search --no-floppy --fs-uuid --set 4f27142f-4f67-41ff-9458-941c0ff0dafe
	linux	/boot/vmlinuz-2.6.31-10-generic root=UUID=4f27142f-4f67-41ff-9458-941c0ff0dafe ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-10-generic
}
menuentry "Ubuntu, Linux 2.6.31-10-generic (recovery mode)" {
	insmod ext2
	set root=(hd0,3)
	search --no-floppy --fs-uuid --set 4f27142f-4f67-41ff-9458-941c0ff0dafe
	linux	/boot/vmlinuz-2.6.31-10-generic root=UUID=4f27142f-4f67-41ff-9458-941c0ff0dafe ro single 
	initrd	/boot/initrd.img-2.6.31-10-generic
}
menuentry "Ubuntu, Linux 2.6.31-5-generic" {
	set quiet=1
	insmod ext2
	set root=(hd0,3)
	search --no-floppy --fs-uuid --set 4f27142f-4f67-41ff-9458-941c0ff0dafe
	linux	/boot/vmlinuz-2.6.31-5-generic root=UUID=4f27142f-4f67-41ff-9458-941c0ff0dafe ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-5-generic
}
menuentry "Ubuntu, Linux 2.6.31-5-generic (recovery mode)" {
	insmod ext2
	set root=(hd0,3)
	search --no-floppy --fs-uuid --set 4f27142f-4f67-41ff-9458-941c0ff0dafe
	linux	/boot/vmlinuz-2.6.31-5-generic root=UUID=4f27142f-4f67-41ff-9458-941c0ff0dafe ro single 
	initrd	/boot/initrd.img-2.6.31-5-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Mac OS X (on /dev/sda2)" {
	insmod hfsplus
	set root=(hd0,2)
	search --no-floppy --fs-uuid --set 9ec541cfafe0ec2a
        insmod vbe
        do_resume=0
        if [ /var/vm/sleepimage -nt10 / ]; then
           if xnu_resume /var/vm/sleepimage; then
             do_resume=1
           fi
        fi
        if [ $do_resume == 0 ]; then
           xnu_uuid 9ec541cfafe0ec2a uuid
           if [ -f /Extra/DSDT.aml ]; then
              acpi -e /Extra/DSDT.aml
           fi
           xnu_kernel /mach_kernel boot-uuid=${uuid} rd=*uuid
           if [ /System/Library/Extensions.mkext -nt /System/Library/Extensions ]; then
              xnu_mkext /System/Library/Extensions.mkext
           else
              xnu_kextdir /System/Library/Extensions
           fi
           if [ -f /Extra/Extensions.mkext ]; then
              xnu_mkext /Extra/Extensions.mkext
           fi
           if [ -d /Extra/Extensions ]; then
              xnu_kextdir /Extra/Extensions
           fi
           if [ -f /Extra/devtree.txt ]; then
              xnu_devtree /Extra/devtree.txt
           fi
           if [ -f /Extra/splash.jpg ]; then
              insmod jpeg
              xnu_splash /Extra/splash.jpg
           fi
           if [ -f /Extra/splash.png ]; then
              insmod png
              xnu_splash /Extra/splash.png
           fi
           if [ -f /Extra/splash.tga ]; then
              insmod tga
              xnu_splash /Extra/splash.tga
           fi
        fi
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

---

### Post by Slug71 on 2009-09-26
> **ranch hand said:**
> Wow, I never heard of ReactOS.  BSD is a closed book to me, have never tried it.

I thinks it would be good to start another thread for BSD and grub2.  Someone out there is doing this.

I have been working to get going on grub2 since A2 came out with it and have collected a number of links.  Some are more useful than others but they may contain a hint that you may recognize as useful;

If you (I hope you do) start a thread on this, I would be really happy if you would post a link here to it.

There is an awful lot to learn in a short time if there are going to be enough of us to help folks when this is released.

I started a thread in General Help but no hits there yet.

[http://ubuntuforums.org/showthread.php?t=1275575](http://ubuntuforums.org/showthread.php?t=1275575)

Also this one..

[http://ubuntuforums.org/showthread.php?t=1269987](http://ubuntuforums.org/showthread.php?t=1269987)

Yeh i only heard about ReactOS like a months ago. I like the concept around it but it still needs a lot of work. It installed fine, fast as hell, and boots fine but once in not much works.

Is the location of my custom entry in the right place?

Thanks for those links, will do some reading.

---

### Post by ranch hand on 2009-09-26
> **Slug71 said:**
> I started a thread in General Help but no hits there yet.

[http://ubuntuforums.org/showthread.php?t=1275575](http://ubuntuforums.org/showthread.php?t=1275575)

Also this one..

[http://ubuntuforums.org/showthread.php?t=1269987](http://ubuntuforums.org/showthread.php?t=1269987)

Yeh i only heard about ReactOS like a months ago. I like the concept around it but it still needs a lot of work. It installed fine, fast as hell, and boots fine but once in not much works.

Is the location of my custom entry in the right place?

Thanks for those links, will do some reading.
Great, I would have posted it here.  Yours may be the better choices.  I subscribed to both of them and will be reading them when I get time.  Thanks for the links.

You got the little bugger in the right place.  I am sorry that I did not mention that you need to make it executable but you must have caught that or it wouldn't work.

There is getting to be some documentation that is useful out there.  I hope the links I gave will help but grub2 is still changing so the folks trying to keep up with it are always going to be behind.

I don't use any MS stuff so ReactOS does not interest me.  It is neat what folks put out though.

I want to try BSD, but right now I am trying to get to the point I was at with MS as far as knowing what I am doing in Linux and particularly in Ubuntu.  Then I will try BSD.

I still think that we will come to really like grub2.

---

### Post by Gina on 2009-09-26
Thank you for your reply ranch hand :)  My comment wasn't aimed at you particularly, just a general comment on how things seemed ATM.  It does sound like grub 2 will be better one it's settled down.  I agree that legacy grub does need some tricky fiddling with to get multiple systems in multi-boot each updating correctly when the OS version is updated.

I guess it's that once you get the hang of one thing, a new one looks more complicated even if it isn't really :lolflag:  I'm all for a modular approach just as I was in favour of object orientated programming when that came in all those years ago :)

---

### Post by Slug71 on 2009-09-26
> **ranch hand said:**
> Great, I would have posted it here.  Yours may be the better choices.  I subscribed to both of them and will be reading them when I get time.  Thanks for the links.

You got the little bugger in the right place.  I am sorry that I did not mention that you need to make it executable but you must have caught that or it wouldn't work.

There is getting to be some documentation that is useful out there.  I hope the links I gave will help but grub2 is still changing so the folks trying to keep up with it are always going to be behind.

I don't use any MS stuff so ReactOS does not interest me.  It is neat what folks put out though.

I want to try BSD, but right now I am trying to get to the point I was at with MS as far as knowing what I am doing in Linux and particularly in Ubuntu.  Then I will try BSD.

I still think that we will come to really like grub2.

When i installed the -11 kernel i lost my custom entry.

I redid it and put it above the debian theme this time to see if that works. 

I also changed this

> menuentry "freebsd" {
set root=(hd0,2,a)
freebsd /boot/loader
}

to this

> menuentry "freebsd" {
set root=(hd0,2)
chainloader +1
boot

Can now access PC-BSD! :):)

---

### Post by VMC on 2009-09-26
That's interesting. I didn't know you can chainload BSD's. I thought those "slices" they have wouldn't allow it. When you do chainload the BSD, do you have another boot record on the BSD partition? Or how did you set it up?

---

### Post by ranch hand on 2009-09-26
> **Slug71 said:**
> When i installed the -11 kernel i lost my custom entry.

I redid it and put it above the debian theme this time to see if that works. 

I also changed this



to this



Can now access PC-BSD! :):)
Hey that is great.  I never even think about chain loading, don't like it for some reason, not really sure why not.  It is the way you boot to MS and I don't have that virus.

This really is exciting to me.  Another piece to the grub2 puzzle.

Have you played with the background and font colors in grub2?  That is what the 05_debian-theme file is there for.  Herman has a good guide to that.

---

### Post by prattmd on 2009-09-26
Has anyone had any sucess booting Moblin 2.1 from Grub2?

---

### Post by Slug71 on 2009-09-27
> **ranch hand said:**
> Hey that is great.  I never even think about chain loading, don't like it for some reason, not really sure why not.  It is the way you boot to MS and I don't have that virus.

This really is exciting to me.  Another piece to the grub2 puzzle.

Have you played with the background and font colors in grub2?  That is what the 05_debian-theme file is there for.  Herman has a good guide to that.


I changed the background and font colours back when i was testing it during Jaunty dev but havent with Karmic yet.

---

### Post by Slug71 on 2009-09-27
> **VMC said:**
> That's interesting. I didn't know you can chainload BSD's. I thought those "slices" they have wouldn't allow it. When you do chainload the BSD, do you have another boot record on the BSD partition? Or how did you set it up?

To be honest im not sure how it works or even why. PC-BSD was my second install on this hard drive though. I got a free P4 at our local dump area and all it needed was some RAM and a HDD. Got that on ebay and decided this was gonna be my test box instead of our production laptop. 

Installed ReactOS first and then PC-BSD both on primary partitions and then installed Ubuntu followed by Kubuntu. Did them all back to back. So PC-BSD must still have its loader in the MBR. Would have thought Grub2 would have totally wiped that all though. :confused:

---

