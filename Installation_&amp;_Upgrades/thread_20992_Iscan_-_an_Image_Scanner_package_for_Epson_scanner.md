---
title: "Iscan - an Image Scanner package for Epson scanners"
date: 2005-03-19
forum: Installation &amp; Upgrades
---

### Post by emperor on 2005-03-19
I downloaded, configured, compiled and built a deb for "iscan version 1.13.1". This is NOT hard but you will need to install a few dev packages until "make" is successfull. I wish I had written down the "dev" packages along the way, but I did not. You can use the handy "checkinstall" utility to automaticly build the "deb" and install the package. Again, not hard!

The iscan package can be downloaded from here: 
[http://www.avasys.jp/english/linux_e/dl_scan.html](http://www.avasys.jp/english/linux_e/dl_scan.html)

Note: As an alternative to compiling from source, you can download the binary package (RPM) and then convert it to a DEB using "alien". 

However there are a couple of gotcha's after installation: (applies to Breezy only!)
===================================
1.The pre-compiled, proprietary epkowa driver library (libesint32.so) was compiled with a bad path to the scanner firmware binary file (esfw32.bin). Source code is not available so this can't be fixed. However you can make a link to fix this problem as shown below Also, edit "/etc/ld.so.conf" and add "/usr/local/lib". Then do the following: 

    cd /usr/share
    ln -s /usr/local/share/iscan iscan
    ldconfig

source: [http://www.michaelminn.com/index.php?linux/peripherals.html](http://www.michaelminn.com/index.php?linux/peripherals.html)

2. "iscan" installs a separate local "/etc/sane.d" directory which is located in: "/usr/local/etc/sane.d". In this directory is the dll.conf, epkowa.conf and epson.conf files that will get read by "scanimage, xscanimage and iscan"! 

You may also need to: (may not be required on Edgy!)
============
add "epkowa" to dll.conf

Edit "/usr/local/etc/sane.d/epkowa.conf", adding the scanner vendor and product code. For example my Epson Photo 2400 is:

0x4b8 0x11b. This info can be usually be obtained directly from running: "sane-find-scanner" or you can run "lsusb".

My Epkowa.conf the has this:
usb ox4b8 0x11b

And finally:
========
I also found that the supplied "Epson.conf" has the SCSI scanner entry enabled, which I commented out with a "#".

---

### Post by micder on 2005-12-01
Hello emperor,

Just downloaded iscan-1.17.0-1.c2.i386.rpm from the Epson site.
Converted this package to iscan_1.17.0-2_i386.deb with alien and 
installed it with dpkg (guess alien -i would do the same)
Did not install libsane-extras.
Added epkowa to /etc/sane.d/dll.conf
And sudo iscan started my Epson 3170.
That was all.
Have to find out which script to change to user rights.

---

### Post by emperor on 2005-12-01
[quote=micder]Hello emperor,
Just downloaded iscan-1.17.0-1.c2.i386.rpm from the Epson site.
Converted this package to iscan_1.17.0-2_i386.deb with alien and 
Added epkowa to /etc/sane.d/dll.conf And sudo iscan started my Epson 3170. That was all. Have to find out which script to change to user rights.[/quote] 
On breezy I installed the latest iscan package installed and the scanner started OK. So, no compiling this time! :p

On breezy, I did not find a problem with user rights, but I did find that iscan would abort when printing due to not being able to find "libpng.so". The libpng library was installed, but the library object file could not be found. The solution to this problem is to make a symbolic link in /usr/lib as follows:

cd /usr/lib
sudo ln -s /usr/lib/libpng12.so.0.1.2.8 libpng.so

iscan will then not abort and print properly.

Note: On Hoary, this may or may not be a problem. If it is a problem the libpng library is may be a different version!

I also found that the package did not put a launcher entry in the menu. However, you can easlily add one using the "System Tools" - "Application Menu Editor" and create a launcher in the "Graphics" menu.

---

### Post by micder on 2005-12-02
Indeed the command Print did crash iscan.
Thanks for your 'cure': > cd /usr/lib
sudo ln -s /usr/lib/libpng12.so.0.1.2.8 libpng.so
The user rights problem was solved by setting:
DEFAULT_OWNER=user in /etc/hotplug/usb/iscan-device.

BTW the scanner can be used by Xsane as well

cheers :smile:

---

### Post by casfindad on 2006-05-15
[QUOTE=micder]Hello emperor,

Just downloaded iscan-1.17.0-1.c2.i386.rpm from the Epson site.
Converted this package to iscan_1.17.0-2_i386.deb with alien and 
installed it with dpkg (guess alien -i would do the same)
Did not install libsane-extras.
Added epkowa to /etc/sane.d/dll.conf
And sudo iscan started my Epson 3170.
That was all.
Have to find out which script to change to user rights.[/QUOTE]


This worked for me as well using the newer iscan-2.0.0-0.c2.i386.rpm with one caveat. After initially installing as above, I kept getting a "scanner not found" error from iscan. I then started up Xsane, which scanned fine. After closing Xsane, I tried iscan again... and lo and behold it now worked! I suspect running sane-find-scanner first may have avoided the problem as well. Happy scanning!

casfindad

P.S. Anyone have success installing Vuescan? I had it running for a while, but re-installing it after a fresh breezy install is not working so far.

---

### Post by casfindad on 2006-05-15
Scratch my PS about vuescan install troubles. My fresh install of iscan (needed by vuescan for the Epson 3170) and perhaps a vuescan update appears to have worked. Vuescan 8.3.43 runs flawlessly. Until a comparable open source package is available,  I highly recommend Vuescan for any OCR work. It's the only Linux OCR package I've tried that really works, and the price is very reasonable.

---

### Post by frio on 2006-05-23
I can get the iscan interface for an Epson 3170 to come up but when I try to preview or scan I get this error:
[B]Could not send command to scanner.
Check the scanner's status.[/B]

I was feeling pretty good once I finally got the interface to start but now I am at a loss... Any ideas or suggestions on what to look at?[LIST]
[*]I used Alien to create a DEB from iscan-2.0.0-0.c2.i386.rpm and it installed fine (as far as I can tell).
[*]Added epkowa and commented out all unneeded entries in dll.conf.
[*]Added the line **usb 0x04b8 0x0116** to epkowa.conf and comment out unneeded entries.[/LIST]:confused:

---

### Post by emperor on 2006-05-24
[quote=frio]I can get the iscan interface for an Epson 3170 to come up but when I try to preview or scan I get this error:
[B]Could not send command to scanner.
Check the scanner's status.[/B]

I:confused:[/quote]

Check that epson is commented out with a '#'. in /etc/sane.d/dll.conf

---

### Post by frio on 2006-05-24
Yep, the only line I left uncommented was the line I added; epkowa

EDIT:
I have run strace on iscan but have no idea what I'm looking at. During the trace, the interface came up, I clicked 'Preview', dismissed the error dialog, and then exited. Maybe someone more familiar with this could take a look at it. See attached dump, had to zip it... Thanks

---

### Post by jspies on 2006-08-26
I have exactly the same problem with iscan in a chrooted environment on AMD64.  I have installed iscan_2.1.0-rc2 and I do get the interface when I run iscan as root.  As normal user I cannot run it - as well as xsane.  Both xsane and iscan cannot send any commands to the scanner.

Any solutions?

---

### Post by emperor on 2006-08-28
> **jspies said:**
> I have exactly the same problem with iscan in a chrooted environment on AMD64.  I have installed iscan_2.1.0-rc2 and I do get the interface when I run iscan as root.  As normal user I cannot run it - as well as xsane.  Both xsane and iscan cannot send any commands to the scanner.

Any solutions?

For normal user access, check that you have the privilege to "Use scanner devices" checked in:

"System-Administration-Users and Groups-Your User ID-Properties-User Privileges"

Did you:
====
1. Add epkowa and comment out epson in "/etc/sane.d/dll.conf"?

2. Comment everything in "/etc/sane.d/epson.conf"

3. Enable your scanner in "/etc/sane.d/epkowa.conf", in my case I have this line only enabled for my "Epson 2400 Photo scanner":

usb 0x04b8 0x011b

I am still using the 1.17.0-2 version of iscan.

---

### Post by silbar on 2006-08-30
> **jspies said:**
> I have exactly the same problem with iscan in a chrooted environment on AMD64.  I have installed iscan_2.1.0-rc2 and I do get the interface when I run iscan as root.  As normal user I cannot run it - as well as xsane.  Both xsane and iscan cannot send any commands to the scanner.


So do I (have the same problem).  But what does it mean, "get the interface"?  All I see is the error message alert box, whether I do iscan as me or as root.  Likewise with xsane (as me or as root) -- it searches for the device but cannot find one.  In my case it is an Epson 1200 Perfection Photo.

So, to repeat, "any solutions"?

---

### Post by silbar on 2006-08-30
Sorry, I only noticed Emperor's posting in response to jspies' after I replied (added my voice to) to jspies.  I have done, I believe, all of the steps laid out by Emperor in yesterday's posting.  The version of iscan that I installed is iscan-2.1.0-1.c2.i386.rpm (which became iscan_2.1.0-2_i386.deb after applying alien).  HOWEVER, iscan still cannot find the device to send it a command.

---

### Post by emperor on 2006-08-30
check and see if "sane-find-scanner" can find your scanner.
[http://www.tldp.org/HOWTO/Scanner-HOWTO/testing.html](http://www.tldp.org/HOWTO/Scanner-HOWTO/testing.html)

---

### Post by silbar on 2006-08-30
Thanks, Emperor, for the quick response.

An AMAZING thing just happened!  After I claimed that the scanner worked in Win98, it occurred to me that I had not yet re-installed the driver on the Win98 side (having had to re-install Win 98 after total bit rot, that which drove me to becoming a Ubuntu user on a now pretty permanent basis).  So I rebooted into Win98 and re-installed the Perfection 1200U driver.  On returning to Ubuntu, NOW the iscan window comes up and I can scan beautifully!

I don't understand how this miracle happened.

It does turn out that if I try to scan to the printer (lpr), the Image Scan! window crashes and disappears.  And, the Xsane application also works.

---

### Post by emperor on 2006-08-30
> **silbar said:**
> It does turn out that if I try to scan to the printer (lpr), the Image Scan! window crashes and disappears.

Post #3 in this thread may address the crash issue.

---

### Post by Peter The Plumber on 2007-01-15
Thanks very much for the step by step directions Emperor! While some of the file locations have changed in 6.06 I was able to get things working as root. I still have to sort out permissions but that's a short leap. Yes, users are allowed to scan under 'system' 'admin'. Thank You!!

---

### Post by Sunflower1970 on 2007-01-20
Woohoo! Thank you for this!

I'm very glad I found this guide. Only (looks at clock) 3 hours after I stareted to begin to add the printer/scanner to use, I got it! I have an Epson RX700 and for the most part this guide began me on my way to figure out what was going on. (It kept wanting to use my TV tuner card as the scanner..took a bit of time to figure out how to turn that off...very weird...)

---

### Post by i8bugs on 2007-01-25
Thanks to all those code-crackers who help us hopeless people learning linux.  I'm grateful for the people how love to figure out problems.  Here's my big issue:

I have an Epson Perfection 2400 Photo.  My OS is Ubuntu Edgy 6.10.  I just downloaded iscan-2.4.0-0.c2.tar.gz from the epkowa website and also downloaded the pdf install manual.  The manual scares the crap outta me!  Lots of "IFs"...
-I have Xsane installed
-I have quiteinsane installed and GIMP
-I want to use the transparency feature on my scanner and to work as well as the windows box feature (this is important...I have years of transparencies)

I have 6 years of using linux, but consider me a noob because I still don't altogether have a golden grasp of terminal commands.

Here are my questions:
Is this a driver, or a front-end, or both?  If this is the proprietary program for this scanner, should this be considered the best? 
Do I need this to properly run my scanner?
I can follow step-by step installs especially if I can cut-paste commands.

This is the only thing left for me to do on this box to make this a dream machine.  Everything else works perfect, but I am afraid of this install because I can't use synaptic.

Thanks in advance...
i8bugs

---

### Post by emperor on 2007-01-26
> **i8bugs said:**
> 
I have an Epson Perfection 2400 Photo.  My OS is Ubuntu Edgy 6.10.  I just downloaded iscan-2.4.0-0.c2.tar.gz from the epkowa website and also downloaded the pdf install manual.

Here are my questions:
Is this a driver, or a front-end, or both?  If this is the proprietary program for this scanner, should this be considered the best? 
Do I need this to properly run my scanner?
I can follow step-by step installs especially if I can cut-paste commands.
i8bugs

You have downloaded the source instead of the binary package Go back to the epkowa website and get the RPM version. Then install "alien" with synaptic and use it to convert the RPM to a Debian/Ubuntu DEB package.

$ sudo alien iscan-2.4.0-0.c2.i386.rpm

Then install the package:

$ sudo dpkg -i iscan_2.4.0-1_i386.deb

The epkowa.conf will be installed in "/etc/sane.d" as expected. You will need to edit epson.conf and dll.conf as indicated else where in this guide. For example:

$ sudo gedit /etc/sane.d/epkowa.conf
$ sudo gedit /etc/sane.d/epson.conf
$ sudo gedit /etc/sane.d/dll.conf

*************
1. iscan uses the epkowa driver as opposed to the epson driver.
2. iscan is the best scanner application for your Epson 2400 scanner on GNU/Linux.
3. To scan slides and convert negatives to digital images you will need to use iscan.
4. Yes, you can cut and paste to a terminal session and execute the commands. (see note below).

Note: the "$" above is not part of the command string. It just indicates that you are logged in as a std user (not a superuser (su).


e.p.

---

### Post by emperor on 2007-01-28
With iscan 2.4, if your scanner is listed in "sane-epkowa" (man sane-epkowa) you may not need to edit "/etc/sane.d/epkowa.conf" after installation.

---

### Post by amanita on 2007-01-30
Thanks Emperor for this post!

I have Epson Perfection V100 and I even had to wipe out my HD and install back i386 arch. just only because there is not other way how to get Iscan 2.3.0 working on amd64 :(

All I did was: (after installing)

```
sudo gedit /etc/sane.d/dll.conf
```

and added epkowa and commented out epson in it as you suggested, no other configuration necessary for me. 8-) cheers

---

### Post by Zleep-Dogg on 2007-02-05
A little advice from one who failed but at last succeded:

I first had the same problem as frio (preview/scan -> could not connect to device...) and learned following:
1) Do **not** install from source unless you also installed SANE from source - it won't install the /etc/hotplug[...] dir if you do... (also says this in the manual)
2) Do **not** have the package "libsane-extras" installed! This package installs a version of the epkowa backend that is apparently conflicting with the one in the iscan rpm


so in short, the guideline must be:

1) fetch the iscan and optionally proprietary plugin as rpm
2) install by doing
sudo alien -i iscan-[...].rpm
sudo alien -i iscan-plugin-[...].rpm 
3) if it doesn't work, try to edit "/usr/local/etc/sane.d/epkowa.conf", adding the scanner vendor and product code (you should be able to find vendor and product code by doing sane-find-scanner in a terminal) - (my V100 photo worked without this)
4) optionally change user rights by changing to DEFAULT_OWNER=user in /etc/hotplug/usb/iscan-device. (credits goes to micder for this one)


