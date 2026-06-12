---
title: "Partially black screen after update on Ubuntu 14.04"
date: 2015-05-07
forum: Installation &amp; Upgrades
---

### Post by elysia2 on 2015-05-07
Hi all!
I have a curious problem after having an update on my ubuntu 14.04 linux box (see attachment): just a portion of the screen is visibile, but icons and mouse are doing nothing...the video card is ok: starting from an usb live Ubuntu 15.04 everything is ok.

I've tried to upgrade to 15.04 but problem still remains...

This is my **lshw -c display** output:

```
  *-display
       description: VGA compatible controller
       product: GF119 [GeForce GT 610]
       vendor: NVIDIA Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vga_controller bus_master cap_list rom
       configuration: driver=nouveau latency=0
       resources: irq:16 memory:f6000000-f6ffffff memory:e8000000-efffffff memory:f0000000-f1ffffff ioport:e000(size=128) memory:f7000000-f707ffff
```

While this is the content of Xorg.0.log:

```

[     9.958] 
X.Org X Server 1.17.1
Release Date: 2015-02-10
[     9.958] X Protocol Version 11, Revision 0
[     9.958] Build Operating System: Linux 3.2.0-61-generic x86_64 Ubuntu
[     9.958] Current Operating System: Linux laura 3.8.0-25-generic #37-Ubuntu SMP Thu Jun 6 20:47:07 UTC 2013 x86_64
[     9.958] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.8.0-25-generic root=UUID=a5bfb6d8-bdbe-4e88-8b8e-434175918e75 ro
[     9.958] Build Date: 19 March 2015  09:26:59AM
[     9.958] xorg-server 2:1.17.1-0ubuntu3 (For technical support please see http://www.ubuntu.com/support) 
[     9.958] Current version of pixman: 0.32.6
[     9.958]     Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
[     9.958] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[     9.958] (==) Log file: "/var/log/Xorg.0.log", Time: Wed May  6 23:17:54 2015
[     9.958] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[     9.959] (==) No Layout section.  Using the first Screen section.
[     9.959] (==) No screen section available. Using defaults.
[     9.959] (**) |-->Screen "Default Screen Section" (0)
[     9.959] (**) |   |-->Monitor "<default monitor>"
[     9.959] (==) No monitor specified for screen "Default Screen Section".
    Using a default monitor configuration.
[     9.959] (==) Automatically adding devices
[     9.959] (==) Automatically enabling devices
[     9.959] (==) Automatically adding GPU devices
[     9.959] (==) ModulePath set to "/usr/lib/x86_64-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[     9.959] (II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
[     9.959] (II) Loader magic: 0x7fcc1a61ed80
[     9.959] (II) Module ABI versions:
[     9.959]     X.Org ANSI C Emulation: 0.4
[     9.959]     X.Org Video Driver: 19.0
[     9.959]     X.Org XInput driver : 21.0
[     9.959]     X.Org Server Extension : 9.0
[     9.959] (II) xfree86: Adding drm device (/dev/dri/card0)
[     9.960] (--) PCI:*(0:1:0:0) 10de:104a:10b0:104a rev 161, Mem @ 0xf6000000/16777216, 0xe8000000/134217728, 0xf0000000/33554432, I/O @ 0x0000e000/128, BIOS @ 0x????????/524288
[     9.960] (II) LoadModule: "glx"
[     9.960] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[     9.965] (II) Module glx: vendor="X.Org Foundation"
[     9.965]     compiled for 1.17.1, module version = 1.0.0
[     9.965]     ABI class: X.Org Server Extension, version 9.0
[     9.965] (==) AIGLX enabled
[     9.965] (==) Matched nvidia as autoconfigured driver 0
[     9.965] (==) Matched nouveau as autoconfigured driver 1
[     9.965] (==) Matched nvidia as autoconfigured driver 2
[     9.965] (==) Matched nouveau as autoconfigured driver 3
[     9.965] (==) Matched modesetting as autoconfigured driver 4
[     9.965] (==) Matched fbdev as autoconfigured driver 5
[     9.965] (==) Matched vesa as autoconfigured driver 6
[     9.965] (==) Assigned the driver to the xf86ConfigLayout
[     9.965] (II) LoadModule: "nvidia"
[     9.965] (WW) Warning, couldn't open module nvidia
[     9.965] (II) UnloadModule: "nvidia"
[     9.965] (II) Unloading nvidia
[     9.965] (EE) Failed to load module "nvidia" (module does not exist, 0)
[     9.965] (II) LoadModule: "nouveau"
[     9.965] (II) Loading /usr/lib/xorg/modules/drivers/nouveau_drv.so
[     9.966] (II) Module nouveau: vendor="X.Org Foundation"
[     9.966]     compiled for 1.17.1, module version = 1.0.11
[     9.966]     Module class: X.Org Video Driver
[     9.966]     ABI class: X.Org Video Driver, version 19.0
```

