---
title: "GAH! Can't install, upgrade or remove anything!"
date: 2007-05-12
forum: Installation &amp; Upgrades
---

### Post by Nameless One on 2007-05-12
Before I had been using the Update Manager (this is on Xubuntu 6.10) to round up all the latest upgrades, around 90 of them. I waited an hour or so for the several hundred megabytes to download. Throughout the process, my connection was dropped several times so I often had to close and reopen the Update Manager. Once the updates were finally downloaded, I was relieved but then instantly disappointed when they wouldn't install.

I don't recall the error I got at the time as I couldn't copy/paste it.
I rebooted and went into Synaptic to try and reapply the updates. Same error.
I tried to update each file individually. Similar error again.
I figured I would try to remove some other packages and clean up before having to download everything again, as I removed all the downloaded packages with a clean command.

I wanted to remove Mozilla Thunderbird and Gxine, but the Xubuntu-desktop metapackage depends on them. So I went to remove that first.
But...
```
couldn't open log `/var/log/dpkg.log': Input/output error
(Reading database ... dpkg: error processing xubuntu-desktop (--remove):
 unable to open files list file for package `landscape-client': Input/output error
Errors were encountered while processing:
 xubuntu-desktop
Processing was halted because there were too many errors.
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:

```
This blasted landscape-client keeps popping up. I recall seeing it mentioned in the earlier errors. So I tried removing that too.
```
sudo apt-get remove landscape-client
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  xubuntu-desktop landscape-client xubuntu-docs
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  landscape-client xubuntu-desktop
0 upgraded, 0 newly installed, 2 to remove and 86 not upgraded.
Need to get 0B of archives.
After unpacking 69.6kB disk space will be freed.
Do you want to continue [Y/n]? Y
(Reading database ... dpkg: error processing xubuntu-desktop (--remove):
 unable to open files list file for package `landscape-client': Input/output error
Errors were encountered while processing:
 xubuntu-desktop
Processing was halted because there were too many errors.
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

Well I'm stumped. Anyone got any clues as why this noob is stumbling over his packages?

---

### Post by heimo on 2007-05-12
Try the **second **part in this post - do not try copying status file at first. Replace gaim with the landscape-client.
[http://ubuntuforums.org/showpost.php?p=2626248&postcount=4](http://ubuntuforums.org/showpost.php?p=2626248&postcount=4)

---

### Post by Nameless One on 2007-05-12
When I tried the first line, substituting in 'landscape-client', I got:
```
sudo mv /var/lib/dpkg/info/landscape-client.* /tmp/
Password:
mv: cannot stat `/var/lib/dpkg/info/landscape-client.list': Input/output error
mv: cannot stat `/var/lib/dpkg/info/landscape-client.md5sums': Input/output error

```

I went to the folder '/var/lib/dpkg/info/' in Thunar, but could find no files with the words 'landscape-client' in their name.
What should I do now? Do I just execute the other two lines?

---

### Post by heimo on 2007-05-12
Oh, I should have used my head. :) But no problem - go ahead and do the --purge remove / install thing for the same package. That could fix it.

---

### Post by Nameless One on 2007-05-12
Sweet mother of Jesus...
```
sudo apt-get --purge remove landscape-client
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  xubuntu-desktop landscape-client xubuntu-docs
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  landscape-client* xubuntu-desktop*
0 upgraded, 0 newly installed, 2 to remove and 86 not upgraded.
Need to get 0B of archives.
After unpacking 69.6kB disk space will be freed.
Do you want to continue [Y/n]? Y
(Reading database ... dpkg: error processing xubuntu-desktop (--purge):
 unable to open files list file for package `landscape-client': Input/output error
Errors were encountered while processing:
 xubuntu-desktop
Processing was halted because there were too many errors.
E: Sub-process /usr/bin/dpkg returned an error code (1)
```
I'm lost. Seems to be a big circle, removing either 'xubuntu-desktop' or 'landscape-client' will just halt over the other package.
Thanks for the quick responses.

---

### Post by heimo on 2007-05-12
Oh. Next I'd try moving those /var/lib/dpkg/info/xubuntu-desktop.* files away, and --purge removing (with apt-get!) xubuntu-desktop and reinstalling it.

---

### Post by Nameless One on 2007-05-12
Attempting to removed 'xubuntu-desktop' also fails over the 'unable to open files list file for package `landscape-client': Input/output error' error. Perhaps it's the fact that there are no 'landscape-client' lists files for it to access? Is there anyway I could replace these files?

```
sudo apt-get --purge remove xubuntu-desktop
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  xubuntu-desktop xubuntu-docs
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  xubuntu-desktop*
0 upgraded, 0 newly installed, 1 to remove and 86 not upgraded.
Need to get 0B of archives.
After unpacking 36.9kB disk space will be freed.
Do you want to continue [Y/n]? Y
(Reading database ... dpkg: error processing xubuntu-desktop (--purge):
 unable to open files list file for package `landscape-client': Input/output error
Errors were encountered while processing:
 xubuntu-desktop
Processing was halted because there were too many errors.
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

---

### Post by heimo on 2007-05-12
I'd try purge removing both of them at once. But before that, moving away  files for those two packages under /var/lib/dpkg/info/. Then
```
sudo apt-get --purge remove lanscape-client xubuntu-desktop
```

---

### Post by Nameless One on 2007-05-12
```
(Reading database ... dpkg: error processing xubuntu-desktop (--purge):
 unable to open files list file for package `landscape-client': Input/output error
Errors were encountered while processing:
 xubuntu-desktop
Processing was halted because there were too many errors.
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

Same thing. I somehow need to replace the list files for `landscape-client'. Is there a way to force a reinstall of a package?

---

### Post by heimo on 2007-05-12
Try:
```
sudo apt-get --reinstall install landscape-client
```EDIT: Removed false information.

---

### Post by heimo on 2007-05-12
You can force installing the landscape package with a command similar to this (replace the package file name with an actual existing file):
```
sudo dpkg --force-all -i /var/cache/apt/archives/landscape-client_i386.deb

```
Using --force flags is always considered potentially harmful / dangerous.

---

### Post by Nameless One on 2007-05-12
This sure is mighty confusing for me.
```
(Reading database ... dpkg: error processing /var/cache/apt/archives/landscape-client_0.1_all.deb (--unpack):
 unable to open files list file for package `landscape-client': Input/output error
Errors were encountered while processing:
 /var/cache/apt/archives/landscape-client_0.1_all.deb
Processing was halted because there were too many errors.
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

Everything that I do just leads back to the "unable to open files list file for package `landscape-client': Input/output error" error message.

I wnet to 'http://packages.ubuntu.com/edgy/source/landscape-client' to see if I could install manually, but all the package is is a bunch of text files saying the package is a placeholder. Who could have thought a placeholder could cause so much trouble?

I have to go for an hour or so, but any extra help is welcome!

EDIT: I'll try the above info soon. Thanks.

---

### Post by Nameless One on 2007-05-12
Well, I tried the force flags, but alas, I got the same error message as before.
This problem is REALLY annoying as I can't install, remove or upgrade ANY package. I just tried installing 'abiword-help' as a test and the same problem arises.
I do hope someone can help me or I may just have to reinstall everything.

---

### Post by heimo on 2007-05-12
Did you try moving the xubuntu-desktop files (to some place from where you can restore them, if necessary)?

At this point I'd probably try using status-old file too.

---

### Post by Nameless One on 2007-05-12
I've tried everything. I replaced the status file with the old one and then updated. I moved around the 'xubuntu-desktop' files and attempted to move the 'landscape-client' files to find they are non-existant. I have tried to force a reinstall of the packages only to receive the same error message, over and over. I tried to do the whole purge and remove thing but yet again, I received the same errors.
I have absolutely no idea what to do now. :confused: :confused: :confused:

---

### Post by jvargaszabo on 2007-05-14
I'm having the same issue, but I'm on Kubuntu Feisty. Please tell me there is a solution for this.

I get the same message, just with more error'd packages. I'll post the script later, but its driving me nuts.

---

### Post by Nameless One on 2007-05-16
After reading some of the below, I almost thought of giving up.
[http://ubuntuforums.org/archive/index.php/t-353923.html]("http://ubuntuforums.org/archive/index.php/t-353923.html")
[http://ubuntuforums.org/archive/index.php/t-249474.html]("http://ubuntuforums.org/archive/index.php/t-249474.html")
[http://ubuntuforums.org/archive/index.php/t-332220.html]("http://ubuntuforums.org/archive/index.php/t-332220.html")
Seems like many people could find no solution and thus just started from scratch.

But I am still determined to find a solution. Perhaps its because I'm too lazy to wipe the slate clean.
I started off by removing the 'landscape-client' list files. I couldn't find them in Thunar, but could still remove them in the terminal. Seems like they may have been corrupted.
```
one@nameless-desktop:/var/lib/dpkg/info$ sudo rm landscape-client.list
one@nameless-desktop:/var/lib/dpkg/info$ sudo rm landscape-client.md5sums
one@nameless-desktop:/var/lib/dpkg/info$ sudo rm landscape-client.postinst

```
Then I went to attempt to remove this darned 'landscape-client'.
```
sudo aptitude remove landscape-client
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
The following packages are BROKEN:
  xubuntu-desktop 
The following packages have been automatically kept back:
  libcurl3 libcurl3-openssl-dev libx11-6 libx11-data libx11-dev 
  linux-image-2.6.17-10-generic linux-image-generic 
  linux-restricted-modules-2.6.17-10-generic 
  linux-restricted-modules-common linux-restricted-modules-generic 
  vmware-player-kernel-modules vmware-player-kernel-modules-2.6.17-10 
The following packages have been kept back:
  app-install-data-commercial avahi-daemon bind9-host curl dbus 
  dbus-1-utils dnsutils evince-gtk file firefox gdm gimp gimp-data gnupg 
  info language-pack-en libavahi-common-data libavahi-common3 
  libavahi-core4 libbind9-0 libcurl3-dev libdbus-1-3 libdns21 libgimp2.0 
  libgnomeprintui2.2-0 libgnomeprintui2.2-common libgtop2-7 libgtop2-common 
  libisc11 libisccc0 libisccfg1 liblwres9 libmagic1 libnspr4 libnss3 
  libpoppler1 libpoppler1-glib libvolumeid0 libwpd-stream8c2a libwpd8c2a 
  libxine-main1 libxine1 linux-generic linux-headers-2.6.17-10 
  linux-headers-2.6.17-10-generic linux-headers-generic linux-libc-dev 
  mozilla-thunderbird nvidia-glx poppler-utils popularity-contest 
  samba-common screen slocate smbclient synaptic system-tools-backends tar 
  tcpdump tzdata udev update-manager volumeid w3m x11-common xbase-clients 
  xfce4-xkb-plugin xorg xserver-xorg xserver-xorg-core 
  xserver-xorg-input-all xserver-xorg-video-all xubuntu-system-tools xutils 
The following packages will be REMOVED:
  landscape-client 
0 packages upgraded, 0 newly installed, 1 to remove and 86 not upgraded.
Need to get 0B of archives. After unpacking 32.8kB will be freed.
The following packages have unmet dependencies:
  xubuntu-desktop: Depends: landscape-client but it is not installable
Resolving dependencies...
The following actions will resolve these dependencies:

Remove the following packages:
xubuntu-desktop

Score is -301

Accept this solution? [Y/n/q/?] Y
The following packages have been automatically kept back:
  libcurl3 libcurl3-openssl-dev libx11-6 libx11-data libx11-dev 
  linux-image-2.6.17-10-generic linux-image-generic 
  linux-restricted-modules-2.6.17-10-generic 
  linux-restricted-modules-common linux-restricted-modules-generic 
  vmware-player-kernel-modules vmware-player-kernel-modules-2.6.17-10 
The following packages will be automatically REMOVED:
  xubuntu-desktop 
The following packages have been kept back:
  app-install-data-commercial avahi-daemon bind9-host curl dbus 
  dbus-1-utils dnsutils evince-gtk file firefox gdm gimp gimp-data gnupg 
  info language-pack-en libavahi-common-data libavahi-common3 
  libavahi-core4 libbind9-0 libcurl3-dev libdbus-1-3 libdns21 libgimp2.0 
  libgnomeprintui2.2-0 libgnomeprintui2.2-common libgtop2-7 libgtop2-common 
  libisc11 libisccc0 libisccfg1 liblwres9 libmagic1 libnspr4 libnss3 
  libpoppler1 libpoppler1-glib libvolumeid0 libwpd-stream8c2a libwpd8c2a 
  libxine-main1 libxine1 linux-generic linux-headers-2.6.17-10 
  linux-headers-2.6.17-10-generic linux-headers-generic linux-libc-dev 
  mozilla-thunderbird nvidia-glx poppler-utils popularity-contest 
  samba-common screen slocate smbclient synaptic system-tools-backends tar 
  tcpdump tzdata udev update-manager volumeid w3m x11-common xbase-clients 
  xfce4-xkb-plugin xorg xserver-xorg xserver-xorg-core 
  xserver-xorg-input-all xserver-xorg-video-all xubuntu-system-tools xutils 
The following packages will be REMOVED:
  landscape-client xubuntu-desktop 
0 packages upgraded, 0 newly installed, 2 to remove and 86 not upgraded.
Need to get 0B of archives. After unpacking 69.6kB will be freed.
Do you want to continue? [Y/n/?] Y
Writing extended state information... Done
(Reading database ... 
dpkg: serious warning: files list file for package `landscape-client' missing, assuming package has no files currently installed.
dpkg: error processing xubuntu-desktop (--remove):
 unable to open files list file for package `iproute': Input/output error
Errors were encountered while processing:
 xubuntu-desktop
Processing was halted because there were too many errors.
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:

```

RAAAHHH! At this point, I'm feeling rather ropable. Several new things have popped up.
It now says: The following packages are BROKEN:
  xubuntu-desktop 
and:  'unable to open files list file for package `iproute': Input/output error'
Now it seems like the corruption of 'landscape-client' has in turn corrupted 'xubuntu-desktop'. Also now it seems like the list files for other packages are also corrupted.
I will continue to try and get this beast up and running again, but any 3rd party help would be warmly appreciated.

---

### Post by Nameless One on 2007-05-16
```
one@nameless-desktop:/var/lib/dpkg/info$ sudo mv /var/lib/dpkg/info/iproute.* /tmp/
mv: cannot stat `/var/lib/dpkg/info/iproute.conffiles': Input/output error
mv: cannot stat `/var/lib/dpkg/info/iproute.list': Input/output error
```

I was trying to move the 'iproute' list files temporarly, but I receive this error message. What does 'cannot stat' mean?
EDIT: Attempting to open any of these files just brings up a new blank document with the files name. Seems like my hard drive is even more corrupt than the government of New Zealand.
I can't even remove the files! This is assuming they are there but hidden.
```
sudo rm /var/lib/dpkg/info/iproute.list
rm: cannot remove `/var/lib/dpkg/info/iproute.list': No such file or directory
```

And the chain of corruption never ends... Now another package is corrupt! Somehow I don't think I will be using that weasel of a update tool again.
```
sudo aptitude reinstall iproute
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
Building tag database... Done      
The following packages have been automatically kept back:
  libcurl3 libcurl3-openssl-dev libx11-6 libx11-data libx11-dev 
  linux-image-2.6.17-10-generic linux-image-generic 
  linux-restricted-modules-2.6.17-10-generic 
  linux-restricted-modules-common linux-restricted-modules-generic 
  vmware-player-kernel-modules vmware-player-kernel-modules-2.6.17-10 
The following packages have been kept back:
  app-install-data-commercial avahi-daemon bind9-host curl dbus 
  dbus-1-utils dnsutils evince-gtk file firefox gdm gimp gimp-data gnupg 
  info language-pack-en libavahi-common-data libavahi-common3 
  libavahi-core4 libbind9-0 libcurl3-dev libdbus-1-3 libdns21 libgimp2.0 
  libgnomeprintui2.2-0 libgnomeprintui2.2-common libgtop2-7 libgtop2-common 
  libisc11 libisccc0 libisccfg1 liblwres9 libmagic1 libnspr4 libnss3 
  libpoppler1 libpoppler1-glib libvolumeid0 libwpd-stream8c2a libwpd8c2a 
  libxine-main1 libxine1 linux-generic linux-headers-2.6.17-10 
  linux-headers-2.6.17-10-generic linux-headers-generic linux-libc-dev 
  mozilla-thunderbird nvidia-glx poppler-utils popularity-contest 
  samba-common screen slocate smbclient synaptic system-tools-backends tar 
  tcpdump tzdata udev update-manager volumeid w3m x11-common xbase-clients 
  xfce4-xkb-plugin xorg xserver-xorg xserver-xorg-core 
  xserver-xorg-input-all xserver-xorg-video-all xubuntu-system-tools xutils 
The following packages will be REINSTALLED:
  iproute 
0 packages upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 86 not upgraded.
Need to get 949kB of archives. After unpacking 0B will be used.
Writing extended state information... Done
Get:1 http://archive.ubuntu.com edgy/main iproute 20051007-4ubuntu2 [949kB]
Fetched 949kB in 39s (23.8kB/s)                                                 
(Reading database ... 
dpkg: serious warning: files list file for package `landscape-client' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `iproute' missing, assuming package has no files currently installed.
dpkg: error processing /var/cache/apt/archives/iproute_20051007-4ubuntu2_i386.deb (--unpack):
 unable to open files list file for package `intltool-debian': Input/output error
Errors were encountered while processing:
 /var/cache/apt/archives/iproute_20051007-4ubuntu2_i386.deb
Processing was halted because there were too many errors.
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
```

---

### Post by heimo on 2007-05-16
Doesn't look good. It might be right time to run fsck on your partitions. You need live-CD to do that (partitions can't be mounted when checked).
[LIST=1]
[*]Write down partition device names from output of mount command or /etc/fstab
[*]Boot from live cd
[*]For each partition, run fsck.ext3 /dev/sda1 (or similar, assuming you're using ext3 filesystem, which is default)[/LIST]After removing any scripts from /var/lib/dpkg/info, you need to --purge remove that package and then reinstall it (which also installs those script files). Remember that your /tmp directory gets emptied at every boot, so that's not a safe place to keep any valuable information.

---

### Post by Nameless One on 2007-05-16
Heh, booting the LiveCD just rekindled my dislike of Firefox.
Anyway, here is the output from 'fsck'ing my Xubuntu partition. I only ran with the '-f' flag as I was unfamiliar with the flags. Also I answered yes to all the questions as many of them were beyond me.
```
sudo fsck.ext3 /dev/hda2 -f
e2fsck 1.40-WIP (14-Nov-2006)
Pass 1: Checking inodes, blocks, and sizes
Inodes that were part of a corrupted orphan linked list found.  Fix<y>? yes

Inode 1044051 was part of the orphaned inode list.  FIXED.
Inode 1044062 was part of the orphaned inode list.  FIXED.
Inode 1044064, i_blocks is 0, should be 8.  Fix<y>? yes


Running additional passes to resolve blocks claimed by more than one inode...
Pass 1B: Rescanning for multiply-claimed blocks
Multiply-claimed block(s) in inode 1044064: 2571932
Multiply-claimed block(s) in inode 1271723: 2571932
Pass 1C: Scanning directories for inodes with multiply-claimed blocks
Pass 1D: Reconciling multiply-claimed blocks
(There are 2 inodes containing multiply-claimed blocks.)

File ... (inode #1044064, mod time Sat May 12 06:26:25 2007) 
  has 1 multiply-claimed block(s), shared with 1 file(s):
        /etc/modprobe.d/alsa-base (inode #1271723, mod time Wed Aug 30 03:50:19 2006)
Clone multiply-claimed blocks<y>? yes

File /etc/modprobe.d/alsa-base (inode #1271723, mod time Wed Aug 30 03:50:19 2006) 
  has 1 multiply-claimed block(s), shared with 1 file(s):
        ... (inode #1044064, mod time Sat May 12 06:26:25 2007)
Multiply-claimed blocks already reassigned or cloned.

Pass 2: Checking directory structure
Entry 'daemon.log.2.gz' in /var/log (1042440) has deleted/unused inode 1044063.  Clear<y>? yes

Entry 'index.db' in /var/cache/man/local (1042485) has deleted/unused inode 1044050.  Clear<y>? yes

Entry 'inputattach.md5sums' in /var/lib/dpkg/info (1043241) has deleted/unused inode 1044033.  Clear<y>? yes

Entry 'intltool-debian.list' in /var/lib/dpkg/info (1043241) has deleted/unused inode 1044034.  Clear<y>? yes

Entry 'intltool-debian.md5sums' in /var/lib/dpkg/info (1043241) has deleted/unused inode 1044035.  Clear<y>? yes

Entry 'iptables.list' in /var/lib/dpkg/info (1043241) has deleted/unused inode 1044038.  Clear<y>? yes

Entry 'iptables.md5sums' in /var/lib/dpkg/info (1043241) has deleted/unused inode 1044039.  Clear<y>? yes

Entry 'iptables.postinst' in /var/lib/dpkg/info (1043241) has deleted/unused inode 1044040.  Clear<y>? yes

Entry 'iptables.prerm' in /var/lib/dpkg/info (1043241) has deleted/unused inode 1044041.  Clear<y>? yes

Entry 'iputils-arping.list' in /var/lib/dpkg/info (1043241) has deleted/unused inode 1044042.  Clear<y>? yes

Entry 'iputils-arping.md5sums' in /var/lib/dpkg/info (1043241) has deleted/unused inode 1044043.  Clear<y>? yes

Entry 'iputils-ping.list' in /var/lib/dpkg/info (1043241) has deleted/unused inode 1044044.  Clear<y>? yes

Entry 'iputils-ping.md5sums' in /var/lib/dpkg/info (1043241) has deleted/unused inode 1044045.  Clear<y>? yes

Entry 'iputils-tracepath.list' in /var/lib/dpkg/info (1043241) has deleted/unused inode 1044046.  Clear<y>? yes

Entry 'iputils-tracepath.md5sums' in /var/lib/dpkg/info (1043241) has deleted/unused inode 1044047.  Clear<y>? yes

Entry 'iso-codes.list' in /var/lib/dpkg/info (1043241) has deleted/unused inode 1044048.  Clear<y>? yes

Entry 'iso-codes.md5sums' in /var/lib/dpkg/info (1043241) has deleted/unused inode 1044049.  Clear<y>? yes

Entry 'klibc-utils.list' in /var/lib/dpkg/info (1043241) has deleted/unused inode 1044052.  Clear<y>? yes

Entry 'klibc-utils.md5sums' in /var/lib/dpkg/info (1043241) has deleted/unused inode 1044053.  Clear<y>? yes

Entry 'klogd.conffiles' in /var/lib/dpkg/info (1043241) has deleted/unused inode 1044054.  Clear<y>? yes

Entry 'klogd.list' in /var/lib/dpkg/info (1043241) has deleted/unused inode 1044055.  Clear<y>? yes

Entry 'klogd.postinst' in /var/lib/dpkg/info (1043241) has deleted/unused inode 1044056.  Clear<y>? yes

Entry 'klogd.postrm' in /var/lib/dpkg/info (1043241) has deleted/unused inode 1044057.  Clear<y>? yes

Entry 'klogd.preinst' in /var/lib/dpkg/info (1043241) has deleted/unused inode 1044058.  Clear<y>? yes

Entry 'klogd.prerm' in /var/lib/dpkg/info (1043241) has deleted/unused inode 1044059.  Clear<y>? yes

Pass 3: Checking directory connectivity
Pass 4: Checking reference counts
Unattached inode 1044064
Connect to /lost+found<y>? yes

Inode 1044064 ref count is 65535, should be 1.  Fix<y>? yes

Pass 5: Checking group summary information
Block bitmap differences:  -2121387 -2121400 -2123948 -2124012 -(2126275--2126307) -(2126310--2126319) -2127873 -(2137139--2137144) -2137337 -(2137428--2137449) -(2137496--2137514) -2193501
Fix<y>? yes

Free blocks count wrong for group #1 (31695, counted=31694).
Fix<y>? yes

Free blocks count wrong for group #64 (5823, counted=5871).
Fix<y>? yes

Free blocks count wrong for group #65 (22300, counted=22348).
Fix<y>? yes

Free blocks count wrong for group #66 (17398, counted=17399).
Fix<y>? yes

Free blocks count wrong (2080234, counted=2080330).
Fix<y>? yes

Inode bitmap differences:  -(1044033--1044035) -(1044038--1044059) -(1044062--1044063)
Fix<y>? yes

Free inodes count wrong for group #64 (11819, counted=11846).
Fix<y>? yes

Free inodes count wrong (1472678, counted=1472705).
Fix<y>? yes


/dev/hda2: ***** FILE SYSTEM WAS MODIFIED *****
/dev/hda2: 139807/1612512 files (1.4% non-contiguous), 1138694/3219024 blocks
```
WTF is one thing, ROTFLMFAO is another. I was surprised at the amount of problems.
I suppose it's now time to boot up and try this beast again.

---

### Post by heimo on 2007-05-16
> **Nameless One said:**
> I was surprised at the amount of problems.

Wow. I'm surprised and impressed if it'll work after all those fixes. I hope it will.

---

### Post by Nameless One on 2007-05-16
WOH!
```
sudo apt-get --purge remove landscape-client
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  xubuntu-desktop landscape-client xubuntu-docs
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  landscape-client* xubuntu-desktop*
0 upgraded, 0 newly installed, 2 to remove and 86 not upgraded.
Need to get 0B of archives.
After unpacking 69.6kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 
dpkg: serious warning: files list file for package `landscape-client' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `iproute' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `intltool-debian' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `klibc-utils' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `xubuntu-desktop' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `iso-codes' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `iputils-ping' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `iputils-tracepath' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `klogd' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `iptables' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `iputils-arping' missing, assuming package has no files currently installed.
101285 files and directories currently installed.)
Removing xubuntu-desktop ...
Removing landscape-client ...
```
IT WORKED! Finally I can remove 'xubuntu-desktop' and 'landscape-client'!

I never realised the solution would be so simple.  Just a quick 'sudo fsck.ext3 /dev/hda2 -f' [to others experiencing the problem, just substitute in your hard disk name where it says hda2], select to fix all the problems and Bob's your uncle. After removing the 2 packages, I successfully reinstalled all the packages that threw up a 'serious warning' before. Then I could remove Mozilla Thunderbird and Gxine successfully, which was what I wanted to do in the first place.

I hope those others who had this problem find some worth out of my fiasco. 
GIANT THANKS to heimo for being a genius! :guitar: :popcorn: :) :KS 
WOOOOOOOOOHHHHHOOOOOO!

---

### Post by heimo on 2007-05-16
> **Nameless One said:**
> IT WORKED!

That's fantastic!

> **Nameless One said:**
> 
GIANT THANKS to heimo for being a genius!


It's always team work. :) For me, "cannot stat" was a clue that there may be something "funny" in the filesystem. Should have thought that earlier. But this is how we learn as a community, hopefully it'll be easier next time. Really happy to hear that your system is back up and running. Keep your eye on any anomalies, sometimes filesystem corruption is early sign of bad hardware. Do your backups of any valuable data now.

Happy hacking! :)

---

