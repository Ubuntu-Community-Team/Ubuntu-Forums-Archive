---
title: "Cannot Get Passed Splash Screen"
date: 2010-05-28
forum: Installation &amp; Upgrades
---

### Post by GardenPlantCulture on 2010-05-28
I have been trying to install ubuntu for a few days. After I select install on the first screen using live it will switch over to the UBUNTU splash screen. I can hear the CD drive and that hard drive working for about 45 seconds to a minute then nothing. It will just sit there on the splash screen for as long as I let it. By let it i mean hours. I and installing it on a Toshiba laptop with 1.6 ghz centrino processor, 160 gb hard drive, and 2.5 gigs of ram. Please Help... Thank You...

---

### Post by darkod on 2010-05-29
Have you tried using the Try Ubuntu option first to load it in live mode and see if it works fine?

Sounds like hardware incompatibility, video driver or something.

---

### Post by kansasnoob on 2010-05-29
If you can run any Ubuntu Live CD on that machine it might help to see the output of:

```
lspci | grep VGA
```

That will show specific graphics card info.

---

### Post by GardenPlantCulture on 2010-05-29
I have tried both ways. I have tried using different f6 options. If I load without splash screen I get to line "(65.993025) (<c01033ec>) syscall_call+0x7/0xb" I hope that helps somehow. I just really really want to get away from Windows without buying a Mac. Thank You in advanced for any help received.

---

### Post by GardenPlantCulture on 2010-05-29
How do I go about doing that. I use to have a decent knowledge of computer before I became a Landscaper. I follow directions perfectly. Thank You For the Help.

---

### Post by darkod on 2010-05-29
Unfortunately, if you can't make it load in live mode, there is not much you can try.

Another option would be to use the Alternate Install CD (image). It still installs the same desktop system but it has text installer, not GUI.

But even if it installs OK, what ever is bothering it right now might make it not boot the first time in normal mode. Maybe you will need to use recovery mode (command prompt) to make it work.

Another option is just trying whether 9.10 or even 8.04 LTS will boot in live mode successfully.

---

### Post by GardenPlantCulture on 2010-05-29
Is there a link where I can get one of those versions that you mentioned?

---

### Post by darkod on 2010-05-29
When you click on the release name at the top, it will open the page for that release.
[http://releases.ubuntu.com/](http://releases.ubuntu.com/)

The image files are at bottom. The standard live cd has the word -desktop- in the fiename, the alternate image has -alternate-. And also the images exist in both 32bit and 64bit version. Just select the one you need.

---

