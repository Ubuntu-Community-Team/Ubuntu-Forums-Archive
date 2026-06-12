---
title: "nvidia-352-dev will not update or uninstall"
date: 2016-10-17
forum: Installation &amp; Upgrades
---

### Post by vanquishedangel on 2016-10-17
Sorry if this has been posted but when checking the forums the search said I needed to add more constraints.

Anyway I am hoping to remove nvidia-352-dev but it is not happening. I have tried booting into safe mode and then going to shell command prompt and typing:

sudo apt-get purge nvidia* but this one thing will not uninstall, it say there were errors with this package. There is something about a new script is missing, or the new program script is missing or something. It will not update either. I waited for the upgrade because I was hoping it would over write it but that did not work. I tried stopping lightdm before the commands but that failed as well.

---

### Post by T.J. on 2016-10-17
Please post the errors if possible.  It is important.

---

### Post by vanquishedangel on 2016-10-18
Here is the terminal output after running sudo apt-get purge nvidia* (sorry about first post, was half awake on 12 hours shifts)

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Note, selecting 'nvidia-325-updates' for glob 'nvidia*'
Note, selecting 'nvidia-346-updates' for glob 'nvidia*'
Note, selecting 'nvidia-driver-binary' for glob 'nvidia*'
Note, selecting 'nvidia-331-dev' for glob 'nvidia*'
Note, selecting 'nvidia-304-updates-dev' for glob 'nvidia*'
Note, selecting 'nvidia-libopencl1-346-updates' for glob 'nvidia*'
Note, selecting 'nvidia-340-updates-uvm' for glob 'nvidia*'
Note, selecting 'nvidia-331-updates-uvm' for glob 'nvidia*'
Note, selecting 'nvidia-cg-toolkit' for glob 'nvidia*'
Note, selecting 'nvidia-opencl-icd-340-updates' for glob 'nvidia*'
Note, selecting 'nvidia' for glob 'nvidia*'
Note, selecting 'nvidia-driver' for glob 'nvidia*'
Note, selecting 'nvidia-modprobe' for glob 'nvidia*'
Note, selecting 'nvidia-texture-tools' for glob 'nvidia*'
Note, selecting 'nvidia-legacy-340xx-vdpau-driver' for glob 'nvidia*'
Note, selecting 'nvidia-349-updates' for glob 'nvidia*'
Note, selecting 'nvidia-opencl-icd-304-updates' for glob 'nvidia*'
Note, selecting 'nvidia-310-updates' for glob 'nvidia*'
Note, selecting 'nvidia-331-updates' for glob 'nvidia*'
Note, selecting 'nvidia-352-dev' for glob 'nvidia*'
Note, selecting 'nvidia-vdpau-driver' for glob 'nvidia*'
Note, selecting 'nvidia-346-dev' for glob 'nvidia*'
Note, selecting 'nvidia-libopencl1-331-updates' for glob 'nvidia*'
Note, selecting 'nvidia-smi' for glob 'nvidia*'
Note, selecting 'nvidia-opencl-icd-361-updates' for glob 'nvidia*'
Note, selecting 'nvidia-313-updates' for glob 'nvidia*'
Note, selecting 'nvidia-legacy-340xx-kernel-dkms' for glob 'nvidia*'
Note, selecting 'nvidia-334-updates' for glob 'nvidia*'
Note, selecting 'nvidia-331-uvm' for glob 'nvidia*'
Note, selecting 'nvidia-prime' for glob 'nvidia*'
Note, selecting 'nvidia-kernel-dkms' for glob 'nvidia*'
Note, selecting 'nvidia-current-updates' for glob 'nvidia*'
Note, selecting 'nvidia-340-dev' for glob 'nvidia*'
Note, selecting 'nvidia-nsight' for glob 'nvidia*'
Note, selecting 'nvidia-common' for glob 'nvidia*'
Note, selecting 'nvidia-opencl-icd-346-updates' for glob 'nvidia*'
Note, selecting 'nvidia-352-updates' for glob 'nvidia*'
Note, selecting 'nvidia-current-dev' for glob 'nvidia*'
Note, selecting 'nvidia-libopencl1-352-updates' for glob 'nvidia*'
Note, selecting 'nvidia-355-updates' for glob 'nvidia*'
Note, selecting 'nvidia-current' for glob 'nvidia*'
Note, selecting 'nvidia-profiler' for glob 'nvidia*'
Note, selecting 'nvidia-337-updates' for glob 'nvidia*'
Note, selecting 'nvidia-358-updates' for glob 'nvidia*'
Note, selecting 'nvidia-367-dev' for glob 'nvidia*'
Note, selecting 'nvidia-cuda-toolkit' for glob 'nvidia*'
Note, selecting 'nvidia-legacy-304xx-driver' for glob 'nvidia*'
Note, selecting 'nvidia-340-updates-dev' for glob 'nvidia*'
Note, selecting 'nvidia-319-updates' for glob 'nvidia*'
Note, selecting 'nvidia-304-dev' for glob 'nvidia*'
Note, selecting 'nvidia-331-updates-dev' for glob 'nvidia*'
Note, selecting 'nvidia-visual-profiler' for glob 'nvidia*'
Note, selecting 'nvidia-persistenced' for glob 'nvidia*'
Note, selecting 'nvidia-current-updates-dev' for glob 'nvidia*'
Note, selecting 'nvidia-361-dev' for glob 'nvidia*'
Note, selecting 'nvidia-settings-binary' for glob 'nvidia*'
Note, selecting 'nvidia-361-updates-dev' for glob 'nvidia*'
Note, selecting 'nvidia-libopencl1-304' for glob 'nvidia*'
Note, selecting 'nvidia-libopencl1-331' for glob 'nvidia*'
Note, selecting 'nvidia-libopencl1-340' for glob 'nvidia*'
Note, selecting 'nvidia-libopencl1-346' for glob 'nvidia*'
Note, selecting 'nvidia-libopencl1-352' for glob 'nvidia*'
Note, selecting 'nvidia-libopencl1-361' for glob 'nvidia*'
Note, selecting 'nvidia-libopencl1-367' for glob 'nvidia*'
Note, selecting 'nvidia-352-updates-dev' for glob 'nvidia*'
Note, selecting 'nvidia-opencl-icd-331-updates' for glob 'nvidia*'
Note, selecting 'nvidia-opencl-icd-352-updates' for glob 'nvidia*'
Note, selecting 'nvidia-304-updates' for glob 'nvidia*'
Note, selecting 'nvidia-340-uvm' for glob 'nvidia*'
Note, selecting 'nvidia-legacy-340xx-driver' for glob 'nvidia*'
Note, selecting 'nvidia-libopencl1-304-updates' for glob 'nvidia*'
Note, selecting 'nvidia-cuda-dev' for glob 'nvidia*'
Note, selecting 'nvidia-cuda-doc' for glob 'nvidia*'
Note, selecting 'nvidia-340-updates' for glob 'nvidia*'
Note, selecting 'nvidia-361-updates' for glob 'nvidia*'
Note, selecting 'nvidia-libopencl1-dev' for glob 'nvidia*'
Note, selecting 'nvidia-opencl-dev' for glob 'nvidia*'
Note, selecting 'nvidia-legacy-304xx-kernel-dkms' for glob 'nvidia*'
Note, selecting 'nvidia-cg-dev' for glob 'nvidia*'
Note, selecting 'nvidia-cg-doc' for glob 'nvidia*'
Note, selecting 'nvidia-libopencl1' for glob 'nvidia*'
Note, selecting 'nvidia-libopencl1-340-updates' for glob 'nvidia*'
Note, selecting 'nvidia-libopencl1-361-updates' for glob 'nvidia*'
Note, selecting 'nvidia-opencl-icd-304' for glob 'nvidia*'
Note, selecting 'nvidia-opencl-icd-331' for glob 'nvidia*'
Note, selecting 'nvidia-opencl-icd-340' for glob 'nvidia*'
Note, selecting 'nvidia-opencl-icd-346' for glob 'nvidia*'
Note, selecting 'nvidia-opencl-icd-352' for glob 'nvidia*'
Note, selecting 'nvidia-opencl-icd-361' for glob 'nvidia*'
Note, selecting 'nvidia-opencl-icd-367' for glob 'nvidia*'
Note, selecting 'nvidia-cuda-gdb' for glob 'nvidia*'
Note, selecting 'nvidia-experimental-304' for glob 'nvidia*'
Note, selecting 'nvidia-experimental-310' for glob 'nvidia*'
Note, selecting 'nvidia-experimental-313' for glob 'nvidia*'
Note, selecting 'nvidia-experimental-319' for glob 'nvidia*'
Note, selecting 'nvidia-experimental-325' for glob 'nvidia*'
Note, selecting 'nvidia-experimental-331' for glob 'nvidia*'
Note, selecting 'nvidia-experimental-334' for glob 'nvidia*'
Note, selecting 'nvidia-experimental-337' for glob 'nvidia*'
Note, selecting 'nvidia-experimental-340' for glob 'nvidia*'
Note, selecting 'nvidia-experimental-343' for glob 'nvidia*'
Note, selecting 'nvidia-experimental-346' for glob 'nvidia*'
Note, selecting 'nvidia-experimental-349' for glob 'nvidia*'
Note, selecting 'nvidia-experimental-352' for glob 'nvidia*'
Note, selecting 'nvidia-experimental-355' for glob 'nvidia*'
Note, selecting 'nvidia-experimental-358' for glob 'nvidia*'
Note, selecting 'nvidia-experimental-304-dev' for glob 'nvidia*'
Note, selecting 'nvidia-experimental-361' for glob 'nvidia*'
Note, selecting 'nvidia-experimental-364' for glob 'nvidia*'
Note, selecting 'nvidia-343-updates' for glob 'nvidia*'
Note, selecting 'nvidia-364-updates' for glob 'nvidia*'
Note, selecting 'nvidia-304' for glob 'nvidia*'
Note, selecting 'nvidia-310' for glob 'nvidia*'
Note, selecting 'nvidia-313' for glob 'nvidia*'
Note, selecting 'nvidia-319' for glob 'nvidia*'
Note, selecting 'nvidia-325' for glob 'nvidia*'
Note, selecting 'nvidia-331' for glob 'nvidia*'
Note, selecting 'nvidia-334' for glob 'nvidia*'
Note, selecting 'nvidia-337' for glob 'nvidia*'
Note, selecting 'nvidia-340' for glob 'nvidia*'
Note, selecting 'nvidia-343' for glob 'nvidia*'
Note, selecting 'nvidia-346' for glob 'nvidia*'
Note, selecting 'nvidia-349' for glob 'nvidia*'
Note, selecting 'nvidia-352' for glob 'nvidia*'
Note, selecting 'nvidia-355' for glob 'nvidia*'
Note, selecting 'nvidia-358' for glob 'nvidia*'
Note, selecting 'nvidia-361' for glob 'nvidia*'
Note, selecting 'nvidia-364' for glob 'nvidia*'
Note, selecting 'nvidia-367' for glob 'nvidia*'
Note, selecting 'nvidia-346-updates-dev' for glob 'nvidia*'
Note, selecting 'nvidia-settings' for glob 'nvidia*'
Note, selecting 'nvidia-opencl-icd' for glob 'nvidia*'
Note, selecting 'nvidia-settings' instead of 'nvidia-settings-binary'
Package 'nvidia-libopencl1-dev' is not installed, so not removed
Package 'nvidia-libopencl1' is not installed, so not removed
Package 'nvidia-vdpau-driver' is not installed, so not removed
Package 'nvidia-legacy-340xx-vdpau-driver' is not installed, so not removed
Package 'nvidia-driver' is not installed, so not removed
Package 'nvidia-legacy-340xx-driver' is not installed, so not removed
Package 'nvidia-legacy-304xx-driver' is not installed, so not removed
Package 'nvidia-kernel-dkms' is not installed, so not removed
Package 'nvidia-legacy-340xx-kernel-dkms' is not installed, so not removed
Package 'nvidia-legacy-304xx-kernel-dkms' is not installed, so not removed
Package 'nvidia' is not installed, so not removed
Package 'nvidia-310' is not installed, so not removed
Package 'nvidia-310-updates' is not installed, so not removed
Package 'nvidia-experimental-310' is not installed, so not removed
Package 'nvidia-313' is not installed, so not removed
Package 'nvidia-313-updates' is not installed, so not removed
Package 'nvidia-experimental-313' is not installed, so not removed
Package 'nvidia-319' is not installed, so not removed
Package 'nvidia-319-updates' is not installed, so not removed
Package 'nvidia-experimental-319' is not installed, so not removed
Package 'nvidia-325' is not installed, so not removed
Package 'nvidia-325-updates' is not installed, so not removed
Package 'nvidia-experimental-325' is not installed, so not removed
Package 'nvidia-experimental-331' is not installed, so not removed
Package 'nvidia-334' is not installed, so not removed
Package 'nvidia-334-updates' is not installed, so not removed
Package 'nvidia-experimental-334' is not installed, so not removed
Package 'nvidia-337' is not installed, so not removed
Package 'nvidia-337-updates' is not installed, so not removed
Package 'nvidia-experimental-337' is not installed, so not removed
Package 'nvidia-experimental-340' is not installed, so not removed
Package 'nvidia-343' is not installed, so not removed
Package 'nvidia-343-updates' is not installed, so not removed
Package 'nvidia-experimental-343' is not installed, so not removed
Package 'nvidia-experimental-346' is not installed, so not removed
Package 'nvidia-349' is not installed, so not removed
Package 'nvidia-349-updates' is not installed, so not removed
Package 'nvidia-experimental-349' is not installed, so not removed
Package 'nvidia-experimental-352' is not installed, so not removed
Package 'nvidia-355' is not installed, so not removed
Package 'nvidia-355-updates' is not installed, so not removed
Package 'nvidia-experimental-355' is not installed, so not removed
Package 'nvidia-358' is not installed, so not removed
Package 'nvidia-358-updates' is not installed, so not removed
Package 'nvidia-experimental-358' is not installed, so not removed
Package 'nvidia-experimental-361' is not installed, so not removed
Package 'nvidia-364' is not installed, so not removed
Package 'nvidia-364-updates' is not installed, so not removed
Package 'nvidia-experimental-364' is not installed, so not removed
Package 'nvidia-smi' is not installed, so not removed
Note, selecting 'libnvtt-bin' instead of 'nvidia-texture-tools'
Package 'nvidia-304' is not installed, so not removed
Package 'nvidia-304-dev' is not installed, so not removed
Package 'nvidia-304-updates' is not installed, so not removed
Package 'nvidia-304-updates-dev' is not installed, so not removed
Package 'nvidia-331' is not installed, so not removed
Package 'nvidia-331-dev' is not installed, so not removed
Package 'nvidia-331-updates' is not installed, so not removed
Package 'nvidia-331-updates-dev' is not installed, so not removed
Package 'nvidia-331-updates-uvm' is not installed, so not removed
Package 'nvidia-331-uvm' is not installed, so not removed
Package 'nvidia-340' is not installed, so not removed
Package 'nvidia-340-dev' is not installed, so not removed
Package 'nvidia-340-updates' is not installed, so not removed
Package 'nvidia-340-updates-dev' is not installed, so not removed
Package 'nvidia-340-updates-uvm' is not installed, so not removed
Package 'nvidia-340-uvm' is not installed, so not removed
Package 'nvidia-346' is not installed, so not removed
Package 'nvidia-346-dev' is not installed, so not removed
Package 'nvidia-346-updates' is not installed, so not removed
Package 'nvidia-346-updates-dev' is not installed, so not removed
Package 'nvidia-352' is not installed, so not removed
Package 'nvidia-352-updates' is not installed, so not removed
Package 'nvidia-352-updates-dev' is not installed, so not removed
Package 'nvidia-361' is not installed, so not removed
Package 'nvidia-361-updates' is not installed, so not removed
Package 'nvidia-361-updates-dev' is not installed, so not removed
Package 'nvidia-current' is not installed, so not removed
Package 'nvidia-current-dev' is not installed, so not removed
Package 'nvidia-current-updates' is not installed, so not removed
Package 'nvidia-current-updates-dev' is not installed, so not removed
Package 'nvidia-experimental-304' is not installed, so not removed
Package 'nvidia-experimental-304-dev' is not installed, so not removed
Package 'nvidia-opencl-icd-304' is not installed, so not removed
Package 'nvidia-opencl-icd-340' is not installed, so not removed
Package 'nvidia-common' is not installed, so not removed
Package 'nvidia-cg-dev' is not installed, so not removed
Package 'nvidia-cg-doc' is not installed, so not removed
Package 'nvidia-cg-toolkit' is not installed, so not removed
Package 'nvidia-cuda-dev' is not installed, so not removed
Package 'nvidia-cuda-doc' is not installed, so not removed
Package 'nvidia-cuda-gdb' is not installed, so not removed
Package 'nvidia-cuda-toolkit' is not installed, so not removed
Package 'nvidia-libopencl1-304' is not installed, so not removed
Package 'nvidia-libopencl1-304-updates' is not installed, so not removed
Package 'nvidia-libopencl1-331' is not installed, so not removed
Package 'nvidia-libopencl1-331-updates' is not installed, so not removed
Package 'nvidia-libopencl1-340' is not installed, so not removed
Package 'nvidia-libopencl1-340-updates' is not installed, so not removed
Package 'nvidia-libopencl1-346' is not installed, so not removed
Package 'nvidia-libopencl1-346-updates' is not installed, so not removed
Package 'nvidia-libopencl1-352' is not installed, so not removed
Package 'nvidia-libopencl1-352-updates' is not installed, so not removed
Package 'nvidia-libopencl1-361' is not installed, so not removed
Package 'nvidia-libopencl1-361-updates' is not installed, so not removed
Package 'nvidia-libopencl1-367' is not installed, so not removed
Package 'nvidia-modprobe' is not installed, so not removed
Package 'nvidia-nsight' is not installed, so not removed
Package 'nvidia-opencl-dev' is not installed, so not removed
Package 'nvidia-opencl-icd-304-updates' is not installed, so not removed
Package 'nvidia-opencl-icd-331' is not installed, so not removed
Package 'nvidia-opencl-icd-331-updates' is not installed, so not removed
Package 'nvidia-opencl-icd-340-updates' is not installed, so not removed
Package 'nvidia-opencl-icd-346' is not installed, so not removed
Package 'nvidia-opencl-icd-346-updates' is not installed, so not removed
Package 'nvidia-opencl-icd-352' is not installed, so not removed
Package 'nvidia-opencl-icd-352-updates' is not installed, so not removed
Package 'nvidia-opencl-icd-361' is not installed, so not removed
Package 'nvidia-opencl-icd-361-updates' is not installed, so not removed
Package 'nvidia-persistenced' is not installed, so not removed
Package 'nvidia-profiler' is not installed, so not removed
Package 'nvidia-visual-profiler' is not installed, so not removed
The following packages were automatically installed and are no longer required:
  bbswitch-dkms libjansson4 libxnvctrl0 screen-resolution-extra
