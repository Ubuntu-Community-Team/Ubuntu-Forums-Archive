---
title: "Not able to boot after recent updates"
date: 2016-04-13
forum: Installation &amp; Upgrades
---

### Post by stuart_jones2 on 2016-04-13
Last night I was downloading updates for Ubuntu 14.04, (I work away and had not updated for 7 days), unfortunately during the process the screen went blank, after a short while I thought my machine had crashed and switched it off.
Unfortunately it now will not boot, it gets to the page in the attached photo.
I'm a _newbie_ with Ubuntu and do not know how to proceed
I appreciate any help

---

### Post by Impavidus on 2016-04-14
Try [Boot-Repair]("https://help.ubuntu.com/community/Boot-Repair"). There are many things that can go wrong after a reset during an upgrade, but it's unlikely Boot-Repair cannot give you a bootable system.

After repairing, you may need to go to "advanced options" in grub and boot an older kernel, maybe in recovery mode. That should give you a menu with an option to fix broken packages. On the other hand, maybe your system boots fine. Even then, check the package manager for any errors. In case of trouble, post the link Boot-Repair gives you here.

---

### Post by stuart_jones2 on 2016-04-14
Thanks Impavidus for your reply,
I downloaded Rufus 2.8 and used it to put Boot - repair on a USB pen as an ISO file, restarted my computer, got to the page as in the attached photograph and nothing happened.
My skill level with computers is low, especially Ubuntu. Did  I miss something in your instructions, or do I need to add a command at Grub??
Again many thanks for your response

---

### Post by Impavidus on 2016-04-15
Did you set your BIOS/UEFI to boot from USB? You have to hit or hold some key before the grub screen appears. Which one depends on your hardware.

Sometimes it's difficult to get a computer to boot from an usb pen. Using a different pen, a different socket on your computer or a different tool to put the .iso on the drive may help.

---

### Post by stuart_jones2 on 2016-04-15
Thanks again Impavidus for your reply,
How do you set your  BIOS/UEFI to boot from USB?
The screen in the attached photo appears at start up, it goes straight to that after pressing the on button on the computer, this is all I have access to, the text information and the flashing : after Grub

---

### Post by Impavidus on 2016-04-15
You may have to hold a key while switching the computer on, Esc, F2, Del, it varies. Or there may be a separate button you have to push with the computer switched off, instead of your normal power button. Every manufacturer does it his own way. If you tell us the make and model of your computer, somebody may know.

---

### Post by stuart_jones2 on 2016-04-15
It's a Packard Bell, Imedia S 64 bit.
When I bought it from PC world, I had them partition the hard drive, Ubuntu on one half, Windows on the other, it normally boots to Ubuntu after a short argument with windows

Thanks for your recent replies Impavidus,
 I'm on holiday from tomorrow and not back till next Thursday so will not be able to reply or do any work to my computer till then. But again thanks for your time

That is me back home, so I can now work on my computer again, any further thoughts on what I can do?

---

### Post by Impavidus on 2016-04-29
It seems that Packard Bell imedias usually need F1, F2 or delete to access the bios. You could try fixing things from that grub prompt (it must be possible to find a working kernel somehow), but I've got absolutely no experience with that. This link might be helpful: [https://help.ubuntu.com/community/Grub2/Troubleshooting](https://help.ubuntu.com/community/Grub2/Troubleshooting)

---

### Post by stuart_jones2 on 2016-04-29
Thanks again Impavidus,
the delete key worked and took me to the BIOS page, I set the Boot priority order to 
1st boot device (removable media)
the second option was Ubuntu, third was CD and fourth was LAN,
I restarted with the USB pen in, and the same story, just went to the page in the picture.
I had a look at the link, but to be honest I'm a bit afraid to/ not sure what to do, I really need someone to tell me exactly what  I should do, I don't want to do any more damage than I already have

---

### Post by Impavidus on 2016-04-29
The only time I used boot-repair I used an Ubuntu live disk and installed it in the live session. It was not the same disk I had used for installation of Ubuntu, but similar (a later version). How did you create the bootable usb? Some tools work more reliable than others. Also, some usb drives work better than others. Do you still have the live disk (dvd or usb) you used for installation? A live disk is a great tool to have in an emergency and your computer should be willing to boot that, as it has before.

---

### Post by stuart_jones2 on 2016-04-29
I used Rufus 2.8 to create the USB file
I don't have the installation disk, it was done for me at PC world, they partitioned the hard drive, with windows on one half and Ubuntu on the other. I don't like windows, but I need it for some programmes I have

---

### Post by Impavidus on 2016-04-30
UNetbootin seems popular. Maybe someone else can help you more creating a bootable usb. It's not my speciality. Consider creating a new thread for that, as I don't think many are still following this one and it's basically a separate issue.

---

### Post by stuart_jones2 on 2016-04-30
Thanks for your help and time Impavidus, will start a new post as suggested

---

### Post by kc1di on 2016-05-04
Best way here will be to use Live usb /Dvd and reinstall grub.  [here is a page ]("https://help.ubuntu.com/community/Grub2/Installing")telling how to do that.

---

### Post by stuart_jones2 on 2016-05-15
Thanks Kc1di for your reply,
I had a look at the page but unfortunately I don't understand/ not sure what to do, still can't get Boot Repair to load at start up.
At the page in the attached photo, I pressed the tab key and got the page in the new attached photo
Thanks again for your time, and sorry for being at bit slow.

