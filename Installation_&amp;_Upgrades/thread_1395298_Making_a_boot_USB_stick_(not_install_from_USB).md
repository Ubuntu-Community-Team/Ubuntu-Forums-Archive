---
title: "Making a boot USB stick (not install from USB)"
date: 2010-01-31
forum: Installation &amp; Upgrades
---

### Post by MarkHowells on 2010-01-31
I'm trying to make a bootable USB stick, pre-loaded with XBMC. I can't help but think I'm making hard work of it.

What I did was make a live karmic live USB stick using USB Creator. So far so good. Then I stripped off the language selection at the beginning so I go straight to the main menu. 

Then I unpacked the squashfs root filesystem onto my harddrive (mounted at ~/squashfs) and executed

# mount -t proc proc ~/squashfs/proc
# chroot ~/squashfs

Then I added my nameserver to /etc/resolv.conf and executed

# add-apt-repository ppa:team-xbmc
# apt-get update

and executed

# apt-get install xbmc

The idea was then to remake the squashfs with XMBC installed and replace the one on the USB stick. However, when I install xbmc I get 

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies.
  xbmc: Depends: xbmc-data (= 1:9.11-karmic1) but it is not going to be installed
        Depends: xbmc-skin-confluence (= 1:9.11-karmic1) but it is not going to be installed or
                 xbmc-skin-pm3-hd (= 1:9.11-karmic1) but it is not going to be installed
        Depends: xbmc-web-pm3 (= 1:9.11-karmic1) but it is not going to be installed
E: Broken packages

```

I suspect the Live distro is therefore incompatible with the xbmc install.

However, what I'm doing feels like a hack. Can anyone point me at a 'proper' way of creating a bootable USB stick with XBMC installed. The idea is to have a silent (diskless) PC that boots of the USB stick then NFS mounts writeable storage for other stuff. I don't want to netboot as that will produce a long startup time and I have to install a PXE/DHCP server onto my ubuntu server...

Thanks.

---

### Post by C.S.Cameron on 2010-01-31
I'm probably missing something but can't you make the flashdrive persistent with usp-creator and just install XBMC?

---

### Post by MarkHowells on 2010-02-01
> **C.S.Cameron said:**
> I'm probably missing something but can't you make the flashdrive persistent with usp-creator and just install XBMC?

I suppose I could, but won't that fail the XBMC install in the same way? I wanted to make absolutely sure that XBMC is not able to write to the local filesystem so that if the USB stick ever fails I can just flash a new one from a master image. I guess that one way would be to install XBMC as you suggest, modify the initrd to mount the casper filesystem as read-only and then have init mount an NFS filesystem to write into (eg use aufs to overlay an NFS root). I also need to replace some of the drivers that are installed.

I am, however, still interested to know why my initial plan doesn't work and how to go about creating something like XBMC-live but with the drivers I want.

---

### Post by MarkHowells on 2010-02-02
I eventually worked out what was wrong. The apt config files for the live distro are missing some entries. I simply copied the /etc/apt/* entries from my main system, ran apt-get update followed by apt-get upgrade on the chrooted system (as described above) and installed xmbc without problems.

I then used mksquashfs to recreate the filesystem.squashfs file, copied it to the stick and booted it. Now I have my stick, with xmbc installed, and can add/remove drivers via the same iterative process. Add an NFS hosted aufs overlay for root and I have a distro that's perfect for my needs. :D

---

