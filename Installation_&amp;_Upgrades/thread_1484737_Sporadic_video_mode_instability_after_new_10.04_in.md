---
title: "Sporadic video mode instability after new 10.04 installation"
date: 2010-05-16
forum: Installation &amp; Upgrades
---

### Post by Chris J on 2010-05-16
After an upgrade failure, I went ahead and did a clean install of 10.04. Everything worked pretty well until I tried to change the screensaver. Then the display spontaneously dropped out of X and then flickered between a blank screen and alphanumeric display. I could not break it out of this without shutting down the system and restarting. The problem is consistent -- happens every time I attempt to change the screensaver. It also fails in the same mode when trying to use Stellarium, and failed once for no particular reason that I could see.

The system is an old H-P Pavilion 542x with a mx70 display. Not sure what the graphics card is. The system is duel-boot with Windows XP on the other side, which I seldom use but has no similar problems. Nor did I see this with Koala so I'm pretty sure it is new with the 10.04 installation. 

If anyone has any suggestions I'd appreciate them. I'm a little timid about using the system for anything serious until the problem is resolved.

---

### Post by Catharsis on 2010-05-16
Sounds like a problem with your graphics card driver. What card do you have?
```
lspci | grep VGA
```

---

### Post by Chris J on 2010-05-16
Re: graphics card: Thanks for telling me how to find that out.

VGA compatible controller: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 01)

---

### Post by Catharsis on 2010-05-16
Some stuff to try:

1) Hold down Shift while booting to enter the grub menu.
2) Press 'e' to edit and remove "quiet splash".
3) Ctrl+x to boot.

If that doesn't fix it, reboot and try this instead:
2) Press 'e' to edit. Replace "quiet splash" with "i915.powersave=0".

I *think* I remember that being a graphics fix for i845 users. Not sure though. It won't save though, so you can try it risk-free (if it works, I can show you how to make it permanent).

Also see:
[https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes](https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes)
Works mostly for i855 cards; I'd be curious how they work for i845 as well.

---

### Post by Chris J on 2010-05-16
> **Catharsis said:**
> Some stuff to try:

1) Hold down Shift while booting to enter the grub menu.
2) Press 'e' to edit and remove "quiet splash".
3) Ctrl+x to boot.

-- This didn't work. 

If that doesn't fix it, reboot and try this instead:
2) Press 'e' to edit. Replace "quiet splash" with "i915.powersave=0".

-- Neither did this. 

I *think* I remember that being a graphics fix for i845 users. Not sure though. It won't save though, so you can try it risk-free (if it works, I can show you how to make it permanent).

Also see:
[https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes](https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes)
Works mostly for i855 cards; I'd be curious how they work for i845 as well.

-- I'm looking at that thread now and may try those fixes later, although it looks like they have some tradeoffs and may be a bit harder to back out of if they don't work.

Thanks for your suggestions, though.

One more thing: it looks like after the crash settles down the monitor is going into power-saving mode, so maybe your last suggestion is pointing in somewhat the right direction.

---

### Post by Catharsis on 2010-05-16
I remember hearing a lot about monitors going to sleep on 10.04. I think this is just a side-affect of an X Server crash (the graphics goes down, so nothing goes to the monitor, so it just shuts off too, like it does when the computer shuts down). Still, it'd be worth searching google and the forums for stuff.

Re: link-- Workaround A works for the VAST majority of i855 users, so it might work for you too. Enable it through grub first to try it, and then you can make it permanent by entering the terminal command if it works. Also, I'm almost positive upgrading to the mainline kernel will fix your problem.

---

### Post by Chris J on 2010-05-17
I tried Workaround A; it did not help. Unfortunately I tried it as suggested in the referenced thread before I saw your last reply. Could you suggest a way to reverse the process?

Also, I can try the mainline kernel as described in the thread but would like to have a way to back out ready at hand, in case of unforeseen problems. 

As you can probably tell, I can find my way around in the terminal window but am far from a Linux expert.

Thanks for your help.

---

### Post by Catharsis on 2010-05-17
> **Chris J said:**
> I tried Workaround A; it did not help. Unfortunately I tried it as suggested in the referenced thread before I saw your last reply. Could you suggest a way to reverse the process?
The terminal command at the top? You can reverse it with:
```
sudo rm /etc/modprobe.d/i915-kms.conf
sudo update-initramfs -u
```

