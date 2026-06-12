---
title: "Cannot install NVIDIA 195.x drivers - installer crashes"
date: 2010-03-16
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by doctordruidphd on 2010-03-16
I cannot install any of the NVIDIA 195.xx, including the most recent 195.36.15, drivers. After stopping kdm (or gdm, depending on which system I'm using), and running "sudo sh ./NV-whatever-pkg2", the installer builds the kernel module, and then hangs at the "Install NVIDIA's 32-bit compatibility OpwenGL libraries?" screen.  And it's a real hang -- requires a hard power down to get out of it. The nvidia-installer.log file is empty.

This also means I cannot install the "nvidia-current" package from the ppa. It quits and does not install the driver.

Thanks for any assistance.


Yeah, I would love to post this to the NVIDIA forum, but they won't let me register because I have a Yahoo (and only a Yahoo) email address. I did search there and cannot find any similar posts.

This system is:
Dell XPS630 Intel Q9550 quad (amd_64)
8gb ram
dual 9800 GT video cards

The 190 drivers do install and run fine. Also, the 195's install and run fine on karmic.

---

### Post by yedidyah on 2010-03-16
I am using:
64 Bit
Lucid Lynx
kernel 2.6.32-16-generic
had same problem with 2.6.32-14-generic
I was working with someone at launchpad who said the problem would be fixed in the next kernel (15) and the
problem was fixed in 2.6.32-15-generic
nVidia 9800 graphics card
driver:
NVIDIA-Linux-x86_64-190.53-pkg2.run

THE PROCESS

Start computer

> Ubuntu is running in low-graphics mode

> The following error was encountered. You may need to update your configuration to solve this.
(EE) NVIDIA: Failed to load the NVIDIA kernel module.
Please check your
(EE) NVIDIA: system's kernel log for additional error messages.
(EE) Failed to load module &#8220;nvidia&#8221; (module-specific error, 0)
(EE) No drivers available.

Click OK

> What would you like to do?
Run Ubuntu in low-graphics mode for just one session
Reconfigure graphics
Troubleshoot the error
Exit to console login
Restart X 

Click the radio button for &#8220;Exit to console login&#8221;

login
password

cd Downloads

sudo sh ./NVIDIA-Linux-x86_64-190.53-pkg2.run

password

accept license agreement

Yes to uninstall existing NVIDIA driver 190.53

> The distribution-provided pre-install script failed! Continue installation anyway?

(new to 10.04 but I have several times successfully installed driver in the past even with this strange error)

select Yes

looks like driver is installing to 100%

THEN

> ERROR: Unable to load the kernel module 'nvidia.ko'. This happens most frequently when this kernel module was built against the wrong or improperly configured kernel sources, with a version of gcc that differs from the one used to build the target kernel, or if a driver such as rivafb/nvidiafb is present and prevents the NVIDIA kernel module from obtaining ownership of the NVIDIA graphics device(s), or NVIDIA GPU installed in this system is not supported by this NVIDIA Linux graphics driver release.

Please see the log entries 'Kernel module load error' and 'Kernel messages' at the end of the file '/var/log/nvidia-installer.log' for more information.



> ERROR: Installation failed. Please see the file '/var/log/nvidia-installer.log' for details. You may find suggestions on fixing installation problems in the README available on the linux driver download page at [www.nvidia.com](www.nvidia.com)


FROM THE END OF FILE /var/log/nvidia-installer.log

> -> Kernel module load error: insmod: error inserting './usr/src/nv/nvidia.ko':

   -1 No such device

-> Kernel messages:

   [   10.442148] vboxnetflt: Unknown symbol RTSemEventCreate

   [   10.442216] vboxnetflt: no symbol version for RTSpinlockAcquire

   [   10.442218] vboxnetflt: Unknown symbol RTSpinlockAcquire

   [   10.442287] vboxnetflt: no symbol version for RTLogLoggerEx

   [   10.442288] vboxnetflt: Unknown symbol RTLogLoggerEx

   [   10.442392] vboxnetflt: no symbol version for RTR0Term

   [   10.442393] vboxnetflt: Unknown symbol RTR0Term

   [   10.442543] vboxnetflt: no symbol version for RTUuidCompareStr

   [   10.442544] vboxnetflt: Unknown symbol RTUuidCompareStr

   [   10.442670] vboxnetflt: no symbol version for RTSemFastMutexDestroy

   [   10.442671] vboxnetflt: Unknown symbol RTSemFastMutexDestroy

   [   10.559474] ppdev: user-space parallel port driver

   [   19.560014] eth0: no IPv6 routers present

   [   71.520023] Clocksource tsc unstable (delta = -266738184 ns)

   [  190.532782] usb 1-5: USB disconnect, address 3

   [  654.592258] nvidia: module license 'NVIDIA' taints kernel.

   [  654.592262] Disabling lock debugging due to kernel taint

   [  655.116105] NVRM: The NVIDIA probe routine was not called for 1

   device(s).

   [  655.116108] NVRM: This can occur when a driver such as rivafb, nvidiafb

   or

   [  655.116110] NVRM: rivatv was loaded and obtained ownership of the NVIDIA

   [  655.116111] NVRM: device(s).

   [  655.116113] NVRM: Try unloading the rivafb, nvidiafb or rivatv kernel

   module

   [  655.116114] NVRM: (and/or reconfigure your kernel without rivafb/nvidiafb

   [  655.116115] NVRM: support), then try loading the NVIDIA kernel module

   again.

   [  655.116117] NVRM: No NVIDIA graphics adapter probed!

ERROR: Installation has failed.  Please see the file

       '/var/log/nvidia-installer.log' for details.  You may find suggestions

       on fixing installation problems in the README available on the Linux

       driver download page at [www.nvidia.com](www.nvidia.com).

---

### Post by Half-Left on 2010-03-16
Can you post the readout of ```
lsmod
``` from the terminal?

---

### Post by cariboo on 2010-03-16
If you don't use the drivers from the repositories, you will have to re-install the Nvidia driver every time there is a new kernel.

I'm not going look for it, but there is a thread in this sub-forum stating that the Nvidia driver will not work with the current kernel, either use the nouveau driver, or the driver from the repositories.

---

### Post by cariboo on 2010-03-16
From the [Release Notes]("http://www.ubuntu.com/testing/lucid/alpha2"):

> Because of the new alternatives system, the nvidia installer from NVIDIA's website currently doesn't work.

**Edit** I found another thread with the same problem, merged the two threads and added info

---

### Post by doctordruidphd on 2010-03-16
> Because of the new alternatives system, the nvidia installer from NVIDIA's website currently doesn't work. 

I'm not really sure what this means. Neither the version from the NVIDIA website, NOR the version in 'nvidia-current' in the repository, will successfully install. This is kernel version 2.6.32-16-generic.

The 190.xx drivers do install fine. Whether this is a different installer program or not, I don't know.

> ERROR: Unable to load the kernel module 'nvidia.ko'. This happens most frequently when this kernel module was built against the wrong or improperly configured kernel sources, with a version of gcc that differs from the one used to build the target kernel, or if a driver such as rivafb/nvidiafb is present and prevents the NVIDIA kernel module from obtaining ownership of the NVIDIA graphics device(s), or NVIDIA GPU installed in this system is not supported by this NVIDIA Linux graphics driver release.
You get this message if you have booted without the 'nomodeset' kernel option, and the nouveau driver has loaded. The reason for it is that the nouveau driver takes control of the NVIDIA hardware, and the nvidia.ko module can't communicate with the hardware once the nouveau driver is loaded. Try booting with the 'nomodeset' kernel option and then installing.

---

### Post by Regenweald on 2010-03-16
-16 Is not working for me also with the nvidia binary but my architecture is 64bit. I simply boot -15. Also, nouveau is not on my system.

---

### Post by Half-Left on 2010-03-16
> **doctordruidphd said:**
> I'm not really sure what this means. Neither the version from the NVIDIA website, NOR the version in 'nvidia-current' in the repository, will successfully install. This is kernel version 2.6.32-16-generic.

The 190.xx drivers do install fine. Whether this is a different installer program or not, I don't know.


You get this message if you have booted without the 'nomodeset' kernel option, and the nouveau driver has loaded. The reason for it is that the nouveau driver takes control of the NVIDIA hardware, and the nvidia.ko module can't communicate with the hardware once the nouveau driver is loaded. Try booting with the 'nomodeset' kernel option and then installing.

Hence why you have to blacklist the nouveau module when manually compiling the NVIDIA driver or sudo rmmod nouveau. check lsmod and find out.

---

### Post by yedidyah on 2010-03-16
> **Half-Left said:**
> Can you post the readout of ```
lsmod
``` from the terminal?

Module                  Size  Used by
binfmt_misc             7960  1 
ppdev                   6375  0 
vboxdrv              1768023  0 
fbcon                  39270  72 
tileblit                2487  1 fbcon
font                    8053  1 fbcon
bitblit                 5779  1 fbcon
softcursor              1565  1 bitblit
vga16fb                12693  0 
vgastate                9857  1 vga16fb
snd_hda_codec_realtek   278794  1 
snd_hda_intel          25453  2 
snd_hda_codec          85855  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               6924  1 snd_hda_codec
snd_pcm_oss            41362  0 
snd_mixer_oss          16267  1 snd_pcm_oss
snd_pcm                87978  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           1782  0 
snd_seq_oss            31187  0 
snd_seq_midi            5829  0 
snd_rawmidi            23388  1 snd_seq_midi
snd_seq_midi_event      7267  2 snd_seq_oss,snd_seq_midi
snd_seq                57417  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              23521  2 snd_pcm,snd_seq
snd_seq_device          6824  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
nouveau               514275  3 
ttm                    60847  1 nouveau
snd                    71010  16 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
drm_kms_helper         30742  1 nouveau
lp                      9336  0 
edac_core              45455  0 
k8temp                  3912  0 
edac_mce_amd            9182  0 
soundcore               8052  1 snd
snd_page_alloc          8660  2 snd_hda_intel,snd_pcm
i2c_piix4               9639  0 
drm                   198930  3 nouveau,ttm,drm_kms_helper
i2c_algo_bit            6024  1 nouveau
parport                37160  2 ppdev,lp
usbhid                 40860  0 
hid                    83312  1 usbhid
floppy                 63156  0 
r8169                  40002  0 
mii                     5205  1 r8169

---

### Post by Half-Left on 2010-03-16
> nouveau 514275 3
ttm 60847 1 nouveau

That is why the NVIDIA installer is saying what it's saying,since it thinks the nouveau module is some framebuffer module that it doesn't like.

---

### Post by doctordruidphd on 2010-03-16
> Hence why you have to blacklist the nouveau module when manually compiling the NVIDIA driver or sudo rmmod nouveau. check lsmod and find out.

Yes, you are right, in that if nouveau is loaded, NVIDIA will not install. However, it is possible to use both nouveau and nvidia, IFF one boots with the 'nomodeset' option and an appropriate xorg.conf for the nvidia driver, or booting without the 'nomodeset' option and an appropriate xorg.conf for the nouveau driver. That is what I am doing. The NVIDIA 190.xx drivers install and work properly in this configuration. The 195.xx drivers will not install. I am having a DIFFERENT problem than yedidyah is having. 
If I boot the wrong way -- without the 'nomodeset' option, and try to install the NVIDIA driver, I get the same problem as yedidyah when trying to install. I expect that, because it is a known issue that both drivers cannot be loaded at the same time. That goes for both the 190.xx and 195.xx drivers.

This is a different problem. It occurs even if I remove all traces of nouveau, by removing the nouveau packages, doing a hunt-and-kill on nouveau files, and rebuilding the initramfs. And it occurs only with the 195 drivers, not with the 190.

This is a 64-bit system.

I will give the rmmod a try.

---

### Post by yedidyah on 2010-03-16
"I am having a DIFFERENT problem than yedidyah is having."

I am sorry doctordruidphd I was not the one who brought my initial question into your thread someone else did it.

I want to apply your instructions to my system (although it is something the developers should get worked out before the final release of lucid because end users are not going to want to have to figure all this out) but I do not know how to boot to the nomodeset.

Please let me know.
Thank you.

---

### Post by doctordruidphd on 2010-03-16
> I am sorry doctordruidphd I was not the one who brought my initial question into your thread someone else did it.

Sorry, no flame intended, we are all trying to get help here.  I just wanted to make clear that the problem I am having is a different one.

What you need to try is booting with the 'nomodeset' kernel option, and see if you can get the NVIDIA driver to install that way. I can get the 190's, but not the 195's, to install using that procedure. To use the nomodeset option, when the grub menu comes up, highlight the entry you want to boot and hit **e** . Look for the line that starts with **kernel** . Move to the end of that line. If there is a **splash** entry, erase it. Now add to the end of that line the word **nomodeset** .  Hit CTRL-X to boot. You should find yourself either at a text console, or else at the 'low graphics mode' screens. Best thing to do is go directly to a text console, then stop x using **sudo service gdm stop**, and then install your NVIDIA driver. Once the driver installs, you should be able to **sudo service gdm start** and get into your system.

On my system, I am using both nouveau and nvidia, so I have separate xorg.conf files, one for each (xorg.conf-nouveau and xorg.conf-nvidia). I have to remember to copy the right one to xorg.conf before rebooting. This is a real hassle, and hopefully will be worked out eventually.

Yes, this does need to get worked out. The nouveau driver works, and using the xrender compositing option, does give some screen effects. But those of us who insist on playing games really need the full 3d acceleration, and that requires the proprietary driver. It is possible to have both, though you need a different xorg.conf file for each, and you have to boot either with or without the 'nomodeset' option to make it work. 

I could not get the 195 drivers to install on my system, even before I put the nouveau stuff on. So I think there is some deeper problem. I did find an email for nvidia tech support, and they are trying to help work through this. So I hope a solution is possible.

I did try sudo rmmod nouveau and lbm-nouveau; this did not help. As I said, since this problem existed before the nouveau stuff was installed, I don't think it's the same problem as the nouveau hardware conflict problem.

---

### Post by yedidyah on 2010-03-16
Thank you for the solution. I am sorry that you haven't got the 195 to work. I wish I could help.

---

### Post by Skerit on 2010-03-21
I'm having the same problem, I can't start the nvidia driver.
I also tried adding the "nomodeset" option to the grub.cfg file, but I believe it ignores it. Ubuntu still starts in fill kms glory.

On my pc, after activating the restricteddrivers, ubuntu also installed a few different versions of the nvidia-packages.

I created a bug report, just in case:
[https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers/+bug/543079](https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers/+bug/543079)

---

### Post by plun on 2010-03-21
Maybe Fedoras sticky guide can be used  ???

[http://forums.fedoraforum.org/showthread.php?t=204752](http://forums.fedoraforum.org/showthread.php?t=204752)

**If Nouveau refuses to die...**

[CODE]su
yum erase xorg-x11-drv-nouveau
mv  /lib/modules/$(uname -r)/kernel/drivers/gpu/drm/nouveau/nouveau.ko /lib/modules/$(uname -r)/kernel/drivers/gpu/drm/nouveau/nouveau.txt
mv /boot/initramfs-$(uname -r).img /boot/initramfs-$(uname -r)-nouveau.img
dracut /boot/initramfs-$(uname -r).img $(uname -r)/CODE]

Translated to Ubuntu.....  ??

---

### Post by doctordruidphd on 2010-03-21
> I'm having the same problem, I can't start the nvidia driver.

Have you set up your xorg.conf for the nvidia driver? The nvidia driver won't start unless xorg.conf is properly installed. If you don't have it set up, the **nvidia-xconfig** program can be used to set up a bare minimum xorg.conf. 

Be aware that the xorg.conf for the nvidia driver is not compatible with nouveau, and visa versa. So to switch between nouveau and nvidia, you must move xorg.conf files around before rebooting with or without nomodeset.

---

### Post by yedidyah on 2010-03-24
doctordruidphd,

have you got anywhere with the new kernel 2.6.32-17-generic?

My computer keeps defaulting back to the problem at start up.

---

### Post by doctordruidphd on 2010-03-24
> have you got anywhere with the new kernel 2.6.32-17-generic?

Nope. Exactly the same problem. Builds the kernel module, then crashes the whole system at the opengl screen.

---

### Post by kyleabaker on 2010-03-24
I'm having the same issues with kernel 2.6.32-17-generic. I'm still booting in -16 to use anything.

---

### Post by yedidyah on 2010-03-24
Do the developers watch these threads or are we going to have to do something with launchpad?

Indeed it answers my question above but have you ever tried to report a bug of this nature with launchpad?

---

### Post by IanW on 2010-03-25
> **yedidyah said:**
> Do the developers watch these threads or are we going to have to do something with launchpad?

Have you scrolled up lately? ;)

