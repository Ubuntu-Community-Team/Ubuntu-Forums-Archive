---
title: "howto for installing bleedging edge Xserver from PPA"
date: 2008-12-11
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by ShirishAg75 on 2008-12-11
Hi all, 
 This is going to be talking about how to test the newest X.org for your system. I had been having issues with having a GUI on my system on jaunty so had to do the same. Tormod Volden has been pretty helpful to get this working for me. 

First some resources 

> [https://wiki.edubuntu.org/XorgOnTheEdge](https://wiki.edubuntu.org/XorgOnTheEdge)
[https://launchpad.net/~xorg-edgers/+archive]("https://launchpad.net/%7Exorg-edgers/+archive")
[http://lists.ubuntu.com/archives/ubuntu-x/](http://lists.ubuntu.com/archives/ubuntu-x/)

IRC channel :- @ freenode #ubuntu-xSo from the page [https://launchpad.net/~xorg-edgers/+archive]("https://launchpad.net/%7Exorg-edgers/+archive") here's the list one has to do. Some things could have been explained better which is not therein. 

a. First add the Xorg jaunty archives either through System > Administration > Software Sources or /etc/apt/sources.list

> deb [http://ppa.launchpad.net/xorg-edgers/ubuntu](http://ppa.launchpad.net/xorg-edgers/ubuntu) jaunty main
deb-src [http://ppa.launchpad.net/xorg-edgers/ubuntu](http://ppa.launchpad.net/xorg-edgers/ubuntu) jaunty main
b. Then either Reload or run sudo apt-get update

c. Then install drm-modules-source

   ```
 $ sudo apt-get install drm-modules-source
```d. Now tried running sudo module-assistant auto-install drm-module. This one fails. 
  What works is :-

```
$ sudo env DRM_MODULES="i915" module-assistant -t auto-install drm-modules

```It gives an error saying couldn't create /usr/src/linux symlink but perhaps that's inconsequential. 

After few minutes you get a drm-modules-2.6.28-2-ub-generic (depending on the kernel chosen)

If not there is a build log which one can use to find out what the issues are at /var/cache/modass/ named something like drm-modules-source kernel-version buildlog (some numbers)

For instance 

drm-modules-source.buildlog.2.6.28-2-ub-generic.1228922933

The buildlog would be something like this 

```

/usr/bin/make -C linux-core KERNELDIR=/usr/src/linux KVERREL=2.6.28-2-ub-generic clean
make[1]: Entering directory `/usr/src/modules/drm-modules/linux-core'
rm -rf *.o *.ko dristat drmstat .depend .*.flags .*.d .*.cmd *.mod.c drm_pciids.h .tmp_versions
make[1]: Leaving directory `/usr/src/modules/drm-modules/linux-core'
/usr/bin/make  -f debian/rules kdist_clean kdist_config binary-modules
make[1]: Entering directory `/usr/src/modules/drm-modules'
/usr/bin/make -C linux-core KERNELDIR=/usr/src/linux KVERREL=2.6.28-2-ub-generic clean
make[2]: Entering directory `/usr/src/modules/drm-modules/linux-core'
rm -rf *.o *.ko dristat drmstat .depend .*.flags .*.d .*.cmd *.mod.c drm_pciids.h .tmp_versions
make[2]: Leaving directory `/usr/src/modules/drm-modules/linux-core'
for templ in ; do \
    cp $templ `echo $templ | sed -e 's/_KVERS_/2.6.28-2-ub-generic/g'` ; \
  done
for templ in `ls debian/*.modules.in` ; do \
    test -e ${templ%.modules.in}.backup || cp ${templ%.modules.in} ${templ%.modules.in}.backup 2>/dev/null || true; \
    sed -e 's/##KVERS##/2.6.28-2-ub-generic/g ;s/#KVERS#/2.6.28-2-ub-generic/g ; s/_KVERS_/2.6.28-2-ub-generic/g ; s/##KDREV##/2.6.28-2.2/g ; s/#KDREV#/2.6.28-2.2/g ; s/_KDREV_/2.6.28-2.2/g  ' < $templ > ${templ%.modules.in}; \
  done
dh_testroot
dh_clean -k
# Build the modules
/usr/bin/make -C linux-core KERNELDIR=/usr/src/linux KVERREL=2.6.28-2-ub-generic \
        EXTRA_CFLAGS=-DGIT_REVISION=\\\"2.4.2~git20081208+modesetting-gem.12e68f80-0ubuntu0tormod\\\"
make[2]: Entering directory `/usr/src/modules/drm-modules/linux-core'
sh ../scripts/create_linux_pci_lists.sh < ../shared-core/drm_pciids.txt
make -C /lib/modules/2.6.28-2-ub-generic/build  SUBDIRS=`/bin/pwd` DRMSRCDIR=`/bin/pwd` modules
make[3]: Entering directory `/usr/src/linux-headers-2.6.28-2-ub-generic'
fatal: Not a git repository
  CC [M]  /usr/src/modules/drm-modules/linux-core/drm_auth.o
  CC [M]  /usr/src/modules/drm-modules/linux-core/drm_bufs.o
/usr/src/modules/drm-modules/linux-core/drm_bufs.c: In function &#8216;drm_rmmap_locked&#8217;:
/usr/src/modules/drm-modules/linux-core/drm_bufs.c:405: warning: enumeration value &#8216;_DRM_GEM&#8217; not handled in switch
  CC [M]  /usr/src/modules/drm-modules/linux-core/drm_context.o
  CC [M]  /usr/src/modules/drm-modules/linux-core/drm_dma.o
  CC [M]  /usr/src/modules/drm-modules/linux-core/drm_drawable.o
  CC [M]  /usr/src/modules/drm-modules/linux-core/drm_drv.o
  CC [M]  /usr/src/modules/drm-modules/linux-core/drm_fops.o
  CC [M]  /usr/src/modules/drm-modules/linux-core/drm_ioctl.o
  CC [M]  /usr/src/modules/drm-modules/linux-core/drm_irq.o
  CC [M]  /usr/src/modules/drm-modules/linux-core/drm_lock.o
  CC [M]  /usr/src/modules/drm-modules/linux-core/drm_memory.o
  CC [M]  /usr/src/modules/drm-modules/linux-core/drm_proc.o
  CC [M]  /usr/src/modules/drm-modules/linux-core/drm_stub.o
  CC [M]  /usr/src/modules/drm-modules/linux-core/drm_vm.o
/usr/src/modules/drm-modules/linux-core/drm_vm.c: In function &#8216;drm_vm_shm_close&#8217;:
/usr/src/modules/drm-modules/linux-core/drm_vm.c:252: warning: enumeration value &#8216;_DRM_GEM&#8217; not handled in switch
  CC [M]  /usr/src/modules/drm-modules/linux-core/drm_sysfs.o
  CC [M]  /usr/src/modules/drm-modules/linux-core/drm_pci.o
  CC [M]  /usr/src/modules/drm-modules/linux-core/drm_agpsupport.o
  CC [M]  /usr/src/modules/drm-modules/linux-core/drm_scatter.o
  CC [M]  /usr/src/modules/drm-modules/linux-core/drm_memory_debug.o
  CC [M]  /usr/src/modules/drm-modules/linux-core/ati_pcigart.o
  CC [M]  /usr/src/modules/drm-modules/linux-core/drm_sman.o
  CC [M]  /usr/src/modules/drm-modules/linux-core/drm_hashtab.o
  CC [M]  /usr/src/modules/drm-modules/linux-core/drm_mm.o
  CC [M]  /usr/src/modules/drm-modules/linux-core/drm_compat.o
  CC [M]  /usr/src/modules/drm-modules/linux-core/drm_fence.o
  CC [M]  /usr/src/modules/drm-modules/linux-core/drm_ttm.o
  CC [M]  /usr/src/modules/drm-modules/linux-core/drm_bo.o
/usr/src/modules/drm-modules/linux-core/drm_bo.c: In function &#8216;drm_bo_delayed_delete&#8217;:
/usr/src/modules/drm-modules/linux-core/drm_bo.c:514: warning: format &#8216;%d&#8217; expects type &#8216;int&#8217;, but argument 4 has type &#8216;long unsigned int&#8217;
  CC [M]  /usr/src/modules/drm-modules/linux-core/drm_bo_move.o
/usr/src/modules/drm-modules/linux-core/drm_bo_move.c: In function &#8216;drm_bo_move_zero&#8217;:
/usr/src/modules/drm-modules/linux-core/drm_bo_move.c:308: warning: unused variable &#8216;page&#8217;
  CC [M]  /usr/src/modules/drm-modules/linux-core/drm_crtc.o
  CC [M]  /usr/src/modules/drm-modules/linux-core/drm_edid.o
  CC [M]  /usr/src/modules/drm-modules/linux-core/drm_modes.o
  CC [M]  /usr/src/modules/drm-modules/linux-core/drm_crtc_helper.o
/usr/src/modules/drm-modules/linux-core/drm_crtc_helper.c: In function &#8216;drm_target_preferred&#8217;:
/usr/src/modules/drm-modules/linux-core/drm_crtc_helper.c:249: warning: unused variable &#8216;preferred&#8217;
  CC [M]  /usr/src/modules/drm-modules/linux-core/drm_regman.o
  CC [M]  /usr/src/modules/drm-modules/linux-core/drm_vm_nopage_compat.o
  CC [M]  /usr/src/modules/drm-modules/linux-core/drm_gem.o
  CC [M]  /usr/src/modules/drm-modules/linux-core/drm_uncached.o
  CC [M]  /usr/src/modules/drm-modules/linux-core/i810_drv.o
  CC [M]  /usr/src/modules/drm-modules/linux-core/i810_dma.o
  CC [M]  /usr/src/modules/drm-modules/linux-core/mach64_drv.o
  CC [M]  /usr/src/modules/drm-modules/linux-core/mach64_dma.o
  CC [M]  /usr/src/modules/drm-modules/linux-core/mach64_irq.o
  CC [M]  /usr/src/modules/drm-modules/linux-core/mach64_state.o
  CC [M]  /usr/src/modules/drm-modules/linux-core/mga_drv.o
  CC [M]  /usr/src/modules/drm-modules/linux-core/mga_dma.o
  CC [M]  /usr/src/modules/drm-modules/linux-core/mga_state.o
  CC [M]  /usr/src/modules/drm-modules/linux-core/mga_warp.o
  CC [M]  /usr/src/modules/drm-modules/linux-core/mga_irq.o
  CC [M]  /usr/src/modules/drm-modules/linux-core/nouveau_drv.o
  CC [M]  /usr/src/modules/drm-modules/linux-core/nouveau_state.o
  CC [M]  /usr/src/modules/drm-modules/linux-core/nouveau_fifo.o
  CC [M]  /usr/src/modules/drm-modules/linux-core/nouveau_mem.o
  CC [M]  /usr/src/modules/drm-modules/linux-core/nouveau_object.o
  CC [M]  /usr/src/modules/drm-modules/linux-core/nouveau_irq.o
  CC [M]  /usr/src/modules/drm-modules/linux-core/nouveau_notifier.o
  CC [M]  /usr/src/modules/drm-modules/linux-core/nouveau_swmthd.o
  CC [M]  /usr/src/modules/drm-modules/linux-core/nouveau_sgdma.o
  CC [M]  /usr/src/modules/drm-modules/linux-core/nouveau_dma.o
  CC [M]  /usr/src/modules/drm-modules/linux-core/nouveau_bo.o
  CC [M]  /usr/src/modules/drm-modules/linux-core/nouveau_fence.o
  CC [M]  /usr/src/modules/drm-modules/linux-core/nv04_timer.o
  CC [M]  /usr/src/modules/drm-modules/linux-core/nv04_mc.o
  CC [M]  /usr/src/modules/drm-modules/linux-core/nv40_mc.o
  CC [M]  /usr/src/modules/drm-modules/linux-core/nv50_mc.o
  CC [M]  /usr/src/modules/drm-modules/linux-core/nv04_fb.o
  CC [M]  /usr/src/modules/drm-modules/linux-core/nv10_fb.o
  CC [M]  /usr/src/modules/drm-modules/linux-core/nv40_fb.o
  CC [M]  /usr/src/modules/drm-modules/linux-core/nv04_fifo.o
  CC [M]  /usr/src/modules/drm-modules/linux-core/nv10_fifo.o
  CC [M]  /usr/src/modules/drm-modules/linux-core/nv40_fifo.o
  CC [M]  /usr/src/modules/drm-modules/linux-core/nv50_fifo.o
  CC [M]  /usr/src/modules/drm-modules/linux-core/nv04_graph.o
  CC [M]  /usr/src/modules/drm-modules/linux-core/nv10_graph.o
  CC [M]  /usr/src/modules/drm-modules/linux-core/nv20_graph.o
  CC [M]  /usr/src/modules/drm-modules/linux-core/nv40_graph.o
  CC [M]  /usr/src/modules/drm-modules/linux-core/nv50_graph.o
  CC [M]  /usr/src/modules/drm-modules/linux-core/nv04_instmem.o
  CC [M]  /usr/src/modules/drm-modules/linux-core/nv50_instmem.o
  CC [M]  /usr/src/modules/drm-modules/linux-core/nouveau_bios.o
  CC [M]  /usr/src/modules/drm-modules/linux-core/nv50_crtc.o
  CC [M]  /usr/src/modules/drm-modules/linux-core/nv50_cursor.o
  CC [M]  /usr/src/modules/drm-modules/linux-core/nv50_lut.o
  CC [M]  /usr/src/modules/drm-modules/linux-core/nv50_fb.o
  CC [M]  /usr/src/modules/drm-modules/linux-core/nv50_output.o
  CC [M]  /usr/src/modules/drm-modules/linux-core/nv50_sor.o
  CC [M]  /usr/src/modules/drm-modules/linux-core/nv50_dac.o
  CC [M]  /usr/src/modules/drm-modules/linux-core/nv50_connector.o
  CC [M]  /usr/src/modules/drm-modules/linux-core/nv50_i2c.o
/usr/src/modules/drm-modules/linux-core/nv50_i2c.c: In function &#8216;nv50_i2c_xfer&#8217;:
/usr/src/modules/drm-modules/linux-core/nv50_i2c.c:336: warning: &#8216;rval&#8217; may be used uninitialized in this function
  CC [M]  /usr/src/modules/drm-modules/linux-core/nv50_display.o
  CC [M]  /usr/src/modules/drm-modules/linux-core/nv50_kms_wrapper.o
/usr/src/modules/drm-modules/linux-core/nv50_kms_wrapper.c: In function &#8216;nv50_kms_crtc_set_config&#8217;:
/usr/src/modules/drm-modules/linux-core/nv50_kms_wrapper.c:523: error: &#8216;struct drm_framebuffer&#8217; has no member named &#8216;mm_handle&#8217;
make[4]: *** [/usr/src/modules/drm-modules/linux-core/nv50_kms_wrapper.o] Error 1
make[3]: *** [_module_/usr/src/modules/drm-modules/linux-core] Error 2
make[3]: Leaving directory `/usr/src/linux-headers-2.6.28-2-ub-generic'
make[2]: *** [modules] Error 2
make[2]: Leaving directory `/usr/src/modules/drm-modules/linux-core'
make[1]: *** [binary-modules] Error 2
make[1]: Leaving directory `/usr/src/modules/drm-modules'
make: *** [kdist_build] Error 2

```

As can be seen there were errors in making this build. 


One thing I didn't know what the drm module I use 

Tromod gave this command to try on a stable system to see what module is being used. 

As I have Intrepid on another hard disk I tried it on :-

```
$ lsmod | grep ^drm
drm                    86056  3 i915

```So came to know it was i915.

Now do an upgrade either through the Update manager or through command-line 

```
$ sudo apt-get safe-upgrade
```The following packages were either upgraded or downgraded depending on the versioning given in the archive. 

> 
mesa-utils libpixman-1-0 libglu1-mesa xserver-common libx1-dev libdrm-intel1 mesa-common mesa-common-dev xserver-xorg-core libdrm2 
libglu1-mesa-dev libgl1-mesa-dev libgl1-mesa-dri libgl1-mesa-glx libxi6 
xserver-xorg-video-intelRebooted, got the login screen but couldn't get the keyboard or the mouse to function. 

Talking with Tromod on IRC came to know that xserver-xorg-input-evdev also needed to be done. Till that time 
the Warning now shown on Xorg-edgers-archive was not visisble so had to resort to 

```
$ apt-cache policy xserver-xorg-input-evdev

xserver-xorg-input-evdev:
  Installed: 1:2.1.0-0ubuntu1
  Candidate: 1:2.1.0-0ubuntu1
  Version table:
 *** 1:2.1.0-0ubuntu1 0
        500 http://archive.ubuntu.com jaunty/main Packages
        100 /var/lib/dpkg/status
     1:2.1.0~git-0ubuntu0tormod 0
        500 http://ppa.launchpad.net jaunty/main Packages
xserver-xorg-input-evdev:
  Installed: 1:2.1.0~git-0ubuntu0tormod
  Candidate: 1:2.1.0-0ubuntu1
  Version table:
     1:2.1.0-0ubuntu1 0
        500 http://archive.ubuntu.com jaunty/main Packages
 *** 1:2.1.0~git-0ubuntu0tormod 0
        500 http://ppa.launchpad.net jaunty/main Packages
        100 /var/lib/dpkg/status

```The one which I needed is 1:2.1.0~git-0ubuntu0tormod

So installed it 

```
$ sudo apt-get install xserver-xorg-input-evdev=1:2.1.0~git-0ubuntu0tormod
```Rebooted again and wallah, I had X, login and everything. 

The only major annonyance was that while using gnome-terminal whenever I used the up arrow key I would get this error message. 

[COLOR=Sienna]**no command 33 has been defined **
[/COLOR]
With Metacity written on the window. 

Going back to the main archive was a little harder. This you should do after rebooting in an non-GUI single user mode/rescue mode environment. 

remove or comment the archive files, remove the drm-modules-2.6.28-2-ub-generic (or whichever kernel version you are trying with) , do an apt-cache policy of each file and get the one which is in archive. For e.g. 

```
$ sudo apt-get install xserver-xorg-input-evdev=1:2.1.0-0ubuntu1

```That's about it. Now back to main and looking forward to next week when the xserver and other stuff would be in main.

---

### Post by klange on 2008-12-11
Makefile:154: *** Cannot find a kernel config file.  Stop.

The DRM modules fail to build. I have the kernel header packages.

---

### Post by STEVE555 on 2008-12-11
Hi ShirishAg75,
              I have been trying out the new xserver 1.6 from the PPA repository,but with no success.

I have followed the howto,and one of the links,but I'm still not getting the login screen.

I'm currently using Kubuntu Jaunty Jackalope Alpha 1 and the binary nvidia 180.11 driver from the NVnews.net website.

I have attached my xorg.0.log with this post.

Regards,
       STEVE555

---

### Post by ShirishAg75 on 2008-12-11
WindowSucks, do you have nvidia. Nvidia has issues.
STEVE555 even yours has the same issue. Refer to the lines with [EE]

```

(EE) Failed to load module "nv" (module requirement mismatch, 0)
(EE) No drivers available.

```Your DRM_Module would be a different chipset **NOT** the i915

```
$ sudo env DRM_MODULES="i915" module-assistant -t auto-install drm-modules
```And nvidia does have issues, dunno why though. I'm no guru. I just had an issue and found the solution to the problem for **my** hardware. I just put up the howto with the idea that people having similar issues specifically with intel **legacy** hardware could also see if it helps them. 

I don't have any ATI or nvidia hardware hence don't have much idea how things run therein, sorry

---

### Post by Starks on 2008-12-11
Does i945 use i915?

---

### Post by klange on 2008-12-11
[SIZE="1"](OT: Why would anyone assume, taking a glance at this board, that I am interested in anything other than Intel graphics?)[/SIZE]

'Fraid not, I have an Intel 945, for which the DRM module is i915, but that would not change the result of the command anyway, as all attempts to build the DRM modules fail, even when I don't specify which one to try and build (the module is supposed to build normally without that added argument, simply with `sudo module-assistant auto-install drm-modules`).

Beyond that, having the kernel source tree interfered with the process, as it only needs the headers. Now my problem comes down to this:
```
Bad luck, the kernel headers for the target kernel version could not be found 
and you did not specify other valid kernel headers to use.
      

If the running kernel has been shipped with the Debian distribution, please 
install the package linux-headers-2.6.28-2-ub-generic. If your kernel source 
tree (or headers) is located in some non-usual location, please set the 
KERNELDIRS environment variable to the path of this directory, or 
(alternatively) specify the source directory we build for with the --kernel-dir
option in module-assistant calls.

```


(There are no nVidia drivers in the xorg-edgers PPA, by the way, it's just `intel` and `radeon`)

**e**: I'll also try to help you out: Anything other than evdev is disabled in X these days. Chances are your keyboard is set to something other than the `evdev` layout, and a side effect happens to be the up arrow key being assigned to "Print Screen". "Print Screen" is command 33 in Metacity.

---

### Post by tormod on 2008-12-11
The drivers have to be rebuilt against the new 1.6 xserver. If you are using binary-only drivers, forget about it. Buy your hardware from companies who support open-source development.

---

### Post by tormod on 2008-12-11
> **WindowsSucks said:**
> [SIZE="1"]'Fraid not, I have an Intel 945, for which the DRM module is i915, but that would not change the result of the command anyway, as all attempts to build the DRM modules fail, even when I don't specify which one to try and build (the module is supposed to build normally without that added argument, simply with `sudo module-assistant auto-install drm-modules`).

The current nv kernel module does not build with the 2.6.28 kernel, therefore you have to specify which modules to build, otherwise it will try to build all of them, and fail on nv50...

You can also try without building new drm modules.

> 
If the running kernel has been shipped with the Debian distribution, please 
install the package linux-headers-2.6.28-2-ub-generic. If your kernel source
Sounds like you didn't get the newest kernel package, there should be no "-ub" in the version.

> 
**e**: I'll also try to help you out: Anything other than evdev is disabled in X these days. Chances are your keyboard is set to something other than the `evdev` layout, and a side effect happens to be the up arrow key being assigned to "Print Screen". "Print Screen" is command 33 in Metacity.
Right. It's a bug in 1.6 beta, they're fixing it upstream.

---

### Post by klange on 2008-12-11
-snip-

**e**: After realizing that module-assistant is completely broken, I just extracted the module archive, cd'd into it, and built it manually. It's working... sort of. I'm getting horribly slow framerates, with or without UXA/DRI2 enabled, and I think one of the X updates screwed up my input as my mouse keeps flickering elsewhere. Definitely not a good situation, and I may have to revert back to the vanilla X server in the Jaunty repos.

[http://oasis-games.com/~klange/wellitworks.png](http://oasis-games.com/~klange/wellitworks.png)

---

### Post by ShirishAg75 on 2008-12-11
I just updated the original post to show a build failure as well as where to find the buildlog . Should make it easier for troubleshooting stuff.

---

### Post by klange on 2008-12-12
Ug... I have to say, I'm having significantly better luck using the vesa drivers at the moment than either set of Intel drivers...

---

### Post by STEVE555 on 2008-12-12
Hi guys,
       I've managed to find a partial solution to my problem,here's what I did.
1)I selected the single-user-mode to my latest kernel and booted into it.
2)in recovery mode I selected drop into a root shell and typed in my password.
3)I then typed in```
init 3
``` and waited for it to load up.
4)When I got to tty 3,I typed in my username and password and typed in ```
sudo /etc/init.d/kdm stop
```and typed in my password again.
5)I re-installed my Nvidia binary driver again and typed in startx,but it was still complaining the ABI version was still different.So I ran this:
6)```
startx -- -ignoreABI
```(type in exactly)and at last!! I get a G.U.I for that session:popcorn:

I would need some help in getting that option to stick to boot into the ordinary kernel,and I have to report that the new Xorg loads a lot slower than the previous version.Also my keyboard mapping seems to be different,and I don't know which package I would need to correct it.

Regards,
       STEVE555

---

### Post by tormod on 2008-12-12
The keymapping issues are reported upstream, see [http://lists.freedesktop.org/archives/xorg/2008-December/041473.html](http://lists.freedesktop.org/archives/xorg/2008-December/041473.html) It did not get fixed in xserver 1.6 beta 3, but hopefully soon. There are reasons these are test packages and not released yet :)

For those not comfortable with package manipulation and a bit of debugging, I can't recommend installing the xorg-edgers packages. On the edge means unreleased, not well tested, and there be bugs. But sometimes it works beautifully and you get better performance than in the old, released, stable versions. And some old bugs are fixed (some replaced by new ones).

As written on the web page, the recommended testing is via the live CD, that's safe and after a reboot you're back to normal.

Of course, Ubuntu and upstream developers are very glad for your early testing and the feedback you can provide on the edgy stuff.

---

### Post by Progressive on 2008-12-12
I had DRI2 working before with my R500, but now it is broken. Also, I can't get glx to load. 

```
Xlib:  extension "GLX" missing on display ":0.0".

```

I am also having that freakin annoying problem with my up arrow. Can't wait for it to be fixed upstream. Any temporary fixes?

Also, it seems that the new tear-free video option EXAVSync breaks the new xserver... that or some of the packages in the PPA are not new enough. Granted, I think I remember it working last time. Is it working for anyone else?

---

### Post by STEVE555 on 2008-12-12
Hi Tormod,
         I can give some feedback,I have attached my xorg.o.log and my nvidia-bug-report.log(even though the last one is usually required in the Nvforums which I'm a member of)

If you need nay other logs,I'll try and provide some more if I can.

Regards,
        STEVE555

---

### Post by Starks on 2008-12-13
Build successful.

:3

[http://pastebin.com/f5ffb1590](http://pastebin.com/f5ffb1590)

---

### Post by PmDematagoda on 2008-12-13
> **STEVE555 said:**
> Hi Tormod,
         I can give some feedback,I have attached my xorg.o.log and my nvidia-bug-report.log(even though the last one is usually required in the Nvforums which I'm a member of)

If you need nay other logs,I'll try and provide some more if I can.

Regards,
        STEVE555

Why are you trying to run the Nvidia binary driver on a git X-Server? IMO, Nvidia takes time to support new X-Servers completely and only do so after they are released(same applies for ATi), so while it is possible to run the driver, it may create bugs which may not really be bugs. If you want to use the X-Server properly, I think you should stick either to the nouveau or nv driver.

And about your nv problem, it is probably because you did not update the nv driver package according to:-
```
(EE) module ABI major version (4) doesn't match the server's version (5)
(II) UnloadModule: "nv"
(II) Unloading /usr/lib/xorg/modules/drivers//nv_drv.so
(EE) Failed to load module "nv" (module requirement mismatch, 0)
(EE) No drivers available.
```
I see that the nv driver hasn't shown up yet(does it support git X?), but there is the nouveau driver which is pretty stable for 2D stuff and last I looked, was quite stable overall(except in 3D). Also, you will need to change xorg.conf to use the nouveau driver.

BTW, I say this only as a person who has had a little bit of experience in building and tinkering with X, not as an X dev. So if I'm wrong, my apologies.

---

### Post by tormod on 2008-12-13
> **PmDematagoda said:**
> Why are you trying to run the Nvidia binary driver on a git X-Server? IMO, Nvidia takes time to support new X-Servers completely and only do so after they are released(same applies for ATi), so while it is possible to run the driver, it may create bugs which may not really be bugs. If you want to use the X-Server properly, I think you should stick either to the nouveau or nv driver.
Right, the binary nvidia driver is not meant to be run with git versions of the server. And I can not rebuild the binary driver, because it is... binary.
> 
And about your nv problem, it is probably because you did not update the nv driver package according to:-
[CODE](EE) module ABI major version (4) doesn't match the server's version (5)
Exactly, I haven't updated any nv driver. Sorry, lack of time and I haven't seen any interest for it before now. I did add a nouveau driver once, but it has to be (updated and) rebuilt for xserver 1.6.

---

### Post by tormod on 2008-12-13
I have come to the understanding that the drm modules from libdrm git (drm-modules-source package) is not up to date, and the stock modules in the 2.6.28 kernel might be better. This means you can skip the compiling modules part (module-assistant). Please uninstall the drm-modules-2.6.28* package if you built and installed it with module-assistant.

If this however make things worse, please report.

---

### Post by Progressive on 2008-12-13
Thank you so much. I have uninstalled drm-modules and most of my little glitches have been fixed. With the old drm, when EXA was on my system tray was messed up, plasma would crash occasionally, etc. I am still unable to switch to console (likely because of kernel modesetting) and my keyboard mappings are of course screwed up. Hopefully both of those things will be resolved shortly. I can't wait until kernel 2.6.29 makes it into jaunty... must... have... kernel modesetting.

Also, my glxgears is running 60 times faster than before. The problem I was having earlier with glx was simply that I had forgotten to purge fglrx.

Cheers!

---

### Post by klange on 2008-12-14
> **tormod said:**
> I have come to the understanding that the drm modules from libdrm git (drm-modules-source package) is not up to date, and the stock modules in the 2.6.28 kernel might be better. This means you can skip the compiling modules part (module-assistant). Please uninstall the drm-modules-2.6.28* package if you built and installed it with module-assistant.

If this however make things worse, please report.
The DRM modules in Jaunty are built without GEM/DRI2 support on Intel, which for most people is the entire point of using your repository.

[On a related note...](http://www.youtube.com/watch?v=4K1BlrmKGKU)

---

### Post by tormod on 2008-12-14
> **WindowsSucks said:**
> The DRM modules in Jaunty are built without GEM/DRI2 support on Intel, which for most people is the entire point of using your repository.

I guess we're stuck in the mud like AliBaba describes on [http://phoronix.com/forums/showpost.php?p=55174&postcount=27](http://phoronix.com/forums/showpost.php?p=55174&postcount=27) (is that thread not already linked from this one?)
> 
[On a related note...](http://www.youtube.com/watch?v=4K1BlrmKGKU)
Yes, it's known that DRI2 does not give any *performance* gains yet...

---

### Post by ShirishAg75 on 2008-12-15
Hi all, 
 This is the status of the upgrade atm, dunno should I full-upgrade or wait for some more time. 

```

Reading package lists...
Building dependency tree...
Reading state information...
Reading extended state information...
Initializing package states...
The following packages are BROKEN:
  xserver-xorg xserver-xorg-input-all 
The following packages will be REMOVED:
  xserver-xorg-input-evdev{a} xserver-xorg-input-mouse{a} 
  xserver-xorg-input-vmmouse{a} xserver-xorg-input-wacom{a} 
  xserver-xorg-video-siliconmotion{a} 
The following packages will be upgraded:
  xserver-xorg-core xserver-xorg-input-kbd xserver-xorg-input-synaptics 
  xserver-xorg-video-geode xserver-xorg-video-intel 
  xserver-xorg-video-tseng 
7 packages upgraded, 0 newly installed, 5 to remove and 0 not upgraded.
Need to get 2930kB of archives. After unpacking 1958kB will be freed.
The following packages have unmet dependencies:
  xserver-xorg: Depends: xserver-xorg-input-evdev but it is not installable
  xserver-xorg-input-all: Depends: xserver-xorg-input-evdev but it is not installable
                          Depends: xserver-xorg-input-mouse but it is not installable
                          Depends: xserver-xorg-input-vmmouse but it is not installable
                          Depends: xserver-xorg-input-wacom but it is not installable
The following actions will resolve these dependencies:

Remove the following packages:
xserver-xorg-input-all

Upgrade the following packages:
xserver-xorg-input-evdev [1:2.1.0-0ubuntu1 (now) -> 1:2.1.0-0ubuntu2 (jaunty)]

Score is 190

Accept this solution? [Y/n/q/?]

```

---

### Post by klange on 2008-12-15
Note: If you're getting really, *really* poor performance with Intel drivers, check your Xorg.*.log for a pipe underrun. If you're getting it, you can try and fix it with `Option "ForceEnablePipeA" "true"` (and setting all of your extra monitor-'s [TV, VGA, etc., whatever you don't use] to an "Ignore"'d monitor). This isn't a perfect fix, but I get wonderful framerates now *with* DRI2. However, my server can still crash, bricking the card until a reboot (which is really bad stuff, especially if you're in the middle of working on something, as anything in your X session is gone, twice as bad if you have no SSH access...)

---

### Post by tormod on 2008-12-16
> **ShirishAg75 said:**
> Hi all, 
 This is the status of the upgrade atm, dunno should I full-upgrade or wait for some more time. 

If you're using the 1.6 packages from xorg-edgers, do not install any packages from main before they have upgraded to 1.6 packages. What is important is the compatibility between the xserver and the driver binaries. The same driver source can be used, but is must be rebuilt with the corresponding xserver header files.

---

### Post by ShirishAg75 on 2008-12-16
Hi Tromod, 
 Doing packages from the main. Just saw that today there was an update to the xorg-server [https://lists.ubuntu.com/archives/jaunty-changes/2008-December/001893.html](https://lists.ubuntu.com/archives/jaunty-changes/2008-December/001893.html) as well as couple of drivers [https://lists.ubuntu.com/archives/jaunty-changes/2008-December/001897.html](https://lists.ubuntu.com/archives/jaunty-changes/2008-December/001897.html) and [https://lists.ubuntu.com/archives/jaunty-changes/2008-December/001898.html](https://lists.ubuntu.com/archives/jaunty-changes/2008-December/001898.html)

---

### Post by tormod on 2008-12-16
Excellent. The keyboard map issue has been solved (it was holding back the upload in Jaunty). It has DRI2 enabled. No need for xorg-edgers at the moment :)

---

### Post by ShirishAg75 on 2008-12-16
Still no desktop for me. First up is my apt term.log of the session. 

```

Log started: 2008-12-17  01:12:23
(Reading database ... 234662 files and directories currently installed.) 
Preparing to replace xserver-xorg-input-kbd 1:1.3.1-1ubuntu2 (using .../xserver-xorg-input-kbd_1%3a1.3.1-2ubuntu1_i386.deb) ... 
Unpacking replacement xserver-xorg-input-kbd ... 
Preparing to replace xserver-xorg 1:7.4~5ubuntu5 (using .../xserver-xorg_1%3a7.4~5ubuntu6_i386.deb) ... 
Unpacking replacement xserver-xorg ... 
Processing triggers for man-db ... 
(Reading database ... 234661 files and directories currently installed.) 
Removing xserver-xorg-input-all ... 
Removing xserver-xorg-input-mouse ... 
Processing triggers for man-db ... 
(Reading database ... 234652 files and directories currently installed.) 
Preparing to replace xserver-xorg-input-evdev 1:2.1.0-0ubuntu1 (using .../xserver-xorg-input-evdev_1%3a2.1.0-0ubuntu2_i386.deb) ... 
Unpacking replacement xserver-xorg-input-evdev ... 
Processing triggers for man-db ... 
(Reading database ... 234651 files and directories currently installed.) 
Removing xserver-xorg-input-wacom ... 
Removing xserver-xorg-input-vmmouse ... 
Processing triggers for hal ... 
Regenerating hal fdi cache ... 
 * Restarting Hardware abstraction layer hald       [80G  [74G[ OK ] 
Processing triggers for man-db ... 
(Reading database ... 234632 files and directories currently installed.) 
Preparing to replace xserver-xorg-video-tseng 1:1.2.0-1build2 (using .../xserver-xorg-video-tseng_1%3a1.2.0-1ubuntu1_i386.deb) ... 
Unpacking replacement xserver-xorg-video-tseng ... 
Preparing to replace xserver-xorg-video-siliconmotion 1:1.6.0-1build2 (using .../xserver-xorg-video-siliconmotion_1%3a1.6.0-1ubuntu1_i386.deb) ... 
Unpacking replacement xserver-xorg-video-siliconmotion ... 
Preparing to replace xserver-xorg-video-geode 2.10.1-5 (using .../xserver-xorg-video-geode_2.11.0-1_i386.deb) ... 
Unpacking replacement xserver-xorg-video-geode ... 
Preparing to replace xserver-xorg-video-intel 2:2.5.1-1ubuntu5 (using .../xserver-xorg-video-intel_2%3a2.5.1-1ubuntu6_i386.deb) ... 
Unpacking replacement xserver-xorg-video-intel ... 
Preparing to replace xserver-xorg-input-synaptics 0.15.2-0ubuntu7 (using .../xserver-xorg-input-synaptics_0.15.2-0ubuntu8_i386.deb) ... 
Unpacking replacement xserver-xorg-input-synaptics ... 
Preparing to replace xserver-xorg-core 2:1.5.3-1ubuntu1 (using .../xserver-xorg-core_2%3a1.5.99.3-0ubuntu1_i386.deb) ... 
Unpacking replacement xserver-xorg-core ... 
Processing triggers for man-db ... 
Processing triggers for hal ... 
Regenerating hal fdi cache ... 
 * Restarting Hardware abstraction layer hald       [80G  [74G[ OK ] 
Setting up xserver-xorg-video-tseng (1:1.2.0-1ubuntu1) ... 
Setting up xserver-xorg-video-siliconmotion (1:1.6.0-1ubuntu1) ... 
Setting up xserver-xorg-video-geode (2.11.0-1) ... 
Setting up xserver-xorg-core (2:1.5.99.3-0ubuntu1) ... 
 
Setting up xserver-xorg-input-kbd (1:1.3.1-2ubuntu1) ... 
Setting up xserver-xorg-video-intel (2:2.5.1-1ubuntu6) ... 
 
Setting up xserver-xorg-input-synaptics (0.15.2-0ubuntu8) ... 
Setting up xserver-xorg-input-evdev (1:2.1.0-0ubuntu2) ... 
Setting up xserver-xorg (1:7.4~5ubuntu6) ... 
 
Processing triggers for libc6 ... 
ldconfig deferred processing now taking place 
Log ended: 2008-12-17  01:12:44

```Here's the /var/log/Xorg.0.log

```

This is a pre-release version of the X server from The X.Org Foundation.
It is not supported in any way.
Bugs may be filed in the bugzilla at http://bugs.freedesktop.org/.
Select the "xorg" product for bugs you find in this release.
Before reporting bugs in pre-release versions please check the
latest version in the X.Org Foundation git repository.
See http://wiki.x.org/wiki/GitPage for git access instructions.

X.Org X Server 1.5.99.3
Release Date: (unreleased)
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-14-server i686 Ubuntu
Current Operating System: Linux Mugglewille-desktop 2.6.28-2-generic #3-Ubuntu SMP Thu Dec 4 21:49:06 UTC 2008 i686
Build Date: 15 December 2008  09:48:13AM
xorg-server 2:1.5.99.3-0ubuntu1 (buildd@rothera.buildd) 
    Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Wed Dec 17 01:15:13 2008
(==) Using config file: "/etc/X11/xorg.conf"
(==) No Layout section.  Using the first Screen section.
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "Configured Monitor"
(**) |   |-->Device "Configured Video Device"
(==) Automatically adding devices
(==) Automatically enabling devices
(==) No FontPath specified.  Using compiled-in default.
(==) FontPath set to:
    built-ins
(==) ModulePath set to "/usr/lib/xorg/modules"
(II) Cannot locate a core pointer device.
(II) Cannot locate a core keyboard device.
(II) The server relies on HAL to provide the list of input devices.
    If no devices become available, reconfigure HAL or disable AllowEmptyInput.
(II) Loader magic: 0x1ac0
(II) Module ABI versions:
    X.Org ANSI C Emulation: 0.4
    X.Org Video Driver: 5.0
    X.Org XInput driver : 4.0
    X.Org Server Extension : 2.0
(II) Loader running on linux
(--) using VT number 8

(--) PCI:*(0@0:2:0) Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device rev 3, Mem @ 0xd0000000/0, 0xdff80000/0
(II) Open ACPI successful (/var/run/acpid.socket)
(II) System resource ranges:
    [0] -1    0    0xffffffff - 0xffffffff (0x1) MX[b]
    [1] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[b]
    [2] -1    0    0x000c0000 - 0x000effff (0x30000) MX[b]
    [3] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[b]
    [4] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[b]
    [5] -1    0    0x00000000 - 0x00000000 (0x1) IX[b]
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions//libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
    compiled for 1.5.99.3, module version = 1.0.0
    Module class: X.Org Server Extension
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension MIT-SCREEN-SAVER
(II) Loading extension XFree86-VidModeExtension
(II) Loading extension XFree86-DGA
(II) Loading extension DPMS
(II) Loading extension XVideo
(II) Loading extension XVideo-MotionCompensation
(II) Loading extension X-Resource
(II) LoadModule: "dbe"
(II) Loading /usr/lib/xorg/modules/extensions//libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
    compiled for 1.5.99.3, module version = 1.0.0
    Module class: X.Org Server Extension
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="X.Org Foundation"
    compiled for 1.5.99.3, module version = 1.0.0
    ABI class: X.Org Server Extension, version 2.0
(==) AIGLX enabled
(==) Exporting typical set of GLX visuals
(II) Loading extension GLX
(II) LoadModule: "record"
(II) Loading /usr/lib/xorg/modules/extensions//librecord.so
(II) Module record: vendor="X.Org Foundation"
    compiled for 1.5.99.3, module version = 1.13.0
    Module class: X.Org Server Extension
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension RECORD
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions//libdri.so
(II) Module dri: vendor="X.Org Foundation"
    compiled for 1.5.99.3, module version = 1.0.0
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension XFree86-DRI
(II) LoadModule: "dri2"
(II) Loading /usr/lib/xorg/modules/extensions//libdri2.so
(II) Module dri2: vendor="X.Org Foundation"
    compiled for 1.5.99.3, module version = 1.0.0
    ABI class: X.Org Server Extension, version 2.0
(II) Loading extension DRI2
(II) Scanning /usr/share/xserver-xorg/pci directory for additional PCI ID's supported by the drivers
(II) Matched intel from file name intel.ids
(==) Matched intel for the autoconfigured driver
(==) Assigned the driver to the xf86ConfigLayout
(II) LoadModule: "intel"
(II) Loading /usr/lib/xorg/modules/drivers//intel_drv.so
(II) Module intel: vendor="X.Org Foundation"
    compiled for 1.5.99.3, module version = 2.5.1
    Module class: X.Org Video Driver
    ABI class: X.Org Video Driver, version 5.0
(II) intel: Driver for Intel Integrated Graphics Chipsets: i810,
    i810-dc100, i810e, i815, i830M, 845G, 852GM/855GM, 865G, 915G,
    E7221 (i915), 915GM, 945G, 945GM, 945GME, 965G, G35, 965Q, 946GZ,
    965GM, 965GME/GLE, G33, Q35, Q33,
    Mobile IntelÂ® GM45 Express Chipset,
    Intel Integrated Graphics Device, G45/G43, Q45/Q43, G41
(II) Primary Device is: PCI 00@00:02:0
(II) resource ranges after xf86ClaimFixedResources() call:
    [0] -1    0    0xffffffff - 0xffffffff (0x1) MX[b]
    [1] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[b]
    [2] -1    0    0x000c0000 - 0x000effff (0x30000) MX[b]
    [3] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[b]
    [4] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[b]
    [5] -1    0    0x00000000 - 0x00000000 (0x1) IX[b]
(II) resource ranges after probing:
    [0] -1    0    0xffffffff - 0xffffffff (0x1) MX[b]
    [1] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[b]
    [2] -1    0    0x000c0000 - 0x000effff (0x30000) MX[b]
    [3] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[b]
    [4] 0    0    0x000a0000 - 0x000affff (0x10000) MS[b]
    [5] 0    0    0x000b0000 - 0x000b7fff (0x8000) MS[b]
    [6] 0    0    0x000b8000 - 0x000bffff (0x8000) MS[b]
    [7] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[b]
    [8] -1    0    0x00000000 - 0x00000000 (0x1) IX[b]
    [9] 0    0    0x000003b0 - 0x000003bb (0xc) IS[b]
    [10] 0    0    0x000003c0 - 0x000003df (0x20) IS[b]
(II) Loading sub module "vgahw"
(II) LoadModule: "vgahw"
(II) Loading /usr/lib/xorg/modules//libvgahw.so
(II) Module vgahw: vendor="X.Org Foundation"
    compiled for 1.5.99.3, module version = 0.1.0
    ABI class: X.Org Video Driver, version 5.0
(II) intel(0): Creating default Display subsection in Screen section
    "Default Screen" for depth/fbbpp 24/32
(==) intel(0): Depth 24, (--) framebuffer bpp 32
(==) intel(0): RGB weight 888
(==) intel(0): Default visual is TrueColor
(II) intel(0): Integrated Graphics Chipset: Intel(R) 845G
(--) intel(0): Chipset: "845G"
(--) intel(0): Linear framebuffer at 0xD0000000
(--) intel(0): IO registers at addr 0xDFF80000
(WW) intel(0): libpciaccess reported 0 rom size, guessing 64kB
(==) intel(0): Using EXA for acceleration
(II) intel(0): 1 display pipe available.
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"
(II) Module "ddc" already built-in
(II) Loading sub module "i2c"
(II) LoadModule: "i2c"
(II) Module "i2c" already built-in
(II) intel(0): Output VGA using monitor section Configured Monitor
(II) intel(0): I2C bus "DVODDC_D" initialized.
(II) Loading sub module "sil164"
(II) LoadModule: "sil164"
(II) Loading /usr/lib/xorg/modules/drivers//sil164.so
(II) Module sil164: vendor="X.Org Foundation"
    compiled for 1.5.99.3, module version = 1.0.0
    ABI class: X.Org Video Driver, version 5.0
(II) intel(0): I2C bus "DVOI2C_E" initialized.
(II) Loading sub module "ch7xxx"
(II) LoadModule: "ch7xxx"
(II) Loading /usr/lib/xorg/modules/drivers//ch7xxx.so
(II) Module ch7xxx: vendor="X.Org Foundation"
    compiled for 1.5.99.3, module version = 1.0.0
    ABI class: X.Org Video Driver, version 5.0
(II) intel(0): I2C bus "DVOI2C_E" removed.
(II) intel(0): I2C bus "DVOI2C_E" initialized.
(II) Loading sub module "ivch"
(II) LoadModule: "ivch"
(II) Loading /usr/lib/xorg/modules/drivers//ivch.so
(II) Module ivch: vendor="X.Org Foundation"
    compiled for 1.5.99.3, module version = 1.0.0
    ABI class: X.Org Video Driver, version 5.0
(II) intel(0): I2C bus "DVOI2C_E" removed.
(II) intel(0): I2C bus "DVOI2C_B" initialized.
(II) Loading sub module "tfp410"
(II) LoadModule: "tfp410"
(II) Loading /usr/lib/xorg/modules/drivers//tfp410.so
(II) Module tfp410: vendor="X.Org Foundation"
    compiled for 1.5.99.3, module version = 1.0.0
    ABI class: X.Org Video Driver, version 5.0
(II) intel(0): I2C bus "DVOI2C_B" removed.
(II) intel(0): I2C bus "DVOI2C_E" initialized.
(II) Loading sub module "ch7017"
(II) LoadModule: "ch7017"
(II) Loading /usr/lib/xorg/modules/drivers//ch7017.so
(II) Module ch7017: vendor="X.Org Foundation"
    compiled for 1.5.99.3, module version = 1.0.0
    ABI class: X.Org Video Driver, version 5.0
(II) intel(0): I2C bus "DVOI2C_E" removed.
(II) intel(0): I2C bus "DVOI2C_E" initialized.
(II) intel(0): I2C bus "DVOI2C_E" removed.
(II) intel(0): I2C bus "DVODDC_D" removed.

Backtrace:
0: /usr/bin/X11/X(xorg_backtrace+0x3b) [0x813263b]
1: /usr/bin/X11/X(xf86SigHandler+0x51) [0x80c5c51]
2: [0xb7fbb400]
3: /usr/bin/X11/X(xf86CrtcSetMode+0x36) [0x80ed4f6]
4: /usr/lib/xorg/modules/drivers//intel_drv.so(i830GetLoadDetectPipe+0x15d) [0xb79e634d]
5: /usr/lib/xorg/modules/drivers//intel_drv.so [0xb79e0495]
6: /usr/bin/X11/X(xf86ProbeOutputModes+0x1a0) [0x80ed8b0]
7: /usr/bin/X11/X(xf86InitialConfiguration+0x149) [0x80ee449]
8: /usr/lib/xorg/modules/drivers//intel_drv.so [0xb79ebaa9]
9: /usr/lib/xorg/modules/drivers//intel_drv.so [0xb79edf48]
10: /usr/bin/X11/X(InitOutput+0xe13) [0x80ae953]
11: /usr/bin/X11/X(main+0x1e1) [0x80717e1]
12: /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe5) [0xb7b88775]
13: /usr/bin/X11/X [0x8070e71]

Fatal server error:
Caught signal 11.  Server aborting


Please consult the The X.Org Foundation support 
     at http://wiki.x.org
 for help. 
Please also check the log file at "/var/log/Xorg.0.log" for additional information.

```and here's the .xsession-errors file 

```

/etc/gdm/Xsession: Beginning session setup...
Setting IM through im-switch for locale=en_IN.
Start IM through /etc/X11/xinit/xinput.d/all_ALL linked to /etc/X11/xinit/xinput.d/default.
Unable to create /home/shirish/.dbus/session-bus
gnome-session[7110]: WARNING: Unable to find provider 'gnome-wm' of required component 'windowmanager'
Window manager warning: Failed to read saved session file /home/shirish/.config/metacity/sessions/109af3ad5af47ee36f122894701878835700000071100015.ms: Failed to open file '/home/shirish/.config/metacity/sessions/109af3ad5af47ee36f122894701878835700000071100015.ms': No such file or directory
E: socket-client.c: socket(): Address family not supported by protocol
Failed to play sound: Not available

(nautilus:7272): GLib-GObject-WARNING **: Two different plugins tried to register 'NautilusBurn'.

(nautilus:7272): GLib-GObject-CRITICAL **: g_type_add_interface_dynamic: assertion `G_TYPE_IS_INSTANTIATABLE (instance_type)' failed

(nautilus:7272): GLib-GObject-CRITICAL **: g_type_add_interface_dynamic: assertion `G_TYPE_IS_INSTANTIATABLE (instance_type)' failed
seahorse nautilus module initialized
Initializing nautilus-share extension
E: socket-client.c: socket(): Address family not supported by protocol

** (nautilus:7272): WARNING **: Unable to add monitor: Not supported
E: socket-client.c: socket(): Address family not supported by protocol
E: socket-client.c: socket(): Address family not supported by protocol
E: socket-client.c: socket(): Address family not supported by protocol
E: socket-client.c: socket(): Address family not supported by protocol
E: socket-client.c: socket(): Address family not supported by protocol

(gnome-panel:7271): Gdk-WARNING **: /build/buildd/gtk+2.0-2.14.5/gdk/x11/gdkdrawable-x11.c:878 drawable is not a pixmap or window
E: socket-client.c: socket(): Address family not supported by protocol
E: socket-client.c: socket(): Address family not supported by protocol
E: socket-client.c: socket(): Address family not supported by protocol
gnome-session[7110]: WARNING: Application 'libcanberra-login-sound.desktop' failed to register before timeout
E: socket-client.c: socket(): Address family not supported by protocol
Connection failure: Connection refused
I: caps.c: Limited capabilities successfully to CAP_SYS_NICE.
I: caps.c: Dropping root priviliges.
I: caps.c: Limited capabilities successfully to CAP_SYS_NICE.
W: ltdl-bind-now.c: Failed to find original dlopen loader.
E: socket-client.c: socket(): Address family not supported by protocol

** (nm-applet:7549): WARNING **: No connections defined
Window manager warning: Error on command 32 "(null)": No command 33 has been defined.

Window manager warning: Error on command 32 "(null)": No command 33 has been defined.

  PID TTY          TIME CMD
 7569 ?        00:00:00 pulseaudio
Window manager warning: Error on command 32 "(null)": No command 33 has been defined.

Window manager warning: Error on command 32 "(null)": No command 33 has been defined.

Window manager warning: Error on command 32 "(null)": No command 33 has been defined.

Window manager warning: Error on command 32 "(null)": No command 33 has been defined.

Window manager warning: Error on command 32 "(null)": No command 33 has been defined.

Window manager warning: Error on command 32 "(null)": No command 33 has been defined.

Window manager warning: Error on command 32 "(null)": No command 33 has been defined.

Window manager warning: Error on command 32 "(null)": No command 33 has been defined.

Window manager warning: Error on command 32 "(null)": No command 33 has been defined.

Window manager warning: Error on command 32 "(null)": No command 33 has been defined.

Window manager warning: Error on command 32 "(null)": No command 33 has been defined.

Window manager warning: Error on command 32 "(null)": No command 33 has been defined.

Window manager warning: Error on command 32 "(null)": No command 33 has been defined.

Window manager warning: Error on command 32 "(null)": No command 33 has been defined.

Window manager warning: Error on command 32 "(null)": No command 33 has been defined.

```

Any ideas anybody?

---

### Post by klange on 2008-12-16
@tormod: The Ubuntu modules and drivers aren't yet DRI2 capable, at least not for an i945, on the newest kernel (-3), with the newest libdrm/mesa and X. However, DRI2 is "there" and UXA is running (might be a lack of GEM, I don't know how to see if it's actually active, but judging from the stuff in /proc/dri/0/*gem*, I would say it's not running).

---

### Post by Triggerhapp on 2008-12-17
ShirishAg75, I am getting the same problem as you (just letting you know you're not alone there :P)

---

### Post by klim8 on 2008-12-17
X intel driver crashed at xf86CrtcSetMode():

[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/308225](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/308225)

It seems fixed in upstream so we only have to wait

---

### Post by Paulo Khouri on 2009-01-25
I dont get assign the PPA repository anymore.

W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 4F191A5A8844C542

to SOLVE: [http://ubuntuforums.org/showthread.php?t=1046158](http://ubuntuforums.org/showthread.php?t=1046158)

Thanx

---

### Post by tormod on 2009-01-25
> **Paulo Khouri said:**
> I dont get assign the PPA repository anymore.

W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 4F191A5A8844C542
AFAIK, it is not a fatal error. Packages will be installed anyway.

---

### Post by Gina on 2009-01-25
> **tormod said:**
> AFAIK, it is not a fatal error. Packages will be installed anyway.Yes, that's what I've found - you get a warning message and if you give the go-ahead the package is installed.

---

