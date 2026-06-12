---
title: "Dependencies problem and nonworking fresh installation of Ubuntu 4.10"
date: 2004-11-25
forum: Installation &amp; Upgrades
---

### Post by urke on 2004-11-25
I use Slackware Linux for couple years and now I wish to switch on Debian based GNU/Linux (reason is: planed leaving out of GNOME and Slack on two insllation CD's). I chose Ubuntu becouse it is small in size (only one installation CD iso for download :) and it is GNOME (I work in prevod.org - project for localisation GNOME to Serbian) based (I not prefer a KDE). I never early not use or try Debian or Debian based distros, and SysV init is strange to me, but I'll get familyar with it :)

My machine is: ABIT KD7-E, Athlon XP 1700+ Palomino, 256MB DDR266, ABIT GeForce4 MX440SE SILURO with 64MB DDR, SB Live!, Maxtor 6Y120P0 (120GB, 8MB cache) as primary master, and Maxtor 6Y060L0 (60GB, 2MB cache) as primary slave. My LG CD-RW 48x/16x/48x attached as secondary master. Network card with Realtek 8139 chip (supported by 8139too kernel module) and Cable net.

I download Ubuntu 4.10 i386 ISO image from one of official Ubuntu FTP mirrors, and burn it to CD. My Slackware GNU/linux 9.1 is on Primary Slave, and Ubuntu 4.10 I install on Primary Master.

*btw, Good bless digital cameras. My HP PhotoSmart 735 and ScrollLock button on keyboard help me to catch and retype all of this terminal messages*

This partition organisation of Ubuntu HDD:

```
IDE1 master (had) - 122.9 GB Maxtor 6Y120P0
      #1 primary    4.2 GB     ext2       /            (boot)
      #2 primary   12.2 GB     ext2       /usr
      #5 logical    2.0 GB     ext2       /tmp
      #6 logical    2.0 GB     ext3       /var
      #7 logical  509.9 MB     swap       swap
      #8 logical   33.7 GB     ext3       /home
      #9 logical   68.0 GB     ext2       /arhiva
```

On boot after the first stage of the installation process is complet, I get this errors after chosing "Ubuntu, kernel 2.6.8.1-3-386":

```
...
 * Running 0dns-down to make sure resolv.conf is ok...                   [ ok ]
 * Starting hotplug sybsystem...
modprobe: FATAL: Error inserting pciehp (/lib/modules/2.6.8.1-3-386/kernel/drive
rs/pci/hotplug/pciehp.ko): Operation not permitted

modprobe: FATAL: Error inserting pciehp (/lib/modules/2.6.8.1-3-386/kernel/drive
rs/pci/hotplug/shpchp.ko): Operation not permitted
```

Ubuntu boot and installation process continue. I set time zone and answer **YES** for "Download software from the Internet?". Installation download Packages lists report this:

```
The following packages will be upgraded:
  libc6 libc6-i686 locales perl-base
4 packages upgraded, 597 newly installed, 0 to remove and 9 not upgraded.
Need to get 77,2MB/408MB of archives. After unpacking 1218MB will be used.
Writing extended state information... Done
```

Then started download and downloaded 67 packages. After setting up xserver-xfree86 keyboard handling, installation continue.

But, I noticed bunch of errors, like this:

```
Unpacking gnome-panel-data (from .../gnome-panel-data_2.8.1-0ubuntu2_all.deb) ...
dpkg: error processing /var/cache/apt/archives/gnome-panel-data_2.8.1-0ubuntu2_a
ll.deb *--unpack):
 corrupted filesystem tarfile - corrupted package archive: Success
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Selecting previously deselected package gnome-panel.
Unpacking gnome-panel (from .../gnome-panel_2.8.1-0ubuntu2_i386.deb) ...
Selecting previously deselected package hicolor-icon-theme.
Unpacking hicolor-icon-theme (from .../hicolor-icon-theme_0.5.3-all.deb) ...
tar: Read 2636 bytes from -
dpkg: error processing /var/cache/apt/archives/gnome-icon-theme_2.8.0-0ubuntu2_a
ll.deb (--unpack):
 failed to open package info file `/var/lib/dpkg/tmp.ci/control` for reading: No
 such file or directory
Selecting previously deselected package capplets-data.
```

After installing all downloaded packages, process reported this:

