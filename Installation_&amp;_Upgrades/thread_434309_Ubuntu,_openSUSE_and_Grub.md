---
title: "Ubuntu, openSUSE and Grub"
date: 2007-05-05
forum: Installation &amp; Upgrades
---

### Post by Jay_in_TN on 2007-05-05
I have a computer with dual HD's, both double partitioned. I have windows 2000 on the first HD, first partition,  and on the second HD I have openSUSE 10.2  and Fedora Core 6. I am using Grub that installed with OpenSUSE because it is a pretty, graphical boot menu, as opposed to the boring, text based menu.
I want to install Ubuntu Edgy (Feisty wont load--hardware issues) on the second partition of the first drive. Will it automatically install a new version of Grub, killing my openSuse grub and forcing a new install of openSUSE to get grub back the way I want it?

openSUSE has a really nice Bootloader interface that searches for other installations and merges them for you, allowing you to customize grub in the easiest way. But after I installed Fedora it killed openSUSE's grub, forcing a reinstall of openSUSE. I would like to avoid this process again after installing Ubuntu.

I am sure this is some way to reconfigure Grub to reload using the pretty, blue graphical interface without reinstalling openSUSE, but I have no idea how to do it.

Any ideas? Anyone else experienced this? Does Ubuntu offer a pretty GUI for Grub and also offer a boot loader that merges existing installs, avoiding all of this?

Thanks,
Jay

---

### Post by Herman on 2007-05-05
Hello Jay_in_TN,
When you install Edgy it will probably install the IPL for Edgy's Grub to your hard disk's MBR, making the MBR point to Edgy's Grub stage2 and other grub files in the Ubuntu filesystem. Edgy will automatically detect Windows 2000, Open Suse, and Fedora Core 6 and add them automatically to your new menu.lst file in Ubuntu.
Ubuntu just has a plain black grub menu at first, with white print on it. It is fully customizable and it is easy for most users to add their own colors or splashimage and configure Ubuntu's Grub any way they like. Most people think that's fun and many people begin learning the fundamentals of basic computer programming that way. It's educational.  Click my third sig link for ideas. :)

However, if you will consider that a chore rather than fun and don't want to do that, it is a trivial matter to re-install  any other operating system's IPL for the other system's Grub to  your MBR any time.  You can do that with a Grub shell.   There is no need to go to all the work of re-installing a whole operating system just because you want to re-install Grub. To get a Grub shell, you just open a terminal and type 'sudo grub', and when you have a grub>_ prompt, you will have a 'Grub shell'.
```
sudo grub
```Then you ask grub for a list of partitions that contain a stage1 file for Grub, you do that by typing 'find /boot/grub/stage1' after the grub prompt. That will give you a list of partitions like (hd0,1), (hd1,0), (hd1,2) or something like that.
```
find /boot/grub/stage1
```Now you pick which partition is the one that has Open Suse's Grub which you want to have your MBR point to. Maybe (hd1,0) I guess? I might be wrong, it's just a guess, hopefully you will know for sure. So to focus the Grub shell's attention on partition (hd1,0), you type 'root (hd1,0)', or you could install Grub from any other partition in the list if you like.
```
root (hd1,0)
```Next you will install the IPL, (stage1) form Open Suse's or whatever grub you picked, to MBR like this 'setup (hd0)'. (hd0) is your first hard disk's MBR.
```
setup (hd0)
```That's it! :)
```
quit
``````
exit
```Then reboot and you can boot into OpenSuse. When you get into OpenSuse, just edit OpenSuse's menu.lst file with an option to boot Ubuntu. The best way to do that would be by pasting in two lines like this,
```
title        Ubuntu Edgy Eft
configfile  (hd0,1)/boot/grub/menu.lst
```Where: Your Ubuntu will be in your second partition in your first hard disk. If not you will have to change the partition numbers until it works. I am only guessing since I don't really know for sure what your partition numbers really are. 
If you need more help please post a copy of your fdisk output, 'sudo fdisk -lu' ```
sudo fdisk -lu
```

---

### Post by Jay_in_TN on 2007-05-06
Wow!
I had read that Ubuntu's support forum's were the best. I have to agree. Thank you so much for such an informative reply. Again---Wow!
I understood everything you said and should have no problem following your instructions. I am curious though--what is IPL?

