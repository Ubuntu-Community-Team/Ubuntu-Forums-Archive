---
title: "lucid lynx alpha, 64 bit, and amazon mp3 downloader"
date: 2010-01-28
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by yedidyah on 2010-01-28
I downloaded amazonmp3.deb from amazon.com
I also downloaded getlibs-all.deb from [http://frozenfox.freehostia.com/cappy/](http://frozenfox.freehostia.com/cappy/)

I am running lucid lynx alpha and I am trying to set up amazon mp3 downloader using the information on the following link:

[http://ubuntuforums.org/showthread.php?t=1240845&highlight=amazon+mp3+downloader](http://ubuntuforums.org/showthread.php?t=1240845&highlight=amazon+mp3+downloader)

_**STEP 1**_
sudo apt-get install libgtkmm-2.4-1c2a libboost-thread1.34.1 libboost-iostreams1.34.1 libboost-signals1.34.1 libboost-date-time1.34.1 libcurl3 libssl0.9.8 xdg-utils
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libgtkmm-2.4-1c2a is already the newest version.
libboost-thread1.34.1 is already the newest version.
E: Couldn't find package libboost-iostreams1.34.1


_**STEP 2**_
cd Downloads 

works fine

_**STEP 3**_
sudo dpkg -i --force-architecture amazonmp3.deb
dpkg: warning: overriding problem because --force enabled:
 package architecture (i386) does not match system (amd64)
(Reading database ... 141361 files and directories currently installed.)
Preparing to replace amazonmp3 1.0.9-1 (using amazonmp3.deb) ...
Unpacking replacement amazonmp3 ...
dpkg: dependency problems prevent configuration of amazonmp3:
 amazonmp3 depends on libglademm-2.4-1c2a; however:
  Package libglademm-2.4-1c2a is not installed.
 amazonmp3 depends on libboost-filesystem1.34.1; however:
  Package libboost-filesystem1.34.1 is not installed.
 amazonmp3 depends on libboost-regex1.34.1; however:
  Package libboost-regex1.34.1 is not installed.
 amazonmp3 depends on libboost-iostreams1.34.1; however:
  Package libboost-iostreams1.34.1 is not installed.
 amazonmp3 depends on libboost-signals1.34.1; however:
  Package libboost-signals1.34.1 is not installed.
 amazonmp3 depends on libboost-date-time1.34.1; however:
  Package libboost-date-time1.34.1 is not installed.
dpkg: error processing amazonmp3 (--install):
 dependency problems - leaving unconfigured
Processing triggers for shared-mime-info ...
Unknown media type in type 'all/all'

Unknown media type in type 'all/allfiles'

Unknown media type in type 'uri/mms'

Unknown media type in type 'uri/mmst'

Unknown media type in type 'uri/mmsu'

Unknown media type in type 'uri/pnm'

Unknown media type in type 'uri/rtspt'

Unknown media type in type 'uri/rtspu'

Unknown media type in type 'fonts/package'

Unknown media type in type 'interface/x-winamp-skin'

Processing triggers for desktop-file-utils ...
Processing triggers for python-gmenu ...
Rebuilding /usr/share/applications/desktop.en_US.utf8.cache...
Invalid desktop file /usr/share/applications/openoffice.org-base.desktop: ParsingError in file '/usr/share/applications/openoffice.org-base.desktop', [Desktop Entry]-Header missing
Processing triggers for python-support ...
Errors were encountered while processing:
 amazonmp3

_**STEP 4**_
sudo getlibs /usr/bin/amazonmp3
No match for libboost_filesystem-gcc42-1_34_1.so.1.34.1
No match for libboost_regex-gcc42-1_34_1.so.1.34.1
No match for libboost_date_time-gcc42-1_34_1.so.1.34.1
No match for libboost_signals-gcc42-1_34_1.so.1.34.1
No match for libboost_iostreams-gcc42-1_34_1.so.1.34.1
No match for libboost_thread-gcc42-mt-1_34_1.so.1.34.1
No packages to install


I tried to find the missing files in synaptic. Perhaps I am missing a repository?

---

### Post by yedidyah on 2010-01-28
Since I am not getting any responses I am wondering if I am too far ahead of everyone (using ubuntu alpha) concerning this issue.

---

### Post by llawwehttam on 2010-01-28
Amazon mp3 downloader is full of DRM. 
[http://www.defectivebydesign.org/what_is_drm](http://www.defectivebydesign.org/what_is_drm)

Read this and then decide if your sure you want to use it.

---

### Post by yedidyah on 2010-01-28
llawwehttam 

thank you for your response I agree with you I prefer not to use anything DRM but I don't know how to completely remove amazonmp3 downloader and I cannot figure out how to use clamz  

[http://code.google.com/p/clamz/](http://code.google.com/p/clamz/)

the description on how to use it is too vague in the README file when it says to open the downloaded amazon file (NameOfFile.amz) with clamz.

---

### Post by llawwehttam on 2010-01-28
This was partially covered here: [http://ubuntuforums.org/showpost.php?p=5522318&postcount=1](http://ubuntuforums.org/showpost.php?p=5522318&postcount=1)

Hope that helps.

---

### Post by yedidyah on 2010-01-28
Thank you for the more detailed information. Can you tell me how to completely remove the amazon mp3 downloader?

---

### Post by yedidyah on 2010-01-28
I tried the remedy at 

[http://www.amazon.com/gp/dmusic/help/amd.html/ref=sv_dmusic_4](http://www.amazon.com/gp/dmusic/help/amd.html/ref=sv_dmusic_4)

Uninstall Instructions

Ubuntu and Debian
sudo apt-get remove amazonmp3 --purge

Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package amazonmp3


But the file is still in /usr/bin/amazonmp3 and is still in Applications->Internet

---

### Post by yedidyah on 2010-01-29
I keep Windows XP caged in a virtualbox so I took a snapshot without the DRM then downloaded it. 

I use the "Public" folder as a share between my XP and Ubuntu host then I simply transfer the song to Ubuntu. 

But I am still unable to remove the the amazon mp3 downloader from Ubuntu.

---

### Post by chrisbell on 2010-02-18
I managed to get this working in lucid by using getlibs and then copying over some libs from another box.  I wrote a quick installer script and bundled the libs into a tarball here:

[http://www.randomdynamics.com/amazonmp3_lib32_lucid.tar.gz](http://www.randomdynamics.com/amazonmp3_lib32_lucid.tar.gz)

The install.sh script makes sure the amazonmp3 and getlibs debs are installed already and then just copies over the missing 32-bit libs into /usr/lib32.

---

### Post by joey-elijah on 2010-02-18
Not that i've tried it on Lucid, but it might be worth giving Pymazon a whirl if you'd prefer something more GUI to download Amazon MP3's with

[http://www.omgubuntu.co.uk/2010/01/pymazon-amazon-mp3-download-replacement.html](http://www.omgubuntu.co.uk/2010/01/pymazon-amazon-mp3-download-replacement.html)

---

### Post by eris23 on 2010-02-18
Thanks chrisbell!  amazonmp3 is now running in my lucid amd64 box

---

### Post by hounddog32 on 2010-04-01
No joy for me - I'm getting some weird things that seem to involve gvfs in /usr/lib - not the 32 bit version that I've had installed. Any ideas?


```
$ amazonmp3 
/usr/share/themes/Ambiance/gtk-2.0/gtkrc:128: error: unexpected identifier `separatorstyle', expected character `}'
/usr/lib/gio/modules/libgiogconf.so: wrong ELF class: ELFCLASS64
Failed to load module: /usr/lib/gio/modules/libgiogconf.so
/usr/lib/gio/modules/libgvfsdbus.so: wrong ELF class: ELFCLASS64
Failed to load module: /usr/lib/gio/modules/libgvfsdbus.so
/usr/lib/gio/modules/libgioremote-volume-monitor.so: wrong ELF class: ELFCLASS64
Failed to load module: /usr/lib/gio/modules/libgioremote-volume-monitor.so
amazonmp3: symbol lookup error: /usr/lib32/libglibmm-2.4.so.1: undefined symbol: g_realloc_n

```

---

### Post by Slim Odds on 2010-04-01
> **llawwehttam said:**
> Amazon mp3 downloader is full of DRM. 
[http://www.defectivebydesign.org/what_is_drm](http://www.defectivebydesign.org/what_is_drm)

Read this and then decide if your sure you want to use it.

Take is easy with the alarmist nonsense. The Amazon MP3 downloader is not the same as their Unbox movie download service. Please take the time to read and understand what is really going on.

> Amazon's new movie download service is called Unbox and it outlines what  DRM implies. The user agreement requires that you allow Unbox DRM  software to monitor your hard drive and to report activity to Amazon. The movie download service is NOT the music download that has NO DRM.

---

### Post by chrisbell on 2010-04-02
> **hounddog32 said:**
> No joy for me - I'm getting some weird things that seem to involve gvfs in /usr/lib - not the 32 bit version that I've had installed. Any ideas?


Does ldd show all dependencies are resolved like so?

$ ldd /usr/lib32/libglibmm-2.4.so.1
	linux-gate.so.1 =>  (0xf7724000)
	libsigc-2.0.so.0 => /usr/lib32/libsigc-2.0.so.0 (0xf76a3000)
	libgobject-2.0.so.0 => /usr/lib32/libgobject-2.0.so.0 (0xf7663000)
	libgthread-2.0.so.0 => /usr/lib32/libgthread-2.0.so.0 (0xf765c000)
	libgmodule-2.0.so.0 => /usr/lib32/libgmodule-2.0.so.0 (0xf7657000)
	librt.so.1 => /lib32/librt.so.1 (0xf764e000)
	libglib-2.0.so.0 => /lib32/libglib-2.0.so.0 (0xf7590000)
	libstdc++.so.6 => /usr/lib32/libstdc++.so.6 (0xf749a000)
	libm.so.6 => /lib32/libm.so.6 (0xf7473000)
	libc.so.6 => /lib32/libc.so.6 (0xf731a000)
	libgcc_s.so.1 => /usr/lib32/libgcc_s.so.1 (0xf72fb000)
	libpthread.so.0 => /lib32/libpthread.so.0 (0xf72e2000)
	libpcre.so.3 => /lib32/libpcre.so.3 (0xf72b1000)
	libdl.so.2 => /lib32/libdl.so.2 (0xf72ad000)
	/lib/ld-linux.so.2 (0xf7725000)

---

### Post by mfraser on 2010-04-19
It requires libboost-filesystem1.34.1 which isn't in Lucid only libboost-filesystem1.40.0.

---

### Post by oldos2er on 2010-04-19
This works for me: [http://code.google.com/p/clamz/](http://code.google.com/p/clamz/)

---

### Post by Yellow Pasque on 2010-04-19
> **mfraser said:**
> It requires libboost-filesystem1.34.1 which isn't in Lucid only libboost-filesystem1.40.0.
Here's my little script to deal with it. I assume you downloaded amazonmp3.deb from amazon's site after agreeing to their TOS, and placed it in your home directory. (Sorry that I couldn't make that part more direct, but it would technically be illegal to circumvent the TOS dialog):
```
#!/bin/sh

sudo dpkg -i --force-all ~/amazonmp3.deb
sudo apt-get install ia32-libs
wget http://frozenfox.freehostia.com/cappy/getlibs-all.deb
sudo dpkg -i getlibs-all.deb
sudo getlibs /usr/bin/amazonmp3
sudo getlibs -p gvfs
sudo getlibs -w http://ftp.osuosl.org/pub/ubuntu/pool/universe/b/boost/libboost-date-time1.34.1_1.34.1-16ubuntu1_i386.deb http://ftp.osuosl.org/pub/ubuntu/pool/universe/b/boost/libboost-filesystem1.34.1_1.34.1-16ubuntu1_i386.deb http://ftp.osuosl.org/pub/ubuntu/pool/universe/b/boost/libboost-iostreams1.34.1_1.34.1-16ubuntu1_i386.deb http://ftp.osuosl.org/pub/ubuntu/pool/universe/b/boost/libboost-regex1.34.1_1.34.1-16ubuntu1_i386.deb http://ftp.osuosl.org/pub/ubuntu/pool/universe/b/boost/libboost-signals1.34.1_1.34.1-16ubuntu1_i386.deb http://ftp.osuosl.org/pub/ubuntu/pool/universe/b/boost/libboost-thread1.34.1_1.34.1-16ubuntu1_i386.deb http://ftp.osuosl.org/pub/ubuntu/pool/main/i/icu/libicu40_4.0.1-2ubuntu2_i386.deb
sudo ldconfig
```

---

### Post by colin-m on 2010-04-20
Thanks for the write-up. I copied and installed the script and it worked straight away.

I can now download mp3's from Amazon again.

---

