---
title: "Package System is Brokem"
date: 2023-04-28
forum: Installation &amp; Upgrades
---

### Post by Tulf on 2023-04-28
I've had an issue with my package system for a few weeks now. I think it may have started when I tried to install wine but I don't see any issues relating to that attempt from the error output.
Regardless attempting to run an update with updater results with this:

I've removed all third party package sources as well as all "Other Software" sources in Updater so update runs fine and returns with:
> 
Hit:1 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) jammy InReleaseHit:2 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) jammy-updates InRelease            
Hit:3 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) jammy-backports InRelease          
Hit:4 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jammy-security InRelease             
Reading package lists... Done                          
Building dependency tree... Done
Reading state information... Done
22 packages can be upgraded. Run 'apt list --upgradable' to see them.


Upgrade obviously doesn't work and results in an unmet dependency for gstreamer1.0-plugins-bad:

> 
The following packages have unmet dependencies: gstreamer1.0-plugins-bad : Depends: libldacbt-enc2 (>= 2.0.2) but it is not installed
E: Unmet dependencies. Try 'apt --fix-broken install' with no packages (or specify a solution).




Same with -f flags and running 'apt --fix-broken install' gives a similar error:

> 
Unpacking libldacbt-enc2:amd64 (2.0.2.3+git20200429+ed310a0-4) ...
dpkg: error processing archive /var/cache/apt/archives/libldacbt-enc2_2.0.2.3+gi
t20200429+ed310a0-4_amd64.deb (--unpack):
 trying to overwrite '/usr/lib/x86_64-linux-gnu/libldacBT_enc.so.2', which is al
so in package libldac:amd64 2.0.2.3~r26478861
Errors were encountered while processing:
 /var/cache/apt/archives/libldacbt-enc2_2.0.2.3+git20200429+ed310a0-4_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)


I've tried deleting the contents of the archive: /var/cache/apt/archives/libldacbt-enc2_2.0.2.3+git20200429+ed310a0-4_amd64.deb as recommended elsewhere to no avail as fix broken install yields the same error as before. 
Same goes with "dist upgrade"

I've also tried purging gstreamer1.0-plugins bad and libldacbtenc with no results. 

Some places have suggested this is an issue with jammy or a conflicting instruction set version which I can't seem to replicate on my system but I'm not sure. 

I'm on Ubuntu 22.04.2 LTS with livepatch if that makes any difference.

I'm really at a loss for what to do, and am considering just doing a clean install again, but wanted to see if anyone here has any inputs. 

Thank you for reading and I greatly appreciate any advice you may have to offer.

---

### Post by ian-weisser on 2023-04-28
[Retracted]

---

### Post by Tulf on 2023-04-28
Forgot to add that I'm using a proprietary NVIDIA driver for my GeForce GTX 1050 Ti Mobile, nvidia-driver-525 (proprietary)
trying to change to 530 yields:
> 
pk-client-error-quark: Error while installing package: trying to overwrite 'usr/lib/x86_64-linux-gnu/libldacBT_enc.so.2', which is also in package libldac (313)


ran apt-clean then  update-m and then dpkg --configure -a gave:
Errors were encountered while processing:
 gstreamer1.0-plugins-bad:amd64
 pulseeffects

then ran sudo apt list --upgradable:

> 
Listing... Done
apt-transport-https/jammy-updates,jammy-updates 2.4.9 all [upgradable from: 2.4.8]
dnsmasq-base/jammy-updates,jammy-security 2.86-1.1ubuntu0.3 amd64 [upgradable from: 2.86-1.1ubuntu0.2]
ipp-usb/jammy-updates,jammy-security 0.9.20-1ubuntu0.22.04.1 amd64 [upgradable from: 0.9.20-1]
libglib2.0-0/jammy-updates 2.72.4-0ubuntu2 amd64 [upgradable from: 2.72.4-0ubuntu1]
libglib2.0-0/jammy-updates 2.72.4-0ubuntu2 i386 [upgradable from: 2.72.4-0ubuntu1]
libglib2.0-bin/jammy-updates 2.72.4-0ubuntu2 amd64 [upgradable from: 2.72.4-0ubuntu1]
libglib2.0-data/jammy-updates,jammy-updates 2.72.4-0ubuntu2 all [upgradable from: 2.72.4-0ubuntu1]
libssl3/jammy-updates,jammy-security 3.0.2-0ubuntu1.9 amd64 [upgradable from: 3.0.2-0ubuntu1.8]
libssl3/jammy-updates,jammy-security 3.0.2-0ubuntu1.9 i386 [upgradable from: 3.0.2-0ubuntu1.8]
linux-generic/jammy-updates,jammy-security 5.15.0.71.69 amd64 [upgradable from: 5.15.0.69.67]
linux-headers-generic/jammy-updates,jammy-security 5.15.0.71.69 amd64 [upgradable from: 5.15.0.69.67]
linux-image-generic/jammy-updates,jammy-security 5.15.0.71.69 amd64 [upgradable from: 5.15.0.69.67]
linux-libc-dev/jammy-updates,jammy-security 5.15.0-71.78 amd64 [upgradable from: 5.15.0-69.76]
linux-modules-nvidia-525-generic/jammy-updates,jammy-security 5.15.0-71.78 amd64 [upgradable from: 5.15.0-69.76+1]
openssl/jammy-updates,jammy-security 3.0.2-0ubuntu1.9 amd64 [upgradable from: 3.0.2-0ubuntu1.8]
tzdata/jammy-updates,jammy-updates 2023c-0ubuntu0.22.04.1 all [upgradable from: 2023c-0ubuntu0.22.04.0]
ubuntu-advantage-tools/jammy-updates 27.14.4~22.04 amd64 [upgradable from: 27.13.6~22.04.1]
vim-common/jammy-updates,jammy-updates,jammy-security,jammy-security 2:8.2.3995-1ubuntu2.7 all [upgradable from: 2:8.2.3995-1ubuntu2.5]
vim-runtime/jammy-updates,jammy-updates,jammy-security,jammy-security 2:8.2.3995-1ubuntu2.7 all [upgradable from: 2:8.2.3995-1ubuntu2.5]
vim-tiny/jammy-updates,jammy-security 2:8.2.3995-1ubuntu2.7 amd64 [upgradable from: 2:8.2.3995-1ubuntu2.5]
vim/jammy-updates,jammy-security 2:8.2.3995-1ubuntu2.7 amd64 [upgradable from: 2:8.2.3995-1ubuntu2.5]
xxd/jammy-updates,jammy-security 2:8.2.3995-1ubuntu2.7 amd64 [upgradable from: 2:8.2.3995-1ubuntu2.5]


