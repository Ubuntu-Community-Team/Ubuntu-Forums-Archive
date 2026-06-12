---
title: "Xserver error “(EE) module ANI major version(6) doesn't match the server's version(8)"
date: 2014-08-26
forum: Installation &amp; Upgrades
---

### Post by sebi2 on 2014-08-26
I have upgraded Ubuntu from 12.04 to 14.04. Afterwards, xserver couldn't start. I have downloaded the latest nvidia drivers from [http://](http://)[1]: [http://www.nvidia.com/content/DriverDownload-March2009/confirmation.php?url=/XFree86/Linux-x86_64/340.32/NVIDIA-Linux-x86_64-340.32.run&lang=us&type=geforcem](http://www.nvidia.com/content/DriverDownload-March2009/confirmation.php?url=/XFree86/Linux-x86_64/340.32/NVIDIA-Linux-x86_64-340.32.run&lang=us&type=geforcem) and rebooted. 

GRUB now has the following entries:

  ```
  *Ubuntu
     Advanced options for Ubuntu
     Memory test (memtest86+)
     Memory test (memtest86+, serial console 115200) 
```

When selecting "Advanced options for Ubuntu" the following entries are displayed:

    ```
Ubuntu, with Linux 3.13.0-34-generic
    Ubuntu, with Linux 3.13.0-34-generic (recovery mode)
    Ubuntu, with Linux 3.5.0-54-generic
    Ubuntu, with Linux 3.5.0-54-generic (recovery mode)
    Ubuntu, with Linux 3.5.0-47-generic
    Ubuntu, with Linux 3.5.0-47-generic (recovery mode)
    Ubuntu, with Linux 3.5.0-46-generic
    Ubuntu, with Linux 3.5.0-46-generic (recovery mode)
    Ubuntu, with Linux 3.5.0-44-generic
    Ubuntu, with Linux 3.5.0-44-generic (recovery mode)
    Ubuntu, with Linux 3.5.0-42-generic
    Ubuntu, with Linux 3.5.0-42-generic (recovery mode)
    Ubuntu, with Linux 3.5.0-41-generic
    Ubuntu, with Linux 3.5.0-41-generic (recovery mode)
    Ubuntu, with Linux 3.5.0-40-generic
    Ubuntu, with Linux 3.5.0-40-generic (recovery mode)
    Ubuntu, with Linux 3.5.0-23-generic
    Ubuntu, with Linux 3.5.0-23-generic (recovery mode)
```

After, installing the drivers, however, selecting any non recovery entry would lead to a black screen with a blinking cursor. After booting into recovery mode I have deleted all nvidia drivers by running:

    ```
sudo ./usr/bin/nvidia-installer --uninstall
```

Now I could again boot from any kernel without GUI enabled. I've tried starting xserver from the command line by running:

  ```
startx
```

An error related to ~/.XAuthority has occured. Running the command again as root threw the error:

  ```
modprobe error could not insert 'nvidia': unknown symbol in module
```

Next, I tried reinstalling xserver:

    ```
sudo apt-get install --reinstall xorg
```

The command was run successfully but I'm now getting the following errors when attempting to **startx**:

```
    (EE) module ABI major version (6) doesn't match the server's version (8)
    xinit: connection to X server lost
    waiting for X server to shut down (EE) Server terminated successfully (0). Closing log file.
```

Why does this occur?

I have installed nvidia-current-updates:

    ```
sudo apt-get install nvidia-current-updates
```

and ran **startx **again. The output was:

   ```
xauthL: timeout in locking authority file ~/.Xauthority
```

Afterwards, the screen kept flashing. I had to jump into terminal mode. The output is as follows:

    ```
waiting for X server to accept connections
```

and a screen of lines:

    ```
No protocol specified
``` 

After removing the **.Xauthority** file and running **startx** the following error is shown:

    ```
(EE) module ABI major version (6) doesn't match the server's version (8)
    xinit: connection to X server lost
    waiting for X server to shut down (EE) Server terminated successfully (0). Closing log file.
```

---

### Post by marino3 on 2014-09-10
Hello from France.

Your post is 2 weeks old, and as I've just run into the very same problem, I'd like to know if yoy have found a solution.

