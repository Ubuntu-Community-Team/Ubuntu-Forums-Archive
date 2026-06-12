---
title: "VNC on a no monitor server"
date: 2010-05-03
forum: Installation &amp; Upgrades
---

### Post by plunderisley on 2010-05-03
I'm trying to get a remote viewer / VNC on a PC without a monitor. The default one that comes with it seems it wont work without a monitor attchched (including that every time I connect, it asks me to enter the keyring password)
Is there a way to get VNC server installed that it will mirror my desktop?

---

### Post by plunderisley on 2010-05-04
Hmm I tried vnc4server, but I cant get it to load the screen I'm logged in on.  It just shows a blank grey screen with a terminal...

---

### Post by lavinog on 2010-05-04
A headless server is another way to describe your setup (if you need to google stuff)

You might not need to be using vnc...What are you wanting to accomplish? (What will the server be used for?)
You can forward gui apps through ssh
install openssh-server on the server
connect to it using
```

ssh -X serverip

```
then try running a gui app like xclock from the terminal.

Is it asking the keyring password to connect to the internet?

---

### Post by plunderisley on 2010-05-05
It asks for a keyring everytime I RealVNC into the server on the server.

All I want to do is run a remote assistance type program that I can take control of the current desktop. I dont want to start a new user or a new session, but just use the current session that the server is logged into.
I got a few GUI apps running (like a ps3 media server) that would be good to reset, and the built in gnome remote app doesn't work without the monitor including that it keeps asking me for that keyring password. I tried changing it to a blank password, but no luck.

---

### Post by lavinog on 2010-05-05
Under remote desktop preferences there is a setting under security: "configure network automatically to accept connections."

---

### Post by plunderisley on 2010-05-05
Hmm, it does not want to boot up at all without a monitor...

EDIT:
I got it to boot, but I cant remote connect in without the monitor plugged in. When I restart, with the monitor plugged in, it works just fine (without the keyring thing now - Thanks). 
How can I make it think theres a monitor plugged in?

---

### Post by eohlde on 2010-05-05
checking 'configure network to automatically accept connections' didn't work for me. 
plunderisley, did you do something else to get it to work?

---

### Post by plunderisley on 2010-05-06
well, with tht emonitor plugged in, I have that checked and I also removed the password from the keyring. Applications - accessories - passwords and encryption keys. rt click on it and change password to blank.

Next step I think is to force 1024x768 resolution at all times even when the monitor is not plugged in. I think that'll fix it.

---

### Post by plunderisley on 2010-05-07
OK I got it to work without a monitor, but it keeps loading in 800x600 mode, even though the xorg.conf is 1024x768

below is a the code

```

Section "Monitor"
	Identifier	"Configured Monitor"
    Modeline        "1024x768"  108.88  1280 1360 1496 1712  1024 1025 1028 1060  -HSync +Vsync
    Option          "PreferredMode" "1024x768"
EndSection
Section "Device"
	Identifier	"device0"
	Driver		"nv"
	VendorName " NVIDIA Corporation"
EndSection
Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	SubSection "Display"
	Depth 24
	Modes		"1024x768"
EndSubSection
EndSection

```

---

### Post by lavinog on 2010-05-07
If this is going to be a headless system you might want to use the mesa drivers.
I think there is an issue with nvidia drivers and KMS that might be the cause of your issue.

---

### Post by Ceyx on 2010-05-08
I had the same problem. Remote desktop worked fine "headless" ( without monitor ) but after upgrade to 10.04 I couldn't get it to boot all the way.

I built a VGA loopback adapter to fool the remote computer into thinking it had a monitor attached when in fact it does not.

