---
title: "[SOLVED] &amp;quot;files not found&amp;quot; during upgrade to Ibex"
date: 2008-10-26
forum: Installation &amp; Upgrades
---

### Post by tgyorgyi on 2008-10-26
I'm trying to upgrade to Ibex online, and got this message, now three times in a row. Internet connection is fine.

> Failed to fetch [http://hu.archive.ubuntu.com/ubuntu/pool/main/g/gcc-4.3/gcc-4.3-base_4.3.2-1ubuntu10_i386.deb](http://hu.archive.ubuntu.com/ubuntu/pool/main/g/gcc-4.3/gcc-4.3-base_4.3.2-1ubuntu10_i386.deb) 404 Not Found
Failed to fetch [http://hu.archive.ubuntu.com/ubuntu/pool/main/g/gcc-4.3/libgcc1_4.3.2-1ubuntu10_i386.deb](http://hu.archive.ubuntu.com/ubuntu/pool/main/g/gcc-4.3/libgcc1_4.3.2-1ubuntu10_i386.deb) 404 Not Found
Failed to fetch [http://hu.archive.ubuntu.com/ubuntu/pool/universe/c/cups/libcupsys2_1.3.9-2_all.deb](http://hu.archive.ubuntu.com/ubuntu/pool/universe/c/cups/libcupsys2_1.3.9-2_all.deb) 404 Not Found
Failed to fetch [http://hu.archive.ubuntu.com/ubuntu/pool/main/libg/libgweather/libgweather1_2.23.91-0ubuntu1_i386.deb](http://hu.archive.ubuntu.com/ubuntu/pool/main/libg/libgweather/libgweather1_2.23.91-0ubuntu1_i386.deb) 404 Not Found
Failed to fetch [http://hu.archive.ubuntu.com/ubuntu/pool/main/g/gnome-applets/gnome-applets-data_2.24.0.1-0ubuntu1_all.deb](http://hu.archive.ubuntu.com/ubuntu/pool/main/g/gnome-applets/gnome-applets-data_2.24.0.1-0ubuntu1_all.deb) 404 Not Found
Failed to fetch [http://hu.archive.ubuntu.com/ubuntu/pool/main/g/gnome-applets/gnome-applets_2.24.0.1-0ubuntu1_i386.deb](http://hu.archive.ubuntu.com/ubuntu/pool/main/g/gnome-applets/gnome-applets_2.24.0.1-0ubuntu1_i386.deb) 404 Not Found
Failed to fetch [http://hu.archive.ubuntu.com/ubuntu/pool/main/u/ubuntu-meta/ubuntu-minimal_1.122_i386.deb](http://hu.archive.ubuntu.com/ubuntu/pool/main/u/ubuntu-meta/ubuntu-minimal_1.122_i386.deb) 404 Not Found
Failed to fetch [http://hu.archive.ubuntu.com/ubuntu/pool/main/g/gnome-desktop/libgnome-desktop-2-7_2.24.0-0ubuntu2_i386.deb](http://hu.archive.ubuntu.com/ubuntu/pool/main/g/gnome-desktop/libgnome-desktop-2-7_2.24.0-0ubuntu2_i386.deb) 404 Not Found

Right now I don't want to do a clean install, I have the release candidate on Live CD, can I get the missing files from that?

---

### Post by plasmafusion on 2008-10-26
the links return a 404 error...
if you try [_this one_]("http://hu.archive.ubuntu.com/ubuntu/pool/main/g/gcc-4.3/gcc-4.3_4.3.2.orig.tar.gz") for example it works.
try another mirror? maybe one close to hungary but not in it?
if not then use the [_alternate cd_]("http://releases.ubuntu.com/releases/8.10/ubuntu-8.10-rc-alternate-i386.iso") to upgrade not the live cd...
   1. Download the alternate CD image
   2. Burn the CD image / re-insert the CD OR mount the CD image (sudo mount -o loop ubuntu-8.10-alternate-i386.iso /mnt/)
   3. A dialog should appear on your screen offering to upgrade your system using the CD
   4. If the dialog does not appear (it may not if you use the mount -o loop option), run the following via ALT-F2:
   5. gksudo “sh /media/cdrom/cdromupgrade” OR gksudo “sh /mnt/cdromupgrade”

---

### Post by tgyorgyi on 2008-10-26
In software sources download is set to "primary server", and changing Hungary for server in another country did not change the error message, download is still attempted from the Hungarian mirror. Which is strange, especially because meanwhile I found others mentioning this error in the Hungarian Ubuntu forum, and for them switching to "primary server" was a solution, but not for me.

I'll try now the alternate CD... although with the alternate CD for 8.04 I had a screen issue. :(

Oct. 27.: alternate CD worked! :)

---

### Post by plasmafusion on 2008-10-26
you could try editing the sources file by hand and comment out any of the hungarian servers.
sorry if you've tried all this already.

---

### Post by tgyorgyi on 2008-10-26
Nope, have not tried that yet. Would not know, how to. Meanwhile, I got the same result with the alternate CD upgrade: even tough I click on NOT using the internet, and the CD is being read, eventually I get the same error message. :(

---