[QUOTE=Banner at top of this very page] Please note: Ubuntu Developers do not usually read the forums, to report a problem found in Lucid please report the bug in Launchpad.[/QUOTE]

---

### Post by Mayfairy on 2010-03-25
I had the same problem with yedidyah. After playing around a bit (a lot actually) I managed to make it work, partly because of ythe replies on this thread, so thanks for that. 

Long story short, I upgraded my Karmic to Lucid and after booting up with 2.6.32.17 kernel I could only start with low-graphics mode (which surprisingly had 1680x1050 resolution which I would use even with regular graphics). My GPU is Nvidia 9800GT. 

What I did was I first uninstalled (with --purge) "nouveau*" which removed some packages including plymouth. After that my TTY's were all scrambled and I couldn't use them. I reinstalled plymouth and some suggested/required nouveausomethingsomething package, but had nouveau itself uninstalled. 
Then I booted up with "nomodeset" and got to a login screen. CTRL-ALT-F1'd to TTY and did "sudo service gdm stop" after which I did "sudo rmmod nouveau" which to my surprise wasnt loaded whereas it before was loaded and couldn't be unloaded because it was in use. Anyways, I didn't think much about that and installed "nvidia-glx-190" and did "sudo nvidia-xconfig" afterwards. Startx command after that gave me a working Nvidia drivers. 

