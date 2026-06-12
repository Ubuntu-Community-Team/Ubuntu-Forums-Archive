---
title: "USB Lucid Bug - Work around in plain English"
date: 2010-05-30
forum: Installation &amp; Upgrades
---

### Post by Badjah on 2010-05-30
Hello All.

I am really not very Linux savy. Have been using Karmic for about a year and wanted to test Lucid NBR on my netbook by running it from a USB stick first. Had loads of problems and bugs with it - However even an idiot like me can work out most of them. However I am suffering from this bug (I think)

[https://bugs.launchpad.net/ubuntu/+source/casper/+bug/557023](https://bugs.launchpad.net/ubuntu/+source/casper/+bug/557023)

when I run apt-get dist-upgrade I get:

```
ubuntu@ubuntu:~$ sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
3 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
Setting up linux-image-2.6.32-22-generic (2.6.32-22.33) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.32-22-generic
cp: cannot stat `/vmlinuz': No such file or directory
Failed to create initrd image.
dpkg: error processing linux-image-2.6.32-22-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-2.6.32-22-generic; however:
  Package linux-image-2.6.32-22-generic is not configured yet.
dpkg: error processing linux-image-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-generic:
 linux-generic depends on linux-image-generic (= 2.6.32.22.23); however:
  Package linux-image-generic is not configured yet.
dpkg: error processing linux-generic (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                                                                                                          No apport report written because the error message indicates its a followup error from a previous failure.
                                                                                       Errors were encountered while processing:
 linux-image-2.6.32-22-generic
 linux-image-generic
 linux-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)

```I notice in the bug reports there were some work arounds. Can anyone explain these to me in a step by step way, in plain English so even an idiot like me can follow it?

Workarounds are

> == workaround ==
create /vmlinuz symbolic link to point to /cdrom/casper/vmlinuz
 $ ln -s /cdrom/casper/vmlinuz /vmlinuz
and

> Workaround was to copy /cdrom/casper/vmlinuz to /boot/vmlinuz-2.6.32-19-generic.  After reinstalling initramfs-tools, /vmlinuz was a link to  /boot/vmlinuz-2.6.32-20-generic as expected.
What are these guys on about? I tried to do what I think they meant - didn't work - I reckon i got it wrong

Please help nice Ubuntu community!! :)

---

### Post by mikewhatever on 2010-05-30
The command as given (ln -s /cdrom/casper/vmlinuz /vmlinuz) will create a symbolic link. Not quite sure where the second part comes from. In case something doesn't work, post the output.
What I don't understand is, why update the kernel on a live usb.

---

### Post by Badjah on 2010-05-30
> **mikewhatever said:**
> The command as given (ln -s /cdrom/casper/vmlinuz /vmlinuz) will create a symbolic link. Not quite sure where the second part comes from. In case something doesn't work, post the output.

Tried that. Then ran dist-upgrade again, same problem. I assume there was no need to reboot? The output above IS the one that came after I tried: $ ln -s /cdrom/casper/vmlinuz /vmlinuz
 
> What I don't understand is, why update the kernel on a live usb.Maybe rather foolishly I was hoping it may help fix another problem I am having whereby the touchpad freezes when Ubuntu establishes a wifi connection - maybe this is stupid, i don't know - seemed worth a go, no? Obviously I'd rather not install Lucid in full until I got some of the more annoying bugs fixed.

---

### Post by ugm6hr on 2010-05-30
Is it even possible to upgrade the kernel on a LiveUSB?

To use the new kernel, you would have to reboot. Rebooting will undo any updates / upgrades, so you'll be back where you started.

---

### Post by Badjah on 2010-05-30
> **ugm6hr said:**
> Is it even possible to upgrade the kernel on a LiveUSB?

To use the new kernel, you would have to reboot. Rebooting will undo any updates / upgrades, so you'll be back where you started.

Yeah I would have thought so too; however I had to install some stuff to get the wifi adapter to work with Lucid and also ran an apt-get upgrade, all the changes seemed to stick, wifi worked, all the upgrades seemed to stick (apart from the kernel) after several reboots. I have even installed skype and that is still there (working fine) even when I have taken the USB out and rebooted it the following day. Maybe I'm missing something, I just thought if all those installations and upgrades would stick, the kernel upgrade may do too. 

As I say I'm not very linux savy, I just try stuff and see what happens!

---

### Post by mikewhatever on 2010-05-30
I think he is symlinking /cdrom/casper/vmlinuz from cdrom to /vmlinuz on the live usb. I'll try it, just for the heck of it.

---

### Post by Badjah on 2010-05-30
> **mikewhatever said:**
> I think he is symlinking /cdrom/casper/vmlinuz from cdrom to /vmlinuz on the live usb. I'll try it, just for the heck of it.

As I said before, I am a bit clueless about a lot of stuff - what does this mean ?

What I got so far anyway is that I am trying to do the impossible (i.e trying to get a half working installation on a USB before installing it)  - well that doesn't surprise me! 

I guess I'll juts have to wait until 10.10 coz 10.04 is really far too buggy for me to want to install it at this stage. Could try Karmic, I s'pose. Never mind guys, thanks for your input anyway.

---

### Post by mikewhatever on 2010-05-30
> **Badjah said:**
> As I said before, I am a bit clueless about a lot of stuff - what does this mean ?

Well, the workaround apparently works, as I was able to install linux-image-2.6.32-22-generic and boot it. What it means is, some under the hood, command line hacking. Nothing major, but then, the level of difficulty depends on one's level of experience with this stuff. I consider mine as advanced beginner, whatever that means.

---

### Post by Badjah on 2010-05-30
> **mikewhatever said:**
> Well, the workaround apparently works, as I was able to install linux-image-2.6.32-22-generic and boot it. What it means is, some under the hood, command line hacking. Nothing major, but then, the level of difficulty depends on one's level of experience with this stuff. I consider mine as advanced beginner, whatever that means.

Can you post what you did in the command line?
So it is not impossible to upgrade the kernel on a live USB then?

---

### Post by darkod on 2010-05-30
> **Badjah said:**
> As I said before, I am a bit clueless about a lot of stuff - what does this mean ?

What I got so far anyway is that I am trying to do the impossible (i.e trying to get a half working installation on a USB before installing it)  - well that doesn't surprise me! 

I guess I'll juts have to wait until 10.10 coz 10.04 is really far too buggy for me to want to install it at this stage. Could try Karmic, I s'pose. Never mind guys, thanks for your input anyway.

I wouldn't say 10.04 is too buggy. Besides, 10.04 is LTS and you are far better installing that than 10.10 which will be 'standard' version. LTS has support for 3yrs, the versions in between only 18 months.

You are making things too complicated yourself, like you said, by trying to make everything to work in live mode.

Install it on your hdd, and start fixing things one by one. That way the fixes will stay permanent, and also the commands and tutorials you will be finding for those fixes will be written for a hdd install, there is no way to tell if they will work or not only in live mode.

Some fixes that you think didn't work, might as well work in hdd install.

The way you are trying to do it, there is really no way to tell what is happening and what not. Just my humble opinion.

---

### Post by Badjah on 2010-05-30
> **darkod said:**
> I wouldn't say 10.04 is too buggy. Besides, 10.04 is LTS and you are far better installing that than 10.10 which will be 'standard' version. LTS has support for 3yrs, the versions in between only 18 months.

You are making things too complicated yourself, like you said, by trying to make everything to work in live mode.

Install it on your hdd, and start fixing things one by one. That way the fixes will stay permanent, and also the commands and tutorials you will be finding for those fixes will be written for a hdd install, there is no way to tell if they will work or not only in live mode.

Some fixes that you think didn't work, might as well work in hdd install.

The way you are trying to do it, there is really no way to tell what is happening and what not. Just my humble opinion.

Cheers for that. So the stuff I have sorted in live mode, like the wifi, for example may not work when I come to do a full install? Thus I may as well just take the plunge. Hmm Am a bit nervous tbh! I don't wanna accidentally screw up my Win7 install if I can't even get a smooth version of linux for my troubles- is the only version of windows I have ever even slightly liked using!

Also, not meaning to offend, as I probably don't know what I am talking about; but does this not defeat the whole point of the live environment? I mean if you try the live version and its all buggy and yet this does not give you any indication how buggy it will be on the full install then what's the point of the live environment, apart from recovery?

---

### Post by darkod on 2010-05-30
> **Badjah said:**
> Cheers for that. So the stuff I have sorted in live mode, like the wifi, for example may not work when I come to do a full install? Thus I may as well just take the plunge. Hmm Am a bit nervous tbh!

The fixes that worked, will probably work. But you'll have to do them again, the installer won't install them for you.
But also the fixes that didn't work (if there are any), might actually work after you install and try to apply them in the full installation.

---

### Post by darkod on 2010-05-30
If you need to make space on the hdd for ubuntu, it's best to shrink the win7 partition using win7 Disk Management. Leave the created space as unallocated, you can't create partition for ubuntu from windows.
Reboot win7 few times to make sure it's happy after the shrink.

Then start the ubuntu installer and just use the Use Largest Available Free space option. That's it.

---

### Post by Badjah on 2010-05-30
> **darkod said:**
> If you need to make space on the hdd for ubuntu, it's best to shrink the win7 partition using win7 Disk Management. Leave the created space as unallocated, you can't create partition for ubuntu from windows.
Reboot win7 few times to make sure it's happy after the shrink.

Then start the ubuntu installer and just use the Use Largest Available Free space option. That's it.
Cool. sounds simple enough. Shame the installer won't install the changes I've made as they seem to be saved to the live USB, I thought there must be way to install the customized live USB, obviously not - shame would have been very handy!

---

### Post by darkod on 2010-05-30
> **Badjah said:**
>  I thought there must be way to install the customized live USB, obviously not - shame would have been very handy!

I haven't actually tried that, you might be right. I can't say either way.

---

### Post by Badjah on 2010-05-30
> **darkod said:**
> I haven't actually tried that, you might be right. I can't say either way.

Thanks for your input anyway. I guess I'm just being too nervous. If the kernel upgrade had sorted out the really annoying [bug that freezes the touchpad]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/577550") (upon connection to wifi) I would have done a full install for sure!

---

### Post by blagosphere on 2010-05-30
Install using WUBI [windows ubuntu installer] it can install several flavors and creates ubuntu in a folder within windows so you can delete it if you dont want it later. no patitioning and no worries!

---

### Post by mikewhatever on 2010-05-30
> **Badjah said:**
> Can you post what you did in the command line?
So it is not impossible to upgrade the kernel on a live USB then?

The first workaround (ln -s /cdrom/casper/vmlinuz /vmlinuz) implies re-linking /vmlinuz on live USB to /cdrom/casper/vmlinuz on the live cd. The command as given wouldn't work, but the following one should:
```
sudo ln -sf /cdrom/casper/vmlinuz /vmlinuz
```

(Alternatively, you could just use the /casper/vmlinuz package from the iso and skip burning a cd. Suppose you have an Ubuntu 10.04 iso on the hdd, your Windows partition or elsewhere. Run **gksudo nautilus** to open Nautilus, navigate to that iso, right click it and select 'Open with Archive Mounter'. In the window that opens, navigate to casper, select and copy vmlinuz file from the iso to /boot/ on you usb. Now, symlink with **sudo ln -sf /boot/vmlinuz /vmlinuz**)

Then install the kernel:
sudo apt-get install linux-image-2.6.32-22-generic

then reinstall initramfs-tools:
sudo apt-get install --reinstall initramfs-tools

then reboot.

---

### Post by Badjah on 2010-05-30
> **mikewhatever said:**
> The first workaround (ln -s /cdrom/casper/vmlinuz /vmlinuz) implies re-linking /vmlinuz on live USB to /cdrom/casper/vmlinuz on the live cd. The command as given wouldn't work, but the following one should:
```
sudo ln -sf /cdrom/casper/vmlinuz /vmlinuz
```(Alternatively, you could just use the /casper/vmlinuz package from the iso and skip burning a cd. Suppose you have an Ubuntu 10.04 iso on the hdd, your Windows partition or elsewhere. Run **gksudo nautilus** to open Nautilus, navigate to that iso, right click it and select 'Open with Archive Mounter'. In the window that opens, navigate to casper, select and copy vmlinuz file from the iso to /boot/ on you usb. Now, symlink with **sudo ln -sf /boot/vmlinuz /vmlinuz**)

Then install the kernel:
sudo apt-get install linux-image-2.6.32-22-generic

then reinstall initramfs-tools:
sudo apt-get install --reinstall initramfs-tools

then reboot.
Thanks, mate, you are a star! First method worked like a charm; however it did not fix the touchpad bug :(. Still now we know you can upgrade the Linux kernel on a live USB! :)

---

### Post by Badjah on 2010-05-30
> **blagosphere said:**
> Install using WUBI [windows ubuntu installer] it can install several flavors and creates ubuntu in a folder within windows so you can delete it if you dont want it later. no patitioning and no worries!
You say that... I had some serious problem with wubi before - killed XP on both my PC and my mum's laptop (not sure how). That was no problem tho coz  I just got rid of XP and did a full Karmic install on both machines- No great loss! :). However I would like not to kill windows 7 if possible, especially as Lucid has this annoying touchpad bug.

---

