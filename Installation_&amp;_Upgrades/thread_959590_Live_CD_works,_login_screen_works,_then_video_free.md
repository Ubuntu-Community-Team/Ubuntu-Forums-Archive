---
title: "Live CD works, login screen works, then video freezes and hangs (please help!)"
date: 2008-10-26
forum: Installation &amp; Upgrades
---

### Post by painaxl on 2008-10-26
Hey all,

I'm having a serious problem with an older computer I just put a fresh install of 8.10rc on. First some background:

This computer ran Drake fine and was upgraded to Gutsy fine. Earlier this year, I did a clean install of Heron to make a /home partition. Everything worked for a while, but after what must have been an update (it's not my computer, so I don't know what update might have caused the issue), the following problem would happen: After logging in, the screen would switch resolutions once and I'd see the mouse. Then, a flicker and the screen is all distorted with just one space of correctly displayed background with the cursor (which is no longer movable). Then it distorts again and the system is completely frozen. Under Heron, I was able to CTRL-ALT-BKSP and return to the login screen where I could select "failsafe GNOME", which would work.

I did a clean install of 8.10rc yesterday in hopes that with a fresh install, the problem would be eliminated. The live CD displays the graphics perfectly and the installation went smoothly. The login screen again displays fine. However, when I log in, the same problems happen. This time, though, "failsafe GNOME" does the same thing. My only option upon logging in is getting to a terminal.

I've tried editing my Xorg.conf, but each field says automatically detected monitor/card etc. I've also read from searching that newer versions of Ubuntu pretty much disregard xorg.conf anyways in favor of autodetecting. Is that true?

Also, why would the login screen be fine and then the crash?  If I hit CTRL-ALT-BKSP while the screen is messed up (before it freezes) the screen changes resolutions and I can see the background of the desktop perfectly before it goes back to the login screen.

The computer is an emachines with onboard graphics (intel chipset) and a CRT monitor that still works fine. This is the first time I've been truly stuck with Ubuntu as I've been able to find my way around pretty much every other problem.

Any help or suggestions anyone would give would be HUGELY appreciated!

---

### Post by painaxl on 2008-10-27
An update:

After reconfiguring xorg.conf, copying from the live CD and everything else I could find online to try, nothing changed.

I downloaded the RC of xubuntu 8.10 and installed it over the Ubuntu 8.10 install.  Xubuntu installed fine and works after logging in.

My understanding then, is that this would be a problem with GNOME, rather than with X as both Xubuntu and Ubuntu use X, right?

---

### Post by jacabmou on 2008-10-27
I have the exact same problem.. almost..

When i login, kdm/xserver(something) restart, and take me back to the login screen.. 

Im using Kubuntu 8.10, and KDE 4.1..

When booting the same disk in Wmware under windows, there is no problem..

