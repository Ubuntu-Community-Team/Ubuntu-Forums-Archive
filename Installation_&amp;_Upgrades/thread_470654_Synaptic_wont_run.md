---
title: "Synaptic wont run"
date: 2007-06-11
forum: Installation &amp; Upgrades
---

### Post by naycon on 2007-06-11
Installed Ubuntu Feisty yesterday, my first atempt to use linux. I ran into some problems though. When trying to run synaptic, nothing happens. Runing it through a terminal with "sudo synaptic" gives the following message:

synaptic: error while loading shared libraries: /usr/lib/libpangox-1.0.so.0: invalid ELF header

Any ideas what I can do to solve this? 

The normal add/remove program doesn't work either, but I don't know how to start that one through a terminal so I don't have any info on why it wont work (it starts, but wont install anything when I click apply. It just updates the list of apps once more).

---

### Post by naycon on 2007-06-11
I just ran update-manager through a terminal with the -d flag and it gives me this:

naycon@Naycon:~$ sudo update-manager -d
warning: could not initiate dbus
could not send the dbus Inhibit signal: org.freedesktop.DBus.Error.NoReply: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.
/usr/sbin/synaptic: error while loading shared libraries: /usr/lib/libpangox-1.0.so.0: invalid ELF header

I've been having problems with the update-manager also, as it wouldn't install any updates, just refresh the list (iow the same thing as the add/remove program). Is there any way to fix the pibpangox-1.0.so file? Seems like it's mentioned in connection with my problems...

---

### Post by grekei on 2007-06-11
No expert in this matter but I have had several problems with synaptic .It appears that if something goes wrong during a download (in my case a broken package) synaptic does not clear itself and the unresolved action stops it from working on anything else and I have not been able to find an easy way to clear it.The following is a  link to a post I made some time ago  I have used this solution to clear synaptic on 2 occasions since and it has worked fine.Solution on page two.

[http://ubuntuforums.org/showthread.php?t=404876](http://ubuntuforums.org/showthread.php?t=404876)

 I think your problem may be similar except that you have an error message rather than a broken package (my case)  stuck in synaptic.The source of the error message is outside my ability at present.It may be prudent to try "Launchpad" before proceeding .Your question WILL be answered and answered by someone that knows more than me.Good luck.
  Cheers:)

---

### Post by bapoumba on 2007-06-11
Please open a terminal (> Accessories > Terminal) and paste the complete output to:
```
sudo aptitude update
```

---

### Post by naycon on 2007-06-11
Your will is my command:

:~$ sudo aptitude update
Get:1 [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) feisty Release.gpg [191B]
Ign [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) feisty/main Translation-en_US
Get:2 [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security Release.gpg [191B]
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Translation-en_US
Ign [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) feisty/restricted Translation-en_US
Ign [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) feisty/universe Translation-en_US
Ign [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) feisty/multiverse Translation-en_US
Ign [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) feisty/main Translation-en_US
Get:3 [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) feisty-updates Release.gpg [191B]
Ign [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) feisty-updates/main Translation-en_US
Ign [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) feisty-updates/restricted Translation-en_US
Hit [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) feisty Release
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Translation-en_US
Hit [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) feisty-updates Release             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security Release              
Hit [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) feisty/main Packages
Hit [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) feisty/restricted Packages
Hit [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) feisty/main Sources
Hit [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) feisty/restricted Sources
Hit [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) feisty/universe Packages
Hit [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) feisty/multiverse Packages
Hit [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) feisty/multiverse Sources
Hit [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) feisty/main Packages
Hit [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) feisty-updates/main Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Packages
Hit [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) feisty-updates/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Sources
Hit [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) feisty-updates/main Sources
Hit [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) feisty-updates/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Packages
Fetched 3B in 0s (5B/s)  
Reading package lists... Done

---

### Post by bapoumba on 2007-06-11
So your system looks up to date, with feisty.

Do you get any error running 
```
update-manager
``` 
from a terminal ? (no sudo or gksudo please).

---

### Post by naycon on 2007-06-11
Running update-manager without sudo in front of it leaves no errors in the terminal. I can't say if it works for updateing my system, since I managed to update everything using apt-get instead.

 (Big thanks for trying to help me out!)

---

### Post by bapoumba on 2007-06-11
> **naycon said:**
> Running update-manager without sudo in front of it leaves no errors in the terminal. I can't say if it works for updateing my system, since I managed to update everything using apt-get instead.

 (Big thanks for trying to help me out!)
I may be wrong here, but I do not think you need to be root to run a regular update with update-manager (for an upgrade to a newer ubuntu version, yes, you do). Anyone knows ?
And in any case, update-manager being a graphical application, you should use **gksudo** ;)