Use 'sudo apt autoremove' to remove them.
The following packages will be REMOVED:
  nvidia-352-dev* nvidia-361-dev* nvidia-367* nvidia-367-dev*
  nvidia-opencl-icd-367* nvidia-prime* nvidia-settings*
0 upgraded, 0 newly installed, 7 to remove and 0 not upgraded.
After this operation, 306 MB disk space will be freed.
N: Ignoring file '50unattended-upgrades.ucf-dist' in directory '/etc/apt/apt.conf.d/' as it has an invalid filename extension
N: Ignoring file '50unattended-upgrades.ucf-old' in directory '/etc/apt/apt.conf.d/' as it has an invalid filename extension
Do you want to continue? [Y/n] y
(Reading database ... 336622 files and directories currently installed.)
Removing nvidia-352-dev (361.45.11-0ubuntu0.16.04.1) ...
Failed to stop var-lib-snapd-lib-gl.mount: Unit var-lib-snapd-lib-gl.mount not loaded.
dpkg: error processing package nvidia-352-dev (--remove):
 subprocess installed pre-removal script returned error exit status 5
Failed to get unit file state for var-lib-snapd-lib-gl.mount: No such file or directory
var-lib-snapd-lib-gl.mount is a disabled or a static unit, not starting it.
Removing nvidia-prime (0.8.4) ...
dpkg: nvidia-367: dependency problems, but removing anyway as you requested:
 nvidia-367-dev depends on nvidia-367 (>= 367.57).

