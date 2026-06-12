---
title: "Review: Kubuntu Hardy on Asus P5QC (Intel P45 chipset)"
date: 2008-09-14
forum: Installation &amp; Upgrades
---

### Post by IgnorantGuru on 2008-09-14
[COLOR="Red"]Note:[/COLOR]  For the most up-to-date info on the Asus P5QC consult [http://wiki.ubuntu.com/Asus_P5QC]("http://wiki.ubuntu.com/Asus_P5QC")

I had read of some serious problems with the P5Q series and P45 chipset with Ubuntu but this was a fairly easy install.  I couldn't find any feedback on the P5QC/Ubuntu combo before building (which was a bit scary) so I thought I would report my results.

Components:

CPU:		Intel Core 2 Duo E8500 Wolfdale 3.16GHz 6MB L2 Cache LGA 775 65W Dual-Core
CPU Cooler:	ZEROtherm CF900 92mm CPU Cooler
CPU Paste:	Arctic Silver 5 Thermal Compound
Mainboard:	ASUS P5QC LGA 775 Intel P45 ATX Motherboard
Memory:		2GB kit (1GBx2), Crucial Ballistix 240-pin DIMM DDR3 PC3-10600 &#8226; 6-6-6-20 &#8226; Unbuffered &#8226; NON-ECC &#8226; DDR3-1333 &#8226; 1.8V &#8226; Crucial #BL2KIT12864BA1336
Video:		ASUS EN8500GT SILENT MAGIC/HTP/512M GeForce 8500GT 512MB 128-bit GDDR2 PCI Express x16 HDCP Ready Video Card
PSU:		Antec NeoPower 650 Blue 650W ATX12V / EPS12V SLI Certified CrossFire Ready 
Hard Drive: Western Digital VelociRaptor WD3000GLFS 300GB 10000 RPM 16MB Cache SATA 3.0Gb/s
DVD Drive:	ASUS DRW-2014L1T Black 20X DVD+R 8X DVD+RW 8X DVD+R DL 20X DVD-R 6X DVD-RW
Monitor:	BenQ V2400W Black-Silver 24" 2ms(GTG) HDMI Widescreen LCD Monitor 250 cd/m2 DC 4000:1(1000:1)
Capture:	ATI TV Wonder VE (PCI)  (old card, linux compatible)

**Comments on the above selections:**
I wanted a fast but quiet system that had good video for media but not for gaming.  I read that Intel has the price-performance edge on AMD now so I decided to give it a try this time.  The P5QC has some flexible features - takes both DDR2 and DDR3 memory, and has a fast FSB.  I went with Crucial's Ballistix memory for stability, low latency, and the ability to overclock it a bit (has heatsinks on the memory).  Video card has HDCP via a DVI connector (no HDMI, but same quality), and the video card is fanless which in my experience makes for a quiet system.  Antec makes quiet and quality PSUs.  The CF900 CPU cooler has heat pipes and a thermistor which controls the fan speed - pretty silent, especially when idle.  Also got some ultra-quiet case fans.  BenQ makes a nice monitor and this one has both DVI and HDMI (and DSUB).  Put it all in a nice roomy aluminum case I reused.  System is extremely quiet and runs cool at CPU 35C MB 37C.

**Comments on build:**
This was a smooth build.  CPU cooler fit great on this board (it's a rather large cooler with heatpipes that has problems with some board configurations - eg memory slots in the way).  Make sure the heatpipes face your RAM, per the intructions.  After reading reviews I bought Artic Silver 5 (OEM tube) instead of using the grease that came with the cooler.  I put two 'uncooked rice grains' worth of compound on the CPU and then screwed on the cooler.  My temps seem to be good based on other reviews.

**kubuntu-8.04.1-alternate-amd64 Install**
First I started with the 64bit version of Kubuntu 8.04.1 (alternate install CD).  The results for that are the same as the 32bit description below.  Well into the installation I gave up because I couldn't get my Brother printer/scanner to work in 64bit.  Maybe it's possible (though it doesn't look like the scanner is) but I decided to save myself the headaches.  (Even though there is much available for 64bit now, it seems there's always a showstopper for me.)

**kubuntu-8.04.1-alternate-i386 Install**
Preinstall, I set SATA to AHCI mode in the BIOS, because others said this is required for the P5Q series boards (I didn't even try the IDE mode).  I left the ACPI and other power management settings as they were.  (My BIOS is version 0803 6/26/08 and the latest on Asus site is 1306 8/25/08.  Thus far I haven't had cause to update the BIOS, but I may do so.)

The install program reported that it couldn't find an ethernet adapter.  This is due to the unsupported Atheros Gigabit LAN.  Other than that the install went smoothly.  Post-install, the system booted fine, video and all.

Asus supplies a linux driver (via module source code) for the Atheros adapter on their website.  Here's how I got it working:

Go to asus.com support and download P5QC motherboard's LinuxDrivers.zip

Unzip the file to a folder of your choice.  cd into the .../LAN/AR8121-linux-ver1.0.0.7/src folder and...

```
sudo KBUILD_NOPEDANTIC=1 make
sudo KBUILD_NOPEDANTIC=1 make install
# substitute your kernel version in the folder name below: 
cd /lib/modules/2.6.24-19-generic/kernel/drivers/net/atl1e
sudo insmod ./atl1e.ko
```

Instantly the ethernet worked - no reboot required.

LinuxDrivers.zip also contained an audio driver but I did not use it - audio seems to be working as-is.

I then did an Adept update which included a kernel update.  Because the LAN driver was a compiled kernel module I expected I would have to recompile it after the kernel update, but I did not - ethernet kept working.

Video performance was poor for playing videos so I installed the Nvidia driver.  This was as simple as: "Go to KMenu->System->Hardware Drivers Manager and check the box to enable the restricted drivers for your NVIDIA card if the option is provided."  (I actually installed nvidia-glx first but AFAIK that's not required.)

Note: In KDE, a hardware card icon will stay in the system tray after this.  Press Ctrl-Esc and kill process jockey-kde to remove it from the system tray.

The rest of the post-install setup was routine - no issues.  I have been using the system several days and it is stable and fast.  I did have to RMA my hard drive because it was emitting a very high-pitched whine.  I had a second drive in the machine so I copied the system partition onto it while I'm waiting for the replacement drive.

**Other install details I use that are not specific to this board (AFAIK):**

For full multimedia (libdvdcss2 and w32codecs, etc):
Add repo: deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) hardy free non-free
```
sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update
```
Then install:
```
sudo apt-get install libdvdcss2 w32codecs mplayer mozilla-mplayer firefox
```
Also do a full upgrade after that because Medibuntu replaces some AV packages.
Also check out my _[mplayer resume script]("http://ubuntuforums.org/showthread.php?t=805369")_.

If you want Java:
```
sudo apt-get install sun-java6-jre
```
Make a symbolic link in your Mozilla Plugins directory /usr/lib/firefox-3.0.1/plugins
pointing to /usr/lib/jvm/java-6-sun/jre/plugin/i386/ns7/libjavaplugin_oji.so
(This won't work in 64bit installs - no sun browser plugin, but I read that gjc now includes one)

Other software I find useful to have in there:
```
sudo apt-get install gimp krita crystalcursors imagemagick jhead amule khexedit libk3b2-extracodecs vcdimager kftpgrabber gftp avidemux unrar kdetv sane xsane sane-utils partimage mencoder pidgin build-essential mirage lame msttcorefonts flash-nonfree
```

**Other Notes:**
If you use _[SystemRescueCD]("http://en.wikibooks.org/wiki/How_To_Backup_Operating_Systems")_ be sure to download the latest version (v1.1.0).  I had an older version which would not boot on this board.

Congrats to Ubuntu for a great install on the P45 chipset!

---

### Post by Contrast on 2008-09-19
Very informative post, thanks for sharing all that. I've got my eye on this board for a system I'll be building in the next couple months (I'll be using mine as a media center PC also, but with a little bit of gaming), so I'll definitely keep this review in mind when I make my final decision.

As a side note, you can always just run:
```
sudo apt-get install kubuntu-restricted-extras
```
to get a lot of the extra packages you referred to in your post. It will pull in just about all the codecs you'll need, along with the Java and Flash browser plug-ins (no need to create that link in Firefox' plug-in directory, as it pulls in sun-java6-plugin).

---

### Post by IgnorantGuru on 2008-09-23
> **Contrast said:**
> As a side note, you can always just run:
```
sudo apt-get install kubuntu-restricted-extras
```

Thanks - I'll make a note of that.

As a little follow-up since my post above...

I did upgrade to the latest BIOS using a USB key and the Alt-F2 EZ Flash method.  Only hiccup was that first I backed up the old ROM to the USB key, then attempted to load the new ROM and it refused.  I rebooted and loaded the new ROM without issue.

Also, I found that the kmix slider would not change the line-in volume (which I use with my tv card via a script which adjusts kmix with dcop).  I tried installing the audio drivers but this did not change the kmix issue.  In case you do want to install the audio drivers...
```

# install curses dev (required by realtek script)
apt-get install libncurses5-dev libncursesw5-dev

#install alsaconf (required by realtek script)
apt-get install gettext dialog
wget http://backports.org/debian/pool/main/a/alsa-utils/alsa-utils_1.0.11.orig.tar.gz
tar xvzf alsa-utils_1.0.11.orig.tar.gz
cd alsa-utils-1.0.11
./configure
make install 

#realtek
cd realtek-linux-audiopack-5.01  #wherever
./install

# in alsaconf  - choose intel-hda sound card

```

The workaround I found was to adjust the line-in (capture0) volume in alsamixer.  Or in a script use amixer:

```
# turn on capture0 (line-in)
amixer set 'Capture',0 cap > /dev/null
# Set capture0 (line-in) volume (not working in kmix)
amixer set 'Capture',0 50% > /dev/null
```

I know you didn't ask for all that but I just thought I would record it here for reference.

---

### Post by IgnorantGuru on 2008-11-14
I have created a wiki for the Asus P5QC here...
[http://wiki.ubuntu.com/Asus_P5QC](http://wiki.ubuntu.com/Asus_P5QC)

That includes an update today on my positive test results with Intrepid.

With continuous use under Kubuntu Hardy, this board has proved to be very stable.  Although I only used Intrepid for a short time due to issues with KDE4 (not board-related AFAIK), it looked to be stable with Intrepid as well.

---

### Post by sir_dave on 2008-12-27
Hi to all,

thanks IgnorantGuru for your Review and your great wiki page. I'm thinking of getting the same board, that's why I just wanted to ask if in your case hibernation and suspend mode work ("out of the box") with Asus P5QC and (e.g.) Intrepid Ibex.

sir_dave

---

### Post by IgnorantGuru on 2008-12-27
> **sir_dave said:**
> I just wanted to ask if in your case hibernation and suspend mode work ("out of the box") with Asus P5QC and (e.g.) Intrepid Ibex.

Hi - I am primarily using Hardy still because I had some disagreements with KDE4 (not hardware related).  I also still have a beta version of Intrepid on my system.  I just tested suspend and hibernate on Hardy and Intrepid beta and it all appeared to work fine.  So I don't think you'll have a problem with Intrepid.

---

