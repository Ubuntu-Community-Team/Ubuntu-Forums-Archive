---
title: "xorg crash after upgrade"
date: 2009-04-05
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by davidself1001 on 2009-04-05
I decided to upgrade 9.04 beta by checking all possible upgrades in the sw sources / update tab so that I could pick up the recent nautilus (show desktop icons) bug fix.  After doing that and restarting I get xorg failures.  It doesn't seem to be able to load my nvidia driver now.  Log file is below (at least the part with errors).  How can I get back to were I was or close?

(II) NVIDIA(0): Creating default Display subsection in Screen section
	"Default Screen" for depth/fbbpp 24/32
(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(0): Option "NoLogo" "True"
(**) NVIDIA(0): Enabling RENDER acceleration
(II) NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
(II) NVIDIA(0):     enabled.
(EE) NVIDIA(0): Failed to load the NVIDIA kernel module!
(EE) NVIDIA(0):  *** Aborting ***
(II) UnloadModule: "nvidia"
(II) UnloadModule: "wfb"
(II) UnloadModule: "fb"
(EE) Screen(s) found, but none have a usable configuration.

Fatal server error:
no screens found

---

### Post by davidself1001 on 2009-04-05
Nee help bad on this one.  I am down cold.  I am running from my Windows partition (undesirable) to try to figure this out.  I didn't create a 9.04 beta CD/DVD.  Is that needed?

---

### Post by davidself1001 on 2009-04-05
Is there some other information I need to provide?

---