Any idea?

Thanks in advance!

Ely

---

### Post by Bashing-om on 2015-05-07
elysia2; Hi !

I see that Nvidia recommends the 346 driver for the [GeForce GT 610] as a proprietary driver.
In preparation for perhaps installing a different driver;
What results when you boot the system in 'recovery' mode ?

Though 15.04 is supposed to have enhanced support for graphics, perhaps 'nouveau' is not cutting it ?

I see in the logs:
> 
9.965] (II) LoadModule: "nvidia"
[     9.965] (WW) Warning, couldn't open module nvidia


Do we need to look and see why Nvidia module did not build ?

[INDENT][INDENT]hey, it's just a thought
[/INDENT][/INDENT]

---

### Post by elysia2 on 2015-05-08
Hi Bashing-om!
if I start Ubuntu in recovery mode, it says that it's running in low resolution but trying to run with default graphical mode just show a black screen with a big cross mouse pointer. It seems also not allowed me to start with a generic configuration. May be because I've missed the Xorg.conf file? It doesn't exist anymore.

Thanks,

ED

---

### Post by Bashing-om on 2015-05-08
elysia2; Shucks,

OK, just means we have to find another means to 'see' what is going on....
Let's find out if you remain on 14.04 or if 15.04 is at play here
Can you boot to terminal ? :
At the grub menu with the ubuntu normal kernel selected press the 'e' key for edit mode -> boot parameters screen
Does a line similar to this exist " linux    /boot/vmlinuz-3.13.0-24-generic root=UUID=217ed9a7-e11a-4e32-8c05-992e8c8932b6 ro  quiet splash $vt_handoff" ? (in 14.04 )
IF so, arrow down to that line and across to the terms "quiet splash" and replace these terms with the term "text" - without the quotes .
Key combo ctl+x to continue the boot process. -> TTY1
Login here with username and password ( there will no no response to the screen when password is entered) .
Now at terminal execute terminal commands:
```

sudo apt-get install pastebinit
cat -n /etc/apt/sources.list | pastebinit
tail -v -n +1 /etc/apt/sources.list.d/* | pastebinit

```
The results of the commands are URLs with contents of the files. Pass those URL's back here and we get an idea of what we are dealing with.

IF the system is stable in this terminal environment we then see about installing a proprietary graphics driver.

[INDENT][INDENT]where there is a will there is a way
[/INDENT][/INDENT]

---

### Post by elysia2 on 2015-05-09
Bashing-om, finally resolved[**[COLOR=#DD4814][B]**[/COLOR][/B]]("http://ubuntuforums.org/member.php?u=1111508")!
I did just add gdm service that I think wasn't influential and then run this from a tty window:
[B]
sudo apt-get install nvidia-current nvidia-settings[/B]

It reconfigured definitely the nvidia driver and at the reboot the screen was ok!!

Thanks for your help anyway!!

---

### Post by Bashing-om on 2015-05-09
elysia2; Great !

As this situation is now under control;
Please mark this thread solved;
aides others seeking the solution,
helps keep the forum clean and
precludes others miss-directing efforts to aid.
[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

and
[INDENT][INDENT][INDENT]keep on keep'n on
[/INDENT][/INDENT][/INDENT]

---

### Post by elysia2 on 2015-05-09
hers is it, thanks! ):P

---

