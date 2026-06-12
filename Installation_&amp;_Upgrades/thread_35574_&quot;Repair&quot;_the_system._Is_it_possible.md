---
title: "&quot;Repair&quot; the system. Is it possible?"
date: 2005-05-19
forum: Installation &amp; Upgrades
---

### Post by svarreby on 2005-05-19
After many attemts to install Ubuntu on my laptop I had success last night. The installation freezed when installing samba-common (everything went fine uptil then).

Because I had my wireless working I thought I just reboot into Rescue Mode and upgrade from there.... and then continue / finish the installation process.

I got an error saying that I should do:

dpkg --configure -a (I think)

... and moments later I was able to start the X-enviroment.

When I first logged in I got an error message saying that there's a problem with HAL
and ACPI.

When I booted up my machine today I could log in as a regular user but I could'nt click on any buttons and menus and I was missing every applet at the upper right corner.

There's pretty good reasons to suspect that these issues are related to the "faulty" installation. Is it some way to "repair" my box (without re-installing the whole OS)?

BTW, I have done a apt-get upgrade

---------------------------------------------------------------------------------------------------------------------------------

EDIT 20.05:
I can see everything (all applets) and use my mouse if I boot in rescue mode and start the X-enviroment from there. The downside is the two error messages about HAL and ACPI.

When I do a normal boot and log in as a regular user, I'm not able to click on anything and a lot of the applets are missing ...
... hope that helps you understand my mess :-) :-) :-)

---

### Post by joelito on 2005-05-19
From a terminal try

$sudo apt-get -f install

this should fix broken packages

---

### Post by meburke on 2005-05-19
I believe it's:
apt-get install -f (which is what the help file says) but I don't know enough about apt to know if it makes any difference.

However, that soesn't seem to fix everything.

I'm running ubuntu on a Toshiba laptop Satellite A45-S150 and had virtually no trouble until I started running Synaptic.  (I had to configure the DVD player to read/play DVD's but the Starter Guide instructions made it a pretty easy job.) Now I have a crapload of partially installed apps on my system, and Synaptic won't work right. Is there a way to undo, or uninstall the apps I loaded according tot he history guide?

Furthermore, I keep getting the following message:

W: Couldn't stat source package list [ftp://ftp.nerim.net](ftp://ftp.nerim.net) stable/main Packages ( /var/lib/apt/lists/ftp.nerim.net_debian-marillat_dists_stable_main_binary-i386_ Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [ftp://ftp.nerim.net](ftp://ftp.nerim.net) stable/main Packages ( /var/lib/apt/lists/ftp.nerim.net_debian-marillat_dists_stable_main_binary-i386_ Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems.

running apt-get update now give me the message:

Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/hoary/Release.gpg](http://us.archive.ubuntu.com/ubuntu/dists/hoary/Release.gpg)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/hoary-updates/Release.gpg](http://us.archive.ubuntu.com/ubuntu/dists/hoary-updates/Release.gpg)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/hoary-security/Release.gpg](http://security.ubuntu.com/ubuntu/dists/hoary-security/Release.gpg)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hoary/Release.gpg](http://archive.ubuntu.com/ubuntu/dists/hoary/Release.gpg)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/hoary-security/main/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/hoary-security/main/binary-i386/Packages.gz)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hoary/multiverse/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/hoary/multiverse/binary-i386/Packages.gz)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/hoary-security/restricted/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/hoary-security/restricted/binary-i386/Packages.gz)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/hoary-security/main/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/hoary-security/main/source/Sources.gz)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/hoary-security/restricted/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/hoary-security/restricted/source/Sources.gz)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/hoary-security/universe/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/hoary-security/universe/binary-i386/Packages.gz)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/hoary-security/universe/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/hoary-security/universe/source/Sources.gz)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hoary/multiverse/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/hoary/multiverse/source/Sources.gz)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/hoary/main/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/hoary/main/binary-i386/Packages.gz)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/hoary/restricted/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/hoary/restricted/binary-i386/Packages.gz)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/hoary/main/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/hoary/main/source/Sources.gz)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/hoary/restricted/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/hoary/restricted/source/Sources.gz)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/hoary/universe/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/hoary/universe/binary-i386/Packages.gz)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/hoary/universe/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/hoary/universe/source/Sources.gz)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/hoary-updates/main/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/hoary-updates/main/binary-i386/Packages.gz)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/hoary-updates/restricted/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/hoary-updates/restricted/binary-i386/Packages.gz)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/hoary-updates/main/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/hoary-updates/main/source/Sources.gz)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/hoary-updates/restricted/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/hoary-updates/restricted/source/Sources.gz)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.

Does this mean that the process is trying to connect to my CD drive and is getting refused?  Anyone know how this could happen and how it can be corrected?

Thank you,

Mike

---

### Post by Xian on 2005-05-19
meburke, it would probably be wise to post the contents of your /etc/apt/sources.list file.

---

### Post by nad on 2005-05-20
As you are using a via chipset, try adding the parameter: acpi=off  to your boot command line. If this helps, edit your /boot/grub/menu.lst to include this parameter at every start.

---

### Post by The Man on 2006-10-25
This is annoying I attempted to install compiz but during enabling nvidia drivers when I start up it show me everything gets to login and I login but it just gives me the mouse with a brown background.
No tool bars or anything I can still use the mouse(only move it)anyway to reapair this?

---

