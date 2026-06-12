---
title: "Virtual Box error!"
date: 2008-04-09
forum: Installation &amp; Upgrades
---

### Post by Ra2yuri on 2008-04-09
Hi! I'm a bit of a n00b to Ubuntu and I really would like to know why I keep getting this error,


VirtualBox kernel driver not installed. The vboxdrv kernel module was either not loaded or /dev/vboxdrv was not created for some reason. Re-setup the kernel module by executing '/etc/init.d/vboxdrv setup' as root.
VBox status code: -1908 (VERR_VM_DRIVER_NOT_INSTALLED).


Result Code: 
0x80004005
Component: 
Console
Interface: 
IConsole {1dea5c4b-0753-4193-b909-22330f64ec45}

 I have tryed everything I had looked up on google! Even re-installing the package. If anyone can give me a clue or hint it will be very generous >_<!

Any thing at all (Note:It maybe something I may have already tried.)

---

### Post by Partyboi2 on 2008-04-09
have you tried
```
sudo /etc/init.d/vboxdrv setup
```?

---

### Post by Peter09 on 2008-04-09
To use virtualbox you need to have the kernal Headers on your machine, otherwise you get an error during the virtualbox build. You need to make sure that the headers that you download are the same version as your kernal.

They are available through Synaptic. Make sure you get the right versions. Then rebuild virtualbox.

PC

---

### Post by Ra2yuri on 2008-04-09
@Partyboi2: I'm afraid I have tryed that. All it pops up is 
"   * Stopping VirtualBox kernel module vboxdrv                             [ OK ] 
 * Removing old VirtualBox kernel module...                              [ OK ] 
 * Recompiling VirtualBox kernel module vboxdrv                          [ OK ] 
 * Starting VirtualBox kernel module vboxdrv                                    
 * Modprobe vboxdrv failed. Please use 'dmesg' to find out why."


> **Peter09 said:**
> To use virtualbox you need to have the kernal Headers on your machine, otherwise you get an error during the virtualbox build. You need to make sure that the headers that you download are the same version as your kernal.

They are available through Synaptic. Make sure you get the right versions. Then rebuild virtualbox.

PC

how do I see my version of kernel headers :D. Sorry I'm still getting use to Ubuntu. Is it usrnam r?

---

### Post by Peter09 on 2008-04-09
I think most of what you will need can be found in here:-

