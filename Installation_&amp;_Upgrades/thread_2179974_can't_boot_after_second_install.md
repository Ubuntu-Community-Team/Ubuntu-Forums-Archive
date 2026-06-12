---
title: "can't boot after second install"
date: 2013-10-10
forum: Installation &amp; Upgrades
---

### Post by ersatzsplatt on 2013-10-10
I have installed 12.04.3 LTS 64 bit desktop.
I wanted/needed to install 32 bit desktop of the same release, so I chose the button to install alongside the existing installation.
When I reboot after install, I can not boot into the 64 bit install anymore

After running the system for a bit, updating some packages and rebooting, the new (32 bit install will not boot either).  The symptoms look the same.  I end up with a small underscore at the upper left hand corner of the screen.  No response to the keyboard that I can find at that point.  ... except ctrl-alt-del (which operates as it should, rebooting the system).

The boot starts with a grub prompts screen offering the newest install and the older (64 bit install).  IF I SELECT RECOVERY MODE, AND THEN SELECT "RESUME NORMAL BOOT", THE SYSTEM WILL BOOT TO A TEXT LOGIN SCREEN.

I have spent a lot of time though getting things installed on my graphical environment.  Yes, the text login will show me my system name and mounts everything for that install (that I am aware of).  The text install also gives me virtual terminals.  Alt-F7 shows me a last line of "Saved ALSA miser settings detected; aumix will not touch mixer. [...]"  Not really a clean indication of what is going on.

It seems like maybe a grub issue, but update-grub does not fix it. (or change anything)

I am very tired of reinstalling my system again and again.

When trying to do the "normal" boot, I see the grub screen, large blinking underscore cursor, some text, Ubuntu graphical screen (as I did when the boot was all going well -- I think this called the splash screen), then it goes to the small underscore which does not blink.


I really would like to be able to use my system.  The boss is not happy about my loss of productivity.

Please help soon.

---

### Post by heir4c on 2013-10-10
Can you log in in the Black screen with the 'prompt' (text login screen)? If so, than log in and type than: startx
Start it on to the desktop?

---

### Post by ersatzsplatt on 2013-10-14
When I type startx, it fails out.  Looking at the log file (/var/log/Xorg.0.log) I see some EE lines:


Failed to load module "intel" (module does not exist, 0)
Failed to load module "vesa" (module does not exist, 0)
Failed to load module "fbdev" (module does not exist, 0)
No drivers available


Toward the top I also see some warnings about some "/usr/share/fonts/X11/"... stuff that "does not exist"

... not sure how to fix this or why it went sour when it was working before.

---

### Post by oldfred on 2013-10-14
Does the 64 bit version still boot?
What video card/chip do you have? And did you install drivers for that chip in your 64 bit insall?

You often need nomodeset to get into low quality video to install proprietary drivers if nVidia or AMD. Press e for edit on grub menu entry and scroll down to linux line, replace quiet splash with nomodeset. I think recovery mode has nomodeset as a default already.

 How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

If you can boot into 64 bit version or command line.

 #To see video:
sudo lshw -c display
sudo lshw | grep -A 11 display
lspci | grep VGA
#Resolution:
xwininfo -root

---

### Post by ersatzsplatt on 2013-10-14
The 64 bit version still boots similarly.  Which is to say, trying to boot directly to the "normal" 64-bit boot option fails out.  Trying to boot with nomodeset DOES work, resulting in a functioning command line login with print at the login saying "mountall: Plymouth command failed" and "mountall: Disconnected from Plymouth"

A key reason I put this in the upgrades and installs section is that the 64-bit install worked great ... until I installed the 32-bit version next to it.  Then the graphical environment dropped out -- would not boot normally into the graphical environment.  I don't know why installing the 32-bit version should break the 64-bit working install ... seems like it shouldn't.

The other key reason is that the 32-bit install seemed to fail as a result of some kind of upgrade or install of an application.

It has an nvidia GeForce and an Intel GPU.  I have installed bumblebee on both the 64-bit and 32-bit installs.

I also have an external drive with the "same" 32-bit install and bumblebee -- the graphical boot/environment works for that.  I can use that for reference ... but I would like to find out why my environment gets corrupted during what I believe is normal use.  I'm a bit worried that my other install will get corrupted too and I will have to keep reinstalling (which I'd like to think everyone would agree is not the preferred working environment).

I've installed bumblebee because no other method that I could find would allow me to use a graphical environment on 12.04 given the system's "optimus" chip.

