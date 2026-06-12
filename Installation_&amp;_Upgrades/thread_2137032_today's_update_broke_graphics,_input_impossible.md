---
title: "today's update broke graphics, input impossible"
date: 2013-04-19
forum: Installation &amp; Upgrades
---

### Post by frankdn01 on 2013-04-19
Running 13.04 and Nvidia graphics.  I allowed an automatic update to occur today (4/19) and upon reboot, the system became unusable.

During boot, an Nvidia splash screen appears briefly (this is new behavior), and a moment later I am presented with a dialog stating that my graphics card & input devices could not be detected and will have to be configured manually.  "OK" is the only user choice here.  Pressing <enter>, I am then given another dialog with several choices presented as radio buttons, but the mouse & keyboard are inoperative (pressing <enter> again has no effect).  I'd provide more detailed info but the system is essentially frozen at this point.

I suspect something in the update (no idea which package!) broke the Nvidia driver.  To recover, I believe I need to boot to standalone and fix, or restore the current driver or reconfigure to use some generic driver.  Unfortunately I have been away from Unix internals for many years now and have forgotten much.  I can't even remember how to remount / to read-write.

Could some kind person lead me through this in detail?  I can at least get to standalone by myself, but need my hand held thereafter.

Thank you!

---

### Post by sudodus on 2013-04-19
13.04 is still a beta version, and can be expected to break every day until the release later this month. Probably more people have the same issue and a bug-fix can be expected soon. Maybe you can report a bug to launchpad, or at least give more details here about your hardware: computer specs and particularly the nvidia card.

Do you know if you have been using a proprietary driver or the built-in driver (nouveau)? Maybe you can check when booted from the install drive. If today's daily build won't work, you can try with the 'original' Raring beta version.

And you are welcome to take part in the beta testing at [[COLOR=#ff0000]http://iso.qa.ubuntu.com/[/COLOR]]("http://iso.qa.ubuntu.com/")

---

### Post by sudodus on 2013-04-19
The iso file of lubuntu-raring-desktop-i386-daily dated 2013-04-19 can run a live session in my computer with an old nvidia on-board chip:

The built-in graphics driver ***nouveau*** is selected automatically and works with the chip ***nvidia Geforce 7050 PV / nForce 630a***

Try the same! Maybe it is the update-upgrade procedure 'only' that broke for you.

---