So, in the end the culprit was nouveau drivers that kept me from installing the real nvidia drivers giving me the exact same error report yedidyah posted on his first message on this thread. 

Thanks to whoever it was that posted about nouveau getting in the way and hope everyone else gets their systems working.


EDIT: Just for your information, my nvidia settings utility reports 195.36.15 drivers and Compiz is working really nicely. :)

---

### Post by Regenweald on 2010-03-25
```

sudo apt-get purge nouveau*

```
```

sudo apt-get install nvidia-glx-185

```
```

sudo shutdown -r now

```
worked for me. Currently booting -17. The purge command also removes plymouth, but I don't believe it works with the binary anyway.

---

### Post by doctordruidphd on 2010-03-25
Whether I try to install the 195.36.15 driver from the nvidia website, or using the same procedure im Mayfairy's post, it just crashes my system.
Nvidia says I should use ubuntu's packages (which don't work). I tried filing a but report on launchpad (bug 537745) but they say they want an apport-collect, and apport just crashes. Maybe if someone who has the same problem can join that bug and do an apport-collect, it might help.

Edit: never mind, 537745 is a different and still unresolved bug. Oh well.

---

### Post by yedidyah on 2010-03-25
Well my check disk is suddenly starting up and now I can't get any of the kernels to work at all. I am going to have to do a reinstall.

