---
title: "Installation of Use next"
date: 2011-12-19
forum: Installation &amp; Upgrades
---

### Post by judodave on 2011-12-19
Was wondering if anyone can help me. I'm quite new to this. I'm trying to install Usenext but when I do I get a warning 

First it says:

"Package is of bad quality"

"The installation of a package which violates the quality standards isn't allowed. This could cause serious problems on your computer. Please contact the person or organisation who provided this package file and include the details beneath."

I thin click on the " ingore and Install" buton and it says 

Lintian check results for /tmp/usenext_5.27.deb:
Use of uninitialized value $ENV{"HOME"} in concatenation (.) or string at /usr/bin/lintian line 112.
E: usenext: arch-independent-package-contains-binary-or-object usr/lib/usenext/libparcalc.so
E: usenext: wrong-file-owner-uid-or-gid usr/ 1000/1000
E: usenext: wrong-file-owner-uid-or-gid usr/bin/ 1000/1000
E: usenext: wrong-file-owner-uid-or-gid usr/bin/usenext 1000/1000
E: usenext: wrong-file-owner-uid-or-gid usr/lib/ 1000/1000
E: usenext: wrong-file-owner-uid-or-gid usr/lib/usenext/ 1000/1000
E: usenext: wrong-file-owner-uid-or-gid usr/lib/usenext/App.ico 1000/1000
E: usenext: wrong-file-owner-uid-or-gid usr/lib/usenext/Ionic.Zlib.dll 1000/1000
E: usenext: wrong-file-owner-uid-or-gid usr/lib/usenext/NntpCore.dll 1000/1000
E: usenext: wrong-file-owner-uid-or-gid usr/lib/usenext/NntpUN.dll 1000/1000
E: usenext: wrong-file-owner-uid-or-gid usr/lib/usenext/NntpWeb.dll 1000/1000
E: usenext: wrong-file-owner-uid-or-gid usr/lib/usenext/Par2Calc.dll 1000/1000
E: usenext: wrong-file-owner-uid-or-gid usr/lib/usenext/Resources.res 1000/1000
E: usenext: wrong-file-owner-uid-or-gid usr/lib/usenext/UseNeXT.exe 1000/1000
E: usenext: wrong-file-owner-uid-or-gid usr/lib/usenext/UseNeXTLauncher.exe 1000/1000
E: usenext: wrong-file-owner-uid-or-gid usr/lib/usenext/libparcalc.so 1000/1000
E: usenext: wrong-file-owner-uid-or-gid usr/lib/usenext/linux 1000/1000
E: usenext: wrong-file-owner-uid-or-gid usr/lib/usenext/usenext.xpm 1000/1000
E: usenext: wrong-file-owner-uid-or-gid usr/share/ 1000/1000
E: usenext: wrong-file-owner-uid-or-gid usr/share/applications/ 1000/1000
E: usenext: wrong-file-owner-uid-or-gid usr/share/applications/usenext.desktop 1000/1000
E: usenext: wrong-file-owner-uid-or-gid usr/share/menu/ 1000/1000
E: usenext: wrong-file-owner-uid-or-gid usr/share/menu/usenext 1000/1000
E: usenext: wrong-file-owner-uid-or-gid usr/share/pixmaps/ 1000/1000
E: usenext: wrong-file-owner-uid-or-gid usr/share/pixmaps/usenext.png 1000/1000
E: usenext: wrong-file-owner-uid-or-gid usr/share/pixmaps/usenext.xpm 1000/1000

It then installs but doesn't open, has any one got any ideas please

Thanks Dave

---

### Post by Mark Phelps on 2011-12-22
Sorry if this is going to sound harsh -- but one of the FIRST things you need to learn, since you admit to being "new to this" is to follow directions!

You were warned NOT to install this package ... but yet, you did it anyway.  You are extremely fortunate that it did not trash your install.

Next time, heed warnings and do NOT install such stuff.

---

### Post by critin on 2011-12-22
> **Was wondering if anyone can help me. **I'm quite new to this. I'm trying to install Usenext but when I do I get a warning 

First it says:

"Package is of bad quality"

"The installation of a package which violates the quality standards  isn't allowed. **This could cause serious problems on your computer.**  Please contact the person or organisation who provided this package file  and include the details beneath."

I thin click on the " ingore and Install" buton and it says 

It must be true--men don't read instructions!  :P

You could try to purge the package I suppose.

---

### Post by leopar on 2012-01-29
Appreciate this is an old thread but this may still be of interest.

Here's the solution suggested by poliviero in the french ubuntu forum which he in turn picked up from a german forum:

He suggests that you reinstall the entire mono environment from ubuntu repository but this may not be necessary:

$ sudo apt-get build-dep monodevelop 

then force install the .deb Usenext package (I use GDebi)
then run the following command to launch usenext:

 $ exec mono --runtime=v4.0 /usr/lib/usenext/UseNeXTLauncher.exe "$@" 

Do this at your own risk, I'm no expert but it works for me though not very elegant. Hopefully Linux users will be better served by the next update of UseNext.

Fyi, i'm dual booting Ubuntu 11.10 with Win7 on 64 bit system.

---

### Post by recluce on 2012-01-29
Don't use UseNext - the company has an extremely shady reputation and the client is junk.

If you want to use UseNet (UseNext sells access to UseNet, that is all they do), get a regular account with one of hundreds of companies that sell access. Reputable companies include giganews, astranews, easynews.com and many others. Install sabnzbd+ (in the repos) for binary downloads and use a spotting forum or NZB indexer to find content (hopefully legal content only!). 

There are literally tons of UseNet "how tos" available on the net, just google for it.

---

### Post by ricey155 on 2012-09-12
no issues with USENEXT for over 4 years works well 

the workaround works cheers for sharing

---

