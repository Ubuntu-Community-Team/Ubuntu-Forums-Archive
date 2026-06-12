---
title: "Jaunty Macbook Pro touchpad"
date: 2009-04-18
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by N_Nick on 2009-04-18
Hey,

I just upgraded to Jaunty RC and i am having some problems with my Macbook Pro 4.1 touchpad.

Two finger tapping for right-click doesn't work, actually when i double tap sometimes it deletes and sometimes it double-clicks. Three finger tapping works as a right click though.  I tried tweaking /etc/hal/fdi/policy/preferences.fdi with no luck.

I would appreciate if someone could link me with his/hers preferences.fdi or point to the right direction. I'm mostly concerned about two finger tapping as a right click but any other useful tweaks are welcome. ;) 

Sorry if this has been posted elsewhere i tried searching the forum.

Cheers

Here's my preferences.fdi:

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
        <merge key="input.x11_options.VertTwoFingerScroll"type="string">true</merge>
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

### Post by mrphd on 2009-04-18
i'm also have problems with my touchpad (on an ASUS VX2), [http://ubuntuforums.org/showthread.php?t=1128265](http://ubuntuforums.org/showthread.php?t=1128265), but my problem is different (tapping no longer works at all)

---

### Post by N_Nick on 2009-04-20
Ok everything is fixed now i got only one problem.

If i tap twice and move the cursor i select things. Its really annoying sometimes.  Is it possible to disable it completely?

---