---

### Post by doctordruidphd on 2010-03-25
I went ahead and filed a launchpad bug on this (548362). Please add your comments to it if relevant.
Specifically, this addresses the 195.36.15 driver failing to install.

---

### Post by yedidyah on 2010-03-26
doctordruidphd,

after I did my reinstall I went to the "Hardware Drivers" program and it installed the Linux-x86_64 195.36.15 nVidia driver on my computer (although it says it is not enabled even though Compiz "works"). 

Is this the genuine 195.36.15 nVidia driver or some knock off that won't run high graphics games?

---

### Post by doctordruidphd on 2010-03-26
Try running the **nvidia-settings** program; if it's not installed, it can be installed through synaptic. If it runs, and shows the correct driver version, then the driver is working.

I believe this is the proprietary nvidia driver, packaged for installation by ubuntu. Not totally sure. But if nvidia-settings says it's working, then it is. You may need to do some customizing of your xorg.conf file to get all its features working, however.

Edit: you will have to do some editing of your xorg.conf to get it working at all, but you can generate a basic xorg.conf with the **nvidia-xconfig** program, if you don't already have an xorg.conf for the driver.

---

### Post by kyleabaker on 2010-03-26
> **Regenweald said:**
> ```

sudo apt-get purge nouveau*

```
```

sudo apt-get install nvidia-glx-185

```
```

sudo shutdown -r now

```
worked for me. Currently booting -17. The purge command also removes plymouth, but I don't believe it works with the binary anyway.