then apt upgrade -f:
> 
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
Correcting dependencies... Done
Calculating upgrade... Done
Get more security updates through Ubuntu Pro with 'esm-apps' enabled:
  libimage-magick-perl imagemagick libjs-jquery-ui libavdevice58 ffmpeg
  libopenexr25 libmagick++-6.q16-8 libpostproc55 libmagickcore-6.q16-6-extra
  libimage-magick-q16-perl libmagickwand-6.q16-6 libavcodec-extra58
  libpython2.7 libavutil56 imagemagick-6.q16 libswscale5 libmagickcore-6.q16-6
  libswresample3 imagemagick-6-common libavformat58 libpython2.7-minimal
  libpython2.7-stdlib libavfilter7
Learn more about Ubuntu Pro at [https://ubuntu.com/pro](https://ubuntu.com/pro)
The following NEW packages will be installed:
  libldacbt-enc2 linux-headers-5.15.0-71 linux-headers-5.15.0-71-generic
  linux-image-5.15.0-71-generic linux-modules-5.15.0-71-generic
  linux-modules-extra-5.15.0-71-generic
  linux-modules-nvidia-525-5.15.0-71-generic
  linux-objects-nvidia-525-5.15.0-71-generic
  linux-signatures-nvidia-5.15.0-71-generic
The following packages will be upgraded:
  apt-transport-https dnsmasq-base ipp-usb libglib2.0-0 libglib2.0-0:i386
  libglib2.0-bin libglib2.0-data libssl3 libssl3:i386 linux-generic
  linux-headers-generic linux-image-generic linux-libc-dev
  linux-modules-nvidia-525-generic openssl tzdata ubuntu-advantage-tools vim
  vim-common vim-runtime vim-tiny xxd
22 upgraded, 9 newly installed, 0 to remove and 0 not upgraded.
2 not fully installed or removed.
15 standard LTS security updates
Need to get 193 MB/193 MB of archives.
After this operation, 729 MB of additional disk space will be used.
Do you want to continue? [Y/n] y
Get:1 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) jammy-updates/main amd64 libglib2.0-bin amd64 2.72.4-0ubuntu2 [80.9 kB]
Get:2 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) jammy-updates/main i386 libglib2.0-0 i386 2.72.4-0ubuntu2 [1,567 kB]
Get:3 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) jammy-updates/main amd64 libglib2.0-0 amd64 2.72.4-0ubuntu2 [1,462 kB]
Get:4 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) jammy-updates/main amd64 libglib2.0-data all 2.72.4-0ubuntu2 [4,968 B]
Get:5 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) jammy-updates/main i386 libssl3 i386 3.0.2-0ubuntu1.9 [1,943 kB]
Get:6 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) jammy-updates/main amd64 libssl3 amd64 3.0.2-0ubuntu1.9 [1,902 kB]
Get:7 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) jammy-updates/main amd64 openssl amd64 3.0.2-0ubuntu1.9 [1,185 kB]
Get:8 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) jammy-updates/main amd64 tzdata all 2023c-0ubuntu0.22.04.1 [354 kB]
Get:9 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) jammy-updates/main amd64 ubuntu-advantage-tools amd64 27.14.4~22.04 [171 kB]
Get:10 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) jammy-updates/main amd64 vim amd64 2:8.2.3995-1ubuntu2.7 [1,728 kB]
Get:11 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) jammy-updates/main amd64 vim-tiny amd64 2:8.2.3995-1ubuntu2.7 [707 kB]
Get:12 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) jammy-updates/main amd64 vim-runtime all 2:8.2.3995-1ubuntu2.7 [6,825 kB]
Get:13 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) jammy-updates/main amd64 xxd amd64 2:8.2.3995-1ubuntu2.7 [53.7 kB]
Get:14 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) jammy-updates/main amd64 vim-common all 2:8.2.3995-1ubuntu2.7 [81.5 kB]
Get:15 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) jammy-updates/universe amd64 apt-transport-https all 2.4.9 [1,510 B]
Get:16 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) jammy-updates/main amd64 dnsmasq-base amd64 2.86-1.1ubuntu0.3 [354 kB]
Get:17 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) jammy-updates/main amd64 ipp-usb amd64 0.9.20-1ubuntu0.22.04.1 [2,017 kB]
Get:18 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) jammy-updates/main amd64 linux-modules-5.15.0-71-generic amd64 5.15.0-71.78 [23.2 MB]
Get:19 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) jammy-updates/main amd64 linux-image-5.15.0-71-generic amd64 5.15.0-71.78 [11.4 MB]
Get:20 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) jammy-updates/main amd64 linux-modules-extra-5.15.0-71-generic amd64 5.15.0-71.78 [64.3 MB]
Get:21 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) jammy-updates/main amd64 linux-generic amd64 5.15.0.71.69 [1,696 B]
Get:22 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) jammy-updates/main amd64 linux-image-generic amd64 5.15.0.71.69 [2,492 B]
Get:23 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) jammy-updates/main amd64 linux-headers-5.15.0-71 all 5.15.0-71.78 [12.3 MB]
Get:24 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) jammy-updates/main amd64 linux-headers-5.15.0-71-generic amd64 5.15.0-71.78 [2,884 kB]
Get:25 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) jammy-updates/main amd64 linux-headers-generic amd64 5.15.0.71.69 [2,346 B]
Get:26 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) jammy-updates/main amd64 linux-libc-dev amd64 5.15.0-71.78 [1,323 kB]
Get:27 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) jammy-updates/restricted amd64 linux-signatures-nvidia-5.15.0-71-generic amd64 5.15.0-71.78 [35.1 kB]
Get:28 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) jammy-updates/restricted amd64 linux-objects-nvidia-525-5.15.0-71-generic amd64 5.15.0-71.78 [56.7 MB]
Get:29 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) jammy-updates/restricted amd64 linux-modules-nvidia-525-5.15.0-71-generic amd64 5.15.0-71.78 [7,022 B]
Get:30 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) jammy-updates/restricted amd64 linux-modules-nvidia-525-generic amd64 5.15.0-71.78 [5,354 B]
Fetched 193 MB in 36s (5,317 kB/s)                                             
Extracting templates from packages: 100%
Preconfiguring packages ...
(Reading database ... 315821 files and directories currently installed.)
Preparing to unpack .../00-libglib2.0-bin_2.72.4-0ubuntu2_amd64.deb ...
Unpacking libglib2.0-bin (2.72.4-0ubuntu2) over (2.72.4-0ubuntu1) ...
Preparing to unpack .../01-libglib2.0-0_2.72.4-0ubuntu2_amd64.deb ...
De-configuring libglib2.0-0:i386 (2.72.4-0ubuntu1), to allow configuration of li
bglib2.0-0:amd64 (2.72.4-0ubuntu1) ...
Unpacking libglib2.0-0:amd64 (2.72.4-0ubuntu2) over (2.72.4-0ubuntu1) ...
Preparing to unpack .../02-libglib2.0-0_2.72.4-0ubuntu2_i386.deb ...
Unpacking libglib2.0-0:i386 (2.72.4-0ubuntu2) over (2.72.4-0ubuntu1) ...
Preparing to unpack .../03-libglib2.0-data_2.72.4-0ubuntu2_all.deb ...
Unpacking libglib2.0-data (2.72.4-0ubuntu2) over (2.72.4-0ubuntu1) ...
Preparing to unpack .../04-libldacbt-enc2_2.0.2.3+git20200429+ed310a0-4_amd64.de
b ...
Unpacking libldacbt-enc2:amd64 (2.0.2.3+git20200429+ed310a0-4) ...
dpkg: error processing archive /tmp/apt-dpkg-install-PANafk/04-libldacbt-enc2_2.
0.2.3+git20200429+ed310a0-4_amd64.deb (--unpack):
 trying to overwrite '/usr/lib/x86_64-linux-gnu/libldacBT_enc.so.2', which is al
