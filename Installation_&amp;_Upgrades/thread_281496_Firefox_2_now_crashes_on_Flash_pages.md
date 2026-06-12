---
title: "Firefox 2 now crashes on Flash pages"
date: 2006-10-21
forum: Installation &amp; Upgrades
---

### Post by steveguy on 2006-10-21
Since upgrading to Edgy (which automatically updates Firefox to 2) every time I visit a page with Flash content, Firefox crashes. I have tried removing/reinstalling both Firefox and Flash (free and non-free). If I remove Flash Firefox 2 is stable.

---

### Post by zeroflake on 2006-10-21
Exact same problem when upgraded to edgy w.firefox 2, i had to downloaded 1.5.0.7 from mozilla to get my flash working, but i want to try version 2... please help!

---

### Post by dto on 2006-10-21
Change xorg.conf so you are in 24-bit mode by default (rather than 16-bit). I  had the same issue and running in 24-bit mode solved it.

---

### Post by steveguy on 2006-10-21
This forum truly is a wonderful place - editing xorg.conf as you suggested cured it for me - thank you!

---

### Post by ekravche on 2006-10-26
have this problem as well, will try to change x.org to 24 bit. I hope that edgy includes my video card drivers otherwise it will be slow

---

### Post by Kayma on 2006-10-27
I had this same problem, and I just wanted to say that this solution worked wonderfully. Thanks a lot, guys!

---

### Post by pachipuro on 2006-10-27
I have this problem also.  Though I`m not sure how to edit xorg.conf to work in 24 mode.  Can anyone help me?  Thanks.

---

### Post by cvmostert on 2006-10-27
> **pachipuro said:**
> I have this problem also.  Though I`m not sure how to edit xorg.conf to work in 24 mode.  Can anyone help me?  Thanks.

great it worked for me too...

what you need to do is get the xorg.conf file... in /etc/X11/ and edit the default depth... to 24.

mine was 16 and i changed it to 24.. seem to work now.. well it loads.. have not tried it yet... but it looks fine.

---

### Post by pachipuro on 2006-10-27
Yeah, I went to the file and tried to change the default depth and got, "Could not save the file /etc/X11/xorg.conf. You do not have the permissions necessary to save the file. Please, check that you typed the location correctly and try again."  I did sudo su in the terminal, so I thought that I had permission.  I'm a little new to all this.

---

### Post by Sqweeks on 2006-10-27
You sir are a god who ever found out how to fix this.

---

### Post by Max Luebbe on 2006-10-27
> **pachipuro said:**
> Yeah, I went to the file and tried to change the default depth and got, "Could not save the file /etc/X11/xorg.conf. You do not have the permissions necessary to save the file. Please, check that you typed the location correctly and try again."  I did sudo su in the terminal, so I thought that I had permission.  I'm a little new to all this.

```
sudo nano /etc/X11/xorg.conf
```
Make changes, then Ctrl-X to exit, y to confirm changes.

---

### Post by pachipuro on 2006-10-28
It worked!  Thanks.

---

### Post by anaxagoras on 2006-10-28
Just to confirm it works here also!

---

### Post by revolutiongames2004 on 2006-11-01
doesnt work for me

---

### Post by sillywilly4 on 2006-11-01
Doesn't work for me either.  NoScript will block the Flash content, but as soon as I try to open the Flash content, firefox crashes

---

### Post by LeslieL on 2006-11-01
gksudo gedit /etc/X11/xorg.conf

---

### Post by paulmerchant on 2006-11-01
I added this line to the end of my /etc/firefox/firefoxrc

export XLIB_SKIP_ARGB_VISUALS=1

Not sure where I found this tip, but it's in a few of the Firefox in Edgy threads. It's save me from crashes related to Flash even without setting 24bit color.

---

### Post by sillywilly4 on 2006-11-01
I just restarted the system and all is good.  As a side note, why does Ubuntu require a reboot to enable settings so much?

---

### Post by handdog on 2006-11-03
> **paulmerchant said:**
> I added this line to the end of my /etc/firefox/firefoxrc

export XLIB_SKIP_ARGB_VISUALS=1

Not sure where I found this tip, but it's in a few of the Firefox in Edgy threads. It's save me from crashes related to Flash even without setting 24bit color.

Sweet, thank you :) :)

---

### Post by ghostrunner on 2006-11-03
My Default Depth was already set to 24.  But Firefox seem to keep crashing when I visit Flash-intensive pages (YouTube, Pandora).  Any other thoughts?

Thanks!

---

