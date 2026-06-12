---
title: "LiveCD install failed - resolution issue"
date: 2006-06-28
forum: Installation &amp; Upgrades
---

### Post by pmasiar on 2006-06-28
I installed breezy and dapper couple of times with no problems. Until today...

Tried to install dapper on another computer. Locally assembled desktop with CRT monitor, no laptop. There is something strange with video card on that PC. I think graphic card uses CPU RAM as graphic memory or something - windows reports 480MB of RAM, but it looks like 512MB for me. 

Anyway, dapper autodetected only single option, 640x480 resolution, although under windows is much higher. And I was not able to change resolution on liveCD - only that one option was allowed.

Worse is, on 640x480 I was not able to install at all!!! With that resolution, windows of installation program did not fit on the screen and I was not able to click to "NEXT". Cannot believe my luck - am I the first one trying to install dapper on 640x480 screen? :confused:  and :mad: 

The shame! The shame! I wanted to show off 6-click install...

Any suggestions what to try next?
Is there a curses-based ASCII install like in old times?

In worst case, some command-line magic? I definitely need ubuntu on that box.
I found this wiki page: [https://help.ubuntu.com/community/FixVideoResolutionHowto](https://help.ubuntu.com/community/FixVideoResolutionHowto)
Did not tried yet: too scared...

In another simmilar thread I found command " sudo dpkg-reconfigure xserver-xorg "
But not sure how it will affect autodetection - autodetection failed before. Hmmmm. Still confused.

---

### Post by taurus on 2006-06-28
You can always use the alternate CD to install it!

---

### Post by vbailey on 2006-06-29
1. Get the specs of your video card and monitor (max resolution, video card memory)

2. Boot up the live CD, run (dont worry ive done this before!) "sudo dpkg-reconfigure xserver-xorg"

3. Choose to autodetect hardware, enter the resolution of your monitor and video card when prompted.

4. Restart x server "CTRL+ALT+BACKSPACE" if it doesnt restart automatically. 

5. Then choose to install dapper. Ubuntu will hold onto the settings after installation.

I had similar problems with a 3dfx voodoo 3 card. :cool:

---

