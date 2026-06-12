---
title: "netinstall - client can't find files on local mirror"
date: 2006-11-05
forum: Installation &amp; Upgrades
---

### Post by mnimbus on 2006-11-05
Hello,
I've been trying to do a network install - pxe and bootup
is fine, installer starts up but says it can't find the right
file on the mirror (apache2 is running on the same machine that has the tftpd).
I can see the log files when the client pc puts them on the web,
and I can ping the client machine from the server.
In the log file, the client seems to be looking for the ubuntu archive,
even though I manually point it to the local server.

Any help is greatly appreciated.

mnimbus

---

### Post by CHR1Six on 2006-11-08
I am having the same problem. My netinstall client appears to be connecting to archive.ubuntu.com and downloading some package information before it connects to my local server. This is causing problems with package resolution and prevents the machine from installing correctly. My PXE server is setup using apache and everything appears to work fine until it attempts to download a few specific packages.

**The Installer Requests:**
nic-restricted-firmware-2.6.17-10-386-di_2.6.17.6-1_i386.udeb

**My Local Mirror has:**
nic-restricted-firmware-2.6.17-10-386-di_2.6.17.5-11_i386.udeb

The installation works flawlessly if I disconnect my network from the internet so I know the connection to archive.ubuntu.com is causing the problem. I am currently searching for a way to prevent the installer from connecting to archive.ubuntu.com and any help would be appreciated.

There is a similar thread at [http://ubuntuforums.org/showthread.php?t=289215&highlight=netinstall]("http://ubuntuforums.org/showthread.php?t=289215&highlight=netinstall") so you may want to watch it too.

---

### Post by CHR1Six on 2006-11-09
mnimbus,
I recently found a solution to your problem. Below are the details, I hope this helps you too.

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
[URL="http://halisway.blogspot.com/2006/06...k-install.html"]
http://halisway.blogspot.com/2006/06...k-install.html[/URL]
[http://halisway.hifichoice.com/preseed-606-auto.cfg]("http://halisway.hifichoice.com/preseed-606-auto.cfg")
[http://d-i.alioth.debian.org/manual/example-preseed.txt]("http://d-i.alioth.debian.org/manual/example-preseed.txt")
[http://mail.wikipedia.org/pipermail/...er/017746.html]("http://mail.wikipedia.org/pipermail/...er/017746.html")

- CHR1Six

---