I have a couple of other questions as well:
I am getting that "tty" error with Feisty, which appears to be related to IDE drivers or some other random hardware issue. So--if I install Edgy and then get the automatic updates, will it update to Feisty and then fail to load? Or--can I install Edgy and update to Feisty and then have Feisty work? I would rather use the new version, but there seems to be a known controller issue (or other hardware issue) with this release, causing this "failed to load tty" error (or however its phrased).

Thanks again for the very detailed response. That was just so very helpful.

For the record--I have used an older version of Mandrake, several versions of Linspire, Fedora and openSuSE. I really like openSuSE, but the ease of installation, speed of improvements/updates, and user support of Ubuntu makes it a real front-runner in the competition to be the leader of the free Linux OS race. I can't believe such a new version of Linux has become so powerful and popular so quickly. How totally cool. I work with technology in schools and I have to say that Ubuntu and Edubuntu will get my recommendation for low-cost alternatives to classrooms. Especially considering how well they perform on older, slower computers. My testbed computer is a Pentium III 733 with a half-gig of memory. Often, computer companies will donate their collection of older computers (in the 800mhz-1ghz range) to schools for free. Imagine a totally free computer lab of 6-8 computers in a single classroom, all running Edubuntu, at no cost whatsoever to the school system or the taxpayers. Wow. It really boggles the mind, huh? Although shared/network printing continues to kick my butt with the Linux distributions...

Anyway--thanks again for such a detailed response.

Jay in Tennessee

---

### Post by Herman on 2007-05-06
:)  The letters 'IPL' stand for 'Initial Program Loader', and it is pretty well an abbreviated way to say 'stage 1 of a boot loader'.

Boot loaders come in two or three pieces, (almost like an insect). 
If you have Windows, it's boot loader has an 'IPL' in the MBR (Master Boot Record) to make the MBR point to the Windows bootloader in the Windows partition, where the rest of the boot loader files are located.
When we install Ubuntu, most people think they 'install grub to MBR', but that's not really the case exactly. Only the the IPL for Grub, not all of Grub, is installed in the MBR.  Grub also has a stage 1_5 that goes into the first trcak of the hard disk which is normally empty. The rest of grub including stage2, which is the main part, is installed in the Ubuntu partition. The IPL makes the MBR point to Grub in the Ubuntu partition, and from there maybe you will decide to boot Ubuntu, or point to another partition and boot some other operating system.
The reason why boot loaders can't fit in the MBR is because the MBR is only one sector of 512 bytes in size. 446 bytes in the MBR are reserved for the IPL for a boot loader and there are four, sixteen byte entries reserved for our partition table, plus a two byte disk signature.  446 bytes is way too small an area for a whole boot loader to fit into.


The operating system that has it's IPL in the MBR will have it's boot loader controlling the booting, at least initially. So the IPL for a boot loader is basically just a pointer. Well, it's a little more complicated than that actually, but the more technically correct one tries to be, the more lengthy and boring the explanation becomes. :)

I'm not sure about your 'tty' error. I haven't experienced that one as far as I can remember. I would stick with Edgy for now maybe. I can't say for sure, but I agree there could be a risk that upgrading will give you the problem again. 

Shared network printing is another subject I don't know anything about. I read that Samba (networking) is good for that.

About Ubuntu for schools, I would think that schools wouldn't be the only places where it makes sense to use such a great operating system that can be  so easily installed in  as many computers as required for zero initial cost. I think Ubuntu is only just beginning to take off. Shortly it will be very widespread and students who have Linux skills will be in demand when they graduate. Lots of government departments and businesses will also see the sense in switching to Ubuntu. An operating system has to be able to be legally fully configurable and customizable (programmable) to suit the computer owner's wants and needs. As people become more and more computer literate and competent, they will want more of the freedom that only open source software can provide.  I think this is just the beginning for Ubuntu. In a few years time Ubuntu will be the dominating operating system world wide.

Regards, Herman :)

---

### Post by Jay_in_TN on 2007-05-07
Thanks again for your replies. Very informative and helpful.
Jay

---

### Post by PlatinumPlus on 2007-05-07
I understand the Alternate CD can allow you to install Ubuntu without having to install a bootloader kinda like with the Edubuntu CDs. Is it not possible to then edit the openSUSE grub / menu.lst and add an entry for Ubuntu?

---

### Post by Herman on 2007-05-07
Hello PlatinumPlus,
Yes, it would be possible to do that if someone knew they wanted to from the beginning and planned it that way.
A better idea would be to use the Alternate CD and install grub, (meaning the IPL for Grub), to the first sector of the Ubuntu partition.
Then you could add an entry to boot Ubuntu to Suse's Grub menu.

