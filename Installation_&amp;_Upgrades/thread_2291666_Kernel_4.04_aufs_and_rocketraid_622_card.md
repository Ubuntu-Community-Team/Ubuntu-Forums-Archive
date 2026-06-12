---
title: "Kernel 4.04 aufs and rocketraid 622 card"
date: 2015-08-21
forum: Installation &amp; Upgrades
---

### Post by Robert_Riley on 2015-08-21
Salutations!

This is my first post here, and of course, it is due to a lack of knowledge. I have tried searching for the answer, but alas, my google skills are not as strong as they could be. 

Background information: For the last several years, I have toyed with Ubuntu, running a media server at home by following the guides at [www.havetheknowhow.com]("http://www.havetheknowhow.com/").
I started with version 10.04 Server LTS. That was fine, until I needed more storage, and ended up destroying my raid array, and causing a kernel panic which I did not know how to resolve.
SO I rebuilt, and this time I used 12.04, and added some drives internally, with FlexRAID running on top to make a nice drive pool, and not ever need to worry about being able to recover from a "real Raid" failure.

I liked it. So I bought an external drive enclosure, and added 4 more 3TB drives. This was not without its challenges, but I overcame them by searching and good old fashioned hands on trial and error.
I followed this guide while under version 12.04: [https://help.ubuntu.com/community/RocketRaid](https://help.ubuntu.com/community/RocketRaid) and was able to get all of my drives working the way I wanted. 18 months go by with nary a problem, then, out of the blue, my main boot drive becomes corrupt and will not boot.

Of to the rebuild I go....now on version 14.04 LTS server. Minor issues having to go back to the guide and get my card to work with the external enclosure, but I got there. Except now I cannot install Flexraid. It needs the 32 bit libraries, and when I try to install, I get a list of alternates. So I install those.

Still not able to make / make install. SO I go looking for another solution, and come across SnapRaid. It works, is free, and looks like a winner to me, except that the pool function has issues with windows machines. I cannot use any of the media on my 20 TB share.

Keep in mind, at this point, I have Ubuntu server 14.04 with Kernel 3.13 (I believe) and my Rocket Raid 622 card with the 4 external drives all working, and SnapRaid is setup and working, I just cannot access the files via Samba on windows machines.

I find this bit of info and proceed to follow the guide: [http://zackreed.me/articles/90-ubuntu-14-04-with-4-0-4-kernel-and-latest-aufs-from-source](http://zackreed.me/articles/90-ubuntu-14-04-with-4-0-4-kernel-and-latest-aufs-from-source)
Once completed I have a custom Kernel 4.04 with aufs. My Rocket Raid 622 did not make it over to the new kernel, but I figure, no problem, I just did this, How hard can it be..so I dive in and I find the following guide for Kernel 4.x:[https://blog.hqcodeshop.fi/archives/266-HighPoint-RocketRAID-620-Linux-driver.html](https://blog.hqcodeshop.fi/archives/266-HighPoint-RocketRAID-620-Linux-driver.html)
It points me to this info on github: [https://github.com/HQJaTu/rr62x](https://github.com/HQJaTu/rr62x)


Now when I try to follow the guide using this info, I am at a loss to get the right kernel Version in the makefile.

I am currently trying this: # make install KERNELDIR=/lib/modules/4.0.4-aufs/build
I get an error about it not recognizing my kernel version, but I do not know enough to modify the code in the makefile.def to fix it.

Here is the output from my make and make install commands.

Any help would be gratefully accepted, as I am just a NOOOB that can follow a guide...Mostly...

root@uhost:/home/justin/rr62x-linux-src-v1.3.3/product/rr62x/linux# make
make[1]: Entering directory `/opt/src/4.0.4aufs/linux-4.0.4'
CC [M] /home/justin/rr62x-linux-src-v1.3.3/product/rr62x/linux/.build/os_linux.o
CC [M] /home/justin/rr62x-linux-src-v1.3.3/product/rr62x/linux/.build/osm_linux.o
CC [M] /home/justin/rr62x-linux-src-v1.3.3/product/rr62x/linux/.build/div64.o
CC [M] /home/justin/rr62x-linux-src-v1.3.3/product/rr62x/linux/.build/hptinfo.o
CC [M] /home/justin/rr62x-linux-src-v1.3.3/product/rr62x/linux/.build/config.o
LD [M] /home/justin/rr62x-linux-src-v1.3.3/product/rr62x/linux/.build/rr62x.o
Building modules, stage 2.
MODPOST 1 modules
WARNING: could not find /home/justin/rr62x-linux-src-v1.3.3/product/rr62x/linux/.build/.him_magni.o.cmd for /home/justin/rr62x-linux-src-v1.3.3/product/rr62x/linux/.build/him_magni.o
LD [M] /home/justin/rr62x-linux-src-v1.3.3/product/rr62x/linux/.build/rr62x.ko
make[1]: Leaving directory `/opt/src/4.0.4aufs/linux-4.0.4'
root@uhost:/home/justin/rr62x-linux-src-v1.3.3/product/rr62x/linux#
root@uhost:/home/justin/rr62x-linux-src-v1.3.3/product/rr62x/linux#
root@uhost:/home/justin/rr62x-linux-src-v1.3.3/product/rr62x/linux#
root@uhost:/home/justin/rr62x-linux-src-v1.3.3/product/rr62x/linux#
root@uhost:/home/justin/rr62x-linux-src-v1.3.3/product/rr62x/linux#
root@uhost:/home/justin/rr62x-linux-src-v1.3.3/product/rr62x/linux# make install
make[1]: Entering directory `/opt/src/4.0.4aufs/linux-4.0.4'
CC [M] /home/justin/rr62x-linux-src-v1.3.3/product/rr62x/linux/.build/os_linux.o
CC [M] /home/justin/rr62x-linux-src-v1.3.3/product/rr62x/linux/.build/osm_linux.o
CC [M] /home/justin/rr62x-linux-src-v1.3.3/product/rr62x/linux/.build/div64.o
CC [M] /home/justin/rr62x-linux-src-v1.3.3/product/rr62x/linux/.build/hptinfo.o
CC [M] /home/justin/rr62x-linux-src-v1.3.3/product/rr62x/linux/.build/config.o
LD [M] /home/justin/rr62x-linux-src-v1.3.3/product/rr62x/linux/.build/rr62x.o
Building modules, stage 2.
MODPOST 1 modules
WARNING: could not find /home/justin/rr62x-linux-src-v1.3.3/product/rr62x/linux/.build/.him_magni.o.cmd for /home/justin/rr62x-linux-src-v1.3.3/product/rr62x/linux/.build/him_magni.o
LD [M] /home/justin/rr62x-linux-src-v1.3.3/product/rr62x/linux/.build/rr62x.ko
make[1]: Leaving directory `/opt/src/4.0.4aufs/linux-4.0.4'
Can not get kernel version from rr62x..
make: *** [install] Error 1
root@uhost:/home/justin/rr62x-linux-src-v1.3.3/product/rr62x/linux#

---

### Post by Irihapeti on 2015-08-22
Thread closed.

Please don't post duplicate threads. They cause confusion and reduce the ability of the community to help.

Your other thread has been moved to the server section.

---

