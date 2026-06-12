---
title: "tri boot problem"
date: 2007-12-05
forum: Installation &amp; Upgrades
---

### Post by drudogg on 2007-12-05
i did read some threads about dual and tri booting, but none of them seemed to answer my question. 

i am getting DSL installed next week and wanted to get everything ready ahead of time so that it would be ready to go.

i got ubuntu 7.10 yesterday and reinstalled my whole computer as follows

ubuntu (sda1) 40gb
winxp (sda5) 80gb
vista (sda6) remainder of 500gb sata drive

also have a 100gb ide drive that i unhooked during install and testing that has just data on it (backup).

i have not been using ubuntu for a while, i did play with it about 2 years ago.

anyway i installed xp then vista and got them running with drivers and all.  then i installed ubuntu without grub. and the only boot options i got were vista and xp. so i reloaded ubuntu with grub. i could not figure out where i was supposed to put grub. it would not load to hd0. so i loaded it to /dev/sda1 and it loaded fine and rebooted and then i get only ubuntu.

i am assuming that i put grub in the wrong place.  so where should it go or is my problem somewhere else?  would it be lost if i reloaded vista now?


i also read this: [http://www.howtoforge.com/dual_boot_windows_xp_vista_ubuntu_feisty_p2?](http://www.howtoforge.com/dual_boot_windows_xp_vista_ubuntu_feisty_p2?)  
and other than the extra os i did exactly what the guide says.




for someone looking for help go to post 12, 16, AND ALSO POST 21 HAS IMPORTANT NOTE FOR MULTI HARD DRIVE USERS! in this thread it may help you out!

---

### Post by drudogg on 2007-12-05
does anyone know if i am barking up the wrong tree or is my problem likely caused by something else. i want to use mostly vista at this point because i do not have any internet access under ubuntu until i get my dsl installed. my wireless usb adapter does not work with ubuntu. i need internet access in the meantime. but i can't boot to any windows so i can't get online at home, i am at work hoping for enlightenment. 

the grub locatiion is the only thing i can figure went wrong. but in the install where you are supposed to see the last line of the first little bit of info on the last screen before installation starts does not show the line for vista/longhorn. 

not sure if it is something i did or did not do. i manually created all of the partitions during xp install. and gave the parameteres to each partition in each install.

---

### Post by viking777 on 2007-12-05
I was under the impression that Windows insisted on being  on the first partition of any drive, now I don't actually have any hard evidence of that, but it is how mine is set up and it works fine. 

I think that to get windows back you will have to boot from the cd enter recovery console and run 'fixmbr' which will get windows back but stuff Ubuntu!

I think also that if you put Windows XP, on sda1 (hd0,0), Vista on sda2 and  then reinstall Ubuntu to sda3 it will automatically pick up the fact that windows exists and add it to grub, then it doesn't really matter where you put grub as it will incorporate windows anyway. 

Mind you that seems like an awful lot of work, so if I were you I would wait a bit and see if anybody comes up with an easier solution!

---

### Post by drudogg on 2007-12-05
so you are saying that i should reload all of it with windows on the partitions before ubuntu? i don't mind trying that, if someone else can verify that it should work.

also should grub pick up both installs or will it send me to the vista boot loader for windows in general?

if there is another way hopefiully someone will chime in.

---

### Post by drudogg on 2007-12-05
is there any other posibilities to make grub find windows? 

i would like to learn more about ubuntu, but it would be a lot easier if i could access the internet from it. i am not opposed to abandoning vista, but i work in IT and i want to learn how to use all of the popular OSes. i got vista pretty well under control and XP is a peice of cake. i want to learn some linux and mac. i have tried linux before, but always got discouraged because i could not get internet access with wireless. (i connect to my mom's network next door) so i am buying my own DSL connection. and i thought that now would be a good time to give it another go. but i want to be able to access all of my operating systems.

i would rather reload everything now than wait until i have actually started loading tihngs and setting up settings.  i don't want to give up on ubuntu again as i like what i see, but i need all three operable.

---

### Post by drudogg on 2007-12-05
any other ideas. maybe super grub disk?

---

### Post by confused57 on 2007-12-05
You could try the bootrec.exe utility on the Vista install DVD to restore your mbr:
[http://support.microsoft.com/kb/927392/en-us](http://support.microsoft.com/kb/927392/en-us)

If this enables you to boot into XP & Vista, you might be able to use EasyBCD to boot Ubuntu:
[http://support.microsoft.com/kb/927392/en-us](http://support.microsoft.com/kb/927392/en-us)
note that grub needs to be installed to the root partition for this to work...grub can be installed to the root partition, using the Ubuntu live cd:
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

---

### Post by uidb4056 on 2007-12-05
I'm not shure how to deal with Vista but before reinstall you could check to do this:

Boot Ubuntu and then open a Terminal sesion

run these commands

sudo cp /boot/grub/menu.lst /boot/grub/menu.org

This makes a copy of your menu.lst file.

Now execute

sudo gedit /boot/grub/menu.lst

Now scroll down to the end of the file and add these lines

title  Windows XP
root (hd0,4)
savedefault
makeactive
chainloader +1

Save the file and reboot, then should appear in the grub meno the option to start Windows XP and if it works at least you can work again with internet from it.

I hope that your mistake was not allow to install grub atumatically when you install Ubuntu because in this whay an automatic search for others OS is made ant added automatically to grub menu.

I hope it will help you

---

### Post by drudogg on 2007-12-05
thanks for the help, i will let you guys know if it works!

---

### Post by drudogg on 2007-12-05
okay i got good news and bad news...

i am repling from home in vista... but grub did not get me here.

if i turn on the computer it comes up in ubuntu beutifully in about 30 seconds.
if i put in the vista disk, i get a menu to boot to vista or xp pro... and no option for ubuntu...

does this make sense at all? this is a gateway desktop GM5472 and i have had boot issues with the previous dualboot xp/vista setup. but this is just wierd...

---

### Post by meierfra on 2007-12-05
How did you get windows installed on  a logical partition? (A logical partition is a partition inside a extended partition)

As far as I know where are only two  to accomplish this:

1)  You  had another primary partition, which you deleted. In this case you are in trouble because the deleted partition contained the booting instruction for all your Windows systems.  You could try the convert your Windows partitions to primary ones. But It probably easier to deleted your windows partition, created a primary partition instead and reinstall.

2)  You copied a primary partition to a logical partition. In this case 
try
title Windows XP
root (hd0,4)
chainloader +1

or 

title Vista
root (hd0,5)
chainloader +1

(makeactive does not work on logical partitions.

---

### Post by drudogg on 2007-12-05
i think that you hit the nail on the head meierfra. at least part of it. 

the logical and primary partition was one problem. but i solved another problem.

here is the way to tri boot with WinXP, Vista, and ubuntu 7.10:

step one load Windows XP
while going through the loading process go on and set up all of the partitions you will need.
(Windows XP creates/deletes partitions faster than Vista or ubuntu)


step two install Vista 
it will see the XP load and create a boot manager for the two...

step three test this dual boot system to make sure that it has full functionality.

if so proceed to step four
load ubuntu on thepartition you setup for it and swap on the last partition if you are using a swap, i put 2gb.

When you get to the last step before installation actually starts click the advanced button in the bottom corner and select the location for GRUB to install to.  I put it on /dev/sda i would assume this puts it in the master boot location rather than one of a partition.

as a side note i disconnected my backup internal hard drive so as not to confuse any of the installations. and once i had set everything up i reconnected it and everything worked as it should.  <<<<<<
   [COLOR="blue"]********NOT A SIDE NOTE I FOUND THIS TO BE AN IMPORTANT STEP IN SOME CASES!!!! READ POST #21 FOR MORE INFO!!!*******[/COLOR]

i am not trying to say that i know everything though if someone wants to add to this be my guest. i just hope that this can help someone else!

---

### Post by meierfra on 2007-12-05
```
 windows likes to be on the first partition  this may be true.
```

As far as  I know this is not true. Windows likes to be an a primary partition.   But whether it is the first, second, third   or fourth  primary partition does not seem to matter. There are lots of people on this forum who claim that Windows likes to be an the first partition, but I have not encountered a single case  where Windows not being on the first partition caused a problem. 

But you can see from this case how this rumors spreads. You got advised that Windows likes to be on the first partition. You moved  Windows  to the first partition and solved your problem, confirming the rumor. But  it was only important  that you moved Windows to a primary partition, not that you moved it to the first partition.

---

### Post by meierfra on 2007-12-05
> but i solved another problem.

What was the other problem? 

As far as I see it you need  to:

First install XP on a primary partition. Install Vista next and then Ubuntu. (Actually you can install Ubuntu at any stage, but you would have to spend a few minutes fixing grub at the end)

---

### Post by meierfra on 2007-12-05
> while going through the loading process go on and set up all of the partitions you will need.
(Windows XP creates/deletes partitions faster than Vista or ubuntu)

Not recommended. XP might be faster, but I have seen various cases where Ubuntu could not be installed on a partition created by XP. It worked out for you. But in general it is better to use gparted  to create the Ubuntu partition. Use Vista to resize a Vista's partition and so on.

---

### Post by drudogg on 2007-12-06
the other problem was actually a windows boot problem... the "rumor" may not be that windows needs to be first but that the non-bootloader/oldest version needs to be first, because this is the 5th time that i have reloaded the 2 versijnos of windows on 2 different computers. 

with XP after Vista the computer had issues booting properly between the 2. i got rid of that problem before i even went forward with ubuntu.

i am not actually saying that windows should be first, but that the software that controls the bootloader should be last. because this  is 3 operating systems i did XP first because then vista would pick it up, and ubuntu last because it would pick up the others. 

i don't knoiw how i got the logical and primary mixed up, i originally set up the partitions with ubuntu and it gives options, and XP doesn't. 

for the record i set up the partitions with XP for all 3, but then went back and added the swap 2gb partition at the end while i was loading ubuntu... i took the partitino that i had created for ubuntu and split it with ubuntu's loader. so you may be right that ubuntu is better, maybe not. i am not claiming to know everything, just provide a trial and error scenario with a solution that has been proven to work at least once... that information may help out someone that is less experienced with ubuntu and dual/tri booting. i am not very experienced with ubuntu, and that may be obvious, but i do know about dual boot setups, and computers in general. the problem is that i deal mostly with windows, and want to learn more about what i don't know. hopfully there is someone else out there like me who wants to do this, and could not find any definative way to set this up, and i can possibly help them out. i did search tri booting on this forum and did not find any thread that answered the question. this would have helped me, and the other threads did not have an answer, i did read them and some dual boot info as well.

thanks for you guys that have helped me, and hopfully i have helped somebody else!

---

### Post by meierfra on 2007-12-06
I'm not disputing that XP needs to be installed (timewise) before  Vista. That is, just as you said,  necessary so that the Vista boot loader can detect XP (XP is not able to detect Vista correctly)  I'm only disputing that it needs to be on first partition. So in my opinion you can triple boot as follows:

Step 1) Install XP to sda3

Step 2) Install Vista to sda2

Step 3) Install Ubuntu to sda1.