See the VGA pinout on this page : [http://pinouts.ru/Video/VGA15_pinout.shtml](http://pinouts.ru/Video/VGA15_pinout.shtml)

I used a quick and dirty method. I got three 100 ohm resistors ( Radio Shack ) and bent them so that one resistor went from pin 1 to 6, another from pin 2 to 7 , and finally the last resistor from pin 3 to 8. 

No soldering required - just bent the leads and jam them in.  Perhaps some hot glue may be good too, if you have pets or small kids.

This fix makes my video card think it has a monitor capable of 1024 * 768 attached to itself. Hah !

Needless to say, if you follow this advice you are on your own if you smoke your card.  Paper clips may work, but may wreck your card...

---

### Post by pmla on 2010-06-15
Having the same problems... trying to remote desktop connect to 10.04 without a screen. Google and googled. Waist of time and patient.

I congratulate you, ingenious solution. But how stupid is a system that one as to go so far just to get a freaking simple remote desktop connection??????
shhhh there is still a lot to be learned from other systems... Sorry to say, linux and ubuntu suck when it comes to anything related to graphical.

For me this is N.1 in sloppiness



> **Ceyx said:**
> I had the same problem. Remote desktop worked fine "headless" ( without monitor ) but after upgrade to 10.04 I couldn't get it to boot all the way.

I built a VGA loopback adapter to fool the remote computer into thinking it had a monitor attached when in fact it does not.

See the VGA pinout on this page : [http://pinouts.ru/Video/VGA15_pinout.shtml](http://pinouts.ru/Video/VGA15_pinout.shtml)

I used a quick and dirty method. I got three 100 ohm resistors ( Radio Shack ) and bent them so that one resistor went from pin 1 to 6, another from pin 2 to 7 , and finally the last resistor from pin 3 to 8. 

No soldering required - just bent the leads and jam them in.  Perhaps some hot glue may be good too, if you have pets or small kids.

This fix makes my video card think it has a monitor capable of 1024 * 768 attached to itself. Hah !

Needless to say, if you follow this advice you are on your own if you smoke your card.  Paper clips may work, but may wreck your card...

---

### Post by CharlesA on 2010-06-15
If you want it to mirror your desktop, you will need to set it to logon automatically, since vino doesn't start unless you are logged in. First connection it will ask for your keyring password, but after that just whatever password you set.

Otherwise you can use a different vncserver (I've used tightvnc), but that creates it's own "virtual desktop."

Use whatever works for you. :)

---

### Post by pmla on 2010-06-15
My system is in autologin. My tightvnc asks for the remote desktop password... :) after inserting it...no screen is displayed.

in 9.10 it worked easelly. I could actually edit the xorg.conf and set it like this, not out of the box but it worked.
sudo nano /etc/X11/xorg.conf

Section "Device"
Identifier "VNC Device"
Driver "vesa"
EndSection
 
Section "Screen"
Identifier "VNC Screen"
Device "VNC Device"
Monitor "VNC Monitor"
SubSection "Display"
Modes "1024x768"
EndSubSection
EndSection
 
Section "Monitor"
Identifier "VNC Monitor"
HorizSync 30-70
VertRefresh 50-75
EndSection


This is one of those things that should be just OUT OF THE BOX... the freaking BOX is blind :)


> **CharlesA said:**
> If you want it to mirror your desktop, you will need to set it to logon automatically, since vino doesn't start unless you are logged in. First connection it will ask for your keyring password, but after that just whatever password you set.

Otherwise you can use a different vncserver (I've used tightvnc), but that creates it's own "virtual desktop."

Use whatever works for you. :)

---

### Post by lavinog on 2010-06-17
This thread seems to have separate issues on it.
The nvidia doesn't support the opensource nv driver.  What nvidia expects you to do is to install the proprietary nvidia drivers with the hardware drivers app.

@Ceyx:  If your system is requiring a loopback cable to function properly, you should file a bug report.  It would also be beneficial to everyone if you mention what video card you are using.

For the issue with keyring requiring a password:  A bug report has been filed: [https://bugs.launchpad.net/ubuntu/+source/vino/+bug/562423](https://bugs.launchpad.net/ubuntu/+source/vino/+bug/562423)
Note: post #11 explains how to fix the issue.

---

### Post by emaro on 2010-07-13
Hello all, yesterday i upgrade to 10.4 and i can't use vino in a machine without monitor. I googled and this works for me (my pc has an ati card):

Disabling KMS:

# ATI Radeon:
echo options radeon modeset=0 > /etc/modprobe.d/radeon-kms.conf

After this all works fine.

This is the source web:
[https://wiki.ubuntu.com/X/KernelModeSetting](https://wiki.ubuntu.com/X/KernelModeSetting)

Thanks - Elias

---

### Post by pmla on 2010-07-13
Not that easy. You also have to delete vino password from the keyring manager. If you don't do this next time you restart your machine you won't be able to remote desktop it.

I eventually fixed it this way. Some things are just pre-history and far away from OUT OF THE BOX.

---

### Post by Ceyx on 2010-11-20
"@Ceyx: If your system is requiring a loopback cable to function properly, you should file a bug report. It would also be beneficial to everyone if you mention what video card you are using."

I haven't had much luck with bug reports - is it me ? ;)

Any VGA card with a 15 pin DSub connector should work with the "resistor" method, but it happened to be an ATI card.

Regards

---

### Post by a904guy on 2011-06-12
I've found a solution to the highest resolution 800x600 using the vesa driver. You can use the dummy driver in xorg to get a full list of supported resolutions to use in a headless VNC

[http://blog.mediafederation.com/andy-hawkins/ubuntu-headless-vnc-vesa-800x600-fix/]("http://blog.mediafederation.com/andy-hawkins/ubuntu-headless-vnc-vesa-800x600-fix/")

---

