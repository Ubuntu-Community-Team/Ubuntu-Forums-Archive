---
title: "System hangs on GUI Installer / Desktop boot"
date: 2015-10-12
forum: Installation &amp; Upgrades
---

### Post by peter169 on 2015-10-12
Hi

I have a problem which started (I think) since the first unity version of ubuntu.

The system is an [INDENT]AMD Athlon XP 2200+
753664K Memory + 32MB Shared
41GB HDD Dual boot with Win XP
[/INDENT]

The problem is that when I try boot from an ubuntu (or lubuntu or xubuntu; all version 14.04.2) desktop disk, the system boots (running through the general boot process as seen by pressing esc. when the splash screen comes on) but then gets to a point where it just hangs. A message comes up on screen saying "No Signal Input or Cable disconnected or Power saving". The system can't be reset using ctrl-alt-del, only the reset button.

When I first got this problem I thought ubuntu desktop (with unity) needed 512MB RAM but later decided it needed 1GB (documentation can be a little misleading.. or maybe it's me).
Once I decided it was 1GB I tried xubuntu and lubuntu and had the same problem.
When those didn't work I tried the lubuntu alternate install disk (unfortunately the only one left now, after a lot of frustrated searching I realised this) and the install booted and ran without a problem.
Unfortunately, as I thought might happen, when I tried to boot the installed system the same problem came up.

I think the most recent version which I didn't have the problem with was either 10.04 or 10.10 so I suspect the problem may have been introduced at the same time as unity (11.04).
I do have an old 9.04 disk and this works fine.

As a last note, the messages during boot seem okay.
Is this one a problem:[INDENT][   16.405546] via-ircc 0000:00:11.0: device not available (can't resolve [io 0x4000-0x407f])[/INDENT]
Think it's the sound card
Or this one:
[INDENT]Starting Reload cups, upon starting avahi-daemon to make sure remote queues are populated     [OK]
Starting Reload cups, upon starting avahi-daemon to make sure remote queues are populated     [fail][/INDENT]
All others [OK]

---

### Post by peter169 on 2015-10-12
I have an update. Didn't try it before, switched to a different session (ctrl-alt-f1) and it worked so seems it's the gui.
Tried nomodeset (e in grub menu then replaced quiet splash with nomodeset), that didn't work.
Also tried noapic and nolapic in the same place (don't know if that is right), didn't work.

If it's the graphics card would it need firmware? I'd think I could install it manually in a separate session terminal but I wouldn't know which firmware to get as the names can be pretty obscure. Google I guess

---

### Post by grahammechanical on 2015-10-12
Question: When you install do you tick the box "Install this third party software?" If you do, then as well as getting some proprietary video & audio codecs you are also getting a proprietary video driver. The owners of proprietary video drivers have a habit of dropping support for older versions of their video cards. Newer versions of Ubuntu come with later versions of proprietary video drivers. This explains why Ubuntu 10.10 worked but 14.04 does not.

When we run a live session we use the open source video driver. So, if the live session works but an installed session does not. Then it most likely will be down to the proprietary video driver not having support for that video card. Try installing without ticking the box "Install this third party software."

Another thing to keep in mind regarding Ubuntu and Unity is that we need a video card that can do accelerated 3D video rendering in hardware. Otherwise the rendering has to be done by the CPU. The video adapter should also have its own memory and not have memory shared with the OS. I would question the usefulness of a video adapter with 256 KB memory in running Unity. I think that 512 KB is much better but 1 GB video memory is much, much better.

You should stick to Lubuntu and consider installing without ticking the box "Install this third party software." After you get a working desktop you might be able to install an older proprietary video driver that dates from the time of Ubuntu 10.10.

Regards.

---

### Post by peter169 on 2015-10-13
Thanks, there's some good info in here that may help me fix the problem.
I'm guessing I wasn't clear so let me try again. When the gui installer is busy booting it hangs. It seems to be only the Installer hanging as I can switch to a different session (ctrl-alt-f1.. actually I tried this later, not with the installer but I'm guessing this would be with the installer too) but this (of course) would mean that the installer never comes up and so the "Install this third party software?" box doesn't either.
The only installer that boots is the non-graphical installer on the lubuntu alternate disk, I don't think the alternate installer has a "Install this third party software?" option. Is that right?
Once installed using the non-graphical alternate installer lubuntu still hangs in the same way when booting to the desktop (this is where I tried ctrl-alt-f1).

I'm quite happy to use lubuntu or xubuntu.

I think I covered everything you said. Hope that's clearer

---

### Post by sudodus on 2015-10-13
I think your problem is caused by poor cooperation between the graphics driver and the graphics chip/card. And as *grahammechanical* wrote, an older version of linux may have a driver that works better with your graphics chip/card.

The oldest version of Ubuntu that is supported is 12.04 LTS. There are light-weight community 're-spins' based on this version, that promise support until April 2017. (Standard Ubuntu is also supported but needs more memory and horsepower.) So you can try ***Bento, Bodhi and LXLE***.

If there are problems also with these re-spins of 12.04 LTS, I suggest that you try ***Wary Puppy, TahrPup and Tiny Core***, which are extremely light-weight and made for old hardware, but still supported.

See this link for more details: [Old hardware brought back to life](http://ubuntuforums.org/showthread.php?t=2130640)

---

### Post by peter169 on 2015-10-13
Good advice, gotcha.

I'll check them out, gonna take me awhile.

Seems Bento may not be easy to get to but was just a quick look.
I'll look more

---

### Post by sudodus on 2015-10-13
[http://bentovillage.org/bento/bento-precise/](http://bentovillage.org/bento/bento-precise/)

[http://linuxvillage.org/](http://linuxvillage.org/)

---

