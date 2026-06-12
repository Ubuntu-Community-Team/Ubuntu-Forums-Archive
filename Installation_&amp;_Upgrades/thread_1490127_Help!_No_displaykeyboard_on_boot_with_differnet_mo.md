---
title: "Help! No display/keyboard on boot with differnet monitor"
date: 2010-05-21
forum: Installation &amp; Upgrades
---

### Post by n2bnt2 on 2010-05-21
Hi,

I setup 10.04 on an older Athlon XP 3000+ ASUS A7N8X board with a Radeon RV250 video card. It works fine and dual boots with XP on the LCD monitor I have.

I took it to my mom's an connected to a iiyama Vision Master 450 CRT. When I boot, I get the grub menu, and if I pick Windows XP, it boots fine. If I pick Ubuntu, the screen goes blank, as small underline cursor appears at the top left, and then the monitor goes into sleep mode and the keyboard is no longer responsive.

I cannot seem to gain access. I cannot hit CTl-ALT-F2 (or ALT-F2) to get to text login (screen is sleeping and no keyboard control).

I tried Live CD, it shows a graphic at the bottom of the screen and then goes blank as well!

Seem like something with monitor resolution, but I cannot seem to figure out how to force it to work. I can't seem to figure out how to get into command line mode on boot either.

Can someone advise? I only have a few days to get this going, before I have to leave.

I'm by no means a wiz with Ubuntu, having only used it for a year now and am learning as I go.

Thanks!

PCM

---

### Post by emanuel.b on 2010-05-21
Are you connecting it by VGA, or S-Video? I've only heard of this happening because of a graphics card issue. But if it was S-Video, maybe, just maybe, it could have messed up your graphics driver. Have you been able to connect it to a different monitor?

---

### Post by n2bnt2 on 2010-05-22
It is connected via the standard video connector.

When I set this up originally, I had it connected to a new LCD monitor. Now, I have an old CRT connected.

When I boot to Windows, it comes up fine. When I boot to Ubuntu, there is a point where the display shuts off. I don't get the login screen at all.

If I boot from the 10.04 Live CD, I see the little icon at the bottom of the screen (human and keyboard?) and then same, thing cursor and then blank screen.

If I boot from a 9.10 (recovery) CD I have, I get the low res video asking to try or install, and when I click choose try Ubuntu, I get a "glowing" Ubuntu circle as it accesses the CD and then I get the same blank screen. However, I can do CTL-ALT-F2 and get a command prompt.

It "seems" like when it switches to higher rez graphics, it doesn't work with this monitor, whether I'm booting what is installed or using LiveCD.

I'm at a loss as to how to resolve this.

Unfortunately, I don't have access to another monitor at this location.

I'm at a loss as to why it works with one monitor and not another. Especially, when using the LiveCD.

Any ideas?

---

### Post by dino99 on 2010-05-22
kind of xorg.conf issue, as lucid dont need it by default you can remove it:

sudo rm -f /etc/X11/xorg.conf

sudo apt-get install -f
sudo dpkg --configure -a

---

### Post by n2bnt2 on 2010-05-23
I got a hold of another monitor (Dell 17" LCD), booted the system, chose Ubuntu (default), it came up just fine as expected.

I'll take a look to see if there is an xorg.conf file there.

What is really perplexing is that even the LiveCDs don't boot up. I would have thought they would be set to use the lowest common denominator for a display. I guess this display is below that :^)

PCM

---

### Post by dino99 on 2010-05-23
sudo update-pciids && update-usbids

---

### Post by n2bnt2 on 2010-05-23
I got around it with a different monitor, but just for future reference, can you elaborate on what the commands do?

Do they re-identify the devices connected to the system?

Would I typically do that whenever I connect new devices, if I was having problems with them?

In this case, where I cannot boot from a liveCD or normally, would I have to try to boot to command line mode and then invoke the commands?

I found that with Karmic, I could boot and do CTL-ALT-F2 to get command line. Is there any other way to do that in Lucid (as the CTL-AlT-F2 didn't work, nor did other combinations)?

Sorry for all the questions, but I'm wondering how I get out of that situation in the future.

Thanks in advance.

PCM

---

