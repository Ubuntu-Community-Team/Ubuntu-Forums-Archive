---
title: "Support for new release (20.04 LTS) on a Dell notebook?"
date: 2020-06-12
forum: Installation &amp; Upgrades
---

### Post by pamctn on 2020-06-12
Hello,
I post this question here but I'm not sure this is the right section of the forums for this topic. I did a little research and did not find answers.

I would like to purchase a Dell Laptop with Ubuntu preinstalled. This is the notebook: [https://www.dell.com/it-it/shop/cty/pdp/spd/g-series-15-3500-laptop/cng3003](https://www.dell.com/it-it/shop/cty/pdp/spd/g-series-15-3500-laptop/cng3003) (cannot find the same model on the USA site)

It comes with Ubuntu 18.04 preinstalled, but I see that 20.04 has already been released.
I have many doubts therefore.
Am I buying an obsolete machine? Is there a chance I wont' be able to run newer software? Will I be able to upgrade to 20.04 if needed or does Dell use their own custom made images to install?

Sorry if this topic has already been discussed somewhere else.
Thanks in advance for any advice provided.
Paolo

---

### Post by CatKiller on 2020-06-12
Dell already have 20.04 images that they're testing. When the tests are complete they'll start selling machines with 20.04 instead of 18.04. Dell's product cycle isn't synchronised with Ubuntu's release cycle, and they only use LTS releases, so it happens from time to time that they're selling machines with the previous LTS release for a while. 

There shouldn't be any problem with installing 20.04 yourself, or upgrading the 18.04 to 20.04, and Dell upstream any changes that need to be made for the hardware. You'll potentially miss out on anything that they find in this testing period - I know that fingerprint reader support was something that they were working on - that hadn't been upstreamed yet. Whether that's worth it to you to wait till the machines get the new image I really couldn't say.

---

### Post by ActionParsnip on 2020-06-12
You can upgrade 18.04 to 20.04 as LTS to the next LTS upgrades are supported. 18.04 is also still very supported all the way up to April 2023 so is far from obsolete

---

### Post by pamctn on 2020-06-12
> **CatKiller said:**
> 
There shouldn't be any problem with installing 20.04 yourself, or upgrading the 18.04 to 20.04, and Dell upstream any changes that need to be made for the hardware. 
So, does this mean Dell migh tbe working on the newer release to fix compatibility problems on "older" laptops as well? I don't know their policy about this, and their web site does not provide much information about this.

---

### Post by pamctn on 2020-06-12
Thank for your reply. "Supported" here means by Canonical, not Dell, do I understand correctly?
So, from a "software" point of view my system will be able to upgrade to the next release but I might experience some compatibility issues with some of my hardware?

---

### Post by GhX6GZMB on 2020-06-12
I wouldn't worry about this. Of course an "official" Dell release would be nice, but it's in no way vital.
You have to realize that all PCs, be it laptops or desktops rely on the same chipsets from a few semiconductor manufacturers. It's not like there are 1000s of different setups.

My experience is, that the standard (x)Ubuntu installer is excellent at recognizing hardware and installing the right drivers. There is an "icky" corner when it comes to GPUs though, where in some cases only proprietary drivers are available. This might cause issues.
If it does, reinstall and allow proprietary drivers during install.

---

### Post by CatKiller on 2020-06-12
> **pamctn said:**
> So, does this mean Dell migh tbe working on the newer release to fix compatibility problems on "older" laptops as well? I don't know their policy about this, and their web site does not provide much information about this.

The ones that come with Linux on, yeah, but they do it by sending whatever fixes are needed upstream rather than really distributing themselves. If the driver, or quirk, or whatever else needs fixing, is handled upstream, then it benefits you whichever distro you use. And means that they don't have to be the only ones maintaining it, of course. I think they have repositories configured when you buy them so that any fixes that are needed for that machine are available even if they haven't made it upstream yet.

Canonical also have a facility where they get hardware and put Ubuntu on it, to set if there's anything that needs fixing. Then the fixes can go into Ubuntu releases and, again, get passed upstream.

I think my XPS 13 came with 14.04 on it, and now it's running 20.04, and it's been flawless all the way.

---

### Post by SeijiSensei on 2020-06-12
> **ml9104 said:**
> There is an "icky" corner when it comes to GPUs though, where in some cases only proprietary drivers are available. This might cause issues. If it does, reinstall and allow proprietary drivers during install.

First I'd visit the Driver Manager in System Settings. It installed the correct NVIDIA driver for my hardware. On 20.04, it detected a USB wifi with the 802.11ac RTL8812 chipset, downloaded the driver source code, and compiled and installed the driver.

My bet is a generic Dell will have all-Intel hardware for which Intel provides the driver source code. It is incorporated into the Linux kernel source.

---

### Post by pamctn on 2020-06-14
Sorry I couldn't answer before but I have been away from my PC. Thanks for all the answers.
I've had mixed experience when trying to install Linux on non-certified hardware (like temperature control not working properly, battery drainage, ecc.) but that was on rather old hardware.
From your answers I understand this should not be a problem here,and that Dell and Canonical should be able to fix most compatibility issues (if I understand correctly)
I'm also somehow concerned that "newer" software on Ubuntu 18.04  might fail to work because you need to upgrade your system, file "XXX" is obsolete, driver "yyy" is no more supported, ecc. and thus needing an early upgrade.
Well. we'll see.

---

### Post by mrdc76 on 2020-06-14
> **pamctn said:**
> Sorry I couldn't answer before but I have been away from my PC. Thanks for all the answers.
I'm also somehow concerned that "newer" software on Ubuntu 18.04  might fail to work because you need to upgrade your system, file "XXX" is obsolete, driver "yyy" is no more supported, ecc. and thus needing an early upgrade.
Well. we'll see.

You are not getting newer software for the 18.04 except as snaps, which will work, or from PPAs, which will also work as they would be designed for this purpose. Binaries downloaded from the Web will eventually cause problems, as developers will target newer distributions, but in that case, would should upgrade from 18.04 to 20.04 anyway.

---

### Post by pamctn on 2020-06-14
Ok, so I see the problem could be with proprietay / third party software. In that case I assume I'll just try and switch to 20.04.
Thanks for your answer.

---

### Post by GhX6GZMB on 2020-06-14
> **pamctn said:**
> 
I'm also somehow concerned that "newer" software on Ubuntu 18.04  might fail to work because you need to upgrade your system, file "XXX" is obsolete, driver "yyy" is no more supported, ecc. and thus needing an early upgrade.
Well. we'll see.

This is where you're wrong. This kind of concern I've labelled "Microsoft thinking", and it's hard to get away from (but you'll learn :)  ).
Fact is, that once a driver or other necessary stuff is in the Linux world, it stays there and is available for later installations/hardware. This is decidedly different to the M$ approach, where "planned obsolescence" is part of the business model.

