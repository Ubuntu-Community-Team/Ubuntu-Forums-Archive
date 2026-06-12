---
title: "No Unity After Upgrading???"
date: 2011-05-02
forum: Installation &amp; Upgrades
---

### Post by HDTimeshifter on 2011-05-02
So I upgraded, but it says something like my system "doesn't have the resources to run Unity".  WTF???  Core 2 Quad Q6600 2.4 GHz, 6 GB, 1 TB HD, nVidia 9500 GT.  So it's not a gaming video card, but not that primitive...???  And I can't even find the Gnome menu item to force it to launch Unity...

---

### Post by mikewhatever on 2011-05-02
First, there is no menu item to force launching Unity. What a silly idea. Can you check what graphics driver you are currently using.

---

### Post by HDTimeshifter on 2011-05-02
Well booting into Windows 7 with my other drive tells me there is a memory error, so I ran Memtest 86+ and there is are memory errors at 00000000404 and 00000000003.  So I removed the 2 GB stick at A1, swapped the other 2 GB stick to B1, and moved the two 1 GB sticks from the B banks to A1 and A2.  They are all PC6400 800MHz RAM.  I ran Memtest again and it reports the errors at the exact same addresses!  Then I removed the other 2 GB stick and  errors at same addresses!  Is this a motherboard problem rather than memory?  Strange that memory would suddenly fail after 2-3 years of use and within 24 hours of doing a Windows 7 update (security and IE9) as well as Ubuntu 11.04 upgrade.

---

### Post by HDTimeshifter on 2011-05-04
Ok, so I isolated and removed the bad memory stick.

How do I turn on Unity???

---

### Post by sknagesh on 2011-05-04
Try unity from terminal.

If unity 3D do not work you can try unity-2d. But you may have to install it forst via apt-get.

---

### Post by HDTimeshifter on 2011-05-05
I get this error when I try launching Unity from a terminal:  "Cannot register the panel shell: there is already one running."

Sounds like you can't launch it from Gnome - it must be launched during startup before a desktop is started?

---

### Post by TennSeven on 2011-05-05
Go to System -> Preferences -> CompizConfig Settings Manager and enable the "Ubuntu Unity Plugin" in the "Desktop" category.

-TennSeven

---