I'm surprised that you couldn't  find any good advice on how to triple boot. XP first, Vista second, Ubuntu third is the standard installation recommendation.

---

### Post by wazzup on 2007-12-06
Why make a dual/triple-boot system... why not install windows (or ubuntu) in a virtual machine and get everything at once ? (at least that is my intention once I get my new pc). Sure you lose a couple procent overhead and direct access to exotic hardware, but do you really need that ?

you can get vmware-server for free these days.

---

### Post by MQMike on 2007-12-06
Follow what meierfra advises.


Otherwise, the best guide I see  out there is:

Vista   ***   The definitive dual-booting guide: Linux, Vista and XP step-by-step
[http://apcmag.com/dualboot](http://apcmag.com/dualboot)

---

### Post by drudogg on 2007-12-06
well in my case i installed xp timewise before vista, but on a later partition and had boot issues, either i did not see xp at all or i had to boot from a cd to get to it. i reversed this and put xp first and vista second timewise and partitioning and it worked flawlessly, upon multiple boots and reboots for testing. 

it could be something to do with the bios/motherboard from gateway in my case, but what does it really hurt to put one first and another afterward, the end result gives them botht the space you wanted and it works does not matter to me wnat parttion it is on, but it happened to matter to the computer.

i think that the stacking of the different OSes gave the latterones more control with regards to the bootloaders themselves. i could be wrong, but in this case that was the variable (in my windows setup at least) i put ubuntu on the first partition the first time, and the last the second time, but as you pointed out there was a partition type problem so that is inconclusive. but for windows this seems to make sense. it did not hurt ubuntu so i am happy.

as to why to dual/tri boot it is easier with other installations of software and hardware down the line to be running in a native environment rather than virtually through another.

---

### Post by drudogg on 2007-12-13
> **drudogg said:**
> 
as a side note i disconnected my backup internal hard drive so as not to confuse any of the installations. and once i had set evrything up i reconnected it and everything worked as it should.



i would like to  add that this proved to be an actual important step in the boot loader for both windows installs, ubuntu did not care because i told it where to install grub myself.

the reason is that my primary (booting) drive is sata and my backup drive is ide and the bios in my computer puts the ide drives as a primary channel to the sata ones.  so even though i was loading all of the OSes on the sata drive the bootloader for xp and vista was putting itself on the ide drive, and that was causing a conflict in the boot process at least for windows. i would say that this could be a reason that some people only see ubuntu when trying to multiboot.

so this may be the important step in this setup... i found this because my windows xp setup got messed up, (a file got corrupted) and i tried to reinstall it, but did not unhook the ide drive and all hell broke loose and i had to redo the whole thing again. so after 2 installs i would say that the major factor in this whole thing was the bootloader conflict with the drives.



i apologize for previous informations that may have been wrong but this seems to be the real problem after multiple tests.


i would like to say that the partition location is most likely irrelevent as was prevoiusly stated above.

---

### Post by MQMike on 2007-12-13
@ drudogg, Post #21:

I hear what you say, and I've read similar accounts before, and I understand the issue you describe, and its subtleties.  Given all that, when your PC boots up, BIOS (& therefore GRUB) gets the drive right.  It may not be what's in device.map, but that's because (1) device.map is used only by the grub shell (the emulator run inside Ubuntu from a command line—Chapter 15 of the GRUB manual); and (2) At boot time, GRUB (the native GRUB that you see when the PC boots) doesn't look at device.map. 
At boot time, what counts is what BIOS (& thus, GRUB) sees as your drives.  So, before installing an OS, if you investigate your drives from a (native) GRUB prompt, grub>, using, say the geometry command,
grub > geometry (hdx), x = 0, 1, 2, ...
that will tell you what drive is which and where the  OSs are.
Then use this information during the installation of Ubuntu to specify where GRUB is to be installed, using the GRUB notation (hdx,y).
No need to disconnect drives.
My 3 cents worth, and I respect that YMMV, but I may not understand exactly why . . . :)