I followed these three commands, which successfully removed:

```

libdrm-nouveau1*
plymouth*
plymouth-x11*
xserver-xorg-video-all*
xserver-xorg-video-nouveau*

```

On restart, I went to Appearance Preferences -> Visual Effects and enabled Extras. This starts up the nvidia driver installer (you could probably do this through the hardware app, I just wanted compiz enabled all in one step).

After restarting, it was finally using the correct drivers. The only problem was that nvidia-settings didn't recognize my second monitor.

> Unable to load X Server Display Configuration page

After restoring a backup xorg.conf I have everything working again.

---

### Post by yedidyah on 2010-03-26
doctordruidphd

I ran nvidia-settings and the nVidia configuration program opened up.

Operating System: Linux-86_64
NVIDIA Driver Version: 195.36.15

I was wondering if the reason I couldn't get this to work before I did the reinstall is because I had been using Lucid since Alpha 1. With all the updates since Alpha 1 I am wondering if it just wouldn't configure right.

Now you mentioned the xorg.conf file would have to be manipulated to get all of nVidia's options working correctly. How do I know if they are working right, if I need to fix xorg.conf and what it is I need to change in xorg.conf.

Is this related to what kyleabaker is talking about?

Further information:
I found when I was reinstalling I couldn't get the new daily build from 3/24/2010 to install so I reinstalled kernel 12 and upgraded to 17. Also when I reinstalled I divided my hard drive between root (10% of total hard drive) swap (2xs my total RAM) and /home (everything else) so if things screw up again (or I need to upgrade) I should be able to preserve /home and install the new software on root(?).

