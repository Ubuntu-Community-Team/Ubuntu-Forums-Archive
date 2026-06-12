---
title: "Xubuntu and XP Pro Dual Boot Problems."
date: 2006-08-05
forum: Installation &amp; Upgrades
---

### Post by A2A on 2006-08-05
Hi all, after trying out Ubuntu on my desktop for a month as a sole OS, I decided to take the leap and install Xubuntu on my laptop.  The laptop is currently running XP Pro SP2 on a NTFS partition.  I d/loaded the Xubuntu i386 desktop CD, checked MD5 sums, burnt the ISO, and then rechecked the CD using the tool provided within the CD.  All checks passed.  

I then changed BIOS to boot from CD-ROM and went ahead with the install by clicking on the "install" icon via the Live CD desktop.  Installation went fine, and I manually created a partition (5GB ext3) to mount Xubuntu on.  A 1024MB swap partition was also created, and about 3GB was left as unused space on the drive.  The NTFS partition (6GB) hosting XP Pro was left intact.  

At the end of the installation, I was prompted to remove the CD and reboot.  Unfortunately, I do not get any option to "select" which OS I want to boot into, and the laptop boots into XP-Pro and allows me to log in etc.  I do not see the Xubuntu partition from "My Computer" once logged into XP.

During the end of the installation, I saw something about GRUB, but the installer never paused and asked for any kind of input from me, so I assumed the dual boot options would be set automatically.  I don't know where I went wrong?

The laptop is a Toshiba Satellite 1800, PIII 1GHz, 512 MB RAM (16MB shared for Video) and a 20GB HDD.  I do have a working floppy drive available on this machine as well.

Any help to resolve this issue and enable me to have a dual boot laptop would be much appreciated.

Regards,

A2A

---

### Post by Herman on 2006-08-05
> At the end of the installation, I was prompted to remove the CD and reboot. Unfortunately, I do not get any option to "select" which OS I want to boot into, and the laptop boots into XP-Pro and allows me to log in etc. I do not see the Xubuntu partition from "My Computer" once logged into XP.
During the end of the installation, I saw something about GRUB, but the installer never paused and asked for any kind of input from me, so I assumed the dual boot options would be set automatically. I don't know where I went wrong? A2A, I am fairly sure that the installer in the 'Desktop' Live/Install CDs just installs Grub to MBR without requiring any input from the user. In your case for some reason, the MBR has not been successfully over-written. 

Sometimes in a computer with more than one hard disk, Grub gets written to the MBR on the second hard disk rather than the first. The BIOS doesn't look on the second hard disk, (unless you do something else special to induce it to). Grub can be installed correctly to the first hard disk's MBR from the Live CD later. [Re-install Grub with the Live CD]("http://users.bigpond.net.au/hermanzone/p15.htm#Re-install_Grub_with_Live_CD") But you didn't mention having more than one hard disk, so that might not be your problem.

Another thing that happens sometimes is that some BIOS's have an MBR protection or a boot sector anti-virus of some kind running that can block anything trying to write to your MBR. It's to prevent 'boot sector' viruses. You could  look through your BIOS for something like that and turn it off until you install Grub to MBR, you can turn it on again later if you want.
You can use the Live CD for that too, [Re-install Grub with the Live CD]("http://users.bigpond.net.au/hermanzone/p15.htm#Re-install_Grub_with_Live_CD")

I presume you don't have the 'Alternate' Install CD, but if you do, you can also re-install Grub with that one,                  [Re-install GRUB with Alternate CD in Rescue mode]("http://users.bigpond.net.au/hermanzone/p15.htm#reinstallgrub").

Maybe just try re-installing GRUB by either of those two methods, and checking your BIOS for MBR write-protect features would be the best place to start. If that doesn't work, post back here again for more ideas.
If there is anything in those links about re-installing Grub that needs clarifying, please don't hesitate to ask, all questions are welcome, Regards, Herman :D

---

