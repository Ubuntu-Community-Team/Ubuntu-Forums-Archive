---
title: "Synaptics touchpad vertical scrolling behaviour change"
date: 2008-08-28
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by _oOMOo_ on 2008-08-28
The area of my touchpad that allows vertical scrolling has moved about 10mm to the right so is almost off the edge of the touchpad. It makes scrolling behaviour erratic and clumsy. Anyone else experiencing this?

---

### Post by hardhu on 2008-08-28
> **_oOMOo_ said:**
> The area of my touchpad that allows vertical scrolling has moved about 10mm to the right so is almost off the edge of the touchpad. It makes scrolling behaviour erratic and clumsy. Anyone else experiencing this?

I have no problems with scrolling, instead I just noticed that tapping on the touchpad doesn't work anymore on my laptop (Acer Aspire 5024, Turion ML-34)

---

### Post by beercz on 2008-08-28
I hadn't noticed this until I read this thread title.

Vertical scrolling does work on my lenovo 3000 n200 laptop using my touchpad, but it is at the extreme right of the pad.

Double-clicking by tapping the touchpad does not work either.

Neither are a real issue for me at the moment.

Has anyone reported a bug?  If so, can the link be posted so we can monitor and comment on the bug.

Thanks

---

### Post by _oOMOo_ on 2008-08-28
I've reported a bug against the synaptics driver package although I'm not sure whether the default settings for the touchpad are actually part of the driver. Best guess on my part, url:

[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-synaptics/+bug/262305]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-synaptics/+bug/262305")

---

### Post by beercz on 2008-08-28
Thanks for this, I will keep an eye on this.

---

### Post by jfernyhough on 2008-08-28
I'm wondering if a sudo dpkg-reconfigure -phigh xserver-xorg will cure the problem - there seems to have been a change in the xserver-input update from earlier.

---

### Post by xerosis on 2008-08-28
The latest X.org updates seem to have removed the synaptics section from xorg.conf, mine's now really slow and I can't right click (macbook) :(

---

### Post by phenest on 2008-08-29
I have a dual boot with Hardy and Intrepid, which share the /home partition. I now have this problem with Hardy too, since it appeared in Intrepid. A setting maybe?

EDIT: Nope. My mistake. Just Intrepid.

---

### Post by beercz on 2008-09-03
I have just noticed that tapping my touchpad works again now, some recent updates must have fixed it (I don't know which one(s) though).

Scrolling with the touchpad *seems* to be a little better now too, or is it just me?

---

### Post by syko21 on 2008-09-03
I'm also seeing this issue. Scroll only works on the far right of the touchpad.

---

### Post by syko21 on 2008-09-03
I found a solution to get normal function back. An update changed /etc/X11/xorg.conf 
Simply change your xorg.conf by commenting out the ZAxis line and add the VertEdgeScroll line.
```

Section "InputDevice"
...
##    Option         "ZAxisMapping" "4 5"
    Option         "VertEdgeScroll" "true"
....
EndSection

```

Please note I did not include the other sections of my xorg.conf . DO NOT DELETE / REMOVE ANYTHING. My solution involves commenting a line, do not delete it unless you are absolutely sure that you know what you are doing.

---

### Post by wgrant on 2008-09-06
> **syko21 said:**
> I found a solution to get normal function back. An update changed /etc/X11/xorg.conf 
Simply change your xorg.conf by commenting out the ZAxis line and add the VertEdgeScroll line.
```

Section "InputDevice"
...
##    Option         "ZAxisMapping" "4 5"
    Option         "VertEdgeScroll" "true"
....
EndSection

```

Please note I did not include the other sections of my xorg.conf . DO NOT DELETE / REMOVE ANYTHING. My solution involves commenting a line, do not delete it unless you are absolutely sure that you know what you are doing.

I fixed the Touchpad tab in the GNOME mouse capplet a couple of days ago. You should be able to do without that line in xorg.conf (in fact, you should be able to do without an xorg.conf at all), and just check the box in System->Preferences->Mouse->Touchpad.

---

### Post by patrickfromspain on 2008-10-03
If I go into the mouse propierte I don't get any Touchpad tab. Any ideas why?

---

### Post by wgrant on 2008-10-03
> **patrickfromspain said:**
> If I go into the mouse propierte I don't get any Touchpad tab. Any ideas why?

It's known, and we're trying to resolve it. Can you confirm that you get an X error when you run 'xinput list-props "SynPS/2 Synaptics TouchPad"' (replacing that device name if necessary, see 'xinput list')?

---

### Post by syko21 on 2008-10-03
> **wgrant said:**
> I fixed the Touchpad tab in the GNOME mouse capplet a couple of days ago. You should be able to do without that line in xorg.conf (in fact, you should be able to do without an xorg.conf at all), and just check the box in System->Preferences->Mouse->Touchpad.

Where do I put custom options for my touchpad I used to have in xorg.conf now so that they'll be used?

---

### Post by wgrant on 2008-10-03
> **syko21 said:**
> Where do I put custom options for my touchpad I used to have in xorg.conf now so that they'll be used?

See the Synaptics section on [https://wiki.ubuntu.com/X/Config](https://wiki.ubuntu.com/X/Config). Note that the example given there won't actually do anything (as commented just above it), but you can get the idea.

Which settings do you need? I may be able to organise their inclusion in the GUI.

---

### Post by syko21 on 2008-10-04
I use SHMConfig and RTCornerButton. For some reason the top right corner of my touchpad when touched sends firefox back a page and the RT... option fixes it.

---

### Post by wgrant on 2008-10-04
> **syko21 said:**
> I use SHMConfig and RTCornerButton. For some reason the top right corner of my touchpad when touched sends firefox back a page and the RT... option fixes it.

SHMConfig is only useful for setting other options... which options do you need SHMConfig for?

---