---

### Post by naycon on 2007-06-11
I think you missunderstood something, because the update-manager does start, but it won't do any updates. Doesn't matter if I run it from a menuitem or if I start it from the terminal using "sudo update-manager", the result is the same. It'll run, and when clicking "install updates" I have to fill in my password and after that it updates the list and does nothing more.

I know that I may use various other ways of installing apps and updating, but the thing is that I'm experiencing a few quite anoying bugs here, which won't let me start certain applications (gaim, gnome-terminal to mention two). Also, ubuntu seem to be built on the ability to autoupdate or autoinstall sometimes (enabling restricted drivers for example), which wont work. It is also quite nice to be able to browse through a list of avaible software to install from within the OS, altough it can be done in alternative ways. 

Now, I'm thinking it might be a problem with the pango library. Is there any way to replace the libpangox-1.0.so file with a freshly downloaded one?

---

### Post by bapoumba on 2007-06-11
may be reinstall it ?
```
sudo apt-get --reinstall install libpango1.0-common
```
(or with aptitude)

Here is the description:
```
~$ aptitude show libpango1.0-common
Package: libpango1.0-common
State: installed
Automatically installed: no
Version: 1.16.2-0ubuntu1
Priority: optional
Section: misc
Maintainer: Ubuntu Desktop Team <ubuntu-desktop@lists.ubuntu.com>
Uncompressed Size: 127k
Depends: debconf | debconf-2.0, defoma (>= 0.11.1), fontconfig (>= 2.1.91)
Recommends: x-ttcidfont-conf, libpango1.0-0
Suggests: ttf-kochi-gothic, ttf-kochi-mincho, ttf-thryomanes, ttf-baekmuk,
          ttf-arphic-gbsn00lp, ttf-arphic-bsmi00lp, ttf-arphic-gkai00mp,
          ttf-arphic-bkai00mp
Replaces: libpango0, libpango-common (< 1.0.0)
Description: Modules and configuration files for the Pango
 Pango is a library for layout and rendering of text, with an emphasis on
 internationalization. Pango can be used anywhere that text layout is needed.
 however, most of the work on Pango-1.0 was done using the GTK+ widget toolkit
 as a test platform. Pango forms the core of text and font handling for
 GTK+-2.0. 
 
 Pango is designed to be modular; the core Pango layout can be used with four
 different font backends: 
 * Core X windowing system fonts 
 * Client-side fonts on X using the Xft library 
 * Direct rendering of scalable fonts using the FreeType library 
 * Native fonts on Microsoft backends 
   
 This package contains the Pango modules and the configuration files which Pango
 needs.
```

Or may be the symlink is not correct ?
```
/usr/lib$ ls -l libpangox-1.0.so.0
lrwxrwxrwx 1 root root 25 2007-04-21 18:56 libpangox-1.0.so.0 -> libpangox-1.0.so.0.1600.2

```

---

### Post by naycon on 2007-06-11
Used the command to reinstall it, and it didn't do any good. Also checked the other two things, and they are identical to the ones you posted (except for the date in the last one obiously). Any ideas?

---

