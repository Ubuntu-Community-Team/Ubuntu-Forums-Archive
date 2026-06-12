---
title: "Minimize-Mazimize and color problems"
date: 2009-02-10
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by Nixie Pixel on 2009-02-10
Hello, today after solving my boot-to-black-screen problem, I have suddenly lost the minimize, maximize, and close window buttons in the upper right of every window.  According to some searches here in the forums there may be an issue with Compiz, so I tried to check my settings there.

Then I saw the second problem, some sort of text color issue so that I can't see the Compiz settings to check them.

Any idea what could be going on?

Thanks!

---

### Post by ronacc on 2009-02-10
sounds like a window decorator problem , if you are using compiz try switching decorators , you can do that with fusion-icon . or try switching between compiz and metacity .

---

### Post by philinux on 2009-02-10
Yep turning off compiz gets the min max and close buttons to be visible. I'm still using compiz as the buttons work. They're just not visible.

---

### Post by Nixie Pixel on 2009-02-10
Thanks - perhaps you can tell me how to do that in the terminal?  I can't see the options on the GUI because of the text color problem.

Compiz is causing the text colors to be unreadable as well?

(See the screenshot in my post above for details)

---

### Post by ronacc on 2009-02-10
what decorator are you using with compiz ? gtk or emerald ? if emerald check your buttons with emerald theme manager , emerald settings>edit themes>titlebar .

---

### Post by ronacc on 2009-02-10
metacity --replace   to change from compiz to metacity .

---

### Post by taavikko on 2009-02-10
> **Nixie Pixel said:**
> Thanks - perhaps you can tell me how to do that 
Compiz is causing the text colors to be unreadable as well?

(See the screenshot in my post above for details)

Theme in use Darkroom I presume, there's bug, concerning text visibility.
Switch to alternate theme. and text should be readable.

---

### Post by Nixie Pixel on 2009-02-12
Thanks, everyone.

Yes, I am using Darkroom - it seems this bug has been around for a while.  How do I check when it will be fixed?

I used metacity --replace to switch to metacity for a while.  This worked well to avoid the missing buttons/titlebar.  It seems that compiz has been recently updated so I want to test and see if the changes have fixed my issues.

However, when I enter compiz --replace at the prompt after keying ALT-F2, it doesn't seem to switch to compiz.  In my session manager I still see metacity running, and no compiz, even after a reboot.

Any idea why compiz is not restarting after entering compiz --replace?

(Also, I tried the metacity --replace and compiz --replace in the terminal, but that just hung my terminal session.  Would someone please explain to me what the difference between entering these commands after ALT-F2 and in the terminal is?)

Thanks!

---

### Post by praxis22 on 2009-02-12
This used to happen to me all the time, but I seem to recall doing:

compiz --replace emerald

I think.

Allowed me to load the emerald windows decorator. 

You may want to check, haven't fixed by grub environment since I rebuilt my PC a few months back, or I'd go in and dig out the commands.

---

### Post by Gourgi on 2009-02-12
you could try installing "fusion-icon" package
it is what i use to switch between metacity and compiz on-the-fly
also it is said to have a _proper_ way of starting compiz.

as for your decorator problem try "emerald"

---

### Post by ronacc on 2009-02-12
also you don't have to use alt>F2 to run compiz --replace you can do it from a term window on your destop .

---

### Post by Nixie Pixel on 2009-02-13
This is the output from compiz --replace in the terminal:

```
Checking for Xgl: not present. 
xset q doesn't reveal the location of the log file. Using fallback /var/log/Xorg.0.log 
Detected PCI ID for VGA: 
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1440x900) to maximum 3D texture size (2048): Passed.
Checking for Software Rasterizer: Not present. 
Checking for nVidia: not present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format
```
Whereupon it hangs and I have to CTRL-C out of it.  I receive similar output with compiz --replace emerald, with the addition "cannot find plugin emerald."

---

### Post by ronacc on 2009-02-13
what video card or gpu do you have ? and what driver are you using ?

---

### Post by Nixie Pixel on 2009-02-17
Intel Graphics Media Accelerator X3100...and I haven't installed a special driver, so whatever is in 2.6.28-7...

---

### Post by ronacc on 2009-02-17
I'm all nvidia here except for my EEE so we need someone whos sharp on intel graphics to chime in here , I can't be of much help . Using the "search this forum" to search on intel I do see a bunch of gripes about the intel driver , you might want to check those .

---

### Post by Vaun on 2009-02-17
That is a bug with compizconfig-settings-manager and the DarkRoom theme.  It was fixed post 0.7.8.

 [http://gitweb.compiz-fusion.org/?p=fusion/compizconfig/ccsm;a=commit;h=28331749466c93b2b1467c213597993dc14ccd64]("http://gitweb.compiz-fusion.org/?p=fusion/compizconfig/ccsm;a=commit;h=28331749466c93b2b1467c213597993dc14ccd64")

Ccsm has not been updated in the repositories since September.  Compiz 0.8 is coming and the fix should be in Jaunty soon.

Compiz bug : [http://bugs.opencompositing.org/show_bug.cgi?id=1025]("http://bugs.opencompositing.org/show_bug.cgi?id=1025")

---

### Post by Pahanilmanlintu on 2009-04-04
I was under impression that the font color problem is because applications don't respect theme color settings. Amule has the same problem. Apparently background colors are explicitly defined as white, while font color is from the theme. Theme is trying to make backgrounds dark and fonts light gray ro something. I could be wrong here. Anyway, it's pretty annoying for someone like me who wants a dark theme. I know the Dust theme works, but only because it's not really dark.

---

