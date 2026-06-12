---
title: "Dual monitor with ATI 5870"
date: 2012-10-01
forum: Installation &amp; Upgrades
---

### Post by rentrimillos on 2012-10-01
I need help!  I installed Ubuntu 12.04 and everything runs fine with one exception.....my dual monitor setup.  I even got my scanner and webcam working!  I have an Asus VW266H plugged into HDMI and an Asus VE256 plugged into DVI port.  My video card is an AMD/ATI 5870.

Using the display setup, I can have one monitor or the other monitor on, but not both.
These are the messages I get:
requested position/size for CRTC 147 is outside the allowed limit: position=(1920, 0), size=(800, 600), maximum=(1920, 1920)

and:
GDBus.Error:org.gtk.GDBus.UnmappedGError.Quark._gnome_2drr_2derror_2dquark.Code3: requested position/size for CRTC 147 is outside the allowed limit: position=(1920, 0), size=(800, 600), maximum=(1920, 1920)

I don't know where to start.  Can anyone help, please?
Thanks

---

### Post by T.J. on 2012-10-02
Hello! =)

Please forgive my manners in answering a question with another, but before I can help you, I need to know:

1.  What interface are you using?  The default named "Unity"?

2. Did you install the proprietary ATI driver from Additional Drivers?If you have, you may find [this]("http://ubuntuforums.org/showthread.php?t=1810936") useful.
 
3. Do you have a second DVI port?

Thanks!
T.J.

---

### Post by rentrimillos on 2012-10-02
Thanks TJ for trying to help....no apology needed.

I did install the ATI driver, but no success.
Also, I need change a statement I made....the second display is connected thru the display port, not DVI.  I apologize for that misstatement.
I assume that I am using the default interface....I didn't change anything.
How do I determine which interface I am using?

TJ, thanks again.

---

### Post by rentrimillos on 2012-10-02
TJ

Sorry....I am using Unity

---

### Post by QIII on 2012-10-02
Are you using the Catalyst Control Center in admin mode to make changes?

---

### Post by rentrimillos on 2012-10-02
QIII

How do I verify that I am doing it in admin mode?

Thanks for your help

---

### Post by QIII on 2012-10-02
Are you being asked for a password?

---

### Post by rentrimillos on 2012-10-02
QIII

Thanks....that took care of my problem.
I was able to resolve it when I logged in as admin.

Everything works!
Thanks all

---