### Post by A2A on 2006-08-05
Herman, thanks for the detailed response.  You guessed correct, there is only one HDD in the machine.  Your suggestion about the BIOS having some kind of lock on it to protect MBR sounds valid.  I will give that a shot  (once i figure out how to actually be able to enter the BIOS and make changes...googling now).  Hitting F12 during a bootup just gives me options to select the booting order... :-(

Will keep you guys posted on the progress.

A2A

P.S:  Is it possible that grub got written to the swap partition??  Just a thought, I thought I'd get that clarified by someone who knows.

---

### Post by Herman on 2006-08-05
> P.S: Is it possible that grub got written to the swap partition?? Just a thought, I thought I'd get that clarified by someone who knows. All bootloaders come in two or three pieces.

Windows bootloader has two main parts, the part in the MBR is very small, only 446 bytes and it's really just a 'pointer'. It uses the other part of the MBR, the 64 byte partition table to point the BIOS in the right direction to find the operating system partition with the larger (functional) part of the bootloader on it. (Stage 2 of NTLDR).

When we 'install Grub to MBR', we are really one installing the 'first stage' of Grub to MBR, the 446 byte 'IPL' or pointer. This just makes the MBR point to the Ubuntu partition where the larger part (Stage2) of Grub lives. The larger, main workings of Grub load the Linux kernel to boot Ubuntu, or, if we select Windows, points the BIOS back to Windows and chainloads (passes responsibility to), the Windows bootloader. 

Grub also has a stage 1.5, that lives in the next 15 sectors of the first track of the first hard disk after the MBR.  The first track of a hard disk is normally empty except for a few special programs like boot loaders and boot managers and the like. It is not formatted with any filesystem, so it is not part of any operating system's partition. The first partition does not begin until sector 63.

I have never tried installing Grub to a swap area. It sounds like an interesting thing to try and see what error messages come up. :D 
I think it would be a very difficult thing to do. Maybe it's possible but I think it would require a conscious effort ny someone who knows what they are doing and/or is a little crazy (like me) :D

Anyway, since I'm here, I was still thinking over your problem, and I dug out my old 'super grub disk' from under a pile of CDs I have here and gave it a run. If you have too much trouble re-installing Grub, you can always use a 'super grub disk' to boot Xubuntu with.

Super Grub Disk.......................................................................................[GO]("http://adrian15.raulete.net/grub/tiki-index.php")

The 'super grub disk' has been improved a lot probably, since the old version I have. Even the old version I have isn't too hard to figure out after a little bit of trial and error. If you aren't afraid of the command line though, the fastest way to use the 'super grub disk', is to boot it and don't bother with any of the fancy stuuf, just press 'c' right away for a command line.
I made some Grub Command line help info on a web page, 
**Grub's Command Line Interface** .................................................................................................[GO]("http://users.bigpond.net.au/hermanzone/p15.htm#cli")

Even if you have never used a command line before, I hope you'll be able to figure that out given that info and a little time.
That will definitely boot Xubuntu for you, or for that matter, any operating system that is bootable in any computer.
You will probably still want a more convenient booting method, but that will get your operating system going to begin with, until we can rig something more permanent. Maybe Super Grub Disk will be an easy way to do that too, there are a lot of interesting looking functions even on my ancient old version. I'm off to download the latest Super Grub Disk and burn it to a CD-RW and play with it some more....
Regards, herman :D

---

### Post by Herman on 2006-08-05
> I will give that a shot  (once i figure out how to actually be able to enter the BIOS and make changes.. Oh, yeah, I forgot about that part... 
Maybe just try hoovering one of your fingers over the 'pause' key and get ready to  hit  'pause' as soon as your computer begins to boot up.  After reading the first screen, press 'enter', and as soon as another screen loads, press 'pause' again and continuse alternating between those two keys until you get to where it has some instructions about how to enter the BIOS.

Inside the BIOS, just be carefull, but there are pretty good instructions in there in most BIOS's that are easy to understand. If you aren't accustomed to poking around in there it's okay, it will get easier with a little practice.
Here' are a coupe of my favorite links about the BIOS, 
[RIGHT][BIOS (Basic Input / Output System)]("http://webpages.charter.net/netw_1/bios.htm")[/RIGHT]
 
[RIGHT][The Definitive BIOS Optimisation Guide]("http://www.adriansrojakpot.com/Speed_Demonz/BIOS_Guide/BIOS_Guide_Index.htm")[URL="http://www.adriansrojakpot.com/Speed_Demonz/BIOS_Guide_Index.htm"]
[/URL][/RIGHT]
 Regards, Herman :D

---

### Post by A2A on 2006-08-05
Hi Herman, Thanks for all your help so far.  Here is my HDD breakup:
> 
ubuntu@ubuntu:~$ sudo grub
Probing devices to guess BIOS drives. This may take a long time.
ubuntu@ubuntu:~$ sudo fdisk -lu

Disk /dev/hda: 20.0 GB, 20003880960 bytes
255 heads, 63 sectors/track, 2432 cylinders, total 39070080 sectors
Units = sectors of 1 * 512 = 512 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *          63    12289724     6144831    7  HPFS/NTFS
/dev/hda2        12289725    26667899     7189087+   f  W95 Ext'd (LBA)
/dev/hda5        12289788    14394239     1052226   82  Linux swap / Solaris
/dev/hda6        14394303    26667899     6136798+  83  Linux
ubuntu@ubuntu:~$
 I tried re-installing grub as per your instructions on your website but was not successful.  I couldn't get past the first part once I did a "sudo grub". Here is the output I got:
> 
grub> find /boot/grub/stage1

Error 15: File not found

grub>

 
I also checked the BIOS settings, and there is nothing that seems to prevent/protect the MBR as you suggested in an earlier post.  
One more thing, when I boot up with the live CD, and open a terminal, the default user is "ubuntu".  As of yet I have not been aboe to login to my Xubuntu system using the user ID I created :-(
Awaiting help anxiously,

A2A

---

### Post by Herman on 2006-08-05
A2A, that is very strange if you did a 'sudo grub' and then 'find /grub/boot/menu.lst and it returned 'file not found'. 
The next logical (to me) step would be to use the Live CD version of Ubuntu and mount the new filesystem (Ubuntu operating system) and take a look and see what is there.

If you can 'mount' your new filesystem according to the following how-to,
        Mount a Ubuntu ext3 or reiserfs filesystem in the Ubuntu 'Desktop' Live/Install CD...........[GO]("http://users.bigpond.net.au/hermanzone/p10.htm#Mounting_Ubuntu_with_Dapper_Desktop_LiveCD") , you should see all your Ubuntu files when you open your /media/ubuntu folder. They should look like this; [Click Here]("http://users.bigpond.net.au/hermanzone/p15.htm#oreintation"), see fig 4 and fig 5 grub page. 

Even if you only have (referring to fig 5 grub) [LIST]
[*]a Linux kernel (it looks like a page with a 'footprint' (Gnome) icon on it, and it will be named vmlinuz (followed by a series of numbers).[/LIST][LIST]
[*]and an initrd.img[/LIST]you can boot Ubuntu with a Super Grub disk (for now until we figure out what;s wrong and how to fix it.)

It is normal for us to have a 'ubuntu@ubuntu~:$ prompt when using the Live CD operating system. You will have your own computername and username when you use your terminal in the hard disk installed system though.

Thank you for including your sudo fdisk output. I have analysed that and it looks 'A- OK', everything *should* work. 

Thanks for sticking with it, Regards, Herman :D

---

### Post by A2A on 2006-08-06
Hi Herman.  Aoplogies for the delay in getting back to you, juggling work and  sleep.  Thanks for all the help provided so far, really makes me feel that with your help (and maybe someone else's from this forum, I will be able to fix my problems).
I did d/load the CD version of Super Grub Disk.  Before I ran that, I mounted the installation partition to the Live CD using the amazing tips on your website.  All went smooth, BUT, when I use the File Manager to view the files in the Boot directory.  There are 6 files there and no Grub girectory.  The names of the files in the Boot directory are:

System.map-2.6.15-23-386 (txt file)
abi-2.6.15-23-386 (txt file)
config-2.6.15-23-386 (txt file)
initrd.img-2.6.15-23-386 (file with a pic of an "open box" in the icon)
memtest86+.bin (file with a "foot" in the icon)
vmlinuz-2.6.15-23-386 (file with a "foot" in the icon)

After this I rebooted the laptop, and tried booting with the Super Grub Disk.  After booting, I tried to mount the partition hosting Linux, but nothing really happened, and I was pretty confused as I couldnt find any directions on how to use that program.  Not much resources available online once I googled it.

Hope you (or someone) has some suggestions for me to try next.

Regards,

A2A

---

### Post by Herman on 2006-08-07
> There are 6 files there and no Grub girectory. No /boot/grub eh?                 Ok, no problem.  :D

My plan is first to boot Ubuntu with Super Grub Disk, and then install GRUB from the internet with 'Synaptic Package Manager'.

Super Grub Disk has an 'Restore Grub in Hard Disk' option, but it won't likely be of any use to us in this particular case.

The way I would like you to use the Super Grub Disk is as follows.[LIST=1]
[*]Boot with the Super Grub Disk in your CD drive
[*]A language selection screen comes up, select English
[*]Some white print on a black background will appear. You can read it if you want, and press 'Enter' to move on to more text two or three times, then you will get a nice menu in a blue panel on a black background. It has several options you can choose from. Ignore all those options and press your 'c' key for a command line. (It says you can do that in the text underneath the menu).
[*]You should be given a black background with white text on it and below that, a grub>_ prompt.
[*]After the grub prompt, type 'root (hd0,5), please be sure to leave spaces where I leave spaces and use the exact spelling and any symbols as I do too. For example, ```
grub> root (hd0,5)
``` If you did that successfully, you should get some feedback about what filesystem grub found on that partition.
[*]After the grub prompt, type 'kernel /vmlinuz root=/dev/hda6' for example, ```
grub> kernel /vmlinuz root=/dev/hda6
``` You should get smoe feedback like '[Linux-bzImage, setup=0x1c100, size=0x15774d], or something similar.
[*]After the grub prompt, type 'initrd /boot/ini', and then press your 'Tab' key. The 'Tab' key will tell grub to complete the rest of the filename for us for your particular initrd image. Actually, we already knw that yours is  initrd.img-2.6.15-23-386, but normally we don't already know that and we need to use the 'Tab Completion' trick to find out for us. It's easier anyway. For example, ```
grub> initrd /boot/ initrd.img-2.6.15-23-386
``` That should return some feedback too, not unlike what you saw for the kernel command.
[*]After the grub prompt, type 'boot'. For example, ```
grub> boot
```. It will say 'uncompressing Linux... OK booting the kernel', but you will have to be quick to read that. Lots of white test on a black background will scroll on your monitor, and... Ubuntu will boot. :D[/LIST]For illustrations of how to do this and more with a GRUB Command Line, [click here]("http://users.bigpond.net.au/hermanzone/p15.htm#cli").

That will do for one post, I'll do another one about how to find Grub in Synaptic.

---

### Post by A2A on 2006-08-07
Herman, I don't know how to thank you enough for your patience and determination to get my laptop computer up and running.  

I just got home from work, and am going to try the instructions you posted in the response above.  Will keep you posted on the progress.

Once again, THANK YOU!

A2A

---

### Post by A2A on 2006-08-07
Hello again Herman.

Got Xubuntu to boot!  Yay, im so excited :-)  Will await instructions on how to add grub via Synaptic Package Manager.

Regards,

A2A

---

### Post by Herman on 2006-08-07
A2A, That's great!
Sorry for the slow reply, I'm juggling work and sleep too, but right now I'm almost late for work.
You should be able to find grub in Synaptic Package Manager, ('System'->'Administration'->'Synaptic'). Once Synaptic is open, you can try just clicking 'edit', and on the edit menu, 'fix broken packages'.  Sometimes that helps.

You can also click the 'reload' button and wait a minute or two.
Then press the 'mark all upgrades' button and wait.
Then press the 'Apply' button to update your system and wait while the updates are installed. That might fix it too.

Just try up to there first, because I need more time to do some experiments here on a test  install to make sure the instructions I want to give you will be safe.
Sorry, but I have to leave right now in a hurry, bye for now, Herman :D

---

### Post by A2A on 2006-08-07
Hi Herman,  Thanks for taking the time to respond.  
I did a edit -> fix broken packages, and there was no improvement  when I rebooted (XP booted up, no choice to choose OS).

So I rebooted with Super Grub Disk, and this time loaded Synaptic, after reloading the list and marking upgrades, I let it rip.   It downloaded 193 updates/addons and then rebooted.  Still goes to XP by default.  

So once again I tried to boot from Super Grub Disk, this time though, there are some "fails" listed in the list that scrolls by with a bunch of "OK's" in it.  Then the computer shuts off by itself :-(
XP still boots and works normally, so no harm done :-)

Please advise if there is still hope, or should I reinstall the Xubuntu CD again.

Thanks once more.  And no worries about the late replies, I totally understand that work and personal life comes first and I know that you have already done so much to help me out.  I almost feel like im being a big trouble...

Regards,

A2A

---

### Post by randell6564 on 2006-08-07
> **A2A said:**
> Hi all, after trying out Ubuntu on my desktop for a month as a sole OS, I decided to take the leap and install Xubuntu on my laptop.  The laptop is currently running XP Pro SP2 on a NTFS partition.  I d/loaded the Xubuntu i386 desktop CD, checked MD5 sums, burnt the ISO, and then rechecked the CD using the tool provided within the CD.  All checks passed.  

I then changed BIOS to boot from CD-ROM and went ahead with the install by clicking on the "install" icon via the Live CD desktop.  Installation went fine, and I manually created a partition (5GB ext3) to mount Xubuntu on.  A 1024MB swap partition was also created, and about 3GB was left as unused space on the drive.  The NTFS partition (6GB) hosting XP Pro was left intact.  

At the end of the installation, I was prompted to remove the CD and reboot.  Unfortunately, I do not get any option to "select" which OS I want to boot into, and the laptop boots into XP-Pro and allows me to log in etc.  I do not see the Xubuntu partition from "My Computer" once logged into XP.

During the end of the installation, I saw something about GRUB, but the installer never paused and asked for any kind of input from me, so I assumed the dual boot options would be set automatically.  I don't know where I went wrong?

The laptop is a Toshiba Satellite 1800, PIII 1GHz, 512 MB RAM (16MB shared for Video) and a 20GB HDD.  I do have a working floppy drive available on this machine as well.

Any help to resolve this issue and enable me to have a dual boot laptop would be much appreciated.

Regards,

A2A

Thats wierd! I dual-booted at one time, XP/ubuntu and I was given Grub options. I even tested xubuntu at one time and if I recall correctly, the install was just like ubuntu!

It should inform you that it has noticed a windows OS and something about if you are sure that this is the only other OS on your box, it should be safe to install Grub onto the MBR.  This all took place on a desktop though. I dont know if there would really be any significant difference.

---

### Post by Cariboo1938 on 2006-08-07
> **Herman said:**
>   But you didn't mention having more than one hard disk, so that might not be your problem.:D
Hello Herman, if you don't mind I want to join in. 
I do have [COLOR="Blue"]2 seperate hard drives[/COLOR]. I do have Ubuntu 6.06 for [COLOR="Blue"]64-bit PC[/COLOR] on one hd and [COLOR="Blue"]WindowXP[/COLOR] on the other hd installed. The hds are SATA hds and Ubuntu is on sda and Windows is on sdb. This is what "fdisk -l" tells me. Right now I disconnect either sda or sdb by disconnecting the cable from the motherboard to run either Linux or Windows. This is not very elegant and I want to install a boot loader. Causes this configuration any foreseeable problems? How do I proceed?
When I open the GRUB window during the boot, I only see several Linux kernels listed but nothing from Windows?
Look forward to hear from you
Juergen

---

### Post by confused57 on 2006-08-07
> **Cariboo1938 said:**
> Hello Herman, if you don't mind I want to join in. 
I do have [COLOR="Blue"]2 seperate hard drives[/COLOR]. I do have Ubuntu 6.06 for [COLOR="Blue"]64-bit PC[/COLOR] on one hd and [COLOR="Blue"]WindowXP[/COLOR] on the other hd installed. The hds are SATA hds and Ubuntu is on sda and Windows is on sdb. This is what "fdisk -l" tells me. Right now I disconnect either sda or sdb by disconnecting the cable from the motherboard to run either Linux or Windows. This is not very elegant and I want to install a boot loader. Causes this configuration any foreseeable problems? How do I proceed?
When I open the GRUB window during the boot, I only see several Linux kernels listed but nothing from Windows?
Look forward to hear from you
Juergen

Might be something here that would work for you:
[http://www.ubuntuforums.org/showthread.php?t=179902](http://www.ubuntuforums.org/showthread.php?t=179902)

In your case, all you should need to do is add the Windows entry in your /boot/grub/menu.lst.

---

### Post by Cariboo1938 on 2006-08-08
> **confused57 said:**
> In your case, all you should need to do is add the Windows entry in your /boot/grub/menu.lst.Your suggestion here is:
-------
title              Windows XP
root               (hd1,0)
savedefault
makeactive
map                (hd0) (hd1)
map                (hd1) (hd0)
chainloader        +1
-------
Ok, I get the picture. My only concern is how to call the drives. In my case I have two SATA hard drives, so this would mean I have to replace hd1 by sdb1 for the Windows drive and hd0 by sda1. This is how it's called in the partition table 
PARTITION TABLE
Linux
Disk /dev/sda: 81.9 GB, 81964302336 bytes
255 heads, 63 sectors/track, 9964 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
   Device Boot Start  End    Blocks    Id    System
/dev/sda1  *  1    64       514048+     83     Linux   /boot
/dev/sda2   65    191      1020127+    83     Linux    / 
/dev/sda3  192    1466     10241437+   83     Linux    /Data
/dev/sda4  1467   9964     68260185     5     Extended
/dev/sda5  1467   5291     30724281    83     Linux    /home
/dev/sda6  5292   7840     20474811    83     Linux    /usr
/dev/sda7  7841   9752     15358108+   83     Linux    /var 
/dev/sda8  9753   9964      1702858+   82     Linux     swap  

Windows XP
Disk /dev/sdb: 122.9 GB, 122941242880 bytes
255 heads, 63 sectors/track, 14946 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
   Device Boot      Start         End      Blocks      Id     System
/dev/sdb1   *           1         2550    20482843+    7    HPFS/NTFS
/dev/sdb2            2551        14946    99570870     7   HPFS/NTFS

Before I mess up I would like to know if this could work? 
I'm certainly very thankfull if you could have a look at it!
Thanks in advance
Juergen

---

### Post by A2A on 2006-08-08
Hi folks,  it's always great to see people so willing to help each other.  That's what makes this a super community.  It is also one of the reasons I chose to install Xubuntu to my laptop as a second option to XP.  
In regards to my dual boot issues, as of my last post:
>  I did a edit -> fix broken packages, and there was no improvement  when I rebooted (XP booted up, no choice to choose OS).

So I rebooted with Super Grub Disk, and this time loaded Synaptic, after reloading the list and marking upgrades, I let it rip. It downloaded 193 updates/addons and then rebooted. Still goes to XP by default. 

So once again I tried to boot from Super Grub Disk, this time though, there are some "fails" listed in the list that scrolls by with a bunch of "OK's" in it. Then the computer shuts off by itself :sad:
XP still boots and works normally, so no harm done :smile: 
Out of curiosity, I decided to d/load the alternate i386 CD as well.  After checking md5sums, and burning the iso to disk, I began the process of trying to install it.  This installation was different to the one I had with the Desktop version of Xubuntu.  I took a deep breath and plunged head first in to the install, not knowing what to expect.  Things went fine, and it finally asked me to configure grub.  It recognized my XP install and asked me if I wanted a dual boot setup.  I almost screamed in joy as I confirmed to the installer "YES!" lol.    After wrapping up, it asked me to remove the CD and reboot.  My Toshiba Satellite 1800 will NOT reboot when linux asks it to. I read on the tester/developer page somewhere that other users with similar machines have the same issues related to rebooting.  
Anyways, I force rebooted (power on/off) and for the first time ever I saw what a grub menu looks for, I selected my Xubuntu OS and pressed enter!  In a couple seconds, I got a nice Xubuntu login window, and I must admit the moment was almost orgasmic!  <grin>
I'm sitting here typing this post from my Xubuntu laptop now.  Will try to do a synaptic update in a few minutes and hopefully it doesn't crash my installation like it did last time.  Will keep you all posted on the results.  

P.S:  Herman, thanks for supporting me all the way.  I'm sure, my Xubuntu/Ubuntu woes are not over yet.  Will keep you posted on my learning experience :-)

---

### Post by Herman on 2006-08-08
A2A, I'm sorry to read of your bad luck with the update, but I'm happy that you succeeded in getting a perfect install in the end. 
I thought it would be a good idea to begin with an update because one time a while back I was doing some experiments to find out which files in the /boot directory could be removed without making the system unbootable. I removed all but the kernel and the initrd.img file and could still boot from a command line and the operating system still worked alright as far as I could tell. Then, after an update, I found, much to my surprise, all of the deleted files replaced. So sometimes that can fix it, but perhaps I was just lucky that particular time, and perhaps grub just happened to be one of the items in the list of updates that time maybe. Well, it's usually a good thing to get all our updates anyway, but not this time in your case. Perhaps there was something else missing in there as well that we wouldn't have been able to detect and that the update didn't agree with. Maybe it's the best thing for that to have happened sooner rather than later. 

The plan I was working to this time was to do download Grub from Synaptic just to make sure the rest of it is complete. However, testings in my own computer did not result in a new grub directory being made in /boot. We would have had to make our own. ```
sudo mkdir /boot/grub
```,That would have given you a new grub directory, and then ```
sudo grub-install /dev/hda
``` , That would have installed Grub to MBR, and given you all the files that go inside the /boot/grub directory except menu.lst. So you would still have to boot from the command line. We would have had to make our own menu.lst file so you can have a nice Grub menu, and be able to choose which operating system to boot. I was planning to do that by copying my sample one off my grub page, and modifying it to suit your system. I just needed to prove that all this would definitely work okay first, but a few other things delayed me. Sorry for being so slow.

Anyhow, congratulations, and I'm happy you have a good system now. Happy Xubuntuing! 
Regards, Herman :D

---

### Post by A2A on 2006-08-08
Thank You Herman.  I really appreciate all that you have done to make my experience with Ubuntu/Xubuntu worthwhile.  You have a very high skill level with linux, and maintain a very well detailed personal website with tons of answers and step by step tips.  

Thanks once again for all your help.

Regards,

A2A

P.S:  I noticed some other person who asked for your help in the thread I started.  I have no issues whatsoever, if you and them (and others) continue to post to a thread I started.

---

### Post by Herman on 2006-08-08
Cariboo1938, That looks okay to me. :D

confused57 is about the best around here for advice on booting with more than one hard disk.

You might also find [Super Grub Disk]("http://adrian15.raulete.net/grub/tiki-index.php") handy. It has options for booting Windows, and for doing all kinds of things with multiple disks and partitions.
The 'Boot Windows', 'Special Boot', and 'Classic Boot' menus that are offered from Super Grub's main menu might help you. If you have a Super Grub Disk, then you will be able to experiment with your /boot/grub/menu.lst and not be afraid. If you make any mistake, you will still be able to boot with Super Grub Disk to fix it.

Regards, Herman :D

---

### Post by confused57 on 2006-08-08
> **Herman said:**
> Cariboo1938, That looks okay to me. :D

confused57 is about the best around here for advice on booting with more than one hard disk.

You might also find [Super Grub Disk]("http://adrian15.raulete.net/grub/tiki-index.php") handy. It has options for booting Windows, and for doing all kinds of things with multiple disks and partitions.
The 'Boot Windows', 'Special Boot', and 'Classic Boot' menus that are offered from Super Grub's main menu might help you. If you have a Super Grub Disk, then you will be able to experiment with your /boot/grub/menu.lst and not be afraid. If you make any mistake, you will still be able to boot with Super Grub Disk to fix it.

Regards, Herman :D
Herman, thanks for the endorsement, the "HowTo" that I wrote up is based on personal experience and expert guidance from others.

The grub Windows entry "should" work & there's almost no way to mess up someone's system by just adding it...can always be removed.  Might want to add it to the very end of the menu.lst, if Ubuntu is the desired default OS.
sda & hda are both designated hd0 in grub...some people have had problems with SATA drives & grub, possibly because of certain SATA controller drivers in linux
Super Grub Disk sounds like an excellent recovery tool to fall back on.

---

### Post by Cariboo1938 on 2006-08-08
> **Herman said:**
> Cariboo1938, That looks okay to me. :D
.....You might also find [Super Grub Disk]("http://adrian15.raulete.net/grub/tiki-index.php") handy. It has options for booting Windows, and for doing all kinds of things with multiple disks and partitions....... 
Regards, Herman :DThank you herman...
Sorry for beeing such a greenhorn in Linux.....
[COLOR="Blue"]** ???so replace hd0 with sda1 and hd1 with sdb1 in the grub menu.lst would be ok??? **[/COLOR]
Now I have sgd_0.9428.iso.bz2 sitting on my desktop and don't know what to do with it. 
[COLOR="Magenta"]I know now: open the downloaded *.bz2 file, extract it to the Desktop and get *.iso file, burn it to a CD and get Super Grub CD! That easy![/COLOR]
the next step would be to edit the /grub/menu.lst, right? 
[COLOR="Blue"](for this I need to know what to call the boot partitions, hd0/hd1 or sda/sdb?)[/COLOR]
And then boot from the SuperBootCD, right? 

 
Thank you for your support and patience!!
Greetings
Juergen

---

### Post by Herman on 2006-08-08
In Ubuntu lots of things are much easier than people might expect if they aren't used to it. 
All I do for a Super Grub Disk is download the sgd_0.9428.iso.bz2 or one of the other similar files, and then right-click on it and click 'extract here' from the right-click menu.
That will give me an .iso file called sgd_0.9428.iso
Then I put a CD-RW in the CD drive and wait a minute... ignore or close any automatic windows the might come up asking what I want to do with the CD.
Then I right-click the sgd_0.9428.iso file and click 'write to disk'. 
You can use a CD-ROM or a CD-RW. I prefer to use CD-RW disks for software just so I can use the disk again when a newer version of the software comes out.
If you use CD-RWs like I do, you don't even need to erase them first when you use them in Ubuntu. Just click 'write to disk' on the file and Ubuntu will notice if there is something written on the disk and will let you know and offer to erase it for you or let you know to try a different CD-RW.
Then you will have a Super Grub Disk.

Confused57's howto and advice is quite safe.

I just think the Super Grub Disk is a good thing. It's the best thing I've found yet to help people with booting problems, and it should be in everyone's software CD collection even if they may never need to use it.

All the best, Rgeards, Herman :D

---

### Post by Cariboo1938 on 2006-08-08
> **Herman said:**
> In Ubuntu lots of things are much easier than people might expect if they aren't used to it. 
 
Confused57's howto and advice is quite safe.

I just think the Super Grub Disk is a good thing. It's the best thing I've found yet to help people with booting problems, and it should be in everyone's software CD collection even if they may never need to use it.

All the best, Rgeards, Herman :D[COLOR="Blue"]**[SIZE="3"]Eureka! I made it![/SIZE]**[/COLOR] Thank you so much Herman, confused57, A2A...If you where here I would give you a hug...
Actually, the only thing I had to do, was to edit the /boot/grub/menu.list as confused57 decribed it, i.e enter 
[COLOR="Red"][I][I][I][I][B]title Windows XP
root (hd1,0)
savedefault
makeactive
map (hd0) (hd1)
map (hd1) (hd0)
chainloader +1.[/B][/I][/I][/I][/I][/COLOR] 
SATA drives caused no problem. They are also named hdo, hd1.

Ubuntu and it's people are great!:grin: 
Regards
Juergen

---

### Post by confused57 on 2006-08-08
> **Cariboo1938 said:**
> [COLOR="Blue"]**[SIZE="3"]Eureka! I made it![/SIZE]**[/COLOR] Thank you so much Herman, confused57, A2A...If you where here I would give you a hug...
Actually, the only thing I had to do, was to edit the /boot/grub/menu.list as confused57 decribed it, i.e enter 
[COLOR="Red"][I][I][I][I][B]title Windows XP
root (hd1,0)
savedefault
makeactive
map (hd0) (hd1)
map (hd1) (hd0)
chainloader +1.[/B][/I][/I][/I][/I][/COLOR] 
SATA drives caused no problem. They are also named hdo, hd1.

Ubuntu and it's people are great!:grin: 
Regards
Juergen

Glad you got it working...it's definitely quite simple to do, but I can understand your apprehension & it's prudent not to take the advice of just anybody.  I've seen many people who've had no problem using this method with SATA drives, but seems like there's always an exception or two.

---

### Post by Cariboo1938 on 2006-08-08
> **Herman said:**
> I just think the Super Grub Disk is a good thing. It's the best thing I've found yet to help people with booting problems, and it should be in everyone's software CD collection even if they may never need to use it.
All the best, Rgeards, Herman :DNow having Dual Boot working I checked the Super Grub Disk and was a bit dissapointed. It seems it is to complicated for my level of Linux experience. I can not access the <--Main Menu, I cannot find the menu to select a OS, I just don't get..
> **Herman said:**
> In Ubuntu lots of things are much easier than people might expect if they aren't used to it. All I do for a Super Grub Disk is download the sgd_0.9428.iso.bz2 **[COLOR="Blue"]or one of the other similar files[/COLOR]**.....It is probably always a good idea to have a boot disk. Is there a simpler one? Because the features of the S.G.D. are to complicated for me...
Greetings
Juergen

---

### Post by A2A on 2006-08-09
> [COLOR=Blue]**[SIZE=3]Eureka! I made it![/SIZE]**[/COLOR] Thank you so much Herman, confused57, A2A...If you where here I would give you a hug... 
Cariboo1938, i'm glad you managed ot get the help you needed and all  worked out for you as well.

Regards,

A2A

---

### Post by Herman on 2006-08-09
> It is probably always a good idea to have a boot disk. Is there a simpler one? Because the features of the S.G.D. are to complicated for me... GAG Boot Manager is easier, it is a Graphical boot manager. It will boot Windows for you very easily. It needs either Grub or Lilo installed to the first sector of your Ubuntu partition though. I recommend Lilo for that. You'll probably never need to use it, but it does give you an second method for booting.  For more info on GAG, here's a link, [GAG Page]("http://users.bigpond.net.au/hermanzone/p12.htm")

S.G.D. will seem easier later when you are ready for it. Regards, Herman :D

---

### Post by Cariboo1938 on 2006-08-09
> **Herman said:**
> GAG Boot Manager is easier, it is a Graphical boot manager. It will boot Windows for you very easily. It needs either Grub or Lilo installed to the first sector of your Ubuntu partition though. I recommend Lilo for that. You'll probably never need to use it, but it does give you an second method for booting.  For more info on GAG, here's a link, [GAG Page]("http://users.bigpond.net.au/hermanzone/p12.htm")

S.G.D. will seem easier later when you are ready for it. Regards, Herman :D
Does gag46 work for the 64bit architecture -Ubuntu?

---

### Post by craiger316 on 2006-08-09
I just installed Ubuntu for the first time on a machine that had WinXP already on it.  I used the graphical install from the normal desktop iso by clicking the install icon on the live-cd desktop.  

Now I was going for the option of cleaning the drive of XP and installing ubuntu overtop, but I did see the option there that would allow me to resize the windows partition and install Ubuntu into the remaining space.

I was curious, my friend wants to dual-boot so he can still play BF2, can he simply choose that option to resize the windows part and install into the remaining space?  Will all the grub options be made for him so that when the install is complete he will have a dual boot system?  Or is he forced to use the alternate-cd install in text mode and do all the options himself?

Thanks in advance,

Craig.

---

### Post by VirtuAlex on 2006-08-09
> **craiger316 said:**
> can he simply choose that option to resize the windows part and install into the remaining space?  Will all the grub options be made for him so that when the install is complete he will have a dual boot system?
Yes, but do the backup first.

---

### Post by craiger316 on 2006-08-09
Thanks for the quick reply.  I'll tell him to ghost his windows partition first.

Little OT here, but is there any free ghosting software out there?  Ideally to ghost from an internal HDD to a USB HDD.

---

### Post by VirtuAlex on 2006-08-09
> **craiger316 said:**
> I'll tell him to ghost his windows partition first.
Little OT here, but is there any free ghosting software out there?  Ideally to ghost from an internal HDD to a USB HDD.
That I do not know, you better do research or start a new thread on this. Honestly, I think it is overkill to back up whole partition which you're looking forward to get rid of (or at least use only for occasional gaming). Just back up the data, like documents, email, etc., or maybe only gamesaves ;) It's 99% chance that everything will go smoothly and you'll never need your backup disks, but it's good to have them anyway and update them regularly. Gives you peace of mind and clears your consciousness. Shit happens, you know, better safe than sorry, and suff like that.

---

### Post by Herman on 2006-08-10
>  Does gag46 work for the 64bit architecture -Ubuntu? Cariboo1938, Yes, I think so. I seem to remember someone else asking me that same question a while ago and tried it and said it did work. Just to check up I looked over GAG's own forums and found one link on the subject. (It sin't a very big forum). [Link ]("http://sourceforge.net/forum/forum.php?thread_id=1258693&forum_id=230440")
Anyway, just give it a try from a floppy disk first to make sure, GAG works great from a floppy disk. :D Regards, Herman

---

### Post by adrian15 on 2006-08-10
> **A2A said:**
> 
System.map-2.6.15-23-386 (txt file)
abi-2.6.15-23-386 (txt file)
config-2.6.15-23-386 (txt file)
initrd.img-2.6.15-23-386 (file with a pic of an "open box" in the icon)
memtest86+.bin (file with a "foot" in the icon)
vmlinuz-2.6.15-23-386 (file with a "foot" in the icon)


Hi all SGD users from this forum. :).
I need some feedback for SGD if you do not mind.
When a normal ubuntu or xubuntu installation is done... do you find in /boot links named initrd.img and vmlinuz that would point to: initrd.img-2.6.15-23-386 and to: vmlinuz-2.6.15-23-386  or these link files do not exist?

Hi Herman. I am asking this because the last version of SGD (Available right now only in Cdrom) has the option: Boot Other Oses -> Boot Linux -> Boot Automatically that should look for vmlinuz,initrd and fstab so that it can handle automatically the boot of Linux. **Without the need of having Grub even installed. ** (The same that Herman explained but without knowing the commands.)

The only problem for this option right now would be the non-existence of the initrd and vmlinuz links.

However if they do not exist or if they are named with other names such as initrd.gz like it happens in other distributions... I will have to implement a command to detect kernel and initrd or one that finds first file with vmlinuz* expression or initrd* expression. What a nightmare! Sometimes programming in Grub Legacy is a nightmare :) you know. ;)

Well! Enjoy SGD!

adrian15

---

### Post by Herman on 2006-08-10
Hello, adrian15, we are extremely honoured by your presence! I am more than happy to provide all the feedback I can , (at least to the limits of my ability). 

As far as I know (being just a user, not a developer or software engineer), the vmlinuz and initrd.img files we have in /boot are the actual kernel and initrd.img. There are links to those from /.

Here is a series of screencaps showing what our /boot and /boot/grub files look like in GUI mode for a typical fresh install.......................[GO]("http://users.bigpond.net.au/hermanzone/p15.htm#oreintation")
Refering to fig 4 grub there, I think the initrd.img and vmlinuz we can see there in / are links, possibly to the files in /boot.  See also figs 5 and 6 below there.

Here is the same thing in CLI mode, but for a different installation,
> herman@yellow:~$ ls -a -l /
total 116
drwxr-xr-x  21 root root  4096 2006-08-08 14:26 .
drwxr-xr-x  21 root root  4096 2006-08-08 14:26 ..
drwxr-xr-x   2 root root  4096 2006-08-08 14:49 bin
drwxr-xr-x   3 root root  4096 2006-08-09 19:18 boot
lrwxrwxrwx   1 root root    11 2006-08-08 14:22 cdrom -> media/cdrom
drwxr-xr-x  16 root root 15200 2006-08-11 07:06 dev
drwxr-xr-x 104 root root  4096 2006-08-11 07:06 etc
drwxr-xr-x   3 root root  4096 2006-08-08 14:49 home
drwxr-xr-x   2 root root  4096 2006-08-08 14:23 initrd
lrwxrwxrwx   1 root root    29 2006-08-08 14:26 initrd.img -> boot/initrd.img-2.6.15-23-386
drwxr-xr-x  19 root root  4096 2006-08-08 14:49 lib
drwxr-xr-x   2 root root 49152 2006-08-08 14:22 lost+found
drwxr-xr-x   8 root root  4096 2006-08-11 07:06 media
drwxr-xr-x   2 root root  4096 2006-05-23 00:00 mnt
drwxr-xr-x   2 root root  4096 2006-08-08 14:23 opt
dr-xr-xr-x 111 root root     0 2006-08-11 17:00 proc
drwxr-xr-x   3 root root  4096 2006-08-08 14:26 root
drwxr-xr-x   2 root root  4096 2006-08-08 14:49 sbin
drwxr-xr-x   2 root root  4096 2006-08-08 14:23 srv
drwxr-xr-x  10 root root     0 2006-08-11 17:00 sys
drwxrwxrwt  10 root root  4096 2006-08-11 07:05 tmp
drwxr-xr-x  11 root root  4096 2006-08-08 14:32 usr
drwxr-xr-x  14 root root  4096 2006-08-08 14:45 var
lrwxrwxrwx   1 root root    26 2006-08-08 14:26 vmlinuz -> boot/vmlinuz-2.6.15-23-386
herman@yellow:~$
                                    > herman@yellow:~$ ls -l -a /boot
total 8468
drwxr-xr-x  3 root root    4096 2006-08-09 19:18 .
drwxr-xr-x 21 root root    4096 2006-08-08 14:26 ..
-rw-r--r--  1 root root  266619 2006-08-09 18:59 abi-2.6.15-23-386
-rw-r--r--  1 root root   69878 2006-08-09 19:01 config-2.6.15-23-386
drwxr-xr-x  2 root root    4096 2006-08-09 19:23 grub
-rw-r--r--  1 root root 6767121 2006-08-09 19:01 initrd.img-2.6.15-23-386
-rw-r--r--  1 root root   94760 2006-08-09 19:01 memtest86+.bin
-rw-r--r--  1 root root 1414477 2006-08-09 19:01 vmlinuz-2.6.15-23-386 One file called System.map-2.6.15-23-386 is missing from the above list because this is the test installation I practiced a simulated recovery with, for A2A's install, (eariler in this thread). I deleted my /boot/grub directory to try to simulate his predicament and then used 'mkdir /boot/grub', followed by 'sudo grub-install /dev/hda', and lastly, 'sudo update-grub, to restore the system and got back all but the System.map, and the test system is functioning quite alright as far as I can  tell.

Below is the contents of the /boot/grub file.
> herman@yellow:~$ ls -l -a /boot/grub/
total 188
drwxr-xr-x 2 root root   4096 2006-08-09 19:23 .
drwxr-xr-x 3 root root   4096 2006-08-09 19:18 ..
-rw-r--r-- 1 root root    197 2006-08-09 19:18 default
-rw-r--r-- 1 root root     30 2006-08-09 19:18 device.map
-rw-r--r-- 1 root root   7508 2006-08-09 19:18 e2fs_stage1_5
-rw-r--r-- 1 root root   7332 2006-08-09 19:18 fat_stage1_5
-rw-r--r-- 1 root root   8128 2006-08-09 19:18 jfs_stage1_5
-rw-r--r-- 1 root root   3705 2006-08-09 19:23 menu.lst
-rw-r--r-- 1 root root   6804 2006-08-09 19:18 minix_stage1_5
-rw-r--r-- 1 root root   9076 2006-08-09 19:18 reiserfs_stage1_5
-rw-r--r-- 1 root root    512 2006-08-09 19:18 stage1
-rw-r--r-- 1 root root 105428 2006-08-09 19:18 stage2
-rw-r--r-- 1 root root   8764 2006-08-09 19:18 xfs_stage1_5
herman@yellow:~$ 
> Hi Herman. I am asking this because the last version of SGD (Available right now only in Cdrom) has the option: Boot Other Oses -> Boot Linux -> Boot Automatically that should look for vmlinuz,initrd and fstab so that it can handle automatically the boot of Linux. **Without the need of having Grub even installed. ** (The same that Herman explained but without knowing the commands.) I am sorry for not knowing that sooner, adrian15. It is my fault. What happened is, I thought I had the newest version when I was downloading it, but I am wrong, it is still an oudated version of SGD (sgd-0.9321) I am using right now.   I tested all the SGD menu options out to learn how SGD works, and  'other OSes Boot' wasn't doing anything for me.
Now that you have prompted me look again, I have downloaded the newest version now (I think) , it is sgd_0.9428.iso. I will burn that one to disk right away after this post and test that one out. Thank you for your instructions. I want to learn what all the functions that Super Grub Disk can do because I think Super Grub Disk is great and will be a huge help to be able to use SGD to help new users solve all kinds of booting up problems.
SGD is good both for those who can use the Command Line as well as those who are reluctant  and frightened by CLI mode.  Booting up problems are very scary for new users especially, even if they are experienced (Windows) users.  This problem is one of the things that keeps some people from getting started with Linux. 
For experienced Linux users, being able to boot without even having Grub installed is quite a feat and so SGD is a valuable rescue tool for those of us who like to experiment and learn new tricks and might sometimes need to recover their system.
I think SGD will start seeing a lot more use around here from now on. 
Thank you, adrian15, for SGD and for your interest in us ordinary users especially. SGD is great!
All the best, Regards, Herman :D

---

### Post by Herman on 2006-08-10
Hello, adrian15,:D, I'm now using sgd_0.9428, and I have gone; other OSes Boot -> Boot Gnu/Linux -> Automatically Boot Gnu/Linux IDE Hard Disk.

SGG is searching each partition automatically, but it still doesn;t seem to be able to boot anything. I have Windows XP on (hd0,1) (I only use it for a guinea pig), and then I have my regular working Ubuntu Dapper install on (hd0,1), plus a test install of Dapper on (hd0,6), for trying out risky tricks with, plus a copy of the test installation that I can restore the test installation with, by copying it and pasting it with a GParted LiveCD, (for when I 'hose' the test install, I can replace it in ten minutes).

Right now, SGD has looked ay (hd0,1) and I have it paused there. The message is as follows,
> root (hd0,1)
fIlesystem type is ext2fs, partition type 0x83
kernel /boot/vmlinuz root=/dev/hda2

Error 15: File not found
   Booting 'it does not boot'

configfile (cd) /boot/sgd/S10en/s25_bootoses/s25linux/autoide/auto3.lst I get a similar error for (hd0,6 and (hd0,7) as well.

Am I doing something wrong? It would be great to be able to have SGD automatically find the kernel and boot without the command line. 

At least (hd0,1) and (hd0,6) will boot from the CLI mode. I don't bother booting (hd0,7) because it is just a backup, but it would work if I edit /etc/fstab. 

If that feature in SGD disk would find my Linux kernel and boot it, it would be great, I could have used that to help A2A withoout needing the command line.

The other SGD options that all work for me  are; 

'Special Boot ->Boot your Gnu/Linux (or other OS) again -> Boot Automatically -> AUTO,
The SGD help information says this option will make SGD automaticlly search for a previous Grub configuration file, and then boot the first operating system it finds that has one, I guess. That one works for me. :D

And, 'Manual Boot -> /boot/grub/menu.lst -> hda -> hdaX
That works for me fine too. I would be able to use that if I wanted to boot the system with the non-first  Grub configuration file that SGD finds. (If I wanted to boot (hd0,6) instead of (hd0,1), for example. :D

Also, 'Classic Boot' -> Boot MBR -> hda ' 
That would find a MBR that has a bootloader installed in it, especailly this would be handy where soemone installs Ubuntu  in a computer with multiple hard disks and especailly when IDE and SCSI or sata disks are both used, and only Windows will boot because Grub went to the non-first MBR by mistake. :D

and 'Classic Boot -> Boot Partition -> hda -> hdaX
That would boot a partition that has a bootloader installed to the first sector of the partition. I do that as an extra method for booting, I like to install Lilo to the partition, and Grub to MBR as well. We can have both, so if one doesn't work for some reason (user's crazy experiments and errors for example), the other loader will still work. That method boots all my operating systems with SGD as well. :D

Everything works for me except 'other OSes Boot' 

Thanks again for your time and interest, Regards, Herman :D

---

### Post by Herman on 2006-08-11
adrian15, I am still not really sure I am using the latest version of Super Grub Disk. I have an .iso file named sgd_0.9428.iso which I have tried burning to  the same CD-RW that version 0.9321 was on, and it looks like it is getting erased first, then the new .iso burned to disk. 
But that it still has printed in the white type on black background after selecting the English Super Grub Disk in 'S.G.D. Language Selection', after the third press of my return (or enter) key, 'Super Grub Disk 0.9321 Fatty Edition'. I have tried burning the sgd_0.9428.iso to a fresh CD-RW that has never had anything else on it before, and still get the same version number 0.9321 instead of 0.9428. 
I have tried re-downloading the file and it still has the old version number in it after it is burned to a CD-RW and is booted.

So I am not really sure I am using the correct (latest) version yet. I wonder why that could be? Maybe the mirror has got the older version copied accidentally somehow with the newer version's number?  :?:

Regards, Herman :D

---

### Post by adrian15 on 2006-08-11
When I am releasing a major version (major improvements, cdrom, floppy and usb version) that I will post in Barrapunto.com, slashdot and of course in freshmeat I go to the introduccion.txt file and update the version of Grub and its edition.

When I am releasing time-to-time cdrom-only version I do not change neither version nor edition. But it is a good thing because this way an edition goes from one version to another (Let's say from 0.9234 to 0.9345). And that was the meaning I wanted to give to edition: An era. A set of versions.

If you want to edit my source code and make it very easy to update the SGD version so that I can update it so not to confuse you and others... you're welcomed to do it.

In conclusion, you have being downloading the last version.

adrian15

---

### Post by adrian15 on 2006-08-11
> **Herman said:**
> Hello, adrian15,:D, I'm now using sgd_0.9428, and I have gone; other OSes Boot -> Boot Gnu/Linux -> Automatically Boot Gnu/Linux IDE Hard Disk.

SGG is searching each partition automatically, but it still doesn;t seem to be able to boot anything. Right now, SGD has looked ay (hd0,1) and I have it paused there. The message is as follows,  I get a similar error for (hd0,6 and (hd0,7) as well.

Am I doing something wrong? It would be great to be able to have SGD automatically find the kernel and boot without the command line. 
If that feature in SGD disk would find my Linux kernel and boot it, it would be great, I could have used that to help A2A withoout needing the command line.


You are using last version. Yes, last published version. When I was talking about "last" version about talking about my last version the one which it is in my computer. I just did think that the last published version had this.

There has been one month or so that I do not develop SGD and I did not remember it.

But you're a lucky man.

[URL="http://adrian15.raulete.net/grub/tiki-download_file.php?fileId=73"]SGD 0.9434 Bzip2 ISO
[/URL]

I've updated it to the misc section so that the least people download it but as it is on the last files section on the main page... other people will use it.

It is a test version. I do not remember which new features it has apart from the Boot Linux Auto one (Check doc/sgd_dev_blog.txt on the source code of this version that I've also uploaded if you want to know more.)

If you think that it does not work. Please create links from:

vmlinuz
initrd.img
(SGD looks only for these files right now. If other files are more often used by Linux distros I will use them.)


to the correct files.

Then re-run SGD Boot Linux Auto option and if it does not work. Please report it!

adrian15

---

### Post by adrian15 on 2006-08-11
> **Herman said:**
> I want to learn what all the functions that Super Grub Disk can do because I think Super Grub Disk is great and will be a huge help to be able to use SGD to help new users solve all kinds of booting up problems.

I think that now that I can cat files with a pause I could add a help item to the main SGD menu to explain the most common boot problems and their solutions by the means of SGD or other programs.

It would be only writing a large txt file with a lot of information because I do not want to have to think on how to do a complex documentation system above the SGD system.

Would you mind being the one who writes this text file?

A good beginning would be to ellaborate on *Situtations where Super Grub Disk is useful*, text, you can find in [SGD main webpage]("http://adrian15.raulete.net/grub/").

If you accept to do the best way for us to communicate would be for you to subscribe to the [SGD Mailing List]("https://listas.ensanjose.net/listinfo/supergrub") too.

adrian15

---

### Post by Herman on 2006-08-11
> I think that now that I can cat files with a pause I could add a help item to the main SGD menu to explain the most common boot problems and their solutions by the means of SGD or other programs.
It would be only writing a large txt file with a lot of information because I do not want to have to think on how to do a complex documentation system above the SGD system.
Would you mind being the one who writes this text file?adrian15, I would love to be able to do that!   :D :D :D

Actually, I was thinking already of asking for your permission to write a web-page on my website about Super Grub Disk too. 
I would like to make a page that explains how to use SGD menu features to trouble-shoot all kinds of bootloader problems, especailly where SGD can help with Ubuntu installs. I can link it to the other Grub Page I have for the CLI mode help.

I am so excited and happy I not sure what to do first, download the latest version and start testing it I guess. Then get in touch with you by PM or mailing list. :D This is just the kind of thing I will love to do! :D
Regards, Herman

---

### Post by confused57 on 2006-08-11
Herman,  I'm looking forward to reading your Super Grub page on your website and many thanks to adrian15 for developing Super Grub.

I've downloaded both the sgd_0.9428 and 0.9434 and plan on trying both out on my test computer running a dual boot of Dapper and Mepis.
There have been numerous posts with people having bootloader problems and about all I can do is guess at how to tell them to proceed in many instances, especially if SATA drives are involved.  This looks like it could be the answer to a lot of problems booting different OS.
Thanks again...

---

### Post by Herman on 2006-08-12
> I'm looking forward to reading your Super Grub page on your website confused57, here is a link for what I am up to so far, but at the time of typing this, it is still very rough and ugly. 

[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)

It will be some time before I will be happy with it. These projects are never completed anyway. There are always more to be added, and then the software is updated. It's a rewarding hobby though. It is especially satisfying when it does actually help someone. Probably this will help a lot of people, so I am impatient to go ahead and get it on out A.S.A.P. 
You will see improvements over this weekend. Then I will only be able to do a little until next weekend, but I will see how much I can do today.
Regards, Herman :D

---

### Post by Cariboo1938 on 2006-08-12
> **Cariboo1938 said:**
> Does gag46 work for the 64bit architecture -Ubuntu?Has any body an answer to this question? I created the Boot floppy and I get the error message: Sector boot not found or invalid. My 2nd hard drive with Windows is not recognized at all. See question in quotes? 

 [COLOR="Orange"]I opened a new thread at the 64 bit forum 
"Boot Floppy/CD gag64" 
because nobody is anwering and I think this is not the right place for this question... [/COLOR]

---

### Post by Herman on 2006-08-12
Hello, Cariboo1938, as far as I can tell it is supposed to work on AMD64 architecture, at least according to the following link found in GAG's own forum. [http://sourceforge.net/forum/forum.php?thread_id=1258693&forum_id=230440](http://sourceforge.net/forum/forum.php?thread_id=1258693&forum_id=230440)
>  I created the Boot floppy and I get the error message: Sector boot not found or invalid. I'm not sure if you mean the floppy disk didn't boot? ...You have set your BIOS boot sequence to include the floppy disk drive before your hard drive? (I know, just checking, sorry :-\" ).
> My 2nd hard drive with Windows is not recognized at all. I don't know, I would imagine it should be.

I'm sorry if GAG Boot Manager isn't working in your machine for you, Cariboo1938.  If you can't get it working, maybe just save it for helping someone else who it will work for. You never know, it might just bring you some good luck! :D

Would you like to test out Super Grub Disk again? I have been working on my web-page for it, so you can see, (I hope) how it works a little easier. [Super Grub Disk Page]("http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html")

To boot Windows on your second hard disk with Super Grub DIsk, you would use either the 'Boot Windows' option from the main menu, or go.'Classic Boot ->Boot Partition -> Hard disk 2-> Partition no.?' That should boot Windows for you.
I'm still working on that webpage, and I am wondering if it's easy for other people to understan or if it's too confusing? :D

All the best, Regards, Herman :D

---

### Post by Cariboo1938 on 2006-08-12
> **Herman said:**
>  
 I'm not sure if you mean the floppy disk didn't boot? ...You have set your BIOS boot sequence to include the floppy disk drive before your hard drive? (I know, just checking, sorry :-\" ).
 I don't know, I would imagine it should be.Hello, Herman, I'm glad you checked on me, Thank you so much. 
Yes, the floppy **does** boot....the gag window opens and gives me the choice to boot from the OS I entered...but it fails to do more...giving me the message:
"Sector boot not found or invalid". This is a message on the 'gag screen'. Here you may see how I set it up:> Setting up Boot Floppy

I follow the instructions on Herman's very detailed "GAG page";
Start menu: 'Choose an option' : Install {4}
2nd menu: 'Choose your keyboard': qwerty {1}
3rd menu: 'Choose your language': English {8}
4th menu:  Choose  "Setup GAG"  Key {S}
New Menu: Choose "Add a new OS"
New menu shows 
Key      Partition    Type
B          83h Linux	Ext2 (Text colour black, also line C,D)
..
G	83h Linux	Ext2 (Text colour blue, also line E,F)
H  
It seems that H is the swap Partition. and the second hard drive, where Windows is installed, is not recognized.  
If I select any of these B-G and follow the instructions to "Save on Floppy" {F}
I get, when restarting with the floppy inserted, the GAG menu showing Linux OS. When I try to start it, I get the error message: "Sector boot not found or invalid". That's it. I have to take the floppy out and reset the computer.
What went wrong?
 > :D Would you like to test out Super Grub Disk again? I have been working on my web-page for it, so you can see, (I hope) how it works a little easier. [Super Grub Disk Page]("http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html")I certainly like to test the Super Grug Disk again. I keep you posted. Just out of curiosity, do you have any thought on the gag message?
Greetings from Beautiful British Columbia (Text on our licence plates)
Cariboo:)

---

### Post by confused57 on 2006-08-12
Cariboo,
   I haven't had any luck myself with a GAG floppy and all my computers are i386...I think that I'm following the instructions to the letter, but I get the same error message you do and I cannot get the GAG floppy to boot my Linux OSes(although I'm inclined to believe it's something I'm doing incorrectly).
   I'm going to give the SGD a try, Herman's instructions make it pretty straightforward and understandable...maybe I'll have better luck with it.

---

### Post by Herman on 2006-08-12
Cariboo1938
I don't know why GAG doesn't seem to recognise your second HDD. Often it takes a little trial and error to get GAG set up for the right partition because it isn't clear which partition is which. *Normally*, though, GAG Boot Manager will boot Windows quite readily, once you find out which partition you want. Make sure you press your '1' key and read all the instructions that come with GAG, and also the '2' key for FAQ. It should be able to do everything you want, according to the instructions in my GAG disk.

To use GAG to boot Linux, it just needs a bootloader installed to the first sector of the Linux (Ubuntu) partition.
To install GRUB in the first sector of your Ubuntu partition at any time after Ubuntu is already installed, [*Click Here*]("http://users.bigpond.net.au/hermanzone/p12.htm#Install_GRUB_to_a_Linux_O.S._Partition")  to see an example.
      To install Lilo in an already installed and working Ubuntu partition, (even if you already have GRUB on MBR), follow this how-to: [Install Lilo from terminal.]("http://users.bigpond.net.au/hermanzone/p12.htm#Install_Lilo_from_terminal")

I'm still hard at it with Super Grub Disk. I'm now up to making a list of bootloader problems and how to solve them with help form S.G.D.
All the best, Regards, Herman :D

Edit, it says in FAQ in GAG Boot Manager that GAG shows only the partitions in one hard disk at a time. To see partitions in the next hard disk, you press '2', and to see a third disk's partitions you press '3', and so on. See FAQ 11(b). :D

---

### Post by Cariboo1938 on 2006-08-13
> **Herman said:**
> I'm still hard at it with Super Grub Disk. I'm now up to making a list of bootloader problems and how to solve them with help form S.G.D.
All the best, Regards, Herman :D  Here my report about SGD: 
Hello Herman,
here the results of my second try with SGD. My system has two hard drives. On the first HD is Linux installed, on the 2nd Windows XP. I created the SGD new today.

I boot from SGD:

---Waterfall screen opens ->I select Engl. SG Disk
---Introduction text  ->Hit return to continue
---Introduction text continued ->Press a key
---Text about the software (Version 0.9321) ->Press a key
---Blue window opens with"8 menu options" from 1. Restore GRUB in hard disk (MBR)                                                            
   to 8. Quit  ->Select "Boot Windows"
---Text, beside other, "If you want to boot a Windows that is not found on 
   the first partition of the first HD, please use "Boot Partition Menu" which is found under "Classic Boot Menu"
    ->Press a key ->Go back to Main Menu ->Choose  Classic Boot ->Choose Boot Partition
    Here is a explanation  which is not quite clear to me, so ->Press a key
---Blue window opens with one option: Boot Partition  ->select "Boot Partition"
---Blue window opens with four partitions listed:  "hda, sda, hd0"
                                                                                  "hdb, sdb, hd1"
                                                                                  "hdc, sdc, hd2"
                                                                                  "hdd, sdd, hd3" 
     Assuming "hdb, sdb, hd1" is my Windows Hard Disk I select hdb.

{BTW, if I choose "hda" system hangs with text line "Booting  'Partition to boo' "on a black screen. If I choose "hdc,hdd" I get error 21: Partition does not exist}      - >Select hdb

---Blue window opens and shows a list of ten partitions, hdb1 through 10. For me it is not clear which one I have to choose because I do not recognize the Windows C:/ partition or a second HD.

If I select, for example "hdb1", in the believe it is the first partition on the 2nd HD ( hdb )
System hans with text lines:

set out_device=(hd1,0)
set out_part=(hd1,0)
set out_lide_part= hdb1 
set out_lscsi_part=sdb1
set out_hurd_part=sd1s1
set out_linux_part=b1
set out_part_n=0
back
back
set aux_part=(hd1,0)
rootnoverify (hd1,0)
chainloader +1
boot

The same sitiation when I tried it 2 days ago. I'm lost in this partition naming problem.](*,)

---

### Post by Cariboo1938 on 2006-08-13
> **Herman said:**
>  .....because it isn't clear which partition is which. *Normally*, though, GAG Boot Manager will boot Windows quite readily, once you find out which partition you want. Make sure you press your '1' key and read all the instructions that come with GAG, and also the '2' key for FAQ. It should be able to do everything you want, according to the instructions in my GAG disk.
:DHerman, it's me again....if I see the result of ```
sudo fdisk -l
```[QUOTE=Terminal]owner@Owner-Desktop:~$ sudo fdisk -l

Disk /dev/sda: 81.9 GB, 81964302336 bytes
255 heads, 63 sectors/track, 9964 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1 */boot        1          64      514048+  83  Linux
/dev/sda2  /           65         191     1020127+  83  Linux
/dev/sda3  /Storage   192        1466    10241437+  83  Linux
/dev/sda4            1467        9964    68260185    5  Extended
/dev/sda5  /home     1467        5291    30724281   83  Linux
/dev/sda6  /usr      5292        7840    20474811   83  Linux
/dev/sda7  /var      7841        9752    15358108+  83  Linux
/dev/sda8            9753        9964     1702858+  82  Linux swap / Solaris

Disk /dev/sdb: 122.9 GB, 122941242880 bytes
255 heads, 63 sectors/track, 14946 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1 * XP         1        2550    20482843+   7  HPFS/NTFS
/dev/sdb2   User    2551       14946    99570870    7  HPFS/NTFS
owner@Owner-Desktop:~$[/QUOTE]I think it is pretty clear what is what or who is who, isn't it?
Kind Regards,Cariboo

---

### Post by Herman on 2006-08-13
Cariboo1938, Thank you very much for your time and effort! You probably don't realize how much that helps me to understand the kind of troubles I need to remember that people have that I need be able to explain about. It looks to me like you did everything right though.

Anyway, I will see if I can explain a bit about Linux names and numbers for hard disks and partition compared with Grub style partition names and numbers. I will have to go back and learn again the Windows way of naming things, because I have forgotten now.
Normally C: would be /dev/hda1 in Linux terms, or (hd0,0) in Grub terms.

 /dev/hda    In Linux, (the first hard disk) is called (hd0) in Grub
 /dev/hdb                            in Linux, (second hard disk) is called (hd1) in Grub
 /dev/hdc in Linux                            (the third hard disk) is called (hd2) in Grub, and so on.
when they are all IDE disks.

If they are SCSI disks, they are    
/dev/sda   = (hd0) in Grub
                                                       /dev/sdb  = (hd1) in Grub
                                                and 
/dev/sdc  = (hd2) in Grub, and so on.
Grub makes no distinction between scsi and ide drives.

Grub always starts counting from the number 0, which is a little confusing until you get used to it.
Partition numbers are the same, the first partition on your first hard drive will be /dev/sda1 in Linux, and (hd0,0) in Grub
............................................................................the second partition will be /dev/sda2 in Linux, and (hd0,1) in Grub.

The second hard hard drive, first partition, which you were trying to boot, would be /dev/sda1in Linux, and (hd1,0) to Grub.
Therefore, I think you did everything okay, I don't know why it didn't boot.

Anyhow, you are dual booting okay eh? It's just that you aren't able to get a seperate bootloader from a floppy disk or CD to work now, right? :D
Regards, Herman

---

### Post by adrian15 on 2006-08-13
> **Cariboo1938 said:**
> ->Select "Boot Windows"
---Text, beside other, "If you want to boot a Windows that is not found on 
   the first partition of the first HD, please use "Boot Partition Menu" which is found under "Classic Boot Menu"
    

You don't get Windows to boot in the second hard disk because the text is not accurate enough.

If you want to boot a Windows that is not found on the first partition of the first hard disk but in the second or third partition (always on the first hard disk) you have to use:
"Boot Partition" Menu found inside "Classic Boot" menu.

If you want to boot a Windows that it is found on a second hard disk you will have to use the "Swap Hard Disk and Boot" option from inside the "Special Boot" menu.

We always consider that Windows was installed in the first hard disk and then the hard disk was moved in the pc to be the second hard disk.


I will update Boot Windows text so that it is more accurate.

A question do you prefer me to add two options to Boot Windows menu:
- Boot windows (This one was already)
- Boot windows on a laptop (Boots second partition on first hard disk. Useful for laptops with backup partitions)
- Boot windows from 2nd hard disk
instead of adding the text to the Windows explanation?


adrian15

---

### Post by adrian15 on 2006-08-13
> **Herman said:**
> I have been working on my web-page for it, so you can see, (I hope) how it works a little easier. [Super Grub Disk Page]("http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html")

That's a great webpage! Keep up the good work. You will hear from me soon with some errors that I may find.

The good thing about this is that I will read your webpage carefully and whatever SGD explanations lack I will add to them.

adrian15

---

### Post by A2A on 2006-08-13
> **adrian15 said:**
> That's a great webpage! Keep up the good work. You will hear from me soon with some errors that I may find.

The good thing about this is that I will read your webpage carefully and whatever SGD explanations lack I will add to them.

adrian15
Herman, adrian15, and the rest of the folks participating in this project.  Keep up the great work!
It's very rewarding to see something come out of this.  I feel thrilled just by the fact that I started this post, and Herman, confused57 and adrian15 took it to the next level.

Bravo!

---

### Post by Cariboo1938 on 2006-08-13
> **adrian15 said:**
> If you want to boot a Windows that it is found on a second hard disk you will have to use the "Swap Hard Disk and Boot" option from inside the "Special Boot" menu.
**[COLOR="Magenta"]This does the trick....now I can boot from SGD.... Muchas gracias, adrian15![/COLOR]**> 
I will update Boot Windows text so that it is more accurate.
A question do you prefer me to add two options to Boot Windows menu:
- Boot windows (This one was already)
- Boot windows on a laptop (Boots second partition on first hard disk. Useful for laptops with backup partitions)
- Boot windows from 2nd hard disk
instead of adding the text to the Windows explanation?Yes, add the options, they are more obvious (indiscutible y más fácil de comprender).
Greetings
Cariboo

---

### Post by Cariboo1938 on 2006-08-13
> **Herman said:**
> Edit, it says in FAQ in GAG Boot Manager that GAG shows only the partitions in one hard disk at a time. To see partitions in the next hard disk, you press '2', and to see a third disk's partitions you press '3', and so on. See FAQ 11(b). :DYes, now I found the 2nd HDD and now I can easy start Windows. In "Add new OS.." you have to press '2' to find the next hard drive...ok. Now I want to boot Linux with GAG and inspite there is allready GRUB installed on my first hard drive GAG hangs when I select to boot from Linux. Though I'm closer, I'm stuck again....](*,) ....actually, I like GAG, it's easy to use...

---

### Post by Herman on 2006-08-14
> Yes, now I found the 2nd HDD and now I can easy start Windows. In "Add new OS.." you have to press '2' to find the next hard drive...ok. Now I want to boot Linux with GAG and inspite there is allready GRUB installed on my first hard drive GAG hangs when I select to boot from Linux. Though I'm closer, I'm stuck again....](*,) ....actually, I like GAG, it's easy to use... Hello, Cariboo1938, We normally install the bootloader (or really a pointer for the bootloader) to MBR. The MBR is located in the first sector of a hard disk.

Another place we can install  a bootloader to is the first sector of a partition.  GAG can only boot Ubuntu or ny Linux if there is a bootloader installed to the first sector of the partition. You  can also have the same boot loader in two places, or have two bootloaders and have one installed to MBR, and the other to the partition.
I recommend to install Grub to MBR (You already have), (that really just means to install a pointer for Grub to MBR),  and Lilo to the first sector of the Ubuntu partition. [Click Here]("http://www.ubuntuforums.org/Install%20Lilo%20from%20terminal.") to see how to do that.

EDIT: Sorry, Cariboo1938  that link was not the link I meant to give you, my mistake, here is the right one, [Install Lilo from terminal.]("http://users.bigpond.net.au/hermanzone/p12.htm#Install_Lilo_from_terminal")  edited 15/08/06.

Then GAG will boot Ubuntu. You are doing very well, keep trying and you will be an expert in no time. You have the right attitude and ability to go a long way in Linux.
Regards, Herman :D

---

### Post by Herman on 2006-08-14
>  That's a great webpage! Keep up the good work. You will hear from me soon with some errors that I may find.
The good thing about this is that I will read your webpage carefully and whatever SGD explanations lack I will add to them. Thank You, adrian15, I will welcome all corrections to errors. I am working on adding more information.  I also want to start typing more text with extra information
to explain what Super Grub Disk can do and how to use it.
I will test out all I can, and other things I will try to verify as best I can by searching and reading. I am happy if you can keep an eye out for any mistakes I might make.
Thanks again, Regards, Herman :D

---

### Post by Cariboo1938 on 2006-08-14
> **Herman said:**
> I recommend to install Grub to MBR (You already have), (that really just means to install a pointer for Grub to MBR),  and Lilo to the first sector of the Ubuntu partition. [Click Here]("http://www.ubuntuforums.org/Install%20Lilo%20from%20terminal.") to see how to do that.
Then GAG will boot Ubuntu. You are doing very well, keep trying and you will be an expert in no time. You have the right attitude and ability to go a long way in Linux.
Regards, Herman :DFirst of all, thank you Herman, for your encouragement...I needed it...because sometimes I think I'm to dumb for Linux!#-o  
The URL="http://www.ubuntuforums.org/Install%20Lilo%20from%20terminal."]Click Here[/URL] brings me directly to the Ubuntu Forums Main search page. I expected to find something like 'install lilo' .... Is there another link you can give me?

---

### Post by confused57 on 2006-08-14
Cariboo,
   Herman "may" have meant this section of his GAG page:
[http://users.bigpond.net.au/hermanzone/p12.htm#Install_GRUB_to_a_Linux_O.S._Partition](http://users.bigpond.net.au/hermanzone/p12.htm#Install_GRUB_to_a_Linux_O.S._Partition)

Sometimes I get pretty frustrated using Linux, thinking maybe I'm too old to learn new things such as Linux...I just keep plugging away and it's coming to me slowly...think it's probably easier for younger people, since they "grew up" using computers.  This community helps make Ubuntu the "best" distro, in my opinion...usually there's always someone experienced here who can and is willing to offer assistance.  Hang in there, if I can do it, anyone can...
Add:  You're the same age as my oldest brother...he's a lot smarter than I  and has always had a technical aptitude, trying to get him into Linux, he'd probably catch on quickly.  Linux is a challenge, but I'm enjoying every minute of it.

---

### Post by Cariboo1938 on 2006-08-14
> **confused57 said:**
> Cariboo,
   Herman "may" have meant this section of his GAG page:
[http://users.bigpond.net.au/hermanzone/p12.htm#Install_GRUB_to_a_Linux_O.S._Partition](http://users.bigpond.net.au/hermanzone/p12.htm#Install_GRUB_to_a_Linux_O.S._Partition)

Sometimes I get pretty frustrated using Linux, thinking maybe I'm too old to learn new things such as Linux...I just keep plugging away and it's coming to me slowly...think it's probably easier for younger people, since they "grew up" using computers.  This community helps make Ubuntu the "best" distro, in my opinion...usually there's always someone experienced here who can and is willing to offer assistance.  Hang in there, if I can do it, anyone can...Thanks confused57, this is the link I was expecting...By The Way..."We are never to old to learn something new, this keeps us young.." That's what I'm telling myself every time when I turn this computer on...the extension to Cariboo is the year when I was born...:-$

---

### Post by adrian15 on 2006-08-14
> **Cariboo1938 said:**
> **[COLOR="Magenta"]This does the trick....now I can boot from SGD.... Muchas gracias, adrian15![/COLOR]**Yes, add the options, they are more obvious (indiscutible y más fácil de comprender).
Greetings
Cariboo
Done.

[Super Grub Disk 0.9442 ISO inside a BZ2]("http://adrian15.raulete.net/grub/tiki-download_file.php?fileId=73")

Version 0.9437 to 0.9442 a) Added link support (You can go to one menu to another one) b) Added links to Boot Windows menu c) Updated Boot Windows and Swap Disks texts. Version 0.9434 to 0.9437 changes 1) Added version number generation from last part of folder where SGD source code is stored. 2) Added edition generation from edition.txt file. Thanks to Herman for trying 0.9428 and thinking that it was 0.9321 because version.txt was not updated. Now the version.txt file will be automatically updated. 3) GPL is correctly copied to the SGD cdrom (or whatever device it is generated). 4) Edition is updated to the name: Boot-Linux-Without-Grub-Installed

---

### Post by adrian15 on 2006-08-14
> **Herman said:**
> Thank You, adrian15, I will welcome all corrections to errors.

I've sent you one mail through the board forum that should go to mail address you subscribed to the forum.

Have you received it?

I'm going to send you another one about your SGD webpage right now.
Can you send confirmation or not in: adrian15 THEROUNDTHING raulete POINT net ?

adrian15

---

### Post by Cariboo1938 on 2006-08-14
> **adrian15 said:**
> Done.
Version 0.9437 to 0.9442 a) Added link support (You can go to one menu to another one) b) Added links to Boot Windows menu c) Updated Boot Windows and Swap Disks texts. Version 0.9434 to 0.9437 changes 1) Added version 
number generation from last part of folder where SGD source code is stored. 2) Added edition generation from edition.txt file. Thanks to Herman for trying 0.9428 and thinking that it was 0.9321 because version.txt was not updated. Now the version.txt file will be automatically updated. 3) GPL is correctly copied to the SGD cdrom (or whatever device it is generated). 4) Edition is updated to the name: Boot-Linux-Without-Grub-InstalledYou also wanted to add options to the  Boot Windows menu--- "Boot Windows from 2nd hard disk"---
instead of adding the text to the Windows explanation. 

For me three things are very  confusing:

1)  In the blue Window there is always this irritating text line: Natural Linux - IDE - Linux-SCSI. What does it mean?
2)  I do not know exactly what to do when it comes to: "1st Hard Drive to swap". The Window shows me hda - hdd but I have only two hard drives. Then the next window says "2nd Hard Drive to swap" and gives me exactly the same hard drive list. The next step is to choose the partition to boot from and here comes a list of 10 partitions which have absolutely nothing to to with my configuration.
3)  Knowing that hda(hd0) is the 1st HD with Linux and hdb(hd1) is the 2nd with Windows, I'm not able to go through this swap procedure to get Windows started. To boot into Windows right now I use "Classic Boot" and boot my MBR(GRUB) on the Linux drive and from there I select Windows. But this is probably not the way Super Grub intends to be.?

---

### Post by adrian15 on 2006-08-15
> **Cariboo1938 said:**
> 
You also wanted to add options to the  Boot Windows menu--- "Boot Windows from 2nd hard disk"---
instead of adding the text to the Windows explanation. 


I didn't mention it? I've done it too.

> **Cariboo1938 said:**
> 
1)  In the blue Window there is always this irritating text line: Natural Linux - IDE - Linux-SCSI. What does it mean?
I should only put one number then?

Natural means number... the 1st, the 2nd, the 3rd hard disk or partition
Linux-IDE is the Linux syntaxis/format for ide devices.
Linux-SCSI is the Linux syntaxis/format for scsi devices.
GRUB is the GRUB syntaxis/format for devices.

The problem is that the name do not get aligned to their examples below. I'll put = (equals) instead of spaces to solve the problem.

> **Cariboo1938 said:**
> 
2)  I do not know exactly what to do when it comes to: "1st Hard Drive to swap". The Window shows me hda - hdd but I have only two hard drives. Then the next window says "2nd Hard Drive to swap" and gives me exactly the same hard drive list. The next step is to choose the partition to boot from and here comes a list of 10 partitions which have absolutely nothing to to with my configuration.

1st Hard Drive to swap:
1. hda sda hd0
2nd Hard Drive to swap:
2. hdb sdb hd1
What to boot? Choose Hard Disk and boot the 2nd one.
Or choose partiton and boot the 2nd Disk-->1st partition.

About showing your configuration instead of constant names without any clue about what you have on your computer... I'll try to work on that. But it is quite difficult right now.

> **Cariboo1938 said:**
> 
3)  Knowing that hda(hd0) is the 1st HD with Linux and hdb(hd1) is the 2nd with Windows, I'm not able to go through this swap procedure to get Windows started. To boot into Windows right now I use "Classic Boot" and boot my MBR(GRUB) on the Linux drive and from there I select Windows. But this is probably not the way Super Grub intends to be.?

Can you please copy-paste your /boot/grub/menu.lst (the part where it talks about windows only) ?

Because your windows disk... has it always been a second hard disk or one day it was a first hard disk and then your moved it to be a second hard disk?


adrian15

---

### Post by Cariboo1938 on 2006-08-17
> **adrian15 said:**
> Can you please copy-paste your /boot/grub/menu.lst (the part where it talks about windows only) ?
Because your windows disk... has it always been a second hard disk or one day it was a first hard disk and then your moved it to be a second hard disk?
adrian15Thanks for the information! Here my menu.lst (for Windows):
> 
title           Windows XP
root            (hd1,0)
savedefault
makeactive
map             (hd0) (hd1)
map             (hd1) (hd0)
chainloader +1

 Originally I only had Windows installed on the 1.hard drive. Than I bought a second hard drive for Linux. I changed the SATA connector to the mother board: The new HDD (Linux) was connected to SATA 0, and the original
HDD Windows) was connected to SATA 1. When the system boots, I can see during the BIOS listings that Linux is first and Windows is second.
Greetings
Cariboo

BTW: SATA hard drives, are they declared as ide-devices or scsi-devices?

---

### Post by adrian15 on 2006-08-17
> **Cariboo1938 said:**
> Thanks for the information! Here my menu.lst (for Windows):

Now I know that you can boot Windows on the 2nd hard disk thanks to SGD following the procedure I told you.

I'll try to make an easier option though.
> **Cariboo1938 said:**
> 
BTW: SATA hard drives, are the declared as ide-devices or scsi-devices?
Usually are declared as scsi-devices. Can you look inside the menu.lst? A line beginning with kernel. Check the text after root= if you see sdaNUMBER or hdaNUMBER. sdaNUMBER would mean scsi.

adrian15

---

### Post by Cariboo1938 on 2006-08-18
> **adrian15 said:**
> 
Usually are declared as scsi-devices. Can you look inside the menu.lst? A line beginning with kernel. Check the text after root= if you see sdaNUMBER or hdaNUMBER. sdaNUMBER would mean scsi.
adrian15This is the line referring to 'kernel'. > kernel          /vmlinuz-2.6.15-26-amd64-generic root=/dev/sda2 ro quiet splashDoes this sda2 mean: First scsi hard drive, second partition? I'm learning, so please apologize my question!

---

### Post by adrian15 on 2006-08-20
> **Cariboo1938 said:**
> This is the line referring to 'kernel'. Does this sda2 mean: First scsi hard drive, second partition? I'm learning, so please apologize my question!

Yes, it does.
In fact, I have a SATA disk at home that is not scsi but that is called like yours: sda. Why? Because linux kernel hackers have wanted to do it like this.

From the Super Grub Disk point of view... and Linux kernel... is a SCSI disk.

adrian15

---

### Post by Cariboo1938 on 2006-08-21
> **adrian15 said:**
> Yes, it does.
In fact, I have a SATA disk at home that is not scsi but that is called like yours: sda. Why? Because linux kernel hackers have wanted to do it like this.

From the Super Grub Disk point of view... and Linux kernel... is a SCSI disk.

adrian15Thank you adrian, for the information...and please keep me posted when a new release of SGD is available..I would like to try it!

Cariboo

---

### Post by akaakmdm on 2006-09-16
I attempted to triple boot my computer.  It has xp pro and server 2003 already installed.  I ran the Xubuntu alternative installation cd and went through it untill the end.  When setup finished,  i removed the disk,  the computer rebooted and it says "Grub loading stage1.5"  then on the next line "Grub Loading.......Please wait".  it stays like this and never gives me a chance to select an operating system.  I can't boot to any OS.:confused:

---

### Post by Herman on 2006-09-18
> I attempted to triple boot my computer. It has xp pro and server 2003 already installed. I ran the Xubuntu alternative installation cd and went through it untill the end. When setup finished, i removed the disk, the computer rebooted and it says "Grub loading stage1.5" then on the next line "Grub Loading.......Please wait". it stays like this and never gives me a chance to select an operating system. I can't boot to any OS Hello akaakmdm, 
Probably grub didn't get installed quite properly, there may be some corrupt files due to some kind of weird problem with your installation. You just need to re-install Grub, you can use a Super Grub Disk to do that with most easily, just follow the intructions on this web page, [Click Here]("http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html"), and when you boot Super Grub Disk, you will get a menu that is orange on the bottom. Select 'English', or another language if you like, then read the text file, press enter three times until you get to the next menu. On the next menu, just select 'Restore Grub in Hard Disk MBR', and from the next menu pick 'Automatically install', and you should see this, [Click Here]("http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#Automatically_Install").

If you just want to use your Ubuntu Dapper Live CD, or any Linux Live CD, just follow these instructions here, [click here]("http://users.bigpond.net.au/hermanzone/p15.htm#Re-install_Grub_with_Live_CD").

It doesn't matter which way you want to do it, with a Linux Live CD, or with a Super Grub Disk, you can choose whichever you think wil be easier.

If you need to know anything more, please feel welcome to ask, and if you need special help, please include a copy of the output from the command 'sudo fdisk -lu', here, thanks, ```
sudo fdisk -lu
``` Okay, bye for now, all the best, Regards, Herman :D

---

