---
title: "Install using network boot from local ftp"
date: 2010-06-14
forum: Installation &amp; Upgrades
---

### Post by njsharp on 2010-06-14
I am raising this as a new thread for extra visibility because a very similar question by glug101:

[http://ubuntuforums.org/showthread.php?t=1285118](http://ubuntuforums.org/showthread.php?t=1285118)

on October 8th 2009 has yet to be answered.

I want to perform a netboot install of Ubuntu using files sourced from a local network FTP server, and I cannot find the necessary installer files anywhere.

Reasons include:
* dead or flaky optical drive and no chance of replacing it
* optical drive is CD but iso is DVD
* several targets, so much faster to load repeatedly from local FTP than from an  internet repo

What I CAN do with Fedora or CentOS is as follows:

1 On a second PC, download the relevant .iso and extract that to a directory (or mount it with -t iso9660 -o loop to make the contents visible without bothering to run the extract or using up more space).  This makes all the files available but most particularly a ram fs and a mini linux installer, such as initrd.gz and vmlinuz

2 On that second PC, also set up the usual DHCP/PXELINUX/TFTP arrangements to cause the netbootable target PC to load those two files and run the installer.  Also run FTP (or HTTP) on that PC

3 Netboot initrd.gz and vmlinuz (names vary) into the target PC.  Answer the installer's questions, including choosing FTP (or HTTP) install method, giving the second PC's IP address, and an account and password, and path to the extracted iso.  The rest is as usual. :D



:( I have not been able to do this with any Ubuntu netboot installer I have found so far.  It either netboots, but then (seems pointless) wants a CD iso, or insists on pulling from a repo.  Yes, I could create a local repo, but that seems to need a lot more work and space than setting up an iso on an ftp server.

Is it simply the case that the Ubuntu family lacks this sort of netbootable installer (in which case, can this be done please?  Pretty please??!!)  or I have just been unlucky in searching for it, in which case can someone please point me at the files!!

By the way, glug101, you also asked for NFS method.  I have not got that to work because I didn't really want to run NFS (or HTTP for that matter).  FTP is just about all my simple mind can cope with!  But I have seen PXELINUX file code where the APPEND line includes bits like 'boot=casper' and 'netboot=nfs' (followed by IP etc and path info for the NFS) that I guess should work.  I've searched in vain for stuff like:

netboot=FTP
ftp=ftp://<account>:<password>@<IP>

Sigh...

---

### Post by glug101 on 2010-07-13
njsharp,

take heart!  There is a solution.  I'm just not able to elaborate on it right now.  I'll try to post something more helpful here later when I'm at home.

---