so in package libldac:amd64 2.0.2.3~r26478861
Preparing to unpack .../05-libssl3_3.0.2-0ubuntu1.9_amd64.deb ...
De-configuring libssl3:i386 (3.0.2-0ubuntu1.8), to allow configuration of libssl
3:amd64 (3.0.2-0ubuntu1.8) ...
Unpacking libssl3:amd64 (3.0.2-0ubuntu1.9) over (3.0.2-0ubuntu1.8) ...
Preparing to unpack .../06-libssl3_3.0.2-0ubuntu1.9_i386.deb ...
Unpacking libssl3:i386 (3.0.2-0ubuntu1.9) over (3.0.2-0ubuntu1.8) ...
Preparing to unpack .../07-openssl_3.0.2-0ubuntu1.9_amd64.deb ...
Unpacking openssl (3.0.2-0ubuntu1.9) over (3.0.2-0ubuntu1.8) ...
Preparing to unpack .../08-tzdata_2023c-0ubuntu0.22.04.1_all.deb ...
Unpacking tzdata (2023c-0ubuntu0.22.04.1) over (2023c-0ubuntu0.22.04.0) ...
Preparing to unpack .../09-ubuntu-advantage-tools_27.14.4~22.04_amd64.deb ...
Unpacking ubuntu-advantage-tools (27.14.4~22.04) over (27.13.6~22.04.1) ...
Preparing to unpack .../10-vim_2%3a8.2.3995-1ubuntu2.7_amd64.deb ...
Unpacking vim (2:8.2.3995-1ubuntu2.7) over (2:8.2.3995-1ubuntu2.5) ...
Preparing to unpack .../11-vim-tiny_2%3a8.2.3995-1ubuntu2.7_amd64.deb ...
Unpacking vim-tiny (2:8.2.3995-1ubuntu2.7) over (2:8.2.3995-1ubuntu2.5) ...
Preparing to unpack .../12-vim-runtime_2%3a8.2.3995-1ubuntu2.7_all.deb ...
Unpacking vim-runtime (2:8.2.3995-1ubuntu2.7) over (2:8.2.3995-1ubuntu2.5) ...
Preparing to unpack .../13-xxd_2%3a8.2.3995-1ubuntu2.7_amd64.deb ...
Unpacking xxd (2:8.2.3995-1ubuntu2.7) over (2:8.2.3995-1ubuntu2.5) ...
Preparing to unpack .../14-vim-common_2%3a8.2.3995-1ubuntu2.7_all.deb ...
Unpacking vim-common (2:8.2.3995-1ubuntu2.7) over (2:8.2.3995-1ubuntu2.5) ...
Preparing to unpack .../15-apt-transport-https_2.4.9_all.deb ...
Unpacking apt-transport-https (2.4.9) over (2.4.8) ...
Preparing to unpack .../16-dnsmasq-base_2.86-1.1ubuntu0.3_amd64.deb ...
Unpacking dnsmasq-base (2.86-1.1ubuntu0.3) over (2.86-1.1ubuntu0.2) ...
Preparing to unpack .../17-ipp-usb_0.9.20-1ubuntu0.22.04.1_amd64.deb ...
Unpacking ipp-usb (0.9.20-1ubuntu0.22.04.1) over (0.9.20-1) ...
Selecting previously unselected package linux-modules-5.15.0-71-generic.
Preparing to unpack .../18-linux-modules-5.15.0-71-generic_5.15.0-71.78_amd64.de
b ...
Unpacking linux-modules-5.15.0-71-generic (5.15.0-71.78) ...
Selecting previously unselected package linux-image-5.15.0-71-generic.
Preparing to unpack .../19-linux-image-5.15.0-71-generic_5.15.0-71.78_amd64.deb 
...
Unpacking linux-image-5.15.0-71-generic (5.15.0-71.78) ...
Selecting previously unselected package linux-modules-extra-5.15.0-71-generic.
Preparing to unpack .../20-linux-modules-extra-5.15.0-71-generic_5.15.0-71.78_am
d64.deb ...
Unpacking linux-modules-extra-5.15.0-71-generic (5.15.0-71.78) ...
Preparing to unpack .../21-linux-generic_5.15.0.71.69_amd64.deb ...
Unpacking linux-generic (5.15.0.71.69) over (5.15.0.69.67) ...
Preparing to unpack .../22-linux-image-generic_5.15.0.71.69_amd64.deb ...
Unpacking linux-image-generic (5.15.0.71.69) over (5.15.0.69.67) ...
Selecting previously unselected package linux-headers-5.15.0-71.
Preparing to unpack .../23-linux-headers-5.15.0-71_5.15.0-71.78_all.deb ...
Unpacking linux-headers-5.15.0-71 (5.15.0-71.78) ...
Selecting previously unselected package linux-headers-5.15.0-71-generic.
Preparing to unpack .../24-linux-headers-5.15.0-71-generic_5.15.0-71.78_amd64.de
b ...
Unpacking linux-headers-5.15.0-71-generic (5.15.0-71.78) ...
Preparing to unpack .../25-linux-headers-generic_5.15.0.71.69_amd64.deb ...
Unpacking linux-headers-generic (5.15.0.71.69) over (5.15.0.69.67) ...
Preparing to unpack .../26-linux-libc-dev_5.15.0-71.78_amd64.deb ...
Unpacking linux-libc-dev:amd64 (5.15.0-71.78) over (5.15.0-69.76) ...
Selecting previously unselected package linux-signatures-nvidia-5.15.0-71-generi
c.
Preparing to unpack .../27-linux-signatures-nvidia-5.15.0-71-generic_5.15.0-71.7
8_amd64.deb ...
Unpacking linux-signatures-nvidia-5.15.0-71-generic (5.15.0-71.78) ...
Selecting previously unselected package linux-objects-nvidia-525-5.15.0-71-gener
ic.
Preparing to unpack .../28-linux-objects-nvidia-525-5.15.0-71-generic_5.15.0-71.
78_amd64.deb ...
Unpacking linux-objects-nvidia-525-5.15.0-71-generic (5.15.0-71.78) ...
Selecting previously unselected package linux-modules-nvidia-525-5.15.0-71-gener
ic.
Preparing to unpack .../29-linux-modules-nvidia-525-5.15.0-71-generic_5.15.0-71.
78_amd64.deb ...
Unpacking linux-modules-nvidia-525-5.15.0-71-generic (5.15.0-71.78) ...
Preparing to unpack .../30-linux-modules-nvidia-525-generic_5.15.0-71.78_amd64.d
eb ...
Unpacking linux-modules-nvidia-525-generic (5.15.0-71.78) over (5.15.0-69.76+1) 
...
Errors were encountered while processing:
 /tmp/apt-dpkg-install-PANafk/04-libldacbt-enc2_2.0.2.3+git20200429+ed310a0-4_am