### Post by bapoumba on 2007-06-11
Hmm, I already looked around, but may be not to the proper places.
(and the date much depend on the date it's been installed).

Do you run KDE ?

---

### Post by naycon on 2007-06-11
Nope, just "normal" ubuntu (gnome I guess it is?) not kubuntu or any other flavour.. 

Would it be possible to delete the whole libpango directory and then run apt-get install to get a realy fresch copy, or wont that do anything that reinstall wouldn't do?

I guess the solution is to understand what the "invalid ELF header" message means? Any clue?

---

### Post by bapoumba on 2007-06-11
> **naycon said:**
> Nope, just "normal" ubuntu (gnome I guess it is?) not kubuntu or any other flavour.. 

Would it be possible to delete the whole libpango directory and then run apt-get install to get a realy fresch copy, or wont that do anything that reinstall wouldn't do?

I guess the solution is to understand what the "invalid ELF header" message means? Any clue?

No, do not delete. If anything, remove or purge with synaptic, apt-get or aptitude.
I had been looking about  the error message, i'm looking again...
Anyone ?

---

### Post by naycon on 2007-06-11
A friend of mine (not running ubuntu but still using linux) made me run 
```
less /usr/lib/libpangox-1.0.so.0.1600.2
```
It would be nice if someone could do the same and check if less displays anything (a good guess should be something about ELF-headers), or if it says that it is a file containing data (shows just gibberish if you choose to read it). My friend got a readable file, but mine just shows gibberish..

---

### Post by bapoumba on 2007-06-11
```
~$ less /usr/lib/libpangox-1.0.so.0.1600.2
"/usr/lib/libpangox-1.0.so.0.1600.2" may be a binary file.  See it anyway? 

```
gibberish here too.

---

### Post by naycon on 2007-06-11
Ok. Anyone know if it's supposed to be that way? 

Edit: Every once in a while everybody files a dumb question, and this time it was my turn. Since you got everything working and you got it in data, it probably should be that way. =).

---

### Post by bapoumba on 2007-06-11
Wild guess: not running mixed 32and 64-bits apps ?

---

### Post by naycon on 2007-06-11
Nopp, just installed 32 bit ubuntu on my Latitude D800 (celeron M 1.7 GHz), and no 64 bits applications added as far as I'm conserned.

---

### Post by bapoumba on 2007-06-11
There are many things relevant to libs and the general idea is here (its an Xlib in that case):
[https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/119340]("https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/119340")
So in your case, which package to reinstall or which symlink to restore ? I have no clue, sorry.
I searched about lipango* in and out. It's quite late here, may be someone else will come up with a brilliant and simple fix ;)

---

### Post by naycon on 2007-06-12
Thanks a lot for helping me out. Someone suggested it might be a problem with my disk, so Im about to do a disk check and after that a reinstall of ubuntu to see if that fix the problem. Im running the liveCD right now, and here everything works like a charm.. Ill get back to you and report the results of the diskcheck and the reinstall. Again, thanks for taking time to help, its really appreciated!

---

### Post by naycon on 2007-06-12
Looks like running
```
e2fsck -c /dev/sda3 -C 0

OBS! Notes to people with similar problems.
Note1: Dont run that comman unless you have NOT booted into your ubuntu diskinstall 
(since the command cant operate on a filesystem in use). Boot from the liveCD instead 
and use a terminal from there to execute the command.

Note2: Since I'm faaar from an expert regarding this, I just want to say that /dev/sda3 
probably refer to MY ubuntu disc, that is the partion on my disc that I installed ubuntu 
on. I'm not sure that it's always like that, so either check with someone who realy knows
 about that (it involved using the mount-command), or maybe someone could correct 
me here below?
```

from a terminal when booted from a liveCD solved the problem. Turns out it was 0.8% of my disksectors that were damaged and running that command fixed the problem. So now I can start synaptic and install applications trought "add/remove". 

Still got problems running the update-manager (something about "could not initiate dbus") but I think I can live with that since it's possible to use apt-get upgrade with the same result, right?

---