I mean a workable solution, not a reinstallation of the system as described here : "OK So you broke X, will will have to re install the system" [http://askubuntu.com/questions/516039/xserver-error-ee-module-abi-major-version6-doesnt-match-the-servers-versi](http://askubuntu.com/questions/516039/xserver-error-ee-module-abi-major-version6-doesnt-match-the-servers-versi)

And BTW, "I" didn't broke X. An automatic dist upgrade did it.

The page "How to reinstall Ubuntu"[SIZE=2] [/SIZE]https://help.ubuntu.com/community/UbuntuReinstallation says that the home folder will remain untouched [SIZE=3]**BUT**[/SIZE]:
- Some special applications settings may be in system folder *(Apache, PHP, MySQL... Argh!)*
- Installed software will be kept where possible* (... which means it's untrustable. How many dozens of apps will be to reinstall/reconfigure?)*
- System-wide steetings will be cleared* (... may be harmless, but a years-used OS is a big and complex thing)*

Seem we have a problem with our X server. Something gave up during the update process from 13.xx to 14.04. I first thought it was due to the reinstallation of the AMD Catalyst driver, but no, the problem is more serious. There is a version mismatch between the ABI module and the X server.

If I find any clue I'll post it here.

Best regards,

M

---

### Post by marino3 on 2014-09-10
An old post here [https://bbs.archlinux.org/viewtopic.php?pid=1246329](https://bbs.archlinux.org/viewtopic.php?pid=1246329) proposes a temporary solution, which consist into adding this in /etc/X11/xorg.conf:

```
Section "Server Flags"
    Option    "IgnoreABI"
EndSection
```

But if you run into this kind of error, there is no failsafe graphic mode any more (so the is no failsafe mode whatsoever).

I'm stuck with the live CD which will not allow myself to modify files on the system hard disk (read only) ... and the root terminal on the broken system and VIM to modify the xorg.conf. VIM...

The post also give another solution, to type "```
startx -- -ignoreABI
```" on the terminal. I'll try that first.

---

### Post by marino3 on 2014-09-10
startx -- -ignoreABI did not work when typed from the root terminal. The screen went black, meaning that X has attempted to start, but nope. Amazingly, no xorg.0.log has been generated.

I also tried to wipe and reinstall xserver-xorg, but nope. Still stuck with my "module ABI major version(6) doesn't match the server's version (8)"...

Seems there is nothing to do about it. No utility to diagnose/correct this. Not even a crappy makeshift.

Shall I wait for a package update to correct this? I can't even know. There is not that much doc on the web about this version mismatch.

Hellish mess.

---

### Post by marino3 on 2014-09-11
Tried:

```
sudo sudo apt-get update
sudo apt-get upgrade
sudo apt-get remove --purge xorg
sudo apt-get remove --purge xserver-xorg
sudo apt-get remove --purge fglrx
sudo apt-get autoremove
sudo apt-get install xorg xserver-xorg
sudo dpkg-reconfigure -phigh xserver-xorg
sudo apt-get install ubuntu-desktop
```

... from the recovery root terminal. Nope.


```
[   356.509] 
X.Org X Server 1.15.1
Release Date: 2014-04-13
[   356.509] X Protocol Version 11, Revision 0
[   356.509] Build Operating System: Linux 3.2.0-37-generic i686 Ubuntu
[   356.509] Current Operating System: Linux MC 3.13.0-35-generic #62-Ubuntu SMP Fri Aug 15 01:58:01 UTC 2014 i686
[   356.509] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.13.0-35-generic root=UUID=516de79f-8347-47ad-acaf-6e44b3fec267 ro recovery nomodeset
[   356.510] Build Date: 30 July 2014  12:19:53AM
[   356.510] xorg-server 2:1.15.1-0ubuntu2.1 (For technical support please see http://www.ubuntu.com/support) 
[   356.510] Current version of pixman: 0.30.2
[   356.510]     Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
[   356.510] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[   356.517] (==) Log file: "/var/log/Xorg.0.log", Time: Thu Sep 11 12:47:50 2014
[   356.518] (==) Using config file: "/etc/X11/xorg.conf"
[   356.518] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[   356.518] (==) No Layout section.  Using the first Screen section.
[   356.518] (**) |-->Screen "Default Screen" (0)
[   356.518] (**) |   |-->Monitor "Configured Monitor"
[   356.519] (**) |   |-->Device "Configured Video Device"
[   356.519] (==) Automatically adding devices
[   356.519] (==) Automatically enabling devices
[   356.519] (==) Automatically adding GPU devices
[   356.519] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[   356.519]     Entry deleted from font path.
[   356.519] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/100dpi/:unscaled,
    /usr/share/fonts/X11/75dpi/:unscaled,
    /usr/share/fonts/X11/Type1,
    /usr/share/fonts/X11/100dpi,
    /usr/share/fonts/X11/75dpi,
    built-ins
[   356.519] (==) ModulePath set to "/usr/lib/i386-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[   356.519] (II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
[   356.519] (II) Loader magic: 0xb77db6c0
[   356.519] (II) Module ABI versions:
[   356.519]     X.Org ANSI C Emulation: 0.4
[   356.519]     X.Org Video Driver: 15.0
[   356.519]     X.Org XInput driver : 20.0
[   356.519]     X.Org Server Extension : 8.0
[   356.519] (II) xfree86: Adding drm device (/dev/dri/card0)
[   356.524] (--) PCI:*(0:2:0:0) 1002:954f:1462:1612 rev 0, Mem @ 0xc0000000/268435456, 0xdfee0000/65536, I/O @ 0x0000de00/256, BIOS @ 0x????????/131072
[   356.524] Initializing built-in extension Generic Event Extension
[   356.525] Initializing built-in extension SHAPE
[   356.525] Initializing built-in extension MIT-SHM

... Blah blah ...

[   356.532] Initializing built-in extension XFree86-DGA
[   356.532] Initializing built-in extension XFree86-DRI
[   356.532] Initializing built-in extension DRI2
[   356.532] (II) LoadModule: "glx"
[   356.533] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[   356.533] (II) Module glx: vendor="X.Org Foundation"
[   356.533]     compiled for 1.10.4, module version = 1.0.0
[   356.533]     ABI class: X.Org Server Extension, version 5.0
[   356.533] (EE) module ABI major version (5) doesn't match the server's version (8)
```


Plainly stated:
```
[   356.519] (II) Module ABI versions:
[   356.519]     X.Org ANSI C Emulation: 0.4
[   356.519]     X.Org Video Driver: 15.0
[   356.519]     X.Org XInput driver : 20.0
[   356.519]     X.Org Server Extension : 8.0
...
[   356.533]     ABI class: X.Org Server Extension, version 5.0
```

Still struggling...

---

### Post by marino3 on 2014-09-11
Got rid of the ABI version error through:

```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get remove --purge xorg xserver-xorg xserver-xorg-core fglrx
sudo apt-get autoremove
sudo apt-get install xorg xserver-xorg xserver-xorg-core
sudo dpkg-reconfigure -phigh xserver-xorg
sudo apt-get install ubuntu-desktop
```

Still black screen, but I'm now facing another probleme related to the proprietary AMD driver.

Opening another post.

---