I have seen other post like this but no solutoin yet..:(

Good luck

Jacob

---

### Post by theducks on 2008-10-27
Kubuntu RC Live CD on Dell GX60 (1G ram )hangs on KDE screen.
Toshiba S1135 has dual screen graphics, issues when trying to use other than clone mode.

Common theme: Intel Graphics chip set ?

---

### Post by jacabmou on 2008-10-28
bumb

---

### Post by gukid on 2009-01-21
I've been having pretty much the exact same problem, generally.  Seems as though the common factor with all the cases I've been reading about have Intel integrated graphics chips, or intel controller cards.

My problem:  Was running ubuntu 8.10 on an older pc no problem, motherboard fried and had to be replaced, replaced the cpu as well.  Put the thing back together, and 8.10 freezes at the login screen.  Every piece of hardware is the same except for the CPU (which is a P3 1ghz, can't see any problem there) and the motherboard (ASUS CUSL2 with integrated Intel video, no integrated sound or network).  I'm not using the integrated video, and have it disabled as much as possible in the bios, display is going through a GeForce2 MX 400.

The exact problem, as far as I can tell, with 8.10 and up (I've tried daily builds).  If I have compiz installed, the pc locks up right at the login screen, no blinking cursor, no keyboard/mouse, can't do anything.  If I uninstall compiz, I get to the login screen, the cursor is blinking on the login prompt, but I can't interact with the mouse/keyboard.

Things I've tried!
8.10 alternate install, has this problem, nothing I can do.

Any Ubuntu daily build alt install, exact same thing.

Fedora 10 Live CD, freezes at a black screen before the login.
Ubuntu 9.04 Daily Live, freezes at black screen before login...

8.04 WORKS! No problems at all. Graphic driver works, compiz works, no lock-ups or freezes, keyboard and mouse always work and detect.


HERE'S THE KICKER:
I installed 8.04, upgraded to 8.10, same problem as listed before.  BUT, if in GRUB if I go to the menu and choose to boot the older kernel, from 8.04, it boots fine but with some driver issues with the graphics... ODD?  From there I also did the upgrade to 9.04 Alpha, will all updates installed, same problems, BUT, again I can boot the very old 8.04 kernel and get in with graphic driver issues.  Not saying it's the kernel, but it seems to be somehow related for sure.

I've been working at this... for about 2 weeks independently now.  I'd love for anyone who really knows what they're doing to ask me some questions so I can get a newer Ubuntu running on this system again.  Seems everything after 8.10 does this, and a fresh 8.10 install USED to work, on the other motherboard, so that pretty much eliminates any possiblity that it's any other hardware in my system.

---

### Post by switchrodeo720 on 2009-01-24
gukid, 

Unfortunately I'm not the expert you're looking for, but I've had similar experiences. I originally upgraded from 8.04 to 8.10 using the update manager and starting having weird issues right away. 

I tried installing 8.10 with a fresh install but couldn't. I then tried another gnome distro (Fedora 10) with no luck. 

Whether I try to install Fedora 10 or Ubuntu 8.10 I get held up during the install process. I've never had any issues with any Ubuntu release before 8.10.

---

### Post by gukid on 2009-01-25
Reading on the internet, it seems quite a lot of people are having very similar issues, and most have just been happy to stay at 8.04, or move to a different distribution that doesn't have problems.

Seems to be 2 common things:

1. Problems with X Login freezing when using an intel chipset (integrated video may not be a factor).  I have this problem.

2. Not getting keyboard/mouse devices on older systems due to the input-evdev/hotplug module.  xorg.conf settings are ignored, and devices are not detected properly, even though they work perfectly in the commandline (why is each part of the system doing things differently anyway?).  I also have this problem.

So right now I'm doing as others are, sitting at 8.04, now using Xfce because it runs much much better than Gnome (I can even play Xvid full screen).  I really wonder if anyone on the dev side is aware of these issues?

Just recently tried Xubuntu 8.10 Live with the same problem.  I've also been testing the daily builds every few days, with no luck whatsoever...

---

### Post by switchrodeo720 on 2009-01-25
I have no problems with Ubuntu 8.04. I plan on staying with it until there's a major reason to update. I ended up installing Fedora 10 on virtual box with no issues, just to give it a try. 

I'm still suprised that not many are talking about a fix for these issues.

---

### Post by gukid on 2009-01-27
I don't think a Virtual Box is a good test though, since it uses emulated hardware and not your real hardware, so the results would be completely different.  Try booting the Fedora 10 Live CD and see what happens.

---

### Post by switchrodeo720 on 2009-01-28
> I don't think a Virtual Box is a good test though, since it uses emulated hardware and not your real hardware, so the results would be completely different. Try booting the Fedora 10 Live CD and see what happens.

I agree. I just wanted to see if it would install. Usually the first advice I've seen given is to check to make sure the .iso download isn't corrupt. Installing on Virtual Box was a way to double check the disk's validity.

I'm positive it's some type of hardware incompatibility.

---

### Post by gukid on 2009-02-01
I think this issue may have been fixed, in some recent ubuntu 8.10 updates.  Was still running ubuntu 8.04 with xfce, and did the 8.10 upgrade (was bored) with full updates and it went through without a hitch.  No lock-up at the login screen, no lost devices.  I suppose I'd have to try a fresh install to find out for sure, but everything seems to be working (except wireless, which doesn't surprise me because it was always tricky to get working.)

---

### Post by switchrodeo720 on 2009-02-01
Great to hear. I think I'm going to wait until Jaunty is released for my next fresh install.

---

### Post by gukid on 2009-02-13
Guess I spoke a bit too soon.  In my excitement, decided to try a fresh install of Ubuntu 8.10 with all updates, and still getting the exact same problems.  Freezing with "processing" mouse cursor before login screen, or after removing compiz, no input devices.

Weird that something about installing Ubuntu 7.04, installing XFCE, and then updating to 8.10 through XFCE worked...  gnome even worked at that point...  wish I had wrote down everything I had done.

---

### Post by gukid on 2009-02-13
Made an interesting discovery...

For some reason, I was suspecting something was up with my wireless network card, so I took it out, and all problems went away...  was able to boot up without the system freezing, or losing input devices.  It's an rtl8185 that was in the other system as well, which worked fine.

Though, I went and changed the placement of my pci cards (has network card and this rtl8185 in the last 2 slots) and now it's working, WITH the rtl8185 in again, but it's not detecting it for wireless internet...  so it could have been an IRQ issue or something all along?  Still trying to figure it out now.

Just in:
Network Manager 0.7
Xubuntu 8.10 ships Network Manager 0.7 (by Dan Williams and others), which comes with long-expected features, such as:
* system wide settings (i.e., no need to log in in order to get a connection)

Locks up before the login screen, maybe right about when it's trying to detect the network settings?  I had removed the Network Manager and was using something else, so more than likely it was a conflict with my card/IRQ and the network manager, that was one of the new features in Ubuntu since 8.10.  Maybe as a suggestion to anyone having this problem, try removing it and using a different network manager like "wicd" to test.

---

