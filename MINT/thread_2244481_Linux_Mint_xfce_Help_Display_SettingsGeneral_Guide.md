---
title: "Linux Mint xfce Help: Display Settings/General Guide?"
date: 2014-09-16
forum: MINT
---

### Post by Henry_Flower on 2014-09-16
I just installed the xfce version of Linux Mint for the first time and things are very basic at the moment. The screen resolution is set to the default 800x600 on my 1080p monitor, there's a home icon and the taskbar is clipped on either side due to the resolution. I'm not sure how to change any resolution settings or any settings at all for that matter. I'm currently downloading the drivers for my graphics card - that may fix the resolution but aside from that, where should I look for a guide to my OS?

It should be noted that I don't have internet access at home where I'm installing everything. I need to go to a nearby coffee shop to download anything and transfer it to my desktop with a thumb drive.

---

### Post by T.J. on 2014-09-16
Resolution problems require some information about your video adapter.  Can you open a terminal, run the "lspci" command, and paste the results here please?

---

### Post by tgalati4 on 2014-09-17
Installing a linux operating system without a reliable internet connection (or decent coffee) is tiresome.  There was a time when linux came on 14 floppy disks, created by downloading on a 1200 baud modem.  Now, an internet connection is vital to get proprietary drivers and to search for solutions for a problem like this.

Look at /var/log/Xorg.0.log for clues as to why your video is not working.  Open a terminal:

```
more /var/log/Xorg.0.log
```

Fortunately viewing log files does not require a trip to the coffee shop.

---

### Post by Henry_Flower on 2014-09-17
Yeah, this is proving to be too much trouble. I'll just wait until I have internet access again. Thanks anyways.

---

### Post by QIII on 2014-09-17
Moved to Other Operating Systems And Projects.

We're happy to help you with Mint, but bear in mind that is a distinct distro in its own right.

In any case, when you get connected we'll still be here!

Cheers!

---

