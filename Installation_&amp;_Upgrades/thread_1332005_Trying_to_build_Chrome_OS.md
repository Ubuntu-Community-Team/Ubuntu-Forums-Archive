---
title: "Trying to build Chrome OS"
date: 2009-11-19
forum: Installation &amp; Upgrades
---

### Post by wesg on 2009-11-19
I've started building Google's Chrome OS and have run into a stumbling block. For the most part, Google's build/install process is quite straight forward -- run some Bash scripts and away you go -- but for some reason the script that creates a chroot environment is not working. It simply says "Mounting chroot environment; Unmounting chroot environment". 

Since this is all still so bleeding edge, I'm a little stuck. Are there any users out there who are trying to build Chrome? Any suggestions about how I can get the chroot script to work properly?

BTW the build instructions are [http://sites.google.com/a/chromium.org/dev/chromium-os/building-chromium-os/build-instructions]("http://sites.google.com/a/chromium.org/dev/chromium-os/building-chromium-os/build-instructions")

---

### Post by Dunge on 2009-11-19
I'm having the same problem. Worth mentioning I'm using Debian in a vmware image to do it.

Edit: Got it, the script expect ~/chromiumos/chroot/home/root/trunk to exist so it can mount something on it. Just create the empty folders.

Second Edit : Hmm that chroot-ed environnement dont have basic things like gcc and pkg-config installed. Am I missing something?

---

### Post by Wiebelhaus on 2009-11-20
> **Dunge said:**
> I'm having the same problem. Worth mentioning I'm using Debian in a vmware image to do it.

Got it, the script expect ~/chromiumos/chroot/home/root/trunk to exist so it can mount something on it. Just create the empty folders.

Thanks.

---

### Post by tkkg on 2009-11-20
> **Dunge said:**
> I'm having the same problem. Worth mentioning I'm using Debian in a vmware image to do it.

Edit: Got it, the script expect ~/chromiumos/chroot/home/root/trunk to exist so it can mount something on it. Just create the empty folders.

Second Edit : Hmm that chroot-ed environnement dont have basic things like gcc and pkg-config installed. Am I missing something?

I've got the same problem. gcc and other basic stuff is missing inside the chroot environment. Did you find a solution for that?

---

### Post by tobytobsen on 2009-11-20
Thank you for that tip! That worked good, now I have the gcc problem, just like you...


./build_platform_packages.sh

The problem is that no compiler is availible in the chroot env?

(chroot)root@toby-laptop:/home/root/trunk/src/scripts# ./build_platform_packages.sh
Building package connman...
/home/root/trunk/src/third_party/connman/connman-0.42 /home/root/trunk/src/third_party/connman
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking whether to enable maintainer-specific portions of Makefiles... no
checking for pkg-config... no
checking for gcc... no
checking for cc... no
checking for cl.exe... no
configure: error: in `/home/root/trunk/src/third_party/connman/connman-0.42':
configure: error: no acceptable C compiler found in $PATH
See `config.log' for more details.
/home/root/trunk/src/third_party/connman /home/root/trunk/src/third_party/connman
./../../scripts/common.sh: line 147: dpkg-buildpackage: command not found


Can anyone help?

---

### Post by wesg on 2009-11-20
Was able to get into chroot. I forgot (was unaware) to run **./make_chroot.sh** before ./enter_chroot.sh

Ran that script, and it worked fine. I'm running the next step right now.

---

### Post by masterblah777 on 2009-11-20
I am having the same issue. I just got into the chroot environment and I have no idea why GCC isn't functioning. I build all the packages just as the instructions said. Does anyone have any ideas about how to get GCC functioning?


EDIT: I copied my GCC folder from my knoppix install because the /chroot/bin was missing GCC and it has a new error 
:
(chroot)root@Microknoppix:/home/root/trunk/src/scripts# ./build_platform_packages.sh
Building package connman...
/home/root/trunk/src/third_party/connman/connman-0.42 /home/root/trunk/src/third_party/connman
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking whether to enable maintainer-specific portions of Makefiles... no
checking for pkg-config... no
checking for gcc... gcc
checking for C compiler default output file name... 
configure: error: in `/home/root/trunk/src/third_party/connman/connman-0.42':
configure: error: C compiler cannot create executables
See `config.log' for more details.
/home/root/trunk/src/third_party/connman /home/root/trunk/src/third_party/connman
./../../scripts/common.sh: line 147: dpkg-buildpackage: command not found

---

### Post by Vgui on 2009-11-20
I think if you are getting that many errors something went wrong earlier...

Are you sure the make_chroot.sh script completed successfully (it should say something about "Successful with no errors")?
I had tried it as root and that caused the "adduser" command to fail, but once I redid it the ./build_platform_packages.sh command ran without any problems.
Really though I think something went wrong if you are having to MANUALLY create the /home/root/ directory structure. Maybe try --replace for your make_chroot.sh command to ensure it starts fresh.

---

### Post by masterblah777 on 2009-11-20
I tried to the make_chroot command a few times and it didn't have any different result either way. I may just have to start from scratch, which would be unfortunate.

---

### Post by Dunge on 2009-11-20
From what I remember, make_chroot did end with a successfull message. If I try to run it again it simply tells me it already exist. I would try --replace but if you said you already tried it I guess I<ll believe you.

Of course it would be foolish to try to populate the chroot manually. Im waiting for a solution cause I cant think of anything else.

---

### Post by Vgui on 2009-11-20
@masterblah777: Wouldn't "starting from scratch" just consist of the *make_local_repo.sh* command, since *make_chroot.sh* is only the second command? Better to do that now than fight the build forever.
You are running these commands as a normal user that gets sudo'd over (via the script), right?

@Dunge: So after *make_chroot.sh* you try *enter_chroot.sh* and it works for you? Then you run into the same GCC problems masterblah777 was having? Maybe try enabling a local account (via src/platform/pam_google/enable_localaccount.sh, run from outside the chroot) and setting the shared password.

I'm not much further ahead as my *build_platform_packages.sh* command failed when trying *copy_chrome_zip.sh*, since for sme reason it was trying to pull the zip off their internal build servers (good old internal alpha code). Hoping my second attempt works better and I can get to building the kernel.

---

### Post by Dunge on 2009-11-20
I just tried make_chroot.sh --replace. From the logs, it actually do configure gcc-base-4.4 . At the end though it say :

Done running debootstrap.
useradd: user 'root' already exists

This might be the problem, I run the scripts in a console terminal as a root (I did sudo su before) since it was in the prerequisites in the google guide to be root. Ill try again as a normal user.

---

### Post by preppietechie on 2009-11-20
I had to run make_chroot.sh *not* as root, which then created the proper folders within the root directory in the chroot environment.  Hope that helps.

---

### Post by Vgui on 2009-11-20
> **Vgui said:**
> ...I had tried it as root and that caused the "adduser" command to fail, but once I redid it the ./build_platform_packages.sh command ran without any problems...


Yep as I suggested earlier it complains about *adduser* failing if you try it as root. Just do a normal user with sudo access and you should have more luck with the make_chroot.sh command.

---

### Post by Crump3t on 2009-11-20
> **Vgui said:**
> @masterblah777: Wouldn't "starting from scratch" just consist of the *make_local_repo.sh* command, since *make_chroot.sh* is only the second command? Better to do that now than fight the build forever.
You are running these commands as a normal user that gets sudo'd over (via the script), right?

@Dunge: So after *make_chroot.sh* you try *enter_chroot.sh* and it works for you? Then you run into the same GCC problems masterblah777 was having? Maybe try enabling a local account (via src/platform/pam_google/enable_localaccount.sh, run from outside the chroot) and setting the shared password.

I'm not much further ahead as my *build_platform_packages.sh* command failed when trying *copy_chrome_zip.sh*, since for sme reason it was trying to pull the zip off their internal build servers (good old internal alpha code). Hoping my second attempt works better and I can get to building the kernel.

Im having the same problem with copy_chrome_zip.sh are you substituting it for chrome-linux.zip from:
[http://build.chromium.org/buildbot/archives/chromium-chromiumos-r32516/](http://build.chromium.org/buildbot/archives/chromium-chromiumos-r32516/) ?

Hopefully it should work :)

---

### Post by dddanmar on 2009-11-20
A few things I've noted:

a) can't be built on an ntfs drive, debbootstrap has a whine
b) if any of the packages during the local repo fail to install, locate debfile.deb, rm debfile.deb and retry ./make_local_repo.sh - I think my internet dropped at one point and I ended up with half of an archive.