I tried again, this time with a different USB pen and using UNetbooting and the boot repair started up. This was the url it gave me,
[http://paste.ubuntu.com/17254572/](http://paste.ubuntu.com/17254572/) 
I made some errors prior to this, and have 2 previous url's
After restarting the computer I pressed enter for ubuntu at the options page, but it just went to a dark purple screen and did nothing, I left it for half an hour, still nothing, turned it off and restarted, this time opened the advanced options menu, got a list that started with the following,
Ubuntu, with Linux 3.13.0-85-generic (recovery mode) and went down to
Ubuntu, with Linux 3.13.0-32- generic (recovery mode)
I appreciate your help so far, but what should I do next?

---

### Post by Impavidus on 2016-06-12
At least you got your grub menu back.

Go to the advanced options and try booting "Ubuntu, with Linux 3.13.0-83-generic (recovery mode)". It seems that the latest kernel is somehow broken, so try booting an older one. This will bring you to a menu with an option to "Repair broken packages". That may fix it.

Later, it may be a good idea to do some cleanup. You have a lot of old kernels. Keeping one old kernel is enough.

---

### Post by stuart_jones2 on 2016-06-12
Cheers Impavidus, success, back up and running on the proper half of my computer
Ran updates and re started, keeps coming up with the options page at start up, but this I can accept.
When you say about a clean up of old kernals, how do I do this? and which one should I keep? (It might have updated to 3.13.0-88)
Again many thanks, one happy bunny!!!

---

### Post by Impavidus on 2016-06-12
A simple```
sudo apt-get autoremove
``` may do the trick. Pay attention to the packages it wants to remove. Keep versions 3.13.0-85 and 3.13.0-88, if you have that one. Else keep one older, although that shouldn't matter too much. It will remove linux-image-[extra-]<some version> and linux-headers-<some version> or something like that. Removing the packages manually one by one works too, but will take a while.

As for the grub menu: Boot-Repair automatically makes the menu visible. On a fresh install with a single OS it's by default invisible. Having the menu visible makes it easier to fix the system when something breaks. If you wish, you can hide it again. Alternatively, you can change the timeout from 10 seconds to something shorter, like 3 seconds. You can do this by editing the file **/etc/default/grub** (use root permissions) and changing the appropriate options. It should be pretty clear. Run
```
sudo update-grub
```afterwards.

If everything is fine, could you mark this thread as solved? Thread tools (top of page) &#8594; mark as solved.

---

### Post by stuart_jones2 on 2016-06-12
Thanks again Impavidus,
the auto remove command didn't show the kernel versions, but did remove some other things, the update grub command showed the kernel versions, but I didn't see how you could delete them, individually or in batch??

---

### Post by MikeMecanic on 2016-06-12
Not bad for a newbie.  Let see how many Kernels you have? Will show you how to delete them after.  Please paste the result for this command line:    


```
dpkg --list | grep linux-image
```

---

### Post by stuart_jones2 on 2016-06-13
Thanks mike,```

stuart@stuart-ubuntu:~$ dpkg--list|grep linux-image
dpkg--list: command not found
stuart@stuart-ubuntu:~$ dpkg --list | grep linux-image
rc  linux-image-3.11.0-15-generic                         3.11.0-15.25~precise1                               amd64        Linux kernel image for version 3.11.0 on 64 bit x86 SMP
rc  linux-image-3.11.0-17-generic                         3.11.0-17.31~precise1                               amd64        Linux kernel image for version 3.11.0 on 64 bit x86 SMP
rc  linux-image-3.11.0-18-generic                         3.11.0-18.32~precise1                               amd64        Linux kernel image for version 3.11.0 on 64 bit x86 SMP
rc  linux-image-3.11.0-19-generic                         3.11.0-19.33~precise1                               amd64        Linux kernel image for version 3.11.0 on 64 bit x86 SMP
rc  linux-image-3.11.0-20-generic                         3.11.0-20.35~precise1                               amd64        Linux kernel image for version 3.11.0 on 64 bit x86 SMP
rc  linux-image-3.11.0-22-generic                         3.11.0-22.38~precise1                               amd64        Linux kernel image for version 3.11.0 on 64 bit x86 SMP
rc  linux-image-3.11.0-23-generic                         3.11.0-23.40~precise1                               amd64        Linux kernel image for version 3.11.0 on 64 bit x86 SMP
rc  linux-image-3.11.0-24-generic                         3.11.0-24.42~precise1                               amd64        Linux kernel image for version 3.11.0 on 64 bit x86 SMP
rc  linux-image-3.11.0-26-generic                         3.11.0-26.45~precise1                               amd64        Linux kernel image for version 3.11.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-32-generic                         3.13.0-32.57                                        amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-3.13.0-33-generic                         3.13.0-33.58                                        amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-34-generic                         3.13.0-34.60                                        amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-35-generic                         3.13.0-35.62                                        amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-36-generic                         3.13.0-36.63                                        amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-37-generic                         3.13.0-37.64                                        amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-39-generic                         3.13.0-39.66                                        amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-40-generic                         3.13.0-40.69                                        amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-43-generic                         3.13.0-43.72                                        amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-44-generic                         3.13.0-44.73                                        amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-45-generic                         3.13.0-45.74                                        amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-46-generic                         3.13.0-46.79                                        amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-48-generic                         3.13.0-48.80                                        amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-49-generic                         3.13.0-49.83                                        amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-52-generic                         3.13.0-52.86                                        amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-53-generic                         3.13.0-53.89                                        amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-54-generic                         3.13.0-54.91                                        amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-55-generic                         3.13.0-55.94                                        amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-57-generic                         3.13.0-57.95                                        amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-58-generic                         3.13.0-58.97                                        amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-59-generic                         3.13.0-59.98                                        amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-61-generic                         3.13.0-61.100                                       amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-62-generic                         3.13.0-62.102                                       amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-63-generic                         3.13.0-63.103                                       amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-65-generic                         3.13.0-65.106                                       amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-66-generic                         3.13.0-66.108                                       amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-67-generic                         3.13.0-67.110                                       amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-68-generic                         3.13.0-68.111                                       amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-71-generic                         3.13.0-71.114                                       amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-74-generic                         3.13.0-74.118                                       amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-76-generic                         3.13.0-76.120                                       amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-77-generic                         3.13.0-77.121                                       amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-79-generic                         3.13.0-79.123                                       amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-83-generic                         3.13.0-83.127                                       amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-85-generic                         3.13.0-85.129                                       amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-88-generic                         3.13.0-88.135                                       amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-extra-3.13.0-33-generic                   3.13.0-33.58                                        amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-34-generic                   3.13.0-34.60                                        amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-35-generic                   3.13.0-35.62                                        amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-36-generic                   3.13.0-36.63                                        amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-37-generic                   3.13.0-37.64                                        amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-39-generic                   3.13.0-39.66                                        amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-40-generic                   3.13.0-40.69                                        amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-43-generic                   3.13.0-43.72                                        amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-44-generic                   3.13.0-44.73                                        amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-45-generic                   3.13.0-45.74                                        amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-46-generic                   3.13.0-46.79                                        amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-48-generic                   3.13.0-48.80                                        amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-49-generic                   3.13.0-49.83                                        amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-52-generic                   3.13.0-52.86                                        amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-53-generic                   3.13.0-53.89                                        amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-54-generic                   3.13.0-54.91                                        amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-55-generic                   3.13.0-55.94                                        amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-57-generic                   3.13.0-57.95                                        amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-58-generic                   3.13.0-58.97                                        amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-59-generic                   3.13.0-59.98                                        amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-61-generic                   3.13.0-61.100                                       amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-62-generic                   3.13.0-62.102                                       amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-63-generic                   3.13.0-63.103                                       amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-65-generic                   3.13.0-65.106                                       amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-66-generic                   3.13.0-66.108                                       amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-67-generic                   3.13.0-67.110                                       amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-68-generic                   3.13.0-68.111                                       amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-71-generic                   3.13.0-71.114                                       amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-74-generic                   3.13.0-74.118                                       amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-76-generic                   3.13.0-76.120                                       amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-77-generic                   3.13.0-77.121                                       amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-79-generic                   3.13.0-79.123                                       amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-83-generic                   3.13.0-83.127                                       amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-85-generic                   3.13.0-85.129                                       amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-88-generic                   3.13.0-88.135                                       amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-generic                                   3.13.0.88.94                                        amd64        Generic Linux kernel image
ii  linux-image-generic-lts-saucy                         3.13.0.88.94                                        amd64        Generic Linux kernel image
ii  linux-image-generic-lts-trusty                        3.13.0.88.94                                        amd64        Generic Linux kernel image
stuart@stuart-ubuntu:~$
```

---

### Post by Impavidus on 2016-06-13
That's the list we need. Now, these few commands will do the trick:```
sudo apt-get remove --purge linux-image-3.11.0-{15,17,18,19,20,22,23,24,26}-generic
sudo apt-get remove --purge linux-image{,-extra}-3.13.0-{32..83}-generic
```I make some use of shell expansions to generate the names of the packages. That second command will request the removal of some packages that haven't been installed (or don't even exist), so it will give some warnings, but that shouldn't matter.

Alongside the linux-image packages, I expect some old linux-headers packages too. You can find them and remove them in the same way.

If you want to understand the shell expansions I used, run this:```
echo foo-{,bar-,boz-}{1..5}
```and you should understand most of it. The shell will expand the things in curly braces, using the alternatives separated by commas and all elements in the sequence indicated by the two dots, generate all combinations and supply those as arguments for the command.

---

### Post by stuart_jones2 on 2016-06-13
Thanks Impavidus, ran the 2 commands, the first one seemed to work, the second didn't
```
stuart@stuart-ubuntu:~$ sudo apt-get remove --purge linux-image-3.11.0-{15,17,18,19,20,22,23,24,26}-generic
[sudo] password for stuart: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED
  linux-image-3.11.0-15-generic* linux-image-3.11.0-17-generic*
  linux-image-3.11.0-18-generic* linux-image-3.11.0-19-generic*
  linux-image-3.11.0-20-generic* linux-image-3.11.0-22-generic*
  linux-image-3.11.0-23-generic* linux-image-3.11.0-24-generic*
  linux-image-3.11.0-26-generic*
0 to upgrade, 0 to newly install, 9 to remove and 14 not to upgrade.
After this operation, 0 B of additional disk space will be used.
Do you want to continue? [Y/n] y
(Reading database ... 1209386 files and directories currently installed.)
Removing linux-image-3.11.0-15-generic (3.11.0-15.25~precise1) ...
Purging configuration files for linux-image-3.11.0-15-generic (3.11.0-15.25~precise1) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.11.0-15-generic /boot/vmlinuz-3.11.0-15-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.11.0-15-generic /boot/vmlinuz-3.11.0-15-generic
Removing linux-image-3.11.0-17-generic (3.11.0-17.31~precise1) ...
Purging configuration files for linux-image-3.11.0-17-generic (3.11.0-17.31~precise1) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.11.0-17-generic /boot/vmlinuz-3.11.0-17-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.11.0-17-generic /boot/vmlinuz-3.11.0-17-generic
Removing linux-image-3.11.0-18-generic (3.11.0-18.32~precise1) ...
Purging configuration files for linux-image-3.11.0-18-generic (3.11.0-18.32~precise1) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.11.0-18-generic /boot/vmlinuz-3.11.0-18-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.11.0-18-generic /boot/vmlinuz-3.11.0-18-generic
Removing linux-image-3.11.0-19-generic (3.11.0-19.33~precise1) ...
Purging configuration files for linux-image-3.11.0-19-generic (3.11.0-19.33~precise1) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.11.0-19-generic /boot/vmlinuz-3.11.0-19-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.11.0-19-generic /boot/vmlinuz-3.11.0-19-generic
Removing linux-image-3.11.0-20-generic (3.11.0-20.35~precise1) ...
Purging configuration files for linux-image-3.11.0-20-generic (3.11.0-20.35~precise1) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.11.0-20-generic /boot/vmlinuz-3.11.0-20-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.11.0-20-generic /boot/vmlinuz-3.11.0-20-generic
Removing linux-image-3.11.0-22-generic (3.11.0-22.38~precise1) ...
Purging configuration files for linux-image-3.11.0-22-generic (3.11.0-22.38~precise1) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.11.0-22-generic /boot/vmlinuz-3.11.0-22-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.11.0-22-generic /boot/vmlinuz-3.11.0-22-generic
Removing linux-image-3.11.0-23-generic (3.11.0-23.40~precise1) ...
Purging configuration files for linux-image-3.11.0-23-generic (3.11.0-23.40~precise1) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.11.0-23-generic /boot/vmlinuz-3.11.0-23-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.11.0-23-generic /boot/vmlinuz-3.11.0-23-generic
Removing linux-image-3.11.0-24-generic (3.11.0-24.42~precise1) ...
Purging configuration files for linux-image-3.11.0-24-generic (3.11.0-24.42~precise1) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.11.0-24-generic /boot/vmlinuz-3.11.0-24-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.11.0-24-generic /boot/vmlinuz-3.11.0-24-generic
Removing linux-image-3.11.0-26-generic (3.11.0-26.45~precise1) ...
Purging configuration files for linux-image-3.11.0-26-generic (3.11.0-26.45~precise1) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.11.0-26-generic /boot/vmlinuz-3.11.0-26-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.11.0-26-generic /boot/vmlinuz-3.11.0-26-generic
stuart@stuart-ubuntu:~$ sudo apt-get remove --purge linux-image{,-extra}-{32..83}-generic
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package linux-image-32-generic
E: Unable to locate package linux-image-33-generic
E: Unable to locate package linux-image-34-generic
E: Unable to locate package linux-image-35-generic
E: Unable to locate package linux-image-36-generic
E: Unable to locate package linux-image-37-generic
E: Unable to locate package linux-image-38-generic
E: Unable to locate package linux-image-39-generic
E: Unable to locate package linux-image-40-generic
E: Unable to locate package linux-image-41-generic
E: Unable to locate package linux-image-42-generic
E: Unable to locate package linux-image-43-generic
E: Unable to locate package linux-image-44-generic
E: Unable to locate package linux-image-45-generic
E: Unable to locate package linux-image-46-generic
E: Unable to locate package linux-image-47-generic
E: Unable to locate package linux-image-48-generic
E: Unable to locate package linux-image-49-generic
E: Unable to locate package linux-image-50-generic
E: Unable to locate package linux-image-51-generic
E: Unable to locate package linux-image-52-generic
E: Unable to locate package linux-image-53-generic
E: Unable to locate package linux-image-54-generic
E: Unable to locate package linux-image-55-generic
E: Unable to locate package linux-image-56-generic
E: Unable to locate package linux-image-57-generic
E: Unable to locate package linux-image-58-generic
E: Unable to locate package linux-image-59-generic
E: Unable to locate package linux-image-60-generic
E: Unable to locate package linux-image-61-generic
E: Unable to locate package linux-image-62-generic
E: Unable to locate package linux-image-63-generic
E: Unable to locate package linux-image-64-generic
E: Unable to locate package linux-image-65-generic
E: Unable to locate package linux-image-66-generic
E: Unable to locate package linux-image-67-generic
E: Unable to locate package linux-image-68-generic
E: Unable to locate package linux-image-69-generic
E: Unable to locate package linux-image-70-generic
E: Unable to locate package linux-image-71-generic
E: Unable to locate package linux-image-72-generic
E: Unable to locate package linux-image-73-generic
E: Unable to locate package linux-image-74-generic
E: Unable to locate package linux-image-75-generic
E: Unable to locate package linux-image-76-generic
E: Unable to locate package linux-image-77-generic
E: Unable to locate package linux-image-78-generic
E: Unable to locate package linux-image-79-generic
E: Unable to locate package linux-image-80-generic
E: Unable to locate package linux-image-81-generic
E: Unable to locate package linux-image-82-generic
E: Unable to locate package linux-image-83-generic
E: Unable to locate package linux-image-extra-32-generic
E: Unable to locate package linux-image-extra-33-generic
E: Unable to locate package linux-image-extra-34-generic
E: Unable to locate package linux-image-extra-35-generic
E: Unable to locate package linux-image-extra-36-generic
E: Unable to locate package linux-image-extra-37-generic
E: Unable to locate package linux-image-extra-38-generic
E: Unable to locate package linux-image-extra-39-generic
E: Unable to locate package linux-image-extra-40-generic
E: Unable to locate package linux-image-extra-41-generic
E: Unable to locate package linux-image-extra-42-generic
E: Unable to locate package linux-image-extra-43-generic
E: Unable to locate package linux-image-extra-44-generic
E: Unable to locate package linux-image-extra-45-generic
E: Unable to locate package linux-image-extra-46-generic
E: Unable to locate package linux-image-extra-47-generic
E: Unable to locate package linux-image-extra-48-generic
E: Unable to locate package linux-image-extra-49-generic
E: Unable to locate package linux-image-extra-50-generic
E: Unable to locate package linux-image-extra-51-generic
E: Unable to locate package linux-image-extra-52-generic
E: Unable to locate package linux-image-extra-53-generic
E: Unable to locate package linux-image-extra-54-generic
E: Unable to locate package linux-image-extra-55-generic
E: Unable to locate package linux-image-extra-56-generic
E: Unable to locate package linux-image-extra-57-generic
E: Unable to locate package linux-image-extra-58-generic
E: Unable to locate package linux-image-extra-59-generic
E: Unable to locate package linux-image-extra-60-generic
E: Unable to locate package linux-image-extra-61-generic
E: Unable to locate package linux-image-extra-62-generic
E: Unable to locate package linux-image-extra-63-generic
E: Unable to locate package linux-image-extra-64-generic
E: Unable to locate package linux-image-extra-65-generic
E: Unable to locate package linux-image-extra-66-generic
E: Unable to locate package linux-image-extra-67-generic
E: Unable to locate package linux-image-extra-68-generic
E: Unable to locate package linux-image-extra-69-generic
E: Unable to locate package linux-image-extra-70-generic
E: Unable to locate package linux-image-extra-71-generic
E: Unable to locate package linux-image-extra-72-generic
E: Unable to locate package linux-image-extra-73-generic
E: Unable to locate package linux-image-extra-74-generic
E: Unable to locate package linux-image-extra-75-generic
E: Unable to locate package linux-image-extra-76-generic
E: Unable to locate package linux-image-extra-77-generic
E: Unable to locate package linux-image-extra-78-generic
E: Unable to locate package linux-image-extra-79-generic
E: Unable to locate package linux-image-extra-80-generic
E: Unable to locate package linux-image-extra-81-generic
E: Unable to locate package linux-image-extra-82-generic
E: Unable to locate package linux-image-extra-83-generic
stuart@stuart-ubuntu:~$ 
```

Did I miss type something?

---

### Post by Impavidus on 2016-06-13
I mistyped something, but fixed it in a minute. I hadn't expected you'd read it already. Try the fixed command above.

---

### Post by MikeMecanic on 2016-06-13
[FONT=FreeSans][SIZE=3]This is the Kernel you are using (that boots) and you do not want to delete this one :[/SIZE][/FONT]
   
 ```
[FONT=FreeSans][SIZE=3]uname -r[/SIZE][/FONT]
```
 
 
  [FONT=FreeSans][SIZE=3]You have a lot.  For the rc one try this command line:[/SIZE][/FONT]
  [FONT=FreeSans][SIZE=3]rc stand for Removal but config files remain in the system.[/SIZE][/FONT]
  
 
 ```
[FONT=FreeSans][SIZE=3][COLOR=#000000]dpkg -l | grep "^rc" | cut -d " " -f 3 | xargs sudo dpkg –purge[/COLOR][/SIZE][/FONT]
``` 
[LEFT] [COLOR=#000000][FONT=FreeSans][SIZE=3]And redo this one to see how many you have left::[/SIZE][/FONT][/COLOR][/LEFT]
 ```
[COLOR=#000000][FONT=FreeSans][SIZE=3]dpkg --list | grep linux-image[/SIZE][/FONT][/COLOR]
```
```
[COLOR=#000000][FONT=FreeSans][SIZE=3]sudo apt-get autoremove[/SIZE][/FONT][/COLOR]
```[LEFT] [COLOR=#000000][FONT=FreeSans][SIZE=3]You can also remove them one by one with this command line.  Just change the number each time.  Example: [/SIZE][/FONT][/COLOR] [/LEFT]
 ```
[COLOR=#000000][FONT=FreeSans][SIZE=3]sudo apt-get purge linux-headers-3.13.0-83 linux-headers-3.13.0-83-generic linux-image-3.13.0-83-generic[/SIZE][/FONT][/COLOR]
``` [LEFT] [COLOR=#000000][FONT=FreeSans][SIZE=3]
An alternative would be Synaptic.  Let see first how many you have left.[/SIZE][/FONT][/COLOR]
[/LEFT]
 [LEFT][[COLOR=#000000][FONT=FreeSans][SIZE=3]Cleaning old kernel in Synaptic[/SIZE][/FONT][/COLOR]]("https://askubuntu.com/questions/2793/how-do-i-remove-old-kernel-versions-to-clean-up-the-boot-menu")
[/LEFT]

---

### Post by stuart_jones2 on 2016-06-13
Thanks for your replies,
Impavidus, where is the new command? above?
Mike, sorry but what is the character in the first code screen after dpkg- ?? I have tried 1,i and l, I think it's an L but it shows up differently in the command box, just want to be sure

---

### Post by Impavidus on 2016-06-13
In post #25. I modified my post, fixing the command, but I didn't leave an edit summary as I modified it within a minute of posting and had not expected that you would have read it already.

---

### Post by stuart_jones2 on 2016-06-13
Same result I'm afraid,
```
stuart@stuart-ubuntu:~$ sudo apt-get remove --purge linux-image{,-extra}-3.13.0-{32..83}-generic
[sudo] password for stuart: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package linux-image-3.13.0-38-generic
E: Couldn't find any package by regex 'linux-image-3.13.0-38-generic'
E: Unable to locate package linux-image-3.13.0-42-generic
E: Couldn't find any package by regex 'linux-image-3.13.0-42-generic'
E: Unable to locate package linux-image-3.13.0-47-generic
E: Couldn't find any package by regex 'linux-image-3.13.0-47-generic'
E: Unable to locate package linux-image-3.13.0-50-generic
E: Couldn't find any package by regex 'linux-image-3.13.0-50-generic'
E: Unable to locate package linux-image-3.13.0-56-generic
E: Couldn't find any package by regex 'linux-image-3.13.0-56-generic'
E: Unable to locate package linux-image-3.13.0-60-generic
E: Couldn't find any package by regex 'linux-image-3.13.0-60-generic'
E: Unable to locate package linux-image-3.13.0-64-generic
E: Couldn't find any package by regex 'linux-image-3.13.0-64-generic'
E: Unable to locate package linux-image-3.13.0-69-generic
E: Couldn't find any package by regex 'linux-image-3.13.0-69-generic'
E: Unable to locate package linux-image-3.13.0-72-generic
E: Couldn't find any package by regex 'linux-image-3.13.0-72-generic'
E: Unable to locate package linux-image-3.13.0-75-generic
E: Couldn't find any package by regex 'linux-image-3.13.0-75-generic'
E: Unable to locate package linux-image-3.13.0-78-generic
E: Couldn't find any package by regex 'linux-image-3.13.0-78-generic'
E: Unable to locate package linux-image-3.13.0-80-generic
E: Couldn't find any package by regex 'linux-image-3.13.0-80-generic'
E: Unable to locate package linux-image-3.13.0-81-generic
E: Couldn't find any package by regex 'linux-image-3.13.0-81-generic'
E: Unable to locate package linux-image-3.13.0-82-generic
E: Couldn't find any package by regex 'linux-image-3.13.0-82-generic'
E: Unable to locate package linux-image-extra-3.13.0-38-generic
E: Couldn't find any package by regex 'linux-image-extra-3.13.0-38-generic'
E: Unable to locate package linux-image-extra-3.13.0-42-generic
E: Couldn't find any package by regex 'linux-image-extra-3.13.0-42-generic'
E: Unable to locate package linux-image-extra-3.13.0-47-generic
E: Couldn't find any package by regex 'linux-image-extra-3.13.0-47-generic'
E: Unable to locate package linux-image-extra-3.13.0-50-generic
E: Couldn't find any package by regex 'linux-image-extra-3.13.0-50-generic'
E: Unable to locate package linux-image-extra-3.13.0-56-generic
E: Couldn't find any package by regex 'linux-image-extra-3.13.0-56-generic'
E: Unable to locate package linux-image-extra-3.13.0-60-generic
E: Couldn't find any package by regex 'linux-image-extra-3.13.0-60-generic'
E: Unable to locate package linux-image-extra-3.13.0-64-generic
E: Couldn't find any package by regex 'linux-image-extra-3.13.0-64-generic'
E: Unable to locate package linux-image-extra-3.13.0-69-generic
E: Couldn't find any package by regex 'linux-image-extra-3.13.0-69-generic'
E: Unable to locate package linux-image-extra-3.13.0-72-generic
E: Couldn't find any package by regex 'linux-image-extra-3.13.0-72-generic'
E: Unable to locate package linux-image-extra-3.13.0-75-generic
E: Couldn't find any package by regex 'linux-image-extra-3.13.0-75-generic'
E: Unable to locate package linux-image-extra-3.13.0-78-generic
E: Couldn't find any package by regex 'linux-image-extra-3.13.0-78-generic'
E: Unable to locate package linux-image-extra-3.13.0-80-generic
E: Couldn't find any package by regex 'linux-image-extra-3.13.0-80-generic'
E: Unable to locate package linux-image-extra-3.13.0-81-generic
E: Couldn't find any package by regex 'linux-image-extra-3.13.0-81-generic'
E: Unable to locate package linux-image-extra-3.13.0-82-generic
E: Couldn't find any package by regex 'linux-image-extra-3.13.0-82-generic'
stuart@stuart-ubuntu:~$
```

---

### Post by MikeMecanic on 2016-06-13
> **stuart_jones2 said:**
> Thanks for your replies,
Mike, sorry but what is the character in the first code screen after dpkg- ?? I have tried 1,i and l, I think it's an L but it shows up differently in the command box, just want to be sure

We are using ```
 so that user(s) can copy/paste the command line to minimize error(s). 

Let's see if you have a boot partition now?

[CODE]sudo lsblk -o NAME,FSTYPE,SIZE,MOUNTPOINT,LABEL
```

---

### Post by stuart_jones2 on 2016-06-14
stuart@stuart-ubuntu:~$ sudo lsblk -o NAME,FSTYPE,SIZE,MOUNTPOINT,LABEL
[sudo] password for stuart: 
NAME   FSTYPE   SIZE MOUNTPOINT              LABEL
sda           931.5G                         
&#9500;&#9472;sda1 ntfs     400M                         RECOVERY
&#9500;&#9472;sda2 vfat     300M /boot/efi               ESP
&#9500;&#9472;sda3          128M                         
&#9500;&#9472;sda4 ntfs   456.1G                         Packard Bell
&#9500;&#9472;sda5 ext4   456.6G /                       
&#9492;&#9472;sda6 ntfs      18G                         Push Button Reset
sdb            14.9G                         
&#9492;&#9472;sdb1 vfat    14.9G /media/stuart/3238-2686 
sr0            1024M                         
stuart@stuart-ubuntu:~$

---

### Post by Impavidus on 2016-06-14
> **stuart_jones2 said:**
> Same result I'm afraid,

Not as bad as you think. It only mentioned the packages you don't have. I had expected it would just ignore those, but it seems it doesn't want to run. Have you checked all old 3.13 kernels are still there by running```
dpkg --list | grep linux-image
```If they are still there, try this to remove them:```
sudo apt-get purge linux-image-3.13.0-32-generic
sudo apt-get purge linux-image{,-extra}-3.13.0-{{33..37},39,40,{43..46},48,49,{52..55},{57..59},{61..63},{65..68},71,74,76,77,79,83}-generic
```I could come up with a fancy one-liner that does all at once, at the risk of making a typo that creates a lot of trouble.

Just to remember, this is some recommended cleanup to remove clutter and free disk space. Your system is already running fine. Once you've removed old kernels, you can check for old header packages with```
dpkg --list | grep linux-headers
```A similar at-get command as above can remove those.

---

### Post by stuart_jones2 on 2016-06-14
```
stuart@stuart-ubuntu:~$ dpkg --list | grep linux-image
ii  linux-image-3.13.0-32-generic                         3.13.0-32.57                                        amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-3.13.0-33-generic                         3.13.0-33.58                                        amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-34-generic                         3.13.0-34.60                                        amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-35-generic                         3.13.0-35.62                                        amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-36-generic                         3.13.0-36.63                                        amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-37-generic                         3.13.0-37.64                                        amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-39-generic                         3.13.0-39.66                                        amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-40-generic                         3.13.0-40.69                                        amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-43-generic                         3.13.0-43.72                                        amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-44-generic                         3.13.0-44.73                                        amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-45-generic                         3.13.0-45.74                                        amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-46-generic                         3.13.0-46.79                                        amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-48-generic                         3.13.0-48.80                                        amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-49-generic                         3.13.0-49.83                                        amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-52-generic                         3.13.0-52.86                                        amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-53-generic                         3.13.0-53.89                                        amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-54-generic                         3.13.0-54.91                                        amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-55-generic                         3.13.0-55.94                                        amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-57-generic                         3.13.0-57.95                                        amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-58-generic                         3.13.0-58.97                                        amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-59-generic                         3.13.0-59.98                                        amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-61-generic                         3.13.0-61.100                                       amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-62-generic                         3.13.0-62.102                                       amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-63-generic                         3.13.0-63.103                                       amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-65-generic                         3.13.0-65.106                                       amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-66-generic                         3.13.0-66.108                                       amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-67-generic                         3.13.0-67.110                                       amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-68-generic                         3.13.0-68.111                                       amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-71-generic                         3.13.0-71.114                                       amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-74-generic                         3.13.0-74.118                                       amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-76-generic                         3.13.0-76.120                                       amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-77-generic                         3.13.0-77.121                                       amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-79-generic                         3.13.0-79.123                                       amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-83-generic                         3.13.0-83.127                                       amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-85-generic                         3.13.0-85.129                                       amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-88-generic                         3.13.0-88.135                                       amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-extra-3.13.0-33-generic                   3.13.0-33.58                                        amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-34-generic                   3.13.0-34.60                                        amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-35-generic                   3.13.0-35.62                                        amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-36-generic                   3.13.0-36.63                                        amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-37-generic                   3.13.0-37.64                                        amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-39-generic                   3.13.0-39.66                                        amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-40-generic                   3.13.0-40.69                                        amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-43-generic                   3.13.0-43.72                                        amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-44-generic                   3.13.0-44.73                                        amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-45-generic                   3.13.0-45.74                                        amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-46-generic                   3.13.0-46.79                                        amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-48-generic                   3.13.0-48.80                                        amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-49-generic                   3.13.0-49.83                                        amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-52-generic                   3.13.0-52.86                                        amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-53-generic                   3.13.0-53.89                                        amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-54-generic                   3.13.0-54.91                                        amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-55-generic                   3.13.0-55.94                                        amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-57-generic                   3.13.0-57.95                                        amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-58-generic                   3.13.0-58.97                                        amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-59-generic                   3.13.0-59.98                                        amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-61-generic                   3.13.0-61.100                                       amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-62-generic                   3.13.0-62.102                                       amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-63-generic                   3.13.0-63.103                                       amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-65-generic                   3.13.0-65.106                                       amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-66-generic                   3.13.0-66.108                                       amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-67-generic                   3.13.0-67.110                                       amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-68-generic                   3.13.0-68.111                                       amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-71-generic                   3.13.0-71.114                                       amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-74-generic                   3.13.0-74.118                                       amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-76-generic                   3.13.0-76.120                                       amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-77-generic                   3.13.0-77.121                                       amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-79-generic                   3.13.0-79.123                                       amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-83-generic                   3.13.0-83.127                                       amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-85-generic                   3.13.0-85.129                                       amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-88-generic                   3.13.0-88.135                                       amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-generic                                   3.13.0.88.94                                        amd64        Generic Linux kernel image
ii  linux-image-generic-lts-saucy                         3.13.0.88.94                                        amd64        Generic Linux kernel image
ii  linux-image-generic-lts-trusty                        3.13.0.88.94                                        amd64        Generic Linux kernel image
```
```
stuart@stuart-ubuntu:~$ sudo apt-get purge linux-image-3.13.0-32-generic
[sudo] password for stuart: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  linux-headers-3.13.0-32 linux-headers-3.13.0-32-generic
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED
  linux-image-3.13.0-32-generic*
0 to upgrade, 0 to newly install, 1 to remove and 14 not to upgrade.
After this operation, 42.0 MB disk space will be freed.
Do you want to continue? [Y/n] y
(Reading database ... 1209386 files and directories currently installed.)
Removing linux-image-3.13.0-32-generic (3.13.0-32.57) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.13.0-32-generic /boot/vmlinuz-3.13.0-32-generic
update-initramfs: Deleting /boot/initrd.img-3.13.0-32-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.13.0-32-generic /boot/vmlinuz-3.13.0-32-generic
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-3.13.0-88-generic
Found initrd image: /boot/initrd.img-3.13.0-88-generic
Found linux image: /boot/vmlinuz-3.13.0-85-generic
Found initrd image: /boot/initrd.img-3.13.0-85-generic
Found linux image: /boot/vmlinuz-3.13.0-83-generic
Found initrd image: /boot/initrd.img-3.13.0-83-generic
Found linux image: /boot/vmlinuz-3.13.0-79-generic
Found initrd image: /boot/initrd.img-3.13.0-79-generic
Found linux image: /boot/vmlinuz-3.13.0-77-generic
Found initrd image: /boot/initrd.img-3.13.0-77-generic
Found linux image: /boot/vmlinuz-3.13.0-76-generic
Found initrd image: /boot/initrd.img-3.13.0-76-generic
Found linux image: /boot/vmlinuz-3.13.0-74-generic
Found initrd image: /boot/initrd.img-3.13.0-74-generic
Found linux image: /boot/vmlinuz-3.13.0-71-generic
Found initrd image: /boot/initrd.img-3.13.0-71-generic
Found linux image: /boot/vmlinuz-3.13.0-68-generic
Found initrd image: /boot/initrd.img-3.13.0-68-generic
Found linux image: /boot/vmlinuz-3.13.0-67-generic
Found initrd image: /boot/initrd.img-3.13.0-67-generic
Found linux image: /boot/vmlinuz-3.13.0-66-generic
Found initrd image: /boot/initrd.img-3.13.0-66-generic
Found linux image: /boot/vmlinuz-3.13.0-65-generic
Found initrd image: /boot/initrd.img-3.13.0-65-generic
Found linux image: /boot/vmlinuz-3.13.0-63-generic
Found initrd image: /boot/initrd.img-3.13.0-63-generic
Found linux image: /boot/vmlinuz-3.13.0-62-generic
Found initrd image: /boot/initrd.img-3.13.0-62-generic
Found linux image: /boot/vmlinuz-3.13.0-61-generic
Found initrd image: /boot/initrd.img-3.13.0-61-generic
Found linux image: /boot/vmlinuz-3.13.0-59-generic
Found initrd image: /boot/initrd.img-3.13.0-59-generic
Found linux image: /boot/vmlinuz-3.13.0-58-generic
Found initrd image: /boot/initrd.img-3.13.0-58-generic
Found linux image: /boot/vmlinuz-3.13.0-57-generic
Found initrd image: /boot/initrd.img-3.13.0-57-generic
Found linux image: /boot/vmlinuz-3.13.0-55-generic
Found initrd image: /boot/initrd.img-3.13.0-55-generic
Found linux image: /boot/vmlinuz-3.13.0-54-generic
Found initrd image: /boot/initrd.img-3.13.0-54-generic
Found linux image: /boot/vmlinuz-3.13.0-53-generic
Found initrd image: /boot/initrd.img-3.13.0-53-generic
Found linux image: /boot/vmlinuz-3.13.0-52-generic
Found initrd image: /boot/initrd.img-3.13.0-52-generic
Found linux image: /boot/vmlinuz-3.13.0-49-generic
Found initrd image: /boot/initrd.img-3.13.0-49-generic
Found linux image: /boot/vmlinuz-3.13.0-48-generic
Found initrd image: /boot/initrd.img-3.13.0-48-generic
Found linux image: /boot/vmlinuz-3.13.0-46-generic
Found initrd image: /boot/initrd.img-3.13.0-46-generic
Found linux image: /boot/vmlinuz-3.13.0-45-generic
Found initrd image: /boot/initrd.img-3.13.0-45-generic
Found linux image: /boot/vmlinuz-3.13.0-44-generic
Found initrd image: /boot/initrd.img-3.13.0-44-generic
Found linux image: /boot/vmlinuz-3.13.0-43-generic
Found initrd image: /boot/initrd.img-3.13.0-43-generic
Found linux image: /boot/vmlinuz-3.13.0-40-generic
Found initrd image: /boot/initrd.img-3.13.0-40-generic
Found linux image: /boot/vmlinuz-3.13.0-39-generic
Found initrd image: /boot/initrd.img-3.13.0-39-generic
Found linux image: /boot/vmlinuz-3.13.0-37-generic
Found initrd image: /boot/initrd.img-3.13.0-37-generic
Found linux image: /boot/vmlinuz-3.13.0-36-generic
Found initrd image: /boot/initrd.img-3.13.0-36-generic
Found linux image: /boot/vmlinuz-3.13.0-35-generic
Found initrd image: /boot/initrd.img-3.13.0-35-generic
Found linux image: /boot/vmlinuz-3.13.0-34-generic
Found initrd image: /boot/initrd.img-3.13.0-34-generic
Found Windows Boot Manager on /dev/sda2@/EFI/Microsoft/Boot/bootmgfw.efi
Adding boot menu entry for EFI firmware configuration
done
Purging configuration files for linux-image-3.13.0-32-generic (3.13.0-32.57) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.13.0-32-generic /boot/vmlinuz-3.13.0-32-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.13.0-32-generic /boot/vmlinuz-3.13.0-32-generic
stuart@stuart-ubuntu:~$ sudo apt-get purge linux-image{,-extra}-3.13.0-{33..37},39,40,{43..46},48,49,{52..55},{57..59},{61..63},{65..68},71,74,76,77,79,83}-generic
sudo: unable to execute /usr/bin/apt-get: Argument list too long
stuart@stuart-ubuntu:~$
```

Looks like there still there ??
```
stuart@stuart-ubuntu:~$ dpkg --list | grep linux-headers
ii  linux-headers-3.13.0-32                               3.13.0-32.57                                        all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-32-generic                       3.13.0-32.57                                        amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.13.0-34                               3.13.0-34.60                                        all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-34-generic                       3.13.0-34.60                                        amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.13.0-35                               3.13.0-35.62                                        all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-35-generic                       3.13.0-35.62                                        amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.13.0-36                               3.13.0-36.63                                        all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-36-generic                       3.13.0-36.63                                        amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.13.0-37                               3.13.0-37.64                                        all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-37-generic                       3.13.0-37.64                                        amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.13.0-39                               3.13.0-39.66                                        all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-39-generic                       3.13.0-39.66                                        amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.13.0-40                               3.13.0-40.69                                        all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-40-generic                       3.13.0-40.69                                        amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.13.0-43                               3.13.0-43.72                                        all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-43-generic                       3.13.0-43.72                                        amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.13.0-44                               3.13.0-44.73                                        all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-44-generic                       3.13.0-44.73                                        amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.13.0-45                               3.13.0-45.74                                        all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-45-generic                       3.13.0-45.74                                        amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.13.0-46                               3.13.0-46.79                                        all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-46-generic                       3.13.0-46.79                                        amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.13.0-48                               3.13.0-48.80                                        all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-48-generic                       3.13.0-48.80                                        amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.13.0-49                               3.13.0-49.83                                        all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-49-generic                       3.13.0-49.83                                        amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.13.0-52                               3.13.0-52.86                                        all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-52-generic                       3.13.0-52.86                                        amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.13.0-53                               3.13.0-53.89                                        all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-53-generic                       3.13.0-53.89                                        amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.13.0-54                               3.13.0-54.91                                        all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-54-generic                       3.13.0-54.91                                        amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.13.0-55                               3.13.0-55.94                                        all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-55-generic                       3.13.0-55.94                                        amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.13.0-57                               3.13.0-57.95                                        all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-57-generic                       3.13.0-57.95                                        amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.13.0-58                               3.13.0-58.97                                        all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-58-generic                       3.13.0-58.97                                        amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.13.0-59                               3.13.0-59.98                                        all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-59-generic                       3.13.0-59.98                                        amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.13.0-61                               3.13.0-61.100                                       all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-61-generic                       3.13.0-61.100                                       amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.13.0-62                               3.13.0-62.102                                       all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-62-generic                       3.13.0-62.102                                       amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.13.0-63                               3.13.0-63.103                                       all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-63-generic                       3.13.0-63.103                                       amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.13.0-65                               3.13.0-65.106                                       all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-65-generic                       3.13.0-65.106                                       amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.13.0-66                               3.13.0-66.108                                       all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-66-generic                       3.13.0-66.108                                       amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.13.0-67                               3.13.0-67.110                                       all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-67-generic                       3.13.0-67.110                                       amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.13.0-68                               3.13.0-68.111                                       all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-68-generic                       3.13.0-68.111                                       amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.13.0-71                               3.13.0-71.114                                       all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-71-generic                       3.13.0-71.114                                       amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.13.0-74                               3.13.0-74.118                                       all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-74-generic                       3.13.0-74.118                                       amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.13.0-76                               3.13.0-76.120                                       all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-76-generic                       3.13.0-76.120                                       amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.13.0-77                               3.13.0-77.121                                       all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-77-generic                       3.13.0-77.121                                       amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.13.0-79                               3.13.0-79.123                                       all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-79-generic                       3.13.0-79.123                                       amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.13.0-83                               3.13.0-83.127                                       all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-83-generic                       3.13.0-83.127                                       amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.13.0-85                               3.13.0-85.129                                       all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-85-generic                       3.13.0-85.129                                       amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.13.0-88                               3.13.0-88.135                                       all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-88-generic                       3.13.0-88.135                                       amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-generic                                 3.13.0.88.94                                        amd64        Generic Linux kernel headers
ii  linux-headers-generic-lts-saucy                       3.13.0.88.94                                        amd64        Generic Linux kernel headers
ii  linux-headers-generic-lts-trusty                      3.13.0.88.94                                        amd64        Generic Linux kernel headers
stuart@stuart-ubuntu:~$
```

---

### Post by Impavidus on 2016-06-14
> **stuart_jones2 said:**
> ```

sudo: unable to execute /usr/bin/apt-get: Argument list too long
stuart@stuart-ubuntu:~$
```

I haven't seen that one in a long time.

Let's just cut it into more manageable pieces:```
sudo apt-get purge linux-image{,-extra}-3.13.0-33-generic
sudo apt-get purge linux-image{,-extra}-3.13.0-34-generic
sudo apt-get purge linux-image{,-extra}-3.13.0-35-generic
sudo apt-get purge linux-image{,-extra}-3.13.0-36-generic
sudo apt-get purge linux-image{,-extra}-3.13.0-37-generic
sudo apt-get purge linux-image{,-extra}-3.13.0-39-generic
sudo apt-get purge linux-image{,-extra}-3.13.0-40-generic
sudo apt-get purge linux-image{,-extra}-3.13.0-43-generic
sudo apt-get purge linux-image{,-extra}-3.13.0-44-generic
sudo apt-get purge linux-image{,-extra}-3.13.0-45-generic
sudo apt-get purge linux-image{,-extra}-3.13.0-46-generic
sudo apt-get purge linux-image{,-extra}-3.13.0-48-generic
sudo apt-get purge linux-image{,-extra}-3.13.0-49-generic
sudo apt-get purge linux-image{,-extra}-3.13.0-52-generic
sudo apt-get purge linux-image{,-extra}-3.13.0-53-generic
sudo apt-get purge linux-image{,-extra}-3.13.0-54-generic
sudo apt-get purge linux-image{,-extra}-3.13.0-55-generic
sudo apt-get purge linux-image{,-extra}-3.13.0-57-generic
sudo apt-get purge linux-image{,-extra}-3.13.0-58-generic
sudo apt-get purge linux-image{,-extra}-3.13.0-59-generic
sudo apt-get purge linux-image{,-extra}-3.13.0-61-generic
sudo apt-get purge linux-image{,-extra}-3.13.0-62-generic
sudo apt-get purge linux-image{,-extra}-3.13.0-63-generic
sudo apt-get purge linux-image{,-extra}-3.13.0-65-generic
sudo apt-get purge linux-image{,-extra}-3.13.0-66-generic
sudo apt-get purge linux-image{,-extra}-3.13.0-67-generic
sudo apt-get purge linux-image{,-extra}-3.13.0-68-generic
sudo apt-get purge linux-image{,-extra}-3.13.0-71-generic
sudo apt-get purge linux-image{,-extra}-3.13.0-74-generic
sudo apt-get purge linux-image{,-extra}-3.13.0-76-generic
sudo apt-get purge linux-image{,-extra}-3.13.0-77-generic
sudo apt-get purge linux-image{,-extra}-3.13.0-79-generic
sudo apt-get purge linux-image{,-extra}-3.13.0-83-generic
```Creating that list of commands only took a handful of seconds.

You can remove those old headers packages with```
sudo apt-get purge linux-headers-3.13.0-32{,-generic}
sudo apt-get purge linux-headers-3.13.0-34{,-generic}
sudo apt-get purge linux-headers-3.13.0-35{,-generic}
sudo apt-get purge linux-headers-3.13.0-36{,-generic}
sudo apt-get purge linux-headers-3.13.0-37{,-generic}
sudo apt-get purge linux-headers-3.13.0-39{,-generic}
sudo apt-get purge linux-headers-3.13.0-40{,-generic}
sudo apt-get purge linux-headers-3.13.0-43{,-generic}
sudo apt-get purge linux-headers-3.13.0-44{,-generic}
sudo apt-get purge linux-headers-3.13.0-45{,-generic}
sudo apt-get purge linux-headers-3.13.0-46{,-generic}
sudo apt-get purge linux-headers-3.13.0-48{,-generic}
sudo apt-get purge linux-headers-3.13.0-49{,-generic}
sudo apt-get purge linux-headers-3.13.0-52{,-generic}
sudo apt-get purge linux-headers-3.13.0-53{,-generic}
sudo apt-get purge linux-headers-3.13.0-54{,-generic}
sudo apt-get purge linux-headers-3.13.0-55{,-generic}
sudo apt-get purge linux-headers-3.13.0-57{,-generic}
sudo apt-get purge linux-headers-3.13.0-58{,-generic}
sudo apt-get purge linux-headers-3.13.0-59{,-generic}
sudo apt-get purge linux-headers-3.13.0-61{,-generic}
sudo apt-get purge linux-headers-3.13.0-62{,-generic}
sudo apt-get purge linux-headers-3.13.0-63{,-generic}
sudo apt-get purge linux-headers-3.13.0-65{,-generic}
sudo apt-get purge linux-headers-3.13.0-66{,-generic}
sudo apt-get purge linux-headers-3.13.0-67{,-generic}
sudo apt-get purge linux-headers-3.13.0-68{,-generic}
sudo apt-get purge linux-headers-3.13.0-71{,-generic}
sudo apt-get purge linux-headers-3.13.0-74{,-generic}
sudo apt-get purge linux-headers-3.13.0-76{,-generic}
sudo apt-get purge linux-headers-3.13.0-77{,-generic}
sudo apt-get purge linux-headers-3.13.0-79{,-generic}
sudo apt-get purge linux-headers-3.13.0-83{,-generic}
```
I'm sure there's a more elegant way, but finding that may take more time than this simple repetition. Sometimes dumb manual work is the easiest way to solve a problem.

---

### Post by stuart_jones2 on 2016-06-14
Thanks Impavidus, did the first 2 on the list, 1st went ok, second seemed to do a lot more, thought I would check with you that this was ok? before carrying on,
```
stuart@stuart-ubuntu:~$ sudo apt-get purge linux-image{,-extra}-3.13.0-33-generic
[sudo] password for stuart: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  linux-headers-3.13.0-32 linux-headers-3.13.0-32-generic
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED
  linux-image-3.13.0-33-generic* linux-image-extra-3.13.0-33-generic*
0 to upgrade, 0 to newly install, 2 to remove and 14 not to upgrade.
After this operation, 0 B of additional disk space will be used.
Do you want to continue? [Y/n] y
(Reading database ... 1208815 files and directories currently installed.)
Removing linux-image-3.13.0-33-generic (3.13.0-33.58) ...
Purging configuration files for linux-image-3.13.0-33-generic (3.13.0-33.58) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.13.0-33-generic /boot/vmlinuz-3.13.0-33-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.13.0-33-generic /boot/vmlinuz-3.13.0-33-generic
Removing linux-image-extra-3.13.0-33-generic (3.13.0-33.58) ...
Purging configuration files for linux-image-extra-3.13.0-33-generic (3.13.0-33.58) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.13.0-33-generic /boot/vmlinuz-3.13.0-33-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.13.0-33-generic /boot/vmlinuz-3.13.0-33-generic
stuart@stuart-ubuntu:~$ sudo apt-get purge linux-image{,-extra}-3.13.0-34-generic
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  linux-headers-3.13.0-32 linux-headers-3.13.0-32-generic
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED
  linux-image-3.13.0-34-generic* linux-image-extra-3.13.0-34-generic*
  linux-signed-image-3.13.0-34-generic*
0 to upgrade, 0 to newly install, 3 to remove and 14 not to upgrade.
After this operation, 194 MB disk space will be freed.
Do you want to continue? [Y/n] y
(Reading database ... 1208815 files and directories currently installed.)
Removing linux-signed-image-3.13.0-34-generic (3.13.0-34.60) ...
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-3.13.0-88-generic
Found initrd image: /boot/initrd.img-3.13.0-88-generic
Found linux image: /boot/vmlinuz-3.13.0-85-generic
Found initrd image: /boot/initrd.img-3.13.0-85-generic
Found linux image: /boot/vmlinuz-3.13.0-83-generic
Found initrd image: /boot/initrd.img-3.13.0-83-generic
Found linux image: /boot/vmlinuz-3.13.0-79-generic
Found initrd image: /boot/initrd.img-3.13.0-79-generic
Found linux image: /boot/vmlinuz-3.13.0-77-generic
Found initrd image: /boot/initrd.img-3.13.0-77-generic
Found linux image: /boot/vmlinuz-3.13.0-76-generic
Found initrd image: /boot/initrd.img-3.13.0-76-generic
Found linux image: /boot/vmlinuz-3.13.0-74-generic
Found initrd image: /boot/initrd.img-3.13.0-74-generic
Found linux image: /boot/vmlinuz-3.13.0-71-generic
Found initrd image: /boot/initrd.img-3.13.0-71-generic
Found linux image: /boot/vmlinuz-3.13.0-68-generic
Found initrd image: /boot/initrd.img-3.13.0-68-generic
Found linux image: /boot/vmlinuz-3.13.0-67-generic
Found initrd image: /boot/initrd.img-3.13.0-67-generic
Found linux image: /boot/vmlinuz-3.13.0-66-generic
Found initrd image: /boot/initrd.img-3.13.0-66-generic
Found linux image: /boot/vmlinuz-3.13.0-65-generic
Found initrd image: /boot/initrd.img-3.13.0-65-generic
Found linux image: /boot/vmlinuz-3.13.0-63-generic
Found initrd image: /boot/initrd.img-3.13.0-63-generic
Found linux image: /boot/vmlinuz-3.13.0-62-generic
Found initrd image: /boot/initrd.img-3.13.0-62-generic
Found linux image: /boot/vmlinuz-3.13.0-61-generic
Found initrd image: /boot/initrd.img-3.13.0-61-generic
Found linux image: /boot/vmlinuz-3.13.0-59-generic
Found initrd image: /boot/initrd.img-3.13.0-59-generic
Found linux image: /boot/vmlinuz-3.13.0-58-generic
Found initrd image: /boot/initrd.img-3.13.0-58-generic
Found linux image: /boot/vmlinuz-3.13.0-57-generic
Found initrd image: /boot/initrd.img-3.13.0-57-generic
Found linux image: /boot/vmlinuz-3.13.0-55-generic
Found initrd image: /boot/initrd.img-3.13.0-55-generic
Found linux image: /boot/vmlinuz-3.13.0-54-generic
Found initrd image: /boot/initrd.img-3.13.0-54-generic
Found linux image: /boot/vmlinuz-3.13.0-53-generic
Found initrd image: /boot/initrd.img-3.13.0-53-generic
Found linux image: /boot/vmlinuz-3.13.0-52-generic
Found initrd image: /boot/initrd.img-3.13.0-52-generic
Found linux image: /boot/vmlinuz-3.13.0-49-generic
Found initrd image: /boot/initrd.img-3.13.0-49-generic
Found linux image: /boot/vmlinuz-3.13.0-48-generic
Found initrd image: /boot/initrd.img-3.13.0-48-generic
Found linux image: /boot/vmlinuz-3.13.0-46-generic
Found initrd image: /boot/initrd.img-3.13.0-46-generic
Found linux image: /boot/vmlinuz-3.13.0-45-generic
Found initrd image: /boot/initrd.img-3.13.0-45-generic
Found linux image: /boot/vmlinuz-3.13.0-44-generic
Found initrd image: /boot/initrd.img-3.13.0-44-generic
Found linux image: /boot/vmlinuz-3.13.0-43-generic
Found initrd image: /boot/initrd.img-3.13.0-43-generic
Found linux image: /boot/vmlinuz-3.13.0-40-generic
Found initrd image: /boot/initrd.img-3.13.0-40-generic
Found linux image: /boot/vmlinuz-3.13.0-39-generic
Found initrd image: /boot/initrd.img-3.13.0-39-generic
Found linux image: /boot/vmlinuz-3.13.0-37-generic
Found initrd image: /boot/initrd.img-3.13.0-37-generic
Found linux image: /boot/vmlinuz-3.13.0-36-generic
Found initrd image: /boot/initrd.img-3.13.0-36-generic
Found linux image: /boot/vmlinuz-3.13.0-35-generic
Found initrd image: /boot/initrd.img-3.13.0-35-generic
Found linux image: /boot/vmlinuz-3.13.0-34-generic
Found initrd image: /boot/initrd.img-3.13.0-34-generic
Found Windows Boot Manager on /dev/sda2@/EFI/Microsoft/Boot/bootmgfw.efi
Adding boot menu entry for EFI firmware configuration
done
Purging configuration files for linux-signed-image-3.13.0-34-generic (3.13.0-34.60) ...
Removing linux-image-extra-3.13.0-34-generic (3.13.0-34.60) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.13.0-34-generic /boot/vmlinuz-3.13.0-34-generic
update-initramfs: Deleting /boot/initrd.img-3.13.0-34-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.13.0-34-generic /boot/vmlinuz-3.13.0-34-generic
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-3.13.0-88-generic
Found initrd image: /boot/initrd.img-3.13.0-88-generic
Found linux image: /boot/vmlinuz-3.13.0-85-generic
Found initrd image: /boot/initrd.img-3.13.0-85-generic
Found linux image: /boot/vmlinuz-3.13.0-83-generic
Found initrd image: /boot/initrd.img-3.13.0-83-generic
Found linux image: /boot/vmlinuz-3.13.0-79-generic
Found initrd image: /boot/initrd.img-3.13.0-79-generic
Found linux image: /boot/vmlinuz-3.13.0-77-generic
Found initrd image: /boot/initrd.img-3.13.0-77-generic
Found linux image: /boot/vmlinuz-3.13.0-76-generic
Found initrd image: /boot/initrd.img-3.13.0-76-generic
Found linux image: /boot/vmlinuz-3.13.0-74-generic
Found initrd image: /boot/initrd.img-3.13.0-74-generic
Found linux image: /boot/vmlinuz-3.13.0-71-generic
Found initrd image: /boot/initrd.img-3.13.0-71-generic
Found linux image: /boot/vmlinuz-3.13.0-68-generic
Found initrd image: /boot/initrd.img-3.13.0-68-generic
Found linux image: /boot/vmlinuz-3.13.0-67-generic
Found initrd image: /boot/initrd.img-3.13.0-67-generic
Found linux image: /boot/vmlinuz-3.13.0-66-generic
Found initrd image: /boot/initrd.img-3.13.0-66-generic
Found linux image: /boot/vmlinuz-3.13.0-65-generic
Found initrd image: /boot/initrd.img-3.13.0-65-generic
Found linux image: /boot/vmlinuz-3.13.0-63-generic
Found initrd image: /boot/initrd.img-3.13.0-63-generic
Found linux image: /boot/vmlinuz-3.13.0-62-generic
Found initrd image: /boot/initrd.img-3.13.0-62-generic
Found linux image: /boot/vmlinuz-3.13.0-61-generic
Found initrd image: /boot/initrd.img-3.13.0-61-generic
Found linux image: /boot/vmlinuz-3.13.0-59-generic
Found initrd image: /boot/initrd.img-3.13.0-59-generic
Found linux image: /boot/vmlinuz-3.13.0-58-generic
Found initrd image: /boot/initrd.img-3.13.0-58-generic
Found linux image: /boot/vmlinuz-3.13.0-57-generic
Found initrd image: /boot/initrd.img-3.13.0-57-generic
Found linux image: /boot/vmlinuz-3.13.0-55-generic
Found initrd image: /boot/initrd.img-3.13.0-55-generic
Found linux image: /boot/vmlinuz-3.13.0-54-generic
Found initrd image: /boot/initrd.img-3.13.0-54-generic
Found linux image: /boot/vmlinuz-3.13.0-53-generic
Found initrd image: /boot/initrd.img-3.13.0-53-generic
Found linux image: /boot/vmlinuz-3.13.0-52-generic
Found initrd image: /boot/initrd.img-3.13.0-52-generic
Found linux image: /boot/vmlinuz-3.13.0-49-generic
Found initrd image: /boot/initrd.img-3.13.0-49-generic
Found linux image: /boot/vmlinuz-3.13.0-48-generic
Found initrd image: /boot/initrd.img-3.13.0-48-generic
Found linux image: /boot/vmlinuz-3.13.0-46-generic
Found initrd image: /boot/initrd.img-3.13.0-46-generic
Found linux image: /boot/vmlinuz-3.13.0-45-generic
Found initrd image: /boot/initrd.img-3.13.0-45-generic
Found linux image: /boot/vmlinuz-3.13.0-44-generic
Found initrd image: /boot/initrd.img-3.13.0-44-generic
Found linux image: /boot/vmlinuz-3.13.0-43-generic
Found initrd image: /boot/initrd.img-3.13.0-43-generic
Found linux image: /boot/vmlinuz-3.13.0-40-generic
Found initrd image: /boot/initrd.img-3.13.0-40-generic
Found linux image: /boot/vmlinuz-3.13.0-39-generic
Found initrd image: /boot/initrd.img-3.13.0-39-generic
Found linux image: /boot/vmlinuz-3.13.0-37-generic
Found initrd image: /boot/initrd.img-3.13.0-37-generic
Found linux image: /boot/vmlinuz-3.13.0-36-generic
Found initrd image: /boot/initrd.img-3.13.0-36-generic
Found linux image: /boot/vmlinuz-3.13.0-35-generic
Found initrd image: /boot/initrd.img-3.13.0-35-generic
Found linux image: /boot/vmlinuz-3.13.0-34-generic
Found Windows Boot Manager on /dev/sda2@/EFI/Microsoft/Boot/bootmgfw.efi
Adding boot menu entry for EFI firmware configuration
done
Purging configuration files for linux-image-extra-3.13.0-34-generic (3.13.0-34.60) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.13.0-34-generic /boot/vmlinuz-3.13.0-34-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.13.0-34-generic /boot/vmlinuz-3.13.0-34-generic
Removing linux-image-3.13.0-34-generic (3.13.0-34.60) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.13.0-34-generic /boot/vmlinuz-3.13.0-34-generic
update-initramfs: Deleting /boot/initrd.img-3.13.0-34-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.13.0-34-generic /boot/vmlinuz-3.13.0-34-generic
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-3.13.0-88-generic
Found initrd image: /boot/initrd.img-3.13.0-88-generic
Found linux image: /boot/vmlinuz-3.13.0-85-generic
Found initrd image: /boot/initrd.img-3.13.0-85-generic
Found linux image: /boot/vmlinuz-3.13.0-83-generic
Found initrd image: /boot/initrd.img-3.13.0-83-generic
Found linux image: /boot/vmlinuz-3.13.0-79-generic
Found initrd image: /boot/initrd.img-3.13.0-79-generic
Found linux image: /boot/vmlinuz-3.13.0-77-generic
Found initrd image: /boot/initrd.img-3.13.0-77-generic
Found linux image: /boot/vmlinuz-3.13.0-76-generic
Found initrd image: /boot/initrd.img-3.13.0-76-generic
Found linux image: /boot/vmlinuz-3.13.0-74-generic
Found initrd image: /boot/initrd.img-3.13.0-74-generic
Found linux image: /boot/vmlinuz-3.13.0-71-generic
Found initrd image: /boot/initrd.img-3.13.0-71-generic
Found linux image: /boot/vmlinuz-3.13.0-68-generic
Found initrd image: /boot/initrd.img-3.13.0-68-generic
Found linux image: /boot/vmlinuz-3.13.0-67-generic
Found initrd image: /boot/initrd.img-3.13.0-67-generic
Found linux image: /boot/vmlinuz-3.13.0-66-generic
Found initrd image: /boot/initrd.img-3.13.0-66-generic
Found linux image: /boot/vmlinuz-3.13.0-65-generic
Found initrd image: /boot/initrd.img-3.13.0-65-generic
Found linux image: /boot/vmlinuz-3.13.0-63-generic
Found initrd image: /boot/initrd.img-3.13.0-63-generic
Found linux image: /boot/vmlinuz-3.13.0-62-generic
Found initrd image: /boot/initrd.img-3.13.0-62-generic
Found linux image: /boot/vmlinuz-3.13.0-61-generic
Found initrd image: /boot/initrd.img-3.13.0-61-generic
Found linux image: /boot/vmlinuz-3.13.0-59-generic
Found initrd image: /boot/initrd.img-3.13.0-59-generic
Found linux image: /boot/vmlinuz-3.13.0-58-generic
Found initrd image: /boot/initrd.img-3.13.0-58-generic
Found linux image: /boot/vmlinuz-3.13.0-57-generic
Found initrd image: /boot/initrd.img-3.13.0-57-generic
Found linux image: /boot/vmlinuz-3.13.0-55-generic
Found initrd image: /boot/initrd.img-3.13.0-55-generic
Found linux image: /boot/vmlinuz-3.13.0-54-generic
Found initrd image: /boot/initrd.img-3.13.0-54-generic
Found linux image: /boot/vmlinuz-3.13.0-53-generic
Found initrd image: /boot/initrd.img-3.13.0-53-generic
Found linux image: /boot/vmlinuz-3.13.0-52-generic
Found initrd image: /boot/initrd.img-3.13.0-52-generic
Found linux image: /boot/vmlinuz-3.13.0-49-generic
Found initrd image: /boot/initrd.img-3.13.0-49-generic
Found linux image: /boot/vmlinuz-3.13.0-48-generic
Found initrd image: /boot/initrd.img-3.13.0-48-generic
Found linux image: /boot/vmlinuz-3.13.0-46-generic
Found initrd image: /boot/initrd.img-3.13.0-46-generic
Found linux image: /boot/vmlinuz-3.13.0-45-generic
Found initrd image: /boot/initrd.img-3.13.0-45-generic
Found linux image: /boot/vmlinuz-3.13.0-44-generic
Found initrd image: /boot/initrd.img-3.13.0-44-generic
Found linux image: /boot/vmlinuz-3.13.0-43-generic
Found initrd image: /boot/initrd.img-3.13.0-43-generic
Found linux image: /boot/vmlinuz-3.13.0-40-generic
Found initrd image: /boot/initrd.img-3.13.0-40-generic
Found linux image: /boot/vmlinuz-3.13.0-39-generic
Found initrd image: /boot/initrd.img-3.13.0-39-generic
Found linux image: /boot/vmlinuz-3.13.0-37-generic
Found initrd image: /boot/initrd.img-3.13.0-37-generic
Found linux image: /boot/vmlinuz-3.13.0-36-generic
Found initrd image: /boot/initrd.img-3.13.0-36-generic
Found linux image: /boot/vmlinuz-3.13.0-35-generic
Found initrd image: /boot/initrd.img-3.13.0-35-generic
Found Windows Boot Manager on /dev/sda2@/EFI/Microsoft/Boot/bootmgfw.efi
Adding boot menu entry for EFI firmware configuration
done
Purging configuration files for linux-image-3.13.0-34-generic (3.13.0-34.60) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.13.0-34-generic /boot/vmlinuz-3.13.0-34-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.13.0-34-generic /boot/vmlinuz-3.13.0-34-generic
stuart@stuart-ubuntu:~$
```

---

### Post by MikeMecanic on 2016-06-15
> **stuart_jones2 said:**
> Thanks Impavidus, did the first 2 on the list, 1st went ok, second seemed to do a lot more, thought I would check with you that this was ok? before carrying on,
```
stuart@stuart-ubuntu:~$ sudo apt-get purge linux-image{,-extra}-3.13.0-33-generic
[sudo] password for stuart: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  linux-headers-3.13.0-32 linux-headers-3.13.0-32-generic
[COLOR=#ff0000][B]Use 'apt-get autoremove' to remove them.
[/B][/COLOR]stuart@stuart-ubuntu:~$
```
I[FONT=FreeSans][SIZE=2] see that you were able to removed the rc ones.   [/SIZE][/FONT] 
 [FONT=FreeSans][SIZE=2]You must run **sudo apt-get autoremove** each time.   Forward!  Keep on cleaning up.[/SIZE][/FONT]
 [FONT=FreeSans][SIZE=2]You don&#8217;t have to re-type the command line each time.  Click the last line in the terminal and get the last command line with the up arrow, then change the digits only.[/SIZE][/FONT]
 [FONT=FreeSans][SIZE=2]Try this to remove more junks:[/SIZE][/FONT]
```
[FONT=FreeSans][SIZE=2]rm -v -f ~/.cache/thumbnails/*/*.png ~/.thumbnails/*/*.png[/SIZE][/FONT]
``` 
 ```
[FONT=FreeSans][SIZE=2]rm -v -f ~/.cache/thumbnails/*/*/*.png ~/.thumbnails/*/*/*.png[/SIZE][/FONT]
``` 
 ```
[FONT=FreeSans][SIZE=2]sync; echo 3 | sudo tee /proc/sys/vm/drop_caches[/SIZE][/FONT]
``` 
 [FONT=FreeSans][SIZE=2]Is this one works so that headers and image can be delete at the same time?  [/SIZE][/FONT] 
 ```
[COLOR=#000000][FONT=FreeSans][SIZE=2]sudo apt-get purge linux-headers-3.13.0-83 linux-headers-3.13.0-83-generic linux-image-3.13.0-83-generic[/SIZE][/FONT][/COLOR]
```

---

### Post by bcschmerker on 2016-06-15
**Glad ye managed to solve the old-Kernels problem.**  I routinely purge old Kernel versions in Synaptic Package Manager, but this task can also be done through APT.  For example, as of 12 June 2016 Ubuntu 16.04.0-LTS had a new set of Packages for Kernel 4.4.0-24-generic, meaning 4.4.0-22-generic needed purge after reboot.  Whereas older versions of Ubuntu require a sudo apt-get purge command,  16.04.0-LTS can use:
```
sudo apt purge --remove linux-*-4.4.0-22 linux-*-4.4.0-22-generic
```
to remove the 4.4.0-22 Kernel Image, Headers, and Tools packages, including configuration files.

---

### Post by stuart_jones2 on 2016-06-15
Ran the linux headers and image commands, this is whats left over,
stuart@stuart-ubuntu:~$ dpkg --list | grep linux-headers
ii  linux-headers-3.13.0-46                               3.13.0-46.79                                        all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-46-generic                       3.13.0-46.79                                        amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.13.0-85                               3.13.0-85.129                                       all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-85-generic                       3.13.0-85.129                                       amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.13.0-88                               3.13.0-88.135                                       all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-88-generic                       3.13.0-88.135                                       amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-generic                                 3.13.0.88.94                                        amd64        Generic Linux kernel headers
ii  linux-headers-generic-lts-saucy                       3.13.0.88.94                                        amd64        Generic Linux kernel headers
ii  linux-headers-generic-lts-trusty                      3.13.0.88.94                                        amd64        Generic Linux kernel headers
stuart@stuart-ubuntu:~$ 

The 3 extra commands didn't work Mike, not recognised, I use Bleach bit, does that do the same job?? Is it worth me adding Synaptic Package Manager to help keep the machine clean? Is it simple to use?

---

### Post by Impavidus on 2016-06-15
It all seems quite clean now. Maybe a few old packages still around, you can remove them if you see any. The apt-get autoremove command is supposed to remove old kernels and related stuff automatically, but doesn't seem to work very reliably on 14.04 (as you saw).

Whenever you remove an old kernel, you get a lot of output because the grub configuration file is regenerated to remove the old kernel from the grub menu. It's not very useful to do so after every removal (the system could regenerate it after the last removal), but that's what the uninstall script says.

Synaptic is a great tool. It's a graphical and easy to use tool to manage packages and is more capable than the software centre (or Ubuntu software nowadays I believe). It was the standard tool before the software centre existed.

---

### Post by MikeMecanic on 2016-06-15
> **stuart_jones2 said:**
> Ran the linux headers and image commands, this is whats left over,
stuart@stuart-ubuntu:~$ dpkg --list | grep linux-headers
The 3 extra commands didn't work Mike, not recognised, I use Bleach bit, does that do the same job?? Is it worth me adding Synaptic Package Manager to help keep the machine clean? Is it simple to use?

                         Yes it is!  Good work Stuart you just made a super clean-up..
 ```
sudo apt-get install synaptic
``` 
 
 Open it and then click search so that the search pop-up shows up.  Then search for **linux-image** and click the ones you want to delete: Mark for complete removal.  Before you apply changes, click again on search and this time search for **linux-headers** and mark the same ones (46 and 85) for complete removal:  Apply changes.
 
 
 After, click on Status and see if there are some left in:  Auto removable + local or obsolete and/or residual config.  Keep in mind that you must keep 3.13.0.88.xx

---

### Post by stuart_jones2 on 2016-06-15
Thanks for the replies, will look into Synaptic.
Shall mark the post solved,
a final big thanks, Impavidus I have taken a lot of your time and you have been very patient with me and it is greatly appreciated, thanks to Mike and others too

---

### Post by Impavidus on 2016-06-15
OK, have a nice day.

---

