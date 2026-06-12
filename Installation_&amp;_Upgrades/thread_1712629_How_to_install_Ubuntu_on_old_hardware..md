---
title: "How to install Ubuntu on old hardware."
date: 2011-03-23
forum: Installation &amp; Upgrades
---

### Post by steve8track on 2011-03-23
I wanted to install Ubuntu on a older laptop so that I could still have all of the bells and whistles where I wanted them and not have some of the hassles of the lighter distributions.  I tried DSL first, but I wanted a more permanent solution in the form of a traditional hard drive install.  Plus I like modern fonts and wanted a new browser rather than firefox 2.0 on DSL.

I'm typing this post from the machine I installed Ubuntu 10.10 on.  Here are my specs:

```

Ubuntu 10.10 32-bit Alternate
IBM Thinkpad iSeries 700 MHz with 128 MB of RAM.
Netgear WG111v2 USB wireless adapter.
Google Chrome (Firefox, and epiphany-webkit)

```

This machine is slow, but it's far more tolerable than I would have thought.  The biggest problem with the limited system specs was overflowing the RAM and having to use swap, so this includes some ways to reduce RAM consumption.  Without anything open, I use most of my RAM, so I'd recommend a system with a tad bit more RAM than this system has.  The command line seems very responsive, and web browser performance is decent.

On to business.

I tried installing Lubuntu from the live CD, but it kept freezing.  Instead, I downloaded the Ubuntu 32-bit Alternative CD so that I could install without a GUI.  On this machine, I needed to add some boot flags, otherwise it would get stuck on a blinking cursor.  On the alternate CD main menu, press F6 to open boot flags, then hit escape to get to the boot line.  Leaving a space after the "--" at the end of the line, add these flags if you have trouble with the installer stopping when it starts:

```
vga=792 acpi=force irqpoll
```

After running through the install, don't log in because the default desktop environment is pretty heavy.  Instead, press Ctrl+Alt+F1 to go to a virtual console.  Let's make ubuntu run faster before we log in graphically.

cd /etc/init/

In this directory are config files for startup processes.  You can see a description by reading the comments in the file.  I suggest running cat to view the contents and determine on a case by case basis what you want to disable.  When you decide you don't need a process, rename the file.  I chose to append a .no to the end of the file.  That way, if you disable something you actually needed, then you can reenable it by moving it back. (text to the right of the # are comments and aren't necessary).

```

clear;ls | grep -v .no #clears the screen and shows the files in the current directory, skipping ones you've already renamed.
cat filename.conf #prints the file
sudo mv filename.conf filename.conf.no #renames the file

```

Here are the files I have and renamed (I disabled power management because I doubt this old of a laptop could run on battery, but I might re-enable it since the battery seems to work):

```

acpid.conf
alsa-mixer-save.conf.no (you can set this the first time by typing alsa-mixer and lowering the volume before rebooting)
anacron.conf.no
apport.conf.no
atd.conf
avahi-daemon.conf.no
console-setup.conf
control-alt-delete.conf
cron.conf.no
cups.conf.no
dbus.conf
dmesg.conf
failsafe-x.conf
gdm.conf
hostname.conf
hwclock.conf
hwclock-save.conf.no (I disabled this because the battery in my BIOS battery is dead anyway)
irqbalance.conf.no
module-init-tools.conf
mountall.conf
mountall-net.conf
mountall-reboot.conf
mountall-shell.conf
mounted-dev.conf
mounted-tmp.conf
mounted-varrun.conf
networking.conf
network-interface.conf
network-interface-security.conf
network-manager.conf
plymouth.conf.no
plymouth-log.conf.no
plymouth-splash.conf.no
plymouth-stop.conf.no
procps.conf
rc.conf
rcS.conf
rc-sysinit.conf
rsyslog.conf
screen-cleanup.conf.no
tty1.conf (you need at least one of these for a virtual console, this is Ctrl+Alt+F1)
tty2.conf
tty3.conf
tty4.conf.no
tty5.conf.no
tty6.conf.no
udev.conf
udev-finish.conf
udevmonitor.conf
udevtrigger.conf
ufw.conf.no
upstart-udev-bridge.conf
ureadahead.conf.no
ureadahead-other.conf.no

```

You can restart the computer and try out the settings:

```

sudo shutdown -r 0 #restart
sudo shutdown -h 0 #or just shutdown

```

After rebooting, you can log in graphically, where we can disable some more processes:

System -> Administer -> Startup

Disable practically everything, unless you need something specifically.  I disabled everything because I'm not even using the default Gnome environment.

Log in to your wireless and install another window manager that uses less RAM.  This one looks great and is pretty lean:

```

sudo apt-get install fvwm-crystal

```

I would also open gconf-editor and make changes in various program settings to disable things you don't want.

System -> Administer -> Login Screen

I set my computer up to log in directly to fvwm-crystal so that I don't waste startup time on this slow machine with the login manager.

If you have problems where it logs in to Gnome instead of fvwm-crystal, then you can remove it from your login menu as an option and force it to load fvwm-crystal:

```

cd /usr/share/xsession/
sudo mv gnome.desktop gnome.desktop.no

```

Then set the default to load fvwm-crystal:
```

cd /etc/gdm/
sudo nano custom.conf

```

Change the line that says DefaultSession to "DefaultSession=fvwm-crystal"

Reboot to your new desktop.

If you have the same iSeries thinkpad as me, the screen resolution is wrong and we'll need to force it to use the correct resolution.

```

sudo gedit /etc/X11/xorg.conf
sudo services gdm restart #start the GUI again

```

Here is my configuration:

```

Section "Device"
	Identifier	"Configured Video Device"
	Driver	 "vesa"
EndSection

Section "Monitor"
	Identifier	"Monitor"
	option "DPMS" "True"
	Horizsync 30.0-60.0
	VertRefresh 50.0-70.0
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor	 "Configured Monitor"
	Device	 "Configured Video Device"
	Subsection "Display"
		Depth	24
		Modes "1024x768@60"
	EndSubsection

EndSection

```

One of the advantages of this window environment is you can still use the wireless applet you used in gnome.  Just right click on the desktop to open a terminal and type "nm-applet" to open the network manager.

Now you can go download google Chrome, install Battle for Wesnoth, or Epiphany, and enjoy your newly resurrected computer.

If you have any suggestions to get even more performance from older hardware, please comment. I hope someone finds this useful.

---

### Post by mörgæs on 2011-03-23
Thanks, it looks interesting. I have and old portable running Lubuntu, but maybe I should try this.

I am a little skeptical, though. Is there any development going on in fvwm-crystal? A brief googling only yields semi-old web pages.

---

### Post by steve8track on 2011-03-23
If lubuntu is working well for you but you want to try and make it faster, I'd just try some of those tweaks on it, like renaming files in /etc/init. 

fvwm-crystal doesn't look like it's changed for years as far as I can tell, but I don't use it all the time.  You could try some other window managers.  After the above tweaks, even gnome ran much better. 

Here are some other lightweight window managers:
wmii - no desktop, just windows adjacent to windows.  could fit this on a 3.5 in floppy
enlightenment - 2mb or so in size, but still has some eye candy

---

