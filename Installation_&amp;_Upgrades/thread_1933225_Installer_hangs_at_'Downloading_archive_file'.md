---
title: "Installer hangs at 'Downloading archive file'"
date: 2012-02-28
forum: Installation &amp; Upgrades
---

### Post by cbSuperiorSoundSystems on 2012-02-28
I'm working on a project that requires that I install Ubuntu Server 10.04 LTS to a netbook without a CD-ROM drive, so I'm using an app called '[Universal USB Installer]("http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/")' to create a bootable USB stick out of the 10.04.4 i386 iso.

The installer seems to progress fine until it gets to a part where there's a progress bar that comes up for a split second then disappears leaving a blue screen with a grey bar at the bottom. The progress bar that appears for a moment says 'Downloading release file'.

The installer just hangs there at the blue screen, and doesn't progress at least for 5 minutes that I've waited for it.

I didn't see a way to verify the integrity of the installer when I booted, otherwise I'd have done that first. Right now I'm re-creating the USB stick using the same iso I downloaded earlier today, for lack of anything else to try.

I checked that the internet connection was good using the OS that's currently installed to the netbook I'm trying to install Ubuntu to, and it's able to reach the internet via DHCP, so I figure the installer is, too.

Any advice is appreciated. Thanks.

EDIT:

I just tried again, and see it's not 'archive' file but rather 'release' file.
'Downloading release file' is what flashes on the screen before it goes blue.

---

### Post by cbSuperiorSoundSystems on 2012-02-29
It doesn't seem to matter which iso I use, one I downloaded yesterday or one I downloaded today, so the iso must be good.

I guess it's time to buy an external CD-RW.

---

### Post by cbSuperiorSoundSystems on 2012-02-29
> **cbSuperiorSoundSystems said:**
> I guess it's time to buy an external CD-RW.


That was the key. Installing from an optical drive.

Now while running the installer from the CD, I get the full menu at bootup, whereas the USB only gave me 2 options, install or something else I don't remember. Now I get to choose the language, check the integrity of the disk, choose expert mode & now it actually installs from the files on the CD rather than trying to use a mirror for the whole shebang.

So, note to anyone trying to install from a USB thumbdrive, it's not the same as using a CD, not by a long shot, and if it works you're luckier than I was.

---