Feel free to copy/paste and modify all you can :) just hope this helps someone :)


Cheers
Esben

---

### Post by JimmyME on 2007-03-10
In case this may be of use to someone else...

I've spent many frustrating hours trying to get my Epson 2450 PHOTO scanner working in Linux with USB.  After receiving a tip to try Firewire instead of USB, it's now working great and I'm using XSANE and scanning negatives with the transparency light.

Use sane-find-scanner to find which /dev/sg* the Espon scanner w/firewire connection is associated with.  Edit the epson.conf file so the only two uncommented lines are:

scsi EPSON
/dev/sg1   

That's it for epson.conf.  The second line /dev/sg1 would be wherever sand-find-scanner found the file.

Then change the permissions for /dev/sg1 so that users have read and write permission.  Now start XSANE and you should be good to go!

Note:  Apparently the location /dev/sg* can or will change as I just found out.  I re-ran sane-find-scanner and located it now at /dev/sg5

---

### Post by tpbarnabas on 2007-03-16
Here is how i've solved the permission problem (Iscan or Xsane working only as sudo iscan, sudo xsane) with my Epson DX5050:

Put user into the scanner group: sudo usermod -a -G username scanner

At the end of /etc/udev/??-libsane.rules add this line to have the scanner available to all members of the scanner group:

