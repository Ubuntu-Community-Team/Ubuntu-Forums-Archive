---
title: "Boot priority list in BIOS: other options dissappeared, showing only &quot;ubuntu&quot;"
date: 2013-03-04
forum: Installation &amp; Upgrades
---

### Post by Deever on 2013-03-04
Hi, guys,

I have a serious issue with my ThinkPad E330 and I'm asking for your help. I installed latest Ubuntu (via USB flash drive) with full encryption sucessfully and after restart my pasword was not accepted. Probably a problem with keyboard settings, because I am sure I did not forget the password in 40 minutes.

So I tried to re-install whole system with the same USB I've already installed it before. But - boot priority list in BIOS (after pressing F1 in BIOS Setup or directly after presing F12 on start-up) shows only one option "ubuntu". No USB, no HDD, no Network options - just "ubuntu". Ths option launches dead-locked system. Here's a screen:

[IMG]http://imgbank.cz/images/2013/03/04/WP001060.jpg[/IMG]

There is also a list of possible boot settings. I've tried them all (UEFI/Legacy boot and boot mode: quick/diagnostics -all possible variants) with aboslutely no luck. Still the only one boot option: "ubuntu". 

[IMG]http://imgbank.cz/images/2013/03/04/WP001062.jpg[/IMG]

I also run Diagnostics, just to check if USB slots even work, and they do (both USB 2.0 a USB 3.0 - I've tried two different USB flash drives):

[IMG]http://imgbank.cz/images/2013/03/04/WP001067.jpg[/IMG] 

I've also tried to "load default settings" in BIOS, but it says that it would not affect boot priority settings (and, in fact, it didn't).

So I am kinda lost and desperate: How do I add the "classic" options on BIOS boot list? Why "ubuntu" just wiped other options out? 

Thank you very much for your help.

---

### Post by oldfred on 2013-03-04
IF you change UEFI first to BIOS/Legacy/CSM first does that let you then boot. And does Boot Mode shown as diagnostics also have to be changed?

---

### Post by Deever on 2013-03-04
Other option for 'boot mode' is 'quick'. Combination 'legacy first' and 'quick' also does no work. Still only 'ubuntu' is shown in boot list.

---

### Post by oldfred on 2013-03-04
I used to think UEFI went and scanned efi partition to find new boot devices. But it actually saves boot entries somewhere and you may have to use its menu to find devices.

Someone posted this, but I have no idea if you have boot maintenance manager or not.

>  Enter your UEFI menu, select "Boot maintenance manager", then "Boot options", then "Add boot option", then "NO VOLUME LABEL,....Primary,Slave...1, GPT,..", then browse the /EFI/ubuntu/ folder via the UEFI boot menu, and select the grubx64.efi . Give it the name you want (eg "Precise"), then "Commit Changes and exit", then Enter. 


Someone also posted this. Does a total cold boot (remove battery and wait a bit) work?
>  (Phoenix Tiano). The every-other boot problem is a bit decieving: What happens is it hangs on a warm/reboot. Boots work every time from cold/power-up.



---

### Post by Deever on 2013-03-04
Solved! All you need to do (it's actually simplest solution ever) is to try to **delete the "ubuntu" device**. This possibility is not obvious, because every other option is missing - so you do not know, which bootable device is "deletable" and which one is not (for example HDD or USB cannot be deleted). It's certainly a bug, but I don't know who is responsible - Ubuntu developers or BIOS developers. Anyway, after deletion of "ubuntu" option is list completely empty and after several reboots BIOS will jump to original "HDD + USB" boot options.

Thanks for you help, guys.

---

### Post by oldfred on 2013-03-04
I think you figured it out. Good to know if someone else has similar issue.

---

