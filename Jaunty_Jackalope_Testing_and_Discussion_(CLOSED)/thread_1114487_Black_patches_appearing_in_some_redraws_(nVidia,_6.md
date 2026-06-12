---
title: "Black patches appearing in some redraws (nVidia, 64-bit)"
date: 2009-04-02
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by Edward C on 2009-04-02
Large patches of some windows on my 64 bit Jaunty machine (using the proprietary nVidia driver) are being blacked out on some occasions when the screen redraws. This occurs regardless of whether Compiz is enabled, or whether I use the 180 driver or the 173 version. My video card is an Asus nVidia 6600GT.

I've attached a screenshot of it happening in GIMP, but it can occur in any application. When it occurs in the main canvas in Firefox, pressing the "Print Screen" key causes it to disappear and re-render the web-page correctly. In all other applications it will survive a Print Screen, and even manual rotation of the desktop-cube.

Is this a known issue? Is it possible that it's a fault within the card (which may have overheated recently)? The fact that I can capture it in a screen-shot suggests to me that it isn't a video hardware fault, but you never know.

---

### Post by Edward C on 2009-04-03
This does not occur when using the 8.10 live CD with the nVidia 173 driver, so it seems like it's a Jaunty bug.

---

### Post by nanog on 2009-04-03
Ummm no its an nvidia binary driver bug.

---

### Post by Edward C on 2009-04-03
Great. Yes, it's bug in a package that is in Jaunty (maybe the nVidia binary, maybe not), as opposed to a Jaunty bug. Thanks for all your help.

---

### Post by phenest on 2009-04-04
> **nanog said:**
> Ummm no its an nvidia binary driver bug.

It's not necessarily a driver bug, but an incompatibility with the kernel. I used to have this issue (and others), and now I have no issues at all, but I'm using the same driver.

---

### Post by axelroo on 2009-04-04
In the meantime, you might need the nvidia driver downloaded from nVidia's website.

---

### Post by Edward C on 2009-04-04
Thanks, I'm not really in a huge rush to fix the problem, just wanted to make sure it was a known issue. Is there a bug raised for it somewhere?

---

### Post by matthew.ball on 2009-04-04
I came across a similar issue yesterday, though it has only happened once.

I updated my nvidia drivers and kernel and grub didn't update - there were issues with the nvidia module.

Updated grub, fixed it and noticed the "eye-candy" was all put back on (I reset xorg so software rendering was on, and then reloaded with the new kernel), and turning off the eye candy seemed to make these black patches appear.

I just rebooted X (unfortunately Ctrl+Alt+Backspace no longer works though, despite having disabled dontzap), and it has not come back.

Edit: I am running a 32-bit laptop though.

---

