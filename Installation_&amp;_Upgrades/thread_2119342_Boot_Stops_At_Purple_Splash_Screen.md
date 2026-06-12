---
title: "Boot Stops At Purple Splash Screen"
date: 2013-02-23
forum: Installation &amp; Upgrades
---

### Post by buzzingrobot on 2013-02-23
Using the instructions [here]("http://www.rodsbooks.com/ubuntu-efi/index.html"), I have 12.04.02 successfully installed on my MacBook Pro 8,2.  This install uses ReFind.

However,  while it boots with ReFind via a Super Grub2 CD, it does not boot successfully via ReFind alone.  The Grub menu displays correctly, then the purple splash screen with the Ubuntu logo in the center. As soon as the 5 red dots display under the logo, the boot stops.

How can I get the boot to complete successfully?

[EDIT:  Booting in recovery mode and then launching the failsafe graphics mode, I see that it fails to load the GLX extension and then reports "No Screens Found". Xorg.Failsafe.log shows this: "(EE) VESA(0): Cannot read V_BIOS(3) input/output error", then the vesa, int10, and vbe modules are unloaded and a fatal "No Screens Found" error is displayed.]

---

### Post by MAFoElffen on 2013-02-24
> **buzzingrobot said:**
> EDIT:  Booting in recovery mode and then launching the failsafe graphics mode, I see that it fails to load the GLX extension and then reports "No Screens Found". Xorg.Failsafe.log shows this: "(EE) VESA(0): Cannot read V_BIOS(3) input/output error", then the vesa, int10, and vbe modules are unloaded and a fatal "No Screens Found" error is displayed.

So.. as you can see by the errors, you are having a graphics problem.

You are already past grub and booting the kernel by the time it gets to the plymouth splash where you lock up.

If at the grub menu, you arrow down one to keep the menu from disappearing... then arrow to the option you want (Ubuntu)... then press <e>.

This will openthe editor on that menu item. Arrow down to the first line that starts with "linux" and replace "quiet splash" with "Single --verbose". Press <cntrl><x> to boot. This should boot the kernel and get you to a text-based tty console. 

Log in and and copy down the results of:
```

lspci -vnn | grep -i VGA

```
Post those results here

Then try:
```

startx

```
Tell me what it does.

---

