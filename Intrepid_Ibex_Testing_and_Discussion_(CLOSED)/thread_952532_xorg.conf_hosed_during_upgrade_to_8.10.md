---
title: "xorg.conf hosed during upgrade to 8.10"
date: 2008-10-19
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by genfool on 2008-10-19
I did a clean install of 8.04 on a spare box all updated,  and then upgraded to 8.10.

When I reboot I get to the login screen, login. I get the gnome background with mouse pointer.
I have been searching for a couple of hours and see others have had this problem. Their fixes did not help.

My xorg.conf file has no mouse section, no keyboard section, Does have a configured monitor with no screen resolutions nothing, just says "configured monitor" same with video "configured video" no drivers listed.

I was also left without a backup. Seems there would be a tool to re-write this, I do not know the name of it.
Dell 1.8 with intel onboard video.
Thanks

---

### Post by genfool on 2008-10-19
Thanks for moving thread,as I could not find the intrepid forum before.
I see what others are doing to solve problem. Looks like I will be writing a new xorg.conf file manually.
I am new to ubuntu, I have been running sabayon and have a gentoo install I fix till broke. 
With gentoo I have a few tools that will write a new xorg file by simply answering a few questions about hardware. That is what I was looking for.

I did add "vesa" and allowed me to start x without keyboard or mouse. I will rewrite the rest now.

I recently found the NM loco team, and the next meeting, my first, will be the intrepid release party. Just wanted to get onboard.
Thanks, again

---

### Post by ktp on 2008-10-19
With 8.10 and new X, your xorg.conf will be small...everythings should be autodected.  here is min config file you will see:
```
Section "Device"
        Identifier      "Configured Video Device"
EndSection

Section "Monitor"
        Identifier      "Configured Monitor"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
EndSection

```

---

### Post by genfool on 2008-10-19
yes, that is what I had.

---

### Post by andrewabc on 2008-10-19
> **genfool said:**
> yes, that is what I had.

That is what every xorg is supposed to look like now.
Everything is autodetected now, and nothing is written to xorg by default.
You can manually edit it if you want.

Basically if autodetect doesn't work, then you are screwed and have to manually edit xorg with no guidance at all (like the previous monitor setting program)

---

### Post by autocrosser on 2008-10-19
Do some searching in this forum for hal.fdi files--I've been working on it with a couple of other guys--everything you would normally config in xorg.conf has been moved to .fdi files in /etc/hal/fdi/policy--that is where you create your mods--It's in a xml format--my keyboard mod looks like:

Name of file: 99-x11-keyboard.fdi

<?xml version="1.0" encoding="ISO-8859-1"?>
<deviceinfo version="0.2">
  <device>
    <match key="info.capabilities" contains="input.keyboard">
      <merge key="input.x11_options.XkbRules" type="string">xorg</merge>
      <merge key="input.x11_options.XkbModel" type="string">macintosh</merge>
      <merge key="input.x11_options.XkbLayout" type="string">us</merge>
    </match>
  </device>
</deviceinfo>

We've been working on a Wiki page--it's link is in the other threads.....

My thread link is: [http://ubuntuforums.org/showthread.php?t=948154](http://ubuntuforums.org/showthread.php?t=948154)

---

### Post by genfool on 2008-10-20
I want to thank Aoutocrosser for the work on hal,
I can understand my monitor not being setup, as it is a oddball lcd with some weird settings, had problems with it before. Setting video and monitor in xorg is not a big deal.
I am using usb and a kvm, they do not work when I start X. Will have to learn how to set them up in hal.

---

