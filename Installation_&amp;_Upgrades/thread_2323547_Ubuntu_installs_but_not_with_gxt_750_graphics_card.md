---
title: "Ubuntu installs but not with gxt 750 graphics card"
date: 2016-05-06
forum: Installation &amp; Upgrades
---

### Post by chris-burmajster on 2016-05-06
Hello,

I've got a problem. I installed a clean 16.04 but it didn't work with my MSI GTX 750 graphics card. I returned the card to Chillblast for checking and it was returned OK. I can use the computer with 16.04 if I remove the card and use the integrated graphics, but this limits me to 1920 x 1080. The monitor has 2560 x 1440. If I replace the card then all that happens is that it lights up the monitor, but doesn't display anything. If I remove it, then it works with 1920 x 1080 (which is the display of the internal graphics card). I tried installing Nvidia drivers via a PPA and got it working, but it was 800 x 600 and 1920 x 1080 the second time. The third time it was back to the "lights up the monitor but doesn't display anything". 

Can anybody please help?

Chris Burmajster

---

### Post by grahammechanical on 2016-05-06
My digital TV that I am using as a monitor can do 8192 x 8192 but the optimum setting according to the manufacturer is 1920 x 1080. And that is the default setting Ubuntu runs my monitor at. And this is because every time Linux loads it accesses the Extended Display Identification Data (EDID) integrated circuit chip in the monitor to get the optimum setting.

What results do you get if you use the Nvidia driver offered in Additional Drivers? This command will list the proprietary video drivers available in 16.04 for your video card. Compare those drivers with what the Nvidia drivers web site recommends for that card.

```
ubuntu-drivers list
```

Regards.

---

### Post by chris-burmajster on 2016-05-06
Intel-microcode. That's what I get.

---

### Post by chris-burmajster on 2016-05-08
I've solved it. I used an HDMI cable to connect the monitor to the computer, in addition to the DVI cable. Graphics card not needed.

---