[http://www.virtualbox.org/wiki/End-user_documentation](http://www.virtualbox.org/wiki/End-user_documentation)


PC```
uname -a
```

 tells you what your kernal headers are

---

### Post by Ra2yuri on 2008-04-09
> **Peter09 said:**
> I think most of what you will need can be found in here:-

[http://www.virtualbox.org/wiki/End-user_documentation](http://www.virtualbox.org/wiki/End-user_documentation)


PC```
uname -a
```

 tells you what your kernal headers are

yeah My kernels match. I've done it through Synaptic a few mins ago.But I still get the same error in VBOX :( . heres my kernel,

 2.6.20-16-generic<-------

And I'll cheack up on the link you gave me.

---

### Post by badhabit on 2008-04-09
PIIX3 cannot attach drive to the Secondary Master.
VBox status code: -102 (VERR_FILE_NOT_FOUND).


This is what I'm getting when I try to run VBox. It was running fine until I updated a day or so back. I'm very new at this so please look over it. I do have to say I wish I had started using linux years ago though.

---

### Post by Peter09 on 2008-04-09
Remember that you will need to build virtualbox every time a new kernel is delivered, this is not a good scenario for Hardy - if thats what you are running, as the kernel is changed quite often.

I am unsure if virtual box has been released for the new kernels, do they show which kernels its valid for?

PC

---

### Post by Ra2yuri on 2008-04-09
well for starters I'm using a deb file. Not ose. And it is for my version of ubuntu (like when u expect it to work). Then you relise that its linux and not windows :D...

---

### Post by badhabit on 2008-04-09
I"m sorry I was not clear on which version I was running. I'm using 8.04 
Here's my kernel
desktop 2.6.24-15-generic #1 SMP Fri Apr 4 03:48:31 UTC 2008 i686 GNU/Linux
I'm guessing they don't have an update for it yet. I've waited 38 years I can wait a few more days for it. I do have to say Ubuntu is a great product and look forward to learning more about it.

By the way, thanks for the help.

---

### Post by badhabit on 2008-04-09
Also I did rebuild the kernel using   sudo /etc/init.d/vboxdrv setup

---

### Post by Peter09 on 2008-04-09
Here is a link that might help:

[http://forums.virtualbox.org/viewtopic.php?p=18716&sid=20ee5317a81851ab3b530cf5dce05e19](http://forums.virtualbox.org/viewtopic.php?p=18716&sid=20ee5317a81851ab3b530cf5dce05e19)

PC

---

### Post by Ra2yuri on 2008-04-09
> **badhabit said:**
> Also I did rebuild the kernel using   sudo /etc/init.d/vboxdrv setup

tryed that as well :),

```
ra2yuri@ra2yuri-desktop:~$ sudo /etc/init.d/vboxdrv setup
 * Stopping VirtualBox kernel module vboxdrv                             [ OK ] 
 * Removing old VirtualBox kernel module...                              [ OK ] 
 * Recompiling VirtualBox kernel module vboxdrv                          [ OK ] 
 * Starting VirtualBox kernel module vboxdrv                                    
 * Modprobe vboxdrv failed. Please use 'dmesg' to find out why.

```

---

### Post by Peter09 on 2008-04-09
what does 

```
dmsg | grep vbox
```

say

PC

---

### Post by Ra2yuri on 2008-04-09
> **Peter09 said:**
> what does 

```
dmsg | grep vbox
```

say

PC

well when I type dmsg in terminal it says

```
[  167.005279] vboxdrv: Trying to deactivate the NMI watchdog permanently...
[  167.005290] vboxdrv: NMI watchdog either active or at least initialized. Please disable the NMI
[  167.005292] vboxdrv: watchdog by specifying 'nmi_watchdog=0' at kernel command line.
[  184.455868] vboxdrv: Trying to deactivate the NMI watchdog permanently...
[  184.455878] vboxdrv: NMI watchdog either active or at least initialized. Please disable the NMI
[  184.455881] vboxdrv: watchdog by specifying 'nmi_watchdog=0' at kernel command line.
[  337.131571] vboxdrv: Trying to deactivate the NMI watchdog permanently...
[  337.131582] vboxdrv: NMI watchdog either active or at least initialized. Please disable the NMI
[  337.131584] vboxdrv: watchdog by specifying 'nmi_watchdog=0' at kernel command line.
[  501.492765] vboxdrv: Trying to deactivate the NMI watchdog permanently...
[  501.492775] vboxdrv: NMI watchdog either active or at least initialized. Please disable the NMI
[  501.492778] vboxdrv: watchdog by specifying 'nmi_watchdog=0' at kernel command line.
[  528.641208] vboxdrv: Trying to deactivate the NMI watchdog permanently...
[  528.641218] vboxdrv: NMI watchdog either active or at least initialized. Please disable the NMI
[  528.641221] vboxdrv: watchdog by specifying 'nmi_watchdog=0' at kernel command line.

```

I'm studying what that means :)...

---

### Post by Partyboi2 on 2008-04-09
> **Ra2yuri said:**
> well when I type dmsg in terminal it says

```
[  167.005279] vboxdrv: Trying to deactivate the NMI watchdog permanently...
[  167.005290] vboxdrv: NMI watchdog either active or at least initialized. Please disable the NMI
[  167.005292] vboxdrv: watchdog by specifying 'nmi_watchdog=0' at kernel command line.
[  184.455868] vboxdrv: Trying to deactivate the NMI watchdog permanently...
[  184.455878] vboxdrv: NMI watchdog either active or at least initialized. Please disable the NMI
[  184.455881] vboxdrv: watchdog by specifying 'nmi_watchdog=0' at kernel command line.
[  337.131571] vboxdrv: Trying to deactivate the NMI watchdog permanently...
[  337.131582] vboxdrv: NMI watchdog either active or at least initialized. Please disable the NMI
[  337.131584] vboxdrv: watchdog by specifying 'nmi_watchdog=0' at kernel command line.
[  501.492765] vboxdrv: Trying to deactivate the NMI watchdog permanently...
[  501.492775] vboxdrv: NMI watchdog either active or at least initialized. Please disable the NMI
[  501.492778] vboxdrv: watchdog by specifying 'nmi_watchdog=0' at kernel command line.
[  528.641208] vboxdrv: Trying to deactivate the NMI watchdog permanently...
[  528.641218] vboxdrv: NMI watchdog either active or at least initialized. Please disable the NMI
[  528.641221] vboxdrv: watchdog by specifying 'nmi_watchdog=0' at kernel command line.

```I'm studying what that means :)...
Add nmi_watchdog=0 to your boot options.
Boot your system and when you see the grub loading stage1.5...(something like that) part press ESC to get to the grub menu. Then highlight the kernel you normally boot into and press "e" to edit then highlight the line starting with "kernel" and press "e" again to edit then at the end of the line add nmi_watchdog=0 then press "enter" then "b" to boot. Ubuntu should then continue to boot. Check to see if it worked. If it worked you will need to addnmi_watchdog=0  to grub menu.lst so that it is permanant. To do that open up /boot/grub/menu.lst
```
gksudo gedit /boot/grub/menu.lst
``` and look for this section which in near the bottom of the page. (It will be slighlty different then the one shown here)
> ## ## End Default Options ##

title        Ubuntu hardy (development branch), kernel 2.6.24-15-generic
root        (hd1,1)
[COLOR=Red]kernel        /boot/vmlinuz-2.6.24-15-generic root=UUID=c61e113a-1e75-40cc-8051-bcceeb33acff ro quiet splash[/COLOR]
initrd        /boot/initrd.img-2.6.24-15-generic
quiet at the end of the kernel line add   ```
nmi_watchdog=0
``` so it would look something like this:
```
kernel        /boot/vmlinuz-2.6.24-15-generic root=UUID=c61e113a-1e75-40cc-8051-bcceeb33acff ro quiet splash nmi_watchdog=0
``` then save
then back in a terminal update grub
```
sudo update-grub
```

---

### Post by badhabit on 2008-04-09
I went in and updated Vbox from terminal. [https://help.ubuntu.com/community/VirtualBox](https://help.ubuntu.com/community/VirtualBox)

Then went into the settings on the Vbox and clicked on cd/dvdrom setting and changed it from whatever it was to my dvd drive. For some reason when I updated it was showing a dvd or cd drive I didn't have. Once I changed that it worked fine. I don't know if it was from the updates or a combo of both.
B H

---

### Post by Ra2yuri on 2008-04-09
> **Partyboi2 said:**
> Add nmi_watchdog=0 to your boot options.
Boot your system and when you see the grub loading stage1.5...(something like that) part press ESC to get to the grub menu. Then highlight the kernel you normally boot into and press "e" to edit then highlight the line starting with "kernel" and press "e" again to edit then at the end of the line add nmi_watchdog=0 then press "enter" then "b" to boot. Ubuntu should then continue to boot. Check to see if it worked. If it worked you will need to addnmi_watchdog=0  to grub menu.lst so that it is permanant. To do that open up /boot/grub/menu.lst
```
gksudo gedit /boot/grub/menu.lst
``` and look for this section which in near the bottom of the page. (It will be slighlty different then the one shown here)
 at the end of the kernel line add   ```
nmi_watchdog=0
``` so it would look something like this:
```
kernel        /boot/vmlinuz-2.6.24-15-generic root=UUID=c61e113a-1e75-40cc-8051-bcceeb33acff ro quiet splash nmi_watchdog=0
``` then save
then back in a terminal update grub
```
sudo update-grub
```

I luv U! Thx a lot. It works now :)

---

### Post by element_G on 2008-04-09
> **Partyboi2 said:**
> have you tried
```
sudo /etc/init.d/vboxdrv setup
```?
just wanted to add that the above command worked like a charm for me :guitar:

---

### Post by badhabit on 2008-04-10
The first time it stopped working for me the sudo /etc/init.d/vboxdrv setup worked for me. This time it would not work. Thanks for all the help and taking the time to help.

---

### Post by Ubuntwan on 2008-04-28
although your problems are solved now, I used different solutions:
Ra2yuri's problem was solved by doing:
sudo apt-get install virtualbox-ose-modules-generic
after which it gave me the same error it gave Badhabit.
This problem was solved by using a post by Rytron in this thread: [http://ubuntuforums.org/showthread.php?t=767451&highlight=PIIX3]("http://ubuntuforums.org/showthread.php?t=767451&highlight=PIIX3")
I had a cd mounted last time virtualbox was running and it was missing this cd now, and gave this error. In the settings menu I unchecked the mount cd/dvd drive checkbox and everything was fine again.

---

### Post by Pollywoggy on 2008-04-28
> **badhabit said:**
> I"m sorry I was not clear on which version I was running. I'm using 8.04 
Here's my kernel
desktop 2.6.24-15-generic #1 SMP Fri Apr 4 03:48:31 UTC 2008 i686 GNU/Linux
I'm guessing they don't have an update for it yet. I've waited 38 years I can wait a few more days for it. I do have to say Ubuntu is a great product and look forward to learning more about it.

By the way, thanks for the help.

I thought I had fixed the problem but I just noticed it is back and it's probably because I upgraded the kernel headers in order to get Truecrypt working again.  I got that working and now Virtualbox is not working.

The thing is I switched from VMware to Virtualbox because of this sort of problem occuring every time I upgrade Linux.  Now I am thinking I should try Win4Lin again, now that apparently Win4Lin does not require kernel modules.

---

### Post by Pollywoggy on 2008-04-28
> **Pollywoggy said:**
> I thought I had fixed the problem but I just noticed it is back and it's probably because I upgraded the kernel headers in order to get Truecrypt working again.  I got that working and now Virtualbox is not working.

The thing is I switched from VMware to Virtualbox because of this sort of problem occuring every time I upgrade Linux.  Now I am thinking I should try Win4Lin again, now that apparently Win4Lin does not require kernel modules.

Virtualbox.org does not yet have debs for Hardy, so I tried the OSE version tarball and that worked.  It took 30 minutes or so to compile but it solves the problem.  Just remove your old virtualbox package before installing this one.  This tarball has the necessary files in it to make a deb if you go into the toplevel directory and issue 'sudo dpkg-buildpackage' and the first time you try this, you will probably get errors relating to dependencies.  Just install those deps with apt-get and then try building the deb again.  I got two debs but I did not install the dbg one.

---

