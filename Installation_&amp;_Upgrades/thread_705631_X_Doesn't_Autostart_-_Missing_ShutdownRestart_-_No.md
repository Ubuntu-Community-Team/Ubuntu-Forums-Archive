---
title: "X Doesn't Autostart - Missing Shutdown/Restart - No Login Window Preferences"
date: 2008-02-23
forum: Installation &amp; Upgrades
---

### Post by leehach on 2008-02-23
Having a problem and going around in circles trying to find a solution.  It seems that a lot of people have this problem (Google "ubuntu missing shutdown"), but there is no consistent diagnosis or solution, some people claim it has been fixed in recent distros, or it's related to kdm, Xgl, beryl, or whatever, but all I'm using is gdm on Gutsy.

The symtpoms, which I *believe* to be related, are:
1) X doesn't start when I boot.  Boot freezes on a screen showing some startup script messages, with the last line ```
*Running local boot scripts (/etc/rc.local)…
```
2) Quit menu does not show Shutdown or Restart options
3) Many people suggest checking "Show actions" in System/Preferences/Login Window, but Login Window does not appear in my System Preferences.

Why do I believe these symptoms to be related?  This is my third Ubuntu install.  First one I had problems with and eventually reinstalled.  Second one had this exact same set of issues, and then, after a few days, everything started working.  Ubuntu would boot to the login screen, I had access to the Login Window manager, and the Quit menu showed Shutdown and Restart.  I don't know why.  I was mucking around with other stuff on the new install, but I don't know that I did anything that should suddenly fix this.  But the point is, all three things started working at the same time.  

Because of something else I screwed up (don't ask), I had to reinstall, and once again I'm having these symptoms.  Currently, I'm using  Ctl+Alt+F2 to get a console and manually typing startx, then to shut down I'm using Ctl+Alt+Backspace to stop X and issuing halt or reboot from the console.  I think this solution may be to focus on why X isn't starting.  Can someone please help?

Also, I'm posting this to Installation because it is something that came up right after a reinstall, but if this is the wrong forum, please direct me to the appropriate one.

---

### Post by leehach on 2008-02-23
Possibly related additional information:

When I boot, after the ubuntu load screen (progress bar), an image of the desktop flashes by before I get to the screen with the "Running local boot scripts" message.  I went to the console and  tried to launch gdm and got the message the gdm is already running.  So, if I understand correctly, gdm is starting but is failing to start an X session.

When I startx, I get a screen of snow (moving white and black pixels, with a horizontal pattern) while the successful login music plays.  Again, this is an issue that I had on my previous install until the magic recovery.  After the magic recovery, the screen of snow stopped appearing.

---

### Post by Sam Lars on 2008-02-23
So startx works, but it doesn't automatically come up?
When you run that from a terminal, the shutdown option is not available... only if you have it started as part of boot.  At least that's what I've experienced.
Try System/**Administration**/Login Window

---

### Post by leehach on 2008-02-23
This is embarrassing, but I'm going to post my own solution.  Hopefully it will help someone else.

I previously was having a problem with xorg.conf.  During installs number 1 and 2, I used```
sudo dpkg-reconfigure xserver-xorg
``` to configure my Intel onboard graphics to use the vesa driver, because the intel driver wasn't working.  On the present install, I edited xorg.conf by hand to change the driver from intel to vesa, as follows:
```
Section "Device"
	Identifier	"Intel Corporation Integrated Graphics Controller"
	Driver		"vesa"
# old
#	Driver		"intel"
	BusID		"PCI:0:2:0"
EndSection

```
Without this edit, I couldn't get into X off of the live CD in order to start the install.  After the install, my edited xorg.conf was saved, and ubuntu started, but with the problematic behavior described above.

So I ran ```
sudo dpkg-reconfigure xserver-xorg
``` again.  Two things changed in xorg.conf.  The keyboard was set to p104 instead of p105, and refresh rates were added in the Monitor Section.  During the reconfigure, I chose the medium options (when setting monitor options, you have the option of basic or easy (don't remember), medium, and advanced).  xorg.conf was modified as follows:
```
Section "Monitor"
	Identifier	"VL173"
	Option		"DPMS"
	HorizSync	30-65		#New line!
	VertRefresh	50-75		#New line!
EndSection

```
I rebooted, and now everything is working:  Ubuntu boots to the login screen, Login Window appears as a System/Preferences option, and Shutdown/Restart appear on the Quit menu.  I also don't have the "snow" screen when X starts.  I also can switch users, which previously wasn't working, but I thought it was an unrelated issue and I was trying to address this issue first.

For anyone who cares to comment, can you please tell me what happened?  Obviously, the monitor wasn't configured correctly.   But if that prevents X from starting, why could I start it manually?  Why would missing Shutdown/Restart be a symptom?  This is now not about solving the problem, but learning more about Ubuntu.  Any responses would be appreciated.

---

### Post by leehach on 2008-02-23
Thanks Sam Lars.  So Shutdown button doesn't appear if you startx from the terminal.  How weird.  As noted, System/Adminsitration/Login Window wasn't available either.  This appears to be a common symptom.

---

