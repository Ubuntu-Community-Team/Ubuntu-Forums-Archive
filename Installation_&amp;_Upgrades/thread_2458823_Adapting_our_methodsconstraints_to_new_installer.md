---
title: "Adapting our methods/constraints to new installer"
date: 2021-03-04
forum: Installation &amp; Upgrades
---

### Post by dlregisx on 2021-03-04
We've got an automated deployment system that starts with booting clients to WinPE, and the clients have no thumb-drives, CD/DVD-ROM type drives either.  Just one or more storage devices and a network connection.  We're working with Ubuntu Server LTS versions and currently support 18.04 and 20.04 ... and we'll be needing to support future versions as well.

Our current method of automated/unattended installs with the Debian-based installer works great:
[LIST]
[*]Boot to WinPE (constraint: this is all we have to work with)
[*]Clean the target drive and create a 2gb FAT partition and format
[*]Copy the EFI and install directories over the network to the target drive
[*]Modify the grub to specify a .seed file on a web server
[*]Boot to the drive
[/LIST]

The .seed file includes a directive specifying the live-installer entry, e.g.,
    d-i live-installer/net-image string [http://xx.xxx.xxx.xx/FTP_Root/Linux/UBUNTU20.04/install/filesystem.squashfs](http://xx.xxx.xxx.xx/FTP_Root/Linux/UBUNTU20.04/install/filesystem.squashfs)

I've been trying to come up with a process under the same constraints.   I've looked at the documentation for the auto-installer config, but there doesn't seem to be any way to specify a network-based location for the ISO or its files.   I've run thru the process manually and the installer reports that it's "unable to find a medium containing a live file system".   It gives the option to proceed and specify a net boot URL.   If I specify our HTTP-based ISO location, the installer seems happy and I can continue specifying configuration options and eventually get a working OS.

After installing, there's a way to dump the answers to the installer prompts in a way that it could be used for the auto-install config.  I was hoping that it would include the specification of the live-installer location, but no luck.  

Are there more options in the grub.cfg file that can be used to specify the live-installer location?  Is there a different approach I should be considering (again, within the constraints of starting with WinPE and not having any removable storage)?

We could partition the target drive with enough space for the entire ISO, but when I tried that the install process complained "blocking probe did not discover any disks"

Thanks,
Dave

---

### Post by grahammechanical on 2021-03-04
I have no experience in what you are doing. I am trying to understand the process. I am guessing that you use WinPE to carry out bullet points 2 - 5.  Are you using Debian-Installer preseeding? There is a Ubuntu alternative. It might let you do what you want.

[https://ubuntu.com/server/docs/install/autoinstall](https://ubuntu.com/server/docs/install/autoinstall)

The autoinstall config file seems to have a section for a URL.

Regards

---

### Post by dlregisx on 2021-03-04
Correct!   We're currently using the Debian-Installer preseeding, and that's working great.  However, from my understanding this installer will no longer be supported... perhaps I'm wrong.  The Ubuntu ISOs previously has an 'install' directory with what was needed to bootstrap.  Starting with 20.04, you'd have to dig through the alternative downloads to find a 'non-live' ISO, and that'd work.  Now they've seem to have dropped that altogether (hinted at here: [https://ubuntuforums.org/showthread.php?t=2444546](https://ubuntuforums.org/showthread.php?t=2444546))

There's some good discussion on the new auto-installer at [https://discourse.ubuntu.com/t/please-test-autoinstalls-for-20-04/15250](https://discourse.ubuntu.com/t/please-test-autoinstalls-for-20-04/15250)

Anyway, I'd be surprised if what we need to do isn't possible, but I'm having trouble finding the documentation that will allow us to put the pieces together.

---

