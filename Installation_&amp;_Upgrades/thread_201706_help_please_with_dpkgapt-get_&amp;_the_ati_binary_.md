---
title: "help please with dpkg/apt-get &amp; the ati binary drivers"
date: 2006-06-22
forum: Installation &amp; Upgrades
---

### Post by herot on 2006-06-22
i tried to install the Ati binary drivers (8.25.18) for my video card and screwed something up...  i went through the ati driver installer ok, and installed the .deb files it created... but it didn't work so i wanted to remove it i tried :

```

root@Armagh:/home/herot/ati# ls
ati-driver-installer-8.25.18-x86.run
fglrx-control_8.25.18-1_i386.deb
fglrx-installer_8.25.18-1_i386.changes
fglrx-kernel-source_8.25.18-1_i386.deb
fglrx-sources_8.25.18-1_i386.deb
usr
xorg-driver-fglrx_8.25.18-1_i386.deb
xorg-driver-fglrx-dev_8.25.18-1_i386.deb
root@Armagh:/home/herot/ati# dpkg -r *.deb
dpkg: you must specify packages by their own names, not by quoting the names of the files they come in

Type dpkg --help for help about installing and deinstalling packages [*];
Use `dselect' or `aptitude' for user-friendly package management;
Type dpkg -Dhelp for a list of dpkg debug flag values;
Type dpkg --force-help for a list of forcing options;
Type dpkg-deb --help for help about manipulating *.deb files;
Type dpkg --licence for copyright licence and lack of warranty (GNU GPL) [*].

Options marked [*] produce a lot of output - pipe it through `less' or `more' !
root@Armagh:/home/herot/ati#

```

AND

```

root@Armagh:/home/herot# apt-get remove xorg-driver-fglrx -f --purge
Reading package lists... Done
Building dependency tree... Done
The following packages will be REMOVED:
  xorg-driver-fglrx
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 26.3MB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 108343 files and directories currently installed.)
Removing xorg-driver-fglrx ...
dpkg-divert: rename involves overwriting `/usr/lib/libGL.so.1' with
  different file `/usr/lib/fglrx/libGL.so.1.xlibmesa', not allowed
dpkg: error processing xorg-driver-fglrx (--remove):
 subprocess post-removal script returned error exit status 2
Errors were encountered while processing:
 xorg-driver-fglrx
E: Sub-process /usr/bin/dpkg returned an error code (1)
root@Armagh:/home/herot#

```

alot of stuff got broke (amarok and mplayer)

and i get this error with glxgears:

```

herot@Armagh:~$ glxgears -printfps
glxgears: error while loading shared libraries: libGL.so.1: cannot open shared object file: No such file or directory
herot@Armagh:~$

```
[COLOR="Red"]
*I believe i have found enough info in [[COLOR="Red"][COLOR="RoyalBlue"]this[/COLOR][/COLOR]]("http://www.ubuntuforums.org/showthread.php?t=188326&highlight=binary+ati+drivers") post to solve this problem... thanks!*[/COLOR]

---

### Post by gerbman on 2006-06-22
If you can't get it working, why not just install the driver that's in the repository?

[https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

---

### Post by catlett on 2006-06-22
> root@Armagh:/home/herot/ati# dpkg -r [COLOR="Red"]*.deb[/COLOR] > you must specify packages by their own names, not by quoting the names of the files they come in

What is the deb file? You can't just enter *
Hopefully if you remove each deb file you will get the result you want.
You should be running ```
dpkg -r fglrx-control_8.25.18-1_i386.deb
``` ```
dpkg -r fglrx-kernel-source_8.25.18-1_i386.deb
``` Etc. Whatever you installed with dpkg -i or whatever debs the installer installed,  have to remove with dpkg -r. I don't know all the file names you used but whatever they are remove them one at a time with dpkg -r. If the package is in synaptic like gerbman says then you definately want to install them from there.

---

### Post by herot on 2006-06-22
yep i figured it out guys... 

What this guy said helped alot!!


Quote:
Originally Posted by Ivhassel
If you tell me how to run that screensaver, while displaying fps, I'll give you my results. As we run the same hardware, I'm particularly interested to see if either of us can get even better performance out of this card.

i don't know how to see the fps for the screensavers, i was just giving you a visual estimate.

BUT i have some good news

i've found a simple solution on another thread, and it seems to be working on my dad's machine with the radeon 9000 pro:

[http://ubuntuforums.org/showthread.php?t=185033](http://ubuntuforums.org/showthread.php?t=185033)

it boils down to two steps:

1) install the *new* ATI drivers, the ones packaged and included in the dapper repositories. you can use the instructions here (from the ubuntu wiki) to do this.
2) replace a single file named /usr/lib/libGL.so.1.2 with the one provided in the above forum thread, one of the people posting (joshrobinson) was great enough to host the file on a server. the file is attached with post #6 in that thread.

anyway, the drivers are installed on my dad's machine, everything seems to be working, and the screensavers are screaming fast . also, judging by the responses in that thread, it worked for a lot of people. i hope it works for everybody in this thread too!

also, know that i did a clean install of dapper before doing the above two steps. it probably wasn't neccessary, but i did it just in case.

---

