---
title: "how to install 11.10 on HP Compaq 8200 Elite all-in-one"
date: 2012-01-19
forum: Installation &amp; Upgrades
---

### Post by gleedadswell on 2012-01-19
Hi everyone,

I've successfully installed 11.10 on an HP Compaq 8200 Elite all-in-one.  There is a known bug:

[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/887756](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/887756)

which makes this nontrivial.  The comments on the bug report page helped me to figure out how to do it, but there were enough steps that I thought it would be helpful to document it a bit.

The crux of the problem is that the LiveCD (I actually used the LiveCD image written to a usb key) boots to a blank screen.  To fix it you need to mess with grub, which if you're a total n00b like me is a little scary.

So I did my grub setup on my install USB key manually.  There's a good step-by-step set of instructions for doing this at:

[http://www.pendrivelinux.com/boot-multiple-iso-from-usb-via-grub2-using-linux/](http://www.pendrivelinux.com/boot-multiple-iso-from-usb-via-grub2-using-linux/)

I then put my ubuntu LiveCD .iso and edited the /boot/grub/grub.cfg on the usb key.  The key, as the bug report says, is that we need "nosplash nomodeset" as boot options.  So here is the grub.cfg (make sure the file name of the .iso matches the file name in grub.cfg).  You shouldn't normally manually edit a grub.cfg, but this is just on a temporary filesystem that will never have grub-update run on it, so it's OK. 

```
set timeout=10
set default=0

menuentry "Run Ubuntu Live ISO" {
 loopback loop /ubuntu.iso
 linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=/ubuntu.iso nosplash nomodeset
 initrd (loop)/casper/initrd.lz
}
```

So far so good.  This should bring up the grub menu, you hit enter to start up the .iso, and the LiveCD .iso runs flawlessly.  BUT...

If you reboot after the install you boot to a blank screen!  This is because now the grub.cfg on your hard drive also needs the "nosplash nomodeset" options.  The easiest way is probably to boot from the LiveCD .iso again.  Once booted, mount the hard drive partition where Ubuntu is installed (easiest using Disk Utility).  Open a terminal and invoke superuser privileges (I just do sudo -i but others seem to prefer prefixing every command with sudo).

Navigate to where the hard drive partition is mounted.  It will be in /media with a name that is likely just a big string of random looking characters.

The difficulty is that editing grub.cfg directly is a bad idea.  Partly because we could really mess up the system if we make a mistake and partly because our grub.cfg could be overwritten during an upgrade.  Instead we have to tell grub-update how to write grub.cfg the way we want it.  This turns out to be easy.  We have to set an environment variable called GRUB_CMDLINE_LINUX_DEFAULT.  This is done in

/etc/default/grub

So just open that to edit it in your favourite text editor.  It is probably set to

"quiet splash"

Replace this with

"quiet nosplash nomodeset"

Save and exit.  Now from the command line run grub-update.

Voila!  We're done.

Now if I can just get Unity 3D working on it...

---

### Post by gleedadswell on 2012-03-05
And now I've got Unity 3D working.

See this thread

[http://ubuntuforums.org/showthread.php?p=11741801#post11741801]("http://ubuntuforums.org/showthread.php?p=11741801#post11741801")

for the blow-by-blow, mostly about things that didn't work.

What finally worked was to upgrade to the linux-3.2 kernel.  I got an ubuntu build of the 3.2 kernel from here:

[http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.2-rc4-oneiric/]("http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.2-rc4-oneiric/")

Grab the files:

linux-headers-3.2.0-030200rc4-generic_3.2.0-030200rc4.201112012035_i386.deb
linux-headers-3.2.0-030200rc4_3.2.0-030200rc4.201112012035_all.deb
linux-image-3.2.0-030200rc4-generic_3.2.0-030200rc4.201112012035_i386.deb

Then, from where ever those landed in your directory structure do

sudo dpkg -i linux*.deb

Now the installation should work without the "nomodeset" option in grub.  So, with root privileges open

/etc/default/grub

In the line that sets GRUB_CMDLINE_LINUX_DEFAULT remove "nomodeset".  Now, as root, run

update-grub

Finally, reboot.  If you log in to the ubuntu desktop now it should have full 3D.  Verify by running "echo $DESKTOP_SESSION" and it should now report

geoff@kinetic-poincare:~$ echo $DESKTOP_SESSION
ubuntu

Hooray!  It all works!

---

### Post by djvujke on 2012-04-25
hello
i have HP Compaq 8200 Elite all in one PC , product no. LN055AV1
Chipset Intel® Q67 Express, Intel(R) Core(TM) i3-2130 CPU @ 3.40GHz
with integrated Intel HD 2000 card

i have currently installed LinuxMint 12 KDE 64bit with kernel 3.0.0-17-generic with kernel option i915.modeset=0 (equal as nomodeset) or otherwise i would end up with black screen.
I have tried booting with acpi_osi=linux pci=noacpi and also with acpi=off but just black screen, although i can hear my hdd working and loggon by heart and hear that its logged on KDE.

i have included xorg-edgers hopping i'll get newer drivers but nothing.

i have also noticed that when ever i play a video file , no matter the format (avi,mov,flv) and no matter the video app (mplayer, vlc) i have this 1 second full black screen , before video starts normally , which also happens when closing video file or continuing further on the list.
But i guess this is beacuse VESA is in use

# inxi -Gx
Graphics: Card: Intel 2nd Generation Core Processor Family Integrated Graphics Controller bus-ID: 00:02.0 
 X.org 2) drivers vesa,intel unloaded: fbdev tty size 189x34 Advanced Data: N/A for root

After this hustle i've manually installed kernel 3.2 packages but still couldn't boot without nomodeset option to workable GUI.

how the heck did you do it?

---

### Post by djvujke on 2012-04-27
I've managed to fix it. i added this 
deb [http://ppa.launchpad.net/francisbrwn9/kernels/ubuntu](http://ppa.launchpad.net/francisbrwn9/kernels/ubuntu) quantal main 
deb-src [http://ppa.launchpad.net/francisbrwn9/kernels/ubuntu](http://ppa.launchpad.net/francisbrwn9/kernels/ubuntu) quantal main 
and installed the kernel and it worked.
previously i manually installed same kernel version 3.2 but from another site by manually downlading and installing packages.

confirm that kernel 3.2 has fixed the issue.

---

