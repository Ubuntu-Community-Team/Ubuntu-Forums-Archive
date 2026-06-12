---
title: "No X after upgrading to Vivid"
date: 2015-05-20
forum: Installation &amp; Upgrades
---

### Post by Olivier Berten on 2015-05-20
Dell XPS12 9Q33

In the first few days after upgrading, X was starting for a few seconds then stopping. Now it doesn't start at all but if I type startx in another tty, it does as it used to do: starting for a few seconds, displaying the mouse cursor then stop.

I tried running gdm and lightdm without any success.

There is no error in Xorg.0.log

Any hint would be welcome ;-)

---

### Post by Olivier Berten on 2015-05-23
Any idea where to look? how to troubleshoot?

---

### Post by grahammechanical on 2015-05-23
There is code that is used to start and stop processes. It is called an init system. Ubuntu 14.10 and lower uses Upstart. Ubuntu 15.04 use SystemD. At the Grub boot menu under Advanced Options for Ubuntu you should find an option for loading Ubuntu with Upstart. See if that makes a difference.

Advanced options also has a Recovery Mode. The recovery mode menu has a Resume option that loads Ubuntu using a fall back open source video driver. It that gets you to a working desktop it could mean that you have some video driver conflict.

Regards.

---

### Post by ubfan1 on 2015-05-23
Check /var/log/syslog for any errors too.

---

### Post by Olivier Berten on 2015-05-23
No success with upstart nor recovery mode...

No error in syslog...

Recovery mode with failsafeX gets me to an X session with a dialog stating "Your screen, graphics card, and input device settings could not be detected correclty. You will need to configure these yourself."

---

### Post by Bashing-om on 2015-05-23
Olivier Berten; Hello;

I will poke my nose into this, see if we can move this along.

Are you ( or rather, did you) have a proprietary graphics driver installed ?
From the CLI do you get positive results from terminal commands:
```

lspci -vnn | grep VGA -A 12
sudo lshw -C display

```
Where only one graphics chip is avalable
and
'lshw' in the config line depicts that the nvidia driver is loaded.
Then we can address:
> 
"Your screen, graphics card, and input device settings could not be detected correclty. You will need to configure these yourself."


See then what results when we reconfigure /etc/X11/Xorg.conf :
```

sudo nvidia-xconfig

```

at the least
[INDENT][INDENT][INDENT]see what we can do
[/INDENT][/INDENT][/INDENT]

---

### Post by Olivier Berten on 2015-05-24
No proprietary driver, as far as I know...

sudo lspci -vnn | grep VGA -A 10
```
00:02.0 VGA compatible controller [0300]: Intel Corporation Haswell-ULT Integrated Graphics Controller [8086:0a16] (rev 09) (prog-if 00 [VGA controller])
	Subsystem: Dell Device [1028:05e3]
	Flags: bus master, fast devsel, latency 0, IRQ 44
	Memory at f7800000 (64-bit, non-prefetchable) [size=4M]
	Memory at e0000000 (64-bit, prefetchable) [size=256M]
	I/O ports at f000 [size=64]
	Expansion ROM at <unassigned> [disabled]
	Capabilities: [90] MSI: Enable+ Count=1/1 Maskable- 64bit-
	Capabilities: [d0] Power Management version 2
	Capabilities: [a4] PCI Advanced Features
	Kernel driver in use: i915

```

sudo lshw -C display
```
  *-display
       description: VGA compatible controller
       product: Haswell-ULT Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 09
       width: 64 bits
       clock: 33MHz
       capabilities: msi pm vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:44 memory:f7800000-f7bfffff memory:e0000000-efffffff ioport:f000(size=64)
```

nvidia-xconfig is not available... which doesn't matter, I guess, since it's an Intel chip...

---

### Post by Bashing-om on 2015-05-24
Olivier Berten; Surprise, surprise;

OK, no Nvidia here, and Intel just works. The Intel driver is loaded.
Appears the problem lies elsewhere than a graphics driver.

What desktop are you running ?
We can try and start the desktop from terminal and see what errors we get.

[INDENT]cause and effect
[/INDENT]

---

### Post by Olivier Berten on 2015-05-30
I'm using Gnome shell.

When I type `sudo gdm` in tty1 I get[code]<7>Enabling debugging
<7>Changing user:group to gdm:gdm
<7>Lost GDM name on bus
<7>Disconnected from D-Bus[code]

And nothing happens...

After `Ctrl+C` I get[code]<7>GDM finished, cleaning up...[code]

---

### Post by Bashing-om on 2015-05-30
Olivier Berten; Hummm ....

GDM, I have limited knowledge of that DE, but will struggle through and see what we can do to get it back:

Check and make sure that GDM is set as the default:
```

cat /etc/X11/default-display-manager
cat /etc/gdm/gdm.conf

```

GDM is set as the default ?
Then let's reboot and get a terminal ( rather than the console);
This is done from the grub menu.
Booting and as soon as the bios screen clears, depress and hold the right-shift- key -> grub menu;
With the ubuntu kernel selected press the 'e' key for edit mode -> boot parameters screen;
Arrow down to the line similar "linux    /boot/vmlinuz-3.13.0-24-generic root=UUID=217ed9a7-e11a-4e32-8c05-992e8c8932b6 ro  quiet splash $vt_handoff" and arrow across to "quiet splash" - replace these terms with the term "text" with out the quotes ;
Key combo ctl+x to continue the boot process to TTY1 .

In this terminal log into the system with user name and password ( there is no response to the screen when password is entered, enter the password blindly and hit the enter key).

Now what results:
```

sudo service gdm start

```
Which 'should' start the GUI in TTY7 .
Key combo alt+F7 to gain the GUI interface and alt+F1 to return to TTY1 .
If the GUI does not start, to shut the system down from terminal:
```

sudo shutdown -h now

```
or to reboot
```

sudo shutdown -r now

```


[INDENT][INDENT][INDENT]maybe we can re-configure GDM
[/INDENT][/INDENT][/INDENT]

---

### Post by Olivier Berten on 2015-07-14
Forgot to tell I was using the gnome3-staging ppa 8-[
Purging it solved my problem... Sorry for the noise...

---

### Post by Bashing-om on 2015-07-14
Olivier Berten; Hey ....

Great, the important thing is that you have solution.

[INDENT][INDENT]just keep on keep'n on
[/INDENT][/INDENT]

---