This was a major revelation to me when starting with (x)Ubuntu.

---

### Post by pamctn on 2020-06-15
Ok, I think I'll get one of the models with 18.04 preinstalled and cross my fingers when I'll need to upgrade... hope all of the hardware will be supported alsp under 20.04 and work fine!
Thanks for all the replies

---

### Post by GhX6GZMB on 2020-06-16
If the HW works under 18.04, it will also work under 20.04. You really need to get away from the MS mindset :)

I've never bought a PC with preinstalled Ubuntu myself, but perhaps it's not a bad idea.

---

### Post by pamctn on 2020-06-17
This is what still confuses me.
If I understand well, Dell have their own images (in this case it is a customized 18.04), with tweaks for each of their models, to ensure everything is working properly.
If a new release comes out (20.04), I would be installing the "standard" version without the tweaks from Dell as they don't support the upgrade (from their site). Or does everything get "passed on" to the next release as well? So, also specific tweaks for existing hardware?

---

### Post by CatKiller on 2020-06-17
*If* Dell have had to heavily customise the image for that hardware, and those customisations haven't made it upstream yet, then you would miss out on those customisations by switching to a vanilla install.

However, Dell try to pick Linux-friendly hardware in the first place, since they don't *want* to do lots of customisation. They just want to sell things with Linux on that work easily with Linux on.

