---
title: "how is xorg configured today"
date: 2009-09-22
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by sdowney717 on 2009-09-22
there is no more xorg.conf
so how is it done?

---

### Post by kansasnoob on 2009-09-22
Specifically what do you need to do?

---

### Post by sdowney717 on 2009-09-22
nothing, but I would like to know

---

### Post by Darkshade on 2009-09-22
Create one :)

---

### Post by JuergenF on 2009-09-22
Hardware today should be able to communicate its features to the system.

You only need a xorg.conf if you have problems (KVM-switches sometimes disturb this 'communication') or 'special' needs (Xinerama/Dualview, higher frequencies etc.). Then you just create one.

---

### Post by andrewabc on 2009-09-22
> **sdowney717 said:**
> there is no more xorg.conf
so how is it done?

So they completely got rid of xorg.conf?
For past couple releases (8.10?, 9.04) they simply had a blank one with no settings in it.

I have 5 button mouse, in past I have had to manually add several lines into xorg.conf to get two side buttons working. Where would I do this now, or is it auto detected and can be changed in system->preferences->mouse ?

I'll have to boot into karmic alpha 6 liveusb I have and see.

EDIT:
I'm using Jaunty and it recognizes my two extra mouse buttons and uses them as forward/back in firefox. And my xorg has no custom settings. But I don't see any options anywheres to customize my mouse buttons.

---

### Post by LKjell on 2009-09-22
eh.. I never did a fresh install of karmic. But are there no xorg file? I know that Fedora does not have the xorg file too. Kinda makes you frustrated when you want to change driver.

---

### Post by JuergenF on 2009-09-22
Oh, I didn't realize this question was for karmic.

But I don't think it is dependent on your DE now. It still should be possible to use your hardware if you use LFS++ with FVWM2 as DE.
So probably it is still: 'just create one' ;)

---

### Post by petteriIII on 2009-09-22
In the begining my laptop didn't boot into Karmic at all because it needed the: Option "DRI" "Off" in xorg.conf. But it was impossible to add because there wasn't any xorg.conf. Week ago I booted with Jaunty, CHROOTed into Karmic, copied Jaynty's xorg.conf into Karmic, edited newly copied xorg.conf and added the option. Then Karmic booted OK. 
Looks like Karmic operates allright without xorg.conf but it honors commands in it if there is xorg.conf.

---

### Post by barisurum on 2009-09-22
I think they should at least provide an xorg.conf-reserve or something, a draft xorg.conf file that could easily be changed to xorg.conf and edited in recovery mode when the system fails to boot.

---

### Post by jerrylamos on 2009-09-22
> **JuergenF said:**
> Hardware today should be able to communicate its features to the system.

You only need a xorg.conf if you have problems (KVM-switches sometimes disturb this 'communication') or 'special' needs (Xinerama/Dualview, higher frequencies etc.). Then you just create one.

JuergenF, hardware communicates its features to the system, all right, but in the case of 
"ATI" on two of my test pc's
and
"Intel" on two more of my test pc's
the alpha, beta, or even release code ubuntu xorg drivers fail sometimes for weeks or months.  Take a look at the plethora of launchpad bugs.

So I end up keying xorg.conf in by hand on CD Live, or after the usual dead screen install booting another image that still works and copying one in, ...  

Gets tiring.  Sure would help if ubuntu provided a scaffold xorg.conf.

Jerry

---

### Post by forumache on 2009-09-23
I create an xorg.conf just to be able to add Driver "nvidia" to it.
Otherwise, it starts the slow nv one.

```
dan@shuttle:~$ cat /etc/X11/xorg.conf
Section "Device"
	Identifier	"Configured Video Device"
	Driver		"nvidia"
	Option		"NoLogo"	"True"
	Option		"DynamicTwinview"	"False"
	Option		"RandrRotation"	"True"
EndSection

```
That's it, nothing more in xorg.conf

---

### Post by dinxter on 2009-09-23
try,
$Xorg -configure
to generate a xorg.conf
or
$xorg-options-editor-gtk 
to fancy add options

[EDIT] obviously you would need to have xorg-options-editor-gtk package installed for second option :)

---

### Post by dinxter on 2009-09-23
sorry, Xorg -configure

-configure
               When  this option is specified, the Xorg server loads all video
               driver modules, probes for available hardware, and  writes  out
               an  initial xorg.conf(5) file based on what was detected.  This
               option currently has some problems on some  platforms,  but  in
               most  cases  it  is  a  good way to bootstrap the configuration
               process.  This option is only available when the server is  run
               as root (i.e, with real-uid 0).

---

### Post by VMC on 2009-09-23
> **sdowney717 said:**
> there is no more xorg.conf
so how is it done?

Somewhere I read that it uses a "default" one. I didn't know either what that meant. I'm guessing it comes come the kernel. Or the kernel supplies it.

---

### Post by dinxter on 2009-09-23
> **VMC said:**
> Somewhere I read that it uses a "default" one. I didn't know either what that meant. I'm guessing it comes come the kernel. Or the kernel supplies it.
xorg autodetects settings unless you have /etc/X11/xorg.conf in which case it uses that instead, see above for generation of a 'default' xorg.conf

---

### Post by doas777 on 2009-09-23
> **VMC said:**
> Somewhere I read that it uses a "default" one. I didn't know either what that meant. I'm guessing it comes come the kernel. Or the kernel supplies it.

the file is just a stub, with almost nothing in it.

it's my understanding that the enviroment is auto-confed from a series of tools. xrandr for video etc.

---

### Post by Simian Man on 2009-09-23
On the new X server which is used by Fedora and, apparently, Ubuntu now too, you don't need an xorg.conf, but [one can be created easily]("https://fedoraproject.org/wiki/How_to_create_xorg.conf") if you wish.  Also, when I install the nVidia drivers on Fedora, an xorg.conf is generated and I imagine Ubuntu would do simlar when you install restricted drivers for your hardware if special settings are needed.  You definitley shouldn't need to type one out from scratch!

---

### Post by VMC on 2009-09-23
> **dinxter said:**
> xorg autodetects settings unless you have /etc/X11/xorg.conf in which case it uses that instead, see above for generation of a 'default' xorg.conf

I wasn't referring to default as when you create using  Xorg -configure. That's why its in quotes. When xorg.conf is missing as the poster was questioning, what is used. What drives the display. Maybe doas777 has answered that.

---

### Post by dinxter on 2009-09-23
> **VMC said:**
> I wasn't referring to default as when you create using  Xorg -configure. That's why its in quotes. When xorg.conf is missing as the poster was questioning, what is used. What drives the display. Maybe doas777 has answered that.
yep, sorry, i realised that just after i posted it, not paying attention too well :) i should know by now i can't multitask

[EDIT] /know/now/ seems i cant type either!

---

### Post by sdowney717 on 2009-09-23
issue was I had done a distribution upgrade to karmic and my video was so screwed, images were upside down and mirrored.
Only fix I found was a format and new install.

One poster said I was using the NV driver and my video card is an ATI, so I questioned why it was not auto configuring properly.

note the picture i took with a phone.
[http://ubuntuforums.org/showthread.php?t=1269091](http://ubuntuforums.org/showthread.php?t=1269091)

---

