---
title: "[SOLVED] Problems with todays updates ..."
date: 2007-11-14
forum: Installation &amp; Upgrades
---

### Post by TR82 on 2007-11-14
Update Manager reliably tells me I have 28 updates to install today. It's just general run of the mill updates, I think.

But not  all changes have been applied. The terminal panel gives me the following error message :

dpkg: parse error, in file '/var/lib/dpkg/status' near line 467 package 'libgnome-speech7':
empty value for version

Any suggestions ? 

Thanks very much :)

---

### Post by erginemr on 2007-11-14
Hello,

Assuming what the error message is correct (that is, the message is pointing the right direction), there is a file "/var/lib/dpkg/status" that is responsible for keeping track of all installed packages in a Debian/Ubuntu system. Apparently, the file in your system has a missing version number under the section for package "libgnome-speech7".

It is easy to check it out. Could you please run the following two commands from the console:

sudo cp /var/lib/dpkg/status /var/lib/dpkg/status.bak

sudo gedit /var/lib/dpkg/status 

The first command takes a backup of the original dpkg database, which you can restore in case of any problem with:
sudo cp /var/lib/dpkg/status.bak /var/lib/dpkg/status

And the second command opens the file in question inside Gnome Editor with root permissions (so that you can make changes and write to it.)

Look for the keyword "Package: libgnome-speech7". Be careful though, the word "libgnome-speech7" exists in several places, as part of the other packages listing their dependencies. You need to find the package itself with "Package: libgnome-speech7".

That part in my "status" file is as follows:
.........
Package: libgnome-speech7
Status: install ok installed
Priority: optional
Section: libs
Installed-Size: 224
Maintainer: Ubuntu Accessibility Developers <ubuntu-accessibility-devel@lists.ubuntu.com>
Architecture: i386
Source: gnome-speech
Version: 1:0.4.16-0ubuntu2
Depends: libbonobo2-0 (>= 2.15.0), libc6 (>= 2.6-1), libespeak1 (>= 1.27), libglib2.0-0 (>= 2.14.0), liborbit2 (>= 1:2.14.8), libstdc++6 (>= 4.2.1)
Recommends: festival
Conflicts: libgnome-speech3
Description: GNOME text-to-speech library
 The GNOME Speech library gives a simple yet general API for programs
 to convert text into speech, as well as speech input.
 .
 Multiple backends are supported by the GNOME Speech library, but
 currently only the Festival, espeak, and speech-dispatcher
 backends are enabled in this package; the other backends require
 either Java or proprietary software.
Original-Maintainer: Mario Lang <mlang@debian.org>
.........

Check and compare that section in your file with mine and if the version number for libgnome-speech7 is really misssing, then complete the line that says version according to my model.

Save it and close. Finally, run the following command from the console to put the changes to effect:
sudo aptitude update

And retry to update your system via the Update Manager.

Good Luck...

---

### Post by TR82 on 2007-11-14
Hi erginemr,

This is the return I got on the file you mentioned.

Package: libgnome-speech7 
Status: install ok installed 
Priority: optional 
Section: libs 
Installed-Size: 224 
Maintainer: Ubuntu Accessibility Developers <ubuntu-accessibility-devel@lists.ubuntu.com> 
Architecture: i386 
Source: gnome-speech 
Version: 1:-0ubuntu2 
Depends: libbonobo2-0 (>= 2.15.0), libc6 (>= 2.6-1), libespeak1 (>= 1.27), libglib2.0-0 (>= 2.14.0), liborbit2 (>= 1:2.14.8), libstdc++6 (>= 4.2.1) 
Recommends: festival 
Conflicts: libgnome-speech3 
Description: GNOME text-to-speech library

As you can see, the version number differs to that you have. I'm unsure why that might be, I did a clean install only on Saturday, haven't altered anything and the only changes to Ubuntu have been those suggested at the weekend by Update Manager itself after the install.

That being said, I've followed your suggestion and amended the version number.

And Eureka ! The updates have all installed successfully.

Thanks very much for your help, I do very much appreciate it when folks go out of their way to help others. Hopefully one day I'll be in a similar position and be able to help others too.

Cheers again. very much appreciated. :)

---

### Post by erginemr on 2007-11-14
):P

You are welcome. I am very glad that you have solved the problem. I am sure that you will start helping other people very soon.

Have a nice day.

---