They have repositories where they put their own bits, should they be needed. If you get a Dell machine with Linux pre-installed make a note of these repositories and then you'll be able to add them again to still have access to Dell's software if you switch to a vanilla install. An upgrade will disable external repositories, but you could also re-enable them again.

---

### Post by GhX6GZMB on 2020-06-17
> **pamctn said:**
> This is what still confuses me.
If I understand well, Dell have their own images (in this case it is a customized 18.04), with tweaks for each of their models, to ensure everything is working properly.
If a new release comes out (20.04), I would be installing the "standard" version without the tweaks from Dell as they don't support the upgrade (from their site). Or does everything get "passed on" to the next release as well? So, also specific tweaks for existing hardware?

That's not how GNU/Linux works. There are no "proprietary" Dell "tweaks" as such. If there are, Dell is obliged to share them with the community*. All old "tweaks" are in the common Linux repositories. I'm working on a 12 years old HP/Compaq and have had zero problems getting drivers installed for it. As soon as it's in the Linux repositories, it stays there.

I'd have absolutely no qualms about installing 20.04 on a new Dell PC, even if Dell does not have an "official" release.

I strongly suspect that the Dell position is about warranty when delivering a PC with factory-installed OS, not about functionality.

*) there are exceptions to this, mainly concerning GPUs where only proprietary drivers are available.

---

### Post by CatKiller on 2020-06-17
> **ml9104 said:**
> There are no "proprietary" Dell "tweaks" as such.

As an example, the very first Developer Edition XPS 13 had a touchpad that was really finicky. They fixed up the configuration for the software they distributed, upstreamed what they'd done, and moved all their XPS 13s (Developer Edition and Windows both) to a more Linux-friendly touchpad for later hardware revisions. That's the kind of thing. For current hardware I know that the fingerprint reader is something that they're working on, so that may come sooner if you're getting your software directly from Dell. It all gets upstreamed, because who wants to keep maintaining that stuff?

---

### Post by GhX6GZMB on 2020-06-17
@pamctn:
Just for translation (I see you're relatively new to this), "upstream" and "upstreaming" means that when you (or Dell) improve or optimize something, you send these changes back to the original/previous developer/maintainer of the package you've changed.
This way, it will be spread to all users along the way, as it will then be incorporated in the Linux repositories/installs (pending approval, of course).

It's a fantastic mechanism, and to my mind has brought Linux way ahead of M$ at this point. 10 years ago I would have said something different, but with the momentum it's developed, it's immensely powerful.

---

### Post by pamctn on 2020-06-19
Thanks for all the info. Actually I don't know much about how new releases are developed, and how support for new /old "stuff" works.
All of your answers have been really useful and provided lots onf info and useful suggestions. 
Thanks for clarifying the meaning of upstreaming, it actually wasn't clear at all for me. Also, thanks for the suggestions about the repositories.
Now it's all about choosing between a G3 anda a G5, but that's a differents history! :-)

---

