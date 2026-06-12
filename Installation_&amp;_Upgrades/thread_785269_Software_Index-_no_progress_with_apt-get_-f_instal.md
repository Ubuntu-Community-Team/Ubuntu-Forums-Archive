---
title: "Software Index- no progress with apt-get -f install"
date: 2008-05-07
forum: Installation &amp; Upgrades
---

### Post by fuzzbuzz85 on 2008-05-07
Hi all,

having quite the nightmare with ubuntu these days. 
I'm (attempting) to run ubuntu on my computer and I'm very new to linux. I have an Athlon XP 2000+, 2 HDs - 160G and 20G and so far have had the following problems:

- Tried to install hardy but had massive problems with errno 5, resulting in me burning about 8 CDs and DVDs trying to get it to work (it didn't). Then burned 7.04 and updated to Gutsy from there, which is where I am now.
- When I open the update manager it says: 'Software Index is Broken'. On opening synaptic it tells me that 3 packages are broken, they are:
	- hpijs
	- hplip
	- xsane
note that the first two are for a HP printer (I don't have a printer), and the last for scanning (I don't have a scanner), so I'm sure you can appreciate my irritation that these two things are blocking me from upgrading!

Anyway

- Tried to fix broken packages, and get following error: "Changes applied: Not all changes and updates succeeded. For further details of the failure, please open terminal below" I expand 'details' and the terminal is empty.

- I now attempt sudo apt-get update in terminal, which ends thus:

"Fetched 7618kB in 37s (204kB/s)                                                
Reading package lists... Done
W: Encountered status field in a non-version description
W: You may want to run apt-get update to correct these problems
sophie@sophie-desktop:~$ "

So I sudo apt-get update again - same message
Then I have a go at sudo apt-get install, which ends

"You might want to run ‘apt-get -f install’ to correct these.
The following packages have unmet dependencies.
  hpijs: Depends: libsane (>= 1.0.11-3) but it is not installed
  hplip: Depends: libsane (>= 1.0.11-3) but it is not installed
  xsane: Depends: libsane (>= 1.0.11-3) but it is not installed
E: Unmet dependencies. Try using -f."

Then I have a go at sudo apt-get -f install:

"The following extra packages will be installed:
  libsane
Suggested packages:
  libsane-doc libsane-extras hpoj
Recommended packages:
  sane-utils
The following NEW packages will be installed
  libsane
0 upgraded, 1 newly installed, 0 to remove and 25 not upgraded.
14 not fully installed or removed.
Need to get 0B/2607kB of archives.
After unpacking 7832kB of additional disk space will be used.
Do you want to continue [Y/n]? y
dpkg: parse error, in file `/var/lib/dpkg/status' near line 761 package `libsane':
 missing version
E: Sub-process /usr/bin/dpkg returned an error code (2)"

So then I have a look at /var/lib/dpkg/status, which tells me that libsane is 'install ok installed'. Hm.

For giggles, I also have a go at sudo dpkg --configure -a:

"sophie@sophie-desktop:~$ sudo dpkg --configure -a
dpkg: parse error, in file `/var/lib/dpkg/status' near line 761 package `libsane':
 missing version
sophie@sophie-desktop:~$"

entry at line 761 is blank. Entry for libsane is: 

"Package: libsane
Status: install ok installed
Priority: optional
Section: libs
Installed-Size: 7648
Maintainer: Ubuntu Core Developers <ubuntu-devel@lists.ubuntu.com>
Architecture: i386
Source: sane-backends
Versikn: 1.0.19~cvs20070505-3ubuntu2
Replaces: libsane-extras (<< 1.0.18.6)
Depends: adduser (>= 3.47), makedev (>= 2.3.1-58), libc6 (>= 2.6-1), libexif12, libgphoto2-2 (>= 2.4.0), libgphoto2-port0 (>= 2.4.0), libieee1284-3, libjpeg62, libtiff4, libusb-0.1-4 (>= 2:0.1.12)
Recommends: udev (>= 0.88-1), module-init-tools (>= 3.2.2-1), sane-utils (>= 1.0.19~cvs20070505-3ubuntu2)
Suggests: libsane-doc, libsane-extras (>= 1.0.18.6), hpoj, hplip
Conflicts: libsane-extras (<< 1.0.18.6)
Conffiles:
 /etc/sane.d/abaton.conf 51591e7ab98851effab49089323cb160
 /etc/sane.d/agfafocus.conf f763f1f31d26507986aad58ca02f79f9
 /etc/sane.d/apple.conf 602eda3ecedd81ef751d9241becb9142
 /etc/sane.d/artec.conf 1b87eeb6069e6f5ac7b5f0cc4bf48083
 /etc/sane.d/avision.conf ace6554933c43240c12b1fd56c38e398
 /etc/sane.d/bh.conf ed8e137983ae58a7bf038180b29737bd
 /etc/sane.d/canon.conf 4afe1a9ccf3c40ff7b667ac7dfb1de25
 /etc/sane.d/canon630u.conf 5fae93df3328f1915e3d26f77a8c3b9d
 /etc/sane.d/coolscan.conf b5a49230bc9b80a4358d966255d4697a
 /etc/sane.d/coolscan2.conf e9039d4f201acacca70e8964ec22ee70
 /etc/sane.d/dc25.conf 0659d0dee2b39c585b6ebc682af0dbd9
 /etc/sane.d/dmc.conf 0731b2373c97cc98c5c42dd56e7fb05c
 /etc/sane.d/epson.conf 318ed78f38b29c99e478cbc7efc8ff14
 /etc/sane.d/fujitsu.conf a430acdbf491ec610a07698b7f40287d
 /etc/sane.d/genesys.conf 7aaf7732969e3445ec6a95e81f88239e
 /etc/sane.d/gt68xx.conf f845a556f99539317c890b5549de35a2
 /etc/sane.d/hp.conf 5328dfe188ece714bf9fdb7e26dc9d00
 /etc/sane.d/leo.conf 008b9b3cad3c7073aa5331a453e68cd6
 /etc/sane.d/lexmark.conf b68eb29617c2a862221ae17fb5fa51b7
 /etc/sane.d/matsushita.conf fe9a8941cd52c7e012724122d67a98e6
 /etc/sane.d/microtek.conf 940c8db7e01ccaa6f2c5be2ca020ddf1
 /etc/sane.d/microtek2.conf 75cb498c51441db57932a4895f7f0d96
 /etc/sane.d/mustek.conf 33284fd785df74d394b9e30a4ec8283e
 /etc/sane.d/mustek_usb.conf f4080c5eacaf30b4ed871a5330960696
 /etc/sane.d/nec.conf 5eed67a9759c991553fa3055af023a33
 /etc/sane.d/pie.conf 7bdb319bd61b19389e93ed85a1ed85d1
 /etc/sane.d/plustek.conf 32da8837e990a3b3996a5a6688ee341a
 /etc/sane.d/plustek_pp.conf 327941a5240e699e3251d74192f4f299
 /etc/sane.d/ricoh.conf b1891143384a7308ec17d9e6ac836201
 /etc/sane.d/s9036.conf 5eed67a9759c991553fa3055af023a33
 /etc/sane.d/sceptre.conf 9d7e8954714b47042b849ddbd2530973
 /etc/sane.d/sharp.conf d16cb589cdceb30d4523334063ddf040
 /etc/sane.d/sp15c.conf 74fd71c4ea2c8c58bbaa2cecfee56f7c
 /etc/sane.d/st400.conf febd1d7966858a4a0352a2fe2c1abfa0
 /etc/sane.d/tamarack.conf 93b1a500916dcfabd8a1c288029a5502
 /etc/sane.d/test.conf eaccee9d3fb610a691705ddf94b9ec11
 /etc/sane.d/teco1.conf 7976c7a3dd90fe100f30a23a29aaea89
 /etc/sane.d/teco2.conf 1f873f79332e99cb0cd2b9eba938ac3b
 /etc/sane.d/teco3.conf 7b632784a85ec6ead7d26e8fd195dea5
 /etc/sane.d/umax.conf 5bcadfd7842926832de6d6e29d23558d
 /etc/sane.d/umax_pp.conf 926aec7aab8c8a577016afe625a73d83
 /etc/sane.d/umax1220u.conf 2d36f1f6c15bbfeaf2049d59dcfefe05
 /etc/sane.d/artec_eplus48u.conf 3672fe16e6b14a124ad74acd47941be9
 /etc/sane.d/ma1509.conf 73a9fd7af5924e04054f43e2708f5059
 /etc/sane.d/ibm.conf d5eab60adbaf729bb5bf781fc4c5409d
 /etc/sane.d/hp5400.conf 25848f289fb76aeb7f78e29ab323dbf8
 /etc/sane.d/u12.conf 9ab31cd28e79474973fc02ccf1c06b99
 /etc/sane.d/snapscan.conf b349efcbcec257f5fca8372f1e47e7e0
 /etc/sane.d/sm3840.conf 9b61359cbcc14b9be4d687b80b772bea
 /etc/sane.d/hp4200.conf 0656916d9805c3af1f81424354082501
 /etc/sane.d/stv680.conf 1a5a8d37f0de964bab25b3908fa907d5
 /etc/sane.d/epson2.conf f670edaaf5407234fb2ef3d40c80e034
 /etc/sane.d/dc210.conf 821754802fb212acc9f48c7dd93ddaa1
 /etc/sane.d/dc240.conf 821754802fb212acc9f48c7dd93ddaa1
 /etc/sane.d/canon_pp.conf 2ecfac7c883bc980aba880f424abb8ad
 /etc/sane.d/hpsj5s.conf 0e969889a4509e62ef352a0222d2620e
 /etc/sane.d/mustek_pp.conf c9d10da50e4b77dcc73b97f67a81a89a
 /etc/sane.d/dell1600n_net.conf ce26ec480900a2420d14d5f2c43f07eb
 /etc/sane.d/gphoto2.conf ca55d23d02774d6eea321dcbd4099e5e
 /etc/sane.d/qcam.conf 7a30e22cd391b7992646723df280f4fe
 /etc/sane.d/v4l.conf c68d472ee915c19d73f255623f4e0223
 /etc/sane.d/net.conf 74d6e085fcf8737e0af676efcb5882c1
 /etc/sane.d/dll.conf 2ff6e3dcebb0852b0d8533c74a0e1db7
 /etc/udev/rules.d/45-libsane.rules 8510e8fda2b256c9698606c1c5546c00
 /etc/modprobe.d/blacklist-scanner ca2a722bce32d218ac6049c3b50c7b85
Description: API library for scanners
 SANE stands for "Scanner Access Now Easy" and is an application
 programming interface (API) that provides standardized access to any
 raster image scanner hardware (flatbed scanner, hand-held scanner,
 video- and still-cameras, frame-grabbers, etc.). The SANE standard is
 free and its discussion and development are open to everybody. The
 current source code is written to support several operating systems,
 including GNU/Linux, OS/2, Win32 and various Unices and is available
 under the GNU General Public License (commercial applications and
 backends are welcome, too, however).
 .
 This package includes the backends for many scanners. A libsane-extras
 package containing some not-yet-included backends is available separately.
 .
 Graphical frontends for sane are available in the packages sane and
 xsane. Command line frontend scanimage, saned and sane-find-scanner are
 available in the sane-utils package.
Original-Maintainer: Julien BLACHE <jblache@debian.org>"

All very annoying, and I'm just going around in circles!
Other problems I've encountered is that firefox isn't really working properly - the 'back' and 'forward' buttons don't function, and I can't set a home page etc. When you open a page from a link the URL doesn't come up in the address box, and worst of all firefox closes whenever I try and paste this message from gedit into the text box, so I've had to do this from my laptop!!... Ho hum..


Anyway, I hope i've provided enough information to be able to supply some ideas coz I'm out of them!
TIA!

---

### Post by fuzzbuzz85 on 2008-05-07
anyone?

---

### Post by fuzzbuzz85 on 2008-05-07
**bump**

---

### Post by fuzzbuzz85 on 2008-05-07
As an update - I seemed to make *some* progress with whacking the alternate hardy cd in the drive and trying to update from there... but then it failed, finally, with the same 'parse; missing version' nonsense it said before. Harumph! 

Strangely, it's now changed all my repositories to hardy, even tho the upgrade technically failed. Ho hum.

---

