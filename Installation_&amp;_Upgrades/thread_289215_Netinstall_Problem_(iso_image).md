---
title: "Netinstall Problem (iso image)"
date: 2006-10-30
forum: Installation &amp; Upgrades
---

### Post by at_a_loss on 2006-10-30
Hi Everyone,

We've successfully set up a PXE server so that we can install ubuntu over the network.  However, we'll be installing ubuntu on a LOT of computers, so we don't want to use internet repositories; we'd rather simply have the iso mounted on a local computer running an apache server, and use that as a repository.

So we have the iso mounted and everything appears to be working.  When it asks to pick a repository, I choose "enter information manually," and put in the IP of the apache server and pick the directory where the iso is mounted.  It works fine until it tries to download certain packages -- the packages are named differently.  For example, the installer tries to get:

/ubuntu/pool/ ...cdrom-core-modules-2.6.15-26-386-di_2.6.15-26.47_i386.udeb

On the iso, the file is named:

cdrom-core-modules-2.6.15-26-386-di_2.6.15-26.46_i386.udeb

In other words, it's looking for 47_i386 instead of 46_i386.  Anyone know a quick fix for this?  The install works fine when we pick an internet mirror.

Any help would be appreciated.

---

### Post by CHR1Six on 2006-11-08
I am having the same problem. My netinstall client appears to be connecting to archive.ubuntu.com and downloading some package information before it connects to my local server. This is causing problems with package resolution and prevents the machine from installing correctly. My PXE server is setup using apache and everything appears to work fine until it attempts to download a few specific packages.

**The Installer Requests:**
nic-restricted-firmware-2.6.17-10-386-di_2.6.17.6-1_i386.udeb

**My Local Mirror has:**
nic-restricted-firmware-2.6.17-10-386-di_2.6.17.5-11_i386.udeb

The installation works flawlessly if I disconnect my network from the internet so I know the connection to archive.ubuntu.com is causing the problem. I am currently searching for a way to prevent the installer from connecting to archive.ubuntu.com and any help would be appreciated.

There is a similar thread at [http://ubuntuforums.org/showthread.php?t=293866]("http://ubuntuforums.org/showthread.php?t=293866") so you may want to watch it too.

---

### Post by amagi on 2006-11-09
Sorry CHR1Six that I have to disappoint you. I currently have no solution for your problem. But... this does not mean that we are at a dead end. Could you use Ethereal to investigate the TCP trafic. That is what I did with my problems and although it takes some time to see what the client machine is actually doing, you will get a much better understanding of what is going on.

The solution I posted was mainly found through investigation of the network flow and looking at what is going on.

I have not been using the PXE mechanism for a while now and can not remember whether or not I was connected to the net or not (although I think I was).

Have you looked into creating a new preseed file with all the required setup info?

Again Sorry I can not be of much more help. I will be monitoring the thread to help where I can.

Cheers

---

### Post by CHR1Six on 2006-11-09
Amagi,
Thank you very much for pointing me in the direction of preseeding. I was originally looking at using kickstart; however, it still gave me the above error when I attempted to install. After doing some research on preseeding I noticed a variable called "apt-setup/security_host" which points to archive.ubuntu.com by default.. Everything worked perfectly once I disabled this setting. I'm currently looking at performing more automation with preseeding; however, the simple version of the fix is listed below for anyone else experiencing the same problem.

Edit your pxelinux.cfg/default file and change the install label from:
> 
LABEL install
        kernel ubuntu-installer/i386/linux
        append vga=normal initrd=ubuntu-installer/i386/initrd.gz ramdisk_size=16417 root=/dev/ram rw --


To Block Security Update Checks:
> 
LABEL install
        kernel ubuntu-installer/i386/linux
        append vga=normal initrd=ubuntu-installer/i386/initrd.gz ramdisk_size=16417 root=/dev/ram rw apt-setup/security_host= mirror/http/proxy= --


I will write a more detailed document for this issue later, for now please feel free to browse some of the sources I used. The sources do not explictly talk about this problem and the security_host but you can figure it out with trial and error.

[http://halisway.blogspot.com/2006/06/ubuntu-dapper-pxe-network-install.html]("http://halisway.blogspot.com/2006/06/ubuntu-dapper-pxe-network-install.html")
[http://halisway.hifichoice.com/preseed-606-auto.cfg]("http://halisway.hifichoice.com/preseed-606-auto.cfg")
[http://d-i.alioth.debian.org/manual/example-preseed.txt]("http://d-i.alioth.debian.org/manual/example-preseed.txt")
[http://mail.wikipedia.org/pipermail/mediawiki-cvs/2006-October/017746.html]("http://mail.wikipedia.org/pipermail/mediawiki-cvs/2006-October/017746.html")

I hope this helps everyone else out too. 

- CHR1Six

---

