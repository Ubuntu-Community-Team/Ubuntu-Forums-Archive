---
title: "Unable to upgrade from karmic to lucid"
date: 2010-02-14
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by doctordruidphd on 2010-02-14
I am trying to upgrade an existing karmic system to lucid, but the upgrade fails every time, and at the same spot.

I am doing the upgrade manually from the console, by changing every instance of "karmic" to "lucid" in /etc/apt/sources.list. I then do a sudo apt-get update, followed by a sudo apt-get -d dist-upgrade (which takes about 5 hours), followed by an update and dist-upgrade. There are a few bumps requiring install -f and dpkg --configure -a, but in the end it all seems to go through.

I am unable to boot the system. It dies after the udev error messages, followed by a message that says it is starting crypto disks (there are no crypto disks on this system). Then it hangs. The system will reboot in response to CTRL-ALT-DEL. I cannot get to an interactive console with any CTRL-ALT-F#. 

I have done this several times over the past few weeks. When I first did it back in December, it worked, but after about Jan 8th, it quit. 

Since I am unable to run any of the install or live CDs (a separate issue, bug report filed, but no help as of yet) I am getting a little concerned, since others have had success with the upgrade. It appears that the file system is not being mounted, as no logs or other files are being written. I have tried a manual update-initramfs, but the same results follow.  

I also tried the upgrade using update-manager, but that failed to complete the upgrade. 

Any idea where to go from here?

---

### Post by nanog on 2010-02-15
we need more detail to help you.

off the cuff suggestions:

chroot in and look at your log files -- esp dmesg and syslog. do you still have grub 0.97 or did you upgrade to 1.97.  are your graphic drivers loading?

---

### Post by doctordruidphd on 2010-02-15
Thanks for your reply.

No log files are being written to the system. The entries in dmesg and syslog are from the last boot prior to the upgrade. So far, I have not been able to find anything being written to the file system after the upgrade.

I do have the system upgraded to grub-pc 1.97. 

The graphic drivers are not loading. I have vga=792, splash and quiet removed. The system is hanging before it gets to the point of loading the NVIDIA drivers. One thing I have not tried is putting the vga= command back in. I will try that and report back what happens.

Another thing I tried is upgrading the kernel package only. The system will boot after doing that, and appears to run normally with the 2.6.32 kernel on it. But when I do the rest of the upgrade, it hangs in the same spot.

---

### Post by wilee-nilee on 2010-02-15
If your computer is USB bootable I have found that ISO's that would not work when burned to a cd worked fine when loaded onto a thumb with the usb creator or netbootin.

---

### Post by ptn107 on 2010-02-15
If you intend on upgrading from the command line you need to be using the command: ```
sudo do-release-upgrade -d
```

---

### Post by ranch hand on 2010-02-15
> **ptn107 said:**
> If you intend on upgrading from the command line you need to be using the command: ```
sudo do-release-upgrade
```
When did this start?

My best two installs of 10.04 are upgraded, one from 9.04>9.10>10.04 and the other 9.01>10.04.   That is three upgrades done by editing the sources list to read the version I was going to, run "sudo apt-get update" and then "sudo apt-get dist-upgrade".

Those 2 are solid and the 9.10>10.04 is the oldest of my seven installs.  Nov. 4th upgraded to the tool chain with that one.

---

### Post by doctordruidphd on 2010-02-15
Tried the upgrade again, same results.

The last lines on the screen are:

udevd[802]: can not read '/etc/udev/rules.d/z80_user.rules'
*Starting init crypto disks . . .

Then hang. Note there are no installed crypto disks on this system.

I attempted to use the vga=792 option, which is what I use with karmic. I get only screen garbage, then hang.

> If your computer is USB bootable I have found that ISO's that would not work when burned to a cd worked fine when loaded onto a thumb with the usb creator or netbootin. 
Yes, I have tried USB sticks; they will not boot, either. Yeah, all the validity checks, etc. No iso images of any version of ubuntu after jaunty will boot. Probably a different issue, but maybe not.

> sudo do-release-upgrade
I was under the impression that was for use after the release date, not for alpha or beta. Am I wrong about that? In any event, I have tried the upgrade using both gnome update-manager and kde packagekit, with the same results. Otherwise I always do it from a tty with x shut down.

I can chroot into the system, apt-get update, etc. Just can't boot.
Also, I cannot boot using a previous kernel, once the upgrade is done.

---

### Post by ranch hand on 2010-02-16
If you can boot to recovery try the dpkg option.  It may help.

If you can then boot to the desktop and get a terminal up try;
```

sudo dpkg-reconfigure _

```
Expect to be there a while.  Once again it may help.

If you can't boot to the desktop you can run the above command from chroot but the results are not quite as good but still may help get you a little further.

One thing that will help, at least in the long run, is if you have grub-legacy on the 9.10 change that before the upgrade to grub 1.97beta4.

---

