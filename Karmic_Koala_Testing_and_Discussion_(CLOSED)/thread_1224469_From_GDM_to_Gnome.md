---
title: "From GDM to Gnome"
date: 2009-07-27
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by dentaku65 on 2009-07-27
It is only my impression or the login procedure is quite slow?
I've noted since Jaunty a really improved boost from Grub to GDM, but the Gnome login (plus Compiz-fusion) is really slow on my machine.

Anyone else noted this?
Any suggestion to speed up?

---

### Post by setherd on 2009-07-27
same here. also I hate the logout.
I'd rather be able to shutdown and/or restart from my desktop
( I know I can do ctrl-alt-del)

---

### Post by amano on 2009-07-27
That will come WHEN the FUSA applet will be ported to use the new GDM. It will come. It may take some weeks. Patience please.

And remember. This is a DEVELOPMENT release. That means that some things are not yet ready and thus cannot be shipped yet.

---

### Post by dentaku65 on 2009-07-27
> **amano said:**
> That will come WHEN the FUSA applet will be ported to use the new GDM. It will come. It may take some weeks. Patience please.

And remember. This is a DEVELOPMENT release. That means that some things are not yet ready and thus cannot be shipped yet.

Hi amano,
I did not reported for lack of patience my post, I just ask...
BTW, what is FUSA applet?
Anyway, I've noted this slow performance in Jaunty too.

---

### Post by wayne_cat on 2009-07-27
> **dentaku65 said:**
> Hi amano,
I did not reported for lack of patience my post, I just ask...
BTW, what is FUSA applet?
Anyway, I've noted this slow performance in Jaunty too.

FUSA = Fast User Switching Applet

edit: maybe interesting:

