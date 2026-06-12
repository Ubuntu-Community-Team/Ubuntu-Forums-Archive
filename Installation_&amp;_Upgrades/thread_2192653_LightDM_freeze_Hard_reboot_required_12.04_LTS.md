---
title: "LightDM freeze Hard reboot required 12.04 LTS"
date: 2013-12-09
forum: Installation &amp; Upgrades
---

### Post by johnd.jasper on 2013-12-09
As with many other Ubuntu users, I unfortunately am suffering with this problem on my Dell Dimension 2400.  Fortunately my HP Pavillion a605uk is free from this problem.  Thanks to the best in Ubuntu brainsharing (you the Ubuntu users!) I've found many avenues of workarounds to try and they are helping me get to grips with it.  I have a (so-far) foolproof workaround - booting into text mode and then manually launching LightDM and if I wasn't so determined to get a proper fix, I'd cut my losses and live with it.  Hopefully what I've learned and am still learning will help further the cause for other sufferers.

Some quick background for those interested: The original install of Ubuntu on this machine worked a charm for several weeks until I installed System Load Monitor from the Software Center.  On my next reboot, the desktop locked up with a gray screen.  I eventually booted from the Live Ubuntu disk and after that, it restarted normally.  I uninstalled SLM but the problem did not go away. I tried reinstalling Ubuntu from scratch but even that didn't help as the problem occurred on the first bootup.  Since then I've become proficient at editing GRUB on the fly, creating custom menus and tweaking various config files, not necessarily to great benefit. (NB: on this hardware, I have to boot up in kernel 3.5.0 to resolve a flashplayer video fault but the lightdm issue occurs in both 3.5.0 and 3.8.x versions)

To recap config changes, I've tried the following (in no specific order):
GRUB:
pci=use_crs

/etc/init/lightdm.conf:
Adding "and stopped udevtrigger" to the "start on" check  [no obvious benefit]
I considered trying versions of the display checks (drm-device-added card0 PRIMARY_DEVICE_FOR_DISPLAY=1) but read that it was only randomly successful for others so gave it a miss.
I also toyed with various "sleep=x" settings that randomly helped, often only for the next reboot.

/etc/rc.local:
Thanks to [this post]("https://bugs.launchpad.net/ubuntu/+source/lightdm/+bug/1188131"), I added the following settings to this script file and set it to executable:

```
/sbin/start lightdm
exit $?
```

This worked on the very next boot but fails more often than works in practice.  I added the "sleep=20" before the start lightdm line which also helped but not consistently.  Using the rc.local script had one strange effect: Prior to this, I would boot into text mode using "no splash --verbose text" from GRUB.  With the rc.local script in use, Ubuntu ignored the option and continued into graphic mode.  Changing "text" to "single" resolved this problem.

But as I said before, what works everytime (so far) is booting into text mode. Because of the Flashplayer problem, I was already using a custom GRUB menu "/etc/grub.d/06_custom" to launch kernel 3.5.0, so I have added an additional "text mode" option which is:

menuentry 'Ubuntu 3.5, Text mode' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    gfxmode $linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set=root ebe52a70-9b3f-4993-9515-d432d5761bad
    linux    /boot/vmlinuz-3.5.0-44-generic root=UUID=ebe52a70-9b3f-4993-9515-d432d5761bad ro   nosplash --verbose single
    initrd    /boot/initrd.img-3.5.0-44-generic
}

This boots to a command line from which I run "sudo lightdm" which brings up the Ubuntu desktop.


That's the story so far.  After today's unsuccessful normal boot followed by text mode boot, I reviewed the system logs and noted that lightdm reported **"pam_unix(lightdm-autologin:session)"** at 06:48.01 followed by **"pam_ck_connector(lightdm-autologin:session): nox11 mode, ignoring PAM_TTY :0"** with the same time stamp.  This coincided with the immediate end of logging anything in syslog:

Dec  9 06:48:01 diningroom dbus[493]: [system] Activating service name='org.freedesktop.ConsoleKit' (using servicehelper)
Dec  9 06:48:02 diningroom dbus[493]: [system] Successfully activated service 'org.freedesktop.ConsoleKit'
Dec  9 06:48:02 diningroom gnome-session[1264]: **WARNING: Session 'ubuntu' runnable check failed: Exited with code 1**
Dec  9 06:48:03 diningroom dbus[493]: [system] Activating service name='org.freedesktop.UPower' (using servicehelper)
Dec  9 06:48:03 diningroom dbus[493]: [system] Successfully activated service 'org.freedesktop.UPower'

This is the state of play for me.  If anyone has any "light" to shed on this lightdm problem, I'd be ever so grateful.

(Wouldn't you know it!  My reliable text mode boot workaround failed once this afternoon after a reboot.  I possibly was too quick to run "sudo lightdm."  After another restart, I ran "sudo lightdm --debug" which successfully booted.)

---

