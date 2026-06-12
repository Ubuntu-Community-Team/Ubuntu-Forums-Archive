---
title: "Just upgraded to 14.04 getting fail message before booting into Ubuntu"
date: 2014-04-24
forum: Installation &amp; Upgrades
---

### Post by StealthMode on 2014-04-24
I am curious what this fail message means when I boot up. I get a flash of the Ubuntu purple screen, then a black screen with flashing cursor for a few seconds. Then I get a very fast flash of this error message before Ubuntu boots up. After booting into Ubuntu, it doesn't seem to have any issues thus far, other than being a little slower perhaps. A couple times it has tried to load Ubuntu, and has frozen with a pixelated half-purple, half-white screen. At that point I had to do a hard shut down and restart. Is this something to do with the Nvidia graphics card? 

The graphics card is Nvidia GeForce Go 7400 - I am currently using the Xorg open source driver. The others listed as proprietary are Nvidia version 304.117 (one being nvidia-304-updates. 

The computer is an HP Pavilion (don't have the computer in front of me in order to get model #). Attached is a picture I snapped of the error message. [ATTACH=CONFIG]252458[/ATTACH]

EDIT: I just realized that I may have worded things incorrectly. I did a fresh install of 14.04, not an upgrade.

---

### Post by Bashing-om on 2014-04-24
StealthMode; Humm,

> 
KVM
KVM (Kernel-based Virtual Machine) is a virtualization infrastructure for the Linux kernel which turns it into a hypervisor. KVM requires a processor with hardware virtualization extension.


Makes me wonder what you installed ?
```

uname -a

```


[INDENT][INDENT]sometimes a guess
[INDENT][INDENT][INDENT]is not good enough
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by StealthMode on 2014-04-24
Here is the output of:
uname -a
```
Linux megatron 3.11.0-12-generic #19-Ubuntu SMP Wed Oct 9 16:20:46 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux
```

---

### Post by Bashing-om on 2014-04-24
StealthMode; UnGood !

something stinks real bad here;
As
> 
At the core of Ubuntu 14.04 is the Linux kernel 3.13.0-24.

And you say ->
> 
I did a fresh install of 14.04, not an upgrade.


Boot that liveDVD to terminal and just to verify run the 'uname -a' command again.

The correct kernel ? -- I would suggest wiping the disk and (RE-)install . "Linux megatron 3.11.0-12-generic" is an old saucy (13.10) kernel and should not even be on a "freash install" .

[INDENT][INDENT]sometimes I do wonder
[INDENT][INDENT][INDENT]this is a case of "that should not happen"
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by StealthMode on 2014-04-24
OOPS! I'm dumb, forgive me. I absent-mindedly just ran the command in terminal while booted into Mint (Cinnamon). Here it is again. 
```
Linux megatron 3.13.0-24-generic #46-Ubuntu SMP Thu Apr 10 19:11:08 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux
```

Should I switch to the Nvidia 304 driver? Or is the Xorg better? Is this not even the cause of the computer's slowness. More RAM needed?

---

### Post by Bashing-om on 2014-04-24
StealthMode; Yeah !

Much better ..Looking at the correct kernel, so that does not pertain to the issue.

OK, back to your original premise.
Let's look : 
To see your graphics card and info:
```

sudo lshw -C display
lspci | grep VGA
lspci -nnk | grep -iA3 vga

```


[INDENT][INDENT]a different perspective
[/INDENT][/INDENT]

---

### Post by StealthMode on 2014-04-25
Output in order
```
 *-display                      description: VGA compatible controller
       product: G72M [GeForce Go 7400]
       vendor: NVIDIA Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vga_controller bus_master cap_list rom
       configuration: driver=nouveau latency=0
       resources: irq:47 memory:dd000000-ddffffff memory:c0000000-cfffffff memory:dc000000-dcffffff

```

```
01:00.0 VGA compatible controller: NVIDIA Corporation G72M [GeForce Go 7400] (rev a1)

```

```
01:00.0 VGA compatible controller [0300]: NVIDIA Corporation G72M [GeForce Go 7400] [10de:01d8] (rev a1)
    Subsystem: Hewlett-Packard Company Device [103c:30bb]
    Kernel driver in use: nouveau
02:00.0 Network controller [0280]: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection [8086:4222] (rev 02)

```

---

### Post by Bashing-om on 2014-04-25
StealthMode; Well,

That too looks good. I would expect no problems with the nouveau driver.


Off topic: Late here and I am beyond maintaining a good thought process, will pick this back up in my AM.

[INDENT][INDENT]maybe time to start looking at the log files ?
[INDENT][INDENT]something good to do to while away time[/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by Bashing-om on 2014-04-25
StealthMode; My top-of-the-morning !


OK, let's make sure all is clean for the nouveau driver;
See how the system performs with the open source driver, and then take it to the next level.
```

dpkg --get-selections | grep nvidia

```

[INDENT][INDENT]sounds like a plan to me
[/INDENT][/INDENT]

---

### Post by StealthMode on 2014-04-25
Thanks Bashing, I'll get to it this afternoon when I get home! I'll post up the output.

---

### Post by StealthMode on 2014-04-25
Ok here is the output of the command you posted Bashing:

```
nvidia-304					installnvidia-libopencl1-304				install
nvidia-opencl-icd-304				install
nvidia-settings					install

```

---

### Post by Bashing-om on 2014-04-25
StealthMode; Humm,

Do we in fact have a conflict of drivers ?
Both " configuration: driver=nouveau" and "nvidia-304					install" //

It is late here my time, will give this due consideration in my AM.

[INDENT]what to do, and
[INDENT][INDENT][INDENT]where do we go from here
[/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by StealthMode on 2014-04-26
Since I have already backed up my data from this computer, and realized that with a dual boot machine, I was just copying a lot of the same settings and such in both OS's, I went ahead and re-installed Ubuntu. I got rid of Mint, at least for now. I'm going to re-run some of the commands you had me do earlier. 

```
[COLOR=#000000][FONT=Ubuntu Mono]dpkg --get-selections | grep nvidia 
```
[/FONT][/COLOR]no output on that one. Seems the others are the same because lspci will be showing hardware, right?

---

### Post by Bashing-om on 2014-04-26
StealthMode; OK !

(RE-)install is always one sure fire fix. Works every time. ->

As this situation is now at a conclusion, please mark this thread solved -> thread tools at the top of the post. This aids others seeking a solution, helps keep the forum tidy and precludes others miss-directing efforts to render aid.

As to looking at your hardware:
```

sudo lshw

```
for "list hardware"; and to see all that is connected to the pci busses:
```

sudo lspci

``` overall, and to get specific, one does numbers, such as:
```

sudo lspci -C display
lspci -nnk | grep -iA3 vga
lspci | grep Ethernet
sudo lshw -C network 

```

The command line is very powerful, in linux the most powerful that is in existence - imho.
See:
```

man lspci
man lshw
man grep

``` just to get an idea of howto and what for.

This is open source (ubuntu) at it's best
[INDENT][INDENT][INDENT]every day can be an experience in learning
[/INDENT][/INDENT][/INDENT]

---

### Post by StealthMode on 2014-04-26
I'm still getting the fail message before Ubuntu starts though... As well as a pretty fair degree of choppiness or slowness.
 
I'm going to check the other thread as well for the "waking from suspend" thread, because my machine is doing that as well.

---

### Post by Bashing-om on 2014-04-26
StealthMode; shucks.

OK how much ram do you have on board ? Need at least 2 gigs for ubuntu to perform. How much memory does the graphics card have ? Need a gig for good performance in the graphics realm.
Else, on lower memory systems, Hey, Lubuntu is a wonder.

As to problems suspending - never had my own lap top to "experiment" with, The only times I see a lap top now-a-days is to fix the kid's or wife's. Can not help ya there. 

[INDENT][INDENT]not that it is good
[INDENT][INDENT][INDENT]maybe, just the way it is
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by StealthMode on 2014-04-27
I know it has 2GB of RAM. What I'm not sure of, if it has space for more. I have the feeling it's maxed out currently. Unless it'll accept a 4gb ram chip. I will pull off the one of the covers and check later on this evening. I was able to snap a couple pictures of the error message it gives upon start up, before Ubuntu boots. Occasionally I also get a frozen half-purple-half-white pixelated screen. At that point, it's completely locked up and I'll have to hard shut down in order to reboot.

EDIT: I hate to move away from Ubuntu, because I really like it so much, but I DO have a start-up disk with Mint 16 (Cinnamon) currently. Do you think that Ubuntu 14's requirements are just too much for this laptop? Do you think it might better handle Cinnamon without the choppiness?

---

### Post by Bashing-om on 2014-04-27
StealthMode; Well, well;

I have yet to mess with Mint, so can not advise in that respect. Nor have I installed 14.04 - I have the liveDVD and the minimalCD and will do clean installs. All I have done with 14.04 is look at it. Pretty impressed with it over 12.04 !

As to installing ubuntu release 14.04, should workie, 2 gigs of ram is good enough !
Don't think  installing Mint will be ant different as both have the same same kernel - just differing desk top environments.

Once more, as I agree, we are still looking at a graphics issue; let's look at what is presently.
```

sudo lshw -C display

```
And consider changing the driver (?) .. in a controlled situation.
[INDENT][INDENT]carefully proceed
[INDENT][INDENT][INDENT]on our merry way
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by StealthMode on 2014-04-27
Here's the output for sudo lshw -C display 
```
*-display                      description: VGA compatible controller
       product: G72M [GeForce Go 7400]
       vendor: NVIDIA Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vga_controller bus_master cap_list rom
       configuration: driver=nouveau latency=0
       resources: irq:47 memory:dd000000-ddffffff memory:c0000000-cfffffff memory:dc000000-dcffffff

```

---

### Post by Bashing-om on 2014-04-27
StealthMode; Hummm,

NO fault seen,

Well, see what I can come up with, working on it.
In the meantime, what returns from:
```

/usr/lib/nux/unity_support_test -p

```

Off topic: bad weather here, shutting down.

[INDENT][INDENT]when all else fails
[INDENT][INDENT][INDENT]read[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by StealthMode on 2014-04-27
output:
```
OpenGL vendor string:   nouveauOpenGL renderer string: Gallium 0.4 on NV46
OpenGL version string:  2.1 Mesa 10.1.0


Not software rendered:    yes
Not blacklisted:          no
GLX fbconfig:             yes
GLX texture from pixmap:  yes
GL npot or rect textures: yes
GL vertex program:        yes
GL fragment program:      yes
GL vertex buffer object:  yes
GL framebuffer object:    yes
GL version is 1.4+:       yes


Unity 3D supported:       no

```

---

### Post by StealthMode on 2014-04-27
whoops, double posted somehow. Sorry.

---

### Post by Bashing-om on 2014-04-28
StealthMode; Not good .
These ->
> 
Not blacklisted:          no
Unity 3D supported:       no

say we are going to have problems !
Lemme see what I can find out to "maybe" address the issue.
[INDENT][INDENT]don't look good for the home team
[/INDENT][/INDENT]

---

### Post by StealthMode on 2014-04-28
Uh oh.... Thank you Bashing for looking into this. I appreciate your time. 

I suppose if it's not an issue to overcome, then I'm glad I kept that Mint 16 start up disk! I am crossing my fingers for Ubuntu though!

---

### Post by Bashing-om on 2014-04-28
StealthMode; umph,

Not finding a lot of help.
Let's see what maybe some blockage.
Post back the outputs of:
```

cat /etc/environment
ls -la /etc/modprobe.d/
cat /etc/modprobe.d/blacklist.conf

```

Else, maybe see what results from the Additional Drivers' install of the 304 driver. (again)

[INDENT][INDENT]one of those times I do wonder
[/INDENT][/INDENT]

---

### Post by StealthMode on 2014-04-28
Output:
```
PATH="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/usr/local/games"
```
```
alex@megatron:~$ ls -la /etc/modprobe.d/
total 64
drwxr-xr-x   2 root root  4096 Apr 16 19:26 .
drwxr-xr-x 135 root root 12288 Apr 28 18:13 ..
-rw-r--r--   1 root root  2507 Feb 13  2013 alsa-base.conf
-rw-r--r--   1 root root   325 Apr 10 08:07 blacklist-ath_pci.conf
-rw-r--r--   1 root root  1603 Apr 10 08:07 blacklist.conf
-rw-r--r--   1 root root   210 Apr 10 08:07 blacklist-firewire.conf
-rw-r--r--   1 root root   677 Apr 10 08:07 blacklist-framebuffer.conf
-rw-r--r--   1 root root   156 Feb 13  2013 blacklist-modem.conf
lrwxrwxrwx   1 root root    41 Apr 25 19:57 blacklist-oss.conf -> /lib/linux-sound-base/noOSS.modprobe.conf
-rw-r--r--   1 root root   583 Apr 10 08:07 blacklist-rare-network.conf
-rw-r--r--   1 root root  1077 Apr 10 08:07 blacklist-watchdog.conf
-rw-r--r--   1 root root   456 Apr 14 10:34 fbdev-blacklist.conf
-rw-r--r--   1 root root   347 Apr 10 08:07 iwlwifi.conf
-rw-r--r--   1 root root   104 Apr 10 08:07 mlx4.conf
-rw-r--r--   1 root root    30 Apr 10 02:56 vmwgfx-fbdev.conf

```
```
 This file lists those modules which we don't want to be loaded by
# alias expansion, usually so some other driver will be loaded for the
# device instead.


# evbug is a debug tool that should be loaded explicitly
blacklist evbug


# these drivers are very simple, the HID drivers are usually preferred
blacklist usbmouse
blacklist usbkbd


# replaced by e100
blacklist eepro100


# replaced by tulip
blacklist de4x5


# causes no end of confusion by creating unexpected network interfaces
blacklist eth1394


# snd_intel8x0m can interfere with snd_intel8x0, doesn't seem to support much
# hardware on its own (Ubuntu bug #2011, #6810)
blacklist snd_intel8x0m


# Conflicts with dvb driver (which is better for handling this device)
blacklist snd_aw2


# causes failure to suspend on HP compaq nc6000 (Ubuntu: #10306)
blacklist i2c_i801


# replaced by p54pci
blacklist prism54


# replaced by b43 and ssb.
blacklist bcm43xx


# most apps now use garmin usb driver directly (Ubuntu: #114565)
blacklist garmin_gps


# replaced by asus-laptop (Ubuntu: #184721)
blacklist asus_acpi


# low-quality, just noise when being used for sound playback, causes
# hangs at desktop session start (Ubuntu: #246969)
blacklist snd_pcsp


# ugly and loud noise, getting on everyone's nerves; this should be done by a
# nice pulseaudio bing (Ubuntu: #77010)
blacklist pcspkr


# EDAC driver for amd76x clashes with the agp driver preventing the aperture
# from being initialised (Ubuntu: #297750). Blacklist so that the driver
# continues to build and is installable for the few cases where its
# really needed.
blacklist amd76x_edac

```

---

### Post by Bashing-om on 2014-04-28
StealthMode; Welp.
Not blacklisted.

I ran across a tid bit on launchpad that "might" help. We can try and see.

Editing a system file, make a backup before editing, just cause something might happen and also easier to revert if needed/wanted.
```

sudo cp /etc/environment /etc/environment-28apr2014
sudo gedit /etc/environment

```
add: UNITY_FORCE_START=1
Save the file
reboot

[INDENT][INDENT]back to the drawing board ?
[/INDENT][/INDENT]

---

### Post by StealthMode on 2014-04-28
Whoops! I'm posting from my phone. My desktop screen appeared quickly, with a frozen mouse pointer and no Unity. Eventually the mouse unfroze and I can move it around now, but still no Unity (no top panel, no launcher, no nothing)! It DID give me a regular login screen though, with top panel. After logging in is when everything disappeared.

---

### Post by Bashing-om on 2014-04-28
StealthMode; See the observance of the 7 Ps is good.

OK, at the login screen -> key combo ctl+alt+F1 -> terminal;
Login (user name and password) and copy the file back in place.
```

sudo cp  /etc/environment-28apr2014 /etc/environment

```

reboot
Is all back as well as was ?

I got a 'nother thought to pursue, see if it pans out to anything.

Will advise soonest I know better.

[INDENT][INDENT]an eraser is most as good
as a good back up file.
[/INDENT][/INDENT]

---

### Post by StealthMode on 2014-04-28
Yes, we're back! Ok thanks, whew! Before I gave it the command to reboot, I ran an update because it said there were package updates available. Before the reboot, there was some output about the noveau driver. Also after rebooting, before Ubuntu booted up, the fail message I get is something like "uvc video failed...."

I guess if I need to make the switch to a different environment like Lubuntu, at least I don't have anything stored on this machine! I've done 2 fresh installs in the last week or so! HAHA

---

### Post by Bashing-om on 2014-04-28
StealthMode; then it is not all bad;

Good we are back up.

That "uvc video failed...." has been with us from the get-go. -> no new news at this time. I be think'n and look'n.

[INDENT][INDENT]a means of last resort ?
[/INDENT][/INDENT]

---

### Post by StealthMode on 2014-04-28
A friend of mine suggested asking about 'nomodeset i915' ?? I have no idea what it is, and a google search yielded several responses, but it seems a bit over my head... 

I'm thinking it's a setting to tell Grub to boot graphics in a certain way? I guess there are different parameters such as setting i915 modeset=1 OR =0... But I don't really know what that means, or what it would do to my system, so I'd rather ask about it instead of blindly making changes.

---

### Post by Bashing-om on 2014-04-28
StealthMode; Yeah,

We can try and see, the boot parameter disables Kernel Mode Setting, and enables the fallback driver llvmpipe.
Test/try -> boot to the grub menu, latest kernel highlighted, -> 'e' key for edit mode -> kernel boot parameters screen;
In the kernel boot parameter screen arrow down to the line similar to "linux /boot/vmlinuz-3.2.0-24-generic root=UUID=dbd69ed2-530c-4409-8f5a-a3f1ea41fc67 ro quiet splash $vt_handoff" and across to "quiet splash" and insert the term "nomodeset" -  with out the quotes -.
Key combo ctl+x to continue the boot process.
Try your seak top and see what results, Not at all likely that 3D will function.

The parameter i915=0 performs the same function for Intel cards. Here we are talking Nvidia.
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)


[INDENT]any info is better then no info
[/INDENT]

---

### Post by StealthMode on 2014-04-29
Do I insert "nomodeset" before, after or in place of quiet splash?

I inserted it before "quiet splash" and booted. It booted into Ubuntu, but in a low graphics mode. Seems to behave the same, but the resolution is definitely much lower. I'm not sure what it means, but I'm sure it hasn't improved anything!

Looks like I need to include it at the end of the line. I'll try it again. I suppose I can also try to change to the nvidia driver and see what happens, right?

---

### Post by Bashing-om on 2014-04-29
StealthMode; Morning !

I did not expect to have good resolution with that fallback driver 'llvmpipe' . I imagine "low graphics" is all it will support. But, was worth a try to see what did result.
I will be looking to see if I can find any options to make the open source 'nouveau' perform better - I am not holding my breath.

As to the 304 proprietary driver, so long as done from the "Additional Drivers" utility ( still available in 14.04 ??) will be easily reverted back to 'nouveau", and no harm done.

If the hardware can not do it, the hardware can not do it.

[INDENT][INDENT]sometimes I wonder
[INDENT][INDENT][INDENT]sometimes I do know
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by StealthMode on 2014-04-29
Ok, I will give it a try at home this afternoon. Seems like before I re-installed, changing from the nouveau driver to the nvidia 304 didn't change much of anything. But I'll go for it. Might as well. 

At this point in the game, do you think I should look into switching to Lubuntu?

---

### Post by Bashing-om on 2014-04-29
StealthMode;

Lubuntu is very high on my mind // lemme tell ya my tale.
My wife's graphics station on an AMD sempron performed very well with release 10.04 ( pry ubuntu 10.04 out of her cold dead fingers !) -> finally updated to 12.04 and laggy and choppy to say the least. Installed Lubuntu 12.04 and I was impressed . System performance was even better than with ubuntu 10.04 and wife was very pleased.

From ubuntu alternates suggestions site:
> 
Lubuntu is a faster, more lightweight and energy saving variant of Ubuntu using LXDE, the Lightweight X11 Desktop Environment. It is targeted at "normal" PC and laptop users running on low-spec hardware.


As 'unity' is resource intensive, you may find that Lubuntu with LXDE will perform .
[https://help.ubuntu.com/community/Lubuntu/GetLubuntu](https://help.ubuntu.com/community/Lubuntu/GetLubuntu)

Wont hurt a thing to burn it to DVD ( will not fit on a CD ) and see how in runs in the "try ubuntu" mode // just bear in mind that running in this environment the OS will be S L O W . If it seems like it will do the job ( and it will ) will only take a matter of minutes to install lubuntu in the place of (u)buntu as the final test. 

I will attest that I like Lubuntu - As I have no need/use for all the bells and whistles offered in the ubuntu release. I keep things simple. To be honest, simple to the point that I run a minimal install of 'buntu, xfce for my desktop and only install on - this my "work" station - those applications that I do use frequently. All else is on other installs. (quadruple booting 'buntu's)

-------------
Let us do that, install Lubuntu, and see if you like it, and we take this matter of graphics up at that point.

[INDENT]you may be pleasantly surprised
[/INDENT]

---

### Post by StealthMode on 2014-04-29
I like the looks of xfce, so I might give Xubuntu a try. Seems that it's light weight enough for the laptop to handle it. Won't hurt now at least, and if it still doesn't work. I could always make the start up usb again and go Lubuntu.

---

### Post by Bashing-om on 2014-04-29
StealthMode; Hey;

What ever you want to try, after a bit of looking around with the Nvidia G72M [GeForce Go 7400] card, it will be trying to get it to fly right with the heavy weight desktop unity. I am more than willing to work with you on whatever you want to do to get a resolution to your situation - get you happy with 'buntu.

And yes ! I do so like xfce4, light weight and easily configured, in line with my ideal of simplicity.

[INDENT][INDENT]what ever it may take
[/INDENT][/INDENT]

---

### Post by StealthMode on 2014-04-30
Well, last night I successfully installed Xubuntu 14.04. I spent some time configuring it and personalizing it, adding some programs as well. It seems to handle the XFCE environment very well. I didn't notice any lagginess or choppiness. I suppose Unity has just become too much to handle for my poor little laptop. I will go ahead and call this one "wrapped up" because I'm not encountering any issues, other than just getting myself accustomed to a different layout. I'll be playing with the themes and such in the next few days. Thanks Bashing-Om for your diligence, I really appreciate the support and the willingness of others to lend a helping hand to someone new(er) to the Linux game!

---

### Post by Bashing-om on 2014-04-30
StealthMode; Good deal !

For further study and enlightenment; I have ran across these:
[http://docs.xfce.org/xfce/xfwm4/wmtweaks](http://docs.xfce.org/xfce/xfwm4/wmtweaks)
[http://www.linuceum.com/Distros/osDesktopConfigXfce.php](http://www.linuceum.com/Distros/osDesktopConfigXfce.php) <-How to Customize the Xfce Desktop
[http://spurint.org/projects/xfce4-debugging/](http://spurint.org/projects/xfce4-debugging/)
[https://wiki.archlinux.org/index.php/Xfce](https://wiki.archlinux.org/index.php/Xfce)

[INDENT][INDENT]ain't 'buntu wonderful
[/INDENT][/INDENT]

---

### Post by StealthMode on 2014-04-30
Thanks for the links. It really is! I'm definitely enjoying it.

---

