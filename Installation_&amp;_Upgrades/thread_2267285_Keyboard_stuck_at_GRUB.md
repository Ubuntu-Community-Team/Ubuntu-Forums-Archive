---
title: "Keyboard stuck at GRUB"
date: 2015-02-28
forum: Installation &amp; Upgrades
---

### Post by nitez on 2015-02-28
I've had ubuntu running as a home server for years now (file server, backup, transmission mainly, some streaming). Now running on precise on an old Pentium Dual Core, 2 GB RAM. I've initially installed desktop edition, now booting to command line and will eventually move to server edition. It's served me greatly over the years but I've had one main recurrent issue:

Every so often, server would get stuck at grub (1.99) and I wouldn't be able to navigate or select menu item. However, when rebooting, hitting F11 for bios boot options and selecting the default drive, I would see the exact same GRUB but can now operate the menu and get the server to work. This is now a constant problem (every boot!).

Is this a GRUB issue or maybe even simply that my hardware is too old???

---

### Post by Bashing-om on 2015-02-28
nitez; Well;

As MAFoElffen has well said:
Ubuntu Server does not use X11 at all, unless the user installs it.

The Server install iso is Linux kernel and so it the installed system. So the keyboard is BIOS to Grub2. Grub2 has kb and basic USB drivers.. Note that LILO doesn't recognized USB keyboards... Then hands off to kernel (kb drivers there also). Then if there are graphics layers, as in a desktop edition, then there are additional keyboard drivers in X11.

After installing Server edition on hundreds of server's... I can confirm that "some" server boards don't like a USB keyboard on the install disk. ...and not all BIOS'es will pick up a USB keyboard in post. USB support on the motherboards has layers... So you have more of a chance on picking up USB keyboard through one of the USB root hub ports than through the second layer or an extension...Those root ports are normally on the back of the motherboard, near the keyboard/mouse PS2 ports. Usually ports
on the front of a PC are on a higher layer or on an extension. But those
same ports do pick up when the kernel boots through the HID drivers.

I have 2 server boards here that are opposite and would only POST with a
USB keyboard, but those are oddballs and not the norm. A ASUS and a Dell 960 server. Funny thing is I have 2 Dell 960 Servers and the other is
fine/normal. But with both those 960's, the USB keyboard is not recognized
in enough time to be able to get into BIOS Settings using a USB keyboard, so it doesn't recognize them early enough on those...

I have access to both PS2 and USB keyboards here, but I "do" a lot of dev
testing. Traditionally, you are going to have more of a chance for success
with a PS2 keyboard during POST and the early boot process. I get
keyboards (both usb or ps2) for about $10 each at a Recycler. I also have
USB/PS2 adapters for my USB mice and keyboards. They plug into the
mouse/keyboard PS2 ports of the motherboard and the USB mouse or keyboard
plug into them.

bk

The bottom line is that it all begins in bios, changing the USB settings in bios may have a good affect.

[INDENT][INDENT]my bit to try and help
[/INDENT][/INDENT]

---

### Post by nitez on 2015-02-28
Thank you Bashing-on, this has definitely led me in the right direction. I enabled support for legacy USB in BIOS and I can navigate without rebooting as described above. That did the trick. However, I will still actually have to press "enter" to boot. I've tried several changes in grub default and timeout in /etc/default/grub followed by sudo update-grub (as described in many other posts) but no no avail. I've now both set back to 0. Am I overlooking something.

PS: as noted above, i want to confirm this is an desktop installation (I wasn't ready for command line only at the time) with a "text" setting in grub. I know by now that it doesn't make sense but that's the situation. Not sure whether this changes anything about this problem?

---

### Post by nitez on 2015-03-01
Thanks again to Bashing-on for helping me fix the keyboard issue.
As for GRUB, this did the trick: [http://ubuntuforums.org/showthread.php?t=1361331]("http://ubuntuforums.org/showthread.php?t=1361331"). Doesn't look very clean but fixed my problem. I still wonder when/how this problem started though ...

---

### Post by Bashing-om on 2015-03-01
nitez; Hey hey ...

Great, making good progress.
That old thread you reference, a lot has changed with grub since then; You will have to be explicit with the edit(s) you made.
Be aware I too boot to terminal, and IF I want a GUI I start it from terminal.
For your consideration, consideration only -  As I am multi-booting - : my /etc/default/grub file:
```

sysop@1404mini:~$ cat /etc/default/grub
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=false
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR="My-Work-14.04"
GRUB_CMDLINE_LINUX_DEFAULT="text"
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
GRUB_GFXMODE=1600x900

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"
sysop@1404mini:~$

```
grub is not only versatile, it is very powerful in what it interacts with the kernel. That is a story for a big book.

[INDENT][INDENT]it is a thing of glory
[/INDENT][/INDENT]

---

### Post by nitez on 2015-03-07
For reference, my grub file:

```
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=3
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=3
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="text"
GRUB_CMDLINE_LINUX=""

# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"

# Uncomment to disable graphical terminal (grub-pc only)
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

I played with the timeout values (0, 3, 5, 10) but it isn't this that solved the issue. What solved it was to change the grub.cfg, precisely in the following sequence:

1) sudo nano /etc/default/grub
2) sudo update-grub
3) sudo nano /boot/grub/grub.cfg

Changing this (i.e. in grub.cfg) from:

```
fi
terminal_output gfxterm
if [ "${recordfail}" = 1 ] ; then
  set timeout=3
else
  if [ x$feature_timeout_style = xy ] ; then
    set timeout_style=hidden
    set timeout=[COLOR="#FF8C00"]0[/COLOR]
  # Fallback hidden-timeout code in case the timeout_style feature is
  # unavailable.
  elif sleep --interruptible 3 ; then
    set timeout=0
  fi
fi

```

... into this:

```
fi
terminal_output gfxterm
if [ "${recordfail}" = 1 ] ; then
  set timeout=3
else
  if [ x$feature_timeout_style = xy ] ; then
    set timeout_style=hidden
    set timeout=[COLOR="#FF8C00"]3[/COLOR]
  # Fallback hidden-timeout code in case the timeout_style feature is
  # unavailable.
  elif sleep --interruptible 3 ; then
    set timeout=0
  fi
fi

```

i.e. second "set timeout=" value changed from '0' to whatever is in the first "set timeout=", 4 lines above (value=3 in this case, as set in /etc/default/grub). Another "sudo update-grub" would overwrite this change in grub.cfg (setting the second "set timeout=" value back to 0). Any idea why that is and why it would block boot to the grub screen?

Haven't had boot problems at all since this change so great for me!

---

