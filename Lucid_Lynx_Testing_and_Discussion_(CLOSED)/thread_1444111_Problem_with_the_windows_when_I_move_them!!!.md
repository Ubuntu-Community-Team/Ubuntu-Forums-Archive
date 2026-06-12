---
title: "Problem with the windows when I move them!!!"
date: 2010-03-31
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by TheNerdAL on 2010-03-31
Okay so sometimes when I move the windows, it just messes up. What could it be? I have print screens included. Thanks! :D 

I'm running Ubuntu 10.04 but it happened to 9.10 too.

---

### Post by marshmallow1304 on 2010-03-31
Looks like a Compiz problem.  Does it happen when you disable desktop effects?

---

### Post by TheNerdAL on 2010-03-31
> **marshmallow1304 said:**
> Looks like a Compiz problem.  Does it happen when you disable desktop effects?

Compiz is not enabled and I have no desktop effects on because my graphics card isn't supported.

---

### Post by shaun_54au2 on 2010-03-31
What graphics card do you use: Nvidia geforce...ati radeon...intel gma...?

---

### Post by TheNerdAL on 2010-03-31
> **shaun_54au2 said:**
> What graphics card do you use?  Desktop or Laptop?

I think SiS Graphics card and desktop.

---

### Post by shaun_54au2 on 2010-03-31
hmmm

---

### Post by shaun_54au2 on 2010-03-31
onboard or pci express...?

---

### Post by TheNerdAL on 2010-03-31
> **shaun_54au2 said:**
> onboard or pci express...?

I have no idea. How do I make sure?

---

### Post by shaun_54au2 on 2010-03-31
if its a desktop computer, check where you connect your monitor.

If you connect where all your other ports are then your using onboard.
If you connect where your pci slots go horizontal its a dedicated card.

SIS sounds like onboard though.

---

### Post by shaun_54au2 on 2010-03-31
One thing you could try is to add a dedicated graphics card, maybe nvidia, install the right driver, and see if the problem continues.

---

### Post by TheNerdAL on 2010-03-31
> **shaun_54au2 said:**
> if its a desktop computer, check where you connect your monitor.

If you connect where all your other ports are then your using onboard.
If you connect where your pci slots go horizontal its a dedicated card.

SIS sounds like onboard though.

Yup. Onboard.

---

### Post by shaun_54au2 on 2010-03-31
depending on what type of slot you have in your computer...agp, pci, pci express x16, pci express x16 2.0,  you can get a pretty cheap priced card for an easy fix.