# EPSON Stylus DX4800 | EPSON Stylus DX5000 | EPSON Stylus DX5050
SYSFS{idVendor}=="04b8", SYSFS{idProduct}=="082b", MODE="660", GROUP="scanner"

Good Luck!

---

### Post by matchstich on 2007-04-12
~/Desktop$ sudo alien iscan-2.6.0-0.c2.i386.rpm
Warning: Skipping conversion of scripts in package iscan: postinst postrm preinst prerm
Warning: Use the --scripts parameter to include the scripts.
iscan_2.6.0-1_i386.deb generated
ides@ides-desktop:~/Desktop$ sudo dpkg -i iscan_2.6.0-1_i386.deb
Selecting previously deselected package iscan.
(Reading database ... 88354 files and directories currently installed.)
Unpacking iscan (from iscan_2.6.0-1_i386.deb) ...
dpkg: error processing iscan_2.6.0-1_i386.deb (--install):
 trying to overwrite `/usr/lib/sane/libsane-epkowa.la', which is also in package libsane-extras
Errors were encountered while processing:
 iscan_2.6.0-1_i386.deb

ok, not sure what this error is all about.

---

### Post by qubithaze on 2007-04-24
Zleep-Dogg, thank you very much.  I had installed from source.  I'm sure you saved me a several frustrating hours with the tip to install from the rpm's.

Thanks again.

---

### Post by emperor on 2007-04-28
On Feisty Fawn, the pre-built version of iscan from Avasys fails when you try to print due to a libc incompatiblity. So, it will have to built from source.

You will need to download iscan-2.6.0-0.c2.tar.gz. You can get it from here:  

[http://www.avasys.jp/english/linux_e/dl_scan.html](http://www.avasys.jp/english/linux_e/dl_scan.html)

Then: tar -xzvf iscan-2.6.0-0.c2.tar.gz

cd /home/emperor/download/iscan-2.6.0  <to your working directory>

Note: All command below run as "root". To get a root prompt, type "sudo su". 

#./configure

You'll have to resolve some missing compilers and and tools in order for the configure to be successful. This will be a challenge! I did not write down every package I installed and my list would be different then yours anyway!

For "make" to be successful, you will need to install some development libs like libgtk and libltdl3-dev (to resolve ltld.h).

#make

The iscan package will try to install "libsane-epkowa.*" in "/usr/local/lib/sane" which does not exists. I resolved this problem by making a symbolic link to create "/usr/local/sane" as follows:

#cd /usr/local/lib
#ln -s /usr/lib/sane .

cd /home/emperor/download/iscan-2.6.0 <my working directory>
#checkinstall

When I ran iscan, it could not find "libesmod.so.1". So, I updated the locate dbase and searched for the library file.

#updatedb
#locate libesmod.so.1

After I found it, I made a symbolic link to "/usr/lib".

#cd /usr/lib 
#ln -s /usr/local/lib/libesmod.so.1 .

Then iscan would start and work OK!

**_ Update for first time installers of iscan:_** 
1. You will need to put **"epkowa.conf"** to the "/etc/sane.d" directory. See thread #39.
2. Also for first timers, you will need to add "epkowa" to /etc/sane.d/**dll.conf** file and disable "epson" by adding a leading #" (#epson).

I have a x86 .deb built and will e-mail it to anyone who is unable to or doesn't want to try and build from source.

e.p.

---

### Post by bren21 on 2007-04-28
Hey emperor I would like your deb if you are willing to give it to me.  I am pming you my email address.

---

### Post by bren21 on 2007-04-29
I downloaded and installed your deb, and followed your instructions, but whenever I run iscan it says cannot send command to scanner. I have a Perfection V350, which is supposed to be supported.

---

### Post by emperor on 2007-04-29
> **bren21 said:**
> I downloaded and installed your deb, and followed your instructions, but whenever I run iscan it says cannot send command to scanner. I have a Perfection V350, which is supposed to be supported.

If this is your first time to install iscan, you will need to do the follow:

sudo gedit /etc/sane.d/dll.conf

Then add "epkowa" and comment out "epson"

The first time you may have to unplug the USB cable and plug it back in. I did not see the problem on subsequate reboots.

One note: Checking "man sane-epkowa" I do not see the V350 listed.

Looking on the avasys site, there is a different binary+plugin install and source file for the V350 (ver 2.3). Looking at the NEWS file in the source for 2.6, the V350 was first supported in v2.3, so the V350 should work with the deb I compiled.

---

### Post by xoros on 2007-04-29
I'm getting the same error "could not send command"

Epson 2450 photo which is listed.

---

### Post by emperor on 2007-04-29
In addition to my previous post, you can run "sane-find-scanner" to see if any scanner's are found. If not, you may need to edit "/etc/sane.d/epkowa.conf" and add the vendor and device ID hex values. (Use "lsusb" to find values)

$ sudo sane-find-scanner

The error "could not send command" could be a rights issue.

Try running iscan in a terminal as root using sudo and see if it works.

$ sudo iscan

---

### Post by xoros on 2007-04-30
1. sane-find-scanner finds the scanner.

2. Tried with sudo =  nope.  same error. 

3. I've done the chmod 0666 thing too... still same error.


Note:
When I had first installed Xsane,  it would open xsane and try to scan but gave an I/O error.  

I uninstalled Xsane and libsane-extras.  

And tried going the iscan route.... compiled it  like you did and changed the dll.conf.  

Tried rebooting,  plugging and unplugging....  still same error.

---

### Post by xoros on 2007-04-30
Here is more things for reference of what i've done....

```
blacksab@blacksab-laptop:~$ lsusb
Bus 003 Device 003: ID 04b8:0112 Seiko Epson Corp. Perfection 2450
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 002: ID 0d3d:0001 Tangtop Technology Co., Ltd 
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 003: ID 046d:c404 Logitech, Inc. TrackMan Wheel
Bus 001 Device 001: ID 0000:0000  
blacksab@blacksab-laptop:~$ sudo chmod 0666 /proc/bus/usb/*/*
Password:
blacksab@blacksab-laptop:~$ sane-find-scanner

  # sane-find-scanner will now attempt to detect your scanner. If the
  # result is different from what you expected, first make sure your
  # scanner is powered up and properly connected to your computer.

  # No SCSI scanners found. If you expected something different, make sure that
  # you have loaded a kernel SCSI driver for your SCSI adapter.
  # Also you need support for SCSI Generic (sg) in your operating system.
  # If using Linux, try "modprobe sg".

found USB scanner (vendor=0x04b8 [EPSON], product=0x0112 [EPSON Scanner]) at libusb:003:003
  # Your USB scanner was (probably) detected. It may or may not be supported by
  # SANE. Try scanimage -L and read the backend's manpage.

  # Not checking for parallel port scanners.

  # Most Scanners connected to the parallel port or other proprietary ports
  # can't be detected by this program.

  # You may want to run this program as root to find all devices. Once you
  # found the scanner devices, be sure to adjust access permissions as
  # necessary.
blacksab@blacksab-laptop:~$ id
uid=1000(blacksab) gid=1000(blacksab) groups=4(adm),20(dialout),24(cdrom),25(floppy),29(audio),30(dip),44(video),46(plugdev),104(scanner),112(netdev),113(lpadmin),115(powerdev),117(admin),119(fuse),1000(blacksab)

```

I would sure like to know how you got yours working :(

---

### Post by emperor on 2007-04-30
I would look for clues as to the cause when running iscan in a terminal. Running it via "strace" will give more detail.

$ strace iscan

or 

$ sudo strace iscan

You can also re-direct the output to a file by appending ">o.txt" after "iscan" above.

Also, check that everything is commented out in "/etc/sane.d/epson.conf".

---

### Post by xoros on 2007-04-30
Hi thanks again for reply 

Somehow I got the iscan gui to come up... but I get "could not send command" when I hit the button to scan.

Here is what happens in strace after I hit the button.... it just keeps repeating this over and over. 

```
select(9, NULL, [], NULL, {0, 1000})    = 0 (Timeout)
gettimeofday({1177959571, 875997}, NULL) = 0
ioctl(8, USBDEVFS_REAPURBNDELAY, 0xbfdc7c48) = -1 EAGAIN (Resource temporarily unavailable)
select(9, NULL, [], NULL, {0, 1000})    = 0 (Timeout)
gettimeofday({1177959571, 876268}, NULL) = 0
ioctl(8, USBDEVFS_REAPURBNDELAY, 0xbfdc7c48) = -1 EAGAIN (Resource temporarily unavailable)
select(9, NULL, [], NULL, {0, 1000})    = 0 (Timeout)
gettimeofday({1177959571, 880559}, NULL) = 0
ioctl(8, USBDEVFS_REAPURBNDELAY, 0xbfdc7c48) = -1 EAGAIN (Resource temporarily unavailable)
slect(9, NULL, [], NULL, {0, 1000})    = 0 (Timeout)
gettimeofday({1177959571, 886279}, NULL) = 0
ioctl(8, USBDEVFS_REAPURBNDELAY, 0xbfdc7c48) = -1 EAGAIN (Resource temporarily unavailable)
select(9, NULL, [], NULL, {0, 1000})    = 0 (Timeout)
gettimeofday({1177959571, 908320}, NULL) = 0

```

Hope that helps ?

EDIT:  I notice that after getting the gui,  then exiting,  gui will not come up again unless I unplug/plug in.   When gui does not come up strace reveals the same output as shown above;  till it finally times out with "could not send command".  

:(

---

### Post by xoros on 2007-04-30
What happens if you try to install epson's TWAIN driver for windows under wine?  

I'm thinking that is not a good idea. ?

---

### Post by emperor on 2007-04-30
Ok, I duplicated the "could not send command" error on another machine that never had iscan installed before. After installing the deb, I found that there was no "epkowa.conf" file in "/etc/sane.d". The default "epkowa.conf" from the development files worked for me with no edits, so I have attached it below. Unzip to your home directory and copy to "/etc/sane.d". ( $sudo cp epkowa.conf /etc/sane.d )

"/etc/sane.d/epkowa.conf"

---

### Post by xoros on 2007-05-01
Yes,  I noticed that also and I had copied an epkowa.conf over.  

But, I had editted it...   maybe that was the problem?   I don't think so, but I will try anyways.

---

### Post by bren21 on 2007-05-07
Okay, I checked and I was missing the epkowa.conf. I unzipped it to the right place, and tried again but it still does not work.

---

### Post by emperor on 2007-05-08
bren21:

Does "scanimage -L" find the epkowa driver?

For example, I get the following:
device `epkowa:libusb:005:004' is a Epson Perfection 2400 flatbed scanner

If not, then there is something fundamental wrong.

If "epkowa:" is found, then "iscan" may not be working due to the v350 "plugin" not being installed. The plugin for the v350 is not included in the source file.

Note: The problem with the std iscan rpm's on Avasys was that Feisty Fawn has libc6-v2.5 and iscan "blows-up".  Edgy had libc6-v2.4 and the pre-compiled rpm's  worked fine.

---

### Post by xoros on 2007-05-08
> **emperor said:**
> bren21:
Note: The problem with the std iscan rpm's on Avasys was that Feisty Fawn has libc6-v2.5 and iscan "blows-up".  Edgy had libc6-v2.4 and the pre-compiled rpm's  worked fine.

Well is there any way to roll back libc6 to 2.4 ?  Or will avasys ever make an updated .deb package for fiesty??

Seems so retarded,  why update versions if its going to break drivers.... shouldn't there be updated drivers first before breaking them ??

---

### Post by bren21 on 2007-05-08
> **emperor said:**
> bren21:

Does "scanimage -L" find the epkowa driver?

For example, I get the following:
device `epkowa:libusb:005:004' is a Epson Perfection 2400 flatbed scanner

If not, then there is something fundamental wrong.


No, my scanner is not found. However when I do sane-find-scanner it is detected. At least I think, it shows a vendor under usb.
```

# sane-find-scanner will now attempt to detect your scanner. If the
  # result is different from what you expected, first make sure your
  # scanner is powered up and properly connected to your computer.

  # No SCSI scanners found. If you expected something different, make sure that
  # you have loaded a kernel SCSI driver for your SCSI adapter.

found USB scanner (vendor=0x04b8, product=0x012f) at libusb:005:004
  # Your USB scanner was (probably) detected. It may or may not be supported by
  # SANE. Try scanimage -L and read the backend's manpage.

  # Not checking for parallel port scanners.

  # Most Scanners connected to the parallel port or other proprietary ports
  # can't be detected by this program.

  # You may want to run this program as root to find all devices. Once you
  # found the scanner devices, be sure to adjust access permissions as
  # necessary.

```

---

### Post by emperor on 2007-05-09
> **xoros said:**
> Well is there any way to roll back libc6 to 2.4 ?  Or will avasys ever make an updated .deb package for fiesty??

Seems so retarded,  why update versions if its going to break drivers.... shouldn't there be updated drivers first before breaking them ??

Avasys does not support even Debian with a deb package. much less Ubuntu. They only build rpm's, presumably for Red Hat or Fedora, but they don't really say. We will see newer binary in the future, but we do not have any control over when.  When I started this thread I had to compile for source to get iscan to work in Ubuntu, then later the binary worked again.

---

### Post by emperor on 2007-05-09
One approach to resolve the problems may be to install the 2.6 binaries on the Avasys site for your printer. 

Then see if "scanimage -L" displays the epkowa correctly. If it does. but iscan blows up as expected due to libc6-v2.5, replace the frontend related files for iscan with the compiled from source deb files one at a time until you get iscan to work. In the binary from Avasys It might just be  or "/usr/bin/iscan" or the lib's in "/usr/lib/"

If helps to run "iscan" from a terminal prompt while trying to resolve the problem.

---

### Post by pepage on 2007-07-21
First I would like to thank everyone for an excellent thread. I just purchased a Dell 1505n laptop and an Epson Perfection V100 scanner($40 rebate). Being new to GNU/Linux, I am having my share of trouble but getting my V100 to work on the laptop is a challenge. Using what I have learned in this thread I can now get some action with SUDO ISCAN

My problem is, I changed the iscan-device file to say DEFAULT_OWNER=user (micder post #4) and DEFAULT_GROUP=scanner but the ISCAN command still does not work. SUDO ISCAN does. I have tried logging out and back in plus disconnecting and reconnecting the scanner and the results are the same. I have not done the print fix yet as I am taking one problem at a time. What am I doing wrong or what should I do next?

---

### Post by matchstich on 2007-07-22
[https://bugs.launchpad.net/ubuntu/+source/sane-backends/+bug/85488](https://bugs.launchpad.net/ubuntu/+source/sane-backends/+bug/85488)

---

### Post by pepage on 2007-07-22
Matchstick,

Thank you for the link! I unplugged my scanner and plugged it into my Windows box where I know it works.

This takes me back to the days when I built a computer from parts purchased at a computer fair. All those dip switch settings. Would get everything working and the next great purchase would have me reworking all my settings. 

My son mentioned he was considering going to Linux but I cannot recommend it.  When computers first came out, you had no choice but to live with the problems but now they are just a tool to launch an application or complete a task. I love my new laptop and will continue to use it for the web but for scanning and doing taxes I will stay with windows. Considered putting windows in a virtual box but then I forgot about windows activation problems. Ugh!

---

### Post by matchstich on 2007-07-22
i use this box as my main one. 

have another box with xp on it that i plan on  keeping.

my scanner worked at first on here but then a update killed it. 

finally got another update that put the scanner back to working. 

went  a few months where i couldn't use my scanner on here.

used the xp box for scanning during that time.

was going to put linux on that xp box.

cept i think i will leave it. just in case.

like having a back up.

---

### Post by Dubbayoo on 2007-07-22
What does this do that xsane doesn't?

---