d64.deb




---

### Post by Tulf on 2023-04-28
Thanks for the response

I checked my logs and they don't seem to mentioned the wine install (I may have cleared then as they only go back to the 7th of this month).

It seems that 
Remove: linux-modules-nvidia-525-5.15.0-60-generic:amd64 (5.15.0-60.66)

Prompts the 

Error: Sub-process /usr/bin/dpkg returned an error code (1)

this is from packagekit role='install-packages'

Basically throws the same error over and over again ever for autoremove, purges etc.

---

### Post by Impavidus on 2023-04-29
There's a conflict between the packages libldacbt-enc2 and libldac. The package libldacbt-enc2 is from the official repos and you've got the right version. The package libldac is not from the official repos. It must come from some source that provides the same software, packed differently. You may have disabled third-party sources, but not removed the software coming from those.

Try removing libldac.

BTW, there should be older versions of logs. Look for a log file with a .1 suffix. Even older may get .2.gz, .3.gz etc. The old ones get compressed. dpkg.log goes back a full year, unless you changed the settings of logrotate.

---

### Post by Tulf on 2023-04-30
Thanks for the reply. libldac is definitely a foreign package but I have no idea how to remove it as apt remove --autoremove gives the dependency error and dkpg -p says the package is not available
I checked my older apt logs (dpkg had no errors) and I'm missing the logs from 3/28 to 4/7. I may not have been as active during that period but I definitely used my comp during that time so it's a little strange. regardless the earliest issue shows this:

