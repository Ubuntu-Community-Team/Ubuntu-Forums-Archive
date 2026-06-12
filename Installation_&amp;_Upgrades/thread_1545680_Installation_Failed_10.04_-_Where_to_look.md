---
title: "Installation Failed 10.04 - Where to look?"
date: 2010-08-04
forum: Installation &amp; Upgrades
---

### Post by zSeries on 2010-08-04
Hi all,

I am trying to install 10.04 32bit onto a new 1.5TB harddrive. I had previously installed 10.04 64bit on an old drive in the same nmachine. I partitioned and formatted the new drive using the old system. I have a couple of windows partitions and restored Win2K images to them, 4 formated Ext3 partions for whever flavour of Linux appeals to me a swap and two huge NTFS Data (home) and work areas. I installed Grub on the new drive, it also has its own partition for boot config files. The old drive has now gone.

Grub2 boots OK and gives me option for all the OS's even the one that are gone, thats OK I can fix that later with grub-update. Win2K boots fine and I see my NTFS partitions.

Now I boot from the Live i386 CD and chosse to install Ubuntu. The only thing that not allowed to default is where to install. Specify partition manually, Choose a spare 20GB Ext3 and the swap is already there too. I let it reformat to Ext3 and mount as /. (In Advanced I let the install boot loader default to ticked on /dev/sda )

The install goes OK until I hit the pop-up "Installation Failed". The installed encountered an unrecoverable error. A desktop session will be run etc etc..

I have tried this at least 10 times no. I downloaded and cut a new CD even though the old one worked fine on another box. Tried unticking the boot loader. Disable the floppy, removed the floppy.

I am relatively new to Ubuntu. Where do I look for the cause of the problem? I'll cut and paste the install log files in a moment. They dont mean anything to me.

Thanks,
Tony.
ASUS M2NPV-VM. AMD64, 1GB, 1.5TB disk (12 partitions)

---

### Post by zSeries on 2010-08-04
install/debug

Ubiquity 2.2.24
/usr/lib/ubiquity/ubiquity/frontend/gtk_ui.py:563: GtkWarning: gtk_window_resize: assertion `width > 0' failed
  widget.resize(w, h)
/usr/lib/ubiquity/ubiquity/frontend/gtk_ui.py:1274: GtkWarning: gtk_progress_set_percentage: assertion `percentage >= 0 && percentage <= 1.0' failed
  self.progress_bar.set_fraction(fraction)
Exception in GTK frontend (invoking crash handler):
Traceback (most recent call last):
  File "/usr/lib/ubiquity/bin/ubiquity", line 524, in <module>
    main(oem_config)
  File "/usr/lib/ubiquity/bin/ubiquity", line 511, in main
    install(query=options.query)
  File "/usr/lib/ubiquity/bin/ubiquity", line 242, in install
    ret = wizard.run()
  File "/usr/lib/ubiquity/ubiquity/frontend/gtk_ui.py", line 513, in run
    self.process_step()
  File "/usr/lib/ubiquity/ubiquity/frontend/gtk_ui.py", line 1179, in process_step
    self.progress_loop()
  File "/usr/lib/ubiquity/ubiquity/frontend/gtk_ui.py", line 1062, in progress_loop
    (ret, realtb))
RuntimeError: Install failed with exit code 1
Traceback (most recent call last):
  File "/usr/share/ubiquity/install.py", line 2566, in <module>
    install.run()
  File "/usr/share/ubiquity/install.py", line 409, in run
    self.configure_hardware()
  File "/usr/share/ubiquity/install.py", line 1402, in configure_hardware
    install_misc.chroot_setup(self.target)
  File "/usr/lib/ubiquity/ubiquity/install_misc.py", line 101, in chroot_setup
    f = open(policy_rc_d, 'w')
IOError: [Errno 2] No such file or directory: '/target/usr/sbin/policy-rc.d'



Traceback (most recent call last):
  File "/usr/lib/ubiquity/bin/ubiquity", line 524, in <module>
    main(oem_config)
  File "/usr/lib/ubiquity/bin/ubiquity", line 511, in main
    install(query=options.query)
  File "/usr/lib/ubiquity/bin/ubiquity", line 242, in install
    ret = wizard.run()
  File "/usr/lib/ubiquity/ubiquity/frontend/gtk_ui.py", line 513, in run
    self.process_step()
  File "/usr/lib/ubiquity/ubiquity/frontend/gtk_ui.py", line 1179, in process_step
    self.progress_loop()
  File "/usr/lib/ubiquity/ubiquity/frontend/gtk_ui.py", line 1062, in progress_loop
    (ret, realtb))
RuntimeError: Install failed with exit code 1
Traceback (most recent call last):
  File "/usr/share/ubiquity/install.py", line 2566, in <module>
    install.run()
  File "/usr/share/ubiquity/install.py", line 409, in run
    self.configure_hardware()
  File "/usr/share/ubiquity/install.py", line 1402, in configure_hardware
    install_misc.chroot_setup(self.target)
  File "/usr/lib/ubiquity/ubiquity/install_misc.py", line 101, in chroot_setup
    f = open(policy_rc_d, 'w')
IOError: [Errno 2] No such file or directory: '/target/usr/sbin/policy-rc.d'

install/dm

X.Org X Server 1.7.6
Release Date: 2010-03-17
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-25-server i686 Ubuntu
Current Operating System: Linux ubuntu 2.6.32-21-generic #32-Ubuntu SMP Fri Apr 16 08:10:02 UTC 2010 i686
Kernel command line: BOOT_IMAGE=/casper/vmlinuz file=/cdrom/preseed/ubuntu.seed boot=casper initrd=/casper/initrd.lz quiet splash -- maybe-ubiquity
Build Date: 23 April 2010  05:11:50PM
xorg-server 2:1.7.6-2ubuntu7 (Bryce Harrington <bryce@ubuntu.com>) 
Current version of pixman: 0.16.4
    Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
    to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Wed Aug  4 07:45:11 2010
(==) Using config directory: "/usr/lib/X11/xorg.conf.d"
resize called 1920 1080
Unable to find a synaptics device.
The XKEYBOARD keymap compiler (xkbcomp) reports:
> Warning:          Type "ONE_LEVEL" has 1 levels, but <RALT> has 2 symbols
>                   Ignoring extra symbols
Errors from xkbcomp are not fatal to the X server
Window manager warning: Invalid WM_TRANSIENT_FOR window 0xc0011f specified for 0xc0408f (Installing).
gnome-settings-daemon: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.0.
Window manager warning: Fatal IO error 11 (Resource temporarily unavailable) on display ':0'.
 ddxSigGiveUp: Closing log

---

### Post by zSeries on 2010-08-04
Fedora 12 (are you allowed to say that here?) installed cleanly on a spare partition. Installed its own boot manager and both Windows and Fedora start without any problems.  So what's wrong with Ubuntu here? What's it really complaining about?
Thanks.

---

### Post by zSeries on 2010-08-08
Bump. Doesn't anyone have any suggestions here? This is a completely new install on a new harddrive. You couldn't get a simpler environment to install upon.
Thanks.

---

### Post by d2night on 2010-08-31
i am having a similar issue.

Can someone please help

---

### Post by Aldrahn on 2010-09-01
Hi everyone. 

Having the exact same issues as OP. 

Clean 500GB drive install. Get an installation error from Ubiquity and what looks to be a very similar log as to what the OP has posted. 
Tried the Kubuntu release as well and am having the same problem. 

Help.... please.

---