```
...
Errors were encountered while processing:
 /var/cache/apt/archives/libgnome-keyring0_0.4.0-0ubuntu1_i386.deb
 /var/cache/apt/archives/gnome-panel-data_2.8.1-0ubuntu2_all.deb
 /var/cache/apt/archives/gnome-icon-theme_2.8.0-0ubuntu2_all.deb
 /var/cache/apt/archives/gnome-gv_2.8.0-0ubuntu2_i386.deb
 /var/cache/apt/archives/gnome-media_2.8.0-0ubuntu2_i386.deb
 /var/cache/apt/archives/gnome-netstatus-applet_2.8.0-0ubuntu1_i386.deb
 /var/cache/apt/archives/gnome-nettool_0.99.3-1ubuntu3_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
Ack! Something bad happened while installing packages.  Trying to recover:
Setting up python2.3-clientcookie (0.4.18-3) ...
```

Installing continued, and I noticed a bunch of dependency errors and configuration fails, like this:

```
dpkg: dependency problems prevent configuration of gnome-terminal:
 gnome-terminal depends on libgnome-keyring0 (>= 0.3.2); however:
  Package libgnome-keyring0 is not installed.
dpkg: error processing nome-terminal (--configure):
 dependency problems - leaving unconfigured
Setting up python-pqueue (0.2-6) ...
Setting up gdb (6.1-3) ...
```

After this step finished, this printed out:

```
(... a lot of package names printed out ...)
gnome-applets-data
Processing was halted because there were too many errors.
Reading Package Lists... Done
Building Dependency Tree
Reading extended state information
Initializing package status... Done
```

Then opened "Ubuntu base system configuration" ncurses dialog that tell me

```
There was a problem installing the selected software.

One or more packages failed to install. This may be due to bug in the packages,
or you may be out of disk space or experiencing some other problems.

...

If you decide not to try again, bear in mind that some packages on your
system will be in a broken state until you manually resolve the problem.
```

Then started aptitude and I press "**g**" for finishing Download/Install/Remove process. Then was reported this:

```
Extracting templates from packages: 11%E: Sub-process /bin/gzip returned an error code (1)
E: Prior errors apply to /var/cache/apt/archives/gnome-netstatus-applet_2.8.0-0u
buntu1_i386.deb
Extracting templates from packages: 100%d file fescriptor
Preconfiguring packages ...
(Reading database ... 52051 files and directories currently installed.)
Unpacking libgnome-keyring0 (from .../libgnome-keyring0_0.4.0-0ubuntu1_i386.deb)
 ...
dpkg: error processing /var/cache/apt/archives/libgnome-keyring0_0.4.0-0ubuntu1_
i386.deb (--unpack):
 current filesystem tarfile - corrupted package archive: Success
Unpacking gnome-panel-data (from .../gnome-panel-data_2.8.1-0ubuntu2_all.deb) ...
```

And on finishing with aptitude upgrade/install process this printed out:

```
(... a lot of package names printed out ...)
gdm
Processing was halted because there were too many errors.
```

After that, Ubuntu Configuration "Thank you for choosing Ubuntu!" dialog apear. I hope that installation finished. I read my new arrived mails and do as described in them (relocation of CID and TrueType fonts directory). Then I tune up /etc/X11R6/XF86Config-4 configuration for preferred resolution 1024x768 and run **# startx**, but X died with:

```
(EE) Unable to find a valid framebuffer device
(EE) NV(0): failed to open framebuffer device, consult warnings and/or errors ab
ove for possible reasons
        (you may have to look at the server log to see warnings)
(EE) Screen(s) found, but none have a usable configuration.

Fatal server error:
no screens found

(some text about where to look for detauiled error report)
XIO:  fatal IO error 104 (Connection reset by peer) on X server ":0.0"
      after 0 requests (0 known processed) with 0 events remaining.
urke@urosevic:/etc/security $ _
```

My questions are:

1) How to fix dependencies errors (libgnome-keyring0 and others) and sucessfully install all packages? (I start memtest to check good working memory, but it is soo long and I breake this process after 3 successfully finished tests)
2) Why X not work after CID and TrueType font directory corections (as described in mail posted by depconf (as I remember) to my local mailbox? I'm not change nothing except FontPath for CID and TrueType and Mode for 24 bits in Screen section to **"1024x768" "800x600"**!
3) Where is Midnight Commander? How to get it and install to my Ubuntu box?
4) How I can compile and make Ubuntu packages for Sylpheed Claws Gtk2 and other apps that I use?

TIA

P.S. Sorry for my bad English and this long error report. If I make some typos, sorry again  ](*,)

---

### Post by urke on 2004-11-27
I get help from my friend Gox. He send me a tip to check MD5 sum of Watry's ISO image, so I do that and found MD5 failed. So I manualy download problematic packages repordet by installation process and finished Ubuntu install. Now I'm fine tune my Ubuntu box.

---

