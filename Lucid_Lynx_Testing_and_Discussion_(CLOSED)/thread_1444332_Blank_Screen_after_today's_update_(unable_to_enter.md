---
title: "Blank Screen after today's update (unable to enter recovery)"
date: 2010-04-01
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by venomenus on 2010-04-01
Hi Guys!

I updated Lucid today then rebooted and now I just get a blank screen :(

before this update I always booted with nomodeset in grub otherwise I would just get a blank screen but now that doesn't seem to make any difference.

removing quiet splash doesn't seem to show any errors and I cannot get into recovery mode as I just get a black screen in that too also ctrl + alt + F1 doesn't do anything.

My graphics card is a Intel 945GM.

I can boot from an original beta 1 usb stick image (with nomodeset) but I don't know what I can do to fix it from there and what logs would be best to look at, I did view Xorg.0.log and found a "Fatal server issue : no screen found" error though.

Also I don't have/use an Xorg.conf file.

any help would be much appreciated

Thanks
Lee

---

### Post by mdurham on 2010-04-01
It sounds like you will have to boot from your USB stick and chroot into your main system, then apt-get update etc from there. That's what I had to do.

---

### Post by macstevejb on 2010-04-01
Having the exact same problem with my netbook that has the same Intel graphics card.

This only started to happen after this morning's updates.

Have nomodeset set in grub but can nether boot into X or to recovery mode.

Am left scratching my head on this one.

mdurham - not sure that's a solution to this problem.

What is it with these latest updates borking my boxes?....my main box with Nvidia graphics wont get past GDM because it crashes and now this prob with my intel graphics netbook! :-(

regards

---

### Post by venomenus on 2010-04-01
> **mdurham said:**
> It sounds like you will have to boot from your USB stick and chroot into your main system, then apt-get update etc from there. That's what I had to do.

Hi,

I just tried this using the tutorial from [http://ubuntuforums.org/showpost.php?p=8068512&postcount=10]("http://ubuntuforums.org/showpost.php?p=8068512&postcount=10"), it downloaded some updates but didn't fix the problem.

Thanks for your suggestion though, I didn't even know that this could be done!, so I learnt something new :)

---

### Post by venomenus on 2010-04-01
Hi,

Im still having no luck with this and I really don't want to have to reinstall 8( lol

I'm not sure if this will help anyone but here is the last few lines of my syslog:

Apr  1 12:24:22 lee-laptop gdm-binary[877]: WARNING: GdmDisplay: display lasted 1.752417 seconds
Apr  1 12:24:22 lee-laptop gdm-simple-slave[999]: WARNING: Unable to load file '/etc/gdm/custom.conf': No such file or directory
Apr  1 12:24:23 lee-laptop avahi-daemon[882]: Registering new address record for fe80::290:f5ff:fe53:ac8b on eth0.*.
Apr  1 12:24:23 lee-laptop kernel: [   11.421048] CE: hpet increasing min_delta_ns to 15000 nsec
Apr  1 12:24:23 lee-laptop ntpdate[1019]: adjust time server 91.189.94.4 offset -0.353113 sec
Apr  1 12:24:24 lee-laptop gdm-binary[877]: WARNING: GdmDisplay: display lasted 1.099960 seconds
Apr  1 12:24:24 lee-laptop gdm-simple-slave[1022]: WARNING: Unable to load file '/etc/gdm/custom.conf': No such file or directory
Apr  1 12:24:25 lee-laptop gdm-binary[877]: WARNING: GdmDisplay: display lasted 1.108458 seconds
Apr  1 12:24:25 lee-laptop gdm-simple-slave[1029]: WARNING: Unable to load file '/etc/gdm/custom.conf': No such file or directory
Apr  1 12:24:26 lee-laptop gdm-binary[877]: WARNING: GdmDisplay: display lasted 1.095375 seconds
Apr  1 12:24:26 lee-laptop gdm-simple-slave[1036]: WARNING: Unable to load file '/etc/gdm/custom.conf': No such file or directory
Apr  1 12:24:27 lee-laptop gdm-binary[877]: WARNING: GdmDisplay: display lasted 1.091444 seconds
Apr  1 12:24:27 lee-laptop gdm-simple-slave[1043]: WARNING: Unable to load file '/etc/gdm/custom.conf': No such file or directory
Apr  1 12:24:28 lee-laptop gdm-binary[877]: WARNING: GdmDisplay: display lasted 1.091465 seconds
Apr  1 12:24:28 lee-laptop gdm-binary[877]: WARNING: GdmLocalDisplayFactory: maximum number of X display failures reached: check X server log for errors
Apr  1 12:24:28 lee-laptop init: gdm main process (877) terminated with status 1
Apr  1 12:24:32 lee-laptop kernel: [   20.293135] eth0: no IPv6 routers present
Apr  1 12:24:43 lee-laptop init: failsafe-x main process (1050) terminated with status 1

I have also noticed that since the 2nd set of updates I got today (via chroot) now when it boots into the blank screen I have to force the shutdown by holding in my power button (before I could just press it and wait for it to gracefully shutdown)

Thanks

---

### Post by zoomy942 on 2010-04-01
i have intel graphics, not the same one, but i think i will wait till tomorrow to update....wow

---

### Post by Stevi on 2010-04-01
I use the radeonhd driver with nomodeset option and my pc is also not able to boot any more. Is it possible that the boot option "nomodeset" doesn't work at the moment?

---

### Post by gmoore777 on 2010-04-01
Now that I rebooted after getting my updates up to speed,
I get to the grub screen and whether I choose -16 or -18 kernel, I get a black screen. 
and CTL-ALT-F1 or any other F key, does nothing.

I am able to ssh into the machine.

"Display controller: Intel Corporation 4 Series Chipset Integrated Graphics Controller"

---

### Post by pveith on 2010-04-01
Me,too. Kernel -14 still works on my MacBook, but newer ones fail miserably.

It is very confusing, as i get GDM, but if i try to log into Gnome, the screen goes black. I still can do a Xterm Session though.

---

### Post by gmoore777 on 2010-04-01
and loading a live CD in (from 3/31/2010), has same outcome: not just a black/blank screen, but the monitor is in that yellow light state (not green).
Like the video card/driver is non-existent.
So it's not cause I have been upgrading this machine from Alpha1, it's the state of the current software.

---

### Post by macstevejb on 2010-04-02
Ok this was too frustrating so for me so the only workaround was to download the latest daily build from here:

[http://cdimage.ubuntu.com/daily-live/current/](http://cdimage.ubuntu.com/daily-live/current/)

and do a fresh reinstall.

I can now boot without any problem and what is more, I no longer have to use the "nomodeset" option in grub.

Probably not the best solution, but at least my intel-based graphics netbook is working fine again.

Regards, :D

---

### Post by jerrylamos on 2010-04-02
> **venomenus said:**
> Hi Guys!

I updated Lucid today then rebooted and now I just get a blank screen :(

before this update I always booted with nomodeset in grub otherwise I would just get a blank screen but now that doesn't seem to make any difference.

removing quiet splash doesn't seem to show any errors and I cannot get into recovery mode as I just get a black screen in that too also ctrl + alt + F1 doesn't do anything.

My graphics card is a Intel 945GM.

I can boot from an original beta 1 usb stick image (with nomodeset) but I don't know what I can do to fix it from there and what logs would be best to look at, I did view Xorg.0.log and found a "Fatal server issue : no screen found" error though.

Also I don't have/use an Xorg.conf file.

any help would be much appreciated

Thanks
Lee

IBM Thinkpad R31 with i830 graphics.  After aptitude update & safe upgrade yesterday 1 April blank screen no matter what, normal, recovery, nomodeset, no quiet splash, nothing.  I can tell the pc is still running and the keybard works because Ctrl-Alt-Del, Enter does shut down.  I'm entering this from a dual boot from Alpha 3 which is running O.K. (for an alpha).

Let me try keying in an xorg.conf into the Beta.

Jerry

---

### Post by jerrylamos on 2010-04-02
> **jerrylamos said:**
> IBM Thinkpad R31 with i830 graphics.  After aptitude update & safe upgrade yesterday 1 April blank screen no matter what, normal, recovery, nomodeset, no quiet splash, nothing.  I can tell the pc is still running and the keybard works because Ctrl-Alt-Del, Enter does shut down.  I'm entering this from a dual boot from Alpha 3 which is running O.K. (for an alpha).

Let me try keying in an xorg.conf into the Beta.

Jerry

Tried an xorg.conf with vesa in it:
Section "Device"
	Identifier	"Configured Video Device"
	Driver	"vesa"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection

Still no screen.  Lucid Beta useless with no screen.  The 1 April Lucid update made a fool of me.

Jerry

---

### Post by venomenus on 2010-04-02
Hi,

I never did get this working in the end yesterday, I just accessed my data from a live USB stick and just kept checking for updates throughout the day.
I have left my laptop at work over Easter so will not be able to try anything new until Tuesday 8( but hopefully when I go back to work a nice update will be ready and waiting to fix this lol!

I dare not update my main pc or netbook though :p

Worst case scenario I shall try and install off a live daily but its just annoying reinstalling everything.

---

### Post by gmoore777 on 2010-04-02
The April 2nd LiveCD still does not display anything on the monitor
and the latest updates on another machine, still does not fix that machine.
(maybe I will log a bug...)

---

### Post by Billxyzzy on 2010-04-02
To add a bit to this problem.  Yesterday I bought a new
ATI graphics card and installed it.  Everything worked
yesterday.  I did some updates at the end of the day and
also this morning.  The same black screen but in recovery
mode I got to the Checking Battery message where it stops.
What I did is to remove the new card and go back to the
onboard video driver ATI and now am back on.
Later today after more updates I may try to put the
board back in and see if it works.
Check the versions of boards your are running.
Hope this helps.

---

### Post by iClouseau88 on 2010-04-02
I confirmed this.  Downloaded and burned April 2 desktop-i386-iso to a CD. Plymouth seems working OK and Welcome screen appears on desktop pc with Nvidia graphic card.  I did not install it on the desktop pc.  Tried installing on laptop with ATI Radeon Xpress 200M video card.  After initial appearance of Plymouth (pink & purple), the screen went blank. Reboot, Welcome screen appeared , froze then laptop screen went blank. My laptop has 2 GB RAM so RAM is sufficient.

It appears the problem is due to the kernel doesn't recognize either "ati" or "radeon" driver of the video card. How can I change the driver to "vesa" if Lucid Beta1 doesn't even load?

This is quite frustrating!

---

### Post by gmoore777 on 2010-04-02
I just logged this bug against "gdm". Not sure if that was the right package.
[https://bugs.launchpad.net/ubuntu/+source/gdm/+bug/554023](https://bugs.launchpad.net/ubuntu/+source/gdm/+bug/554023)

---

### Post by gmoore777 on 2010-04-05
LiveCD of today, 4/5/2010, still DOA on my
Dell Optiplex 760 with " VGA compatible controller: Intel Corporation 4 Series Chipset Integrated Graphics Controller (rev 03)".

---

### Post by gmoore777 on 2010-04-05
The April 5th LiveCD does work fine booting up on a Dell Optiplex GX 520 with:
 "VGA compatible controller: Intel Corporation 82945G/GZ Integrated Graphics Controller (rev 02)"

---

### Post by dannyboy79 on 2010-04-05
> **gmoore777 said:**
> The April 5th LiveCD does work fine booting up on a Dell Optiplex GX 520 with:
 "VGA compatible controller: Intel Corporation 82945G/GZ Integrated Graphics Controller (rev 02)"

ive been an ubuntu user since 5.04 (forgot name) and I just can't believe how the release cycle can call this a beta release with all these graphic problems. a system isn't usable at all without any darn graphics on it! i haven't had as many problems in the past than with this release. i have normally gone to all the release's prior to final release and haven't had issues like this. I run ati and nvidia cards and one SIS. this is horrible. i know they'll sort it all out by the final release (LTS) but it sure is a bumpy ride this time

---

### Post by venomenus on 2010-04-06
Hi,

I got my laptop working today by adding "i915.modeset=0" instead of nomodeset in grub.

Since then I have also done a fresh install of Lucid from the 5th April Live CD and can also confirm that using this I no longer need either "nomodeset" or "i915.modeset=0" 

Whooopy! :guitar:

---

### Post by amano on 2010-04-06
Well, I updated my system from Karmic to Lucid today and can't boot to the desktop anymore. My Asrock ION 330 just shows a blinking cursor and is loading until the harddisk loading noise suddenly stops. Switching the tty doesn't help, just Ctrl+Alt+Del restarts the system (at least sometimes). The recovery Grub entry prints the boot messages to the screen until everything comes to a halt as well (after some ext4 messages, though not ones indicating any severe errors). 

Adding nomodeset to the Grub parameters (via "E") didn't change anything and manually editing the xorg.conf (from another Ubuntu install) to use nouveau came to nothing. Even deleting the xorg.conf didn't do the trick.

Do you have any other ideas to get my system booting again? I had the closed source 185 drivers installed and those got updated to the 195 ones during the "update-manager -d" distupgrade.

Are there any ASROCK ION users around who can confirm my experience (or have an opposite experience)


Since no splash is showing up I guess that my problem might be driver related. Since nomodeset didn't change anything, it could be a bug in the upgrade path to the new alternative system? 

Any ideas are welcome. I can't even file a bug since I can't see a way to offer some helpful data or helpful symptoms to diagnose the culprit.

---

### Post by amano on 2010-04-06
Needless to say that booting from the live cd works like a charm...

:confused:

---

### Post by venomenus on 2010-04-07
> **amano said:**
> Needless to say that booting from the live cd works like a charm...

:confused:

I don't know if your problem is related to the problem I had but if you can it may just be best to do a fresh install of Lucid from the April 5th Live CD located here [http://cdimage.ubuntu.com/daily-live/20100405/]("http://cdimage.ubuntu.com/daily-live/20100405/")
:(

---

### Post by amano on 2010-04-07
That might get the OS going again, but then the bug remains uncovered/undebugged.

If there is really a problem with the upgrade path, the update might eat a lot of installs for the big crowd of users that upgrade when the final ubuntu is released.

Did you file a bug where I can contribute?

---

### Post by venomenus on 2010-04-07
Hi,

gmoore777 has a bug filed here [https://bugs.launchpad.net/ubuntu/+s...dm/+bug/554023]("https://bugs.launchpad.net/ubuntu/+s...dm/+bug/554023") though I am not sure if its related to the problem you are having.

Thanks

---

### Post by gmoore777 on 2010-04-07
Doesn't sound like the same bug, as the LiveCD, as of April 5th, 
still won't boot in my Dell Optiplex 780 machines with the "VGA compatible controller: Intel Corporation 4 Series Chipset Integrated Graphics Controller (rev 03)".
Since Amano can boot with the April 5th LiveCD, his problem is probably something different although his symptoms seem similar.

After the machine "stops", can you `ssh` in from another machine?
(this assumes that you had ssh installed prior to the upgrade and that you have a second machine.)

What VGA controller do you have?  Load LiveCD and run `lspci`

---

### Post by amano on 2010-04-07
No second machine at my command here, sorry. :(

Well. I will install from the live disk then. ;)

---

### Post by amano on 2010-04-07
Ok the plot thickens. I reinstalled Lucid (almost) Beta 2 and I cannot install the proprietary nVidia drivers via jockey:

> 2010-04-07 20:36:19,411 DEBUG: Installing package: nvidia-current
2010-04-07 20:40:24,103 DEBUG: install progress statusChange dpkg-exec 0.000000
2010-04-07 20:40:25,699 DEBUG: install progress statusChange dkms 0.000000
2010-04-07 20:40:25,700 DEBUG: install progress statusChange dkms 4.000000
2010-04-07 20:40:26,097 DEBUG: install progress statusChange dkms 8.000000
2010-04-07 20:40:26,147 DEBUG: install progress statusChange dkms 12.000000
2010-04-07 20:40:26,296 DEBUG: install progress statusChange fakeroot 12.000000
2010-04-07 20:40:26,297 DEBUG: install progress statusChange fakeroot 16.000000
2010-04-07 20:40:26,536 DEBUG: install progress statusChange fakeroot 20.000000
2010-04-07 20:40:26,574 DEBUG: install progress statusChange fakeroot 24.000000
2010-04-07 20:40:26,698 DEBUG: install progress statusChange patch 24.000000
2010-04-07 20:40:26,700 DEBUG: install progress statusChange patch 28.000000
2010-04-07 20:40:26,863 DEBUG: install progress statusChange patch 32.000000
2010-04-07 20:40:26,901 DEBUG: install progress statusChange patch 36.000000
2010-04-07 20:40:27,033 DEBUG: install progress statusChange nvidia-current 36.000000
2010-04-07 20:40:27,034 DEBUG: install progress statusChange nvidia-current 40.000000
2010-04-07 20:40:47,039 DEBUG: install progress statusChange nvidia-current 44.000000
2010-04-07 20:40:47,083 DEBUG: install progress statusChange nvidia-current 48.000000
2010-04-07 20:40:47,209 DEBUG: install progress statusChange nvidia-settings 48.000000
2010-04-07 20:40:47,312 DEBUG: install progress statusChange nvidia-settings 52.000000
2010-04-07 20:40:47,426 DEBUG: install progress statusChange nvidia-settings 56.000000
2010-04-07 20:40:47,464 DEBUG: install progress statusChange nvidia-settings 60.000000
2010-04-07 20:40:47,506 DEBUG: install progress statusChange man-db 60.000000
2010-04-07 20:40:50,193 DEBUG: install progress statusChange dpkg-exec 60.000000
2010-04-07 20:40:50,442 DEBUG: install progress statusChange dkms 60.000000
2010-04-07 20:40:51,077 DEBUG: install progress statusChange dkms 64.000000
2010-04-07 20:40:51,119 DEBUG: install progress statusChange dkms 68.000000
2010-04-07 20:40:51,156 DEBUG: install progress statusChange fakeroot 68.000000
2010-04-07 20:40:51,190 DEBUG: install progress statusChange fakeroot 72.000000
2010-04-07 20:40:51,711 DEBUG: install progress statusChange fakeroot 76.000000
2010-04-07 20:40:51,757 DEBUG: install progress statusChange patch 76.000000
2010-04-07 20:40:51,802 DEBUG: install progress statusChange patch 80.000000
2010-04-07 20:40:51,837 DEBUG: install progress statusChange patch 84.000000
2010-04-07 20:40:51,871 DEBUG: install progress statusChange nvidia-current 84.000000
2010-04-07 20:40:51,939 DEBUG: install progress statusChange nvidia-current 88.000000
2010-04-07 20:42:13,154 DEBUG: install progress statusChange nvidia-current 92.000000
2010-04-07 20:42:13,372 DEBUG: install progress statusChange nvidia-settings 92.000000
2010-04-07 20:42:13,429 DEBUG: install progress statusChange nvidia-settings 96.000000
2010-04-07 20:42:13,485 DEBUG: install progress statusChange nvidia-settings 100.000000
2010-04-07 20:42:13,543 DEBUG: install progress statusChange python-gmenu 100.000000
2010-04-07 20:42:14,562 DEBUG: install progress statusChange initramfs-tools 100.000000
2010-04-07 20:42:34,301 DEBUG: install progress statusChange python-support 100.000000
2010-04-07 20:42:36,520 DEBUG: Selecting previously deselected package dkms.
(Reading database ... 124579 files and directories currently installed.)
Unpacking dkms (from .../dkms_2.1.1.2-2fakesync1_all.deb) ...
Selecting previously deselected package fakeroot.
Unpacking fakeroot (from .../fakeroot_1.14.4-1ubuntu1_amd64.deb) ...
Selecting previously deselected package patch.
Unpacking patch (from .../patch_2.6-2ubuntu1_amd64.deb) ...
Selecting previously deselected package nvidia-current.
Unpacking nvidia-current (from .../nvidia-current_195.36.15-0ubuntu1_amd64.deb) ...
Selecting previously deselected package nvidia-settings.
Unpacking nvidia-settings (from .../nvidia-settings_195.36.08-0ubuntu1_amd64.deb) ...
Processing triggers for man-db ...
Setting up dkms (2.1.1.2-2fakesync1) ...

Setting up fakeroot (1.14.4-1ubuntu1) ...
update-alternatives: using /usr/bin/fakeroot-sysv to provide /usr/bin/fakeroot (fakeroot) in auto mode.

Setting up patch (2.6-2ubuntu1) ...
Setting up nvidia-current (195.36.15-0ubuntu1) ...
update-alternatives: using /usr/lib/nvidia-current/ld.so.conf to provide /etc/ld.so.conf.d/GL.conf (gl_conf) in auto mode.
update-initramfs: deferring update (trigger activated)
Loading new nvidia-current-195.36.15 DKMS files...
First Installation: checking all kernels...
Building only for 2.6.32-19-generic
Building for architecture x86_64
Building initial module for 2.6.32-19-generic
Done.

nvidia-current.ko:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/2.6.32-19-generic/updates/dkms/

depmod........

DKMS: install Completed.

Setting up nvidia-settings (195.36.08-0ubuntu1) ...
Processing triggers for python-gmenu ...
Rebuilding /usr/share/applications/desktop.POSIX.cache...
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.32-19-generic
Processing triggers for python-support ...

2010-04-07 20:42:39,069 DEBUG: XorgDriverHandler device sections ({0: ['\tIdentifier\t"Default Device"\n', '\tOption\t"NoLogo"\t"True"\n', '\tDriver\t"nvidia"\n']})
2010-04-07 20:44:40,424 DEBUG: XorgDriverHandler device sections ({0: ['\tIdentifier\t"Default Device"\n', '\tOption\t"NoLogo"\t"True"\n', '\tDriver\t"nvidia"\n']})
2010-04-07 20:46:36,923 DEBUG: XorgDriverHandler device sections ({0: ['\tIdentifier\t"Default Device"\n', '\tOption\t"NoLogo"\t"True"\n', '\tDriver\t"nvidia"\n']})

---

### Post by dannyboy79 on 2010-04-07
> **amano said:**
> Well, I updated my system from Karmic to Lucid today and can't boot to the desktop anymore. My Asrock ION 330 just shows a blinking cursor and is loading until the harddisk loading noise suddenly stops. Switching the tty doesn't help, just Ctrl+Alt+Del restarts the system (at least sometimes). The recovery Grub entry prints the boot messages to the screen until everything comes to a halt as well (after some ext4 messages, though not ones indicating any severe errors). 

Adding nomodeset to the Grub parameters (via "E") didn't change anything and manually editing the xorg.conf (from another Ubuntu install) to use nouveau came to nothing. Even deleting the xorg.conf didn't do the trick.

Do you have any other ideas to get my system booting again? I had the closed source 185 drivers installed and those got updated to the 195 ones during the "update-manager -d" distupgrade.

Are there any ASROCK ION users around who can confirm my experience (or have an opposite experience)


Since no splash is showing up I guess that my problem might be driver related. Since nomodeset didn't change anything, it could be a bug in the upgrade path to the new alternative system? 

Any ideas are welcome. I can't even file a bug since I can't see a way to offer some helpful data or helpful symptoms to diagnose the culprit.

edit your boot line within your grub and remove "quiet splash". that's what I did and I get right gdm. however, after entering clicking on my username and entering the password, screen goes black and Im presented with gdm again. it's a loop. so I just go to tty1, then stop gdm with sudo service gdm stop, then i just type startx, and I am brought to the desktop. NICE

---

### Post by dannyboy79 on 2010-04-07
> **amano said:**
> Ok the plot thickens. I reinstalled Lucid (almost) Beta 2 and I cannot install the proprietary nVidia drivers via jockey:

straight from teh ubuntu lucid changes page.
[http://www.ubuntu.com/testing/lucid/alpha2](http://www.ubuntu.com/testing/lucid/alpha2)

Jockey (Ubuntu's restricted driver manager) doesn't yet support the new alternatives system used by the nvidia driver packages, so in order to install nvidia drivers you will have to install them from the command line: 
sudo apt-get install nvidia-current (or nvidia-173 or nvidia-96) 

select the alternative that matches the driver that you have installed 
(e.g. /usr/lib/nvidia-current/ld.so.conf for nvidia-current): 

sudo update-alternatives --config gl_conf 

update the ld cache: 
sudo ldconfig 

then configure your xorg.conf with: 
sudo nvidia-xconfig 

And restart your computer.

---

### Post by amano on 2010-04-07
Well, though not being hooked up by jockey yet, the drivers seem to have been installed and seem to work...

---