I *think* I have enough HDD space for this all to compile, can anyone report from start to finish how much space they required using the browser binary? Considering the source.tgz for ChromiumOS is 200mb + the .deb files it downloads + the make files, what should a user expect to have free?

I've been trying to do something like this for awhile, xPUD nearly fits the bill but I'd like to be able to make fast-booting appliances that are easy to configure with apt-get. 

Party + Random Laptop + ChromeOS+XMMS+A few scripts+USB Drive with MP3s = Mobile DJ. 
Restricted Windows Domain Machine + ChomeOS + Quake4Linux = Wasted study hours
etc.etc.etc.

Google, Canonical, thanks for getting into bed with each other.

---

### Post by Dunge on 2009-11-20
At the end of build_image.sh :

> home/dunge/trunk/src/build/images/999.999.32509.003818-a1/rootfs/boot is device /dev/loop0
0+1 records in
1+0 records out
512 bytes (512 B) copied, 0.00424551 s, 121 kB/s
Warning: /home/dunge/trunk/src/build/images/999.999.32509.003818-a1/mbr.image is not a block device
Disk /home/dunge/trunk/src/build/images/999.999.32509.003818-a1/mbr.image: cannot get geometry

Disk /home/dunge/trunk/src/build/images/999.999.32509.003818-a1/mbr.image: 0 cylinders, 64 heads, 32 sectors/track

