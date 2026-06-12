---
title: "Can't install, just blinking line"
date: 2011-08-31
forum: Installation &amp; Upgrades
---

### Post by UnresponsiveBeeVictim on 2011-08-31
I'm trying to get Ubuntu installed on a new-ish system.  It's a Core2Duo, MSI motherboard, 2gb ram, Radeon HD4960, etc.  I've tried multiple images and every time I boot off of them I just get a blinking line right after bios.  No boot menu, nothing.

Also tried an Nvidia 8800GTS on the off chance it was a videocard issue, which resulted in the same blinking line.

:confused:Completely lost right now.  Thanks

---

### Post by Hakunka-Matata on 2011-08-31
It sounds like you boot medium is not valid.
Have a look at [http://www.ubuntu.com/download/ubuntu/download](http://www.ubuntu.com/download/ubuntu/download)

---

### Post by UnresponsiveBeeVictim on 2011-08-31
I've been dd-ing the images from OSX to different USB flash drives.  Thing is, I haven't been converting them to img first, just dd-ing the isos.  Maybe that is the issue, I am in the process of dd-ing a converted img right now.

edit:  Nope, same issue as before. :(

---

### Post by Hakunka-Matata on 2011-08-31
If you want to install Ubuntu on your netbook, then I'd recommend using unetbootin (in my signature) to build your bootable flashdrive.  download the .iso from the link in post# 2
**EDIT:  You'll probably have to change the permissions on the .bin to make it executable.**

---

### Post by UnresponsiveBeeVictim on 2011-08-31
unetbootin doesn't work properly on OSX. :(

edit:  Tried unetbootin on a Win7 system and I still have the blinking line.

---

### Post by Hakunka-Matata on 2011-08-31
> **UnresponsiveBeeVictim said:**
> unetbootin doesn't work properly on OSX. :(

edit:  Tried unetbootin on a Win7 system and I still have the blinking line.

Guess I don't follow what the problem is, 

[LIST]
[*]did unetbootin build the flash drive using the win7 machine & ubuntu.iso file as input?
[/LIST]

Included here are two thumbnails of a working 11.04 flashdrive's directory, and partitioning
Good Luck.

Flash drive partition only has to be ~ 1GiB

---

### Post by Bizz on 2011-08-31
I was having basically the exact same issue as you've described. I hit F6 to bring up additional options and chose acpi=off. It then went to the installer just fine. 

I'm not sure if this "fix" will work for you, but good luck!

---

### Post by Hakunka-Matata on 2011-08-31
> **Bizz said:**
> I was having basically the exact same issue as you've described. I hit F6 to bring up additional options and chose acpi=off. It then went to the installer just fine. 

I'm not sure if this "fix" will work for you, but good luck!

Good to know, what Release Ubuntu were you using when this happened?

---

### Post by Bizz on 2011-08-31
> **Hakunka-Matata said:**
> Good to know, what Release Ubuntu were you using when this happened?

11.04 64b, the problem was also occurring with the 32b version as well.

---