I now have what looks like a good graphical environment boot after some help from the good people at the bumblebee IRC (thanks corollax).  To get the 32-bit to boot, we looked at the errors I was seeing:
[COLOR=#000000]Failed to load module "intel" (module does not exist, 0)[/COLOR]
[COLOR=#000000]Failed to load module "vesa" (module does not exist, 0)[/COLOR]
[COLOR=#000000]Failed to load module "fbdev" (module does not exist, 0)[/COLOR]
[COLOR=#000000]No drivers available
[/COLOR][COLOR=#000000]
[/COLOR] then installed the packages which addressed the deficiency:

[COLOR=#000000][FONT=Consolas]xserver [/FONT][/COLOR]package seemed to address the intel driver issue.  That still did not fix all the issues.
[COLOR=#000000][FONT=Consolas]sudo apt-get install xserver-xorg-video-all [/FONT][/COLOR]fixed the vesa and fbdev module does not exist issues.

Now I am able to boot to a graphical login screen for the 32-bit install.  BUT THE LOGIN FAILS EACH TIME I TYPE THE PASSWORD IN.  This is not me typing the wrong password in because it fails every time and I can interleave logins to the virtual terminal (successfully).

I have a string of lines in the Xorg.0.log file that say:
(EE) FBDEV(0): FBIOPUTCMAP: Invalid argument
My key questions now are:
1.)  What do I need to do to be able to log into my graphical environment?
2.)  What caused the corruption of my system so that graphics failed out so badly?

---

### Post by oldfred on 2013-10-14
Can you set which video you boot with in UEFI/BIOS? Or does it auto switch?
You may need Intel boot settings, not nVidia nomodeset.

 Force Intel Video mode as boot parameter in grub menu - change to your screen size
video=1280x1024-24@60
and if that doesn't work you can try
video=VGA-1:1280x1024-24@60
 i915.i915_enable_rc6=1

   Asus i3 with Intel graphics, 
acpi_osi=Linux
video=1280x1024-24@75 or whatever native resolution is

   Some other boot options
acpi_osi=Linux  acpi_backlight=vendor

   For Intel graphics running slow:
sudo apt-get install mesa-utils
glxinfo | grep OpenGL | head -n3



       New Intel driver installer (only with 13.04)
[http://www.phoronix.com/scan.php?page=news_item&px=MTQyNTQ](http://www.phoronix.com/scan.php?page=news_item&px=MTQyNTQ)
Intel "Haswell" System 76 Iris Pro Linux Graphics Yield Some Wins Against Windows
[http://www.phoronix.com/scan.php?page=article&item=intel_irispro_linwin&num=1](http://www.phoronix.com/scan.php?page=article&item=intel_irispro_linwin&num=1)
NVIDIA's Linux Driver On Ubuntu Is Very Competitive With Windows 8
[http://www.phoronix.com/scan.php?page=article&item=nvidia_windows8_geforce&num=1](http://www.phoronix.com/scan.php?page=article&item=nvidia_windows8_geforce&num=1)
Linux 3.2 To 3.8 Kernels With Intel Ivy Bridge Graphics
[http://www.phoronix.com/scan.php?page=article&item=intel_linux32_38&num=1](http://www.phoronix.com/scan.php?page=article&item=intel_linux32_38&num=1)

If this is a high performance new system, why 32 bit? It greatly limits your system.
      
 Linus does not like PAE or 32 bit.
[http://cl4ssic4l.wordpress.com/2011/05/24/linus-torvalds-about-pae/](http://cl4ssic4l.wordpress.com/2011/05/24/linus-torvalds-about-pae/)

 32-bit vs. 64-bit Ubuntu 13.04 Linux Performance with only 1GB of RAM & most tests better with 64bit Mac Mini
[http://www.phoronix.com/scan.php?page=article&item=ubuntu_x86_1304&num=1](http://www.phoronix.com/scan.php?page=article&item=ubuntu_x86_1304&num=1)
Ubuntu 12.10: 32-bit vs. 64-bit Linux Performance
[http://www.phoronix.com/scan.php?page=article&item=ubuntu_1210_3264&num=1](http://www.phoronix.com/scan.php?page=article&item=ubuntu_1210_3264&num=1)
Assuming your hardware is x86_64 capable (basically any modern Intel/AMD CPU) and have at least 2GB of RAM, you really should be running the 64-bit version.
Essentially says if you can use the 64bit kernel you should.April 2011
[http://www.phoronix.com/scan.php?page=article&item=ubuntu_natty_pae64&num=1](http://www.phoronix.com/scan.php?page=article&item=ubuntu_natty_pae64&num=1)
[https://help.ubuntu.com/community/32bit_and_64bit](https://help.ubuntu.com/community/32bit_and_64bit)

---

### Post by ersatzsplatt on 2013-10-14
Thanks for the reply oldfred.

BIOS does not give me any control over the GPU used.

It seems like the video is sort of working now (see my last reply) ... but the graphical environment denies my login attempts.  Do you suggest that messing with the drivers is going to get the system to let me log in?  I'll surely try anything that you think will help me with that.

My work requires I use 12.04.  I cannot use 13.04.

I am not married to exclusive 32-bit use.  There are 32 bit systems that I also use though, and there may be some use in my having consistent system environments.  Recall that I installed 64-
bit first -- I intended to install 32-bit as an alternative, but after the 32-bit install 64-bit would no longer boot.

At this point, I still have the same 2 questions:
[COLOR=#000000]1.) What do I need to do to be able to log into my graphical environment?[/COLOR]
[COLOR=#000000]2.) What caused the corruption of my system so that graphics failed out so badly?
[/COLOR]

---

### Post by oldfred on 2013-10-14
Is system UEFI or BIOS. the 32 bit version will not install in UEFI mode.
Is this a Haswell or new 4th gen Intel chip? They seem to need the kernel & driver updates in beta 13.10.

I do not see how 32 bit could interfere with 64 bit unless related to UEFI as how UEFI starts to boot is how it must continue to boot. So booting in 32 bit may create issues? But 32 bit only has BIOS based install.

---

### Post by ersatzsplatt on 2013-10-15
here is what I see x8 cores (as indicated by cpuinfo)

vendor_id	: GenuineIntel
cpu family	: 6
model		: 60
model name	: Intel(R) Core(TM) i7-4800MQ CPU @ 2.70GHz
stepping	: 3
microcode	: 0x7
cpu MHz		: 800.000
cache size	: 6144 KB
physical id	: 0
siblings	: 8
core id		: 3
cpu cores	: 4
apicid		: 7
initial apicid	: 7
fdiv_bug	: no
hlt_bug		: no
f00f_bug	: no
coma_bug	: no
fpu		: yes
fpu_exception	: yes
cpuid level	: 13
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx pdpe1gb rdtscp lm constant_tsc arch_perfmon pebs bts xtopology nonstop_tsc aperfmperf eagerfpu pni pclmulqdq dtes64 monitor ds_cpl vmx smx est tm2 ssse3 fma cx16 xtpr pdcm pcid sse4_1 sse4_2 x2apic movbe popcnt tsc_deadline_timer aes xsave avx f16c rdrand lahf_lm abm ida arat epb xsaveopt pln pts dtherm tpr_shadow vnmi flexpriority ept vpid fsgsbase tsc_adjust bmi1 hle avx2 smep bmi2 erms invpcid rtm
bogomips	: 5387.88
clflush size	: 64
cache_alignment	: 64
address sizes	: 39 bits physical, 48 bits virtual
power management:

I'm not sure what generation that makes the cpu.

I have to use 12.04.

I fixed the login issue by following these steps:

sudo apt-get update
sudo apt-get -d install --reinstall gdm
sudo apt-get remove --purge gdm
sudo apt-get install gdm
per [http://askubuntu.com/questions/136821/ubuntu-12-04-forced-into-low-graphics-mode-server-is-already-active-for-displa](http://askubuntu.com/questions/136821/ubuntu-12-04-forced-into-low-graphics-mode-server-is-already-active-for-displa)

I think lightdm started to come back somehow.  I had to go to gdm instead of lightdm for graphics to work after initial install (geforce issue I guess).  The reinstall outlined above seems to correct some lightdm contention.

---

### Post by oldfred on 2013-10-15
I thought all new i-series with -4xxx were Haswell.  So best to use newest kernel and Ubuntu version.
Previous generation were all -3xxxx - Ivy Bridge and before that Sandy Bridge
[http://www.intel.com/content/www/us/en/processors/processor-numbers.html](http://www.intel.com/content/www/us/en/processors/processor-numbers.html)

 Intel Haswell - Linux support June 2013
[http://www.phoronix.com/scan.php?page=news_item&px=MTM5MzU](http://www.phoronix.com/scan.php?page=news_item&px=MTM5MzU)

---