sfdisk: ERROR: sector 0 does not have an msdos signature
 /home/dunge/trunk/src/build/images/999.999.32509.003818-a1/mbr.image: unrecognized partition table type
Old situation:
No partitions found
Warning: given size (1945600) exceeds max allowable size (0)
Warning: given size (1945600) exceeds max allowable size (0)
Warning: given size (1945600) exceeds max allowable size (0)
New situation:
Units = sectors of 512 bytes, counting from 0

   Device Boot    Start       End   #sectors  Id  System
/home/dunge/trunk/src/build/images/999.999.32509.003818-a1/mbr.image1             1   1945600    1945600  83  Linux
/home/dunge/trunk/src/build/images/999.999.32509.003818-a1/mbr.image2       1945601   3891200    1945600  82  Linux swap / Solaris
/home/dunge/trunk/src/build/images/999.999.32509.003818-a1/mbr.image3   *   3891201   5836800    1945600  83  Linux
/home/dunge/trunk/src/build/images/999.999.32509.003818-a1/mbr.image4             0         -          0   0  Empty
Warning: partition 1 extends past end of disk
Successfully wrote the new partition table

Re-reading the partition table ...
BLKRRPART: Inappropriate ioctl for device

If you created or changed a DOS partition, /dev/foo7, say, then use dd(1)
to zero the first 512 bytes:  dd if=/dev/zero of=/dev/foo7 bs=512 count=1
(See fdisk(8).)
Done.  Image created in /home/dunge/trunk/src/build/images/999.999.32509.003818-a1
To copy to USB keyfob, outside the chroot, do something like:
  ./image_to_usb.sh --from=~/chromeos/src/build/images/999.999.32509.003818-a1 --to=/dev/sdb
To convert to VMWare image, outside the chroot, do something like:
  ./image_to_vmware.sh --from=~/chromeos/src/build/images/999.999.32509.003818-a1


