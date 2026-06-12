---
title: "Kubuntu 11.10 won't boot after last package upgrade"
date: 2011-11-03
forum: Installation &amp; Upgrades
---

### Post by t-dome on 2011-11-03
Hi,

I have a Kubuntu 11.10 64 bit installation. It worked for a few days, I did update it every day, no problems. After doing an update today (no "critical" packages it seems), the orange button appeared that Linux should be restarted. After that, Kubuntu wouldn't boot anymore, not even in recovery mode.
The blue Kubuntu boot screen appears for a few seconds, but then the screen goes blank. When I immediately press Ctrl-Alt-F1 to see the what's going on, only one message appears (I can't remember it - nothing important), and then it halts.

The very strange thing is, that the original _unmodified_ USB stick with Kubuntu 11.10 x64 also doesn't start anymore, although this is the same stick I installed Kubuntu from in the first place.

Booting the previous Kubuntu version 11.04 x32 from the stick works. Windows 7 x64 from the HDD also.

System: Intel Sandy Bridge with HD 2000 graphics (that's also used), 8 GB RAM, Kubuntu 11.10 64 bit.

I'm sure I'm not the only one with this problem, it seems like Kubuntu 11.10 is a problem child. I had some other issues with the same version on another computer.

Can anyone help? I could boot from an USB stick to read some logfile from the HDD, just tell me which one if you have any idea.

Thanks

---

### Post by t-dome on 2011-11-03
Solved. In short: more of a hardware problem I guess.

Before, with CPU-Graphics, the BIOS showed 1,6 volts for the memory (my Kingston modules are rated at 1,5V).
I've even overridden the automatic settings to go to 1,5V but then the system didn't even start, weird RGB color blocks appearing, and I had to do a CMOS reset.

Besides forcing the mem voltage to 1,5V (like it should be) described above I've not altered any vital settings in the EFI BIOS.

After putting in my "spare" GeForce 8800GT card and two resets, the BIOS settings went automatically to 1,5V (I had set them to "Auto" again) and everything is working fine now: booting Kubuntu from HDD, DVD, USB, doing the memory check.

BTW, I have an Asus P8H67M-Pro B3 mainboard.

Cheers

---