I think you can also do that with the 'Desktop' CD as well now, (install Grub's IPL to the Ubuntu partition instead of to MBR).

In any case, it doesn't hurt to install Ubuntu Grub's IPL to MBR. You can always just re-install an IPL for any other Grub or some other boot loader to the MBR later. The MBR is made out of the same material as the rest of the hard disk and you won't ever wear it out before the hard disk's bearings wear out. I write different IPLs to my MBR and bootsectors all the time and I am still using the same hard disks I have had for years. I experiment a lot testing different boot loaders and software for installing and uninstalling them. It doesn't really matter how you do it, as long as you end up with your system booting the way you want it to. :)

Regards, Herman :)

---

### Post by PlatinumPlus on 2007-05-07
> **Herman said:**
> 

I think you can also do that with the 'Desktop' CD as well now, (install Grub's IPL to the Ubuntu partition instead of to MBR).
Regards, Herman :)

Is there somewhere to verify this so that I can just wait for my shipment from shipit and not have to DL the alternate CD :)

---

### Post by Herman on 2007-05-07
It really isn't an important issue at all, but if you are worried about it, you should make a backup of the IPL area of your MBR just in case. Here is an illustrated step by step how-to on that, using the Ubuntu 'Desktop' LiveCD,
[**MBR Backup and Restore**]("http://users.bigpond.net.au/hermanzone/p13.htm#mbr_dd")
That will back up and restore an exact duplicate of your original MBR's IPL data for you, exactly as it was prior to the installation. That will be all you'd ever need. You probably wouldn't ever want to restore your old MBR code anyway once you have upgraded to Grub.

Regards, Herman :)

---

### Post by PlatinumPlus on 2007-05-08
I have a couple of machines with encryption software that loads from MBR. I once installed Zenwalk and I couldn't boot into WinXP after overwriting MBR. I will try the Backup and Restore if I fail to get a CD that allows me to install grub to partition.

---

### Post by Herman on 2007-05-08
Oh, I see, that's interesting. Exactly what do you mean when you say the encryption software loads from MBR? Which part of the MBR? You mean it's in the bootloader area of the MBR (first sector of your hard disk?), or do you really mean there is some software that installs somewhere in the first track of the hard disk, between the MBR and the start of the first partition?
It would be good to know that exactly because I may need to be aware of it if I ever want to help someone with a related problem that could potentially cause. 
What is the name of the encryption software and where did you get it from? 
Can you link me to the home page for it? I would like to learn all about that. 
Backing up the bootloader area of the MBR won't help if the encryption software is elsewhere in the first track of the hard disk.
Regards, Herman :)

---

### Post by PlatinumPlus on 2007-05-09
As soon as I boot my machine SafeBoot starts to run saying something like verifying code, then I get a screen to type my name and password. After that, I then get a Grub menu. If I install to MBR I go straight to the Grub menu and there is no verifying etc. but since it has encrypted my XP partition I can neither boot into XP nor view it from any Linux like I could before. This software seems to have no uninstall option otherwise I would have uninstalled ´updated´ MBR then reinstalled it.

I have installed Kubuntu 7.04 with the Alternate CD :guitar:

---

### Post by Herman on 2007-05-09
Thanks PlatinumPlus,
Safeboot, [http://www.safeboot.com/](http://www.safeboot.com/)
 I will look into the details how how that works and find out if it installs something in the MBR. It looks like nice software other than that. I'm only another Ubuntu user, not a member of any official team or anything like that, but I do try to help people with booting. It's a hobby of mine. Thanks for letting me know. Now I can help find out more about it so I can people better if they have concerns with how it interacts, (or fails to interact) with Grub.
Maybe I or someone else reading this can come up with a grub workaround to make Grub compatible with Safeboot, maybe we just need to learn a small modification to the boot entries for Windows to get Windows to boot through safeboot. I'll look into it.
Thanks again PlatinumPlus,

Regards, Herman :)

Great to read you have had a successfull install of Kubuntu 7.04 with the Alternate CD, Welcome to Ubuntu and congratulations! :)

---

### Post by PlatinumPlus on 2007-05-10
That will be good for future installs. 

I now have Pardus and Kubuntu installed along-side WinXP and I hope I won't have to deal with MBR for a while now :)  But I believe if I had lilo instead of grub I might not have been able to change my options with this encryption software installed.

Thanks Herman.

---

