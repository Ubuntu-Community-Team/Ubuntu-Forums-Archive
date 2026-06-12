---
title: "Compilation Installation problem"
date: 2005-11-04
forum: Installation &amp; Upgrades
---

### Post by orly on 2005-11-04
Hello all,
First I would like to say that I'm a newbie in Linux-related topics, although I have searched and searched again the Internet before posting this subject.
The fact is that I installed Ubuntu 5.10 from the server CD download distribution, and I want to use Webmin from the server, but it didn't installed any GUI and while trying:
apt-get install x-system-core
it wasn't found, my PC has no connection to Internet yet, so I had 2 options:

1) My PC has a motorola sm56 winmodem, I found a linux driver for it, but didn't know how to compile it, after days and days....
apt-get install gcc gcc-4.0 make etc etc etc, but still unsuccessfully, here is the Makefile:
... 
all: 
echo "Writing Version.c"
echo "#define UTS_RELEASE \""`uname -r`"\"" >version.c
echo "const char __module_kernel_version[] __attribute__((section(\".modinfo\" ))) = \"kernel_version=\"UTS_RELEASE;">>version.c
echo "#ifdef MODVERSIONS" >>version.c
echo "const char __module_using_checksums[] __attribute__((section(\".modinfo\"))) = \"using_checksums=1\";" >>version.c
echo "#endif">>version.c
echo Compiling version.c
gcc -DLINUX -D__KERNEL__ -DMODULE -Wall -O -fomit-frame-pointer -o version.a -c version.c
echo Linking output version.a with Motorola proprietary sm56.lib 
ld -r -o sm56.a version.a sm56.lib
echo Updating kernel symbols in output sm56.a
objcopy --redefine-sym kmalloc=kmalloc_hack --redefine-sym __vmalloc=vmalloc_hack sm56.a sm56_h.a
echo Compiling kmhack.o from input kludge.c
gcc -DLINUX -D__KERNEL__ -DMODULE -Wall -O -I/usr/src/linux-2.4/include -fomit-frame-pointer -o kmhack.o -c kludge.c 
echo Linking kmhack.o with sm56_h.a to generate sm56.o
ld -r -o sm56.o sm56_h.a kmhack.o
echo "Please Run \"make install\" "

clean:
rm -f *.a
rm -f *~
rm -f *.o
rm -f version.c 
rm -f *.oo
install:
make all
#Took From Original Sm56setup
chmod u+x ./sminst.sh
./sminst.sh

now, the all label calls:
gcc -DLINUX -D__KERNEL__ -DMODULE -Wall -O -I/usr/src/linux-2.4/include -fomit-frame-pointer -o kmhack.o -c kludge.c 
I know Ubuntu doesn't use that Kernel, I know it's 2.6.12.9 or something similar that:
uname -r
could give me.
but I haven't found anything under /usr/src

2) On the other hand I downloaded at work:
X.org, fvwm, wdm, xterm, fonts, firefox, openssl and ssleay and while trying to compile X.org I'm getting errors because there are compilation packages that are not shipped with the server installation CD as bison, and some of this:
binutils cpp cpp-4.0 fetchmail flex gcc gcc-4.0 libarchive-zip-perl libc6-dev libcompress-zlib-perl libdb4.3-dev libpcre3 libpopt-dev linux-kernel-headers lynx m4 make ncftp nmap openssl perl perl-modules unzip zip zlib1g-dev autoconf automake1.9 libtool bison autotools-dev
While runing ./configure of fvwm, it depends on X

My questions are:
_ Supposing you could help me to use the winmodem, is it factible to get all compilation packages from universal repositories using dial-up?
_ What compilation packages am I missing in order to compile X besides bison?
_ How can I get those packages <> than apt-get?
I have Kubuntu installation CD, can I use it to include X.org and compilation packages in a PC that get installed using the Server-specific distribution CD? and if it could be done, how? what the sources.list will look like?

Any help will be appreciated,
Regards,
Orlando Otero

---

### Post by drashkeev on 2005-11-04
Well, first of all, it's apt-get install x-window-system-core. Is there any reason you're trying to compile X? Do you actually need a custom X? If not, then all you need to do is make sure apt knows about your cdrom. Edit the file /etc/apt/sources.list . There should be a source line for the cdrom. Uncomment it (make sure it doesn't have a # in front of the line), and you'll be fine. Not sure if the server distribution includes X on the cdrom, though.

If you want to go ahead and use the kubuntu disk, all you have to do is run (as root)

apt-cdrom add
apt-get update
apt-get install whatever_you_want

What is the exact error you're getting in compiling the winmodem driver? The way you have it worded, it could be a missing compiler, bad libraries, or no kernel sources.

Dialup is slow. X is big. quite big, especially if you count the fonts it insists on downloading. So is gnome. It would take you a few days of solid downloading to download it all. I know. I've been in the same boat :-) Perhaps you can use a friend's fast connection, or something. It's not cool if your phone line is tied up.

Yours,

Dmitry

---

### Post by orly on 2005-11-04
Thanks Dmitry for your replay,
And yes, the server CD doesn't come with X, I'll try:
apt-cdrom add  <Actually another CD(Kubuntu)>?
apt-get update
apt-get install whatever_you_want

Actually I have the source for X(don't need to download using dial-up), but missing compiler package, anyway, I don't want custom X, I just followed some tutorial steps in order to have some GUI enable in Ubuntu Server by downloading sources and compiling them.

The error related to winmodem compile process is I think due to missing kernel sources. I don't know if Ubuntu stores the sources in /usr/src/<kernel-version>/ directory or a different one, but the fact is that there is no "kernel directory" under /usr/src/.
Can I just download the kernel sources and copy them into that location? or the Installation CD comes with them?

Ah, I dont know if Server CD and Kubuntu CD store the same content in /etc/apt/sources.list, if not, please, anyone could tell me how the first 3 lines of /etc/apt/sources.list in a Kubuntu installation looks like?

Regards,
Orlando Otero

---

### Post by mo_x on 2005-11-04
First 3 lines of my /etc/apt/sources.list:
```
deb cdrom:[Kubuntu 5.10 _Breezy Badger_ - Release amd64 (20051012)]/ breezy main restricted

deb [http://nl.archive.ubuntu.com/ubuntu](http://nl.archive.ubuntu.com/ubuntu) breezy main restricted
deb-src [http://nl.archive.ubuntu.com/ubuntu](http://nl.archive.ubuntu.com/ubuntu) breezy main restricted
```
To compile a kernel module you need to install the kernel headers . Look for something like linux-headers or kernel-headers.

---

