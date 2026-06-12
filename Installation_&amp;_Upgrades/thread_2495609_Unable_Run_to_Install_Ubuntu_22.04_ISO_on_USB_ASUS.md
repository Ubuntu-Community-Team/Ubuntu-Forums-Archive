---
title: "Unable Run to Install Ubuntu 22.04 ISO on USB/ ASUS ROG NVIDIA RTX 3060"
date: 2024-02-24
forum: Installation &amp; Upgrades
---

### Post by jsaf on 2024-02-24
Hello,

I've tried some troubleshooters and AIs to get this right, but I need some human intelligence!

Again, I have ASUS ROG NVIDIA RTX 3060
I will outline the problem:
[LIST=1]
[*]I downloaded Rufus to generate a ISO USB boot installer of Ubuntu 22.04 Desktop and I the ISO from official Ubuntu webpage
[*]I used Rufus to write ISO with defaults so I can make a partition apart from Windows 11
[*]I tried running the bios by pressing F12, and I also accessed the boot priority and set the USB first before Windows.
[*]I selected "try or install Ubuntu"
[*]Then I get a black screen error and a log I photographed.
[/LIST]

I tried researching the log to no avail. Found some dated thing about CDs but I don't have a CD ROM. 
Here is a link to the log image: [https://www.screencast.com/t/XXD3YaCJeLu7](https://www.screencast.com/t/XXD3YaCJeLu7)
it generally states the device connections, the video, inputs, usb, but it gets t a part near the bottom third that goes wrong. It says "asus:probe of 0003:0B05:19B6:0003: ASUS input not registered"
asus: probe... failed with error -12
and it mentions some other inputs and write protect is off and no caching page found. 

What can I do? Please advise.

---

### Post by oldfred on 2024-02-24
Is this similar?
Asus ROG G14  Needed 22.04.4 & safe graphics
[https://ubuntuforums.org/showthread.php?t=2492628](https://ubuntuforums.org/showthread.php?t=2492628)

---

### Post by jsaf on 2024-02-24
I took a look at this post. I did some things like trying to reformat etc, change the USB port, and I tried it on another computer. The other computer could run the bootable USB just fine, in fact I am installing it there now, so that works. 

The first post is about a mac, so I don't find it that helpful and the user got further along than I did. It wont even start the Ubuntu/ROG loading screen to even do the first prompt, it seems a plain USB reading error to me, but I don't have a clue what to do. It looks like others tried disabling the UEFI, and I tried restarting by selecting the option for UEFI which reminds me of old windows BIOs. I changed some recommended settings and tried decrypting the laptop because I read there is an issue with making partitions while encrypted in some cases. 

I disabled fast boot, and removed energy saver option on USB to be sure it is on. I doubt I have tried everything but I am not familiar with these sorts of errors, as I usually just run the OS installer just fine.

There is definitely a unique issue with the ROG if the other laptop from Windows 11 can use it.

---

### Post by jsaf on 2024-02-24
Out of these steps I did:
**Summary UEFI install instructions:**
**1. Back up Windows, your data, and make a Windows repair/recovery flash drive**
[COLOR=#0000FF]**I got backup **[/COLOR]
**2. Download and create Ubuntu 64 bit installer, USB flash drive (new versions may not work with DVD).**
[COLOR=#0000FF]**Done, works.**[/COLOR]
**3. Only use Windows own Disk Management tools to shrink Windows & reboot so it can run chkd**
[COLOR=#0000ff][/COLOR][COLOR=#0000ff]I did shrink C: and reboot the PC, so is running chkd automatic or did I miss a step?[/COLOR]
**4. Turn off Windows fast startup & bitlocker in Windows.**
[B][COLOR=#0000ff]I turned off Windows fast boot in the BIOs, but I am not fnding fast startup directly in Windows. And I turned off bitlocker encrypt. [/COLOR]
5. In UEFI turn off fast boot (different than fast start up) and often better but not required to turn off Secure boot (may be called "other" vs. "Windows"), only some may need CSM mode on (older Dell), but still select UEFI. Usually best to have UEFI only as boot mode.[/B]
[B][COLOR=#0000ff]I turned off fast boot in UEFI. [/COLOR]
6. Some UEFI may need you to turn on or allow USB boot, especially if Secure boot is on
[COLOR=#0000ff]I will investigate this and I need to turn off secure boot[/COLOR][/B]
[B]7. Boot Ubuntu live installer in UEFI live mode, and verify your system works ok. How you boot installer UEFI or BIOS is how it installs.
[COLOR=#0000ff]I did boot it and set it as first priority over windows.[/COLOR][/B]
**8. Install Ubuntu. links to screen shots below Only / (root) as ext4 & ESP required. But may want others. Only one ESP per drive and installer will auto find it, if existing.**
**new versions will install proprietary nVidia driver if Safe Boot option & choose to install third-party software options are checked. If UEFI Secure Boot on, user must provide UEFI secure boot key.**
**If nVidia or AMD video may need nomodeset boot parameter. Some brands also may need other boot parameters.**
**Create backup procedure for your Ubuntu data and configuration files.**
[B]If Issue with install, more info needed, or terms not understood, see info & links below:

[COLOR=#0000ff]&#8203;[/COLOR]
[/B]

---

### Post by jsaf on 2024-02-24
I managed to it to install using the second option with safe graphics. Don't install it with "Try or Install Ubuntu" if you get this message because I tried everything and you still may need to disable things for the partition to work. But I am still getting a login error. I am not sure if it is trying to download packets from a mirror or what on my first login, but it's taking forever! I tried using 
Ctrl + Alt F2/F3/F4/F5/F6  (holding it down as you switch) and several other commands to try typing in what I read is the tty. However, I am not sure I got that to work either. I could write on a huge black screen but it didn't show you anything worked when you press enter, it's just a bunch of frozen lines of text. What can I do to get to the login?

---

### Post by oldfred on 2024-02-24
If you needed Safe Graphics, that would also say you need a proprietary driver.
During install is a checkbox to install optional restricted or proprietary drivers.

If you can boot recovery mode, or second line in grub menu to recovery mode menu, you can install the correct nVidia driver from Ubuntu repository.
Or if graphics do load in low quality mode you can use System settings & drivers tab.

Fast Boot is an UEFI setting. Needs to be off whenever making any system changes. But you can turn it back on once you are not making any changes.
Fast startup is a Windows hibernation setting that is the default mode of shutdown. Windows updates may turn it back on.

Fast Start up off (always on hibernation), note that Windows turns this back on with updates, SHIFT + Shut down button
[http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472](http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472)
[https://www.elevenforum.com/t/turn-on-or-off-fast-startup-in-windows-11.1212/](https://www.elevenforum.com/t/turn-on-or-off-fast-startup-in-windows-11.1212/)
[https://www.makeuseof.com/windows-11-turn-on-or-off-fast-startup/](https://www.makeuseof.com/windows-11-turn-on-or-off-fast-startup/)

---

### Post by jsaf on 2024-02-25
I did manage to fix the loin/booting but the NVIDIA driver seems to be behind the inability of a device. I could post that with hardware instead. I am not sure what the best NVIDIA device is for my laptop and the resources are quite vague on selecting why its of value or how its capable to run my devices. However, I am enjoying this installation. I have never used Ubuntu before, and it quite fun and very steady even with programs that are unstable on Windows.

---

### Post by oldfred on 2024-02-25
Ubuntu typically suggests which driver is best.
But if you have installed an incorrect one, you have to totally purge old one first or you get conflicts and then major graphics issues.

This will show if driver installed:
#What is installed
dkms status

# list drivers available, same list as system settings,  software updates,  additional drivers or last tab
ubuntu-drivers devices
# or
ubuntu-drivers devices | grep recommended 

Some older instructions have you add a ppa, that is not required anymore.
[https://ubuntuforums.org/showthread.php?t=2383560&p=13735336#post13735336](https://ubuntuforums.org/showthread.php?t=2383560&p=13735336#post13735336)

---

### Post by jsaf on 2024-02-25
How would I purge the whole NVIDIA driver and reinstall? The grep recommend was: Ddriver   : nvidia-driver-535 - distro non-free recommended.

---

### Post by oldfred on 2024-02-25
If you click on the link above, it shows the purge command.
If you have correct driver, no need to purge & reinstall.

Also here:
[https://askubuntu.com/questions/1478024/how-do-i-install-an-arbitrary-proprietary-nvidia-gpu-driver-on-ubuntu-studio-22](https://askubuntu.com/questions/1478024/how-do-i-install-an-arbitrary-proprietary-nvidia-gpu-driver-on-ubuntu-studio-22)

> sudo apt-get remove --purge nvidia-*
sudo ubuntu-drivers devices
If you just want default version - recommended one
sudo ubuntu-drivers autoinstall
Or you can manually choose any in list.
sudo apt-get install nvidia-XXX 

Some after a purge need this:
sudo apt update
sudo apt install linux-generic
sudo apt full-upgrade



---

### Post by jsaf on 2024-02-25
I found some thread that tells how to purge all of the NVIDIA, but it automatically installs the prior driver when doing so, and that one doesn't even load the login. It's the nvidia-535 default. But I went to NVIDIA to manually install .run driver for linux. I was able to get that to run but the NVIDIA driver isn't working. It could not install the kernal. I have a log file I saved to this post if that helps. DeepSeek Coder said, "The error message you're seeing indicates that there's a mismatch  between the compiler used to compile the kernel and the compiler used to  compile the NVIDIA driver. This can cause issues during the  installation process." The kernal wasn't successfully built.

I don't know what that means except I have no driver but a default. 

So trying the software app isn't working and the alternative drivers. They don't pick one suited for the card or have it on the list as there's no match with NVIDIA's actual driver resource: 
[https://www.nvidia.com/Download/index.aspx?lang=en-us](https://www.nvidia.com/Download/index.aspx?lang=en-us)

I downloaded the recommended: NVIDIA-Linux-x86_64-550.54.14.run

I tried keeping the common driver using a regex from DeepSeek while purging all the other packages. But the automatic installer kicks in: sudo apt-get remove --purge $(dpkg -l | grep '^ii' | grep -v '^ii  nvidia-common' | awk '{print $2}' | grep '^nvidia-')

---

### Post by jsaf on 2024-02-25
I went to NVIDIA to download a driver by selecting my card for linux64: [https://www.nvidia.com/Download/index.aspx?lang=en-us](https://www.nvidia.com/Download/index.aspx?lang=en-us)
I got NVIDIA-Linux-x86_64-550.54.14.run

I used the purge commands before you responded, thanks also for that! And then I tried installing using the .run file I downloaded and did the default Ubuntu installation command, but that made the original problem occur where Ubuntu login was frozen in a state. So I tried removing that, currently I don't have a proper driver. In addition when using the .run driver directly from NVIDIA the kernal build failed. I included a log attachment. 

I will continue browsing your threads. I appreciate your work helping me further.

---

### Post by jsaf on 2024-02-25
I made an advanced reply for you that includes logs, sorry if there's a duplicate, I hadn't realized how to find those associated with the thread. I will look at this.

---

### Post by oldfred on 2024-02-25
Did you miss that you should install the nVidia driver from the Ubuntu repository, not directly from nVidia.
I do not know how to uninstall a .run file. But it should have instructions on how to do that.

With the .run version, you have to, in effect, reinstall it with every kernel update as the update does not then work to incorporate the nVidia driver.
With the Ubuntu version, it just works.

---

### Post by jsaf on 2024-02-25
I did try those steps actually, I used each command in the list, tried the repositories and it had no benefit for my tablet drawing device. 

I currently have a basic nVidia driver working, and it's from the Ubuntu repo because the driver from NVIDIA .run didn't work. I am not sure what to do about the drawing tablet's interface with this version of nVidia. On Windows I had a similar problem, where it only connected to the screen by extending without any keys, but I found a firmware updating package and it worked fine. It makes me think that the nVidia driver may not be the whole issue anymore. I would prefer to use the drawing tablet on Linux because the software is smoother. 

These are my current driver packages:
jsafr@jsafr-ROG-Zephyrus-M16-GU603HM-GU603HM:~/Desktop$  dpkg -l | grep -i nvidia
ii  libnvidia-cfg1-545:amd64                         545.29.06-0ubuntu0.22.04.2              amd64        NVIDIA binary OpenGL/GLX configuration library
ii  libnvidia-common-545                             545.29.06-0ubuntu0.22.04.2              all          Shared files used by the NVIDIA libraries
rc  libnvidia-compute-525-server:amd64               525.147.05-0ubuntu0.22.04.1             amd64        NVIDIA libcompute package
rc  libnvidia-compute-535:amd64                      535.154.05-0ubuntu0.22.04.1             amd64        NVIDIA libcompute package
rc  libnvidia-compute-535-server:amd64               535.154.05-0ubuntu0.22.04.1             amd64        NVIDIA libcompute package
ii  libnvidia-compute-545:amd64                      545.29.06-0ubuntu0.22.04.2              amd64        NVIDIA libcompute package
ii  libnvidia-compute-545:i386                       545.29.06-0ubuntu0.22.04.2              i386         NVIDIA libcompute package
ii  libnvidia-decode-545:amd64                       545.29.06-0ubuntu0.22.04.2              amd64        NVIDIA Video Decoding runtime libraries
ii  libnvidia-decode-545:i386                        545.29.06-0ubuntu0.22.04.2              i386         NVIDIA Video Decoding runtime libraries
ii  libnvidia-encode-545:amd64                       545.29.06-0ubuntu0.22.04.2              amd64        NVENC Video Encoding runtime library
ii  libnvidia-encode-545:i386                        545.29.06-0ubuntu0.22.04.2              i386         NVENC Video Encoding runtime library
ii  libnvidia-extra-545:amd64                        545.29.06-0ubuntu0.22.04.2              amd64        Extra libraries for the NVIDIA driver
ii  libnvidia-fbc1-545:amd64                         545.29.06-0ubuntu0.22.04.2              amd64        NVIDIA OpenGL-based Framebuffer Capture runtime library
ii  libnvidia-fbc1-545:i386                          545.29.06-0ubuntu0.22.04.2              i386         NVIDIA OpenGL-based Framebuffer Capture runtime library
ii  libnvidia-gl-545:amd64                           545.29.06-0ubuntu0.22.04.2              amd64        NVIDIA OpenGL/GLX/EGL/GLES GLVND libraries and Vulkan ICD
ii  libnvidia-gl-545:i386                            545.29.06-0ubuntu0.22.04.2              i386         NVIDIA OpenGL/GLX/EGL/GLES GLVND libraries and Vulkan ICD
ii  libnvidia-nscq-525                               525.147.05-0ubuntu0.22.04.1             amd64        NVSwitch Configuration and Query library
rc  linux-modules-nvidia-525-server-6.5.0-21-generic 6.5.0-21.21~22.04.1                     amd64        Linux kernel nvidia modules for version 6.5.0-21
ii  linux-objects-nvidia-525-server-6.5.0-21-generic 6.5.0-21.21~22.04.1                     amd64        Linux kernel nvidia modules for version 6.5.0-21 (objects)
ii  linux-objects-nvidia-535-6.5.0-21-generic        6.5.0-21.21~22.04.1                     amd64        Linux kernel nvidia modules for version 6.5.0-21 (objects)
ii  linux-signatures-nvidia-6.5.0-21-generic         6.5.0-21.21~22.04.1                     amd64        Linux kernel signatures for nvidia modules for version 6.5.0-21-generic
ii  nvidia-compute-utils-545                         545.29.06-0ubuntu0.22.04.2              amd64        NVIDIA compute utilities
ii  nvidia-dkms-545                                  545.29.06-0ubuntu0.22.04.2              amd64        NVIDIA DKMS package
ii  nvidia-driver-545                                545.29.06-0ubuntu0.22.04.2              amd64        NVIDIA driver metapackage
ii  nvidia-firmware-545-545.29.06                    545.29.06-0ubuntu0.22.04.2              amd64        Firmware files used by the kernel module
ii  nvidia-kernel-common-545                         545.29.06-0ubuntu0.22.04.2              amd64        Shared files used with the kernel module
ii  nvidia-kernel-source-545                         545.29.06-0ubuntu0.22.04.2              amd64        NVIDIA kernel source package
ii  nvidia-prime                                     0.8.17.1                                all          Tools to enable NVIDIA's Prime
ii  nvidia-settings                                  510.47.03-0ubuntu1                      amd64        Tool for configuring the NVIDIA graphics driver
ii  nvidia-utils-545                                 545.29.06-0ubuntu0.22.04.2              amd64        NVIDIA driver support binaries
ii  screen-resolution-extra                          0.18.2                                  all          Extension for the nvidia-settings control panel
ii  xserver-xorg-video-nvidia-545                    545.29.06-0ubuntu0.22.04.2              amd64        NVIDIA binary Xorg driver


I may need to have a word with the Huion tablet co.

---

### Post by jsaf on 2024-02-25
Wow, the firmware update for Windows 11 on Huion crossed over to the nVidia control on Linux. All problems were solved, the nVidia starts the OS/login, the tablet draws because of the firmware package on the other dual boot side. Thanks for your help MasterRoaster!

---