Still, it seems like I have a image created. Ill try it later.

---

### Post by dddanmar on 2009-11-20
I was caught also by 

a) no user root exists (so don't run it as sudo and check all your permissions)

b) After following the build instructions, downloading chrome-linux.zip to chrome-chromeos.zip in /local_assests/, as noted the copy script fails! 

Outside of the chroot:
 ```

cp ~/chromeOS/src/build/x86/local_assests/chrome-chromeos.zip ~/chromeOS/chroot/

```

```

vi ~/chromeOS/chroot/home/trunk/src/scripts/copy_chrome_zip.sh

```

Comment out download() functions in the script and replace with

```

cp /chrome-chromeos.zip /home/user/trunk/src/platform/chrome/

```

Check the directories for your own symlinks / users.
  
Fixed ./build_platform_packages.sh [COLOR=Black]failing while unzip is trying to locate the file.

[/COLOR]

---

### Post by wesg on 2009-11-20
Managed to get it running in a VMWare Fusion install. Kinda cool, but mine doesn't quite look like the PR screenshots I'm looking at...

---

### Post by dddanmar on 2009-11-21
Woo, made a usb image, used the scripts to copy it to an 8gb pen and reboot!

My desktop has internet connectivity, but the ATI card too choppy for video playback.

EEEPC 701 w/ 2gbRAM runs it well enough for me to post this, the Google account integration is nice, and there's even a hotmail icon installed by default, encouraging the competition. Aww, its so sweet. I tried playing a few youtube videos and sound worked fine, though everything seemed to get a little overloaded after a few videos. Early days yet.

Oh, and it won't connect to a wireless connection without some kind of wireless encryption.

Is it worthwhile making a torrent of the .image and mbr files along with the install_to_usb script? Everything else out there seems to be VMWare images.

*edii*

Ok so, installed to the eeePC's SSD, it boots even faster then before (obv..). 

Once the bugs get ironed out this could be a real contender. I know splashtop has been there before but at least this has backing from both Google and Canonical so it might get somewhere.

Next step is to get some start building a few things in the chroot and rebuilding the iso!

---

### Post by jjbarrows on 2009-11-21
I've compiled chromiumOS. But can't get the usb boot to work, I use the script and it created three 950meg partitions and wrote the mbr, but I get 'operating system not found' at boot.

Any ideas?
-joseph

---

### Post by LuisPT on 2009-11-21
It should be great to have a simple script to run all the compilation process and scripts, because people are getting a litle confused about the correct steps.

Just my 50cents of the day.

Regards.

---

### Post by dddanmar on 2009-11-21
I was thinking of fixing the scripts and posting the patches... it wasn't impossible to get it to build but there were a few steps that were unautomated or just broken that didn't need to be.

jjbarrows, are you sure you are point it to /dev/sdb and not /dev/sdb1?
Also, any errors from the build process that might have been missed?

---

### Post by Crump3t on 2009-11-21
Mines compiled and booted, mouse is choppy on my aspire one. I found that to run build_image.sh. I had to rename my chroot's home folder from "david" to "root" as I couldnt find the part of the script where it attempted to get the release from root. Other than that and the copy_chrome_zip.sh thing it compiled fine. I've attached a patched version of the copy_chrome_zip.sh.[]("http://david-w.org/copy_chrome_zip.zip")

---

### Post by dkrrunner on 2009-11-21
Is anyone having trouble downloading the Chromium Binary (chrome-linux.zip)? When I click on the link, it returns a 403 forbidden and says I don't have permission to download the file.

---

### Post by dkrrunner on 2009-11-22
Nevermind. I tried it again today and the link works again. :D

---

