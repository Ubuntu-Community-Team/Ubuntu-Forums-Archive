---
title: "Display Disabled at first boot after install"
date: 2010-09-24
forum: Installation &amp; Upgrades
---

### Post by PCBruiser on 2010-09-24
I have noticed a fairly large number of references to the problem that the Live/Graphical Install 10.10 Beta CD/USB stick fails to load.  I have also seen several topics where using the text version of the installer works, but then on the first and subsequent boots, Ubuntu fails to load and the monitor is turned off.  I believe that I have found the bug responsible for the issue, and a simple work around.

The problem is simple.  The native resolutions available in the default set of drivers in the current versions of Ubuntu max out at a max resolution of 1280x1024 pixels.  During the install, or load of the Live version, the installer polls the system's hardware to determine the resolution of the user's monitor.  If the monitor is an LCD, LED or plasma display, that poll generally returns the native resolution of the monitor, in my case 1920x1080 pixels.   Since the native video driver cannot accommodate displays larger than 1280x1024, I think the driver install fails.  On the next and subsequent boots, no driver is loaded, and the monitor turns off.

While I would characterise that as a serious bug, there is also an easy fix.

1.  Use the text version of the installer.

2.  When it loads to the purple Ubuntu screen, click the {space} bar to open an options menu at the bottom of the Ubuntu screen.  Click on F6 and check the option [COLOR=DarkRed]**nomodeset**[/COLOR].  Then continue the boot.

3.  The text installer should now work and install Ubuntu 10.10.

4.  On the following boot, when Grub is on the screen, highlight the installed system (it should already be highlighted in Grub) and click on **e** to enter an edit screen.

5.  Add the following to the line that starts with ** linux /boot/vmlinz ...** :
[COLOR=DarkRed][B]
nomodeset
[/B][/COLOR]
and click {esc} to end the editing session.  Make sure you have at lease 2 spaces between **[COLOR=DarkRed]nomodeset[/COLOR]** and any other Grub runtime switch.

6.  Ubuntu should now load correctly to a terrible looking screen.  That is because by using the [COLOR=DarkRed]**nomodeset**[/COLOR] boot switch you have bypassed Ubuntu's bootstrap check for the user's monitor resolution.

7.  Install the correct drivers for your video card using the Additional Drivers Control Panel, and then reboot.  

8.  Your system should now reboot normally and each time thereafter.  

Once the correct driver is installed, Ubuntu's loader will use that in lieu of the default one from the installer or live CD/USB flash stick.  You do not need to make any further edits of Grub since the edit above was used only for the single boot.

---

### Post by sikander3786 on 2010-09-24
Nice effort in setting up a guide like that. I have a few suggestions though.

> 1. Use the text version of the installer.

Do you mean alternate install disc?

> 5. Add the following to the line that starts with  linux /boot/vmlinz ... :

nomodeset

I think you'll need to type that in place of "quiet and splash".

> Additional Drivers Control Panel

It is present under System > Administration > Hardware Drivers. Will be easier to find if you mention it.

Also I think **nomodeset** only works for nvidia cards. For intel cards you've to add something like **i915.modeset=0 xforcevesa** (some other options can also be used). Not sure though. Need a bit of research.

Good work. Your very first post is a guide, nice to see that.

Welcome to the forums. :-)

---

### Post by PCBruiser on 2010-09-24
Hi,

THX for your comments.  A couple of responses to your points:

1.  Yes, exactly, the alternate install disk.

5.  I did not replace [COLOR=DarkRed]**quite splash**[/COLOR].  Rather, I left it intact.  I think it would work either way.

7.  Unfortunately, I do not have an ATI vidcard handy or I would have tested the procedure with that as well.  I would guess that Intel video would have the same issue as well.  Perhaps someone with an ATI or Intel card who had this issue can try it out.  AFAIK, [COLOR=DarkRed]**nomodeset**[/COLOR] is not manufacturer dependent, but it would be nice to have that confirmed, or not, as the case may be.

I think this issue is fairly wide spread as I noticed several new topics just posted on the same issue.  It is a bug that really needs to be dealt with.

---

