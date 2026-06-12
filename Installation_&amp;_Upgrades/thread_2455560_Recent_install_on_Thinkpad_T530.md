---
title: "Recent install on Thinkpad T530"
date: 2020-12-22
forum: Installation &amp; Upgrades
---

### Post by anarchyalaska on 2020-12-22
I have recently installed the latest Ubuntu on my T530 machine and the touch pad occasionally goes out or stutters. It seems to come back to life if I move my USB mouse. The trackpoint (nub) doesn't work at all.

Could someone aid me in fixing this/better understanding the matter. 

If it's allowed I'd offer 5$ BTC bounty for the fix.

I tried :

```
$ sudo apt-get install *synaptics
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Note, selecting 'xorg-driver-synaptics' for glob '*synaptics'
Note, selecting 'xserver-xorg-input-synaptics' for glob '*synaptics'
Note, selecting 'xserver-xorg-input-synaptics' instead of 'xorg-driver-synaptics'
The following package was automatically installed and is no longer required:
  libfprint-2-tod1
Use 'sudo apt autoremove' to remove it.
Suggested packages:
  gpointing-device-settings touchfreeze
The following NEW packages will be installed:
  xserver-xorg-input-synaptics
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 62.9 kB of archives.
After this operation, 204 kB of additional disk space will be used.
Get:1 http://us.archive.ubuntu.com/ubuntu focal/universe amd64 xserver-xorg-input-synaptics amd64 1.9.1-1ubuntu3 [62.9 kB]
Fetched 62.9 kB in 1s (54.1 kB/s)                       
Selecting previously unselected package xserver-xorg-input-synaptics.
(Reading database ... 180767 files and directories currently installed.)
Preparing to unpack .../xserver-xorg-input-synaptics_1.9.1-1ubuntu3_amd64.deb ...
Unpacking xserver-xorg-input-synaptics (1.9.1-1ubuntu3) ...
Setting up xserver-xorg-input-synaptics (1.9.1-1ubuntu3) ...
Processing triggers for man-db (2.9.1-1) ...


```

```
$ xinput list
&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; SynPS/2 Synaptics TouchPad                  id=11    [slave  pointer  (2)]
&#9116;   &#8627; Razer Razer Mamba                           id=14    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Power Button                                id=6    [slave  keyboard (3)]
    &#8627; Video Bus                                   id=7    [slave  keyboard (3)]
    &#8627; Video Bus                                   id=8    [slave  keyboard (3)]
    &#8627; Sleep Button                                id=9    [slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard                id=10    [slave  keyboard (3)]
    &#8627; ThinkPad Extra Buttons                      id=13    [slave  keyboard (3)]


```

```
$ sudo cat /etc/default/grub
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT=0
GRUB_TIMEOUT_STYLE=hidden
GRUB_TIMEOUT=0
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"


```

---

### Post by ActionParsnip on 2020-12-22
Try the boot options in #6 here
[https://ubuntuforums.org/showthread.php?t=2442660](https://ubuntuforums.org/showthread.php?t=2442660)

Do they help?

---

### Post by #&amp;thj^% on 2020-12-22
Along with the above suggestion^^^^^

```
xinput list
&#9121; Virtual core pointer                    	id=2	[master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer              	id=4	[slave  pointer  (2)]
&#9116;   &#8627; SYNA8004:00 06CB:CD8B Mouse             	id=10	[slave  pointer  (2)]
&#9116;   &#8627; SYNA8004:00 06CB:CD8B Touchpad          	id=11	[slave  pointer  (2)]
&#9116;   &#8627; TPPS/2 Elan TrackPoint                  	id=14	[slave  pointer  (2)]
&#9123; Virtual core keyboard                   	id=3	[master keyboard (2)]
    &#8627; Virtual core XTEST keyboard             	id=5	[slave  keyboard (3)]
    &#8627; Power Button                            	id=6	[slave  keyboard (3)]
    &#8627; Video Bus                               	id=7	[slave  keyboard (3)]
    &#8627; Sleep Button                            	id=8	[slave  keyboard (3)]
    &#8627; Integrated Camera: Integrated C         	id=9	[slave  keyboard (3)]
    &#8627; sof-hda-dsp Headset Jack                	id=12	[slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard            	id=13	[slave  keyboard (3)]
    &#8627; ThinkPad Extra Buttons                  	id=15	[slave  keyboard (3)]

```
All my TP's work as expected, T430, t420, t530, t520 & X1 Carbon.
I will add placement for USB mouse dongle seems key here.
**I place any USB mouse dongle in the right rear port, this helps with the cross-talk that occurs on Ubuntu.**
And the key for me was to check all installed software related.
```
sudo apt list --installed | grep libinput
```
For my carbon x1:
```

WARNING: apt does not have a stable CLI interface. Use with caution in scripts.

libinput-bin/focal-updates,now 1.15.5-1ubuntu0.2 amd64 [installed,automatic]
libinput10/focal-updates,now 1.15.5-1ubuntu0.2 amd64 [installed,automatic]
xserver-xorg-input-libinput/focal,now 0.29.0-1 amd64 [installed,automatic]

```
Most of my issues went away with the install of "xserver-xorg-input-libinput". _And where I placed the USB dongle for the added mouse._
```
sudo apt install --reinstall xserver-xorg-input-libinput
```
Good Luck!

---

