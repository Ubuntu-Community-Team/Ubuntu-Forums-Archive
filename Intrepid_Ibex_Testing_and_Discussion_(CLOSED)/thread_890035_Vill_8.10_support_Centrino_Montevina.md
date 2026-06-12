---
title: "Vill 8.10 support Centrino Montevina"
date: 2008-08-14
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by Bossieman on 2008-08-14
Im thinking of buying a [Montevina]("http://en.wikipedia.org/wiki/Centrino") based Zepto computer with a Intel® GMA 4500MHD graphics card, Intel WiFi 533AN Shirley Peak B/G/N.

According to Wiki the hardware for the Montevina platform is:

an Intel Mobile 4 Express series chipset (codenamed Cantiga; GL40, GS45, GM45, GM47 or PM45) with Intel's GMA X4500 graphics technology and ICH9M southbridge, 1066 MT/s front side bus. The graphics core GM45/47 is expected to be clocked at 533/640MHz which will contain ten unified shaders, up from the eight provided by GMA X3100.

    * RAM support for DDR2-667, DDR2-800, DDR3-800, DDR3-1066 SO-DIMM.
    * NAND flash-memory caching branded as Intel Turbo Memory (codenamed Robson 2).
    * Gigabit Ethernet LAN controllers 82567LM and 82567LF (codenamed Boazman).[12].
    * Main support for DisplayPort with an external connector attached to the motherboard along with full supplemental support of HDMI, DVI, and VGA standards.

Wireless Modules

    * an Intel WiFi Link 5100/5300 mini-PCIe adapter (codenamed Shiloh), and the add-on card WiMAX (802.16) (codenamed Dana Point), or
    * the Intel combo WiFi/WiMAX Link 5150/5350 mini-PCIe adapter (code-named Echo Peak).

---

### Post by MaX on 2008-08-15
If the hardware is supported Ubuntu will probably work.

---

### Post by syxbit on 2008-08-15
don't be on that working well.

I've bought numerous laptops, and usually it takes the Ubuntu release AFTER the release that's released just after the hardware comes out.

it might work, but it's a hassle.
wireless might be iffy, sound might be iffy, graphics may be iffy (depends on what intel driver Intrepid ships)

it's nice to have the latest hardware, but it comes at a price.

i got a thinkpad t61 right when they came out (santa rosa), and it took quite a few months to even boot, and a few more for stability.
be warned. linux isn't the place for supporting the latest hardware (and if it was, ubuntu wouldn't be the place either.)

---

### Post by Nullack on 2008-08-15
Intel are one of the best hardware vendors for Linux support

---

### Post by pelle.k on 2008-08-15
> I've bought numerous laptops, and usually it takes the Ubuntu release AFTER the release that's released just after the hardware comes out.
I second that. This pisses me off every time, and by now, i really should now better. Still i keep looking an new notebooks though, and i've also been interested in buing a new nox/mythos zepto.
However, they claim to support ubuntu 8.04 OOB (if you install properitary drivers and fingerprint drivers, but the webcam is still under heavy development...).
There's always ndiswrapper for the wifi though!
In the end, i'll probably go with a trusty (linux supported) dell notebook to be on the safe side.

---

### Post by InfinityCircuit on 2008-08-15
It will support the chipset but probably not the wireless/integrated graphics.  Someone had a 5300 AGN the other day and it seemed like linux support was nonexistent--I don't know if he ever got ndiswrapper to work.  The thing to keep in mind is that although stuff like the Thinkpad T61 has Suse Enterprise as an option and thus has drivers for linux, the newer Thinkpad, etc. with this chipset don't have that option yet.

---

### Post by komesh11 on 2008-08-17
I have bought an AOpen MP45 and tried Ubuntu (both Hardy Heron and Intrepid Alpha) and the graphics card is not recognized (Intel X4500 aka Cantiga). Ubuntu will not even give me a VESA screen. Fedora did not work either. Damn Small Linux will give a VESA screen.

The Intel drivers are out:

[http://downloadcenter.intel.com/Detail_Desc.aspx?agr=Y&ProductID=2159&DwnldID=16751&strOSs=39&OSFullName=Linux*&lang=eng](http://downloadcenter.intel.com/Detail_Desc.aspx?agr=Y&ProductID=2159&DwnldID=16751&strOSs=39&OSFullName=Linux*&lang=eng)

But no support for it in the Ubuntu kernel yet.

I have found some discussions about it on the Ubuntu-bugs archive:

[http://www.mail-archive.com/ubuntu-bugs@lists.ubuntu.com/msg837892.html](http://www.mail-archive.com/ubuntu-bugs@lists.ubuntu.com/msg837892.html)

Not sure what to make of it.

Hope this helps someone.

---

### Post by Nullack on 2008-08-17
Are you saying your GPU doesnt support kernel 2.6.26.x or are you actually saying that it isnt the Ubuntu repos and you dont know how to install it manually?

What bug have you created about this problem?

---

### Post by komesh11 on 2008-08-17
I don't know how to install it manually and not sure whether it is in the repos or not. If someone could tell me how then I would test it out.

---

### Post by Nullack on 2008-08-17
Personally Im not going to offer assistance unless you either search for an existing bug about this problem and join it or create a new bug report for this :)

---

### Post by komesh11 on 2008-08-18
I created a bug for this:

Bug 258994

Any help is appreciated.

thanks.

---

### Post by Nullack on 2008-08-18
Good stuff. So we need to figure out if your boot failure is on X or the kernel. What exactly happens when you say it will not boot to a login screen?

Heres a URL with many details about G45s on Linux:

[http://www.phoronix.com/scan.php?page=article&item=intel_x4500hd&num=1](http://www.phoronix.com/scan.php?page=article&item=intel_x4500hd&num=1)

---

### Post by komesh11 on 2008-08-18
Thanks for your help.

It seems like I need xf86-video-intel 2.4.1 for my box to work. How can I check which version of xf86-video-intel is in the kernel?

---

### Post by Nullack on 2008-08-18
One way should be to look at your Xorg logs in the gnome log viewer. If not, try starting X in the extra verbose mode. I dont have that hardware specifically, but this should work. Once you find the version if its not the right one you can always compile your own if needed - you wont be stuck with non working hardware with the G45.

---

### Post by Bossieman on 2008-09-14
Good news here! Just tried out 8.10 on my Montevina Zepto Nox and sound works perfectly. The computer was delivered with Intel 4965AGN card so no problem there.

---

### Post by Charlie708 on 2008-09-25
I have been using Hardy with my T400, and it has been working well so far.  Vesa worked really well in the beginning with the 4500M, and drivers are now available.  I get a 5300 tomorrow, will report about it.

---