[http://www.markshuttleworth.com/archives/233](http://www.markshuttleworth.com/archives/233)

---

### Post by dentaku65 on 2009-07-27
> **wayne_cat said:**
> FUSA = Fast User Switching Applet

edit: maybe interesting:

[http://www.markshuttleworth.com/archives/233](http://www.markshuttleworth.com/archives/233)

ah, ok... I don't use fast-user-switching-applet, I prefer to have all those entries on the bottom of menu of main-menu applet... but is FAST applet improves GDM login?

---

### Post by Martje_001 on 2009-07-27
No, it doesn't speedup the login process.

---

### Post by ranch hand on 2009-07-27
First; right click on a panel and add the "Shut Down" applet.  This will give you the right stuff to shut down with untill thisgets straight.

Second; my ATI card does not do well with compiz and from what I have used, I don't like it anyway.  My box, minus compiz, is VERY fast on all of the boot string.  9.04 is about 4 times faster than 8.04.  9.10 is almost twice as fast as 9.04.

---

### Post by dentaku65 on 2009-07-27
> **ranch hand said:**
> First; right click on a panel and add the "Shut Down" applet.  This will give you the right stuff to shut down with untill thisgets straight.

Second; my ATI card does not do well with compiz and from what I have used, I don't like it anyway.  My box, minus compiz, is VERY fast on all of the boot string.  9.04 is about 4 times faster than 8.04.  9.10 is almost twice as fast as 9.04.

Ok I've tried with metacity... 25 seconds from GDM to Gnome desktop completely loaded (same "speed" with compiz enabled).

Maybe it depends by my Intel video card.

Anyone else at GDM login have this poor performance?

---

### Post by wayne_cat on 2009-07-27
> **dentaku65 said:**
> Ok I've tried with metacity... 25 seconds from GDM to Gnome desktop completely loaded (same "speed" with compiz enabled).

Maybe it depends by my Intel video card.

Anyone else at GDM login have this poor performance?

25 seconds is quite long ... do you have any errors in .xsession-errors or in the gdm log files?
```

/var/log/gdm/*
```

---

### Post by dentaku65 on 2009-07-27
> **wayne_cat said:**
> 25 seconds is quite long ... do you have any errors in .xsession-errors or in the gdm log files?
```

/var/log/gdm/*
```

This is the .xession-error
> /etc/gdm/Xsession: Beginning session setup...
Setting IM through im-switch for locale=en_US.
Start IM through /etc/X11/xinit/xinput.d/all_ALL linked to /etc/X11/xinit/xinput.d/default.
GNOME_KEYRING_SOCKET=/tmp/keyring-zyqt5E/socket
SSH_AUTH_SOCK=/tmp/keyring-zyqt5E/socket.ssh

(gnome-settings-daemon:2765): GLib-CRITICAL **: g_propagate_error: assertion `src != NULL' failed

(gnome-settings-daemon:2765): GLib-CRITICAL **: g_propagate_error: assertion `src != NULL' failed
Checking for Xgl: not present. 
xset q doesn't reveal the location of the log file. Using fallback /var/log/Xorg.0.log 
Detected PCI ID for VGA: 
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Checking screen 1Comparing resolution (1024x768) to maximum 3D texture size (2048): Passed.
Checking for Software Rasterizer: Not present. 
Checking for nVidia: not present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
/usr/bin/compiz.real (core) - Warn: Plugin 'core' already active

(polkit-gnome-authentication-agent-1:2849): GLib-GIO-WARNING **: g_simple_async_result_complete() called from outside main loop!

(polkit-gnome-authentication-agent-1:2849): GLib-GIO-WARNING **: g_simple_async_result_complete() called from outside main loop!

(polkit-gnome-authentication-agent-1:2849): GLib-GIO-WARNING **: g_simple_async_result_complete() called from outside main loop!
** (nm-applet:2863): DEBUG: applet_common_device_state_changed
** (nm-applet:2863): DEBUG: old state indicates that this was not a disconnect 0
** (nm-applet:2863): DEBUG: applet_common_device_state_changed
** (nm-applet:2863): DEBUG: foo_client_state_changed_cb
** (nm-applet:2863): DEBUG: applet_common_device_state_changed
** (nm-applet:2863): DEBUG: applet_common_device_state_changed
Terminated
** (nm-applet:2863): DEBUG: applet_common_device_state_changed
/usr/bin/compiz.real (cube) - Warn: Failed to load slide: /usr/share/gdm/themes/Human/ubuntu.png

(gnome-panel:2843): Gdk-WARNING **: /build/buildd/gtk+2.0-2.17.6/gdk/x11/gdkdrawable-x11.c:952 drawable is not a pixmap or window

(parcellite:2873): Gdk-CRITICAL **: gdk_window_thaw_toplevel_updates_libgtk_only: assertion `private->update_and_descendants_freez
e_count > 0' failed
/usr/lib/python2.6/dist-packages/FusionIcon/interface_gtk/main.py:213: GtkWarning: gdk_window_thaw_toplevel_updates_libgtk_only: a
ssertion `private->update_and_descendants_freeze_count > 0' failed
  gtk.main()
/usr/bin/compiz.real (animation) - Error: Animation settings mismatch in "Animation Selection" list for Open event.
** (nm-applet:2863): DEBUG: applet_common_device_state_changed
** (nm-applet:2863): DEBUG: foo_client_state_changed_cb
compiz.real (cube) - Warn: Failed to load slide: /usr/share/gdm/themes/Human/ubuntu.png
Segmentation fault (core dumped)
Window manager warning: Failed to read saved session file /home/sava/.config/metacity/sessions/10a017fe6198ea2ed312487283015741460
0000027140025.ms: Failed to open file '/home/sava/.config/metacity/sessions/10a017fe6198ea2ed3124872830157414600000027140025.ms': 
No such file or directory
compiz.real (animation) - Error: Animation settings mismatch in "Animation Selection" list for Open event.
compiz.real (animation) - Error: Animation settings mismatch in "Animation Selection" list for Open event.
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open 
usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.

evolution-alarm-notify-Message: Setting timeout for 10860 1248739200 1248728340
evolution-alarm-notify-Message:  Tue Jul 28 02:00:00 2009

evolution-alarm-notify-Message:  Mon Jul 27 22:59:00 2009



---

### Post by wayne_cat on 2009-07-27
well .. I don't see an "extraordinary" error .. only the typical sings for "Gnome is a mess at the moment" 

what happens if you stop gdm and start Gnome with startx ... is this faster?

---

### Post by tekstr1der on 2009-07-27
> **dentaku65 said:**
> It is only my impression or the login procedure is quite slow?
I've noted since Jaunty a really improved boost from Grub to GDM, but the Gnome login (plus Compiz-fusion) is really slow on my machine.

All I can say is I've noted the same exact thing. Takes about 20 seconds from Grub to GDM. That part's nice. After login, about 25 seconds to full desktop. Prior to adding a GDM background, I would just be staring at a black screen with cursor for those ~25 seconds. Lots of HDD activity during the time period in question which I don't remember from Intrepid or Jaunty. My .xsession-errors looks very similar to yours and doesn't indicate anything overly suspicious. I would love to get some idea of why this is. Been meaning to ask, but been busy with bigger bugs of late.

---

### Post by papangul on 2009-07-27
I am also going through through same login delay problem, for the time being I am using openbox instead of gnome.

---

### Post by psyke83 on 2009-07-27
> **dentaku65 said:**
> It is only my impression or the login procedure is quite slow?
I've noted since Jaunty a really improved boost from Grub to GDM, but the Gnome login (plus Compiz-fusion) is really slow on my machine.

Anyone else noted this?
Any suggestion to speed up?

Are you noticing the cursor stuttering if you try to move it during the GDM -> GNOME transition? If so, that's because of KMS.

Boot with the "nomodeset" GRUB parameter and see if the login is faster.

---

### Post by taavikko on 2009-07-28
> **psyke83 said:**
> Boot with the "nomodeset" GRUB parameter and see if the login is faster.

How much can the excess software, added startup applications delay the login?
Samba etc.

---

### Post by tekstr1der on 2009-07-28
> **psyke83 said:**
> Are you noticing the cursor stuttering if you try to move it during the GDM -> GNOME transition? If so, that's because of KMS.

No stuttering, just lots of disk I/O. KMS hands control to the graphic driver early (about 2 seconds) into the boot process AFAIK. Maybe I don't fully understand the interaction between GDM and Intel driver, but I don't think KMS is the issue here.

> **psyke83 said:**
> Boot with the "nomodeset" GRUB parameter and see if the login is faster.

This has no impact. Still takes25 seconds from GDM login to desktop with or without "nomodeset" parameter. I was excited to try this to at least rule out one possibility. Thanks.

---

### Post by dentaku65 on 2009-07-28
> **psyke83 said:**
> Are you noticing the cursor stuttering if you try to move it during the GDM -> GNOME transition? If so, that's because of KMS.

Boot with the "nomodeset" GRUB parameter and see if the login is faster.

No difference with "nomodeset" parameter. The GDM login is still slow.

---

### Post by psyke83 on 2009-07-28
> **tekstr1der said:**
> No stuttering, just lots of disk I/O. KMS hands control to the graphic driver early (about 2 seconds) into the boot process AFAIK. Maybe I don't fully understand the interaction between GDM and Intel driver, but I don't think KMS is the issue here.



This has no impact. Still takes25 seconds from GDM login to desktop with or without "nomodeset" parameter. I was excited to try this to at least rule out one possibility. Thanks.

KMS causes issues with some chipsets. On my 855GM (which is the same as the OP's, if I recall correctly) it causes delays when initializing OpenGL applications, or performing any XRender requests (such as during login). These issues don't exist when KMS is disabled.

It causes cursor stuttering, though, not a large delay.

---

### Post by MacUntu on 2009-07-28
Just removed all but one panels and on that panel all applets. That shaved off 15 seconds (slow 5400rpm disk, one fresh stock user vs. one with this minimal panel)... there's really room for improvement and that's why GDM -> desktop speedup is one of the targets for 9.04/9.10.

---

### Post by tekstr1der on 2009-07-29
> **MacUntu said:**
> Just removed all but one panels and on that panel all applets. That shaved off 15 seconds (slow 5400rpm disk, one fresh stock user vs. one with this minimal panel)... 

I created a test user profile and did the same: 1 panel, no applets. Yes, I confirm that login to this user desktop is indeed considerably faster (about 12 seconds from login to desktop). Almost as quick as I'd like to see my profile load.

> **MacUntu said:**
> there's really room for improvement and that's why GDM -> desktop speedup is one of the targets for 9.04/9.10.

Indeed there's room. If this is one of the targets for gnome, it seems to be regressing. As of today's updates to 2.27.5 for gnome, it's taking an additional 5 seconds to get to a functional desktop. 30-35 seconds from login. Now it takes about a full minute total to boot to a usable desktop. On the same machine, it was about 50 seconds using Intrepid.

---

### Post by dentaku65 on 2009-07-29
> **tekstr1der said:**
> I created a test user profile and did the same: 1 panel, no applets. Yes, I confirm that login to this user desktop is indeed considerably faster (about 12 seconds from login to desktop). Almost as quick as I'd like to see my profile load.



Indeed there's room. If this is one of the targets for gnome, it seems to be regressing. As of today's updates to 2.27.5 for gnome, it's taking an additional 5 seconds to get to a functional desktop. 30-35 seconds from login. Now it takes about a full minute total to boot to a usable desktop. On the same machine, it was about 50 seconds using Intrepid.

I can confirm performance regression with Gnome 2.27.5 
But I have the suspect that my Intel card has still many problems with Karmic (and viceversa) :-)

---

### Post by ranch hand on 2009-07-29
Herman
I can't find it now, but I just read (yesterday) that there is a problem with grub2 and LVM.  They have not gotten that straight yet.

---

### Post by loomsen on 2009-07-29
> 
yep &#8221;short and long URL&#8222;
[http://yep.it/](http://yep.it/)


nice one, been looking for some tinier url than tiny.url just now :D

---