### Post by frecel on 2009-11-22
I'm also having problems with gcc on chroot. 
```
(chroot)root@frecel-desktop:/home/root/trunk/src/scripts# ./build_platform_packages.sh 
Building package connman...
/home/root/trunk/src/third_party/connman/connman-0.42 /home/root/trunk/src/third_party/connman
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking whether to enable maintainer-specific portions of Makefiles... no
checking for pkg-config... no
checking for gcc... no
checking for cc... no
checking for cl.exe... no
configure: error: in `/home/root/trunk/src/third_party/connman/connman-0.42':
configure: error: no acceptable C compiler found in $PATH
See `config.log' for more details.
/home/root/trunk/src/third_party/connman /home/root/trunk/src/third_party/connman
./../../scripts/common.sh: line 147: dpkg-buildpackage: command not found

```

Anyone got solution for that?

EDIT: I got gcc to work, i had to copy gcc files to those directories
```
/usr/bin/gcc /usr/lib/gcc /usr/lib64/gcc
```

But now I have another problem

```
(chroot)root@frecel-desktop:/home/root/trunk/src/scripts# ./build_platform_packages.sh 
Building package connman...
/home/root/trunk/src/third_party/connman/connman-0.42 /home/root/trunk/src/third_party/connman
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking whether to enable maintainer-specific portions of Makefiles... no
checking for pkg-config... no
checking for gcc... gcc
checking for C compiler default output file name... 
configure: error: in `/home/root/trunk/src/third_party/connman/connman-0.42':
configure: error: C compiler cannot create executables
See `config.log' for more details.
/home/root/trunk/src/third_party/connman /home/root/trunk/src/third_party/connman
./../../scripts/common.sh: line 147: dpkg-buildpackage: command not found

```

---

### Post by SawyerLX on 2009-11-22
You guys keep doin the hard work, the rest of us will start looking for any other linux distributions' forums  if other s  are comparing ideas :popcorn:
good luck.  ..  .. ..

---

### Post by dddanmar on 2009-11-23
Any errors with GCC has to do with building / configuring with sudo.

I just extract the source directory to somewhere I have full user rights to and work in a normal terminal w/out sudo. There's a way around it if you really really want to build with sudo but if you don't need it, don't use it. Also, manually copying gcc binaries might work, but there's always support files that may not have been generated properly when the initial build failed.

My suggestion, go back a few steps, reset your file permissions on the entire subdirectory containing source and repo and try again. The build scripts ask for root permission when they need it and seem to drop it somewhere along the line before moving on to gcc.

---

### Post by k64 on 2009-11-27
Hello, my name is Kenny Strawn, from the PC World Forums. I posted a similar thread there stating this same problem, only to get help here. In my case, it was ./make_local_repo.sh that I forgot to run, not ./make_chroot.sh. However, I got good help from this thread. Thank you all, and I am posting from my working Acer Aspire One AOA110-1545 with Chrome OS on it.

P.S. I used my Ubuntu 9.10 desktop to build it.

---

### Post by dddanmar on 2009-12-08
Good on you k64, I'm still fiddling at home with ChromeOS.

Mainly, rip out Chrome browser and add in some arcade emulators, my eeePC now goes from power button to automatically logged in and spawning emulators in under 8 seconds.

I've given up trying to help with the open source version of ChromiumOS, it seems the public release is so far behind the development release its just not worth it yet...

---

### Post by HarshReality on 2009-12-16
this is most annoying.. copy_chrome errors like there is no end in sight so I tried the one here (granted its not pulling the snapshot but it beats nothing..) and I keep getting:
```

dh_testroot
rm -f build-stamp
rm -f LATEST chrome-chromeos.zip chrome-linux.zip
dh_clean
 debian/rules build
dh_testdir
./copy_chrome_zip.sh
make: ./copy_chrome_zip.sh: Command not found
make: *** [build-stamp] Error 127
dpkg-buildpackage: failure: debian/rules build gave error exit status 2
(chroot)steven@steven-desktop:~/trunk/src/scripts$ 

```

---

### Post by dddanmar on 2010-01-12
Looks like its dropped the sh script or is in the wrong directory.

I did fix my .sh file again for getting the chrome, I'll dredge it up and see if I can post it again.

---

