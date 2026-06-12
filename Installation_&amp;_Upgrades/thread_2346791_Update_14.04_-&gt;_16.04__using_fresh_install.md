---
title: "Update 14.04 -&gt; 16.04  using fresh install"
date: 2016-12-18
forum: Installation &amp; Upgrades
---

### Post by cscj01 on 2016-12-18
I tried to upgrade to 16.04 using the upgrade process, but my system got hosed.  Fortunately, I had a backup and restored it with no problems.  Now I am considering doing a fresh install.  My issue is, I do not have a separate ~/ partition.  I am wondering if I should backup ~/, do the fresh install over my existing system, and then restore my ~/ over the new one or should I merge it or should I selectively replace certain files/directories, etc.  Any guidance here?

This got duplicated when the Forums went down just as I was posting.  Perhaps a moderator could remove one of these.

---

### Post by oldfred on 2016-12-18
You can use report post for any issue, its not just for spam.

Jailed other post.

I always use a separate25GB / (root) partition, but have data in other partitions as I like to install and test changes in newer versions, but keep LTS as main working install.

---

### Post by ian-weisser on 2016-12-18
If you want to stick to a fresh install, I recommend a full backup, and then selective restore file-by-file. It's a good opportunity to houseclean. It's amazing what you discover that you don't use anymore.

Best guidance depends on your comfort level and skills.

Some gurus in this forum swear by fresh-installs, others swear by upgrades. Both are extensively tested and work very well.
FYI: Most upgrade failures can be easily prevented or fixed.

---

### Post by cscj01 on 2016-12-18
> **ian-weisser said:**
> If you want to stick to a fresh install, I recommend a full backup, and then selective restore file-by-file. It's a good opportunity to houseclean. It's amazing what you discover that you don't use anymore.

Best guidance depends on your comfort level and skills.

Some gurus in this forum swear by fresh-installs, others swear by upgrades. Both are extensively tested and work very well.
FYI: Most upgrade failures can be easily prevented or fixed.

I had so many errors that I couldn't boot.  So I had to restore my backup.  I have always done upgrades before with only minor issues.  This time was a show stopper.  I do use some PPA's, so I'm not sure if that caused any issues.  I also have some programs that are not distributed any way except from the developer, i.e., Vuescan and Moneydance.  I believe Moneydance is distributed as a .deb, but Vuescan is just a folder with some files.  I use Vuescan to scan film strips and photos.  The PPAs could be removed prior to upgrade, but I think the Upgrade process is supposed to disable those anyway.  I'm not really into a fresh install, but I had such a bad experience with the Upgrade attempt that I just don't want to deal with the hassle.  If I knew it had been improved since my disaster (early this year, Spring I believe), I might give it another try.

---

