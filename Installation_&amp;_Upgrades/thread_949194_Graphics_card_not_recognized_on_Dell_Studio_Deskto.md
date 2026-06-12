---
title: "Graphics card not recognized on Dell Studio Desktop?"
date: 2008-10-15
forum: Installation &amp; Upgrades
---

### Post by rujith on 2008-10-15
I'm trying to run Ubuntu 8.0.4 off a CD on a Dell Studio Desktop. The
start-up goes fine, but when it's about to start X (or thereabouts),
the VGA display just goes blank.

The Dell Studio Desktop has an Integrated Intel GMA X4500HD graphics
card, with two outputs at the back: HDMI and VGA. I've connected a VGA
monitor; I don't have an HDMI-capable display. I'm wondering whether
Ubuntu is trying to output just HDMI via the graphics card?  That does
seem unlikely, however.  More likely is that the graphics card is not
supported.

Here's more details of what I'm doing:

Machine: Dell Studio Desktop
Intel Core 2 Duo Processor E7200
Integrated Intel GMA X4500HD Graphics

Booting Ubuntu 8.0.4, x86, normal desktop off a CD.

Boot parameters: deleted "quiet splash --" and added
"all_generic_ide".

Boot using the option "Try Ubuntu without changing
your computer."

I also tried various other options, such as Safe Graphics display,
noapic, nolapic, aic7xxx.aic7xxx=no_probe. None of those helped.

Anyway, Ubuntu starts booting, spits out a whole bunch of messages,
upto:

Starting GNOME display manager
Starting atd
Starting crond
Checking battery state

And then my VGA display just goes blank.

Any help would be appreciated on how to complete the boot. Somebody's
got to have figured out how to run Ubuntu on these new Dell Studio
Desktop machines!

Thanks,
Rujith de Silva.
[http://rujith.com/](http://rujith.com/)

---

### Post by pelle.k on 2008-10-19
Yeah, the graphics card is unsupported in hardy, unless you manually install it, which is a bit painful.
I suggest you wait another two weeks and install ubuntu 8.10 (intrepid ibex), should be supported there.

You could of course run it using "vesa" driver instead. First, boot it in "recovery" mode. Then run "Xorg -configure".
That should leave you with a config file in /root.
Make a backup of xorg.conf if you wish, "cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup"
Copy the created xorg.conf, "cp /root/xorg.conf* /etc/X11/xorg.conf"
Open it up with nano, "nano /etx/X11/xorg.conf"
Change *driver* in *device* section to "vesa". Then save and close with ctrl+x and press "y".
Reboot, and try as you would normally.

Keep in mind, the "vesa" driver pretty much sucks though, and it's not meant for everyday desktop usage really.

---

### Post by rujith on 2008-10-19
Okay, glad it's a known issue.

Can I boot off the Live CD into "recovery" mode, as you suggested?
I don't see an option to do that.  The furthest I've got is
a blank VGA screen (after using all_generic_ide), or the initramfs
shell prompt (without using all_generic_ide).

- Rujith.

---

### Post by pelle.k on 2008-10-20
Oh, i thought you had installed it already, cause then you could boot it in recovery mode.
Try the "alternate" install cd, it uses a no (pretty) graphics install mode. Should install just fine, as long as there are no other problems other than your video card.

---

### Post by rujith on 2008-10-20
Cool.  I'll probably just try Ibex instead.  I don't mind running the beta
for a couple of weeks until the release.

---

### Post by pelle.k on 2008-10-20
OK. good luck :)
It should be *fairly* stable, since it's mostly "frozen" by now. Only heavy bugfixing left until release. The ReleaseCandidate is supposed to be out this thursday - i'm going update as well.

---

### Post by tomcogc on 2011-01-13
> **rujith said:**
> I'm trying to run Ubuntu 8.0.4 off a CD on a Dell Studio Desktop. Thestart-up goes fine, but when it's about to start X (or thereabouts),the VGA display just goes blank.The Dell Studio Desktop has an Integrated Intel GMA X4500HD graphicscard, with two outputs at the back: HDMI and VGA. I've connected a VGAmonitor; I don't have an HDMI-capable display. I'm wondering whetherUbuntu is trying to output just HDMI via the graphics card? That doesseem unlikely, however. More likely is that the graphics card is notsupported.Here's more details of what I'm doing:Machine: Dell Studio DesktopIntel Core 2 Duo Processor E7200Integrated Intel GMA X4500HD GraphicsBooting Ubuntu 8.0.4, x86, normal desktop off a CD.Boot parameters: deleted "quiet splash --" and [[COLOR=#000000]added[/COLOR]](http://www.violetin.net/de/health/health-insurance-the-impact-of-malpractice.html)"all_generic_ide".Boot using the option "Try Ubuntu without changingyour computer."I also tried various other options, such as Safe Graphics display,noapic, nolapic, aic7xxx.aic7xxx=no_probe. None of those helped.Anyway, Ubuntu starts booting, spits out a whole bunch of messages,upto:Starting GNOME display managerStarting atdStarting crondChecking battery stateAnd then my VGA display just goes blank.Any help would be appreciated on how to complete the boot. Somebody'sgot to have figured out how to run Ubuntu on these new Dell StudioDesktop machines!Thanks,Rujith de Silva.[http://rujith.com/](http://rujith.com/)Nice writing, Thanks for your analysis!

---

