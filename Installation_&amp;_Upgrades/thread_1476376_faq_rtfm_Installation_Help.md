---
title: "faq? rtfm? Installation Help"
date: 2010-05-07
forum: Installation &amp; Upgrades
---

### Post by KermitTensmeyer on 2010-05-07
Is there a document, wiki or webpage that might suggest the best way to approach identifying installation issues with regards to the current software?

 While I'm having a small amount of trouble (yes it's broken) with some portions of the current system (10.4), I've having greater problems trying to figure the current state of the running system.


 (yes it has run once since the initial install. There is likely some X-Org display issue, but I can't tell if problems A, B or C is driving the interface problem or masking the issue.)

Usually problems are resolved by process of elimination (ii. is working, iii is working, etc..) and reviewing the logs.

 I tried to figure out which runstate the system was in  (ps -ef no longer shows the run state, and inittab doesn't exist.) It would appear that much of the startup sequence isn't in /etc/init.d (but where?)

 Why would NetworkManager startup modem-manager? (how to disable? couldn't figure that out so I purged modem-manager. Now will that break something else?)

so.  is there a checklist of things to verify?
     is there any docs on where the configuration data now resides?
     is there a way to determine if/what the messages in Xorg.n.log are errors or informational descriptors?

  [email]tensmeyer.kermit@consultant.com[/email]

---

### Post by phillw on 2010-05-07
Hi,

With 10.04 there is a new manual out, head over to [http://ubuntu-manual.org/](http://ubuntu-manual.org/) for more details. (oooh, it's good :-) )


Regards,

Phill.

---

### Post by djchandler on 2010-05-07
If your installation boots at all, Linux writes logs in the directory /var/log. Errors are written to **/var/log/messages**.

If you can boot to the command line of the recovery console, you can view the logs using nano.

**nano /var/log/messages** will let you view the error messages.

---

### Post by KermitTensmeyer on 2010-05-07
ok. I see the logs. I read the logs.

 any hints as to what order things should complete?

are messages such as "/etc/avahi/services not found"  errors or info?
is "/etc/gdm/custom.conf not found" the reason that the X window isn't displaying?

it used to be common to display the startup messages on tty1/console. Not there any more.
 Which message should I expect when the system "thinks" the X window has been setup? If there is a mis-match because it thinks that it's on X:display or vgaFrameBuffer, or radionFrameBuffer.

would messages of the form "too much work  IRQ17" imply a driver miss-match? (cat /proc/interrupts indicates that 17 is associated with radeon.)

 is there a location that maps module depmod to drivers? (hmm. that information used to show up in /var/log/syslog. Not sure where that info is any more)

---

### Post by djchandler on 2010-05-07
> **KermitTensmeyer said:**
> ok. I see the logs. I read the logs.

 any hints as to what order things should complete?

are messages such as "/etc/avahi/services not found"  errors or info?
is "/etc/gdm/custom.conf not found" the reason that the X window isn't displaying?

it used to be common to display the startup messages on tty1/console. Not there any more.
 Which message should I expect when the system "thinks" the X window has been setup? If there is a mis-match because it thinks that it's on X:display or vgaFrameBuffer, or radionFrameBuffer.

would messages of the form "too much work  IRQ17" imply a driver miss-match? (cat /proc/interrupts indicates that 17 is associated with radeon.)

is there a location that maps module depmod to drivers? (hmm. that information used to show up in /var/log/syslog. Not sure where that info is any more)

You can edit your boot parameters in GRUB. See [this guide]("https://help.ubuntu.com/community/BootOptions"). I  suggest you use this on a temporary basis. I believe it's the default to  display boot messages booting to the recovery console, but that could be messed up with what's going on with your computer.

[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

The /etc directories contain configurations.

Yes, the reason gdm won't draw the screen is because the custom.conf  file isn't being found. /etc/avahi/services is an empty folder on my computer, but that doesn't there's no need for it to be there.

There is a history of installation and removal of .deb packages in /var/log/apt/history.log. If you are root or super user, you can view the installation,  upgrade and update process steps in /var/log/apt/term.log.

Your installation did not, perhaps could not, complete your installation  properly. X is not even close to being set up properly. If this was my  decision to make, I would start over.

The message about an IRQ being overworked would imply to me an issue involving a BIOS setting possibly. Are you having the BIOS assign an IRQ to video? It's usually an option, and only for very old VGA cards, and probably hasn't been necessary since the AGP bus was introduced. The default is no IRQ assigned. Changing this setting in your BIOS could solve your problems.

> Assign IRQ For VGA
This function allows BIOS to make an IRQ available to VGA cards. Most
current VGA card models do not require this function to be enabled.


---

### Post by KermitTensmeyer on 2010-05-09
When I changed the grub entry ( grub.conf ) to "QUIET NOSPLASH ACPI=false" the unbuntu entries in grub2 were all foobar. [yes I HAD tested by adding "ACPI=false" to the end of the runtime entry when booting from grub2. and yes it mimimzied some of the issues."

The last time I tried to install from the USB-stick method using the 10.04 live CD. This time I burned a DVD and borrowed a usb-DVD drive to boot the machine. The Graphic install failed with the same type of issues. I'm reinstalling using the text mode. if this works, then this will be the first time that Ubuntu has been able to install GUI mode (Gnome or XFCE) from text mode. All previous attempts on this machine have failed. Only graphic mode installs have succeeded before on this specific desktop (AMD64)

if this fails I'll move back to 9.04 which worked before (gui install from usb-stick/live-CD)

== Sorry If I sound a little frustrated, but it would appear that a number of things get assumed and not documented, it would not appear that the install from live-cd doesn't probe the modules and and only uses a preset list without running detect. It would appear that several "methods" of delivery were setup without anyway to detect that conflicts existed.

 Under normal circumstances (to the best of my knowledge) only one X display method should be setup (either an X display or a Radeon FrameBuffer or a Vesa Framebuffer) but not all three at the same time.  Eliminating modelines usually is most effective after the Display is mapped to a device.  Running modeline matches against multiple devices and failing because a non-existent devices does have the correct parameters, and other matches succeed. Given the way the Xorg.0.log file reads now, it is dificult to see which is the current selected device, or where the data driving the log execution is coming from.
   If the Live-CD install  doesn't configure "devices" properly, is there a list/document/wiki that indicates what script/process/Gui/Config should be used to configure elements of the system.   [[ for example.  XF86Config used to be the method to reconfigure X at considerable risk, many other config programs have been made to use instead of XF86Config, but which is the preferred method when Ubuntu is screwed up. 

It may well be that successive releases have simplified the configuration process, but I would still be interested in knowing what configuration/management process are being done for me behind the scenes. It would be nice to know (and knewbies could safely ignore)  which messages indicate errors to be fixed and messages that could be ignored

  thanks for the help

---

### Post by KermitTensmeyer on 2010-05-10
imagine that, installs with text and gui didn't work


On 10.04   installs (with usb-stick,live-cd,  DVD) fail to deliver a working system

   significant issues with  radion device driver using irq17, and the driver for serial6250 being called for irq17


  major issue with acpi usage.

 (also happens with live-DVD  AMD64  iso   and 386.iso)


so when I went back to using 9.10 install,  everything worked,  no significant kernel errors, no acpi errors, no irq17 errors

     10.04 has some major installation issues, that exist beyond the kernel realm

  Imagine that....

---

