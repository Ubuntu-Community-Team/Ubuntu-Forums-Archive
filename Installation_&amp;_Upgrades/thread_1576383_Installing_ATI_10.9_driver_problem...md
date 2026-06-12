---
title: "Installing ATI 10.9 driver problem.."
date: 2010-09-17
forum: Installation &amp; Upgrades
---

### Post by chronaden on 2010-09-17
I Wanted to install the new drivers for my 64bit Ubuntu 10.04. 
Heres what I did:

sudo apt-get purge fglrx
reboot  sudo sh ati-driver-installer-10-9-x86.x86_64.run --buildpkg Ubuntu/lucid
dpkg -i *.deb
reboot

And my CCC info still says:
[http://imgur.com/SBv9L.png](http://imgur.com/SBv9L.png)

Why isn't anything upgraded?, I don't get any errors during install or anything.

---

### Post by coudy on 2010-09-17
You are lucky, 
I can install new drivers, but after reboot X won't start. I have black screen, and I can't switch to console. 


> **chronaden said:**
> I Wanted to install the new drivers for my 64bit Ubuntu 10.04. 
Heres what I did:

sudo apt-get purge fglrx
reboot  sudo sh ati-driver-installer-10-9-x86.x86_64.run --buildpkg Ubuntu/lucid
dpkg -i *.deb
reboot

And my CCC info still says:
[http://imgur.com/SBv9L.png](http://imgur.com/SBv9L.png)

Why isn't anything upgraded?, I don't get any errors during install or anything.

---

### Post by chronaden on 2010-09-17
Bummer, are these drivers majorly bugged or? o0

---

### Post by coudy on 2010-09-17
Ok, solved, I have now 10.9 on 64b Lucid and it is working. 
Try to install only 
fglrx_8.771-0ubuntu1_amd64.deb
fglrx-amdcccle_8.771-0ubuntu1_amd64.deb 
 
do not install 
fglrx-modaliases_8.771-0ubuntu1_amd64.deb

---

### Post by chronaden on 2010-09-18
Great...

Now I can't get anything to work, any kind of purge/removal/install/reinstall 10.9 or the normal ones via the Menu dont work anymore.. 
I noticed that a new kernel update was installed, maybe something to do with that?

What fresh hell.. :(

---

### Post by Captain Giraffe on 2010-09-18
I think I have a solution to your problem. After a bit of research I found 
related to [https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bugs?start=150](https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bugs?start=150) . There's more than a page of bug reports with this problem.
The bug seems to come from the fact that a function: compat_alloc_user_space() has been moved to a GPL only section. So including this new function results in another build failure.

The thread at
[http://archives.free.net.ph/message/20100918.082657.4e5cc10e.en.html](http://archives.free.net.ph/message/20100918.082657.4e5cc10e.en.html)
states "Don't use arch_compat_alloc_user_space() that would be worse."

I have no idea why it would be worse so I tried it, and it seems to work like a charm.

The fix committed at
[https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/641890](https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/641890)
Seems to me to introduce a certain demise from a stack overflow. When I tried it my computer just decided to reboot (I'm guessing as a result of the stack overflow).

So my prescription would be:
After the failed build:
-sudo edit the file at /var/lib/dkms/fglrx/8.771/source/kcl_ioctl.c
line 196; at the end of the file.
```
Change 
return compat_alloc_user_space(size);
To
return arch_compat_alloc_user_space(size);
```
Save file

```
sudo dpkg --configure fglrx
```
and maybe a
```
sudo dpkg --configure fglrx-amdcccle
```
and don't forget
```
sudo aticonfig --initial
```

This is on a x86_64 Lucid system and my gpu is an ati HD3870.

---

### Post by chronaden on 2010-09-18
Your trick didnt work for me, but this did the trick:
[https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/641890](https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/641890)

---

### Post by Captain Giraffe on 2010-09-18
Why didn't my trick work?

When I tried the launchpad advice it seemed to work at first on the desktop, but when I started an OpenGL app (world of warcraft) it crashed immediately. The crash led me to the conclusion that the launchpad advice is as faulty as it appears to be; function calling itself=> stack overflow.

---

### Post by chronaden on 2010-09-19
don't know, when i changed it to arch... etc. I got some error again with "arch" in the errorcode, but i fixed with one of your url's, so good times :)

---

### Post by sojou on 2010-09-19
> **Captain Giraffe said:**
> Why didn't my trick work?

When I tried the launchpad advice it seemed to work at first on the desktop, but when I started an OpenGL app (world of warcraft) it crashed immediately. The crash led me to the conclusion that the launchpad advice is as faulty as it appears to be; function calling itself=> stack overflow.

The actual source file is here (at least in the 10.9 version of the installer): /usr/src/fglrx-8.771. The one in var/lib/dkms/fglrx/* is a temporary copy.

So modifying that file in /usr/src/... with arch_... replacement works. [like you noted, the launchpad solution is a recursion].

---

### Post by sojou on 2010-09-19
> **sojou said:**
> The actual source file is here (at least in the 10.9 version of the installer): /usr/src/fglrx-8.771. The one in var/lib/dkms/fglrx/* is a temporary copy.

So modifying that file in /usr/src/... with arch_... replacement works. [like you noted, the launchpad solution is a recursion].

oops. forgot to mention that I used the latest installer (10.9) from the amd website: [http://support.amd.com/us/gpudownload/Pages/index.aspx](http://support.amd.com/us/gpudownload/Pages/index.aspx)

I did not use the one from the ubuntu repository. [Perhaps these two fglrx packages install and use the source files from different places].

---

### Post by h4ck3r on 2010-09-20
> **Captain Giraffe said:**
> I think I have a solution to your problem. After a bit of research I found 
related to [https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bugs?start=150](https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bugs?start=150) . There's more than a page of bug reports with this problem.
The bug seems to come from the fact that a function: compat_alloc_user_space() has been moved to a GPL only section. So including this new function results in another build failure.

The thread at
[http://archives.free.net.ph/message/20100918.082657.4e5cc10e.en.html](http://archives.free.net.ph/message/20100918.082657.4e5cc10e.en.html)
states "Don't use arch_compat_alloc_user_space() that would be worse."

I have no idea why it would be worse so I tried it, and it seems to work like a charm.

The fix committed at
[https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/641890](https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/641890)
Seems to me to introduce a certain demise from a stack overflow. When I tried it my computer just decided to reboot (I'm guessing as a result of the stack overflow).

So my prescription would be:
After the failed build:
-sudo edit the file at /var/lib/dkms/fglrx/8.771/source/kcl_ioctl.c
line 196; at the end of the file.
```
Change 
return compat_alloc_user_space(size);
To
return arch_compat_alloc_user_space(size);
```
Save file

```
sudo dpkg --configure fglrx
```
and maybe a
```
sudo dpkg --configure fglrx-amdcccle
```
and don't forget
```
sudo aticonfig --initial
```

This is on a x86_64 Lucid system and my gpu is an ati HD3870.

I did everything, and this finally fixed it!!!!! +1 This needs to be stickied!!!!

---

### Post by mst7 on 2010-09-24
> **h4ck3r said:**
> I did everything, and this finally fixed it!!!!! +1 This needs to be stickied!!!!

I did that, and i have error in /var/lib/dkms/fglrx/8.771/build/make.log

```

DKMS make.log for fglrx-8.771 for kernel 2.6.32-25-generic (x86_64)
pi&#261;, 24 wrz 2010, 15:46:16 CEST
AMD kernel module generator version 2.1
doing Makefile based build for kernel 2.6.x and higher
rm -rf *.c *.h *.o *.ko *.GCC* .??* *.symvers
make -C /lib/modules/2.6.32-25-generic/build SUBDIRS=/var/lib/dkms/fglrx/8.771/build/2.6.x modules
make[1]: Wej&#347;cie do katalogu `/usr/src/linux-headers-2.6.32-25-generic'
  CC [M]  /var/lib/dkms/fglrx/8.771/build/2.6.x/firegl_public.o
  CC [M]  /var/lib/dkms/fglrx/8.771/build/2.6.x/kcl_acpi.o
  CC [M]  /var/lib/dkms/fglrx/8.771/build/2.6.x/kcl_agp.o
  CC [M]  /var/lib/dkms/fglrx/8.771/build/2.6.x/kcl_debug.o
  CC [M]  /var/lib/dkms/fglrx/8.771/build/2.6.x/kcl_ioctl.o
/var/lib/dkms/fglrx/8.771/build/2.6.x/kcl_ioctl.c: In function ‘KCL_IOCTL_AllocUserSpace32’:
/var/lib/dkms/fglrx/8.771/build/2.6.x/kcl_ioctl.c:196: error: implicit declaration of function ‘compat_alloc_user_space’
/var/lib/dkms/fglrx/8.771/build/2.6.x/kcl_ioctl.c:196: warning: return makes pointer from integer without a cast
make[2]: *** [/var/lib/dkms/fglrx/8.771/build/2.6.x/kcl_ioctl.o] error 1
make[1]: *** [_module_/var/lib/dkms/fglrx/8.771/build/2.6.x] error 2
make[1]: Opuszczenie katalogu `/usr/src/linux-headers-2.6.32-25-generic'
make: *** [kmod_build] error 2
build failed with return value 2

```

fglrx.0.crash
```
ProblemType: Package
DKMSBuildLog:
 DKMS make.log for fglrx-8.771 for kernel 2.6.32-25-generic (x86_64)
 pi&#261;, 24 wrz 2010, 16:06:29 CEST
 AMD kernel module generator version 2.1
 doing Makefile based build for kernel 2.6.x and higher
 rm -rf *.c *.h *.o *.ko *.GCC* .??* *.symvers
 make -C /lib/modules/2.6.32-25-generic/build SUBDIRS=/var/lib/dkms/fglrx/8.771/build/2.6.x modules
 make[1]: Wej&#347;cie do katalogu `/usr/src/linux-headers-2.6.32-25-generic'
   CC [M]  /var/lib/dkms/fglrx/8.771/build/2.6.x/firegl_public.o
   CC [M]  /var/lib/dkms/fglrx/8.771/build/2.6.x/kcl_acpi.o
   CC [M]  /var/lib/dkms/fglrx/8.771/build/2.6.x/kcl_agp.o
   CC [M]  /var/lib/dkms/fglrx/8.771/build/2.6.x/kcl_debug.o
   CC [M]  /var/lib/dkms/fglrx/8.771/build/2.6.x/kcl_ioctl.o
 /var/lib/dkms/fglrx/8.771/build/2.6.x/kcl_ioctl.c: In function ‘KCL_IOCTL_AllocUserSpace32’:
 /var/lib/dkms/fglrx/8.771/build/2.6.x/kcl_ioctl.c:196: error: implicit declaration of function ‘compat_alloc_user_space’
 /var/lib/dkms/fglrx/8.771/build/2.6.x/kcl_ioctl.c:196: warning: return makes pointer from integer without a cast
 make[2]: *** [/var/lib/dkms/fglrx/8.771/build/2.6.x/kcl_ioctl.o] B&#322;&#261;d 1
 make[1]: *** [_module_/var/lib/dkms/fglrx/8.771/build/2.6.x] B&#322;&#261;d 2
 make[1]: Opuszczenie katalogu `/usr/src/linux-headers-2.6.32-25-generic'
 make: *** [kmod_build] B&#322;&#261;d 2
 build failed with return value 2
Date: Fri Sep 24 16:06:36 2010
ErrorMessage: fglrx kernel module failed to build
Package: fglrx
PackageVersion: 2:8.771-0ubuntu1
SourcePackage: fglrx-installer
```

---

### Post by anihilat0r on 2010-09-26
@[B]Captain Giraffe
[/B]Thanks for the tip, however it didnt't quite work as 
sudo dpkg --configure fglrx
returned errors (no package "fglrx" and package already configured and so on..).

I've got it then finally working on Kubuntu 9.10 (x64) by mixing a few tutorials and hints from various forums. If anyone's interested, here is how:

**Required for building .debs:**
```

sudo apt-get install build-essential cdbs fakeroot dh-make debhelper debconf libstdc++6 dkms libQtGui4

```Purge existing installations of the ati driver and packages

**Build packages**
```

./ati-driver-installer-10-9-x86.x86_64.run --extract
cd fglrx-install*/arch/x86_64/usr/lib/
ln -s libatiuki.so.1.0 libatiuki.so.1
cd ../../../..
sudo ./ati-installer.sh 10.9 --buildpkg Ubuntu/karmic

```Hint: At this point, you may encounter build errors and have to delete the directory /usr/share/ati/lib64 (if existst) to successfuly build the packages. If so, repeat the last command above.

```

cd
sudo dpkg -i *.deb
sudo aticonfig --initial

```[B]

Now the discussed part:
[/B]```

cd /usr/src/fglrx-8.771/
sudo edit kcl_ioctl.c

```line 196; at the end of the file.
Change
```

return compat_alloc_user_space(size);
To
return arch_compat_alloc_user_space(size);

```And finally, to build the kernel module fglrx.ko:
```

sudo dkms build -m fglrx -v 8.771
sudo dkms install -m fglrx -v 8.771
sudo reboot

```Hope it helps!

---

### Post by aarons6 on 2010-09-30
> **anihilat0r said:**
> @[B]Captain Giraffe
[/B]Thanks for the tip, however it didnt't quite work as 
sudo dpkg --configure fglrx
returned errors (no package "fglrx" and package already configured and so on..).

I've got it then finally working on Kubuntu 9.10 (x64) by mixing a few tutorials and hints from various forums. If anyone's interested, here is how:

**Required for building .debs:**
```

sudo apt-get install build-essential cdbs fakeroot dh-make debhelper debconf libstdc++6 dkms libQtGui4

```Purge existing installations of the ati driver and packages

**Build packages**
```

./ati-driver-installer-10-9-x86.x86_64.run --extract
cd fglrx-install*/arch/x86_64/usr/lib/
ln -s libatiuki.so.1.0 libatiuki.so.1
cd ../../../..
sudo ./ati-installer.sh 10.9 --buildpkg Ubuntu/karmic

```Hint: At this point, you may encounter build errors and have to delete the directory /usr/share/ati/lib64 (if existst) to successfuly build the packages. If so, repeat the last command above.

```

cd
sudo dpkg -i *.deb
sudo aticonfig --initial

```[B]

Now the discussed part:
[/B]```

cd /usr/src/fglrx-8.771/
sudo edit kcl_ioctl.c

```line 196; at the end of the file.
Change
```

return compat_alloc_user_space(size);
To
return arch_compat_alloc_user_space(size);

```And finally, to build the kernel module fglrx.ko:
```

sudo dkms build -m fglrx -v 8.771
sudo dkms install -m fglrx -v 8.771
sudo reboot

```Hope it helps!


i am having a problem installing the Proprietary drivers on kubuntu 10.04.

i got to that last part and did you forget something? i ran the sudo dkms and it says that fglrx is not in the tree.. 

how do i put it in the tree?

---

### Post by _Ikke_ on 2010-09-30
Thanks, it worked (after a few tries). You made my day.

---

### Post by sberriman on 2010-09-30
Okay, thanks guys - finally got fglrx 10.9 running on Lucid x86_64 after the kernel update today (to 2.6.32-25) screwed up the previous version.  I ended up doing it slightly differently though.

I extracted the installer in my home directory:
```

cd ~
./ati-driver-installer-10-9-x86.x86_64.run --extract
```Next I had to change to ~/fglrx-install*/arch/x86_64/usr/ and create a symlink for lib pointing at lib64 (as I didn't have a lib) before linking the SO:

```

cd fglrx-install*/arch/x86_64/usr/
ln -s lib64 lib
cd lib
ln -s libatiuki.so.1.0 libatiuki.so.1
```Then I searched for **kcl_ioctl.c**, which I found in '~/fglrx-install.*/common/lib/modules/fglrx/build_mod'.  This is where I edited the return function, as detailed previously. I then returned to the top fglrx directory, and built and installed the packages without any fuss:

```

cd ~/fglrx-install*
sudo ./ati-installer.sh 10.9 --buildpkg Ubuntu/lucid
cd ..
sudo dpkg -i *.deb
sudo aticonfig --initial
```And after a reboot, all was good again!  This way also successfully installed Catalyst Control Center too.

---

### Post by nullmodem on 2010-09-30
Thanks for the tip, Captain Giraffe.

Though I'd recommend modifying the files in the temporary directory ati-driver-installer-10-9-x86.x86_64.run or similar extracts to. This way the changes are slipstreamed into the package, making it easier to re-apply in future or share across machines.

When the script's run, the first thing it will do is create a temporary directory (e.g. fglrx-install.jOKtvu).

Change "compat_alloc_user_space" to "arch_compat_alloc_user_space" in:
common/lib/modules/fglrx/build_mod/kcl_ioctl.c
install/lib/modules/fglrx/build_mod/kcl_ioctl.c

They may be owned by root, so you may need to sudo to edit them.

Once modified, tell the installer to generate a distribution-specific package, and install.

If after a reboot, it's not working (No acceleration, glxinfo may segfault). Run "sudo aticonfig --initial". After a reboot everything should work.

---

### Post by doggie on 2010-09-30
THANKS!!!!! anihilat0r...... i did everything you said... and it's finally working again!!! \\:D/ =D> =D> =D>

---

### Post by aarons6 on 2010-09-30
OMG how can this be so complicated.. :(
does ATI not want us using their video cards??
ive done everything in this thread to try to install the drivers so 3d works on my system..
 
after many many many many many reboots and downloading files and stuff i figured its my system.
 
so i downloaded the iso of kubuntu 10.04 desktop x64.. took all my drives out.. put in a fresh formated ext4 drive..
 
installed it.. extracted the run file..
edited the .c file
downloaded the lib32 and all the build stuff with apt-get
 
built the .debs
installed the .debs
 
it built the module :)
 
rebooted to a black screen with this error.. 
 
'dlopen: /usr/lib/xorg/modules/drivers/fglrx_drv.so: undefined symbol: resVgaShared'
 
Fatal server error:
no screens found.. 
 
 
AAAAAAAAAAAAAAAAARRRRRRRRRRRRRRRRRRRGGGGGGGGGGGGGGGGG!!!
 
i will never purchase an ATI video card again :(
 
 
how do i fix this??

---

### Post by jarpiw on 2010-10-02
> **aarons6 said:**
> 
 
'dlopen: /usr/lib/xorg/modules/drivers/fglrx_drv.so: undefined symbol: resVgaShared'
 
Fatal server error:
no screens found.. 
 
 
AAAAAAAAAAAAAAAAARRRRRRRRRRRRRRRRRRRGGGGGGGGGGGGGGGGG!!!
 
i will never purchase an ATI video card again :(
 
 
how do i fix this??

I had the same mate but tried this: [http://support.amd.com/us/kbarticles/Pages/GPU83ATICatalystLinuxHotfix.aspx](http://support.amd.com/us/kbarticles/Pages/GPU83ATICatalystLinuxHotfix.aspx) and it's working now.

Also check that: [http://wiki.cchtml.com/index.php/Ubuntu_Lucid_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Lucid_Installation_Guide).

---

### Post by antiplex on 2010-10-07
i just wanted to thank everybody who helped to find the described solution, i followed the description of sberriman and succesfully built and installed the ati-driver for kernel 2.6.32-25 after removing all content of /usr/share/ati/lib64 (as mentioned by anihilat0r)

greets, anti

---

### Post by aarons6 on 2010-10-08
after working on this for a week i have decided that its just not worth it.. i went back to the drivers that kubuntu installs when you apt-get install fglrx..

here was my problem.. after getting the drivers to install by installing the hotfix, Xorg was using up 100% CPU.

nothing i did fixed it.

---

### Post by FlameReaper on 2010-10-29
Read this thread a few times over, and finally figured what I needed to do in order to keep my ATI card (well, it's a laptop chip, a Mobility Radeon HD 5470) running in the later kernels (such as 2.6.32-25). Worked like a charm, I can't express enough thanks for this! :D

This was the reason I decided to hold back my upgrade to Maverick from Lucid ^^; seeing that Maverick starts with the 2.6.32-25 installed :D

---