> **Chris J said:**
> Also, I can try the mainline kernel as described in the thread but would like to have a way to back out ready at hand, in case of unforeseen problems.
You can choose which kernel to boot into in GRUB. Just hold down Shift while booting to get there. If you don't like the mainline, just go to GRUB and choose a different kernel.

If you want to remove it, just boot into a different kernel, go to Synaptic, search "2.6.34", and mark the image and headers for Complete Removal and then Apply. Super easy.

---

### Post by Chris J on 2010-05-17
OK, well, I'm confused now. But it still doesn't work right; I'm sure of that.

I went back and undid Workaround A using your suggested procedure. No problem there. Then I re-tested your first two suggestions having to do with GRUB (post #4) and the problem was still there with Stellarium, but the system seemed much more stable when working with the screensaver utility. Then I rebooted into what should be my original configuration and the screensaver settings works OK. Graphics still didn't work with Stellarium at all though.

So I went and got the mainline kernel and tried it. Same thing. Stellarium crashes video right away, and sometimes the screen goes alpha and blanks out for no reason, with no way to break out of it except to reboot. So I'm pretty sure the mainline kernel didn't help. I'll leave it in there for now, though, since you reminded me I can pick the kernel in GRUB. By the way, the system is dual-boot with Windows XP, so GRUB appears with every boot. I just have to pay attention during boot if I don't want the last installed kernel. 

Any other suggestions would be welcome.

---

### Post by Catharsis on 2010-05-17
Sounds like a problem with the Stellarium application. It might be worthwhile to look at its compatibility with Lucid Lynx or use their forums/bug-trackers.

---

### Post by Chris J on 2010-05-18
> **Catharsis said:**
> Sounds like a problem with the Stellarium application. It might be worthwhile to look at its compatibility with Lucid Lynx or use their forums/bug-trackers.
I'll look into Stellarium more. But their website/bug tracker indicates that it has been tested with Lucid. 

Anyway, Stellarium aside, the video does occasionally crash just at random times; for example, when reading mail or using Firefox or sometimes if I just linger on a menu for awhile.

---

### Post by bobmckenzie123 on 2010-05-18
Hi,

I don't think it's a Stellarium issue because I'm in the same boat.  I've been using ubuntu since 8.04 on my old IBM Netvista that uses the same on-board Intel chipset.  Back then I was using Compiz and I was also developing a Quake 3-esque game using OpenGL.  I upgraded to 9.04 and everytime I tried to run my little program the screen would flicker and then go black.  I couldn't even use Compiz or even set my Visual Effect (under Appearance Preferences) to anything but None.  I read there were issues with the new architecture and 8 series intel video chipsets and I really didn't have the time nor drive to figure it out.

When 10.04 came out I was hoping things would be different so I installed last week.  I've been trying to use Blender 2.5 but the same thing as before is occurring.  When I try to bump up my Visual Effects to Normal I get a little dialog saying something along the lines of 'Searching for drivers' and then it just says Visual Effects cannot be enabled.

It looks like we are going down the same path.  I tried solution A in the link in the post above, with the same result.  Then I tried the Grub mods (however I did it right in the /etc/default/grub file) and other than actually seeing the console on bootup, the same results when starting blender 2.5.

I could have sworn that I read that up until 9.04 all intel cards used the xserver-xorg-video-i740 driver.  Starting with 9.04 it's using xserver-xorg-video-intel.  Would it be possible/helpful to change the driver back to 740?  If so, how do you do that?  Or before attempting this should I keep going with the remainder of the solutions from the above link?

Let me clarify though, video playback (except for HD) is pretty good.  My system is very stable.  It's just when I try to do anything that is OpenGL related my screen flashes and then goes black.

Thanks,

---

### Post by Chris J on 2010-05-18
I am also unable to enable Visual Effects, see the same messages. I have just ignored it up to this point but I guess it may be a related issue. Nice to find someone in the same boat (misery loves company).

For some reason, my system has stabilized a little in the last day or so. I can't say that I've done anything to account for it. It does still flicker and die once in awhile though.

---

