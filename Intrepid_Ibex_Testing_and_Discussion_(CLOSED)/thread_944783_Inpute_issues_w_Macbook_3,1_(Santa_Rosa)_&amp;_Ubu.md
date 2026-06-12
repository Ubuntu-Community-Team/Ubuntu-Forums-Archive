---
title: "Inpute issues w/ Macbook 3,1 (Santa Rosa) &amp; Ubuntu 8.10 (Intrepid Ibex)"
date: 2008-10-11
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by C38a7r1zvl on 2008-10-11
Hi everyone!

Having been annoyed by Mac OSX for long enough now, I wanted to finally switch back to Kubuntu. Figuring that Intrepid probably supports the newerish hardware of the 3,1 model better than previous versions, I went with the beta version of it.

Installation went smooth and e.g. wifi installation was very easy. However, I ran into issues with keyboard & trackpad usage. Before going into these though, I'd like to make you all aware of a [wiki page]("https://wiki.ubuntu.com/MacBook/SantaRosa") I've started to specifically address 8.10 on a 3,1 model. Please change and/or append it according to your knowledge!

So here we go:

I am a bit stumped with getting my keyboard (it's the German variant) to work properly. I installed pommed but the only function key working is Mute.

When running xev, pressing fn alone doesn't report anything at all. fn+F1 for instance is mapped to XF86Stop whereas it should dim screen brightness.

I tried messing around with xkbd layouts and symbol tables but while dpkg-reconfigure xserver-xorg makes a backup copy of the existing xorg.conf, it does NOT change the actual xorg.conf file. Apparently xorgs autoconfigure magic has come a long way lately but unfortunately I don't know how to properly configure it now.. :)

Of course I've tried pommed and yes, it recognizes my macbook properly but no, it does not do anything. So, any pointers on this one?

[COLOR="Silver"]Also, I don't know how to configure my touchpad. I pretty much want it to behave like in OSX (right click emulation, two-finger scroll). Again, it seems to come down to how to configure xorg?[/COLOR] (**Solved!** See post below)

I don't necesserily need long step-by-steps but any pointers are greatly appreciated! If somebody could provide me with a big picture overview over the new xorg configuration process, that would be fantastic as well!

Thanks a lot!
- Niels

---

### Post by C38a7r1zvl on 2008-10-12
I've just updated [the wiki page]("https://wiki.ubuntu.com/MacBook/SantaRosa#Touchpad%20(appletouch)") with my new findings regarding touchpad functionality. 

To make your touchpad behave pretty much like under OSX just create a new file /etc/hal/fdi/policy/appletouch.fdi with the following content:
```
<?xml version="1.0" encoding="ISO-8859-1"?>
<deviceinfo version="0.2">
  <device>
    <match key="info.capabilities" contains="input.touchpad">
      <match key="info.product" contains="appletouch">
        <merge key="input.x11_driver" type="string">synaptics</merge>
        <merge key="input.x11_options.VertTwoFingerScroll" type="string">1</merge>
        <merge key="input.x11_options.HorizTwoFingerScroll" type="string">1</merge>
        <merge key="input.x11_options.TapButton1" type="string">0</merge>
        <merge key="input.x11_options.TapButton2" type="string">3</merge>
        <merge key="input.x11_options.TapButton3" type="string">2</merge>
        <merge key="input.x11_options.FingerLow" type="string">10</merge>
        <merge key="input.x11_options.FingerHigh" type="string">20</merge>
        <merge key="input.x11_options.PressureMotionMinZ" type="string">10</merge>
      </match>
    </match>
  </device>
</deviceinfo>
```

For more info [head over to the wiki]("https://wiki.ubuntu.com/MacBook/SantaRosa#Touchpad%20(appletouch)").

---

### Post by incubus on 2008-10-12
Nicely done!  Could you also update this wiki with a link to your article?

[https://wiki.ubuntu.com/X/Config](https://wiki.ubuntu.com/X/Config)

I'm guessing this new method of configuring inputs will be one of the top things that will catch people by surprise when upgrading to Intrepid.

incubus

---

### Post by C38a7r1zvl on 2008-10-12
Good idea, incubus! I've added the link under "Contributed Documentation -- Touchpad Config".

You're probably right with your guess that the whole xorg auto configuration might catch many by surprise. Personally I think it would be a good idea to ship e.g. the above mentioned appletouch.fdi right out of the box. That way, instead of being surprised by the fact that config tweakage doesn't work as in previous Ubuntu versions, users might actually be surprised by everything just working as expected without any manual intervention whatsoever. 

Do you, or others here, think this would make sense?

Best,
Niels

---

### Post by incubus on 2008-10-12
niels,

Honestly, what I would love to have is a simple article explaining the overall idea first.  I suspect I don't know how the whole thing is supposed to work in the first place.  For example, if I'm not mistaken, we're already going to ship a few files.  Take a look at:

```

/usr/share/hal/fdi/policy/

```

So as you can see, there are a few .fdi files related to apple already, although none for the touchpad as the one you wrote.  Is that the place where we'd include it?

That said, I think it would be just a matter of opening a report at launchpad and requesting its inclusion.  I don't have a macbook anymore, but I'd be happy to help you with what I can.

incubus

---

