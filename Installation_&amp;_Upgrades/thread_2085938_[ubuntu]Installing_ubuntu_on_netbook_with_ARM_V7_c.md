---
title: "[ubuntu]Installing ubuntu on netbook with ARM V7 cpu (WM8850)"
date: 2012-11-19
forum: Installation &amp; Upgrades
---

### Post by vasilevich on 2012-11-19
Recently I have bought this:
[http://dx.com/p/v702-7-0-lcd-android-4-0-netbook-w-wi-fi-camera-lan-hdmi-sd-slot-pink-154852](http://dx.com/p/v702-7-0-lcd-android-4-0-netbook-w-wi-fi-camera-lan-hdmi-sd-slot-pink-154852)

It has android 4.0.3
kernel 3.0.8
build number:
4.0.3 ICS Ver 1.1.0-20120801.112457

I would like to flash ubuntu instead of the android, 
I managed to run debian alongside the android using android linux installer app however thats not what i want because there was no complete xorg support, 
I want to flash the whole system using the ubuntu operating system. 
the device is rooted and I managed to flash it a few times using some roms with android with an SD card and i was wondering how to go about flashing or creating and flashing an ubuntu rom over the currently installed android rom. 
the roms I used so far look something like this:
[IMG]http://nanospic.ro/wp-content/uploads/2012/09/sd-card.bmp[/IMG]
any ideas or instructions are welcome sorry if wrong section.

---

### Post by nautilus on 2012-12-31
Well, the latest Ubuntu Core is compiled in thumb2 which the WM8850 can't handle.  The options are to run an older Ubuntu Core build on it or Debian.  I opted for Debian (Squeeze), and I run it directly off the SD card at the moment.

The steps are a bit complicated to get a working Debian filesystem and it involves bootstrapping and u-boot scripts and such, but if you're interested I could probably put the sdcard image up for download somewhere?

I should mention a few caveats; things like acpid expect .. well, ACPI, which these don't have.  So instead of the backlight brightness being somewhere like /sys/class/backlight/acpi_backlight0/brightness it's in somewhere like /sys/class/leds/lcd-backlight/brightness or something.  In short, that sort of stuff doesn't work out of the box.

Then there's power saving...  where to begin, I have barely scratched the surface.  If you are really motivated you could play with wakelocks which are available if you build the kernel with Android features.  Otherwise you have to wander the same odd sysfs tree to suspend and wake the thing.

One last note is that most Android kernels are compiled with "paranoid networking", so even once you get your Linux desktop and you pull up a browser, by default you probably won't be able to access any websites.  The trick is to associate some key groups to your user.  Read more on that at [http://www.elinux.org/Android_Security](http://www.elinux.org/Android_Security) if you like.

Otherwise, let me know how your progress at getting Ubuntu running on there comes along!  I would prefer it myself, but I'm not very familiar with making a "core", or if there's even a proper process for the general public.

---

### Post by chelovek84 on 2013-04-10
WM8850 kernel source released
[http://github.com/wondermedia/wm8850](http://github.com/wondermedia/wm8850)

---

### Post by chelovek84 on 2013-04-24
> **chelovek84 said:**
> WM8850 kernel source released
[http://github.com/wondermedia/wm8850](http://github.com/wondermedia/wm8850)


Assembly source files missing :(

Maybe be this will be somehow useful [https://github.com/apc-io/apc-8950](https://github.com/apc-io/apc-8950)

---

