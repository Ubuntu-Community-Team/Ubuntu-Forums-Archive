---
title: "Mouse/Trackpad Serious Issues in Karmic After Latest Update"
date: 2009-07-25
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by iaskedalice09 on 2009-07-25
I'm having serious issues with my trackpad (and even mouse) after the latest update (kernel 2.6.31-4-generic).

[LIST]
[*]My trackpad won't scroll
[*]My trackpad's buttons won't click
[*]My mouse buttons won't click
[*]My trackpad/mouse CAN click in Firefox though not input boxes
[*]This problem also occurs in the previous kernel (after the update)
[*]I can't switch applications by ALT + TAB
[*]xserver-xorg-input-synaptics and xserver-xorg-input all are both installed according to apt-get
[*]Right-click doesn't work at all
[*]output of xinput list attached
[/LIST]

Any advice is REALLY appreciated.

---

### Post by iaskedalice09 on 2009-07-25
I can't upload files either...Sorry...

---

### Post by taavikko on 2009-07-25
How about searching little before posting?
[http://ubuntuforums.org/showthread.php?t=1221888](http://ubuntuforums.org/showthread.php?t=1221888)

for some of the issues...

---

### Post by iaskedalice09 on 2009-07-25
Thanks for your wonderful advice but I've already seen that thread. The only reason I'm able to post here is because I followed the advice there to install gsynaptic.

As far as the other fixes like horizontal scrolling/scrolling/tap clicking, etc. I don't know how to implement them. If you would be so kind as to enlighten me, I would be thoroughly appreciative.

Next time, please don't assume that I haven't looked. Thanks. :)

---

### Post by iaskedalice09 on 2009-07-25
Also, when I open pidgin or just about any application along side Firefox 3.0, I can't switch applications. When I killed pidgin and put it on a separate workdesk, it wouldn't let me switch workdesks.

---

### Post by iaskedalice09 on 2009-07-25
I've run gedit /etc/X11/xorg.conf but it was a blank file. I figured this was the wrong file to edit. The files listed in man xorg are either blank or incomprehensible to me.

What do I add to which file?

---

### Post by taavikko on 2009-07-25
> **iaskedalice09 said:**
> 
As far as the other fixes like horizontal scrolling/scrolling/tap clicking, etc. I don't know how to implement them. If you would be so kind as to enlighten me, I would be thoroughly appreciative.


You can play with settings with
```
gconf-editor /desktop/gnome/peripherals/touchpad
```


For editing xorg.conf, there isn't much need for this anymore.
input devices are automatically configured.

---

### Post by iaskedalice09 on 2009-07-25
Hi,
The issue with the trackpad still isn't cleared up, but at least the mouse works somewhat correctly.

Hopefully gnome-settings-daemon will fix this.

---

### Post by iaskedalice09 on 2009-08-02
I forgot to mention that I am not using a Symnatec Laptop, I am using a Dell Inspiron 1525. So, I don't think the g-d-s fix will work for me. :(

---

### Post by wayne_cat on 2009-08-02
> **iaskedalice09 said:**
> I forgot to mention that I am not using a Symnatec Laptop, I am using a Dell Inspiron 1525. So, I don't think the g-d-s fix will work for me. :(

The Inspiron has an ALPS touchpad ...driven by the psmouse kernel module .. is it loaded?
```

lsmod |grep psmouse
```The configuration should work with the tools that manage synaptics (i.e. gnome-mouse-properties)

---

### Post by iaskedalice09 on 2009-08-05
output:
psmouse                56180  0 

Any insight?

---

### Post by iaskedalice09 on 2009-08-06
> **iaskedalice09 said:**
> output:
psmouse                56180  0 

Any insight?
Do you think, given the output, that it's loaded, or not?

---

### Post by iaskedalice09 on 2009-08-09
bump please help

---

### Post by wayne_cat on 2009-08-09
> **iaskedalice09 said:**
> bump please help

sorry ... did not see your answer ... could you please post the result from:

```
synclient -l
```

---

### Post by drs305 on 2009-08-09
On my Lenovo laptop in Karmic, I have to run the following to enable the touchpad tapping. The pointer moves but tapping doesn't work until this command is executed:
```
synclient TapButton1=1
```
I'll get around to putting in a config file eventually. Since it's my travel laptop, leaving it alone is almost like having a secret security feature to prevent others from using it.  ;-)

---

### Post by iaskedalice09 on 2009-08-09
Result of synclient -l

Unable to find a synaptics device.

And touchpad tapping works but it's VERY erratic and not normal. Pre the gnome-daemon-settings update to ..4 it was great. Now it's very very weird.

---

### Post by iaskedalice09 on 2009-08-10
There's no synaptics device. Should I be worried?

---

### Post by iaskedalice09 on 2009-08-11
bump again...sorry... just need help

There's no synaptics device.

---

### Post by wayne_cat on 2009-08-11
> **iaskedalice09 said:**
> bump again...sorry... just need help

There's no synaptics device.

I don't know any other tools to configure a touchpad ... file a bug report.

---

### Post by iaskedalice09 on 2009-08-12
Thanks, pls see [https://bugs.launchpad.net/ubuntu/+source/gnome-settings-daemon/+bug/412291](https://bugs.launchpad.net/ubuntu/+source/gnome-settings-daemon/+bug/412291) for the bug report

---

