---
title: "CD/DVD Drive Disappears(!) in Lucid After Initial Mount at Boot"
date: 2010-06-06
forum: Installation &amp; Upgrades
---

### Post by casparov on 2010-06-06
Hi, Everyone...

I have been at this problem for some time, a recognized bug in Lucid. Upon doing a fresh install of 10.04 the system runs nominally, except for the CD/DVD drive, which will not play or recognize disks after initially recognizing them upon booting. (In fact, the only way to use a disk in the drive is to reboot the system.)

This shouldn't be, but has become, quite a distraction, since it is an on-going irritation and sours the Ubuntu experience (though it has its impressive moments, for sure). For instance, there are times when I can do a few things on the Net and come back to my CD/DVD drive and the disk and drive will be beautifully operational. At other times, after a bit of activity on the PC, I will return to the file system and the CD/DVD dive will have disappeared! From what I can tell there is some problem about mounting the drive, but that is the extent of my knowledge (which is really low).

Again, this is a problem that is recognized elsewhere as a legitimate bug. [https://bugs.launchpad.net/ubuntu/+s...ev/+bug/562092](https://bugs.launchpad.net/ubuntu/+s...ev/+bug/562092) ; [https://bugs.launchpad.net/ubuntu/lu...ev/+bug/554433](https://bugs.launchpad.net/ubuntu/lu...ev/+bug/554433) It has also been complained of on this board: [http://www.uluga.ubuntuforums.org/sh....php?p=9256142](http://www.uluga.ubuntuforums.org/sh....php?p=9256142) 

Does anyone have an idea? 

Thanks so much for any help,

Casp

---

### Post by davidmohammed on 2010-06-06
both of those links don't point to anything relevant...

---

### Post by davidmohammed on 2010-06-06
... forget that - looks like launchpad is having issues.

Have you tried the upstream kernels such as 2.6.34?  Issue is supposed to be fixed there.

---

### Post by casparov on 2010-06-06
David...

Thanks for the reply. 

How to I go about accessing and using upstream kernels?

Thanks so much,

C.

---

### Post by davidmohammed on 2010-06-06
Have a look at [this]("https://wiki.ubuntu.com/KernelTeam/MainlineBuilds?action=show&redirect=KernelMainlineBuilds") - it describes where the mainline kernels are and how to install.

---

### Post by casparov on 2010-06-06
David...

Thanks, again, for the reply. 

I have looked at your link and will attempt this.  For my level, it seems a bit involved.  But it may be a kernel problem because Karmic was perfect for me.

All Regards, C.

---

### Post by SpaceBison on 2010-06-06
> **davidmohammed said:**
> Have a look at [this]("https://wiki.ubuntu.com/KernelTeam/MainlineBuilds?action=show&redirect=KernelMainlineBuilds") - it describes where the mainline kernels are and how to install.
Thanks, I've been having the same issue and this seems to have fixed it. My question is would I have to reinstall this whenever Ubuntu pushes out a new kernel through the automatic updates? I guess I'll find out sooner or later, thanks.

---

### Post by casparov on 2010-06-06
David... 

I downloaded the kernel that you suggested but couldn't install it.  Here is my terminal after several attempts: 

whit@whit-desktop:~$ sudo dpkg -i linux-image-2.6.34-020634-generic_2.6.34-020634_i386.deb
dpkg: error processing linux-image-2.6.34-020634-generic_2.6.34-020634_i386.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 linux-image-2.6.34-020634-generic_2.6.34-020634_i386.deb
whit@whit-desktop:~$

I have no idea how to install things like this.  :(

All Regards,  C.

---

### Post by SpaceBison on 2010-06-06
> **casparov said:**
> David... 

I downloaded the kernel that you suggested but couldn't install it.  Here is my terminal after several attempts: 

whit@whit-desktop:~$ sudo dpkg -i linux-image-2.6.34-020634-generic_2.6.34-020634_i386.deb
dpkg: error processing linux-image-2.6.34-020634-generic_2.6.34-020634_i386.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 linux-image-2.6.34-020634-generic_2.6.34-020634_i386.deb
whit@whit-desktop:~$

I have no idea how to install things like this.  :(

All Regards,  C.

Make sure that you're in the same directory as the file you just download before trying to install it. Try this first in the terminal, hit enter, then the rest of it:> cd Downloads

If that doesn't work just go to where ever you downloaded it to and double click on it. It should prompt you for your password and install it for you. Once it has finished you'll need to restart your computer.

---

### Post by casparov on 2010-06-07
Space...

Thanks for that--I just double clicked it, and it did the job.  That's my level of Linux competence.  LOL!  

I will be back when I see if this worked,  C.

---

### Post by casparov on 2010-06-07
Space and David... 

Thanks so much for the idea to install the kernel--David is, most likely correct about the problem.  But, while the drive seems to be better, it still is not recognize consistently.

However, the new kernel will not enable normal graphics; i.e., my Nvidia 3D graphics are not available.  The system states that it installs the driver and directs a restart; once restarted it will not enable the driver.  

So, right now, I gained consistent DVD recognition (sort of) but lost the graphics power to use it.  I have posted another thread relating to the new problem: [http://ubuntuforums.org/showthread.php?p=9423266#post9423266](http://ubuntuforums.org/showthread.php?p=9423266#post9423266)

Is there an easy way to restore the original kernel?

Any other ideas?  C.

---

### Post by davidmohammed on 2010-06-07
> **SpaceBison said:**
> Thanks, I've been having the same issue and this seems to have fixed it. My question is would I have to reinstall this whenever Ubuntu pushes out a new kernel through the automatic updates? I guess I'll find out sooner or later, thanks.

No you will not - if you display your grub during boot (press shift after BIOS screen) you'll see the new kernel as the default at the top of the screen.  I would expect during the LTS lifecycle new 2.6.32.xx kernels to be released - these will also appear in your grub list.  I would from time-to-time boot up from these newer kernels to see if canonical have fixed your issue.  If the 2.6.32.xx kernels fix your issue then you can delete your 2.6.34 kernel you've installed (instructions in the link I gave you to install)

---

### Post by davidmohammed on 2010-06-07
> **casparov said:**
> Space and David... 

Thanks so much for the idea to install the kernel--David is, most likely correct about the problem.  But, while the drive seems to be better, it still is not recognize consistently.

However, the new kernel will not enable normal graphics; i.e., my Nvidia 3D graphics are not available.  The system states that it installs the driver and directs a restart; once restarted it will not enable the driver.  

So, right now, I gained consistent DVD recognition (sort of) but lost the graphics power to use it.  I have posted another thread relating to the new problem: [http://ubuntuforums.org/showthread.php?p=9423266#post9423266](http://ubuntuforums.org/showthread.php?p=9423266#post9423266)

Is there an easy way to restore the original kernel?

Any other ideas?  C.

If you press shift after the bios screen on boot you'll notice the list of kernels installed.  Choose the lucid kernel (2.6.32.22) if you want to boot from the most recent lucid kernel.

If you want to make the lucid kernel the default - you can change the default in grub - from memory I think that is in the file /etc/default/grub.  Change the default value from 0 to probably 2.

run sudo update-grub afterwords and reboot.  During reboot don't forget to press shift to examine if the default kernel is correctly chosen in the grub list.

---

### Post by casparov on 2010-06-07
David...

You are right again, as the shift+hold option displayed the GRUB kernel menu.

However, each kernel (three of them: *.32.22, *.32.21, and *.34) will not allow my NVIDIA restricted driver to load.  Also, the PC displays a very odd splash screen of vertical bars before getting to the desktop when using the earlier kernels.

Do yo have any idea how I could restore my visual effects or the restricted driver?  (Also, I downloaded the most recent NVIDIA driver to my desktop.)  As you might imagine, the machine is somewhat limited w/ only the default display capability.   

(And to let you know, I have tried to install the proper driver using the options from the Appearance menu and the Hardware Drivers option from the Administration menu.  The latter menu provides two driver options, and I have used both.  Each time the Appearance/Visual Effects route installs the driver, directs a reboot, then indicates that the effects are not available.  That is why I downloaded the appropriate driver from the NVIDIA site [NVIDIA-Linux-x86-195.36.24-pkg1.run] but don't know how to install if--if that would correct the problem.)

Another thing...   The only way I can access my favorite video (from the UK) is via Livestation, and now that application only states that, "This system does not support opengl."  Would the restricted driver get around that error?

Anyway, David, thanks so much again...   C.

---

### Post by davidmohammed on 2010-06-08
OK,
  question for you:  did you install both of the "<header>.deb" packages when you installed the kernel? i.e. the package names that has "header" somewhere in the file names

e.g. for a intel processor did you download and install the following packages

 linux-headers-2.6.34-020634-generic_2.6.34-020634_i386.deb 17-May-2010 22:38  675K 
 linux-headers-2.6.34-020634_2.6.34-020634_all.deb 17-May-2010 20:27  9.6M 
 linux-image-2.6.34-020634-generic_2.6.34-020634_i386.deb 


try the following (summarised from [here]("http://www.sucka.net/2010/04/how-to-install-nvidia-video-driver-in-10-04-lucid-lynx/")): boot using the brand new 2.6.34 kernel

then in a terminal do the following (copy and paste the text below)

```
sudo aptitude install build-essential
```
uninstall any and all nvidia components installed.

```
sudo apt-get purge nvidia*
```
Next we need to blacklist &#8220;nouveau&#8221;.  

```
gksudo gedit /etc/modprobe.d/blacklist.conf
``` 
add the following text to this file.

```
blacklist nouveau
```

Next ,install the latest official stable driver from the repository

```
sudo apt-get install nvidia-current
```
Next we&#8217;ll load the Nvidia kernel module

```
sudo modprobe nvidia-current
```
Verify it&#8217;s successful entry via lsmod like so

```
sudo lsmod | grep -i nvidia
```
And one last step, we must create the Nvidia configuration file.

```
sudo nvidia-xconfig
```

---

### Post by casparov on 2010-06-09
David...

Your latest is exquisite information, and this thread will provide a lot of know-how to many new to Linux.

However, when I checked your first link on your latest post, I found that I cannot edit the file within /etc because I don't have ownership rights; i.e., I couldn't blacklist nouveau (as if I know what that means).

Do you happen to know how I could make that particular file writable? 

I apologize for the ignorance.

All Regards,   C.

---

### Post by davidmohammed on 2010-06-09
ok - have revised my post above showing how to edit this file.

---

### Post by casparov on 2010-06-10
David...

How in the world do you know all this? 

Anyway, I followed your instructions w/ everything going swimmingly until the command "sudo modprobe nvidia-current", whereupon this was generated in terminal:  

Setting up nvidia-settings (195.36.08-0ubuntu2) ...
Processing triggers for python-gmenu ...
Rebuilding /usr/share/applications/desktop.en_US.utf8.cache...
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.34-020634-generic
Processing triggers for python-support ...
whit@whit-desktop:~$ sudo modprobe nvidia-current
**FATAL: Module nvidia_current not found.**

I'm sorry to hold you up, yet again.  (But I think you're close!!!:p)

If you can translate this my gratitude would know no earthly bounds!!!

All Regards,  C.

---

### Post by davidmohammed on 2010-06-10
There is a similar thread [here]("http://ubuntuforums.org/showthread.php?t=1439734&page=2") for your "not found" issue.  Reading through it, two conclusions.

1. some people have found that if you just reboot after completing the instructions, things work ok
2. some people have found that if the default lucid nvidia drivers don't work, then "purge" the driver as described above and then install the driver directly from the nvidia website.

Suggest have a read of the thread to see which method will work for you.

---

### Post by casparov on 2010-06-11
David...

Thanks so much, again and again and again, for your latest input...

I got past the terminal command to install the current NVIDIA driver and completed the list of commands.  However, the last command generates an exception but states that a "new configuration" was executed.  Upon restart, and gaining the appearances menu and visual effects, the NVIDIA driver is not loaded or working because the visual effects cannot be enabled.

Okay, now...   Your second suggestion was to purge the NVIDIA driver and install the driver from the NVIDIA site.  I have downloaded the appropriate driver and used the information here ([http://ubuntuforums.org/showthread.php?t=239797](http://ubuntuforums.org/showthread.php?t=239797)) to install it.  But  I am prevented from completing the installation by a warning that "X-server" must be stopped before the installation can be completed.  Therefore, I went here ([http://ubuntuforums.org/showthread.php?t=614843](http://ubuntuforums.org/showthread.php?t=614843)) to understand how to stop X-server but am a bit lost about the GUI logon.  Do you know a way of installing the NVIDIA driver that would work?  Before attempting that should I follow the instructions on this thread to purge the current driver?

[I should also add that, as things are--and upon restart--I get a warning that the system is running in low graphics mode and that the NVIDIA driver is not loaded, nor are the NVIDIA configuration settings active. (Actually, I used this opportunity as an attempt to load the driver that I downloaded, believing that, since the warning cited here had an option to "restart X", I had a window in which X-server was not active.  Apparently, this was not the case, as the attempt to install the driver generated the same error pertaining to stopping X.  Also, under System/Administration is a menu for NVIDIA X Server settings, which, when clicked, indicates that the system is not running the NVIDIA driver.)  At this time the hardware drivers tool (System->Administration->Hardware Drivers) indicates that there are no proprietary drivers in the system.  If that all helps... ]  

I believe we are really close--thanks to you...  :p   C.

---

### Post by davidmohammed on 2010-06-11
Ok, 
  sounds like you are nearly there.  

Yes - purge the nvidia driver.

Print out the command line install instructions for the nvidia driver - you are going to need to type the install instructions below

Suggest reboot to startup BUT DONT login as normal (i.e. you dont login to your desktop)using the 2.6.34 kernel.  If you have an automatic login, then just logout.

press CTRL + ALT+F2.  The screen should turn black with tty2 at the top.  Login again.  You will be at a prompt waiting for you to type 

sudo /etc/init.d/gdm stop

now install the nvidia driver using the printout above

then start X via

sudo /etc/init.d/gdm start

press CTRL + ALT + F7 to see your graphical login page.

Suggest reboot and then login again

---

### Post by GlennW on 2010-06-15
I've been following this thread with interest since we share a common issue, I think. I can't play a DVD. I've done virtually everything in every thread/search I can find related to this issue to no avail. 

I have already manually updated to the latest kernel (2.6.34). I have no nVidia issues which is great. But, I still cannot play a DVD. 

I'm hoping the next updates will bring a resolution to this issue since there are so many folks suffering the same ills. 

How can 10.04, which is the best distro I've used, drop the ball so badly? 

Thanks for any thoughts.

---

### Post by davidmohammed on 2010-06-15
Hi there,
  I note your frustration - but in this case, I don't blame canonical.  There is a growing consensus that upstream, too many new features are being packed into the kernel, without adequate regression testing of existing capability.  The consequence is too many breakages.  

For my two cents worth - Linus Torvalds should insist on one or two kernel releases that doesnt have any new features but just bug fixes.

---

### Post by GlennW on 2010-06-15
> **davidmohammed said:**
> Hi there,
  I note your frustration - but in this case, I don't blame canonical.  There is a growing consensus that upstream, too many new features are being packed into the kernel, without adequate regression testing of existing capability.  The consequence is too many breakages.  

For my two cents worth - Linus Torvalds should insist on one or two kernel releases that doesnt have any new features but just bug fixes.

Thanks, David, for the input. However, canonical must recognize this as a major breakage. What happens now to the many folks who aren't able to use a live CD because of this and thus may not be able to upgrade?

---

### Post by salima on 2010-08-19
hi-
i am a new user and just learning, but i love ubuntu for a million reasons already.

i installed 8.10 from a disk someone gave me and decided to upgrade to 10.04, managed to make a disk in four nights (slow connection) and all i want to do is install the upgrade. i dont really care for now or in the near future if my cd or dvd player works...i just want to upgrade for now. when i put in the cd, i get this:  
Unable to mount
DBus error org.freedesktop.DBus.Error.NoReply: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.

so before i add kernels and things, can you tell me the fastest way to take care of this without wrecking anything else? i have only ubuntu on this machine. 

thanks!

---

### Post by rykel on 2010-12-07
Hi gang, I am using Maverick and it is now 8 December 2010 yet still my CD/DVD drive only shows up at boot... after an Eject, it disappears completely and no longer can be mounted.    :(

Please help??

---

### Post by oldnat on 2011-03-27
Same thing (10.10). 
The first DVD I can insert, mounts, OK. 
After ejecting the whole drive "disappears".
Simple reboot seems not to help, I have to shut down (physically unpower) the machine and then boot again to have the DVD drive again (for one session again).

Any ideas?

Thanks

---