[http://www.newegg.com/Store/SubCategory.aspx?SubCategory=48&name=Desktop-Graphics-Video-Cards](http://www.newegg.com/Store/SubCategory.aspx?SubCategory=48&name=Desktop-Graphics-Video-Cards)

---

### Post by TheNerdAL on 2010-04-01
> **shaun_54au2 said:**
> depending on what type of slot you have in your computer...agp, pci, pci express x16, pci express x16 2.0,  you can get a pretty cheap priced card for an easy fix.

[http://www.newegg.com/Store/SubCategory.aspx?SubCategory=48&name=Desktop-Graphics-Video-Cards](http://www.newegg.com/Store/SubCategory.aspx?SubCategory=48&name=Desktop-Graphics-Video-Cards)

Ahhh, so basically get a new video card huh? If I do get one, will I be able to use Desktop Effects or is that a different card?

---

### Post by shaun_54au2 on 2010-04-01
Just be careful to get a card with supported linux drivers.

ati:  [http://support.amd.com/us/gpudownload/Pages/index.aspx](http://support.amd.com/us/gpudownload/Pages/index.aspx)

nvidia: [http://www.nvidia.com/Download/index5.aspx?lang=en-us](http://www.nvidia.com/Download/index5.aspx?lang=en-us)

---

### Post by shaun_54au2 on 2010-04-01
> **TheNerdAL said:**
> Ahhh, so basically get a new video card huh? If I do get one, will I be able to use Desktop Effects or is that a different card?
  

As long as the card has supported drivers desktop effects should work with no problems.  I have gotten very good results with NVIDIA myself.  I can even do some gaming.

---

### Post by TheNerdAL on 2010-04-01
> **shaun_54au2 said:**
> Just be careful to get a card with supported linux drivers.

ati:  [http://support.amd.com/us/gpudownload/Pages/index.aspx](http://support.amd.com/us/gpudownload/Pages/index.aspx)

nvidia: [http://www.nvidia.com/Download/index5.aspx?lang=en-us](http://www.nvidia.com/Download/index5.aspx?lang=en-us)

Sweet! :D I think it's VGA though. Hmm.. I just wish there was a way to fix it without spending like 100 bucks or so. like updating the drivers.

---

### Post by shaun_54au2 on 2010-04-01
> **TheNerdAL said:**
> Sweet! :D I think it's VGA though. Hmm.. I just wish there was a way to fix it without spending like 100 bucks or so. like updating the drivers.


The most you might have to spend is maybe 40.00 including shipping:

[http://www.newegg.com/Store/SubCateg...cs-Video-Cards]("http://www.newegg.com/Store/SubCategory.aspx?SubCategory=48&name=Desktop-Graphics-Video-Cards")

---

### Post by TheNerdAL on 2010-04-01
> **shaun_54au2 said:**
> The most you might have to spend is maybe 40.00 including shipping:

[http://www.newegg.com/Store/SubCateg...cs-Video-Cards]("http://www.newegg.com/Store/SubCategory.aspx?SubCategory=48&name=Desktop-Graphics-Video-Cards")

Thanks! :D Ima ask my for that for my birthday. :P But if there is any other way to try and fix it, I would love to try it.

---

### Post by shaun_54au2 on 2010-04-01
there is some driver information here
[http://www.sis.com/support/support_faqs_16.htm](http://www.sis.com/support/support_faqs_16.htm)

for sis graphics card but from the looks of it you might already be running the most compatible sis graphics driver.

---

### Post by shaun_54au2 on 2010-04-01
you could try checking to verify whether there is a proprietary driver or not installed.

Run a terminal and type** jockey-gtk**

If there are any sis related drivers there and they are not activated you could activate them and see if that helps.

Another thing you could try is to run** update manager **and see if there are any updates that might fix the problem you are having.

---

### Post by shaun_54au2 on 2010-04-01
> **TheNerdAL said:**
> Thanks! :D Ima ask my for that for my birthday. :P But if there is any other way to try and fix it, I would love to try it.


you could try checking to verify whether there is a proprietary driver or not installed.

Run a terminal and type** jockey-gtk**

If there are any sis related drivers there and they are not activated you could activate them and see if that helps.

Another thing you could try is to run** update manager **and see if there are any updates that might fix the problem you are having.

[IMG]http://ubuntuforums.org/images/misc/progress.gif[/IMG]

---

### Post by TheNerdAL on 2010-04-01
> **shaun_54au2 said:**
> there is some driver information here
[http://www.sis.com/support/support_faqs_16.htm](http://www.sis.com/support/support_faqs_16.htm)

for sis graphics card but from the looks of it you might already be running the most compatible sis graphics driver.
I used:
```
lspci
```
And got this:
```
00:00.0 Host bridge: Silicon Integrated Systems [SiS] 760/M760 Host (rev 02)
00:01.0 PCI bridge: Silicon Integrated Systems [SiS] SG86C202
00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS964 [MuTIOL Media IO] (rev 36)
00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE] (rev 01)
00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] AC'97 Sound Controller (rev a0)
00:03.0 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.1 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.2 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.3 USB Controller: Silicon Integrated Systems [SiS] USB 2.0 Controller
00:04.0 Ethernet controller: Silicon Integrated Systems [SiS] SiS900 PCI Fast Ethernet (rev 90)
00:05.0 IDE interface: Silicon Integrated Systems [SiS] RAID bus controller 180 SATA/PATA [SiS] (rev 01)
00:0a.0 Communication controller: Conexant Systems, Inc. Device 2702 (rev 01)
00:0b.0 FireWire (IEEE 1394): VIA Technologies, Inc. VT6306/7/8 [Fire II(M)] IEEE 1394 OHCI Controller (rev 80)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 661/741/760 PCI/AGP or 662/761Gx PCIE VGA Display Adapter
```

Would that help?

---

### Post by TheNerdAL on 2010-04-01
> **shaun_54au2 said:**
> you could try checking to verify whether there is a proprietary driver or not installed.

Run a terminal and type** jockey-gtk**

If there are any sis related drivers there and they are not activated you could activate them and see if that helps.

Another thing you could try is to run** update manager **and see if there are any updates that might fix the problem you are having.

[IMG]http://ubuntuforums.org/images/misc/progress.gif[/IMG]

I did the ```
Jockey-gtk
```thing and I got this:
```
Traceback (most recent call last):
  File "/usr/bin/jockey-gtk", line 417, in <module>
    sys.exit(u.run())
  File "/usr/lib/python2.6/dist-packages/jockey/ui.py", line 427, in run
    self.ui_show_main()
  File "/usr/bin/jockey-gtk", line 101, in ui_show_main
    self.update_tree_model()
  File "/usr/bin/jockey-gtk", line 277, in update_tree_model
    for h_id in self.get_displayed_handlers():
  File "/usr/lib/python2.6/dist-packages/jockey/ui.py", line 771, in get_displayed_handlers
    return self.backend().available(self.argv_options.mode)
  File "/usr/lib/python2.6/dist-packages/jockey/ui.py", line 110, in backend
    self._check_repositories()
  File "/usr/lib/python2.6/dist-packages/jockey/ui.py", line 794, in _check_repositories
    if self._dbus_iface.has_repositories():
  File "/usr/lib/pymodules/python2.6/dbus/proxies.py", line 68, in __call__
    return self._proxy_method(*args, **keywords)
  File "/usr/lib/pymodules/python2.6/dbus/proxies.py", line 140, in __call__
    **keywords)
  File "/usr/lib/pymodules/python2.6/dbus/connection.py", line 620, in call_blocking
    message, timeout)
dbus.exceptions.DBusException: org.freedesktop.DBus.Error.NoReply: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.

```

---

### Post by shaun_54au2 on 2010-04-01
try going to system>administration>hardware drivers

see if there is anything sis in there
should look like this:

[IMG]http://blog.garethj.com/wp-content/uploads/2009/10/Hardware-Drivers.png[/IMG]

---

### Post by TheNerdAL on 2010-04-01
> **shaun_54au2 said:**
> try going to system>administration>hardware drivers

see if there is anything sis in there
should look like this:

[IMG]http://blog.garethj.com/wp-content/uploads/2009/10/Hardware-Drivers.png[/IMG]

No proprietary drivers.

---

### Post by Sef on 2010-04-01
Moved to Lucid.

---

### Post by shaun_54au2 on 2010-04-01
ok so you are using the linux default driver.

---

### Post by TheNerdAL on 2010-04-01
> **Sef said:**
> Moved to Lucid.

I am using Lucid but this happened to me before Lucid.

---

### Post by TheNerdAL on 2010-04-01
> **shaun_54au2 said:**
> ok so you are using the linux default driver.

Okay, now what?

---

### Post by shaun_54au2 on 2010-04-01
> **Sef said:**
> Moved to Lucid.


The same thing happened to him in ubuntu 10.04 _***BETA***_

---

### Post by shaun_54au2 on 2010-04-01
One thing you could tweak with is changing to a lower resolution just to see if the problem goes away.  If it does its definitely got to do graphics capabilities. ie the lower the resolution the better the frame rate.

---

### Post by NightwishFan on 2010-04-01
This link may have some information:
[http://www.winischhofer.eu/linuxsispart3.shtml#faq](http://www.winischhofer.eu/linuxsispart3.shtml#faq)

If you do not find a way to fix it, report a bug using this command. You will need a launchpad account.
```
ubuntu-bug xserver-xorg-video-sis
```

---

### Post by TheNerdAL on 2010-04-01
> **shaun_54au2 said:**
> One thing you could tweak with is changing to a lower resolution just to see if the problem goes away.  If it does its definitely got to do graphics capabilities. ie the lower the resolution the better the frame rate.

If I do change resolutions, the screen isn't as sharp as my current resolution which is 1440x900.

---

### Post by TheNerdAL on 2010-04-01
> **NightwishFan said:**
> This link may have some information:
[http://www.winischhofer.eu/linuxsispart3.shtml#faq](http://www.winischhofer.eu/linuxsispart3.shtml#faq)

If you do not find a way to fix it, report a bug using this command. You will need a launchpad account.
```
ubuntu-bug xserver-xorg-video-sis
```

Reporting isn't an option right now because I am having a problem with the reporting program due to Lucid being Beta.

---

### Post by shaun_54au2 on 2010-04-01
My best answer is that your sis onboard graphics is having a hard time displaying your windows at your current resolution.  A dedicated graphics card would probably fix the problem.

---

### Post by NightwishFan on 2010-04-01
This link says that some chipsets have issues and that the drivers may be fine. [http://www.winischhofer.eu/linuxsispart1.shtml#13](http://www.winischhofer.eu/linuxsispart1.shtml#13)

Was there ever a distro that it worked on, without these issues?

---

### Post by TheNerdAL on 2010-04-01
> **shaun_54au2 said:**
> My best answer is that your sis onboard graphics is having a hard time displaying your windows at your current resolution.  A dedicated graphics card would probably fix the problem.

Okay thanks, but is there a way to make the resolution(when I lower it) more sharper?

---

### Post by TheNerdAL on 2010-04-01
> **NightwishFan said:**
> This link says that some chipsets have issues and that the drivers may be fine. [http://www.winischhofer.eu/linuxsispart1.shtml#13](http://www.winischhofer.eu/linuxsispart1.shtml#13)

Was there ever a distro that it worked on, without these issues?

Umm, nope. Only Windows XP. But i think it worked on Ubuntu 9.04.

---

### Post by shaun_54au2 on 2010-04-01
> **NightwishFan said:**
> This link says that some chipsets have issues and that the drivers may be fine. [http://www.winischhofer.eu/linuxsispart1.shtml#13](http://www.winischhofer.eu/linuxsispart1.shtml#13)

Was there ever a distro that it worked on, without these issues?

 " You may likewise disable the shared memory in the BIOS.

 My advice: **Don't buy a machine with a SiS760 unless this machine has dedicated local video memory.** And please don't complain about "driver bugs" if you see "flashing lines" on the screen; these are the typical effects of a bandwidth problem and unavoidable - even the Windows driver can't do better. In such cases, reduce the resolution and/or refresh rate and/or color depth, or use one output (CRT1 or CRT2) only. Sorry, can't help it. **There is no driver bug involved.**
  For poor Averatec 6240 users: My drivers at least *allow* 1280x800 on the LCD if the external monitor is enabled... the Windows driver kicks you back to 1024x768 in such a case."


from the link you gave: [http://www.winischhofer.eu/linuxsispart1.shtml#13](http://www.winischhofer.eu/linuxsispart1.shtml#13)

---

### Post by NightwishFan on 2010-04-01
> **TheNerdAL said:**
> Okay thanks, but is there a way to make the resolution(when I lower it) more sharper?

If this worked before or on another Linux, file a bug when you can.

As for the resolution I think you can make it sharp by tweaking xorg, but do not ask me how to do that, xorg hates me. :D

---

### Post by TheNerdAL on 2010-04-01
> **NightwishFan said:**
> If this worked before or on another Linux, file a bug when you can.

As for the resolution I think you can make it sharp by tweaking xorg, but do not ask me how to do that, xorg hates me. :D

Okay, thanks! :D Now to work on my other forum about the bug in Update Manager.

---