> 
Start-Date: 2023-03-28  23:57:46
Commandline: packagekit role='update-packages'
Install: linux-modules-nvidia-525-5.15.0-69-generic:amd64 (5.15.0-69.76, automatic), linux-modules-5.15.0-69-generic:amd64 (5.15.0-69.76, automatic), linux-modules-extra-5.15.0-69-generic:amd64 (5.15.0-69.76, automatic), linux-objects-nvidia-525-5.15.0-69-generic:amd64 (5.15.0-69.76, automatic), libldacbt-enc2:amd64 (2.0.2.3+git20200429+ed310a0-4, automatic), linux-headers-5.15.0-69:amd64 (5.15.0-69.76, automatic), linux-signatures-nvidia-5.15.0-69-generic:amd64 (5.15.0-69.76, automatic), linux-image-5.15.0-69-generic:amd64 (5.15.0-69.76, automatic), linux-headers-5.15.0-69-generic:amd64 (5.15.0-69.76, automatic)
Upgrade: tcpdump:amd64 (4.99.1-3build2, 4.99.1-3ubuntu0.1), libcurl4:amd64 (7.81.0-1ubuntu1.8, 7.81.0-1ubuntu1.10), libreoffice-calc:amd64 (1:7.3.7-0ubuntu0.22.04.1, 1:7.3.7-0ubuntu0.22.04.2), libnvidia-common-525:amd64 (525.78.01-0ubuntu0.22.04.1, 525.89.02-0ubuntu0.22.04.1), libimage-magick-perl:amd64 (8:6.9.11.60+dfsg-1.3ubuntu0.22.04.1, 8:6.9.11.60+dfsg-1.3ubuntu0.22.04.2), libnvidia-fbc1-525:amd64 (525.78.01-0ubuntu0.22.04.1, 525.89.02-0ubuntu0.22.04.1), libnvidia-fbc1-525:i386 (525.78.01-0ubuntu0.22.04.1, 525.89.02-0ubuntu0.22.04.1), python3.10:amd64 (3.10.6-1~22.04.2, 3.10.6-1~22.04.2ubuntu1), libreoffice-gnome:amd64 (1:7.3.7-0ubuntu0.22.04.1, 1:7.3.7-0ubuntu0.22.04.2), libmm-glib0:amd64 (1.18.6-1, 1.20.0-1~ubuntu22.04.1), evince:amd64 (42.3-0ubuntu2, 42.3-0ubuntu3), libsnmp-base:amd64 (5.9.1+dfsg-1ubuntu2.4, 5.9.1+dfsg-1ubuntu2.6), uno-libs-private:amd64 (1:7.3.7-0ubuntu0.22.04.1, 1:7.3.7-0ubuntu0.22.04.2), libreoffice-base-core:amd64 (1:7.3.7-0ubuntu0.22.04.1, 1:7.3.7-0ubuntu0.22.04.2), libreoffice-pdfimport:amd64 (1:7.3.7-0ubuntu0.22.04.1, 1:7.3.7-0ubuntu0.22.04.2), libnvidia-gl-525:amd64 (525.78.01-0ubuntu0.22.04.1, 525.89.02-0ubuntu0.22.04.1), libnvidia-gl-525:i386 (525.78.01-0ubuntu0.22.04.1, 525.89.02-0ubuntu0.22.04.1), libcurl3-gnutls:amd64 (7.81.0-1ubuntu1.8, 7.81.0-1ubuntu1.10), linux-headers-generic:amd64 (5.15.0.67.65, 5.15.0.69.67), libnvidia-extra-525:amd64 (525.78.01-0ubuntu0.22.04.1, 525.89.02-0ubuntu0.22.04.1), libreoffice-core:amd64 (1:7.3.7-0ubuntu0.22.04.1, 1:7.3.7-0ubuntu0.22.04.2), libsnmp40:amd64 (5.9.1+dfsg-1ubuntu2.4, 5.9.1+dfsg-1ubuntu2.6), libqmi-proxy:amd64 (1.30.4-1, 1.32.0-1ubuntu0.22.04.1), nvidia-compute-utils-525:amd64 (525.78.01-0ubuntu0.22.04.1, 525.89.02-0ubuntu0.22.04.1), printer-driver-foo2zjs-common:amd64 (20200505dfsg0-2ubuntu2, 20200505dfsg0-2ubuntu2.22.04.1), modemmanager:amd64 (1.18.6-1, 1.20.0-1~ubuntu22.04.1), nvidia-driver-525:amd64 (525.78.01-0ubuntu0.22.04.1, 525.89.02-0ubuntu0.22.04.1), chromium-codecs-ffmpeg-extra:amd64 (1:85.0.4183.83-0ubuntu2, 1:85.0.4183.83-0ubuntu2.22.04.1), libldb2:amd64 (2:2.4.4-0ubuntu0.1, 2:2.4.4-0ubuntu0.22.04.1), libpango-1.0-0:amd64 (1.50.6+ds-2, 1.50.6+ds-2ubuntu1), libldap-common:amd64 (2.5.13+dfsg-0ubuntu0.22.04.1, 2.5.14+dfsg-0ubuntu0.22.04.1), xserver-xorg-core:amd64 (2:21.1.3-2ubuntu2.7, 2:21.1.3-2ubuntu2.8), libmbim-glib4:amd64 (1.26.2-1build1, 1.28.0-1~ubuntu20.04.1), printer-driver-splix:amd64 (2.0.0+svn315-7fakesync1build3, 2.0.0+svn315-7fakesync1ubuntu0.22.04.1), nmap-common:amd64 (7.91+dfsg1+really7.80+dfsg1-2build1, 7.91+dfsg1+really7.80+dfsg1-2ubuntu0.1), libreoffice-common:amd64 (1:7.3.7-0ubuntu0.22.04.1, 1:7.3.7-0ubuntu0.22.04.2), libnvidia-encode-525:amd64 (525.78.01-0ubuntu0.22.04.1, 525.89.02-0ubuntu0.22.04.1), libnvidia-encode-525:i386 (525.78.01-0ubuntu0.22.04.1, 525.89.02-0ubuntu0.22.04.1), ure:amd64 (1:7.3.7-0ubuntu0.22.04.1, 1:7.3.7-0ubuntu0.22.04.2), vim:amd64 (2:8.2.3995-1ubuntu2.3, 2:8.2.3995-1ubuntu2.4), libsasl2-modules:amd64 (2.1.27+dfsg2-3ubuntu1.1, 2.1.27+dfsg2-3ubuntu1.2), libsasl2-2:amd64 (2.1.27+dfsg2-3ubuntu1.1, 2.1.27+dfsg2-3ubuntu1.2), imagemagick:amd64 (8:6.9.11.60+dfsg-1.3ubuntu0.22.04.1, 8:6.9.11.60+dfsg-1.3ubuntu0.22.04.2), xxd:amd64 (2:8.2.3995-1ubuntu2.3, 2:8.2.3995-1ubuntu2.4), nvidia-utils-525:amd64 (525.78.01-0ubuntu0.22.04.1, 525.89.02-0ubuntu0.22.04.1), libpython3.10-minimal:amd64 (3.10.6-1~22.04.2, 3.10.6-1~22.04.2ubuntu1), apparmor:amd64 (3.0.4-2ubuntu2.1, 3.0.4-2ubuntu2.2), xserver-xorg-video-nvidia-525:amd64 (525.78.01-0ubuntu0.22.04.1, 525.89.02-0ubuntu0.22.04.1), libpython3.10-stdlib:amd64 (3.10.6-1~22.04.2, 3.10.6-1~22.04.2ubuntu1), vim-common:amd64 (2:8.2.3995-1ubuntu2.3, 2:8.2.3995-1ubuntu2.4), libreoffice-draw:amd64 (1:7.3.7-0ubuntu0.22.04.1, 1:7.3.7-0ubuntu0.22.04.2), software-properties-common:amd64 (0.99.22.5, 0.99.22.6), libevdocument3-4:amd64 (42.3-0ubuntu2, 42.3-0ubuntu3), libapparmor1:amd64 (3.0.4-2ubuntu2.1, 3.0.4-2ubuntu2.2), libapparmor1:i386 (3.0.4-2ubuntu2.1, 3.0.4-2ubuntu2.2), libuno-purpenvhelpergcc3-3:amd64 (1:7.3.7-0ubuntu0.22.04.1, 1:7.3.7-0ubuntu0.22.04.2), libsasl2-modules-db:amd64 (2.1.27+dfsg2-3ubuntu1.1, 2.1.27+dfsg2-3ubuntu1.2), libuno-cppu3:amd64 (1:7.3.7-0ubuntu0.22.04.1, 1:7.3.7-0ubuntu0.22.04.2), python3-software-properties:amd64 (0.99.22.5, 0.99.22.6), libreoffice-impress:amd64 (1:7.3.7-0ubuntu0.22.04.1, 1:7.3.7-0ubuntu0.22.04.2), libreoffice-style-tango:amd64 (1:7.3.7-0ubuntu0.22.04.1, 1:7.3.7-0ubuntu0.22.04.2), libuno-cppuhelpergcc3-3:amd64 (1:7.3.7-0ubuntu0.22.04.1, 1:7.3.7-0ubuntu0.22.04.2), libmagick++-6.q16-8:amd64 (8:6.9.11.60+dfsg-1.3ubuntu0.22.04.1, 8:6.9.11.60+dfsg-1.3ubuntu0.22.04.2), fonts-opensymbol:amd64 (2:102.12+LibO7.3.7-0ubuntu0.22.04.1, 2:102.12+LibO7.3.7-0ubuntu0.22.04.2), libldap-2.5-0:amd64 (2.5.13+dfsg-0ubuntu0.22.04.1, 2.5.14+dfsg-0ubuntu0.22.04.1), libnvidia-decode-525:amd64 (525.78.01-0ubuntu0.22.04.1, 525.89.02-0ubuntu0.22.04.1), libnvidia-decode-525:i386 (525.78.01-0ubuntu0.22.04.1, 525.89.02-0ubuntu0.22.04.1), linux-generic:amd64 (5.15.0.67.65, 5.15.0.69.67), libevview3-3:amd64 (42.3-0ubuntu2, 42.3-0ubuntu3), isc-dhcp-common:amd64 (4.4.1-2.3ubuntu2.3, 4.4.1-2.3ubuntu2.4), python3-macaroonbakery:amd64 (1.3.1-2, 1.3.1-2ubuntu0.1), libmagickcore-6.q16-6-extra:amd64 (8:6.9.11.60+dfsg-1.3ubuntu0.22.04.1, 8:6.9.11.60+dfsg-1.3ubuntu0.22.04.2), xserver-xorg-legacy:amd64 (2:21.1.3-2ubuntu2.7, 2:21.1.3-2ubuntu2.8), evince-common:amd64 (42.3-0ubuntu2, 42.3-0ubuntu3), printer-driver-foo2zjs:amd64 (20200505dfsg0-2ubuntu2, 20200505dfsg0-2ubuntu2.22.04.1), nvidia-kernel-common-525:amd64 (525.78.01-0ubuntu0.22.04.1, 525.89.02-0ubuntu0.22.04.1), libreoffice-style-colibre:amd64 (1:7.3.7-0ubuntu0.22.04.1, 1:7.3.7-0ubuntu0.22.04.2), libpangocairo-1.0-0:amd64 (1.50.6+ds-2, 1.50.6+ds-2ubuntu1), libpython3.10:amd64 (3.10.6-1~22.04.2, 3.10.6-1~22.04.2ubuntu1), libreoffice-writer:amd64 (1:7.3.7-0ubuntu0.22.04.1, 1:7.3.7-0ubuntu0.22.04.2), update-notifier:amd64 (3.192.54.5, 3.192.54.6), xserver-common:amd64 (2:21.1.3-2ubuntu2.7, 2:21.1.3-2ubuntu2.8), libreoffice-avmedia-backend-gstreamer:amd64 (1:7.3.7-0ubuntu0.22.04.1, 1:7.3.7-0ubuntu0.22.04.2), libimage-magick-q16-perl:amd64 (8:6.9.11.60+dfsg-1.3ubuntu0.22.04.1, 8:6.9.11.60+dfsg-1.3ubuntu0.22.04.2), isc-dhcp-client:amd64 (4.4.1-2.3ubuntu2.3, 4.4.1-2.3ubuntu2.4), libuno-salhelpergcc3-3:amd64 (1:7.3.7-0ubuntu0.22.04.1, 1:7.3.7-0ubuntu0.22.04.2), libmagickwand-6.q16-6:amd64 (8:6.9.11.60+dfsg-1.3ubuntu0.22.04.1, 8:6.9.11.60+dfsg-1.3ubuntu0.22.04.2), libreoffice-style-breeze:amd64 (1:7.3.7-0ubuntu0.22.04.1, 1:7.3.7-0ubuntu0.22.04.2), vim-tiny:amd64 (2:8.2.3995-1ubuntu2.3, 2:8.2.3995-1ubuntu2.4), libmbim-proxy:amd64 (1.26.2-1build1, 1.28.0-1~ubuntu20.04.1), libpangoft2-1.0-0:amd64 (1.50.6+ds-2, 1.50.6+ds-2ubuntu1), software-properties-gtk:amd64 (0.99.22.5, 0.99.22.6), systemd-hwe-hwdb:amd64 (249.11.2, 249.11.3), imagemagick-6.q16:amd64 (8:6.9.11.60+dfsg-1.3ubuntu0.22.04.1, 8:6.9.11.60+dfsg-1.3ubuntu0.22.04.2), linux-image-generic:amd64 (5.15.0.67.65, 5.15.0.69.67), libpython3.10-dev:amd64 (3.10.6-1~22.04.2, 3.10.6-1~22.04.2ubuntu1), linux-firmware:amd64 (20220329.git681281e4-0ubuntu3.10, 20220329.git681281e4-0ubuntu3.11), python3-ldb:amd64 (2:2.4.4-0ubuntu0.1, 2:2.4.4-0ubuntu0.22.04.1), vim-runtime:amd64 (2:8.2.3995-1ubuntu2.3, 2:8.2.3995-1ubuntu2.4), libmagickcore-6.q16-6:amd64 (8:6.9.11.60+dfsg-1.3ubuntu0.22.04.1, 8:6.9.11.60+dfsg-1.3ubuntu0.22.04.2), libqmi-glib5:amd64 (1.30.4-1, 1.32.0-1ubuntu0.22.04.1), libreoffice-help-common:amd64 (1:7.3.7-0ubuntu0.22.04.1, 1:7.3.7-0ubuntu0.22.04.2), python3-protobuf:amd64 (3.12.4-1ubuntu7, 3.12.4-1ubuntu7.22.04.1), gir1.2-pango-1.0:amd64 (1.50.6+ds-2, 1.50.6+ds-2ubuntu1), python3-uno:amd64 (1:7.3.7-0ubuntu0.22.04.1, 1:7.3.7-0ubuntu0.22.04.2), python3.10-dev:amd64 (3.10.6-1~22.04.2, 3.10.6-1~22.04.2ubuntu1), libuno-sal3:amd64 (1:7.3.7-0ubuntu0.22.04.1, 1:7.3.7-0ubuntu0.22.04.2), libreoffice-ogltrans:amd64 (1:7.3.7-0ubuntu0.22.04.1, 1:7.3.7-0ubuntu0.22.04.2), xserver-xephyr:amd64 (2:21.1.3-2ubuntu2.7, 2:21.1.3-2ubuntu2.8), libreoffice-style-galaxy:amd64 (1:7.3.7-0ubuntu0.22.04.1, 1:7.3.7-0ubuntu0.22.04.2), brave-browser:amd64 (1.48.171, 1.49.128), libgraphicsmagick-q16-3:amd64 (1.4+really1.3.38-1, 1.4+really1.3.38-1ubuntu0.1), netplan.io:amd64 (0.105-0ubuntu2~22.04.1, 0.105-0ubuntu2~22.04.3), imagemagick-6-common:amd64 (8:6.9.11.60+dfsg-1.3ubuntu0.22.04.1, 8:6.9.11.60+dfsg-1.3ubuntu0.22.04.2), nmap:amd64 (7.91+dfsg1+really7.80+dfsg1-2build1, 7.91+dfsg1+really7.80+dfsg1-2ubuntu0.1), libreoffice-style-yaru:amd64 (1:7.3.7-0ubuntu0.22.04.1, 1:7.3.7-0ubuntu0.22.04.2), libnvidia-cfg1-525:amd64 (525.78.01-0ubuntu0.22.04.1, 525.89.02-0ubuntu0.22.04.1), linux-modules-nvidia-525-generic:amd64 (5.15.0-60.66, 5.15.0-69.76), libprotobuf23:amd64 (3.12.4-1ubuntu7, 3.12.4-1ubuntu7.22.04.1), nvidia-kernel-source-525:amd64 (525.78.01-0ubuntu0.22.04.1, 525.89.02-0ubuntu0.22.04.1), curl:amd64 (7.81.0-1ubuntu1.8, 7.81.0-1ubuntu1.10), thermald:amd64 (2.4.9-1ubuntu0.1, 2.4.9-1ubuntu0.2), libreoffice-math:amd64 (1:7.3.7-0ubuntu0.22.04.1, 1:7.3.7-0ubuntu0.22.04.2), libpangoxft-1.0-0:amd64 (1.50.6+ds-2, 1.50.6+ds-2ubuntu1), libnvidia-compute-525:amd64 (525.78.01-0ubuntu0.22.04.1, 525.89.02-0ubuntu0.22.04.1), libnvidia-compute-525:i386 (525.78.01-0ubuntu0.22.04.1, 525.89.02-0ubuntu0.22.04.1), libreoffice-gtk3:amd64 (1:7.3.7-0ubuntu0.22.04.1, 1:7.3.7-0ubuntu0.22.04.2), python3.10-minimal:amd64 (3.10.6-1~22.04.2, 3.10.6-1~22.04.2ubuntu1), ubuntu-advantage-tools:amd64 (27.13.5~22.04.1, 27.13.6~22.04.1), libreoffice-help-en-us:amd64 (1:7.3.7-0ubuntu0.22.04.1, 1:7.3.7-0ubuntu0.22.04.2), libreoffice-style-elementary:amd64 (1:7.3.7-0ubuntu0.22.04.1, 1:7.3.7-0ubuntu0.22.04.2), libnetplan0:amd64 (0.105-0ubuntu2~22.04.1, 0.105-0ubuntu2~22.04.3), update-notifier-common:amd64 (3.192.54.5, 3.192.54.6), signal-desktop:amd64 (6.7.0, 6.11.0), linux-libc-dev:amd64 (5.15.0-67.74, 5.15.0-69.76)
Remove: linux-modules-nvidia-525-5.15.0-60-generic:amd64 (5.15.0-60.66)
Error: Sub-process /usr/bin/dpkg returned an error code (1)
End-Date: 2023-03-28  23:57:51


---

### Post by Tulf on 2023-04-30
The nvidia driver seems to be involved with the issue and I can't switch to 530, in fact the system is back to using the generic xorg driver which is strange and frustrating as I've never had this issue before. I've been using the dedicated nvidia drivers since I've built this system.

---

### Post by #&amp;thj^% on 2023-04-30
> **Tulf said:**
> The nvidia driver seems to be involved with the issue and I can't switch to 530, in fact the system is back to using the generic xorg driver which is strange and frustrating as I've never had this issue before. I've been using the dedicated nvidia drivers since I've built this system.

What happens if you purge the driver and reboot before trying the install again.
Suggest:
```
sudo apt remove --purge nvidia*
```
Back-ups are a good thing to have in place *now*

---

### Post by Tulf on 2023-07-11
Purge doesn't work at all. For anything. Even holding the problematic packages doesn't work. I'm really stumped with how this happened or why. It's more of a personal curiosity at this point since it will be easier to simply do a clean install.

---

