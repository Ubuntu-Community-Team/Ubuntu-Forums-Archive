---
title: "Can't upgrade Please help!"
date: 2010-02-14
forum: Installation &amp; Upgrades
---

### Post by redcrystalmoon on 2010-02-14
So my computer (asus netbook) is currently running eeebuntu 9.04 and I was trying to upgrade to 9.10 ubuntu. 
I've had a number of problems so not sure where to start... I'll try to keep it brief.
my computer was running fine but started to lag so I updated, which cause my wireless to not work anymore... (Apparently the new kernel didn't support my atheros (AR242x) wireless card.)
I tried to get ndiswrapper working with no success.

To make a long story short I just decided to do a fresh install of koala and downloaded the iso. But, before I could load it onto a usb, I decided to see if I could just upgrade right from the update manager. I followed a tutorial from the ubuntu page about doing a clean upgrade which involved removing third party packages and repositories.

(I should mention that before I even did the updates initially, I *was *prompted to upgrade but decided not to at that point. Then after the updates, some of which did not get fully installed, there was no more option for the upgrade. I'm assuming that's because not all of the updates were done for whatever reason[the error said something about the repositories])

So I created a third party filter in synaptic and removed the following packages:
-adobe-flashplugin
-linux headers-2.6.28-12
-linux headers-2.6.29-1
-linux-image-2.6.29-1-netbook
-medibuntu-keyring
-python-software-properties

there was also -base files and -python-apt in the list but I opted to keep them there since they had a long list of dependencies which would have also been removed.

The next step in the tutorial was to uncheck the third party software boxes in the repos tab within synaptic, but when I went there it looked quite different than normal and there were no tabs at all and no place to see which repos were from where, just a list of all them, some grey'd out.

I went to system-administration and looked for the icon 'software sources' which usually brings me to the same screen but it was missing... So, I went back in and reinstalled Python-software-properties, and medibuntu-keyring not really knowing which thing I had taken out that would have caused it to leave. (assumed the python package, admittedly I'm not even sure what medibuntu is... kind of an armature!) Either way, the software sources icon did not reappear and neither did the software window from synaptic change back to normal so I thought I might have to reboot....

Now! my computer wont even boot up into eeebuntu GUI anymore and gives me this message when I try to turn it on:

udevam trigger is not permitted while udev is unconfigured. gave up waiting for root device. common problems:
-Boot args (cat /proc/cmdline)
-check rootdelay=(did the system wait long enough?)
-check root=(did the system wait for the right device?)
-missing modules (cat /proc/modules; ls/dev)

Alert /dev/disk/b1-vuid/678cad37-eo7a-4fa3-9bd2-b4e673bed3od does not exist. Dropping to a shell!

BusyBox v1.10.2 (ubuntu1:1.102-2ubuntu7) built-in shell(ash)

(initramfs)


And I have NO idea what that means!
I just want to get into my desktop and get that iso off there to I can do a fresh install and kiss all these problems goodby! (assuming, or moreover hoping, that my wireless works out of the box with koala!)

If anyone can shed some light on this for me I would greatly appreciate it because I have no clue what to do next!
Thank you!

(I guess that wasn't too brief... sorry...)

---

### Post by Satoru-san on 2010-02-14
Are you able to still boot one of your old kernels, this will help us know where to start. Thanks.

When you pass POST hold down the shift key to get grub menu

---

### Post by redcrystalmoon on 2010-02-14
ahh ok, I was able to boot up to a previous kernel, 2.6.11 I think...
Should have just tried that first...  like I said, ameture... thanks. at least I can get the iso...
I'm not sure what your second sentence meant though...
geeze I thought I was actually learning about all this but once I have a problem I realize how much I'm in the dark about how this stuff really works...
Thanks for your reply! 

(that was a quick fix... wish I could get my second card reader working that fast! lol)

---

### Post by Satoru-san on 2010-02-14
> **redcrystalmoon said:**
> 
I'm not sure what your second sentence meant though...
hehe, if you were able to boot your old kernel you did just that. :P

The computer when it boots does a Power On Self Test (P.O.S.T.) when it passes that it loads grub, which in ubuntu the time out is 0 seconds, so you have to hold down shift to get a menu.

If you want to continue to use an older kernel you can switch the order of the kernels so the old one is at the top.
```
gksudo gedit /etc/defaults/grub
sudo update-grub
```

This might fix your new kernel 

```
sudo apt-get purge <kernel version>
sudo apt-get install <kernel version>
```

cheers.

---

### Post by redcrystalmoon on 2010-02-14
lol thanks ;o)
I just pressed "esc" when the little thingie was counting down... but I appreciate knowing the technical terms...

I'm checking out koala now from my flash drive and it's pretty snazzy, the wireless works and it seems to be much faster on my machine already, even from the usb, so I'm not going to bother with trying to fix the old one, I'm just going to do a fresh install...
Thanks again for your replys!

~RCM

---

### Post by Satoru-san on 2010-02-14
No problem, in thread tools there is an option to mark as solved, please do so.

Have fun.:popcorn:

---

### Post by redcrystalmoon on 2010-02-14
Oh, but I do have one more question if your up for answering...
I want to switch my file system from ext3 to ext4 and in the release notes it says I have to "use the grub-install command to reinstall my boot loader. 
Does that mean I just type in sudo grub-install ? because when I tried that to see what would happen it told me my command was wrong... or more specifically... "device not specified" and some other stuff...
I, *am* learning... but I'm not intuitive about the terminal yet!

---

### Post by Satoru-san on 2010-02-14
I don't use ubuntu, so I cant tell you, but you can do this to get help on anything...

```
man <command>
info <command>
<command> --help
```All have their own purpose, there is even online linux man pages.

:)

I take that back I have that command 

```
NAME
       grub-install - install GRUB on your drive

SYNOPSIS
       grub-install [OPTION] install_device

DESCRIPTION
       Install GRUB on your drive.

```

You need to put device after it ie /dev/sda1 or whatever yoru /boot thing goes to in fstab

---

### Post by redcrystalmoon on 2010-02-14
Hmm, I ran info-grub and it's telling me about installing, Now I'm scared! lol
I really don't know my way around well enough to get myself out of a jam if I brick my computer!
I'd like to switch to etx4 because I believe it's better and possibly faster(?) but I don't want to run the wrong command and break it either... it's telling me there's a bunch of different ways to do it and if I don't get the right one my computer quite possibly wont boot...
Maybe I should just stick with ext3...

Or maybe that's just being a quitter,lol
I'm gonna do some more reading...

---

### Post by redcrystalmoon on 2010-02-14
HaHa!
I just decided to go for it, install and see what happens and It automatically loads in ext4 anyway... lol
Thanks for your help ;o)

---

### Post by Satoru-san on 2010-02-14
EDIT: Thats good to hear you didnt "brick" it.


Dont worry thats not possible :) 
look at man chroot.

You cant break linux.... EVER! you should NEVER have to reinstall. EVER!:p

---

