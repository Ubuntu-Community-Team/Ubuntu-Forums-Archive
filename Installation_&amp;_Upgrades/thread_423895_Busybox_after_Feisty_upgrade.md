---
title: "Busybox after Feisty upgrade"
date: 2007-04-26
forum: Installation &amp; Upgrades
---

### Post by villelai on 2007-04-26
After upgrading my Edgy to Feisty, I got following errors:

[[IMG]http://img238.imageshack.us/img238/3149/82678324lt1.jpg[/IMG]](http://imageshack.us)

[[IMG]http://img238.imageshack.us/img238/4664/87329727wf5.jpg[/IMG]](http://imageshack.us)

Rescue mode didn't work either. With newest kernel from Edgy (2.6.17-11-generic) I got same messages. I used this kernel before update and it worked with Edgy.
Surprisingly older kernel (2.6.17-10-generic) works quite well (nvidia binary drivers don't work). But of course I would like to use newest kernel (2.6.20-15-generic).

I have
Asus P5B
Intel E6300
Geforce 7600GS
250GB SATA HDD

In /boot/grub/menu.lst I have kernel parameters for every kernel
root=UUID=865f899d-7647-4293-9c16-37ed7683e487 ro quiet locale=fi_FI
I tried root=/dev/sda1 too and it didn't make difference.

Any idea how to solve problem?

Edit: I forgot to mention that Feisty liveCD booted all right. No problems with that. I haven't tried clean install because I want keep my programs, settings, etc.

---

### Post by sk8dork on 2007-04-26
my dad was going to try out ubuntu with this latest release (he's a windows guy working for dell) and he got this same thing when he tried to boot the latest feisty liveCD. i didn't know what to tell him. he has a seperate sata drive he wanted to load ubuntu on to dual boot with windows, but he never got to the desktop. more info on this issue would be greatly appreciated, as i would love to get him into ubuntu and away from windows.

i was thinking before that the alternative CD might help, but seeing as you got this after upgrading to feisty and he got it trying to boot into the liveCD, i'm not sure it will help.

---

### Post by villelai on 2007-04-26
I forgot to mention that Feisty liveCD booted all right. No problems with that. I haven't tried clean install because I want keep my programs, settings, etc.

---

### Post by John Jason Jordan on 2007-04-26
> **villelai said:**
> I forgot to mention that Feisty liveCD booted all right. No problems with that. I haven't tried clean install because I want keep my programs, settings, etc.
Similar thing happened to me. Took me a long time to resolve, mostly because of the time spent learning how to do it. Here is the thread where I posted how I fixed it.

[http://ubuntuforums.org/showthread.php?t=419724](http://ubuntuforums.org/showthread.php?t=419724)

---

### Post by villelai on 2007-04-26
> **John Jason Jordan said:**
> Similar thing happened to me. Took me a long time to resolve, mostly because of the time spent learning how to do it. Here is the thread where I posted how I fixed it.

[http://ubuntuforums.org/showthread.php?t=419724](http://ubuntuforums.org/showthread.php?t=419724)

I'm sorry but that didn't help. My menu.list is ok (I suppose), and I can boot with old kernel.

---

### Post by John Jason Jordan on 2007-04-26
> **villelai said:**
> I'm sorry but that didn't help. My menu.list is ok (I suppose), and I can boot with old kernel.
Did you do this part?

----
First, boot to the live/install CD, then open a terminal. Then create a folder for a mount point and mount the partition where your borked Ubuntu is installed. In my case that is hda2 (throughout the following change "hda2" to whatever your partition is):

sudo mkdir /media/hda2
sudo mount /dev/hda2 /media/hda2

Then do:

sudo mount -o bind /dev /media/hda2/dev
sudo mount -o bind /proc /media/hda2/proc

The purpose is to mount bind the /dev and /proc folders on the borked installation to the live CD copy that is running. Otherwise a lot of the apt-get and dpkg commands will not complete correctly. And then chroot yourself into the borked installation:

sudo chroot /media/hda2

That will put you at a root prompt, so the sudo's are no longer necessary. Now just do

apt-get -install -f
and
dpkg --configure -a

And you should have much better luck getting the borked installation fixed. You may have to run them over a few times, alternating each time.

In my case after apt-get install -f and then dpkg --configure -a at the end it said it couldn't fix acpi-support, powermanagement-interface, gnome-power-manager, and gnome-session. I tried to remove them with dpkg -r <package> and then reinstall, but stopped after the first one. That is, I successfully rremoved acpi-support, but then couldn't reinstall it. After that I decided to leave well enough alone and try to boot.
-----

The key is to chroot to your old partition from the live CD, then mount bind /proc and /dev to get them out of the way, and then fix the upgrade from the command line.

---

### Post by villelai on 2007-04-26
> **John Jason Jordan said:**
> Did you do this part?
...


I think there is no need to do that because I have working Feisty install (with old kernel) and I have no broken packets. I can do apt-get -install -f and dpkg --configure -a but they do nothing. The problem is somewhere else.

---

### Post by sk8dork on 2007-04-27
this may be a shot in the dark but i have gotten over issues on my systems when going to a newer kernel by booting to recovery mode for the kernel and doing 
sudo aptitude update
sudo aptitude dist-upgrade
worth a shot if you can get to the command prompt in recovery mode.

---

### Post by villelai on 2007-04-29
> **sk8dork said:**
> this may be a shot in the dark but i have gotten over issues on my systems when going to a newer kernel by booting to recovery mode for the kernel and doing 
sudo aptitude update
sudo aptitude dist-upgrade
worth a shot if you can get to the command prompt in recovery mode.

I can't boot to rescue mode with new kernel. Same busybox again.

---

### Post by villelai on 2007-04-29
I solved the problem. I reinstalled all stuff related to newest kernel and it booted!

---