---

### Post by drudogg on 2007-12-13
being that i am not that smart, and that will only work for the grub info, i have to say that disconnecting an ide drive when installing everything to a sata may be the way to go... 

i can only believe that the installers were loading to the MBR of the "extra" drive because it was IDE and it viewed the IDE as the PRIMARY interface. i guess that if there was no IDE drive in there then i would not have had a problem... but part of the problem was from the windows side because it was where the conflicts began. i had this issue before ever thinking about ubuntu.

---

### Post by bwanaaa on 2007-12-15
I have the same problem-
-partitioned my hd into 3 partitions using xp
-first partition left raw,middle partition ntfs, third partition ntfs
-put xp on the middle partition, 
-confirmed it worked

-rebooted using a vista64 install dvd, installed vista64 to the third partition
-confirmed both partitions worked

-installed ubuntu on the first partition using the option in the partition manager of ubuntu to install into the largest free space (this happens to be the first  partition)

->ubuntu boots fine.ran this (sudo gedit /boot/grub/menu.lst) in terminal and added

title            Vista
root             (hd0,2) 
chainloader      +1


->tried to reboot into vista and get the 'bootmgr is missing' message.
-> my directory structure in gparted looks like this:
/dev/sda1     'lock icon'               ext3
/dev/sda2     'lock icon'               extended
/dev/sda6     'lock icon'               linux-swap
/dev/sda5     'caution triangle'      ntfs
/dev/sda3     'caution triangle'      ntfs

/dev/sda2  is preceded by a triangle and the two entries under (/dev/sda6   and /dev/sda5) it are indented

-the xp install is on /dev/sda5
-the vista install is on /dev/sda3  


I FIXED this problem in the following way:
-boot from vista dvd and select repair-the computer then finds the old vista install, and then reboots
-boot from vista dvd and select repair AGAIN-it asks what kind of problem and i choose a startup problem- then the boot manager is fixed
-reboot and allow grub to come up-select vista and it works.

---

### Post by bwanaaa on 2007-12-15
why do my ntfs partitions have yellow caution triangles?

---

