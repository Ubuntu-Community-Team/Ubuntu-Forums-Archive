---
title: "Ubuntu doesn't recognize my CD drive"
date: 2004-10-11
forum: Installation &amp; Upgrades
---

### Post by jaspeers on 2004-10-11
I'm still really new to Linux and have been running Fedora Core 2 for about the last three weeks now.  Ubuntu sounds perfect to me, but I'm running into a snag in the installation program.

The CD boots fine, but the actual installation program doesn't recognize my CD drive.  It does ask if I have a floppy disk for it (I don't), and recommends I go into another console with Alt-F2 and look for the device under /dev.  I don't see anything there, but there is a /cdrom which doesn't seem to work.

I have a serial ata drive, but other than that I can't think of anything weird with my drive setup.  The CD drive is a Lite-On 52X burner.

I looked on google and through the mailing list archives but didn't find anything that seemed to help.  I hope I've included enough relevant information here, can anyone give me any pointers as to what I'm doing wrong?

Thanks.

---

### Post by FLeiXiuS on 2004-10-12
Believe it or not, I had that same problem with my PC at school.  Turned out I just replaced my cd-rom drive until the installation was finished.  

Other options may include:
-Hard Drive Install
-Networked Install (http/ftp)

**Hard Drive Install**
1.) Place Ubuntu ISO onto a seperate partition/hard drive as to what your install Ubuntu on.
2.) When the CDROM drive fails to ignitiate stage 1, it will prompt you with other methods of installations.
3.) Select Hard Drive Installation
4.) Enter in the location of the ISO then begin.


**Network Install**
I haven't tried this yet with Ubuntu, but with many other distrobutions it has been a sucess story.

*Requirements: HTTP or FTP Remote Server*
Keep in mind, LAN is much faster.  So a local PC would be critical.

_HTTP_
1.) Extract the ISO in a directory with http access on the remote machine.
2. )Boot the Ubuntu CD and let the cdrom fail at stage 1.
3. )Select HTTP install
4.) Enter in the IP / Location of the extracted ISO on the remote server
5.) The Process should begin to install

_FTP_
1.) Extract the ISO in a directory with http access on the remote machine.
2.) Setup a username/password to access these files
3.) Boot the Ubuntu CD and let the cdrom fail at stage 1.
4.) Select FTP install
5.) Enter in the IP / Location / Username / Password of the FTP server where the ISO is located
6.) The Process should begin to install


I hope this helped it sure did for me and also saved me a  lot of CD's  :D .  Once the installation is complete then you can worry about troubleshooting he CDROM.  Any questions regarding this please let me know!

---

### Post by justBE on 2004-10-26
There is no  menu for selecting .iso files / http or ftp install in the ubuntu installer.. is it? :(

---

### Post by Baloo on 2004-10-27
I had a similar problem when I tried to install from my second cd drive. Try putting the install cd in your first cdrom drive and installing from there.

---

### Post by cacofonix on 2004-10-27
I dont know if this will be applicable to ubuntu as its taken from the slackware site
[QUOTE=slackware.com FAQ]Q: 	 How do I install from the ISO9660 image if I don't have a CD-R or CD-RW drive (or "I have no way to burn this image that I just downloaded.")?

With loopback of course! You can mount the ISO9660 image on the kernel loopback device from another filesystem.

For example, say you download the ISO9660 image under Windows. Boot the Slackware boot and root disks for your system. Assuming your Windows partition is /dev/hda1 and you downloaded the ISO9660 image to C:, issue these commands:

mkdir -p /dos
mount -t vfat /dev/hda1 /dos
cd /dos
mknod /dev/loop0 b 7 0
mkdir /INSTALL
mount -o loop /dos/install.iso /INSTALL

You can then tell the Slackware setup program to install from a premounted directory and pass it /INSTALL/slakware. This trick can also be used if you cannot make a valid CD with your burner.

Have fun![/QUOTE]

I hope that helps :D

---

### Post by justBE on 2004-10-27
[QUOTE=Baloo]I had a similar problem when I tried to install from my second cd drive. Try putting the install cd in your first cdrom drive and installing from there.[/QUOTE] 
 didn't work for me :(

---

### Post by Tigerfunk on 2005-01-20
BUMP

Same problem, same cd drive

---

### Post by gruike on 2005-01-20
[QUOTE=cacofonix]I dont know if this will be applicable to ubuntu as its taken from the slackware site

With loopback of course! You can mount the ISO9660 image on the kernel loopback device from another filesystem.

I hope that helps :D[/QUOTE]

Doesn't work.  the loop module isn't avaible.

I am trying to install ubuntu from windows without burning a cd (my cd-burner is dead). I put the iso content on a fat32 partition (i'll call it part6) and i managed to boot it with grub for nt. But the installer wants to load files from the cd. I tried to trick it mounting part6 at /cdrom, didn't worked. I symlinked /dev/cdroms/cdrom0 to /dev/discs/blabla/part6, didn't worked. I tried to mount the iso (wich is still on the main windows partition), but no loop module.

I don't know what to do, don't know what to dooo, don't know what to do.

---

### Post by gruike on 2005-01-20
Ok. I installed the loop module (loop-modules-2.6.8.1-3-386-di_0.64ubuntu13_i386.udeb) and modutils (modutils_2.4.26-1ubuntu3_i386.deb). But when i run "modprobe loop" it says 
modprobe: relocation error: modprobe: symbol query modules version GLIBC-2.0 not defined in file libc.so.6 with link time reference.
I installed libc6-udeb_2.3.2.ds1-13ubuntu2_i386.udeb, modprobe said QM-MODULES function not implemented.

---