### Post by grandtoubab on 2010-02-16
what about the official way ???
[http://www.ubuntu.com/testing/lucid/alpha2](http://www.ubuntu.com/testing/lucid/alpha2)

---

### Post by ranch hand on 2010-02-16
While Ubuntu has faith in Update Mangler I do not.  I prefer the traditional Debian method.

---

### Post by doctordruidphd on 2010-02-16
Thank You again for the replies and suggestions. 

> If you can boot to recovery try the dpkg option. It may help.
If you can then boot to the desktop and get a terminal up try;

Problem is, I can't boot at all. Whether booting regular or rescue, and whether booting the old 2.6.31 or new 2.6.32 kernel, it dies before mounting the file system. I cannot even get the initramfs, busybox, or "maintenance shell" prompts. It's really dead, except that it does respond to CTRL-ALT-DEL, which says to me the kernel is alive. Nothing else is, though.

The system is running grub-1.97. It is a karmic system that is up-to-date before upgrading, and works -- same system I amusing now. What I do is copy it over to another partition, do the necessary changes to fstab, boot the system, update-initramfs and update-grub. Reboot, make the changes from karmic>lucid in sources.list, get to a tty console, kill x, do the apt-get update, and then dist-upgrade. There are a couple of glitches requiring install -f and dpkg --configure -a. In the end, all of the updates go through. I follow with another install -f, dpkg configure -a, and update/dist upgrade, just to catch anything that may have come down the pipe (this is about a 8 hour process for all of it).

> sudo dpkg-reconfigure
Right, I cannot boot. I will try this from chroot (not a whole lot to lose).
Once again, thanks, and any ideas welcome at this point, as something is REALLY broke here.

---

### Post by nanog on 2010-02-16
does grub come up at all? if not, the you may need to reconfigure grub -- lots of posts on this here. just search. udev or initramfs have been having problems of late.

you may want to check this out:

[http://ohioloco.ubuntuforums.org/showthread.php?t=1403446&highlight=initramfs](http://ohioloco.ubuntuforums.org/showthread.php?t=1403446&highlight=initramfs)

---

### Post by doctordruidphd on 2010-02-16
sudo dpkg-reconfigure -a
does not appear to work in lucid. I get the following error message:

```
root@Wolfenstein:/# dpkg-reconfigure --all
This is not dpkg install-info anymore, but GNU install-info
See the man page for ginstall-info for command line arguments
install-info: No dir file specified; try --help for more information.

```

I couldn't find anything that made sense in man ginstall-info.

---

### Post by doctordruidphd on 2010-02-16
> does grub come up at all? if not, the you may need to reconfigure grub -- lots of posts on this here. just search. occasionally udev or initramfs get borked.

Yes, grub comes up fine, and will boot the other os's on the system without any trouble.

> useful commands:

Repair broken upgrade

sudo dpkg --configure -a

reconfigure/repair package

sudo dpkg-reconfigure <package name>

fix broken package

sudo apt-get -f install <package name> 

Yes, have used all of those, multiple times, during and after the upgrade before rebooting, and chroot'd into the system after (will not boot).

Is there, somewhere, a detailed descritption of how the boot process works in lucid (it has obviously changed from karmic)? Since there is nothing being written to dmesg, I can't tell where it is breaking, or what is breaking. If I had some sort of list of what gets run in what order, it might be helpful. Once again, I cannot boot, either regular or recovery mode, and it is hanging before the file system mounts, so no logs are being written.

---

### Post by nanog on 2010-02-16
have you checked out the link i posted above above. it really sounds like you have a problem with nitramfs (loads kernel/drivers into ram) and/or udev (manages i/o devices).

fix ramfs:
```

sudo update-initramfs
```

---

### Post by doctordruidphd on 2010-02-16
> have you checked out the link i posted above above

Yes. The version of the file I have that is mentioned in the thread is already patched. I have run update-initramfs, both after the original install, and from chroot: it runs without errors, and generates an initrd.img, though I do suspect that is where the problem ultimately lies, or with udev.

---

### Post by VMC on 2010-02-16
> **doctordruidphd said:**
> ...I have vga=792, splash and quiet removed...This has caught my eye. Do you really have "splash" removed? If so that could be one of your problems.
I have been having problems with Plymouth and this has come up both with and without "splash" removed.

Apparently with "splash" removed, both GDM and Plymouth are fighting for VT terminals. Although in my case and in all my cases VT7 was always used for the desktop.

The reason I had "splash" removed dated back to karmic, when I had issues. Now I leave "splash" in to avoid conflict.

You want "quite" removed so you can see what messages come across at boot-up.

---

### Post by doctordruidphd on 2010-02-16
Problem Solved. Geez, what a nightmare!

> Do you really have "splash" removed?
Yes. Neither usplash, nor splashy, nor plymouth are installed.

But that gave me an idea. I installed plymouth, and put the splash command back in the boot file. On rebooting, up came plymouth. It flashed several messages, and then:

```
Waiting for /media/vault
```

AHA! I have three USB disks, which I have entries for in /etc/fstab by UUID. Works nicely (in < lucid) so that when I plug them in, they go where I want them. Evidently lucid is not going to cooperate with that method. That is where it is hanging, on entries in fstab that don't point to installed drives. Commenting them out in fstab and rebooting brought the bloody thing up! I'll figure out the fstab problem later...

Thanks to all who offered suggestions. I knew it was only a matter of time...

---

### Post by doctordruidphd on 2010-02-17
Further experiments have shown that adding the 'noauto' option in fstab will allow the system to boot, even if the devices are listed and not plugged in.

---

### Post by frogotronic on 2010-03-04
Well, I cannot upgrade at all - its a complete barf (see screenshot).

I filed a bug report here: [https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/531470](https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/531470)

If anyone has a workaround, I'd appreciate it.

Thanks,
CH   :popcorn:

---

### Post by nanog on 2010-03-04
cement head, this post was marked solved. please start a new post with information on the errors that occurred suring upgrade. you can also try chrooting (see link in my sig) and trying the commands in my sig. this should give you error/dependency data that will allow this problem to be solved.

---

### Post by frogotronic on 2010-03-04
> **nanog said:**
> cement head, this post was marked solved. please start a new post with information on the errors that occurred suring upgrade. you can also try chrooting (see link in my sig) and trying the commands in my sig. this should give you error/dependency data that will allow this problem to be solved.

as in the marker for stem cells?

---

