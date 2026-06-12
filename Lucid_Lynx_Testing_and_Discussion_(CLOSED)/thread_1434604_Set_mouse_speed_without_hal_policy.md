---
title: "Set mouse speed without hal policy"
date: 2010-03-20
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by Navix77 on 2010-03-20
Now that hal is gone is there anyway to set the mouse speed like you could with a hal policy. I need this:

<match key="info.capabilities" contains="input.mouse">
   <merge key="input.x11_options.ConstantDeceleration" type="string">2</merge>
</match>

I've tried "xset m" but it's still too fast.

---

### Post by megaexception on 2010-03-20
i have very similar question (only difference - i have touchpad not mouse).

1) temporary fix
open terminal, use "xinput list" to find out your mouse device name.
use "xinput list-props '<you mouse device name>'" to see driver options list
use "xinput set-prop '<you mouse device name>' <option name> <value>" to change option value
this works, but this is current session only


2) permanent solution should be udev
create rule in /etc/udev/rules.d
rule must match device add event for mouse, and set properties
look for examples in /lib/udev/rules.d/
but this doesn't work yet :(

---

### Post by Fatboy Snarky on 2010-04-06
Hi megaexception,


thank you for your explanation!

Is there any way to not only change the acceleration/threshold setting but the mouse resolution or scan rate?

For Logitech mouses there is the tool "lomoco".

While the scan rate clearly depends on the specific hardware,
isn't there a possibility to change the 1:1 translation of physical mouse movement events (events per millimeter) into
"logical" events (screen pixels per event)?

An integer multiplyer/divider would be easy, but is there a way to do this other than using special/modified hardware drivers?


--
Thanks for KDE 4.4.2-0ubuntu1~karmic1~ppa2 packages!

---