---

### Post by kyleabaker on 2010-03-26
> **yedidyah said:**
> doctordruidphd

I ran nvidia-settings and the nVidia configuration program opened up.

Operating System: Linux-86_64
NVIDIA Driver Version: 195.36.15

I was wondering if the reason I couldn't get this to work before I did the reinstall is because I had been using Lucid since Alpha 1. With all the updates since Alpha 1 I am wondering if it just wouldn't configure right.

Now you mentioned the xorg.conf file would have to be manipulated to get all of nVidia's options working correctly. How do I know if they are working right, if I need to fix xorg.conf and what it is I need to change in xorg.conf.

Is this related to what kyleabaker is talking about?

Further information:
I found when I was reinstalling I couldn't get the new daily build from 3/24/2010 to install so I reinstalled kernel 12 and upgraded to 17. Also when I reinstalled I divided my hard drive between root (10% of total hard drive) swap (2xs my total RAM) and /home (everything else) so if things screw up again (or I need to upgrade) I should be able to preserve /home and install the new software on root(?).

I've been updating since Alpha 1 as well, so we could easily of had/have the same issues with nvidia. With the exception of dual screens working, removing nouveau was sufficient for me.

---

### Post by fcrowder on 2010-03-26
I am having a similar problem. I'm running mythbuntu 9.10 kernal .20       with 185 nvidia drivers.  the problem is when I start up  I have to go in low graphics. it says 

