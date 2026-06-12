---
title: "Problems with 19.10 installer/freshly installed system - graphics?"
date: 2019-11-15
forum: Installation &amp; Upgrades
---

### Post by sgage on 2019-11-15
I'm having trouble with installing Ubuntu 19.10. Attempting to boot to the regular live desktop resulted in the screen turning black, a message on the monitor saying 'no signal', and the light on the monitor turning from blue to amber. Recovering from this state required unplugging the machine.

I was able to install using the 'safe graphics' mode, and it went normally. But upon rebooting into my fresh install, the same thing happened as described above.

Does anyone know of a way I can get this to work? I've never had this problem with the Ubuntu installer - 19.04 worked just fine.

TIA

---

### Post by CatKiller on 2019-11-15
You know what would really help people that want to help you with your hardware problem? Details of your hardware.

The symptom you're seeing is because the resolution is being set to one that your monitor can't handle. Why that is no one can say from the information you've provided.

---

### Post by sgage on 2019-11-15
Sorry,

I should have added that my graphics is bog-standard Intel integrated graphics - Intel® HD Graphics 630. The monitor is an Acer v173 that can do up to 1280x1024 (which is what I run it at). CPU is Intel Core i5-7400.

I think those are the relevant details, but if more info would be helpful, I'll happily provide it.

---

### Post by oldfred on 2019-11-15
Can you boot from grub menu the recovery mode?

Intel should just work.

Arch has some useful info on Intel issues:
[https://wiki.archlinux.org/index.php/intel_graphics](https://wiki.archlinux.org/index.php/intel_graphics)

On my Skylake system I added this boot parameter, but system worked without it.
 i915.fastboot=1 kernel parameter. Fastboot helps provide a clean, flicker-free Linux boot experience.
New 5.1 kernel will include it by default on Skylake and newer

---

### Post by sgage on 2019-11-15
> **oldfred said:**
> Can you boot from grub menu the recovery mode?

Intel should just work.

Arch has some useful info on Intel issues:
[https://wiki.archlinux.org/index.php/intel_graphics](https://wiki.archlinux.org/index.php/intel_graphics)

On my Skylake system I added this boot parameter, but system worked without it.
 i915.fastboot=1 kernel parameter. Fastboot helps provide a clean, flicker-free Linux boot experience.
New 5.1 kernel will include it by default on Skylake and newer

Yes, I can boot to the recovery mode. And as I mentioned earlier, this installation was actually made by using the 'safe graphics' mode of the installer. 

I tried a couple of suggestions from the link you posted, but no joy. 

Yes, Intel should just work, and it always has. It worked for every Ubuntu from 18.04 to 19.04 on this computer with this same GPU. What changed, I wonder.

---

### Post by CatKiller on 2019-11-15
OK, that's most of it but, from the age, I'm assuming that the connection is going through some kind of adaptor. Confirmation of that would be nice.

There is a perfectly functional way of setting resolutions, called EDID: the computer asks the display which resolutions it can do, the display responds, and both ends negotiate to get something they're both happy with - normally the highest resolution the display can handle. Unfortunately your monitor is from a period where monitor manufacturers did a really crummy job of supporting EDID, and most adaptors don't pass those signals through anyway. 

So, first things first: check your cabling. The EDID signal passes through pins that are rarely used so a cheap and unscrupulous cable maker can save a couple of pence worth of copper by not bothering to connect them to anything. The same goes for any adaptors that you're using; swap them out if you have anything better. 

The next step is that you want **a** display, even if it's not the greatest yet. Using the **nomodeset** kernel option, which you can select from the Grub menu, will tell your system that you don't want it to try to change the resolution. It will just use whatever resolution the BIOS sets it to, which presumably works for you given that you said that you *could* see things in the low-graphics installer.

The next step is to make the correct resolution available for your desktop environment. The easiest way to do that is to create a config snippet in a file in /etc/X11/xorg.conf.d that describes the features of your monitor that your system would normally get from EDID. The most important values are the HorizSync and VertRefresh values, which you can normally get from the monitor manual or specifications. There seem to be several similar models with that model number, but from looking at the manual from one of them ```
HorizSync 30-80
VertRefresh 49-75
``` seems like the right sort of thing. Check the values before you use them if you are able to. You'll need to restart X for changes to the configuration to take effect. With the right values in the right format the resolution can be determined automatically even without EDID: if you've ever used a "monitor driver" in Windows, that's exactly what that does. 

Once your desktop environment is up and running at the correct resolution you can edit Grub's config so that the bootup and console screens are at the correct resolution if you want to, provided your graphics chip can do so. The resolutions that a given graphics device can do in graphical mode are not necessarily the same as the resolutions it can do in text mode.

---

### Post by sgage on 2019-11-15
Thanks for this information. I will certainly try these suggestions tomorrow morning - I have a disability that causes my eyesight to go to pieces from early-afternoon on. 

There is no kind of extra adaptor - it's just the VGA out port on the computer to the (as you surmised) relatively old monitor. The monitor does 1280x1024 just fine, and that has always been detected.

I guess what baffles me is that I've never had this problem before, and suddenly here it is. I mean, 19.04 worked fine. What changed, I wonder...

---

### Post by CatKiller on 2019-11-15
I'm at my computer now rather than trying to type it all on my phone, so I can give more information about configuring X.

The file you'll want to create will be called something like /etc/X11/xorg.conf.d/20-monitor.conf. It will need to be in that directory, I believe it needs to end in .conf, and I understand that the numbers at the front of config file names are to do with priority if two files configure the same thing, but the bit in the middle you can set as whatever you want.

Inside that file, you'll put something like

```
Section "Monitor"
        Identifier      "Configured Monitor"
        HorizSync       30-80
        VertRefresh     49-75
EndSection
```

You probably won't need the line that starts with *Identifier*, but I've put it there to remind us where it would go if you do need it. If you were doing a full xorg.conf that specified everything it wouldn't matter what you put as the Identifier *provided it is consistent throughout the file*. Here, we'd want it to be consistent with whatever X is using to describe that monitor. So don't put that line in first off but, if it doesn't work, set the Identifier to however your X log file (/var/log/Xorg.0.log) describes your monitor. It might be "Configured Monitor," "Default Monitor," or something like that. I think that, without the Identifier, it will apply to every monitor.

As to why it did work and now doesn't, I couldn't say. Intel *have* been playing around with the way that resolution is set for their flicker-free boot that oldfred alluded to. That stops the resolution being changed from how the BIOS sets it until the end of the boot process so that you don't have lots of mode changes. Possibly that's messed with the detection process, since it's now happening at a different time. There is definitely some dark art to detecting and setting the resolution, since often the proprietary Nvidia driver can do it when the open source nouveau driver can't on exactly the same hardware. I have no idea why that would be.

Actually, I've just checked, and flicker-free boot is incredibly likely to be the reason: it was turned on by default for 19.10 on UEFI systems and wasn't for 19.04. It's *possible* that turning off the Compatibility Support Module in the BIOS (which makes a UEFI system also respond to BIOS-isms) or disabling the flicker-free boot process might fix your issue without changing your X configuration. It's not something I've played with since my Intel systems are on 18.04 and almost never reboot.

---

### Post by sgage on 2019-11-16
Well, I tried the 20-monitor.conf method - no joy. I also disabled 'legacy bios mode' - no change. I tried a couple of things from the Arch wiki that seemed relevant - no go. I can't think of anything more to do, so I guess I'll be sticking with 18.04 for now, and hope this thing gets addressed in future.

Thanks all for your help! If you think of something else to try, I'm all ears, but my computer is tired of rebooting for now...

---

