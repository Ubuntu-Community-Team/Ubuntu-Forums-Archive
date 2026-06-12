---
title: "MacBook2,1 Touchpad/Trackpad issues on Intrepid RC"
date: 2008-10-26
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by Cifra on 2008-10-26
Well, the only thing that still doesn't work on my MacBook is the touchpad. I made a HAL .fdi file like the wiki says ([https://help.ubuntu.com/community/MacBook/](https://help.ubuntu.com/community/MacBook/)) and now scrolling works, but I still can't get the twofinger+button left click. The wiki says it should work, but it doesn't. Has anyone solved this?

Also, moving the mouse with the touchpad is much slower and weirder on Ubuntu than in Mac OSX

---

### Post by kosumi68 on 2008-10-26
> **Cifra said:**
> Well, the only thing that still doesn't work on my MacBook is the touchpad. I made a HAL .fdi file like the wiki says ([https://help.ubuntu.com/community/MacBook/](https://help.ubuntu.com/community/MacBook/)) and now scrolling works, but I still can't get the twofinger+button left click. The wiki says it should work, but it doesn't. Has anyone solved this?

Also, moving the mouse with the touchpad is much slower and weirder on Ubuntu than in Mac OSX

The wiki says the fdi files goes into /etc/hal/fdi, but it should be in /usr/share/hal/fdi.

---

### Post by Cifra on 2008-10-27
Copied the file touchpad.fdi to /usr/share/hal/fdi/policy/

Still doesn't work.

---

### Post by wgrant on 2008-10-27
> **kosumi68 said:**
> The wiki says the fdi files goes into /etc/hal/fdi, but it should be in /usr/share/hal/fdi.

/etc/hal/fdi/policy is the correct place. Only packages should be touching /usr.

---

### Post by Cifra on 2008-10-27
Well, I broke the system, so I had to do a second install. Now I just pasted this into appletouch.fdi in /etc/hal/fdi/policy/ AND IT WORKS!

Now I have another question. I have a two finger tap to right click. How could I change thus code to have a "two finger+button click" ( like on MAc OS X) right-click function?

```
<?xml version="1.0" encoding="ISO-8859-1"?>
<deviceinfo version="0.2">
  <device>
    <match key="info.capabilities" contains="input.touchpad">
      <match key="info.product" contains="appletouch">
        <merge key="input.x11_driver" type="string">synaptics</merge>
        <merge key="input.x11_options.SHMConfig" type="string">true</merge>
        <merge key="input.x11_options.VertEdgeScroll" type="string">false</merge>
        <merge key="input.x11_options.HorizEdgeScroll" type="string">false</merge>
        <merge key="input.x11_options.VertTwoFingerScroll" type="string">true</merge>
        <merge key="input.x11_options.HorizTwoFingerScroll" type="string">true</merge>
        <merge key="input.x11_options.RTCornerButton" type="string">false</merge>
        <merge key="input.x11_options.RBCornerButton" type="string">false</merge>
        <merge key="input.x11_options.LBCornerButton" type="string">false</merge>
        <merge key="input.x11_options.LTCornerButton" type="string">false</merge>
        <merge key="input.x11_options.TapButton1" type="string">0</merge>
        <merge key="input.x11_options.TapButton2" type="string">3</merge>
        <merge key="input.x11_options.TapButton3" type="string">2</merge>
        <merge key="input.x11_options.PalmDetect" type="string">1</merge>
      </match>
    </match>
  </device>
</deviceinfo>
```

---

### Post by kosumi68 on 2008-10-27
> **Cifra said:**
> 
Now I have another question. I have a two finger tap to right click. How could I change thus code to have a "two finger+button click" ( like on MAc OS X) right-click function?
[/CODE]

Add these lines:
```

        <merge key="input.x11_options.ClickFinger1" type="string">1</merge>
        <merge key="input.x11_options.ClickFinger2" type="string">3</merge>
        <merge key="input.x11_options.ClickFinger3" type="string">2</merge>

```

---