EE Failed to load module "type1" (module does not exist, 0)
EE Failed to load module "freetype" (module does not exist,0)
EE NVIDIA: failed to load the NVIDIA Kernal module. please check system;s kernal log for additional error messages.
EE Failed to load module "nvidia" (module-specif error,0)
EE No drivers available



I tried uninstalling it and installing 190 like above but then it went to black screen just befor login and stayed there. I had to reload 185 drivers to get back up and running in low graphics.

---

### Post by yedidyah on 2010-03-27
fcrowder

you said:

I tried uninstalling it and installing 190 like above but then it went to black screen just befor login and stayed there. I had to reload 185 drivers to get back up and running in low graphics.

I don't understand. Are you saying you did it the way kyleabaker did or something else?

---

### Post by fcrowder on 2010-03-27
I purged nvidia drivers 185 and then installed 190. then I had the black screen also purged the nau. thing..  had to reinstall 185 to get back to low graphics but now mythtv won't start backend or frontend ;( thinking of doing a complet reinstall. does anyone know what I need to do to save my list of shows I have for recording? not the recordings them selves but the list that myth uses to find the programs useing the guide data.

---

### Post by myromance123 on 2010-03-28
*I used Ubuntu 10.04 Beta 1 with a 9400GT Nvidia Graphics Card, a GREAT BIG THANKS to Regenweald for giving me the solution :)

I had the problem of being unable to use the drivers from Administration>Hardware Drivers because after restarting, it would give me the same problems as did installing Nvidia's drivers from their site, which are the options of Exit to Console & Run Ubuntu in Low Graphics Mode etc...

After doing this,

> Code:

```
sudo apt-get purge nouveau*

```


I attempted to reinstall the driver from Nvidia's site (195.36.15) without restarting and it wouldn't register that the X server was not running even after doing several ```
sudo gdm service stop
```. So I forced shutdown.

Power on, came to the options of Exit To Console etc and chose Exit To Console and reattempted to install 195.36.15. This time no complaints about X server, installation started and the error 'The distribution-provided pre-install script failed! Continue installation anyway? ' came out as usual. Still continued on with the installation.

 After the installation completed, I did ```
sudo service gdm start
``` and it works!

Restarted the computer to see if it would stick, it still works :D
PS: Just thought I should write down what I went through incase there are others who experience this :)

---

### Post by fcrowder on 2010-03-28
I did fresh install and now it all works and seems like things are faster too. YAY
still had to do this aswell to fix nvidia

To blacklist the module, add the following to the end of /etc/modprobe.d/blacklist.conf :
 blacklist cx18
 Reboot and try to enable your restricted drivers.

well can't seem to win for losing. now that I blocked cx18 my hauppage card is not working..

---

### Post by fcrowder on 2010-03-29
found this and fixed most of my problems.. now I have static on one tuner though..
New Steps:
Startup your system and either get to a console from the GRUB menu or boot to Ubuntu in low graphics mode and open a terminal once it's up. Once up, type the following command
sudo pico /etc/default/grub
Once inside of the file, search for this line
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
right before the last ", put vmalloc=256M, so that the line looks like:
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash vmalloc=256M"
Then, hit CTRL+O and ENTER, and then CTRL+X. This will bring you back to the terminal. At this point, we need the startup system to reconfigure itself, so we type the following command
sudo update-grub
Now, reboot the system

**NOTICE** If this doesn't work, try putting 192M instead of 256M. This has been reported to help as well.

What we've done is create an automatically booting proceedure that will allow us to use our video cards!

---