### Post by TheFu on 2020-06-24
Just saw this announcement: [https://www.phoronix.com/scan.php?page=news_item&px=Dell-XPS-Ubuntu-20.04-Shipping](https://www.phoronix.com/scan.php?page=news_item&px=Dell-XPS-Ubuntu-20.04-Shipping)
> As of today, the Dell XPS 13 Developer Edition with 10th Gen Intel Core CPU is now offering a pre-install with 20.04 LTS rather than the two-year-old Ubuntu 18.04 LTS. 

More: [https://www.dell.com/en-us/work/shop/cty/pdp/spd/xps-13-9300-laptop/ctox13w10p1c2700u](https://www.dell.com/en-us/work/shop/cty/pdp/spd/xps-13-9300-laptop/ctox13w10p1c2700u)

---

### Post by exhile on 2020-07-01
I will be purchasing a Dell XPS 13 9300 with Ubuntu 20.04 preinstalled. I selected the 3840&#8201;×&#8201;2400 (WQUXGA) display as well. Just curious if anyone has used terminal at that small of a resolution?

---

### Post by TheFu on 2020-07-01
Shouldn't matter. Just set the font size as you like.  That's been possible at least 30 yrs.

---

### Post by exhile on 2020-07-02
> **TheFu said:**
> Shouldn't matter. Just set the font size as you like.  That's been possible at least 30 yrs.

Thanks for the reply! Yeah, you're probably right though I am accustomed to a 1920x1080 screen and not a 3840x2400 screen.

---

### Post by TheFu on 2020-07-02
> **exhile said:**
> Thanks for the reply! Yeah, you're probably right though I am accustomed to a 1920x1080 screen and not a 3840x2400 screen.

Probably? <rbg>  You can control the font, font size, foreground and background colors for xterms. 
```
uxterm -sb -fs 18 -bg black -fg yellow -fa 'Monospace' -u8  &
```
You can change the font size while running an xterm or uxterm using the ... let me try it ... <cnt>+right mouse button. Hold the right button down until the menu is displayed. The size options are relative to the size specified when running.  Xterms have been around at least 30 yrs.  If a "modern" terminal doesn't support it, get a better terminal. Seriously.

---

### Post by exhile on 2020-07-02
> **TheFu said:**
> Probably? <rbg>  You can control the font, font size, foreground and background colors for xterms. 
```
uxterm -sb -fs 18 -bg black -fg yellow -fa 'Monospace' -u8  &
```
You can change the font size while running an xterm or uxterm using the ... let me try it ... <cnt>+right mouse button. Hold the right button down until the menu is displayed. The size options are relative to the size specified when running.  Xterms have been around at least 30 yrs.  If a "modern" terminal doesn't support it, get a better terminal. Seriously.

I appreciate the assistance; however, I will have to wait until the delivery of my XPS 9300 to actually try your suggestion. Supposedly my XPS 9300 will arrive on August 5th which is one day before 20.04.1 is scheduled to be released. What a coincidence but yeah, 1 month of waiting.

---

### Post by TheFu on 2020-07-02
Uh ... this is a general command that should work on any Unix system with a GUI.  See the "18"?  That's the font size.  Play with it on your current workstation.

---

### Post by corradoventu on 2020-07-03
I'm using Ubuntu 20.04 and 20.10 on a  different Dell laptop (I removed Windows) and I see no problems, all hardware is well supported.
```
corrado@corrado-n3-gorilla:~$ inxi -SCGx
System:    Host: corrado-n3-gorilla Kernel: 5.4.0-26-generic x86_64 bits: 64 compiler: gcc v: 9.3.0 
           Desktop: GNOME 3.36.3 Distro: Ubuntu 20.10 (Groovy Gorilla) 
CPU:       Topology: Quad Core model: Intel Core i5-1035G1 bits: 64 type: MT MCP arch: Ice Lake rev: 5 
           L2 cache: 6144 KiB 
           flags: avx avx2 lm nx pae sse sse2 sse3 sse4_1 sse4_2 ssse3 vmx bogomips: 19046 
           Speed: 3601 MHz min/max: 400/3600 MHz Core speeds (MHz): 1: 3601 2: 2974 3: 1879 4: 1701 5: 2309 
           6: 2457 7: 1591 8: 3425 
Graphics:  Device-1: Intel Iris Plus Graphics G1 vendor: Dell driver: i915 v: kernel bus ID: 00:02.0 
           Device-2: Realtek Integrated_Webcam_HD type: USB driver: uvcvideo bus ID: 1-6:3 
           Display: x11 server: X.Org 1.20.8 driver: modesetting unloaded: fbdev,vesa 
           resolution: 1920x1080~60Hz 
           OpenGL: renderer: Mesa Intel UHD Graphics (ICL GT1) v: 4.6 Mesa 20.1.2 direct render: Yes 
corrado@corrado-n3-gorilla:~$ 

```

---

### Post by exhile on 2020-07-18
Well, I got my Dell XPS13 9300. It's a very nice laptop.

```
user@XPS13:~$ inxi -SCGx
System:
  Host: XPS13 Kernel: 5.4.0-40-generic x86_64 bits: 64 compiler: gcc 
  v: 9.3.0 Desktop: Gnome 3.36.1 Distro: Ubuntu 20.04 LTS (Focal Fossa) 
CPU:
  Topology: Quad Core model: Intel Core i7-1065G7 bits: 64 type: MT MCP 
  arch: Ice Lake rev: 5 L2 cache: 8192 KiB 
  flags: avx avx2 lm nx pae sse sse2 sse3 sse4_1 sse4_2 ssse3 vmx 
  bogomips: 23961 
  Speed: 1001 MHz min/max: 400/3900 MHz Core speeds (MHz): 1: 917 2: 900 
  3: 900 4: 900 5: 901 6: 900 7: 900 8: 902 
Graphics:
  Device-1: Intel Iris Plus Graphics G7 vendor: Dell driver: i915 v: kernel 
  bus ID: 00:02.0 
  Display: x11 server: X.Org 1.20.8 driver: modesetting unloaded: fbdev,vesa 
  tty: N/A 
  OpenGL: renderer: Mesa Intel Iris Plus Graphics (ICL GT2) 
  v: 4.6 Mesa 20.0.8 direct render: Yes 
user@XPS13:~$ 

```

```
user@XPS13:~$ inxi -Fxz
System:
  Kernel: 5.4.0-40-generic x86_64 bits: 64 compiler: gcc v: 9.3.0 
  Desktop: Gnome 3.36.1 Distro: Ubuntu 20.04 LTS (Focal Fossa) 
Machine:
  Type: Laptop System: Dell product: XPS 13 9300 v: N/A serial: <filter> 
  Mobo: Dell model: 077Y9N v: A00 serial: <filter> UEFI: Dell v: 1.0.11 
  date: 05/08/2020 
Battery:
  ID-1: BAT0 charge: 51.0 Wh condition: 51.0/51.0 Wh (100%) 
  model: LGC-LGC6.5 DELL 2XXFW05 status: Full 
CPU:
  Topology: Quad Core model: Intel Core i7-1065G7 bits: 64 type: MT MCP arch: Ice Lake 
  rev: 5 L2 cache: 8192 KiB 
  flags: avx avx2 lm nx pae sse sse2 sse3 sse4_1 sse4_2 ssse3 vmx bogomips: 23961 
  Speed: 1000 MHz min/max: 400/3900 MHz Core speeds (MHz): 1: 1000 2: 1000 3: 1000 
  4: 1001 5: 1000 6: 1000 7: 1000 8: 1001 
Graphics:
  Device-1: Intel Iris Plus Graphics G7 vendor: Dell driver: i915 v: kernel 
  bus ID: 00:02.0 
  Display: x11 server: X.Org 1.20.8 driver: modesetting unloaded: fbdev,vesa 
  resolution: 1920x1200~60Hz 
  OpenGL: renderer: Mesa Intel Iris Plus Graphics (ICL GT2) v: 4.6 Mesa 20.0.8 
  direct render: Yes 
Audio:
  Device-1: Intel Smart Sound Audio vendor: Dell driver: snd_hda_intel v: kernel 
  bus ID: 00:1f.3 
  Sound Server: ALSA v: k5.4.0-40-generic 
Network:
  Device-1: Intel Killer Wi-Fi 6 AX1650i 160MHz Wireless Network Adapter 
  vendor: Bigfoot Networks driver: iwlwifi v: kernel port: 4000 bus ID: 00:14.3 
  IF: wlp0s20f3 state: up mac: <filter> 
Drives:
  Local Storage: total: 238.47 GiB used: 32.43 GiB (13.6%) 
  ID-1: /dev/nvme0n1 model: CL1-3D256-Q11 NVMe SSSTC 256GB size: 238.47 GiB 
Partition:
  ID-1: / size: 225.10 GiB used: 32.40 GiB (14.4%) fs: ext4 dev: /dev/nvme0n1p3 
Sensors:
  System Temperatures: cpu: 43.0 C mobo: N/A 
  Fan Speeds (RPM): N/A 
Info:
  Processes: 281 Uptime: 2h 14m Memory: 15.23 GiB used: 3.22 GiB (21.1%) Init: systemd 
  runlevel: 5 Compilers: gcc: 9.3.0 Shell: bash v: 5.0.17 inxi: 3.0.38 
user@XPS13:~$ 

```

---

