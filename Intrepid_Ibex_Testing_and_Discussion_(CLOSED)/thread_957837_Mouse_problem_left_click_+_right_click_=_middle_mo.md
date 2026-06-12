---
title: "Mouse problem: left click + right click = middle mouse button"
date: 2008-10-24
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by WWSmith36 on 2008-10-24
With the new xorg and xserver I have noticed a problem with my mouse.  If I use left and right mouse button at the same time - it responds as if I clicked the middle mouse button.

There is no mouse entry in my xorg.conf
I added an entry for my mouse and included this option

```
Option "Emulate3Buttons" "false"
```

but xorg did not respect this.

Is there any way to fix this?

---

### Post by ddrichardson on 2008-10-25
If this is with Ibex, [snag a bug report]("https://bugs.launchpad.net/xorg/+filebug") and it may get caught before release.

---

### Post by wgrant on 2008-10-25
It's not a bug. xorg.conf is deprecated for setting input device options; see [the HAL section of the X configuration page](https://wiki.ubuntu.com/X/Config#hal) for details.

---

### Post by wgrant on 2008-10-25
> **ddrichardson said:**
> If this is with Ibex, [snag a bug report]("https://bugs.launchpad.net/xorg/+filebug") and it may get caught before release.

As well as not being a bug, that's not the right URL. If it were one, such a bug should be filed against Ubuntu's xorg, not upstream xorg.

---

### Post by ddrichardson on 2008-10-25
I do apologise

---

### Post by WWSmith36 on 2008-10-26
> It's not a bug. xorg.conf is deprecated for setting input device options; see the HAL section of the X configuration page for details.

I am not sure if I am interpreting this correctly.  It is my understand the I need to add a new fdi file in /etc/hal/fdi/policy directory.

I created a file mouse.fdi

```
<?xml version="1.0" encoding="ISO-8859-1"?>
<deviceinfo version="0.2">
 <device>
  <match key="input.x11_driver" string="mouse">
   <merge key="input.x11_options.Emulate3Buttons" type="bool">false</merge>
  </match>
 </device>
</deviceinfo>
```

This does not help.  I am missing something

---

