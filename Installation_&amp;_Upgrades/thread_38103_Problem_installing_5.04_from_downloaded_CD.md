---
title: "Problem installing 5.04 from downloaded CD"
date: 2005-05-30
forum: Installation &amp; Upgrades
---

### Post by Scott5114 on 2005-05-30
Hello there.

I've got a problem doing a clean install of Ubuntu 5.04 (Hoary Hedgehog) on my computer. I can start the installer and set all the options (most times), but when the actual installation of the packages starts I get an error that looks like this:

> **_Debootstrap Error_**
Couldn't retrieve libc6. This may be due to a network problem or a bad CD, depending on your installation method.

If you are installing from CD-R or CD-RW, burning the CD at a lower speed may help.

Hitting ENTER, I get:
> **_Failed to install the base system_**
The base system installation into /target/ failed.

Check /var/log/messages or see virtual console 3 for details.

When I go to either Virtual Console 3 or the messages file, I see this:
```

File descriptor 3 left open
File descriptor 4 left open
File descriptor 5 left open
File descriptor 6 left open
	No matching physical volumes found
File descriptor 3 left open
File descriptor 4 left open
File descriptor 5 left open
File descriptor 6 left open
	No volume groups found
	Reading all physical volumes. This may take a while...

```

Finally, I checked Virtual Console 4 and saw:
```

May 29 22:36:18 base-installer: info: Execution hook before debootstrap
May 29 22:36:20 base-installer: info: Running /usr/lib/base-installer.d/40netcfg
May 29 22:37:22 run-debootstrap[26401]: file:///cdrom/pool/main/g/glibc/libc6_2.3.2.ds1-20ubuntu13_i386.deb was corrupt
May 29 22:41:25 base-installer: error: exiting on error base-installer/debootstrap-failed

```

Having read the first screen's recommendation to lower the burning speed, I made some new discs:

1) 24x, not finalized
2) 20x, finalized
3) 16x, finalized

...all three of which have failed.

Occasionally the installer locks up. The most usual time for it to do so is when it is setting up the / partition, usually around 11% or 74%. This has happened 3 different times. Also, it locked up once when it was "retrieving locales."

I'm hoping that the .iso file is not corrupt...it took me three days to download on dial-up :( *Is there a way to check and see if the file (or setup disc) is correct or not?* I had ordered a pressed CD about six weeks ago, but it *still* hadn't arrived yet, and I was getting tired of waiting. 

I'm attempting to install on a computer with a Intel Pentium III, 384 MB RAM, 80GB hard drive, nVidia Riva TNT2 graphics card. It's a Gateway...and that's all the stats I can remember offhand. 

Thanks in advance for any help you can provide.
-Scott

---

### Post by apollyonis on 2005-05-30
Its probably a bad .iso download. Check MD5 against the key that corresponds to the .iso that you downloaded and are trying to burn.

539a25fd0c5e1e6bb5d1f968ec25b759   ubuntu-5.04-dvd-amd64.iso
765dc370887735af71bc2cf6fcc9fafd       ubuntu-5.04-dvd-i386.iso
73d38d21bd14b902252bca0f39e7eb54  ubuntu-5.04-dvd-powerpc.iso
46135038af6dd2ef36fd8d521afe7de4     ubuntu-5.04-install-amd64.iso
f6b3f164c99761234858a4d2c12d0840   ubuntu-5.04-install-i386.iso
bf3fe18eb2fbc450769237dec189405b    ubuntu-5.04-install-powerpc.iso
664e3d7864c0f4f2d2efc09ec230fb2e     ubuntu-5.04-live-amd64.iso
77a1a8be45e0cc93a14c9b9bf00f6648   ubuntu-5.04-live-i386.iso
811a1aec315dae0ceef5d8e626584874  ubuntu-5.04-live-powerpc.iso

---