Removing nvidia-367 (367.57-0ubuntu3) ...
Removing all DKMS Modules
Done.
update-alternatives: using /usr/lib/nvidia-367-prime/ld.so.conf to provide /etc/ld.so.conf.d/x86_64-linux-gnu_GL.conf (x86_64-linux-gnu_gl_conf) in auto mode
update-alternatives: using /usr/lib/nvidia-367-prime/ld.so.conf to provide /etc/ld.so.conf.d/x86_64-linux-gnu_EGL.conf (x86_64-linux-gnu_egl_conf) in auto mode
update-alternatives: using /usr/lib/nvidia-367-prime/alt_ld.so.conf to provide /etc/ld.so.conf.d/i386-linux-gnu_GL.conf (i386-linux-gnu_gl_conf) in auto mode
update-alternatives: using /usr/lib/nvidia-367-prime/alt_ld.so.conf to provide /etc/ld.so.conf.d/i386-linux-gnu_EGL.conf (i386-linux-gnu_egl_conf) in auto mode
update-alternatives: using /usr/lib/x86_64-linux-gnu/mesa/ld.so.conf to provide /etc/ld.so.conf.d/x86_64-linux-gnu_GL.conf (x86_64-linux-gnu_gl_conf) in auto mode
update-alternatives: using /usr/lib/x86_64-linux-gnu/mesa-egl/ld.so.conf to provide /etc/ld.so.conf.d/x86_64-linux-gnu_EGL.conf (x86_64-linux-gnu_egl_conf) in auto mode
update-alternatives: using /usr/lib/i386-linux-gnu/mesa/ld.so.conf to provide /etc/ld.so.conf.d/i386-linux-gnu_GL.conf (i386-linux-gnu_gl_conf) in auto mode
update-alternatives: using /usr/lib/i386-linux-gnu/mesa-egl/ld.so.conf to provide /etc/ld.so.conf.d/i386-linux-gnu_EGL.conf (i386-linux-gnu_egl_conf) in auto mode
INFO:Disable nvidia-367
DEBUG:Parsing /usr/share/ubuntu-drivers-common/quirks/lenovo_thinkpad
DEBUG:Parsing /usr/share/ubuntu-drivers-common/quirks/put_your_quirks_here
DEBUG:Parsing /usr/share/ubuntu-drivers-common/quirks/dell_latitude
update-initramfs: deferring update (trigger activated)
dpkg: nvidia-361-dev: dependency problems, but removing anyway as you requested:
 nvidia-352-dev depends on nvidia-361-dev.

Removing nvidia-361-dev (367.57-0ubuntu3) ...
Removing nvidia-367-dev (367.57-0ubuntu3) ...
Errors were encountered while processing:
 nvidia-352-dev
E: Sub-process /usr/bin/dpkg returned an error code (1)


Here is the error code synaptic pops up after uninstalling nvidia-352-dev:

E: nvidia-352-dev: subprocess installed pre-removal script returned error exit status 5

---

### Post by vanquishedangel on 2016-10-18
Problem has been fixed, this is how it was able to be fixed: 

sudo mv /var/lib/dpkg/info/<packagename>.* /tmp/
sudo dpkg --remove --force-remove-reinstreq <packagename>
sudo apt-get remove <packagename>
sudo apt-get autoremove && sudo apt-get autoclean

Change <packagename> to nvidia-352-dev.



Found the answer here:
[http://askubuntu.com/questions/780384/unable-to-install-or-upgrade-after-an-upgrade-to-16-04-with-gcc-doc-error](http://askubuntu.com/questions/780384/unable-to-install-or-upgrade-after-an-upgrade-to-16-04-with-gcc-doc-error)

---