### Post by cscj01 on 2017-01-04
After making sure my system was as vanilla as possible (PPAs removed, any things I had changed as relates to config files, etc,), I once again tried to upgrade from 14.04 to 16.04 (x64).  I made sure I had the latest updates prior to beginning the update process.  Things ended as before with the system in an unusable state (the message was something like that).  I could not boot and had to restore my backup.  Since I depend on Darktable, and they no longer support 14.04, I have to upgrade to get release 2.2.  So, I seem to be left with no options except to move to another platform or do a fresh install.  As I have always done upgrades before (even when everything didn't go smoothly, I could always boot and take care of the issues), is there anyone who can give me some guidance on the steps to accomplish this?  I know I would need to backup /home, but what about config files I may have changed?  How should these be handled?  Are there other things I should be checking that I don't know about, etc.?  Any help would be very much appreciated.

System went unavailable while I was posting, and I ending up with two posts instead of one.  Would a moderator remove one of these please?  Thank you.

---

### Post by ian-weisser on 2017-01-04
If you show us the log of the failed upgrade (in /var/log), or show us the exact error messages and exactly the steps you took to cause the error messages, then we can probably offer you some good help diagnosing and fixing the problem(s).

However, we cannot see what you see. We are not psychic. All we know is that your system has lots of (vague) problems, and that apparently upgrading left your system unbootable in some way. Any advice we offer is pure blind speculation.

Simple question: A complete backup-reinstall-restore-and-customize takes perhaps one afternoon. How much time are you willing to invest to repair your current broken system? Do you want this to be a learning opportunity, or you you simply want to get working again as fast as possible?

---

### Post by cscj01 on 2017-01-04
Well, I use Clonezilla to create a copy of my Ubuntu partition.  Since I had to restore the backed up partition, there won't be anything in /var/log about the install, will there?  Since the system is unusable and will not boot, I suppose I could use a Live CD/DVD to boot into after the install fails but before I restore my backup to see if I could pull anything from /var/log.  Will that be available on the system partition if I try that?  If not, how can I get the contents of the log without being able to boot my system?

---

### Post by cscj01 on 2017-01-06
Bump

---

### Post by ian-weisser on 2017-01-06
> **cscj01 said:**
> Since the system is unusable and will not boot, I suppose I could use a Live CD/DVD to boot into after the install fails but before I restore my backup to see if I could pull anything from /var/log.  Will that be available on the system partition if I try that?

Yes, that's the step to try for troubleshooting.

---

### Post by cscj01 on 2017-01-08
Okay, I tried it again, except this time, I ran ```
sudo apt-get autoremove
sudo apt-get update
sudo do-release-upgrade
```I did this after disabling all my PPA's.  The reason I did not use Software Upgrader is I wanted to see what was happening in real time.  I can say the following situation occurred many times.

While preparing to install/upgrade some package, I received a message saying the package depended on some other software, but the other software was going to be removed because I had said to remove it.  From my perspective, how do you tell the do-release-upgrade script to not remove certain software?  My assumption is the script should be smart enough to not remove packages that are needed to do the upgrade.  Maybe I am being naive, but how in the world can I rectify this?  Should I run```
ppa-purge
```for all PPA's I have in addition to disabling them?  I am at a loss here.

---

### Post by ian-weisser on 2017-01-08
Using PPA-Purge is a correct move.
It's not enough to merely disable PPA sources. You must uninstall all the PPA-provided software.
Those non-Ubuntu packages sometimes cause version conflicts that look very similar to what you describe.

You cannot tell do-release-upgrade to both 'make a sandwich' and 'do not use bread'. It's impossible, and do-release-upgrade will tell you so init's own cryptic fashion when it starts to cry about the impossibility.
When do-release-upgrade gives you such package warnings ('Foo 1.3 cannot be installed!'), it's trying to tell you that packages you *already installed* (like Foo 1.32 from a PPA) has already created a similar impossible situation.

---

### Post by cscj01 on 2017-01-09
Okay, I used ppa-purge to regress every PPA I had back to the current release of the product on 14.04.  I tried to upgrade.  Same problem.  The Upgrade is not successful due to too many dependency issues. It seems as if I am stuck on 14.04 forever.  What is the problem here?  Is there any hope at all that this can be salvaged?

---

### Post by ian-weisser on 2017-01-09
Non-Ubuntu software is the most frequent cause for symptoms you describe, but not the only cause.
We must see your upgrade logs to progress.

---

### Post by cscj01 on 2017-01-09
Well, I can't get a live DVD that will boot.  First I burned a DVD+R.  That had a bad sector.  Then I burned a DVD+RW.  The DVD is read for a while, a message comes up asking what I want to do.  I choose **Run Ubuntu Without Installing**.  After some additional loading from the DVD, another message appears in the upper left hand corner of the screen that this is **Ubuntu 16.04** followed by a **Login:** prompt.  That goes away, and the DVD begins to "surge" (a sound like blowing wind) for a second or two, and that pattern repeats at intervals of about 30 seconds.  The system never comes up.

I then burned a DVD-RW.  Same result as the DCD+RW.  The file I have was downloaded from the Ubuntu web site, and the file is **ubuntu-16.04.1-desktop-amd64.iso**.  I do not know why this is happening.  I have never had any problems with live CD's or DVD's.  This is insane.  I have an Intel I5-3570K CPU with 32 GB of memory on a Gigabyte Z77X-UD5H Mobo.  I have a GeForce GTX 750 TI graphics card.  I have had no problems with 14.04.5 which I am currently running.  My equipment should be supported by Ubuntu.  What in the world is happening here?

---

### Post by ian-weisser on 2017-01-09
Been there.
The only time I ever have problems with USB sticks or DVDs or other media is the time I *need* them to work.

Have a good laugh about it.
Take a break.
Then back to one step at a time.

---

### Post by efflandt on 2017-01-09
Note that if you use Startup Disk Creator in 14.04 on a BIOS system (not UEFI) to create bootable 16.04 live/install USB, you may get an error during boot due to 14.04 using an older syslinux version. So if using BIOS see [http://askubuntu.com/questions/486602/ubuntu-14-04-lts-live-usb-boot-error-gfxboot-c32not-a-valid-com32r-image](http://askubuntu.com/questions/486602/ubuntu-14-04-lts-live-usb-boot-error-gfxboot-c32not-a-valid-com32r-image) which tells how to get in and fix it on that USB flash device.

---

### Post by cscj01 on 2017-01-09
Okay, I have something installed.  My system says it is 16.04.1 running kernel 3.13.0-105.  I'm not sure that's right because I have a boat full of dependency errors.  I have screenlog.0 from /var/log/dist-upgrades which shows all the problems incurred.  It is a large file. It is 7.5 MB.  I cannot attach a file that large.  What now?

---

### Post by cscj01 on 2017-01-09
BTW, I ran a couple of commands.  Here are the results:```
sudo apt -f install
[sudo] password for butch: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... failed.
The following packages have unmet dependencies:
 blender : Depends: blender-data (= 2.69-4ubuntu2) but 2.76.b+dfsg0-3build1 is installed
 bogofilter-bdb : Depends: libgsl0ldbl (>= 1.9) but it is not installable
 digikam : Depends: libopencv-core2.4 but it is not installable
 enblend : Depends: libgsl0ldbl (>= 1.9) but it is not installable
 enfuse : Depends: libgsl0ldbl (>= 1.9) but it is not installable
 freerdp-x11 : Depends: libfreerdp1 (>= 1.0.1) but it is not installable
 frei0r-plugins : Depends: libopencv-core2.4 but it is not installable
                  Depends: libopencv-imgproc2.4 but it is not installable
                  Depends: libopencv-objdetect2.4 but it is not installable
 gdm : Depends: libgdm1 (= 3.10.0.1-0ubuntu3.2) but 3.18.3-0ubuntu2 is installed
       Depends: gir1.2-gdm-1.0 (= 3.10.0.1-0ubuntu3.2) but 3.18.3-0ubuntu2 is installed
 gir1.2-cogl-1.0 : Depends: libcogl15 (>= 1.15.8) but it is not installable
 gir1.2-freedesktop : Depends: gir1.2-glib-2.0 (= 1.40.0-1ubuntu0.2) but 1.46.0-3ubuntu1 is installed
 gnome-bluetooth : Depends: gir1.2-gnomebluetooth-1.0 (= 3.8.2.1-0ubuntu4.2) but 3.18.2-1ubuntu2 is installed
                   Depends: obexd-client but it is not installable
 gnome-commander : Depends: libtag1c2a (>= 1.5) but it is not installable
 gparted : Depends: libatkmm-1.6-1v5 (>= 2.24.0) but it is not installed
           Depends: libglibmm-2.4-1v5 (>= 2.46.0) but it is not installed
           Depends: libgtkmm-2.4-1v5 (>= 1:2.24.0) but it is not installed
           Depends: libpangomm-1.4-1v5 (>= 2.38.0) but it is not installed
           Depends: libsigc++-2.0-0v5 (>= 2.6.1) but it is not installed
 gstreamer0.10-plugins-good : Depends: libtag1c2a (>= 1.5) but it is not installable
 gstreamer1.0-clutter : Depends: libcogl15 (>= 1.15.8) but it is not installable
 gvfs : Depends: gvfs-libs (= 1.20.3-0ubuntu1.2) but 1.28.2-1ubuntu1~16.04.1 is installed
 gvfs:i386 : Depends: gvfs-libs:i386 (= 1.20.3-0ubuntu1.2) but 1.28.2-1ubuntu1~16.04.1 is installed
 gvfs-backends : Depends: gvfs-libs (= 1.20.3-0ubuntu1.2) but 1.28.2-1ubuntu1~16.04.1 is installed
 gvfs-daemons : Depends: gvfs-libs (= 1.20.3-0ubuntu1.2) but 1.28.2-1ubuntu1~16.04.1 is installed
 gvfs-libs : Depends: gvfs-common (= 1.28.2-1ubuntu1~16.04.1) but 1.20.3-0ubuntu1.2 is installed
 gvfs-libs:i386 : Depends: gvfs-common:i386 (= 1.28.2-1ubuntu1~16.04.1)
 indicator-datetime : Depends: libical1 (>= 1.0) but it is not installable
 inkscape : Depends: libgsl0ldbl (>= 1.9) but it is not installable
 kid3-core : Depends: libtag1c2a (>= 1.9.1) but it is not installable
 libalgorithm-diff-xs-perl : Depends: perlapi-5.18.1 but it is not installable
 libapparmor-perl : Depends: perlapi-5.18.2 but it is not installable
 libapt-pkg-perl : Depends: perlapi-5.18.1 but it is not installable
 libarchive12 : Depends: libnettle4 (>= 2.3) but it is not installable
 libarchive13 : Depends: libnettle4 (>= 2.3) but it is not installable
 libasync-interrupt-perl : Depends: perlapi-5.18.1 but it is not installable
 libbit-vector-perl : Depends: perlapi-5.18.1 but it is not installable
 libcairo-perl : Depends: perlapi-5.18.1 but it is not installable
 libclone-perl : Depends: perlapi-5.18.1 but it is not installable
 libclutter-gst-2.0-0 : Depends: libcogl15 (>= 1.15.8) but it is not installable
 libcogl-pango15 : Depends: libcogl15 (>= 1.15.8) but it is not installable
 libcommon-sense-perl : Depends: perl (< 5.18.3~) but 5.22.1-9 is installed
 libcompress-raw-lzma-perl : Depends: perlapi-5.18.1 but it is not installable
 libcups2-dev : Depends: libcups2 (= 1.7.2-0ubuntu1.7) but 2.1.3-4 is installed
 libcupscgi1 : Depends: libcups2 (= 1.7.2-0ubuntu1.7) but 2.1.3-4 is installed
 libcupsimage2 : Depends: libcups2 (= 1.7.2-0ubuntu1.7) but 2.1.3-4 is installed
 libcupsimage2:i386 : Depends: libcups2:i386 (= 1.7.2-0ubuntu1.7) but 2.1.3-4 is installed
 libcupsmime1 : Depends: libcups2 (= 1.7.2-0ubuntu1.7) but 2.1.3-4 is installed
 libcupsppdc1 : Depends: libcups2 (= 1.7.2-0ubuntu1.7) but 2.1.3-4 is installed
 libdate-calc-xs-perl : Depends: perlapi-5.18.1 but it is not installable
 libdatetime-perl : Depends: perlapi-5.18.1 but it is not installable
 libdbd-mysql-perl : Depends: perlapi-5.18.2 but it is not installable
 libdbi-perl : Depends: perlapi-5.18.1 but it is not installable
 libdevice-serialport-perl : Depends: perlapi-5.18.1 but it is not installable
 libecal-1.2-16 : Depends: libical1 (>= 1.0) but it is not installable
 libedata-cal-1.2-23 : Depends: libical1 (>= 1.0) but it is not installable
 libevent-perl : Depends: perlapi-5.18.1 but it is not installable
 libfile-fcntllock-perl : Depends: perlapi-5.18.1 but it is not installable
 libfontconfig1 : Depends: fontconfig-config (= 2.11.94-0ubuntu1.1) but 2.11.0-0ubuntu4.2 is installed
 libfontconfig1:i386 : Depends: fontconfig-config:i386 (= 2.11.94-0ubuntu1.1)
 libfreerdp-core1.1 : Depends: libfreerdp-codec1.1 (>= 1.1.0~beta1+git20130629) but it is not installed
                      Depends: libwinpr-sysinfo0.1 (>= 1.1.0~beta1+git20130629) but it is not installed
 libfreerdp-gdi1.1 : Depends: libfreerdp-codec1.1 (>= 1.1.0~beta1+git20130629) but it is not installed
 libfreerdp-plugins-standard : Depends: libwinpr-sysinfo0.1 (>= 1.1.0~beta1+git20130629) but it is not installed
 libgail-3-0 : Depends: libgtk-3-0 (= 3.10.8-0ubuntu1.6) but 3.18.9-1ubuntu3.1 is installed
 libglib-perl : Depends: perlapi-5.18.1 but it is not installable
 libglib2.0-bin : Depends: libglib2.0-0 (= 2.40.2-0ubuntu1) but 2.48.1-1~ubuntu16.04.1 is installed
 libglib2.0-dev : Depends: libglib2.0-0 (= 2.40.2-0ubuntu1) but 2.48.1-1~ubuntu16.04.1 is installed
 libgnome2-canvas-perl : Depends: perlapi-5.18.1 but it is not installable
 libgnome2-perl : Depends: perlapi-5.18.1 but it is not installable
 libgnome2-vfs-perl : Depends: perlapi-5.18.1 but it is not installable
 libgnome2-wnck-perl : Depends: perlapi-5.18.1 but it is not installable
 libgnutls28 : Depends: libhogweed2 (>= 2.7) but it is not installable
               Depends: libnettle4 (>= 2.7) but it is not installable
 libgoo-canvas-perl : Depends: perlapi-5.18.1 but it is not installable
 libgtk-3-0-dbg : Depends: libgtk-3-0 (= 3.10.8-0ubuntu1.6) but 3.18.9-1ubuntu3.1 is installed
 libgtk-3-dev : Depends: libgtk-3-0 (= 3.10.8-0ubuntu1.6) but 3.18.9-1ubuntu3.1 is installed
                Depends: gir1.2-gtk-3.0 (= 3.10.8-0ubuntu1.6) but 3.18.9-1ubuntu3.1 is installed
 libgtk2-appindicator-perl : Depends: perlapi-5.18.1 but it is not installable
 libgtk2-gladexml-perl : Depends: perlapi-5.18.1 but it is not installable
 libgtk2-imageview-perl : Depends: perlapi-5.18.1 but it is not installable
 libgtk2-perl : Depends: perlapi-5.18.2 but it is not installable
 libgtk2-unique-perl : Depends: perlapi-5.18.1 but it is not installable
 libguard-perl : Depends: perlapi-5.18.1 but it is not installable
 libhtml-parser-perl : Depends: perlapi-5.18.1 but it is not installable
 libimage-imlib2-perl : Depends: perlapi-5.18.1 but it is not installable
 libio-pty-perl : Depends: perlapi-5.18.1 but it is not installable
 libjson-xs-perl : Depends: perlapi-5.18.1 but it is not installable
 libk3b6 : Depends: libtag1c2a (>= 1.5) but it is not installable
 libkface2 : Depends: libopencv-contrib2.4 but it is not installable
             Depends: libopencv-core2.4 but it is not installable
             Depends: libopencv-imgproc2.4 but it is not installable
             Depends: libopencv-objdetect2.4 but it is not installable
 libkfilemetadata4 : Depends: libtag1c2a (>= 1.5) but it is not installable
 liblist-moreutils-perl : Depends: perlapi-5.18.1 but it is not installable
 liblocale-gettext-perl : PreDepends: perlapi-5.18.1 but it is not installable
 libmusicbrainz-discid-perl : Depends: perlapi-5.18.1 but it is not installable
 libnet-dbus-perl : Depends: perlapi-5.18.1 but it is not installable
 libnet-dns-perl : Depends: perlapi-5.18.1 but it is not installable
 libnet-libidn-perl : Depends: perlapi-5.18.1 but it is not installable
 libnet-ssleay-perl : Depends: perlapi-5.18.2 but it is not installable
 libopencolorio1v5 : Depends: libtinyxml2.6.2v5 but it is not installed
 libopenimageio1.3 : Depends: libopencolorio1 but it is not installable
                     Depends: libopencv-highgui2.4 but it is not installable
 libpackage-stash-xs-perl : Depends: perlapi-5.18.1 but it is not installable
 libpango-perl : Depends: perlapi-5.18.1 but it is not installable
 libparams-classify-perl : Depends: perlapi-5.18.1 but it is not installable
 libparams-util-perl : Depends: perlapi-5.18.1 but it is not installable
 libparams-validate-perl : Depends: perlapi-5.18.1 but it is not installable
 libperl-dev : Depends: perl (= 5.18.2-2ubuntu1.1) but 5.22.1-9 is installed
 libperl5.18 : Depends: perl-base (= 5.18.2-2ubuntu1.1) but 5.22.1-9 is installed
 libperlio-gzip-perl : Depends: perlapi-5.18.1 but it is not installable
 libproc-processtable-perl : Depends: perlapi-5.18.1 but it is not installable
 libpurple0 : Depends: perlapi-5.18.2 but it is not installable
 libreoffice : Depends: libreoffice-java-common (>= 1:5.1.4~) but 1:4.2.8-0ubuntu4 is installed
 libreoffice-base : Depends: libreoffice-base-drivers (= 1:5.1.4-0ubuntu1) but 1:4.2.8-0ubuntu4 is installed
                    Recommends: libreoffice-java-common (>= 1:5.1.4~) but 1:4.2.8-0ubuntu4 is installed
 libreoffice-calc : Depends: libetonyek-0.1-1 but it is not installed
                    Depends: libmwaw-0.3-3 but it is not installed
                    Depends: libodfgen-0.1-1 but it is not installed
                    Depends: liborcus-0.10-0v5 (>= 0.9.2-4ubuntu2) but it is not installed
                    Depends: librevenge-0.0-0 but it is not installed
                    Depends: libwps-0.4-4 but it is not installed
 libreoffice-core : Depends: libclucene-contribs1v5 (>= 2.3.3.4) but it is not installed
                    Depends: libclucene-core1v5 (>= 2.3.3.4) but it is not installed
                    Depends: libcmis-0.5-5v5 but it is not installed
                    Depends: libeot0 but it is not installed
                    Depends: librevenge-0.0-0 but it is not installed
 libreoffice-draw : Depends: libcdr-0.1-1 but it is not installed
                    Depends: libfreehand-0.1-1 but it is not installed
                    Depends: libmspub-0.1-1 but it is not installed
                    Depends: libmwaw-0.3-3 but it is not installed
                    Depends: libodfgen-0.1-1 but it is not installed
                    Depends: libpagemaker-0.0-0 (>= 0.0) but it is not installed
                    Depends: librevenge-0.0-0 but it is not installed
                    Depends: libvisio-0.1-1 but it is not installed
                    Depends: libwpg-0.3-3 but it is not installed
 libreoffice-impress : Depends: libetonyek-0.1-1 but it is not installed
                       Depends: libmwaw-0.3-3 but it is not installed
                       Depends: libodfgen-0.1-1 but it is not installed
                       Depends: librevenge-0.0-0 but it is not installed
 libreoffice-writer : Depends: libabw-0.1-1v5 but it is not installed
                      Depends: libe-book-0.1-1 but it is not installed
                      Depends: libetonyek-0.1-1 but it is not installed
                      Depends: libmwaw-0.3-3 but it is not installed
                      Depends: libodfgen-0.1-1 but it is not installed
                      Depends: librevenge-0.0-0 but it is not installed
                      Depends: libwpd-0.10-10 but it is not installed
                      Depends: libwpg-0.3-3 but it is not installed
                      Depends: libwps-0.4-4 but it is not installed
 libsocket6-perl : Depends: perlapi-5.18.2 but it is not installable
 libsub-identify-perl : Depends: perlapi-5.18.1 but it is not installable
 libsub-name-perl : Depends: perlapi-5.18.1 but it is not installable
 libterm-readkey-perl : Depends: perlapi-5.18.1 but it is not installable
 libterm-readline-gnu-perl : Depends: perlapi-5.18.1 but it is not installable
 libtext-charwidth-perl : Depends: perlapi-5.18.1 but it is not installable
 libtext-csv-xs-perl : Depends: perlapi-5.18.1 but it is not installable
 libtext-iconv-perl : Depends: perlapi-5.18.1 but it is not installable
 libtext-soundex-perl : Depends: perlapi-5.18.1 but it is not installable
 libtotem0 : Depends: libcogl15 (>= 1.15.8) but it is not installable
 libuuid-perl : Depends: perlapi-5.18.1 but it is not installable
 libwinpr-sspi0.1 : Depends: libwinpr-sysinfo0.1 (>= 1.1.0~beta1+git20130629) but it is not installed
 libwinpr-utils0.1 : Depends: libwinpr-sysinfo0.1 (>= 1.1.0~beta1+git20130629) but it is not installed
 libxml-libxml-perl : Depends: perlapi-5.18.2 but it is not installable
 libxml-parser-perl : Depends: perlapi-5.18.1 but it is not installable
 mysql-workbench : Depends: libctemplate2 but it is not installable
                   Depends: libmysqlcppconn7 (>= 1.1.3) but it is not installable
                   Depends: libpcrecpp0 (>= 7.7) but it is not installable
 perlmagick : Depends: perlapi-5.18.2 but it is not installable
 pidgin : Depends: perlapi-5.18.2 but it is not installable
 python-gi-cairo : Depends: python-gi (= 3.12.0-1ubuntu1) but 3.20.0-0ubuntu1 is installed
 remmina-plugin-rdp : Depends: libfreerdp1 (>= 1.0~beta5) but it is not installable
 rhythmbox : Depends: python3 (< 3.5) but 3.5.1-3 is installed
             Depends: gir1.2-rb-3.0 (= 3.0.2-0ubuntu2) but 3.3-1ubuntu7 is installed
 rhythmbox-plugin-magnatune : Depends: rhythmbox (= 3.3-1ubuntu7) but 3.0.2-0ubuntu2 is installed
 rhythmbox-plugins : Depends: rhythmbox (= 3.3-1ubuntu7) but 3.0.2-0ubuntu2 is installed
 totem : Depends: libcogl15 (>= 1.15.8) but it is not installable
         Depends: totem-common (= 3.10.1-1ubuntu4) but 3.18.1-1ubuntu4 is installed
 unity-control-center : Depends: libcheese-gtk23 (>= 3.4.0) but it is not installable
                        Depends: libcheese7 (>= 3.0.1) but it is not installable
 unity-settings-daemon : Depends: gnome-settings-daemon-schemas (< 3.10) but 3.18.2-0ubuntu3.1 is installed
 vlc-nox : Depends: libebml4 but it is not installable
           Depends: libfreerdp1 (>= 1.0.1) but it is not installable
           Depends: libmatroska6 but it is not installable
           Depends: libsidplay2 but it is not installable
           Depends: libtag1c2a (>= 1.7) but it is not installable
E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.
E: Unable to correct dependencies

``````
sudo dpkg -C
The following packages have been unpacked but not yet configured.
They must be configured using dpkg --configure or the configure
menu option in dselect for them to work:
 account-plugin-aim   Messaging account plugin for AIM
 account-plugin-jabber Messaging account plugin for Jabber/XMPP
 account-plugin-salut Messaging account plugin for Local XMPP (Salut)
 account-plugin-yahoo Messaging account plugin for Yahoo!
 accountsservice      query and manipulate user account information
 adwaita-icon-theme   default icon theme of GNOME (small subset)
 apparmor             user-space parser utility for AppArmor
 apt-utils            package management related utility programs
 bamfdaemon           Window matching library - daemon
 blender-data         Very fast and versatile 3D modeller/renderer - data packa
 bluez                Bluetooth tools and daemons
 bluez-obexd          bluez obex daemon
 cgmanager            Central cgroup manager daemon
 cheese               tool to take pictures and videos from your webcam
 cli-common           common files between all CLI packages
 console-setup        console font and keymap setup program
 console-setup-linux  Linux specific part of console-setup
 consolekit           framework for defining and tracking users, sessions and s
 cryptsetup           disk encryption support - startup scripts
 cups                 Common UNIX Printing System(tm) - PPD/driver support, web
 cups-bsd             Common UNIX Printing System(tm) - BSD commands
 cups-client          Common UNIX Printing System(tm) - client programs (SysV)
 cups-core-drivers    Common UNIX Printing System(tm) - PPD-less printing
 cups-daemon          Common UNIX Printing System(tm) - daemon
 dbus                 simple interprocess messaging system (daemon and utilitie
 deja-dup             Back up your files
 dh-python            Debian helper tools for packaging Python libraries and ap
 duplicity            encrypted bandwidth-efficient backup
 empathy              GNOME multi-protocol chat and call client
 evolution            groupware suite with mail client and organizer
 evolution-data-server evolution database backend server
 evolution-data-server-online-accounts evolution data server integration with U
 evolution-plugins    standard plugins for Evolution
 fontconfig           generic font configuration library - support binaries
 gir1.2-atk-1.0       ATK accessibility toolkit (GObject introspection)
 gir1.2-clutter-1.0:amd64 GObject introspection data for the Clutter 1.0 library
 gir1.2-gdesktopenums-3.0 GObject introspection for GSettings desktop-wide sche
 gir1.2-gdm-1.0       GObject introspection data for the GNOME Display Manager
 gir1.2-gnomebluetooth-1.0:amd64 Introspection data for GnomeBluetooth
 gir1.2-gnomedesktop-3.0:amd64 Introspection data for GnomeDesktop
 gir1.2-gtk-3.0:amd64 GTK+ graphical user interface library -- gir bindings
 gir1.2-gweather-3.0:amd64 GObject introspection data for the GWeather library
 gir1.2-mutter-3.0    GObject introspection data for Mutter
 gir1.2-panelapplet-5.0 GObject introspection for the GNOME Panel Applet librar
 gir1.2-pango-1.0:amd64 Layout and rendering of internationalized text - gir bind
 gir1.2-rb-3.0:amd64  GObject introspection data for the rhythmbox music player
 gir1.2-webkit2-4.0:amd64 Web content engine library for GTK+ - GObject introspecti
 git                  fast, scalable, distributed revision control system
 gnome-applets        Various applets for the GNOME panel - binary files
 gnome-applets-data   Various applets for the GNOME panel - data files
 gnome-contacts       Contacts manager for GNOME
 gnome-control-center utilities to configure the GNOME desktop
 gnome-desktop3-data  Common files for GNOME desktop apps
 gnome-font-viewer    font viewer for GNOME
 gnome-icon-theme-symbolic GNOME desktop icon theme (symbolic icons)
 gnome-menus          GNOME implementation of the freedesktop menu specificatio
 gnome-online-accounts service to manage online accounts for the GNOME desktop
 gnome-panel          launcher and docking facility for GNOME
 gnome-settings-daemon daemon handling the GNOME session settings
 gnome-shell          graphical shell for the GNOME desktop
 gnome-themes-standard:amd64 Adwaita GTK+ 2 theme — engine
 gnome-themes-standard-data Adwaita GTK+ 2 theme — common files
 gparted              GNOME partition editor
 grilo-plugins-0.2-base:amd64 Framework for discovering and browsing media - Base Plu
 gstreamer1.0-clutter-3.0 Clutter PLugin for GStreamer 1.0
 gstreamer1.0-plugins-bad:amd64 GStreamer plugins from the "bad" set
 gstreamer1.0-plugins-bad-faad:amd64 GStreamer faad plugin from the "bad" set
 gstreamer1.0-plugins-bad-videoparsers:amd64 GStreamer videoparsers plugin from the "
 gstreamer1.0-plugins-base:amd64 GStreamer plugins from the "base" set
 gstreamer1.0-plugins-good:amd64 GStreamer plugins from the "good" set
 gvfs-libs:amd64      userspace virtual filesystem - private libraries
 gvfs-libs:i386       userspace virtual filesystem - private libraries
 indicator-applet-complete Clone of the GNOME panel indicator applet
 initramfs-tools      generic modular initramfs generator (automation)
 initramfs-tools-core generic modular initramfs generator (core tools)
 initscripts          scripts for initializing and shutting down the system
 keyboard-configuration system-wide keyboard preferences
 klibc-utils          small utilities built with klibc for early boot
 krb5-multidev        Development files for MIT Kerberos without Heimdal confli
 libanyevent-perl     event loop framework with multiple implementations
 libappstream-glib8:amd64 GNOME library to access AppStream services
 libass5:amd64        library for SSA/ASS subtitles rendering
 libatk1.0-dev        Development files for the ATK accessibility toolkit
 libautodie-perl      Perl pragma to make certain failures fatal
 libavcodec-ffmpeg-extra56:amd64 FFmpeg library with additional de/encoders for audio
 libavdevice-ffmpeg56:amd64 FFmpeg library for handling input and output devices - ru
 libavfilter-ffmpeg5:amd64 FFmpeg library containing media filters - runtime files
 libavformat-ffmpeg56:amd64 FFmpeg library with (de)muxers for multimedia containers 
 libavresample-ffmpeg2:amd64 FFmpeg compatibility library for resampling - runtime fi
 libbamf3-2:amd64     Window matching library - shared library
 libboost-filesystem1.58.0:amd64 filesystem operations (portable paths, iteration ove
 libboost-locale1.58.0:amd64 C++ facilities for localization
 libbz2-dev:amd64     high-quality block-sorting file compressor library - deve
 libc6-dev:amd64      GNU C Library: Development Libraries and Header Files
 libcairo-gobject2:amd64 Cairo 2D vector graphics library (GObject library)
 libcairo-script-interpreter2:amd64 Cairo 2D vector graphics library (script interpre
 libcairo2:amd64      Cairo 2D vector graphics library
 libcairo2:i386       Cairo 2D vector graphics library
 libcairo2-dev        Development files for the Cairo 2D graphics library
 libcamel-1.2-54:amd64 Evolution MIME message handling library
 libcap-ng0:amd64     An alternate POSIX capabilities library
 libcgmanager0:amd64  Central cgroup manager daemon (client library)
 libcgmanager0:i386   Central cgroup manager daemon (client library)
 libchamplain-0.12-0:amd64 C library providing ClutterActor to display maps
 libchamplain-gtk-0.12-0:amd64 Gtk+ widget to display maps
 libcheese-gtk25:amd64 tool to take pictures and videos from your webcam - widge
 libcheese8:amd64     tool to take pictures and videos from your webcam - base 
 libck-connector0:amd64 ConsoleKit libraries
 libclutter-1.0-0:amd64 Open GL based interactive canvas library
 libclutter-gst-3.0-0:amd64 Open GL based interactive canvas library GStreamer elemen
 libclutter-gtk-1.0-0:amd64 Open GL based interactive canvas library GTK+ widget
 libcogl-pango20:amd64 Object oriented GL/GLES Abstraction/Utility Layer
 libcogl-path20:amd64 Object oriented GL/GLES Abstraction/Utility Layer
 libcogl20:amd64      Object oriented GL/GLES Abstraction/Utility Layer
 libcompress-raw-bzip2-perl low-level interface to bzip2 compression library
 libcompress-raw-zlib-perl low-level interface to zlib compression library
 libcpufreq0          shared library to deal with the cpufreq Linux kernel feat
 libcryptui0a:amd64   UI library for OpenPGP prompts
 libcups2:amd64       Common UNIX Printing System(tm) - Core library
 libcups2:i386        Common UNIX Printing System(tm) - Core library
 libdbus-1-3:amd64    simple interprocess messaging system (library)
 libdbus-1-3:i386     simple interprocess messaging system (library)
 libdbus-1-dev:amd64  simple interprocess messaging system (development headers
 libdvdnav4:amd64     DVD navigation library
 libdvdread4:amd64    library for reading DVDs
 libebackend-1.2-10:amd64 Utility library for evolution data servers
 libebook-1.2-16:amd64 Client library for evolution address books
 libebook-contacts-1.2-2:amd64 Client library for evolution contacts books
 libecal-1.2-19:amd64 Client library for evolution calendars
 libedata-book-1.2-25:amd64 Backend library for evolution address books
 libedata-cal-1.2-28:amd64 Backend library for evolution calendars
 libedataserver-1.2-21:amd64 Utility library for evolution data servers
 libedataserverui-1.2-1:amd64 Utility library for evolution data servers
 libevolution         evolution libraries
 libexpat1-dev:amd64  XML parsing C library - development kit
 libfarstream-0.2-5:amd64 Audio/Video communications framework: core library
 libfcitx-gclient0:amd64 Flexible Input Method Framework - D-Bus client library fo
 libfontconfig1:amd64 generic font configuration library - runtime
 libfontconfig1:i386  generic font configuration library - runtime
 libfontconfig1-dev:amd64 generic font configuration library - development
 libfreerdp-cache1.1:amd64 Free Remote Desktop Protocol library (cache library)
 libfreerdp-common1.1.0:amd64 Free Remote Desktop Protocol library (common library)
 libfreerdp-core1.1:amd64 Free Remote Desktop Protocol library (core library)
 libfreerdp-crypto1.1:amd64 Free Remote Desktop Protocol library (freerdp-crypto libr
 libfreerdp-gdi1.1:amd64 Free Remote Desktop Protocol library (GDI library)
 libfreerdp-locale1.1:amd64 Free Remote Desktop Protocol library (locale library)
 libfreerdp-plugins-standard:amd64 RDP client for Windows Terminal Services (plugins)
 libfreerdp-utils1.1:amd64 Free Remote Desktop Protocol library (freerdp-utils libra
 libfreetype6-dev:amd64 FreeType 2 font engine, development files
 libgcab-1.0-0:amd64  Microsoft Cabinet file manipulation library
 libgck-1-0:amd64     Glib wrapper library for PKCS#11 - runtime
 libgck-1-0:i386      Glib wrapper library for PKCS#11 - runtime
 libgcr-base-3-1:amd64 Library for Crypto related tasks
 libgcr-base-3-1:i386 Library for Crypto related tasks
 libgdal1i            Geospatial Data Abstraction Library
 libgdata22:amd64     Library for accessing GData webservices - shared librarie
 libgeocode-glib0:amd64 geocoding and reverse geocoding GLib library using Nomina
 libgjs0e             Mozilla-based javascript bindings for the GNOME platform
 libgmp-dev:amd64     Multiprecision arithmetic library developers tools
 libgmpxx4ldbl:amd64  Multiprecision arithmetic library (C++ bindings)
 libgnome-bluetooth13:amd64 GNOME Bluetooth tools - support library
 libgnome-desktop-3-12:amd64 Utility library for loading .desktop files - runtime fil
 libgnutls30:amd64    GNU TLS library - main runtime library
 libgnutls30:i386     GNU TLS library - main runtime library
 libgoa-1.0-0b:amd64  library for GNOME Online Accounts
 libgoa-backend-1.0-1:amd64 backend library for GNOME Online Accounts
 libgom-1.0-0:amd64   Object mapper from GObjects to SQLite
 libgphoto2-6:amd64   gphoto2 digital camera library
 libgphoto2-6:i386    gphoto2 digital camera library
 libgphoto2-dev:amd64 gphoto2 digital camera library (development files)
 libgphoto2-port12:amd64 gphoto2 digital camera port library
 libgphoto2-port12:i386 gphoto2 digital camera port library
 libgssapi-krb5-2:amd64 MIT Kerberos runtime libraries - krb5 GSS-API Mechanism
 libgssapi-krb5-2:i386 MIT Kerberos runtime libraries - krb5 GSS-API Mechanism
 libgssrpc4:amd64     MIT Kerberos runtime libraries - GSS enabled ONCRPC
 libgstreamer-plugins-bad1.0-0:amd64 GStreamer development files for libraries from t
 libgstreamer-plugins-base1.0-0:amd64 GStreamer libraries from the "base" set
 libgstreamer-plugins-base1.0-0:i386 GStreamer libraries from the "base" set
 libgstreamer-plugins-good1.0-0:amd64 GStreamer development files for libraries from 
 libgstreamer1.0-0:amd64 Core GStreamer libraries and elements
 libgstreamer1.0-0:i386 Core GStreamer libraries and elements
 libgtk-3-0:amd64     GTK+ graphical user interface library
 libgtk-3-common      common files for the GTK+ graphical user interface librar
 libgweather-3-6:amd64 GWeather shared library
 libharfbuzz-dev      Development files for OpenType text shaping engine
 libharfbuzz-gobject0:amd64 OpenType text shaping engine ICU backend (GObject library
 libharfbuzz-icu0:amd64 OpenType text shaping engine ICU backend
 libharfbuzz0b:amd64  OpenType text shaping engine (shared library)
 libharfbuzz0b:i386   OpenType text shaping engine (shared library)
 libhdf5-10:amd64     Hierarchical Data Format 5 (HDF5) - runtime files - seria
 libhogweed4:amd64    low level cryptographic library (public-key cryptos)
 libhogweed4:i386     low level cryptographic library (public-key cryptos)
 libimobiledevice6:amd64 Library for communicating with the iPhone and iPod Touch
 libinput10:amd64     input device management and event handling library - shar
 libio-compress-perl  bundle of IO::Compress modules
 libk5crypto3:amd64   MIT Kerberos runtime libraries - Crypto Library
 libk5crypto3:i386    MIT Kerberos runtime libraries - Crypto Library
 libkadm5clnt-mit9:amd64 MIT Kerberos runtime libraries - Administration Clients
 libkadm5srv-mit9:amd64 MIT Kerberos runtime libraries - KDC and Admin Server
 libkdb5-8:amd64      MIT Kerberos runtime libraries - Kerberos database
 libkeyutils1:amd64   Linux Key Management Utilities (library)
 libkeyutils1:i386    Linux Key Management Utilities (library)
 libkmlbase1:amd64    Library to manipulate KML 2.2 OGC standard files - libkml
 libkmldom1:amd64     Library to manipulate KML 2.2 OGC standard files - libkml
 libkmlengine1:amd64  Library to manipulate KML 2.2 OGC standard files - libkml
 libkrb5-3:amd64      MIT Kerberos runtime libraries
 libkrb5-3:i386       MIT Kerberos runtime libraries
 libkrb5-dev          Headers and development libraries for MIT Kerberos
 liblcms2-dev:amd64   Little CMS 2 color management library development headers
 libltdl-dev:amd64    System independent dlopen wrapper for GNU libtool
 libmatroska6v5:amd64 extensible open standard audio/video container format (sh
 libmirclient9:amd64  Display server for Ubuntu - client library
 libmircommon5:amd64  Display server for Ubuntu - shared library
 libmirprotobuf3:amd64 Display server for Ubuntu - RPC definitions
 libmpdec2:amd64      library for decimal floating point arithmetic (runtime li
 libmutter0g          window manager library from the Mutter window manager
 libmysqlcppconn7v5   MySQL Connector for C++ (library)
 libncurses5-dev:amd64 developer's libraries for ncurses
 libndp0:amd64        Library for Neighbor Discovery Protocol
 libnetcdf11          Interface for scientific data access to large binary data
 libnm-glib4:amd64    network management framework (GLib shared library)
 libnm-util2:amd64    network management framework (shared library)
 libnm0:amd64         GObject-based client library for NetworkManager
 libnma0:amd64        library for wireless and mobile dialogs (libnm version)
 libnspr4-0d:amd64    NetScape Portable Runtime Library - transitional package
 libodbc1:amd64       ODBC library for Unix
 libodbc1:i386        ODBC library for Unix
 libogdi3.2           Open Geographic Datastore Interface Library -- library
 libopencolorio1v5    complete color management solution - runtime
 libopencv-calib3d2.4v5:amd64 computer vision Camera Calibration library
 libopencv-contrib2.4v5:amd64 computer vision contrib library
 libopencv-features2d2.4v5:amd64 computer vision Feature Detection and Descriptor Ext
 libopencv-flann2.4v5:amd64 computer vision Clustering and Search in Multi-Dimensiona
 libopencv-highgui2.4v5:amd64 computer vision High-level GUI and Media I/O library
 libopencv-imgproc2.4v5:amd64 computer vision Image Processing library
 libopencv-legacy2.4v5:amd64 computer vision legacy library
 libopencv-ml2.4v5:amd64 computer vision Machine Learning library
 libopencv-objdetect2.4v5:amd64 computer vision Object Detection library
 libopencv-video2.4v5:amd64 computer vision Video analysis library
 libopenexr22:amd64   runtime files for the OpenEXR image library
 libp11-kit-dev:amd64 library for loading and coordinating access to PKCS#11 mo
 libpam-ck-connector:amd64 ConsoleKit PAM module
 libpam-systemd:amd64 system and service manager - PAM module
 libpanel-applet0     library for GNOME Panel applets
 libpango-1.0-0:amd64 Layout and rendering of internationalized text
 libpango-1.0-0:i386  Layout and rendering of internationalized text
 libpango1.0-0:amd64  Layout and rendering of internationalized text (transitio
 libpango1.0-0:i386   Layout and rendering of internationalized text (transitio
 libpango1.0-dev      Development files for the Pango
 libpangocairo-1.0-0:amd64 Layout and rendering of internationalized text
 libpangocairo-1.0-0:i386 Layout and rendering of internationalized text
 libpangoft2-1.0-0:amd64 Layout and rendering of internationalized text
 libpangoft2-1.0-0:i386 Layout and rendering of internationalized text
 libpangox-1.0-0:amd64 pango library X backend
 libpangox-1.0-0:i386 pango library X backend
 libpangoxft-1.0-0:amd64 Layout and rendering of internationalized text
 libpangoxft-1.0-0:i386 Layout and rendering of internationalized text
 libpcre3-dev:amd64   Perl 5 Compatible Regular Expression Library - developmen
 libpeas-1.0-0:amd64  Application plugin library
 libpeas-1.0-0-python3loader Application plugin library
 libperl5.22:amd64    shared Perl library
 libpng12-dev:amd64   PNG library - development
 libpoppler58:amd64   PDF rendering library
 libprotobuf-lite9v5:amd64 protocol buffers C++ library (lite version)
 libpython3-stdlib:amd64 interactive high-level object-oriented language (default 
 libpython3.5:amd64   Shared Python runtime library (version 3.5)
 libpython3.5-stdlib:amd64 Interactive high-level object-oriented language (standard
 libreoffice          office productivity suite (metapackage)
 libreoffice-base     office productivity suite -- database
 libreoffice-base-core office productivity suite -- shared library
 libreoffice-calc     office productivity suite -- spreadsheet
 libreoffice-common   office productivity suite -- arch-independent files
 libreoffice-core     office productivity suite -- arch-dependent files
 libreoffice-draw     office productivity suite -- drawing
 libreoffice-gnome    office productivity suite -- GNOME integration
 libreoffice-gtk      office productivity suite -- GTK+ integration
 libreoffice-impress  office productivity suite -- presentation
 libreoffice-l10n-en-gb office productivity suite -- English_british language p
 libreoffice-math     office productivity suite -- equation editor
 libreoffice-ogltrans LibreOffice Impress extension for slide transitions using
 libreoffice-pdfimport PDF Import component for LibreOffice
 libreoffice-style-galaxy office productivity suite -- Galaxy (Default) symbol 
 libreoffice-style-human office productivity suite -- Human symbol style
 libreoffice-style-tango office productivity suite -- Tango symbol style
 libreoffice-writer   office productivity suite -- word processor
 librhythmbox-core9:amd64 support library for the rhythmbox music player
 librtmp1:amd64       toolkit for RTMP streams (shared library)
 libsecret-1-0:amd64  Secret store
 libsecret-1-0:i386   Secret store
 libsodium18:amd64    Network communication, cryptography and signaturing libra
 libsoundtouch1:amd64 Sound stretching library
 libssh-gcrypt-4:amd64 tiny C SSH library (gcrypt flavor)
 libssl-dev:amd64     Secure Sockets Layer toolkit - development files
 libswresample-ffmpeg1:amd64 FFmpeg library for audio resampling, rematrixing etc. - 
 libsz2:amd64         Adaptive Entropy Coding library - SZIP
 libtag1v5:amd64      audio meta-data library
 libtag1v5-vanilla:amd64 audio meta-data library - vanilla flavour
 libtagc0:amd64       audio meta-data library - C bindings
 libtasn1-6-dev:amd64 Manage ASN.1 structures (development)
 libtelepathy-farstream3:amd64 Glue library between telepathy and farstream
 libtelepathy-glib0:amd64 Telepathy framework - GLib library
 libtimezonemap-data  GTK+3 timezone map widget - data files
 libtimezonemap1:amd64 GTK+3 timezone map widget
 libtirpc1:amd64      transport-independent RPC library
 libunity-settings-daemon1:amd64 Helper library for accessing settings
 liburiparser1:amd64  URI parsing library compliant with RFC 3986
 libusbmuxd4:amd64    USB multiplexor daemon for iPhone and iPod Touch devices 
 libwacom2:amd64      Wacom model feature query library
 libwayland-cursor0:amd64 wayland compositor infrastructure - cursor library
 libwayland-dev       wayland compositor infrastructure - development files
 libwayland-server0:amd64 wayland compositor infrastructure - server library
 libwebkit2gtk-4.0-37:amd64 Web content engine library for GTK+
 libwebp5:amd64       Lossy compression of digital photographic images.
 libwebp5:i386        Lossy compression of digital photographic images.
 libwinpr-sspi0.1:amd64 Windows Portable Runtime library (sspi library)
 libwinpr-synch0.1:amd64 Windows Portable Runtime library (synch library)
 libwinpr-utils0.1:amd64 Windows Portable Runtime library (utils library)
 libx11-6:amd64       X11 client-side library
 libx11-6:i386        X11 client-side library
 libx11-data          X11 client-side library
 libx11-dev:amd64     X11 client-side library (development headers)
 libxcb1:amd64        X C Binding
 libxcb1:i386         X C Binding
 libxcb1-dev:amd64    X C Binding, development files
 libxdmcp-dev:amd64   X11 authorisation library (development headers)
 libxdmcp6:amd64      X11 Display Manager Control Protocol library
 libxdmcp6:i386       X11 Display Manager Control Protocol library
 libxfont1:amd64      X11 font rasterisation library
 libxkbcommon-dev     library interface to the XKB compiler - development files
 libxkbcommon-x11-0:amd64 library to create keymaps with the XKB X11 protocol
 libzmq5:amd64        lightweight messaging kernel (shared library)
 lightdm              Display Manager
 locales              GNU C Library: National Language (locale) data [support]
 mcp-account-manager-uoa GNOME multi-protocol chat and call client (UOA plugin)
 mplayer              movie player for Unix-like systems
 mplayer2             transitional package from mplayer2 to mplayer
 mutter               lightweight GTK+ window manager
 netbase              Basic TCP/IP networking system
 nfs-common           NFS support files common to client and server
 ntpdate              client for setting system time from NTP servers
 onboard              Simple On-screen Keyboard
 p11-kit-modules:amd64 p11-glue proxy and trust modules
 pdl                  perl data language: Perl extensions for numerics
 perl                 Larry Wall's Practical Extraction and Report Language
 plymouth             boot animation, logger and I/O multiplexer
 plymouth-label       boot animation, logger and I/O multiplexer - label contro
 plymouth-theme-ubuntu-logo boot animation, logger and I/O multiplexer - ubuntu
 plymouth-theme-ubuntu-text boot animation, logger and I/O multiplexer - ubuntu
 plymouth-x11         boot animation, logger and I/O multiplexer - X11 renderer
 python-gi            Python 2.x bindings for gobject-introspection libraries
 python-lockfile      file locking library for Python — Python 2 library
 python3              interactive high-level object-oriented language (default 
 python3-apt          Python 3 interface to libapt-pkg
 python3-brlapi       Braille display access via BRLTTY - Python3 bindings
 python3-bsddb3       Python interface for Berkeley DB (Python 3.x)
 python3-cairo        Python 3 bindings for the Cairo vector graphics library
 python3-crypto       cryptographic algorithms and protocols for Python 3
 python3-dbus         simple interprocess messaging system (Python 3 interface)
 python3-gdbm:amd64   GNU dbm database support for Python 3.x
 python3-gi           Python 3 bindings for gobject-introspection libraries
 python3-gi-cairo     Python 3 Cairo bindings for the GObject library
 python3-icu          Python 3 extension wrapping the ICU C++ API
 python3-libapparmor  AppArmor library Python3 bindings
 python3-lxml         pythonic binding for the libxml2 and libxslt libraries
 python3-markupsafe   HTML/XHTML/XML string library for Python 3
 python3-pkg-resources Package Discovery and Resource Access using pkg_resource
 python3-pycurl       Python bindings to libcurl (Python 3)
 python3-uno          Python-UNO bridge
 python3.5            Interactive high-level object-oriented language (version 
 rhythmbox-plugin-magnatune Magnatune plugin for rhythmbox music player
 rhythmbox-plugins    plugins for rhythmbox music player
 rpcbind              converts RPC program numbers into universal addresses
 rsyslog              reliable system and kernel logging daemon
 seahorse-daemon      Seahorse pass phrase caching agent
 software-center      Utility for browsing, installing, and removing software
 systemd-shim         shim for systemd
 udisks2              D-Bus service to access and manipulate storage devices
 ufw                  program for managing a Netfilter firewall
 uno-libs3            LibreOffice UNO runtime environment -- public shared libr
 upower               abstraction for power management
 upstart              event-based init daemon - essential binaries
 ure                  LibreOffice UNO runtime environment
 usbmuxd              USB multiplexor daemon for iPhone and iPod Touch devices
 vino                 VNC server for GNOME
 x11proto-input-dev   X11 Input extension wire protocol
 xine-ui              the xine video player, user interface
 zlib1g-dev:amd64     compression library - development

The following packages are awaiting processing of triggers that they
have activated in other packages.  This processing can be requested using
dselect or dpkg --configure --pending (or dpkg --triggers-only):
 evolution-common     architecture independent files for Evolution
 libgnome2-common     The GNOME library - common files
 nautilus-sendto      integrates Evolution and Pidgin into the Nautilus file ma
 totem-common         Data files for the Totem media player

The following packages have been triggered, but the trigger processing
has not yet been done.  Trigger processing can be requested using
dselect or dpkg --configure --pending (or dpkg --triggers-only):
 desktop-file-utils   Utilities for .desktop files
 gconf2               GNOME configuration database system (support tools)
 lintian              Debian package checker

The following packages are missing the md5sums control file in the
database, they need to be reinstalled:
 gsfonts-other        Additional fonts for the ghostscript interpreter
 libjson0:amd64       JSON manipulation library (transitional package)
 libjson0:i386        JSON manipulation library (transitional package)
 libreoffice3-ure     UNO Runtime Environment
 medibuntu-keyring    GnuPG key of the Medibuntu repository
 openproj             A desktop replacement for Microsoft Project
 pdfsam               PDF Split and Merge
 sun-java6-fonts      Lucida TrueType fonts (from the Sun JRE)

```

---

### Post by ian-weisser on 2017-01-09
Ah that provides much information. thank you.
Please show us the contents of your broken system's /etc/apt/sources.list

---

### Post by cscj01 on 2017-01-09
Here are the contents of /etc/apt/sources.lst```
deb http://archive.ubuntu.com/ubuntu xenial universe main restricted multiverse
deb http://security.ubuntu.com/ubuntu/ xenial-security universe main multiverse restricted
deb http://archive.ubuntu.com/ubuntu xenial-updates universe main multiverse restricted
# deb http://debian.tagancha.org/debian/ trusty main # disabled on upgrade to trusty
# deb-src http://debian.tagancha.org/debian/ trusty main # disabled on upgrade to trusty
deb http://archive.ubuntu.com/ubuntu xenial-backports universe main multiverse restricted
deb http://archive.canonical.com/ xenial partner
deb-src http://archive.canonical.com/ xenial partner
# deb http://debian.scribus.net/debian/ trusty main
# deb-src http://debian.scribus.net/debian/ trusty main # disabled on upgrade to trusty


# deb http://repository.spotify.com stable non-free # disabled on upgrade to xenial
# deb-src http://repository.spotify.com stable non-free # disabled on upgrade to trusty
# deb http://ppa.launchpad.net/pmjdebruijn/darktable-release/ubuntu trusty main
# deb-src http://ppa.launchpad.net/pmjdebruijn/darktable-release/ubuntu trusty source
# deb http://download.virtualbox.org/virtualbox/debian xenial contrib # disabled on upgrade to xenial
# deb-src http://download.virtualbox.org/virtualbox/debian trusty contrib
# deb http://ppa.launchpad.net/otto-kesselgulasch/gimp/ubuntu trusty main
# deb-src http://ppa.launchpad.net/otto-kesselgulasch/gimp/ubuntu trusty main
# deb http://archive.getdeb.net/ubuntu trusty-getdeb apps
# deb-src http://archive.getdeb.net/ubuntu trusty-getdeb apps
# deb http://ppa.launchpad.net/unit193/crosswire/ubuntu trusty main
# deb-src http://ppa.launchpad.net/unit193/crosswire/ubuntu trusty main
# deb http://www.openprinting.org/download/printdriver/debian/ lsb3.2 main
# deb-src http://www.openprinting.org/download/printdriver/debian/ lsb3.2 main
# deb http://ppa.launchpad.net/linuxgndu/sqlitebrowser/ubuntu trusty main
# deb-src http://ppa.launchpad.net/linuxgndu/sqlitebrowser/ubuntu trusty main
```

---

### Post by DuckHook on 2017-01-09
> **cscj01 said:**
> Okay, I have something installed.  My system says it is [COLOR="#FF0000"]16.04.1[/COLOR] running kernel [COLOR="#FF0000"]3.13.0-105[/COLOR].

> **ian-weisser said:**
> …Please show us the contents of your broken system's /etc/apt/sources.listI've no desire to muddy the waters here Ian, especially after you've taken OP this far, but I've seen this combo (Xenial with old, oddball Trusty kernel) when a new Xenial install is attempted over an old Trusty one, but user chooses to ***not*** format / (root) at the partition stage during setup. Trying again, but this time making sure to format the / partition will wipe it of all old files and ensure that a pristine new install takes hold.

---

### Post by ian-weisser on 2017-01-10
> **cscj01 said:**
> I have screenlog.0 from /var/log/dist-upgrades which shows all the problems incurred.  It is a large file. It is 7.5 MB.  I cannot attach a file that large.  What now?

That's an achievement!
Why don't you show us the first errors and the subsequent 50-or-so lines?

---

### Post by bhcarpe on 2017-01-10
This is still cscj01.  I had to log in with a new account because my computer went down, and I am now working from a Live DVD of Xenial.  Here are the pertinent lines from screenlog.0 as they occured.  I have inserted some indicators to show some okay message were skipped.```
dpkg: libnettle4:amd64: dependency problems, but removing anyway as you requested: 
 libgnutls28:amd64 depends on libnettle4 (>= 2.7); however: 
  Package libnettle4:amd64 is to be removed. 
 libarchive12:amd64 depends on libnettle4 (>= 2.3); however: 
  Package libnettle4:amd64 is to be removed. 
 libarchive13:amd64 depends on libnettle4 (>= 2.3); however: 
  Package libnettle4:amd64 is to be removed. 
 libhogweed2:amd64 depends on libnettle4; however: 
  Package libnettle4:amd64 is to be removed.
.
.
Removing libnettle4:amd64 (2.7.1-1ubuntu0.1) ... 
dpkg: libhogweed2:amd64: dependency problems, but removing anyway as you requested: 
 libgnutls28:amd64 depends on libhogweed2 (>= 2.7); however: 
  Package libhogweed2:amd64 is to be removed. 

.
.
.
dpkg: libcogl15:amd64: dependency problems, but removing anyway as you requested: 
 libtotem0 depends on libcogl15 (>= 1.15.8); however: 
  Package libcogl15:amd64 is to be removed. 
 gir1.2-cogl-1.0 depends on libcogl15 (>= 1.15.8). 
 libclutter-gst-2.0-0:amd64 depends on libcogl15 (>= 1.15.8). 
 libcogl-pango15:amd64 depends on libcogl15 (>= 1.15.8); however: 
  Package libcogl15:amd64 is to be removed. 
 gstreamer1.0-clutter depends on libcogl15 (>= 1.15.8). 
 libcheese-gtk23:amd64 depends on libcogl15 (>= 1.15.8); however: 
  Package libcogl15:amd64 is to be removed. 
 totem depends on libcogl15 (>= 1.15.8); however: 
  Package libcogl15:amd64 is to be removed. 
 libmutter0c depends on libcogl15 (>= 1.15.8); however: 
  Package libcogl15:amd64 is to be removed. 
 libclutter-gtk-1.0-0:amd64 depends on libcogl15 (>= 1.15.8); however: 
  Package libcogl15:amd64 is to be removed. 
 empathy depends on libcogl15 (>= 1.15.8); however: 
  Package libcogl15:amd64 is to be removed. 
 libclutter-1.0-0:amd64 depends on libcogl15 (>= 1.15.8
.
.
.
dpkg: libcogl15:amd64: dependency problems, but removing anyway as you requested: 
 libtotem0 depends on libcogl15 (>= 1.15.8); however: 
  Package libcogl15:amd64 is to be removed. 
 gir1.2-cogl-1.0 depends on libcogl15 (>= 1.15.8). 
 libclutter-gst-2.0-0:amd64 depends on libcogl15 (>= 1.15.8). 
 libcogl-pango15:amd64 depends on libcogl15 (>= 1.15.8); however: 
  Package libcogl15:amd64 is to be removed. 
 gstreamer1.0-clutter depends on libcogl15 (>= 1.15.8). 
 libcheese-gtk23:amd64 depends on libcogl15 (>= 1.15.8); however: 
  Package libcogl15:amd64 is to be removed. 
 totem depends on libcogl15 (>= 1.15.8); however: 
  Package libcogl15:amd64 is to be removed. 
 libmutter0c depends on libcogl15 (>= 1.15.8); however: 
  Package libcogl15:amd64 is to be removed. 
 libclutter-gtk-1.0-0:amd64 depends on libcogl15 (>= 1.15.8); however: 
  Package libcogl15:amd64 is to be removed. 
 empathy depends on libcogl15 (>= 1.15.8); however: 
  Package libcogl15:amd64 is to be removed.
```There are many, many more of these.

---

### Post by ian-weisser on 2017-01-10
Both libnettle4 and libcogl15 were dropped from Ubuntu between 14.04 and 16.04, so are properly removed...along with any dependencies.
User can also remove those packages (and their associated applications) before upgrading, to prevent the removal notifications.

Show more!

---

### Post by bhcarpe on 2017-01-10
Moving on down screenlog.0 we have```
dpkg: libgnome-control-center1: dependency problems, but removing anyway as you requested: 
 deja-dup depends on libgnome-control-center1 (>= 1:3.3.5); however: 
  Package libgnome-control-center1 is to be removed. 
 gnome-control-center depends on libgnome-control-center1 (>= 1:3.5.2); however: 
  Package libgnome-control-center1 is to be removed.
.
.
.
Removing libgnome-control-center1 (1:3.6.3-0ubuntu56.1) ... 
Processing triggers for libc-bin (2.19-0ubuntu6.9) ...dpkg: libgnome-control-center1: dependency problems, but removing anyway as you requested: 
 deja-dup depends on libgnome-control-center1 (>= 1:3.3.5); however: 
  Package libgnome-control-center1 is to be removed. 
 gnome-control-center depends on libgnome-control-center1 (>= 1:3.5.2); however: 
  Package libgnome-control-center1 is to be removed.
.
.
.
dpkg: libmutter0c: dependency problems, but removing anyway as you requested: 
 gir1.2-mutter-3.0 depends on libmutter0c (<< 3.11); however: 
  Package libmutter0c is to be removed. 
 gir1.2-mutter-3.0 depends on libmutter0c (>= 3.10); however: 
  Package libmutter0c is to be removed. 
 gir1.2-mutter-3.0 depends on libmutter0c (<< 3.11); however: 
  Package libmutter0c is to be removed. 
 gir1.2-mutter-3.0 depends on libmutter0c (>= 3.10); however: 
  Package libmutter0c is to be removed.
.
.
.
dpkg: libical1: dependency problems, but removing anyway as you requested: 
 libecal-1.2-16 depends on libical1 (>= 1.0); however: 
  Package libical1 is to be removed. 
 libevolution depends on libical1 (>= 1.0); however: 
  Package libical1 is to be removed. 
 evolution depends on libical1 (>= 1.0); however: 
  Package libical1 is to be removed. 
 evolution-plugins depends on libical1 (>= 1.0); however: 
  Package libical1 is to be removed. 
 indicator-datetime depends on libical1 (>= 1.0); however: 
  Package libical1 is to be removed. 
 evolution-data-server depends on libical1 (>= 1.0); however: 
  Package libical1 is to be removed. 
 gnome-panel depends on libical1 (>= 1.0); however: 
  Package libical1 is to be removed. 
 libedata-cal-1.2-23 depends on libical1 (>= 1.0); however: 
  Package libical1 is to be removed.
.
.
.
dpkg: libmozjs-24-0: dependency problems, but removing anyway as you requested: 
 libgjs0e depends on libmozjs-24-0; however: 
  Package libmozjs-24-0 is to be removed.dpkg: libopencv-flann2.4:amd64: dependency problems, but removing anyway as you requested: 
 libopencv-features2d2.4:amd64 depends on libopencv-flann2.4 (= 2.4.8+dfsg1-2ubuntu1); however: 
  Package libopencv-flann2.4:amd64 is to be removed. 
 libopencv-calib3d2.4:amd64 depends on libopencv-flann2.4; however: 
  Package libopencv-flann2.4:amd64 is to be removed.
.dpkg: libopencv-flann2.4:amd64: dependency problems, but removing anyway as you requested: 
 libopencv-features2d2.4:amd64 depends on libopencv-flann2.4 (= 2.4.8+dfsg1-2ubuntu1); however: 
  Package libopencv-flann2.4:amd64 is to be removed. 
 libopencv-calib3d2.4:amd64 depends on libopencv-flann2.4; however: 
  Package libopencv-flann2.4:amd64 is to be removed.
.
.
dpkg: libmozjs-24-0: dependency problems, but removing anyway as you requested: 
 libgjs0e depends on libmozjs-24-0; however: 
  Package libmozjs-24-0 is to be removed.
.
.
.
dpkg: libopencv-core2.4:amd64: dependency problems, but removing anyway as you requested: 
 libopencv-imgproc2.4:amd64 depends on libopencv-core2.4 (= 2.4.8+dfsg1-2ubuntu1). dpkg: libopencv-flann2.4:amd64: dependency problems, but removing anyway as you requested: 
 libopencv-features2d2.4:amd64 depends on libopencv-flann2.4 (= 2.4.8+dfsg1-2ubuntu1); however: 
  Package libopencv-flann2.4:amd64 is to be removed. 
 libopencv-calib3d2.4:amd64 depends on libopencv-flann2.4; however: 
  Package libopencv-flann2.4:amd64 is to be removed.
 gstreamer1.0-plugins-bad:amd64 depends on libopencv-core2.4; however: 
  Package libopencv-core2.4:amd64 is to be removed. 
 libopencv-features2d2.4:amd64 depends on libopencv-core2.4. 
 libopencv-legacy2.4:amd64 depends on libopencv-core2.4. dpkg: libopencv-flann2.4:amd64: dependency problems, but removing anyway as you requested: 
 libopencv-features2d2.4:amd64 depends on libopencv-flann2.4 (= 2.4.8+dfsg1-2ubuntu1); however: 
  Package libopencv-flann2.4:amd64 is to be removed. 
 libopencv-calib3d2.4:amd64 depends on libopencv-flann2.4; however: 
  Package libopencv-flann2.4:amd64 is to be removed.
 libopencv-calib3d2.4:amd64 depends on libopencv-core2.4. 
 digikam depends on libopencv-core2.4; however: 
  Package libopencv-core2.4:amd64 is to be removed. 
 libopencv-contrib2.4:amd64 depends on libopencv-core2.4. 
 libopencv-video2.4:amd64 depends on libopencv-core2.4. 
 libopencv-highgui2.4:amd64 depends on libopencv-core2.4; however: 
  Package libopencv-core2.4:amd64 is to be removed.
.
.
.
dpkg: libopencv-flann2.4:amd64: dependency problems, but removing anyway as you requested: 
 libopencv-features2d2.4:amd64 depends on libopencv-flann2.4 (= 2.4.8+dfsg1-2ubuntu1); however: 
  Package libopencv-flann2.4:amd64 is to be removed. 
 libopencv-calib3d2.4:amd64 depends on libopencv-flann2.4; however: 
  Package libopencv-flann2.4:amd64 is to be removed.
.
.
.
dpkg: libopencv-flann2.4:amd64: dependency problems, but removing anyway as you requested: 
 libopencv-features2d2.4:amd64 depends on libopencv-flann2.4 (= 2.4.8+dfsg1-2ubuntu1); however: 
  Package libopencv-flann2.4:amd64 is to be removed. 
 libopencv-calib3d2.4:amd64 depends on libopencv-flann2.4; however: 
  Package libopencv-flann2.4:amd64 is to be removed.
.
.
.
dpkg: libopencv-imgproc2.4:amd64: dependency problems, but removing anyway as you requested: 
 gstreamer1.0-plugins-bad:amd64 depends on libopencv-imgproc2.4; however: 
  Package libopencv-imgproc2.4:amd64 is to be removed. 
 libopencv-features2d2.4:amd64 depends on libopencv-imgproc2.4 (= 2.4.8+dfsg1-2ubuntu1); however: 
  Package libopencv-imgproc2.4:amd64 is to be removed. 
 libopencv-legacy2.4:amd64 depends on libopencv-imgproc2.4; however: 
  Package libopencv-imgproc2.4:amd64 is to be removed. 
 libopencv-calib3d2.4:amd64 depends on libopencv-imgproc2.4; however: 
  Package libopencv-imgproc2.4:amd64 is to be removed. 
 libopencv-contrib2.4:amd64 depends on libopencv-imgproc2.4; however: 
  Package libopencv-imgproc2.4:amd64 is to be removed. 
 libopencv-video2.4:amd64 depends on libopencv-imgproc2.4 (= 2.4.8+dfsg1-2ubuntu1); however: 
  Package libopencv-imgproc2.4:amd64 is to be removed. 
 libopencv-highgui2.4:amd64 depends on libopencv-imgproc2.4 (= 2.4.8+dfsg1-2ubuntu1); however: 
  Package libopencv-imgproc2.4:amd64 
.
.
.
dpkg: libopencv-imgproc2.4:amd64: dependency problems, but removing anyway as you requested: 
 gstreamer1.0-plugins-bad:amd64 depends on libopencv-imgproc2.4; however: 
  Package libopencv-imgproc2.4:amd64 is to be removed. 
 libopencv-features2d2.4:amd64 depends on libopencv-imgproc2.4 (= 2.4.8+dfsg1-2ubuntu1); however: 
  Package libopencv-imgproc2.4:amd64 is to be removed. 
 libopencv-legacy2.4:amd64 depends on libopencv-imgproc2.4; however: 
  Package libopencv-imgproc2.4:amd64 is to be removed. 
 libopencv-calib3d2.4:amd64 depends on libopencv-imgproc2.4; however: 
  Package libopencv-imgproc2.4:amd64 is to be removed. 
 libopencv-contrib2.4:amd64 depends on libopencv-imgproc2.4; however: 
  Package libopencv-imgproc2.4:amd64 is to be removed. 
 libopencv-video2.4:amd64 depends on libopencv-imgproc2.4 (= 2.4.8+dfsg1-2ubuntu1); however: 
  Package libopencv-imgproc2.4:amd64 is to be removed. 
 libopencv-highgui2.4:amd64 depends on libopencv-imgproc2.4 (= 2.4.8+dfsg1-2ubuntu1); however: 
  Package libopencv-imgproc2.4:amd64 
.
.
.
dpkg: libopencv-features2d2.4:amd64: dependency problems, but removing anyway as you requested: 
 libopencv-legacy2.4:amd64 depends on libopencv-features2d2.4; however: 
  Package libopencv-features2d2.4:amd64 is to be removed. 
 libopencv-calib3d2.4:amd64 depends on libopencv-features2d2.4 (= 2.4.8+dfsg1-2ubuntu1); however: 
  Package libopencv-features2d2.4:amd64 is to be removed. 
 libopencv-contrib2.4:amd64 depends on libopencv-features2d2.4; however: 
  Package libopencv-features2d2.4:amd64 is to be removed.
.
.
.
dpkg: libopencv-calib3d2.4:amd64: dependency problems, but removing anyway as you requested: 
 gstreamer1.0-plugins-bad:amd64 depends on libopencv-calib3d2.4; however: 
  Package libopencv-calib3d2.4:amd64 is to be removed. 
 libopencv-legacy2.4:amd64 depends on libopencv-calib3d2.4 (= 2.4.8+dfsg1-2ubuntu1). 
 libopencv-contrib2.4:amd64 depends on libopencv-calib3d2.4 (= 2.4.8+dfsg1-2ubuntu1).
.
.
.
dpkg: libopencv-calib3d2.4:amd64: dependency problems, but removing anyway as you requested: 
 gstreamer1.0-plugins-bad:amd64 depends on libopencv-calib3d2.4; however: 
  Package libopencv-calib3d2.4:amd64 is to be removed. 
 libopencv-legacy2.4:amd64 depends on libopencv-calib3d2.4 (= 2.4.8+dfsg1-2ubuntu1). 
 libopencv-contrib2.4:amd64 depends on libopencv-calib3d2.4 (= 2.4.8+dfsg1-2ubuntu1).
.
.
.
dpkg: libopencv-calib3d2.4:amd64: dependency problems, but removing anyway as you requested: 
 gstreamer1.0-plugins-bad:amd64 depends on libopencv-calib3d2.4; however: 
  Package libopencv-calib3d2.4:amd64 is to be removed. 
 libopencv-legacy2.4:amd64 depends on libopencv-calib3d2.4 (= 2.4.8+dfsg1-2ubuntu1). 
 libopencv-contrib2.4:amd64 depends on libopencv-calib3d2.4 (= 2.4.8+dfsg1-2ubuntu1).
.
.
.
dpkg: libopencv-calib3d2.4:amd64: dependency problems, but removing anyway as you requested: 
 gstreamer1.0-plugins-bad:amd64 depends on libopencv-calib3d2.4; however: 
  Package libopencv-calib3d2.4:amd64 is to be removed. 
 libopencv-legacy2.4:amd64 depends on libopencv-calib3d2.4 (= 2.4.8+dfsg1-2ubuntu1). 
 libopencv-contrib2.4:amd64 depends on libopencv-calib3d2.4 (= 2.4.8+dfsg1-2ubuntu1).
.
.
.
dpkg: libopencv-highgui2.4:amd64: dependency problems, but removing anyway as you requested: 
 libopenimageio1.3 depends on libopencv-highgui2.4; however: 
  Package libopencv-highgui2.4:amd64 is to be removed. 
 gstreamer1.0-plugins-bad:amd64 depends on libopencv-highgui2.4; however: 
  Package libopencv-highgui2.4:amd64 is to be removed. 
 libopencv-legacy2.4:amd64 depends on libopencv-highgui2.4 (= 2.4.8+dfsg1-2ubuntu1); however: 
  Package libopencv-highgui2.4:amd64 is to be removed. 
 libopencv-contrib2.4:amd64 depends on libopencv-highgui2.4 (= 2.4.8+dfsg1-2ubuntu1); however: 
  Package libopencv-highgui2.4:amd64 is to be removed. 
 libopencv-objdetect2.4:amd64 depends on libopencv-highgui2.4 (= 2.4.8+dfsg1-2ubuntu1); however: 
  Package libopencv-highgui2.4:amd64 is to be removed.
.
.
.
dpkg: libopencv-highgui2.4:amd64: dependency problems, but removing anyway as you requested: 
 libopenimageio1.3 depends on libopencv-highgui2.4; however: 
  Package libopencv-highgui2.4:amd64 is to be removed. 
 gstreamer1.0-plugins-bad:amd64 depends on libopencv-highgui2.4; however: 
  Package libopencv-highgui2.4:amd64 is to be removed. 
 libopencv-legacy2.4:amd64 depends on libopencv-highgui2.4 (= 2.4.8+dfsg1-2ubuntu1); however: 
  Package libopencv-highgui2.4:amd64 is to be removed. 
 libopencv-contrib2.4:amd64 depends on libopencv-highgui2.4 (= 2.4.8+dfsg1-2ubuntu1); however: 
  Package libopencv-highgui2.4:amd64 is to be removed. 
 libopencv-objdetect2.4:amd64 depends on libopencv-highgui2.4 (= 2.4.8+dfsg1-2ubuntu1); however: 
  Package libopencv-highgui2.4:amd64 is to be removed.
.
.
.
dpkg: libopencv-ml2.4:amd64: dependency problems, but removing anyway as you requested: 
 libopencv-legacy2.4:amd64 depends on libopencv-ml2.4 (= 2.4.8+dfsg1-2ubuntu1); however: 
  Package libopencv-ml2.4:amd64 is to be removed. 
 libopencv-contrib2.4:amd64 depends on libopencv-ml2.4 (= 2.4.8+dfsg1-2ubuntu1); however: 
  Package libopencv-ml2.4:amd64 is to be removed.
.
.
.
dpkg: libopencv-objdetect2.4:amd64: dependency problems, but removing anyway as you requested: 
 gstreamer1.0-plugins-bad:amd64 depends on libopencv-objdetect2.4; however: 
  Package libopencv-objdetect2.4:amd64 is to be removed. 
 libopencv-contrib2.4:amd64 depends on libopencv-objdetect2.4 (= 2.4.8+dfsg1-2ubuntu1); however: 
  Package libopencv-objdetect2.4:amd64 is to be removed. 
 frei0r-plugins depends on libopencv-objdetect2.4; however: 
  Package libopencv-objdetect2.4:amd64 is to be removed. 
 libkface2 depends on libopencv-objdetect2.4; however: 
  Package libopencv-objdetect2.4:amd64 is to be removed.
.
.
.
dpkg: libopencv-objdetect2.4:amd64: dependency problems, but removing anyway as you requested: 
 gstreamer1.0-plugins-bad:amd64 depends on libopencv-objdetect2.4; however: 
  Package libopencv-objdetect2.4:amd64 is to be removed. 
 libopencv-contrib2.4:amd64 depends on libopencv-objdetect2.4 (= 2.4.8+dfsg1-2ubuntu1); however: 
  Package libopencv-objdetect2.4:amd64 is to be removed. 
 frei0r-plugins depends on libopencv-objdetect2.4; however: 
  Package libopencv-objdetect2.4:amd64 is to be removed. 
 libkface2 depends on libopencv-objdetect2.4; however: 
  Package libopencv-objdetect2.4:amd64 is to be removed.
.
.
.
dpkg: libopencv-video2.4:amd64: dependency problems, but removing anyway as you requested: 
 gstreamer1.0-plugins-bad:amd64 depends on libopencv-video2.4; however: 
  Package libopencv-video2.4:amd64 is to be removed. 
 libopencv-legacy2.4:amd64 depends on libopencv-video2.4 (= 2.4.8+dfsg1-2ubuntu1); however: 
  Package libopencv-video2.4:amd64 is to be removed. 
 libopencv-contrib2.4:amd64 depends on libopencv-video2.4 (= 2.4.8+dfsg1-2ubuntu1); however: 
  Package libopencv-video2.4:amd64 is to be removed.
.
.
.
dpkg: libopencv-contrib2.4:amd64: dependency problems, but removing anyway as you requested: 
 gstreamer1.0-plugins-bad:amd64 depends on libopencv-contrib2.4; however: 
  Package libopencv-contrib2.4:amd64 is to be removed. 
 libkface2 depends on libopencv-contrib2.4.
.
.
.
dpkg: libopencv-legacy2.4:amd64: dependency problems, but removing anyway as you requested: 
 gstreamer1.0-plugins-bad:amd64 depends on libopencv-legacy2.4; however: 
  Package libopencv-legacy2.4:amd64 is to be removed.
.
.
.
dpkg: libopencv-legacy2.4:amd64: dependency problems, but removing anyway as you requested: 
 gstreamer1.0-plugins-bad:amd64 depends on libopencv-legacy2.4; however: 
  Package libopencv-legacy2.4:amd64 is to be removed.
.
.
.
dpkg: perl-modules: dependency problems, but removing anyway as you requested: 
 git depends on perl-modules. 
 cli-common depends on perl-modules. 
 perl depends on perl-modules (>= 5.18.2-2ubuntu1.1). 
 libswitch-perl depends on perl-modules. 
 update-inetd depends on libfile-temp-perl; however: 
  Package libfile-temp-perl is not installed. 
  Package perl-modules which provides libfile-temp-perl is to be removed. 
 liburi-perl depends on libnet-perl; however: 
  Package libnet-perl is not installed. 
  Package perl-modules which provides libnet-perl is to be removed. 
 libmailtools-perl depends on libnet-perl; however: 
  Package libnet-perl is not installed. 
  Package perl-modules which provides libnet-perl is to be removed.
```I'm stopping here because I almost lost everything.  I'll add more after you take a look at this.

---

### Post by ian-weisser on 2017-01-10
Same story so far, all those top-level packages were dropped between 14.04 and 16.04 (libgnome-control-center1, libmutter0c, libical1, libmozjs-24-0,libopencv-*2.4, perl-modules)
Removal of those packages is expected behavior.
The lack of replacement packages and the dependency warnings are not expected behavior.

---

### Post by bhcarpe on 2017-01-10
I skipped to the end to show you the messages about broken packages.  I tried to fix them with aptitude, synaptic, and apt-get commands, but nothing seemed to work. Here's some of the tail end of the log.```
Investigating (9) cheese [ amd64 ] < 3.18.1-2ubuntu3 > ( gnome ) 
Broken cheese:amd64 Depends on libcheese8 [ amd64 ] < 3.18.1-2ubuntu3 > ( libs ) (>= 3.18.0) 
  Considering libcheese8:amd64 234 as a solution to cheese:amd64 1 
  Removing cheese:amd64 rather than change libcheese8:amd64 
Investigating (9) vino [ amd64 ] < 3.8.1-0ubuntu9.1 > ( gnome ) 
Broken vino:amd64 Depends on libsoup2.4-1 [ amd64 ] < 2.52.2-1ubuntu0.1 > ( libs ) (>= 2.24.0) 
  Considering libsoup2.4-1:amd64 234 as a solution to vino:amd64 1 
  Removing vino:amd64 rather than change libsoup2.4-1:amd64 
Investigating (9) gir1.2-ebookcontacts-1.2 [ amd64 ] < 3.10.4-0ubuntu1.5 -> 3.18.5-1ubuntu1 > ( introspection ) 
Broken gir1.2-ebookcontacts-1.2:amd64 Depends on gir1.2-edataserver-1.2 [ amd64 ] < 3.10.4-0ubuntu1.5 -> 3.18.5-1ubuntu1 > ( libs ) (= 3.10.4-0ubuntu1.5) 
  Considering gir1.2-edataserver-1.2:amd64 234 as a solution to gir1.2-ebookcontacts-1.2:amd64 1 
    Reinst Failed because of gir1.2-edataserver-1.2:amd64 
  Removing gir1.2-ebookcontacts-1.2:amd64 rather than change gir1.2-edataserver-1.2:amd64 
Investigating (9) libgupnp-1.0-4 [ amd64 ] < 0.20.10-1ubuntu1 -> 0.20.16-1 > ( universe/libs ) 
Broken libgupnp-1.0-4:amd64 Depends on libgssdp-1.0-3 [ amd64 ] < 0.14.7-1ubuntu1 -> 0.14.14-1ubuntu1 > ( universe/libs ) (>= 0.14.0) 
  Considering libgssdp-1.0-3:amd64 234 as a solution to libgupnp-1.0-4:amd64 1 
    Reinst Failed because of libgssdp-1.0-3:amd64 
  Removing libgupnp-1.0-4:amd64 rather than change libgssdp-1.0-3:amd64 
Investigating (9) libgda-5.0-4 [ amd64 ] < 5.2.2-1 -> 5.2.4-1ubuntu1 > ( universe/libs ) 
Broken libgda-5.0-4:amd64 Depends on libsoup2.4-1 [ amd64 ] < 2.52.2-1ubuntu0.1 > ( libs ) (>= 2.4.1) 
  Considering libsoup2.4-1:amd64 234 as a solution to libgda-5.0-4:amd64 1 
  Re-Instated libgda-5.0-common:amd64 
    Reinst Failed because of libsoup2.4-1:amd64 
  Removing libgda-5.0-4:amd64 rather than change libsoup2.4-1:amd64 
Investigating (9) gir1.2-totem-plparser-1.0 [ amd64 ] < 3.10.2-0ubuntu1 -> 3.10.6-1ubuntu1 > ( libs ) 
Broken gir1.2-totem-plparser-1.0:amd64 Depends on libtotem-plparser18 [ amd64 ] < 3.10.2-0ubuntu1 -> 3.10.6-1ubuntu1 > ( libs ) (>= 3.10.0) 
  Considering libtotem-plparser18:amd64 234 as a solution to gir1.2-totem-plparser-1.0:amd64 1 
    Reinst Failed because of libtotem-plparser18:amd64 
  Removing gir1.2-totem-plparser-1.0:amd64 rather than change libtotem-plparser18:amd64 
Investigating (9) libdmapsharing-3.0-2 [ amd64 ] < 2.9.24-0ubuntu1 -> 2.9.34-1 > ( libs ) 
Broken libdmapsharing-3.0-2:amd64 Depends on libsoup2.4-1 [ amd64 ] < 2.52.2-1ubuntu0.1 > ( libs ) (>= 2.32) 
  Considering libsoup2.4-1:amd64 234 as a solution to libdmapsharing-3.0-2:amd64 1 
    Reinst Failed because of libsoup2.4-1:amd64 
  Removing libdmapsharing-3.0-2:amd64 rather than change libsoup2.4-1:amd64 
Investigating (9) unity-scope-home [ amd64 ] < 6.8.2+14.04.20131029.1-0ubuntu1 -> 6.8.2+16.04.20160212.1-0ubuntu1 > ( gnome ) 
Broken unity-scope-home:amd64 Depends on libsoup-gnome2.4-1 [ amd64 ] < 2.44.2-1ubuntu2.1 -> 2.52.2-1ubuntu0.1 > ( libs ) (>= 2.27.4) 
  Considering libsoup-gnome2.4-1:amd64 234 as a solution to unity-scope-home:amd64 1 
    Reinst Failed because of libsoup-gnome2.4-1:amd64 
  Removing unity-scope-home:amd64 rather than change libsoup-gnome2.4-1:amd64 
Investigating (9) gnome-video-effects [ amd64 ] < 0.4.1-0ubuntu1 -> 0.4.1-3ubuntu1 > ( gnome ) 
Broken gnome-video-effects:amd64 Depends on gstreamer1.0-plugins-good [ amd64 ] < 1.8.2-1ubuntu0.3 > ( libs ) 
  Considering gstreamer1.0-plugins-good:amd64 234 as a solution to gnome-video-effects:amd64 1 
    Reinst Failed because of gstreamer1.0-plugins-good:amd64 
  Removing gnome-video-effects:amd64 rather than change gstreamer1.0-plugins-good:amd64 
Investigating (9) shotwell [ amd64 ] < 0.18.0-0ubuntu4.4 -> 0.22.0+git20160108.r1.f2fb1f7-0ubuntu1 > ( gnome ) 
Broken shotwell:amd64 Depends on librest-0.7-0 [ amd64 ] < 0.7.90-0ubuntu1 -> 0.7.93-1 > ( libs ) (>= 0.7) 
  Considering librest-0.7-0:amd64 234 as a solution to shotwell:amd64 1 
    Reinst Failed because of librest-0.7-0:amd64 
  Removing shotwell:amd64 rather than change librest-0.7-0:amd64 
Investigating (9) friends-dispatcher [ amd64 ] < 0.2.0+14.04.20140217.1-0ubuntu1 > ( misc ) 
Broken friends-dispatcher:amd64 Depends on gir1.2-ebookcontacts-1.2 [ amd64 ] < 3.10.4-0ubuntu1.5 -> 3.18.5-1ubuntu1 > ( introspection ) (>= 3.8) 
  Considering gir1.2-ebookcontacts-1.2:amd64 234 as a solution to friends-dispatcher:amd64 1 
  Removing friends-dispatcher:amd64 rather than change gir1.2-ebookcontacts-1.2:amd64 
Investigating (9) gdm [ amd64 ] < 3.10.0.1-0ubuntu3.2 -> 3.18.3-0ubuntu2 > ( universe/gnome ) 
Broken gdm:amd64 Depends on gdm3 [ amd64 ] < none -> 3.18.3-0ubuntu2 > ( universe/gnome ) 
  Considering gdm3:amd64 3 as a solution to gdm:amd64 1 
    Reinst Failed because of gnome-settings-daemon:amd64 
    Reinst Failed because of gdm3:amd64 
  Removing gdm:amd64 rather than change gdm3:amd64 
Investigating (9) unity [ amd64 ] < 7.2.6+14.04.20160408-0ubuntu1 -> 7.4.0+16.04.20160906-0ubuntu1 > ( gnome ) 
Broken unity:amd64 Depends on libappstream-glib8 [ amd64 ] < 0.5.13-1ubuntu4 > ( libs ) (>= 0.5.1) 
  Considering libappstream-glib8:amd64 234 as a solution to unity:amd64 1 
    Reinst Failed because of libappstream-glib8:amd64 
  Removing unity:amd64 rather than change libappstream-glib8:amd64 
Investigating (9) rhythmbox-plugin-magnatune [ amd64 ] < 3.3-1ubuntu7 > ( universe/gnome ) 
Broken rhythmbox-plugin-magnatune:amd64 Depends on rhythmbox [ amd64 ] < 3.0.2-0ubuntu2 -> 3.3-1ubuntu7 > ( gnome ) (= 3.3-1ubuntu7) 
  Considering rhythmbox:amd64 234 as a solution to rhythmbox-plugin-magnatune:amd64 1 
  Removing rhythmbox-plugin-magnatune:amd64 rather than change rhythmbox:amd64 
Investigating (9) mutter [ amd64 ] < 3.18.3-0ubuntu2 > ( universe/x11 ) 
Broken mutter:amd64 Depends on zenity [ amd64 ] < 3.8.0-1ubuntu1 -> 3.18.1.1-1ubuntu2 > ( gnome ) 
  Considering zenity:amd64 234 as a solution to mutter:amd64 1 
  Removing mutter:amd64 rather than change zenity:amd64 
Investigating (9) gir1.2-ebook-1.2 [ amd64 ] < 3.10.4-0ubuntu1.5 -> 3.18.5-1ubuntu1 > ( libs ) 
Broken gir1.2-ebook-1.2:amd64 Depends on gir1.2-ebookcontacts-1.2 [ amd64 ] < 3.10.4-0ubuntu1.5 -> 3.18.5-1ubuntu1 > ( introspection ) (= 3.10.4-0ubuntu1.5) 
  Considering gir1.2-ebookcontacts-1.2:amd64 234 as a solution to gir1.2-ebook-1.2:amd64 0 
    Reinst Failed because of gir1.2-ebookcontacts-1.2:amd64 
  Removing gir1.2-ebook-1.2:amd64 rather than change gir1.2-ebookcontacts-1.2:amd64 
Investigating (9) darktable [ amd64 ] < 1.4-2 -> 2.0.3-1 > ( universe/graphics ) 
Broken darktable:amd64 Depends on libsoup2.4-1 [ amd64 ] < 2.52.2-1ubuntu0.1 > ( libs ) (>= 2.4.0) 
  Considering libsoup2.4-1:amd64 234 as a solution to darktable:amd64 0 
  Re-Instated libgraphicsmagick-q16-3:amd64 
    Reinst Failed because of libsoup2.4-1:amd64 
    Reinst Failed because of libosmgpsmap-1.0-1:amd64 
  Removing darktable:amd64 rather than change libsoup2.4-1:amd64 
Investigating (9) gnome-web-photo [ amd64 ] < 0.10.6-1 > ( universe/gnome ) 
Broken gnome-web-photo:amd64 Depends on libsoup2.4-1 [ amd64 ] < 2.52.2-1ubuntu0.1 > ( libs ) (>= 2.24.3) 
  Considering libsoup2.4-1:amd64 234 as a solution to gnome-web-photo:amd64 0 
  Removing gnome-web-photo:amd64 rather than change libsoup2.4-1:amd64 
Investigating (9) libpurple-dev [ amd64 ] < 1:2.10.9-0ubuntu3.3 -> 1:2.10.12-0ubuntu5.1 > ( universe/libdevel ) 
Broken libpurple-dev:amd64 Depends on libpurple0 [ amd64 ] < 1:2.10.9-0ubuntu3.3 -> 1:2.10.12-0ubuntu5.1 > ( universe/net ) (>= 1:2.10.12) 
  Considering libpurple0:amd64 234 as a solution to libpurple-dev:amd64 0 
    Reinst Failed because of libpurple0:amd64 
  Removing libpurple-dev:amd64 rather than change libpurple0:amd64 
Investigating (9) libqt5multimedia5-plugins [ amd64 ] < none -> 5.5.1-4ubuntu2 > ( libs ) 
Broken libqt5multimedia5-plugins:amd64 Depends on libqgsttools-p1 [ amd64 ] < none -> 5.5.1-4ubuntu2 > ( libs ) (>= 5.5.1) 
  Considering libqgsttools-p1:amd64 0 as a solution to libqt5multimedia5-plugins:amd64 0 
  Holding Back libqt5multimedia5-plugins:amd64 rather than change libqgsttools-p1:amd64 
Investigating (9) ubuntu-docs [ amd64 ] < 14.04.5 -> 16.04.4 > ( text ) 
Broken ubuntu-docs:amd64 Depends on yelp [ amd64 ] < 3.10.2-0ubuntu1 -> 3.18.1-1ubuntu4 > ( gnome ) 
  Considering yelp:amd64 234 as a solution to ubuntu-docs:amd64 0 
    Reinst Failed because of yelp:amd64 
  Removing ubuntu-docs:amd64 rather than change yelp:amd64 
Investigating (9) indicator-network [ amd64 ] < none -> 0.7.1+16.04.20160406.1-0ubuntu1 > ( universe/gnome ) 
Broken indicator-network:amd64 Depends on network-manager [ amd64 ] < 0.9.8.8-0ubuntu7.3 -> 1.2.2-0ubuntu0.16.04.3 > ( net ) 
  Considering network-manager:amd64 234 as a solution to indicator-network:amd64 0 
  Holding Back indicator-network:amd64 rather than change network-manager:amd64 
Investigating (9) rhythmbox-plugin-cdrecorder [ amd64 ] < 3.0.2-0ubuntu2 -> 3.3-1ubuntu7 > ( universe/gnome ) 
Broken rhythmbox-plugin-cdrecorder:amd64 Depends on libbrasero-media3-1 [ amd64 ] < 3.10.0-0ubuntu1 -> 3.12.1-1ubuntu3~16.04 > ( universe/libs ) (>= 3.0.0) 
  Considering libbrasero-media3-1:amd64 234 as a solution to rhythmbox-plugin-cdrecorder:amd64 0 
    Reinst Failed because of libbrasero-media3-1:amd64 
  Removing rhythmbox-plugin-cdrecorder:amd64 rather than change libbrasero-media3-1:amd64 
Investigating (9) banshee [ amd64 ] < 2.9.0+really2.6.2-2ubuntu2.1 -> 2.9.0+really2.6.2-7ubuntu2 > ( universe/sound ) 
Broken banshee:amd64 Depends on libsoup-gnome2.4-1 [ amd64 ] < 2.44.2-1ubuntu2.1 -> 2.52.2-1ubuntu0.1 > ( libs ) (>= 2.27.4) 
  Considering libsoup-gnome2.4-1:amd64 234 as a solution to banshee:amd64 0 
    Reinst Failed because of libsoup-gnome2.4-1:amd64 
  Removing banshee:amd64 rather than change libsoup-gnome2.4-1:amd64 
Investigating (9) libedata-book-1.2-20 [ amd64 ] < 3.10.4-0ubuntu1.5 > ( libs ) 
Broken libedata-book-1.2-20:amd64 Depends on libebackend-1.2-7 [ amd64 ] < 3.10.4-0ubuntu1.5 > ( libs ) (>= 3.7.90) 
  Considering libebackend-1.2-7:amd64 234 as a solution to libedata-book-1.2-20:amd64 0 
  Removing libedata-book-1.2-20:amd64 rather than change libebackend-1.2-7:amd64 
Investigating (9) gnome-media [ amd64 ] < 3.4.0-1ubuntu2 > ( gnome ) 
Broken gnome-media:amd64 Depends on gstreamer0.10-plugins-good [ amd64 ] < 0.10.31-3+nmu1ubuntu5.2 -> 0.10.31-3+nmu4ubuntu2.16.04.2 > ( universe/libs ) 
  Considering gstreamer0.10-plugins-good:amd64 234 as a solution to gnome-media:amd64 0 
  Removing gnome-media:amd64 rather than change gstreamer0.10-plugins-good:amd64 
Investigating (9) unity-scope-musicstores [ amd64 ] < 6.9.0+14.04.20151120.2-0ubuntu1 > ( gnome ) 
Broken unity-scope-musicstores:amd64 Depends on libsoup2.4-1 [ amd64 ] < 2.52.2-1ubuntu0.1 > ( libs ) (>= 2.4.0) 
  Considering libsoup2.4-1:amd64 234 as a solution to unity-scope-musicstores:amd64 0 
  Removing unity-scope-musicstores:amd64 rather than change libsoup2.4-1:amd64 
Investigating (9) qml-module-qtmultimedia [ amd64 ] < none -> 5.5.1-4ubuntu2 > ( libs ) 
Broken qml-module-qtmultimedia:amd64 Depends on libqt5multimedia5-plugins [ amd64 ] < none -> 5.5.1-4ubuntu2 > ( libs ) 
  Considering libqt5multimedia5-plugins:amd64 0 as a solution to qml-module-qtmultimedia:amd64 0 
  Holding Back qml-module-qtmultimedia:amd64 rather than change libqt5multimedia5-plugins:amd64 
Investigating (9) subtitleeditor [ amd64 ] < 0.41.0-2ubuntu1 -> 0.52.1-2 > ( universe/x11 ) 
Broken subtitleeditor:amd64 Depends on gstreamer1.0-plugins-good [ amd64 ] < 1.8.2-1ubuntu0.3 > ( libs ) 
  Considering gstreamer1.0-plugins-good:amd64 234 as a solution to subtitleeditor:amd64 0 
    Reinst Failed because of gstreamer1.0-plugins-good:amd64 
  Removing subtitleeditor:amd64 rather than change gstreamer1.0-plugins-good:amd64 
Investigating (9) xiphos [ amd64 ] < 3.1.5+dfsg-1build3 -> 4.0.4+dfsg1-1 > ( universe/gnome ) 
Broken xiphos:amd64 Depends on libwebkitgtk-3.0-0 [ amd64 ] < 2.4.10-0ubuntu0.14.04.1 -> 2.4.11-0ubuntu0.1 > ( universe/libs ) (>= 1.5.1) 
  Considering libwebkitgtk-3.0-0:amd64 234 as a solution to xiphos:amd64 0 
  Removing xiphos:amd64 rather than change libwebkitgtk-3.0-0:amd64 
Investigating (9) libges-1.0-0 [ amd64 ] < 1.2.0-2 -> 1.6.2-1 > ( universe/libs ) 
Broken libges-1.0-0:amd64 Depends on gstreamer1.0-plugins-good [ amd64 ] < 1.8.2-1ubuntu0.3 > ( libs ) (>= 1.2.3) 
  Considering gstreamer1.0-plugins-good:amd64 234 as a solution to libges-1.0-0:amd64 0 
  Re-Instated gstreamer1.0-x:amd64 
    Reinst Failed because of gstreamer1.0-plugins-good:amd64 
  Removing libges-1.0-0:amd64 rather than change gstreamer1.0-plugins-good:amd64 
Investigating (9) banshee-extension-soundmenu [ amd64 ] < 2.9.0+really2.6.2-2ubuntu2.1 -> 2.9.0+really2.6.2-7ubuntu2 > ( universe/gnome ) 
Broken banshee-extension-soundmenu:amd64 Depends on banshee [ amd64 ] < 2.9.0+really2.6.2-2ubuntu2.1 -> 2.9.0+really2.6.2-7ubuntu2 > ( universe/sound ) (>= 2.9.0+really2.6.2) 
  Considering banshee:amd64 234 as a solution to banshee-extension-soundmenu:amd64 0 
    Reinst Failed because of banshee:amd64 
  Removing banshee-extension-soundmenu:amd64 rather than change banshee:amd64 
Investigating (9) ubuntu-sso-client-qt [ amd64 ] < 13.10-0ubuntu6 -> 13.10-0ubuntu11 > ( universe/python ) 
Broken ubuntu-sso-client-qt:amd64 Depends on python-ubuntu-sso-client [ amd64 ] < 13.10-0ubuntu6 -> 13.10-0ubuntu11 > ( universe/python ) (= 13.10-0ubuntu6) 
  Considering python-ubuntu-sso-client:amd64 234 as a solution to ubuntu-sso-client-qt:amd64 0 
    Reinst Failed because of python-ubuntu-sso-client:amd64 
  Removing ubuntu-sso-client-qt:amd64 rather than change python-ubuntu-sso-client:amd64 
Investigating (9) rhythmbox-mozilla [ amd64 ] < 3.0.2-0ubuntu2 -> 3.3-1ubuntu7 > ( universe/web ) 
Broken rhythmbox-mozilla:amd64 Depends on rhythmbox [ amd64 ] < 3.0.2-0ubuntu2 -> 3.3-1ubuntu7 > ( gnome ) (= 3.3-1ubuntu7) 
  Considering rhythmbox:amd64 234 as a solution to rhythmbox-mozilla:amd64 0 
    Reinst Failed because of rhythmbox:amd64 
  Removing rhythmbox-mozilla:amd64 rather than change rhythmbox:amd64 
Investigating (9) apturl [ amd64 ] < 0.5.2ubuntu4 -> 0.5.2ubuntu11.1 > ( admin ) 
Broken apturl:amd64 Depends on gir1.2-webkit-3.0 [ amd64 ] < 2.4.10-0ubuntu0.14.04.1 -> 2.4.11-0ubuntu0.1 > ( universe/libs ) 
  Considering gir1.2-webkit-3.0:amd64 234 as a solution to apturl:amd64 0 
  Re-Instated apturl-common:amd64 
    Reinst Failed because of gir1.2-webkit2-4.0:amd64 
  Removing apturl:amd64 rather than change gir1.2-webkit-3.0:amd64 
Investigating (9) libgdata13 [ amd64 ] < 0.14.1-1 > ( libs ) 
Broken libgdata13:amd64 Depends on libsoup2.4-1 [ amd64 ] < 2.52.2-1ubuntu0.1 > ( libs ) (>= 2.41.90) 
  Considering libsoup2.4-1:amd64 234 as a solution to libgdata13:amd64 0 
  Removing libgdata13:amd64 rather than change libsoup2.4-1:amd64 
Investigating (9) metacity [ amd64 ] < 1:2.34.13-0ubuntu4.1 -> 1:3.18.7-0ubuntu0.2 > ( x11 ) 
Broken metacity:amd64 Depends on zenity [ amd64 ] < 3.8.0-1ubuntu1 -> 3.18.1.1-1ubuntu2 > ( gnome ) 
  Considering zenity:amd64 234 as a solution to metacity:amd64 0 
  Removing metacity:amd64 rather than change zenity:amd64 
Investigating (9) boot-sav [ amd64 ] < 3.199~ppa40~precise > ( admin ) 
Broken boot-sav:amd64 Depends on zenity [ amd64 ] < 3.8.0-1ubuntu1 -> 3.18.1.1-1ubuntu2 > ( gnome ) 
  Considering zenity:amd64 234 as a solution to boot-sav:amd64 0 
  Removing boot-sav:amd64 rather than change zenity:amd64 
Investigating (9) libfriends0 [ amd64 ] < 0.1.2+14.04.20131108.1-0ubuntu1 > ( libs ) 
Broken libfriends0:amd64 Depends on friends-dispatcher [ amd64 ] < 0.2.0+14.04.20140217.1-0ubuntu1 > ( misc ) 
  Considering friends-dispatcher:amd64 234 as a solution to libfriends0:amd64 -1 
  Removing libfriends0:amd64 rather than change friends-dispatcher:amd64 
Investigating (9) sound-juicer [ amd64 ] < 3.5.0-0ubuntu1 -> 3.18.1-1 > ( universe/gnome ) 
Broken sound-juicer:amd64 Depends on libbrasero-media3-1 [ amd64 ] < 3.10.0-0ubuntu1 -> 3.12.1-1ubuntu3~16.04 > ( universe/libs ) (>= 2.91.91) 
  Considering libbrasero-media3-1:amd64 234 as a solution to sound-juicer:amd64 -1 
    Reinst Failed because of gstreamer1.0-plugins-good:amd64 
  Removing sound-juicer:amd64 rather than change libbrasero-media3-1:amd64 
Investigating (9) gufw [ amd64 ] < 14.04.2-0ubuntu1.2 -> 16.04.1-0ubuntu1.1 > ( universe/admin ) 
Broken gufw:amd64 Depends on gir1.2-webkit-3.0 [ amd64 ] < 2.4.10-0ubuntu0.14.04.1 -> 2.4.11-0ubuntu0.1 > ( universe/libs ) 
  Considering gir1.2-webkit-3.0:amd64 234 as a solution to gufw:amd64 -1 
    Reinst Failed because of gir1.2-webkit-3.0:amd64 
  Removing gufw:amd64 rather than change gir1.2-webkit-3.0:amd64 
Investigating (9) boot-sav-extra [ amd64 ] < 3.199~ppa40~precise > ( admin ) 
Broken boot-sav-extra:amd64 Depends on boot-sav [ amd64 ] < 3.199~ppa40~precise > ( admin ) 
  Considering boot-sav:amd64 234 as a solution to boot-sav-extra:amd64 -1 
  Removing boot-sav-extra:amd64 rather than change boot-sav:amd64 
Investigating (9) gthumb [ amd64 ] < 3:3.3.1.is.3.2.7-0ubuntu1 -> 3:3.4.3-1 > ( universe/gnome ) 
Broken gthumb:amd64 Depends on libsoup-gnome2.4-1 [ amd64 ] < 2.44.2-1ubuntu2.1 -> 2.52.2-1ubuntu0.1 > ( libs ) (>= 2.36) 
  Considering libsoup-gnome2.4-1:amd64 234 as a solution to gthumb:amd64 -1 
  Re-Instated gthumb-data:amd64 
    Reinst Failed because of libsoup2.4-1:amd64 
  Removing gthumb:amd64 rather than change libsoup-gnome2.4-1:amd64 
Investigating (9) libfarstream-0.1-0 [ amd64 ] < 0.1.2-1ubuntu3 -> 0.1.2-3ubuntu1 > ( universe/libs ) 
Broken libfarstream-0.1-0:amd64 Depends on gstreamer0.10-plugins-good [ amd64 ] < 0.10.31-3+nmu1ubuntu5.2 -> 0.10.31-3+nmu4ubuntu2.16.04.2 > ( universe/libs ) (>= 0.10.29) 
  Considering gstreamer0.10-plugins-good:amd64 234 as a solution to libfarstream-0.1-0:amd64 -1 
    Reinst Failed because of gstreamer0.10-plugins-good:amd64 
  Removing libfarstream-0.1-0:amd64 rather than change gstreamer0.10-plugins-good:amd64 
Investigating (9) gnome-mplayer [ amd64 ] < 1.0.8-2 -> 1.0.9-3ubuntu1 > ( universe/graphics ) 
Broken gnome-mplayer:amd64 Depends on libgda-5.0-4 [ amd64 ] < 5.2.2-1 -> 5.2.4-1ubuntu1 > ( universe/libs ) (>= 5.0.2) 
  Considering libgda-5.0-4:amd64 234 as a solution to gnome-mplayer:amd64 -1 
    Reinst Failed because of libgda-5.0-4:amd64 
  Removing gnome-mplayer:amd64 rather than change libgda-5.0-4:amd64 
Investigating (9) hardinfo [ amd64 ] < 0.5.1-1.2ubuntu4 -> 0.5.1-1.4ubuntu1 > ( universe/x11 ) 
Broken hardinfo:amd64 Depends on libsoup2.4-1 [ amd64 ] < 2.52.2-1ubuntu0.1 > ( libs ) (>= 2.4.0) 
  Considering libsoup2.4-1:amd64 234 as a solution to hardinfo:amd64 -1 
    Reinst Failed because of libsoup2.4-1:amd64 
  Removing hardinfo:amd64 rather than change libsoup2.4-1:amd64 
Investigating (9) pitivi [ amd64 ] < 0.93-3ubuntu0.1 -> 0.95-1 > ( universe/gnome ) 
Broken pitivi:amd64 Depends on gstreamer1.0-plugins-good [ amd64 ] < 1.8.2-1ubuntu0.3 > ( libs ) (>= 1.2.3) 
  Considering gstreamer1.0-plugins-good:amd64 234 as a solution to pitivi:amd64 -1 
  Re-Instated gir1.2-gstreamer-1.0:amd64 
  Re-Instated gir1.2-gst-plugins-base-1.0:amd64 
    Reinst Failed because of libges-1.0-0:amd64 
    Reinst Failed because of gir1.2-ges-1.0:amd64 
  Removing pitivi:amd64 rather than change gstreamer1.0-plugins-good:amd64 
Investigating (9) quodlibet [ amd64 ] < 3.0.2-3 -> 3.5.3-1 > ( universe/sound ) 
Broken quodlibet:amd64 Depends on gstreamer1.0-plugins-good [ amd64 ] < 1.8.2-1ubuntu0.3 > ( libs ) 
  Considering gstreamer1.0-plugins-good:amd64 234 as a solution to quodlibet:amd64 -1 
  Re-Instated fonts-font-awesome:amd64 
  Re-Instated fonts-lato:amd64 
  Re-Instated libjs-modernizr:amd64 
  Re-Instated sphinx-rtd-theme-common:amd64 
  Re-Instated exfalso:amd64 
    Reinst Failed because of gstreamer1.0-plugins-good:amd64 
  Removing quodlibet:amd64 rather than change gstreamer1.0-plugins-good:amd64 
Investigating (9) deja-dup-backend-gvfs [ amd64 ] < 30.0-0ubuntu4.1 -> 34.2-0ubuntu1.1 > ( universe/utils ) 
Broken deja-dup-backend-gvfs:amd64 Depends on gvfs-backends [ amd64 ] < 1.20.3-0ubuntu1.2 -> 1.28.2-1ubuntu1~16.04.1 > ( libs ) 
  Considering gvfs-backends:amd64 234 as a solution to deja-dup-backend-gvfs:amd64 -1 
    Reinst Failed because of gvfs-backends:amd64 
  Removing deja-dup-backend-gvfs:amd64 rather than change gvfs-backends:amd64 
Investigating (9) soundconverter [ amd64 ] < 2.1.5-1~getdeb1 -> 3.0.0~alpha1+git20151209-1 > ( universe/sound ) 
Broken soundconverter:amd64 Depends on gstreamer0.10-plugins-good [ amd64 ] < 0.10.31-3+nmu1ubuntu5.2 -> 0.10.31-3+nmu4ubuntu2.16.04.2 > ( universe/libs ) 
  Considering gstreamer0.10-plugins-good:amd64 234 as a solution to soundconverter:amd64 -1 
    Reinst Failed because of gstreamer1.0-plugins-good:amd64 
  Removing soundconverter:amd64 rather than change gstreamer0.10-plugins-good:amd64 
Investigating (9) xiphos-dbg [ amd64 ] < 3.1.5+dfsg-1build3 -> 4.0.4+dfsg1-1 > ( universe/debug ) 
Broken xiphos-dbg:amd64 Depends on xiphos [ amd64 ] < 3.1.5+dfsg-1build3 -> 4.0.4+dfsg1-1 > ( universe/gnome ) (= 4.0.4+dfsg1-1) 
  Considering xiphos:amd64 234 as a solution to xiphos-dbg:amd64 -1 
  Removing xiphos-dbg:amd64 rather than change xiphos:amd64 
Investigating (9) evolution-indicator [ amd64 ] < 0.2.20-0ubuntu15 -> 0.2.20-0ubuntu23 > ( universe/gnome ) 
Broken evolution-indicator:amd64 Depends on libedataserver-1.2-18 [ amd64 ] < 3.10.4-0ubuntu1.5 > ( libs ) (>= 3.5.91) 
  Considering libedataserver-1.2-18:amd64 234 as a solution to evolution-indicator:amd64 -1 
    Reinst Failed because of libedataserver-1.2-21:amd64 
  Removing evolution-indicator:amd64 rather than change libedataserver-1.2-18:amd64 
Investigating (9) glabels [ amd64 ] < 3.2.1-1~getdeb1 -> 3.2.1-2build1 > ( universe/gnome ) 
Broken glabels:amd64 Depends on libebook-1.2-14 [ amd64 ] < 3.10.4-0ubuntu1.5 > ( libs ) (>= 3.5.91) 
  Considering libebook-1.2-14:amd64 234 as a solution to glabels:amd64 -1 
  Re-Instated glabels-data:amd64 
    Reinst Failed because of libebook-1.2-16:amd64 
  Removing glabels:amd64 rather than change libebook-1.2-14:amd64 
Investigating (9) python-webkit [ amd64 ] < 1.1.8-3ubuntu2 -> 1.1.8-3.1 > ( universe/python ) 
Broken python-webkit:amd64 Depends on libwebkitgtk-1.0-0 [ amd64 ] < 2.4.10-0ubuntu0.14.04.1 -> 2.4.11-0ubuntu0.1 > ( universe/libs ) (>= 1.3.10) 
  Considering libwebkitgtk-1.0-0:amd64 234 as a solution to python-webkit:amd64 -1 
    Reinst Failed because of libwebkitgtk-1.0-0:amd64 
  Removing python-webkit:amd64 rather than change libwebkitgtk-1.0-0:amd64 
Investigating (9) darktable-dbg [ amd64 ] < 1.4-2 > ( debug ) 
Broken darktable-dbg:amd64 Depends on darktable [ amd64 ] < 1.4-2 -> 2.0.3-1 > ( universe/graphics ) (= 1.4-2) 
  Considering darktable:amd64 234 as a solution to darktable-dbg:amd64 -2 
  Removing darktable-dbg:amd64 rather than change darktable:amd64 
Investigating (9) librhythmbox-core8 [ amd64 ] < 3.0.2-0ubuntu2 > ( libs ) 
Broken librhythmbox-core8:amd64 Depends on libsoup2.4-1 [ amd64 ] < 2.52.2-1ubuntu0.1 > ( libs ) (>= 2.33.92) 
  Considering libsoup2.4-1:amd64 234 as a solution to librhythmbox-core8:amd64 -2 
  Removing librhythmbox-core8:amd64 rather than change libsoup2.4-1:amd64 
Investigating (9) libthumbnailer0 [ amd64 ] < 1.1+14.04.20150205-0ubuntu1 > ( libdevel ) 
Broken libthumbnailer0:amd64 Depends on libsoup2.4-1 [ amd64 ] < 2.52.2-1ubuntu0.1 > ( libs ) (>= 2.4.0) 
  Considering libsoup2.4-1:amd64 234 as a solution to libthumbnailer0:amd64 -2 
  Removing libthumbnailer0:amd64 rather than change libsoup2.4-1:amd64 
Investigating (9) os-uninstaller [ amd64 ] < 3.199~ppa40~precise > ( admin ) 
Broken os-uninstaller:amd64 Depends on boot-sav [ amd64 ] < 3.199~ppa40~precise > ( admin ) 
  Considering boot-sav:amd64 234 as a solution to os-uninstaller:amd64 -2 
  Removing os-uninstaller:amd64 rather than change boot-sav:amd64 
Investigating (9) unity-lens-friends [ amd64 ] < 0.1.3+14.04.20140317-0ubuntu1 > ( misc ) 
Broken unity-lens-friends:amd64 Depends on libfriends0 [ amd64 ] < 0.1.2+14.04.20131108.1-0ubuntu1 > ( libs ) (>= 0.1.0) 
  Considering libfriends0:amd64 234 as a solution to unity-lens-friends:amd64 -2 
  Removing unity-lens-friends:amd64 rather than change libfriends0:amd64 
Investigating (9) exaile [ amd64 ] < 3.3.2-1 > ( sound ) 
Broken exaile:amd64 Depends on gstreamer0.10-plugins-good [ amd64 ] < 0.10.31-3+nmu1ubuntu5.2 -> 0.10.31-3+nmu4ubuntu2.16.04.2 > ( universe/libs ) 
  Considering gstreamer0.10-plugins-good:amd64 234 as a solution to exaile:amd64 -2 
  Removing exaile:amd64 rather than change gstreamer0.10-plugins-good:amd64 
Done 
 
Broken packages  
 
Your system contains broken packages that couldn't be fixed with this  
software. Please fix them first using synaptic or apt-get before  
proceeding.  
 
 
Preparing the upgrade failed  
 
Preparing the system for the upgrade failed so a bug reporting  
process is being started.  
 

 === Command terminated with exit status 1 (Mon Jan  9 18:24:43 2017) ===
```

---

### Post by cscj01 on 2017-01-12
Bump

---

### Post by oldfred on 2017-01-12
Have you checked your sources.list. One user in another recent thread had mixed versions.

 Check sources & ppas
find /etc/apt/  -name '*.list' -exec bash -c 'echo -e "\n$1\n"; cat -n "$1"' _ '{}' \;

---

### Post by cscj01 on 2017-01-12
```
find /etc/apt/ -name '*.list' -exec bash -c 'echo -e "\n$1\n"; cat -n "$1"' _ '{}' \;

/etc/apt/sources.list

     1	deb http://archive.ubuntu.com/ubuntu trusty universe main restricted multiverse
     2	deb http://security.ubuntu.com/ubuntu/ trusty-security universe main multiverse restricted
     3	deb http://archive.ubuntu.com/ubuntu trusty-updates universe main multiverse restricted
     4	# deb http://debian.tagancha.org/debian/ trusty main # disabled on upgrade to trusty
     5	# deb-src http://debian.tagancha.org/debian/ trusty main # disabled on upgrade to trusty
     6	deb http://archive.ubuntu.com/ubuntu trusty-backports universe main multiverse restricted
     7	deb http://archive.canonical.com/ trusty partner
     8	deb-src http://archive.canonical.com/ trusty partner
     9	# deb http://debian.scribus.net/debian/ trusty main
    10	# deb-src http://debian.scribus.net/debian/ trusty main # disabled on upgrade to trusty
    11	
    12	
    13	deb http://repository.spotify.com stable non-free
    14	# deb-src http://repository.spotify.com stable non-free # disabled on upgrade to trusty
    15	deb http://ppa.launchpad.net/pmjdebruijn/darktable-release/ubuntu trusty main
    16	# deb-src http://ppa.launchpad.net/pmjdebruijn/darktable-release/ubuntu trusty source
    17	deb http://download.virtualbox.org/virtualbox/debian trusty contrib
    18	# deb-src http://download.virtualbox.org/virtualbox/debian trusty contrib
    19	# deb http://ppa.launchpad.net/otto-kesselgulasch/gimp/ubuntu trusty main
    20	# deb-src http://ppa.launchpad.net/otto-kesselgulasch/gimp/ubuntu trusty main
    21	# deb http://archive.getdeb.net/ubuntu trusty-getdeb apps
    22	# deb-src http://archive.getdeb.net/ubuntu trusty-getdeb apps
    23	deb http://ppa.launchpad.net/unit193/crosswire/ubuntu trusty main
    24	deb-src http://ppa.launchpad.net/unit193/crosswire/ubuntu trusty main
    25	# deb http://www.openprinting.org/download/printdriver/debian/ lsb3.2 main
    26	# deb-src http://www.openprinting.org/download/printdriver/debian/ lsb3.2 main
    27	deb http://ppa.launchpad.net/linuxgndu/sqlitebrowser/ubuntu trusty main
    28	deb-src http://ppa.launchpad.net/linuxgndu/sqlitebrowser/ubuntu trusty main

/etc/apt/sources.list.d/otto-kesselgulasch-gimp-edge-trusty.list

     1	deb http://ppa.launchpad.net/otto-kesselgulasch/gimp-edge/ubuntu trusty main
     2	# deb-src http://ppa.launchpad.net/otto-kesselgulasch/gimp-edge/ubuntu trusty main

/etc/apt/sources.list.d/pmjdebruijn-ufraw-testing-trusty.list


/etc/apt/sources.list.d/nilarimogard-webupd8-trusty.list

     1	deb http://ppa.launchpad.net/nilarimogard/webupd8/ubuntu trusty main
     2	deb-src http://ppa.launchpad.net/nilarimogard/webupd8/ubuntu trusty main

/etc/apt/sources.list.d/tualatrix-ppa-trusty.list

     1	deb http://ppa.launchpad.net/tualatrix/ppa/ubuntu trusty main
     2	# deb-src http://ppa.launchpad.net/tualatrix/ppa/ubuntu trusty main

/etc/apt/sources.list.d/upubuntu-com-finance-precise.list


/etc/apt/sources.list.d/linuxgndu-sqlitebrowser-trusty.list

     1	# deb-src http://ppa.launchpad.net/linuxgndu/sqlitebrowser/ubuntu trusty main

/etc/apt/sources.list.d/spotify.list


/etc/apt/sources.list.d/xorg-edgers-ppa-trusty.list

     1	deb http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu trusty main
     2	# deb-src http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu trusty main

/etc/apt/sources.list.d/audacity-team-daily-precise.list


/etc/apt/sources.list.d/ubuntuhandbook1-ppa-trusty.list

     1	deb http://ppa.launchpad.net/ubuntuhandbook1/ppa/ubuntu trusty main
     2	# deb-src http://ppa.launchpad.net/ubuntuhandbook1/ppa/ubuntu trusty main

/etc/apt/sources.list.d/hugin-hugin-builds-trusty.list

     1	deb http://ppa.launchpad.net/hugin/hugin-builds/ubuntu trusty main
     2	# deb-src http://ppa.launchpad.net/hugin/hugin-builds/ubuntu trusty main

/etc/apt/sources.list.d/lazka-ppa-trusty.list

     1	deb http://ppa.launchpad.net/lazka/ppa/ubuntu trusty main
     2	# deb-src http://ppa.launchpad.net/lazka/ppa/ubuntu trusty main

/etc/apt/sources.list.d/tualatrix-ppa-precise.list


/etc/apt/sources.list.d/intellinuxgraphics.list


/etc/apt/sources.list.d/hugin-hugin-builds-precise.list
```This is after I restored my backup to 14.04.5.  I had to restore the backup to get some work done.  I used ppa-purge on all the PPA's listed in /etc/apt/sources.list before beginning the upgrade.  However, I did not know there were other sources in /etc/apt/sources.list.d.  Obviously, I have some entries in/etc/apt/sources.list.d that should not be there.  Should I get rid of those before trying to upgrade?  BTW, this thread has the wrong title.  I initially created it after a bad upgrade attempt from 14.04 to 16.04.  However, one of the respondents suggested I could probably do the upgrade and clear up the issues after the upgrade.  As you can tell from the thread, I have been unsuccessful in my attempts.  So how should I proceed to have a successful upgrade from 14.04 to 16.04?  I am completely baffled by what is happening.  Thanks for your

---

### Post by oldfred on 2017-01-12
I would back up your list of ppa and start clean.
It does not look like you have any of the old precise ppas with anything still active.

But all those ppa will lead to issues as they may have newer or different versions.

---

### Post by cscj01 on 2017-01-12
> **oldfred said:**
> I would back up your list of ppa and start clean.
It does not look like you have any of the old precise ppas with anything still active.

But all those ppa will lead to issues as they may have newer or different versions.

Do you mean delete the sources in /etc/apt/sources.list or the files in /etc/apt/sources.list.d or both?  Also, shouldn't I run ppa-purge for all the PPA's?  Finally, should I try to run ppa-purge for the old PPA's listed in /etc/apt/sources.list.d such as the precise ones for example?

---

### Post by oldfred on 2017-01-12
I do not know what ppa purge does.

All the precise look like empty folders. But if anything in them then that needs to be deleted/purged.

Do not delete sources.list or you will not be able to do anything. 
You can just add # in front of anything you do not want.

---

### Post by cscj01 on 2017-01-12
ppa-purge removes the PPA code and re-installs the release distributed code.  Essentially, it gets the particular package back to what was distributed with the release.

---

### Post by cscj01 on 2017-01-13
> **ian-weisser said:**
> Same story so far, all those top-level packages were dropped between 14.04 and 16.04 (libgnome-control-center1, libmutter0c, libical1, libmozjs-24-0,libopencv-*2.4, perl-modules)
Removal of those packages is expected behavior.
The lack of replacement packages and the dependency warnings are not expected behavior.

I have some more of the screenlog.0 in post #27.  I haven't heard back from you.  I am still at a loss to say what is going wrong.  Are you still in the loop?

---

### Post by cscj01 on 2017-01-17
I have done a clean install from a 16.04 Live DVD after backing up my 14.04 installation to a USB drive.  Things are running now on 16.04.  I am getting my application base back as it was.  So, I will close this thread.

---

