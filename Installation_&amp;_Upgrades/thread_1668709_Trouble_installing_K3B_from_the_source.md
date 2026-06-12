---
title: "Trouble installing K3B from the source"
date: 2011-01-16
forum: Installation &amp; Upgrades
---

### Post by vasyl4 on 2011-01-16
Hey, I'm having trouble installing K3B(version k3b-2.0.2, because in synaptic there is older 1.91.version) on Ubuntu 10.04 from the source.
After downloading the k3b-2.0.2.tar.bz2 and extracting that file i did :

mkdir build
cd build

when i`m trying to do cmake i get this:

vasyl@vasyl-desktop:~/k3b-2.0.2/build$ cmake ..
CMake Error at /usr/share/cmake-2.8/Modules/FindKDE4.cmake:98 (MESSAGE):
ERROR: cmake/modules/FindKDE4Internal.cmake not found in
/home/vasyl/.kde/share/apps;/usr/share/kde4/apps
Call Stack (most recent call first):
CMakeLists.txt:52 (find_package)


-- Configuring incomplete, errors occurred!
vasyl@vasyl-desktop:~/k3b-2.0.2/build$

So what should i do? 
Please help.

---

### Post by Scooby-2 on 2012-01-29
On the k3b.org site if you click on "Installation" on the left hand side you get a page which tells you how to build k3b from source. The text is as follows:
> Installation from Source                    
[LIST]
[*]The first thing to do is to get the requirements installed (see [the requirements page]("http://k3b.plainblack.com/requirements")). You need at least install the Qt and kdelibs devel packages.
For a working audio player you need the kdemultimedia devel package.
For mp3 decoding support you need to install libmad.
For FLAC decoding and encoding support you need to install the FLAC++ libraries and headers.
For Ogg Vorbis decoding and encoding you need to install the Ogg Vorbis libraries and headers.
[*]Get the source from [the K3b download page]("http://k3b.plainblack.com/download") (Example: k3b-1.0.tar.bz2)
[*]Extract the source to a temporarly directory: 
# tar -xjvf k3b-1.0.tar.bz2 and change to the created directory: # cd k3b-1.0
[*]Configure the source: 
# ./configure (with older versions of K3b one needed to provide a prefix but the new KDE build system is able to guess it properly) 
 After the configuration finished you will see a summary. If one of the features you want to be enabled is not you need to check the requirements again.
[*]Start the compilation: 
# make
[*]And finally if the command above did not show any errors install K3b: 
# su -c "make install" (You will have to type in your root password.)
[*]Now you may start K3b from the KMenu (Multimedia section) or run it from a shell or the Alt-F2 menu via 'k3b'.
[/LIST]
I tried this but it doesn't work as there is no configure script included in the source so the "./configure" fails with a not found message. There are no instructions in the download, either.

Here's how I installed version 2.0.0, which appears to be the latest version supported by Lucid:

Download the file libk3b6_2.0.0-0ubuntu1~lucid2_i386.deb from:
http://launchpadlibrarian.net/51791014/libk3b6_2.0.0-0ubuntu1%7Elucid2_i386.deb

Double-click the file to start the Package Installer. Ignore the message "An older version is available in a software channel" by just pressing close. Click "Install package" and it will also install libkcddb4 and libflac++6 which are required.

Download the file k3b-data_2.0.0-0ubuntu1~lucid2_all.deb from:
http://launchpadlibrarian.net/51791011/k3b-data_2.0.0-0ubuntu1%7Elucid2_all.deb

and install it as above, ignoring the message again.

Download the file k3b_2.0.0-0ubuntu1~lucid2_i386.deb from:
http://launchpadlibrarian.net/51791010/k3b_2.0.0-0ubuntu1%7Elucid2_i386.deb

and install it as above.

I hope this helps you. All of this is out there on the Web but scattered - I couldn't find it in this form.

:biggrin:

P.S. Sorry about the lack of hyperlinks. For some reason when I try to insert them they are shortened to contain full stops, and then they don't work. So a bit of copying and pasting is required.

---

