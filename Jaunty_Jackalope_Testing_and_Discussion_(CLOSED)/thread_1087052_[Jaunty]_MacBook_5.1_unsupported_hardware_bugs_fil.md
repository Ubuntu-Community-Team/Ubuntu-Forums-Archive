---
title: "[Jaunty] MacBook 5.1 unsupported hardware bugs filed"
date: 2009-03-04
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by gotgenes on 2009-03-04
Today I filed several bug reports for unsupported hardware on the Apple MacBook 5.1 (aluminum unibody MacBook) on Launchpad for the Mactel support team and Ubuntu developers to take a look at, per cyberdork33's suggestion.

[LIST]
[*][touchpad]("https://bugs.launchpad.net/mactel-support/+bug/337935")
[*][Caps Lock LED]("https://bugs.launchpad.net/mactel-support/+bug/337941")
[*][keyboard backlight]("https://bugs.launchpad.net/mactel-support/+bug/337945")
[*][sound]("https://bugs.launchpad.net/mactel-support/+bug/337947")
[*][reboot]("https://bugs.launchpad.net/mactel-support/+bug/338083")
[/LIST]

Please add any reports you file to this thread.

---

### Post by inphektion on 2009-03-04
thanks.  I think that covers my issues...

---

### Post by cyberdork33 on 2009-03-04
I think the key thing missing for the keyboard problems is the hal interface to applesmc (hal-applesmc package). I added some packages to the bugs.

---

### Post by _mario_ on 2009-03-05
> **cyberdork33 said:**
> I think the key thing missing for the keyboard problems is the hal interface to applesmc (hal-applesmc package). I added some packages to the bugs.

yes. as far as i know the key differences between the ubuntu version (jaunty) and its corresponding PPA dkms packages are as follows:

[LIST]
[*]**applesmc-dkms**: adds support for MacBook Air 2 and MacPro 3.
[*]**bcm5974-dkms**: adds support for MacBook 5, MacBook Pro 5, MacBook Air 2 (Wellspring3 devices) and its special integrated button.
[*]**hid-dkms**: seems to be obsolete in jaunty. the kernel keycodes for F3 and F4 (Expose/Dashboard) changed to newly created constants that aren't currently assigned keysyms by X11.
[*]**mbp-nvidia-bl-dkms**: adds support for MacBook 5, MacBook Pro 5, MacBook Air 2.
[*]**nvidia-bl-dkms**: not available upstream. but better brightness control on machines incorporating nvidia graphics chips. unfortunately, known to **not work** on **MacBook Pro 5**.
[*]**usbhid-dkms**: too complex to compare the sources. according to the package description, should be obsolete. works on my machine (MacBook Pro 4) which is handled similarly by the new module hid_apple.
[/LIST]

ciao,
Mario

---

### Post by cyberdork33 on 2009-03-05
> **_mario_ said:**
> **applesmc-dkms**: adds support for MacBook Air 2 and MacPro 3.
I haven't been able to get the repo version or this version to work on my iMac5,1 or my MBP4,1 and I am positive that it worked on my iMac previously (I was marked as a tester for the patch).

> **_mario_ said:**
> **hid-dkms**: seems to be obsolete in jaunty. the kernel keycodes for F3 and F4 (Expose/Dashboard) changed to newly created constants that aren't currently assigned keysyms by X11.That was patched in the kernel I believe. I still haven't been able to get them to do actions in compiz though... xev does show keycodes for them though.> **_mario_ said:**
> **usbhid-dkms**: too complex to compare the sources. according to the package description, should be obsolete. works on my machine (MacBook Pro 4) which is handled similarly by the new module hid_apple. That appears to be the case on my MBP4,1 as well. Does this work on the version 5 hardware though? I believe that support for that hardware is what this dkms package provided.

---

### Post by _mario_ on 2009-03-05
> **cyberdork33 said:**
> I haven't been able to get the repo version or this version to work on my iMac5,1 or my MBP4,1 and I am positive that it worked on my iMac previously (I was marked as a tester for the patch).
i can confirm that the PPA version does work on my MBP4,1. the repo version might work as well. never tried again since Hardy whose version didn't work at that time.

> **cyberdork33 said:**
> 
That was patched in the kernel I believe. I still haven't been able to get them to do actions in compiz though... xev does show keycodes for them though.

does xev also show a keysym? if yes, you should be able to assign arbitrary functions in compiz. otherwise you'll have to add a keysym manually via xmodmap or patch your X11 keyboard layout definition. that's what i did.

> **cyberdork33 said:**
> 
That appears to be the case on my MBP4,1 as well. Does this work on the version 5 hardware though? I believe that support for that hardware is what this dkms package provided.

this package has been created to finally overcome the need to add those annoying and error-prone usbhid quirks. remember? ;-) this stuff finally went into the upstream version (including Wellspring3 devices incorporated into 5th gen machines).

ciao,
Mario

---

### Post by cyberdork33 on 2009-03-05
OK I will try with the applesmc module again. It might be because I am booting via EFI...

---

