---
title: "Suspend / resume ends with black screen, white hyphen cursor on Aspire V5"
date: 2015-04-27
forum: Installation &amp; Upgrades
---

### Post by alfu2 on 2015-04-27
On an Acer Aspire V5-122P-0408, dual boot with Win 8. (I am not authorized to create a search tag for this machine, nor to use an extant tag longer than 18 chars)

Win 8 suspend/resumes perfectly, so this is not a hardware issue. The error report indicates a failure in executable **[FONT=courier new]usr/share/apport/apportcheckresume[/FONT]**

Choosing Applications/Log Out/Suspend or closing the lid initiates suspend mode. Lifting lid does nothing. Then typing a key results in disk activity, backlight, and a white non-blinking underscore cursor, which is a prompt for something. Typing 'resume' at the prompt does nothing, nor does anything else I can find.

I have made sure that **[FONT=courier new]sudo gedit etc/fstab[/FONT]** and **[FONT=courier new]sudo gedit etc/initramfs-tools/conf.d/resume[/FONT]** show the same Linux swap partition UUID, also confirmed in viewing the GParted information for the swap partition. Also tried using the ATI binary X.Org driver (the controller showed up in the Settings Manager once, never to be seen again) and the stock driver from the 14.04 install DVD. Same behavior with both of these.

Any hints?

---

### Post by kurt18947 on 2015-04-27
No expert no experience with Win8 but I believe there's something about fastboot that must be disabled in BIOS. Have you done that?

---

### Post by alfu2 on 2015-04-27
> **kurt18947 said:**
> No expert no experience with Win8 but I believe there's something about fastboot that must be disabled in BIOS. Have you done that?

Yes. If you leave fastboot enabled, you have to hit f12 for boot options to boot into Ubuntu. My install successfully gives me a choice of Ubuntu or Win 8.

---

### Post by alfu2 on 2015-05-04
I found a simple solution that worked for me: 
**[FONT=courier new]sudo apt-get install acpi[/FONT]**

[FONT=arial]from [http://askubuntu.com/questions/389909/screen-doesnt-reactivate-on-acer-aspire-v5-123](http://askubuntu.com/questions/389909/screen-doesnt-reactivate-on-acer-aspire-v5-123)

I tested it once and it worked.[/FONT] However, I still have an odd thing: selecting **application menu/Log Out** in order to get to the suspend button results in a long delay before the Log Out dialog appears. On my old H-P, it was almost instantaneous (with the same O/S install).  At first I thought it was due to encrypting the home folder during install, but I re-installed without selecting that option, and it's no better. 

I found out how to Suspend and Shut Down immediately without having to go through **Applications  Menu/Log Ou**t. Go to** Applications Menu / Settings Manager / Panel** and add  **Action Buttons (external)**. These options are then immediately  available. Everything works now, except Bluetooth, of course.

---

