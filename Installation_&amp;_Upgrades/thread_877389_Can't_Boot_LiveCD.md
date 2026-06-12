---
title: "Can't Boot LiveCD"
date: 2008-08-01
forum: Installation &amp; Upgrades
---

### Post by phylae on 2008-08-01
I'm trying to get my mom's computer to run faster. It has XP, so obviously I am recommending a complete reinstall (she refuses to try ubuntu).

Since reinstalling everything takes a long time, I thought I would to the Ubuntu LiveCD to see if things are still slow in Ubuntu (just in case it is a hardware problem).

I downloaded the ISO, the md5 checksum matched. I burned the CD with Nero Burning ROM, and the verify passed.

I booted from the CD and chose to "Try without changing etc...". It looked like it was booting, but it never got into Ubuntu. I waited 45 minutes. All I saw was the orange bar bouncing back and forth (and it was going WAY WAY slower than it usually does). I pressed CTRL + ALT + F1 and it didn't list any errors. All it said was something like "loading please wait...".

I pressed CTRL + ALT + DEL and restarted. The CD booted, and this time I tried the integrity check. The same thing happened as before.

I rebooted to the CD again and entered MemTest86. That worked.

I rebooted and tried "safe graphics mode". That did the same thing as the normal boot.

I tried the CD in another computer (Dell XPS M1330 with Vista) and the LiveCD booted fine.

**Any ideas why the LiveCD won't boot?**

Here are the system specs:
Intel Pentium 4 D 830 3.0Ghz dual core 800Mhz socket 775
Generic DDR RAM PC3200 400MHz 1GB * two sticks = 2GB total
Motherboard: asus p5rd1-vm socket 775 ddr ati xpress 200 PCI-E ATX
sapphire radeon x550 pcie16x 256MB TVOUT DVI

there is also a maxtor 300GB hard drive (with Windows XP on it).
Plus there are two 500GB drives that are RAID-1. The RAID is handled by the motherboard. I think it is one of those semi-hardware ones that are not quite software-based, but close.

---

### Post by Partyboi2 on 2008-08-01
> Since reinstalling everything takes a long time, I thought I would to the Ubuntu LiveCD to see if things are still slow in Ubuntu (just in case it is a hardware problem). The live cd will be slower then if ubuntu was installed on the hard drive, so would you get an accurate idea if ubuntu was faster or slower due to hardware running the live cd? If you want to install ubuntu you could try the [[COLOR=Blue]alternate cd [/COLOR]]("http://releases.ubuntu.com/8.04.1/")which is a text base installer but this will install ubuntu.

Edit: [http://www.tweakxp.com/performance_tweaks.aspx](http://www.tweakxp.com/performance_tweaks.aspx)

---

### Post by phylae on 2008-08-01
Thanks for the link. I will look into some of those options.

I know the LiveCD will be slow, but I waited 45 minutes and it still hadn't booted. There is definitely something wrong (and it doesn't seem to be the CD that is the problem. Windows XP is running very slowly. Many times it will take 5+ minutes to open a webpage, and pretty much every application has far higher CPU usage than expected. In terms of speed, the LiveCD is normally quite liveable, while XP is not. So I want to see if the LiveCD is also slow.

I also want my mom to try the LiveCD because that might convince her to try Ubuntu.

Thanks

---

### Post by rbstern on 2008-08-01
You might try burning the CD with something other than NERO.  I had a similar problem, although I never got further than the Caldera DOS message, with CDs burned via Nero.

I burned a CD with ImgBurn, and the problem was solved.

[http://www.imgburn.com/](http://www.imgburn.com/)

---

### Post by Partyboi2 on 2008-08-01
When you are at the main menu press F6 and change the word splash to nosplash and press enter.

---

### Post by phylae on 2008-08-01
> **Partyboi2 said:**
> When you are at the main menu press F6 and change the word splash to nosplash and press enter.

I first burned a new cd (with cdrecorder), then I changed splash to nosplash and I got this error:

"139.653357 usb 1-2: device not accepting address 2, error -62"

I'm going to try again after unplugging all the USB devices (printer and scanner). Any other suggestions?

---

### Post by phylae on 2008-08-07
I never did figure out what was wrong. I think that Ubuntu didn't like her 5-in-1 memory card reader. I think it is USB-based, but there was no easy way to unplug it.

I ended up reinstalling Windows XP for her (maybe I'll get her to try Ubuntu next time her computer fails).

---

### Post by Partyboi2 on 2008-08-07
If her computer fails next time and you decide to try ubuntu again, try using ```
debian-installer/probe/usb=false
``` as a boot option (f6 at the main menu)

---

### Post by lukjad on 2008-08-07
To try another lighter distro might help. Look up Puppy Linux, esp. TEENpup and burn that CD. It may just work better for a test. Also, sometime it is simply that you have the CD in the wrong CD/DVD drive. If your Mom's PC has more than one CD/DVD drive, try the other drive. Also, sometimes if there is only one drive and it is set to slave it can cause problems.

If none of these work, feel free to PM me to remind me of this thread. Keep on posting!

Hope this helped.

---

### Post by SkonesMickLoud on 2008-08-07
Try burning the .iso to a CD using something other than Nero, and burn at 4x or less.

You could also use Wubi to "nest" Ubuntu inside of XP:

[http://wubi-installer.org/](http://wubi-installer.org/)

---

### Post by phylae on 2008-08-08
Thanks for the suggestions. I will have to keep those in mind next time I visit my mom!

---

