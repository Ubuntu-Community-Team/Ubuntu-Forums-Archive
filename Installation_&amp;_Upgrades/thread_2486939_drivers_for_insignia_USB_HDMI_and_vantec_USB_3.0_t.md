---
title: "drivers for insignia USB HDMI and vantec USB 3.0 to HDMI Display adapter"
date: 2023-05-17
forum: Installation &amp; Upgrades
---

### Post by ackahpaul on 2023-05-17
Good morning all,

Please I am  need to Ubuntu and I  switching from Windows, please where will I get drivers for insignia USB 3.0 to HDMI Display adapter as well as Vantec USB 3.0 to HDMI Display adapter.

Thanks

---

### Post by ActionParsnip on 2023-05-17
If you run:
```

sudo lshw -C display; lsb_release -a; uname -a; lsusb

```
What is the full output please?

---

### Post by MAFoElffen on 2023-05-18
InsigniaProduct.com says for that adapter (their own):
> 
Product Features.  USB 3.0 to HDMI: Mirror or extend your computer's display by connecting  from your computer's USB-A port to HDMI-enabled monitor, TV or  Projector. For Windows: Works with windows 10 or 11, but **can't support the Mac OS, Chrome OS, Android OS, Linux OS**, Game OS.
Vantec does not say that it will work with Linux, but... It it is made for Vantec by DisplayLink, and DisplayLink does say their devices work for Ubuntu... and they have a support page if there are problems.

RE: [https://support.displaylink.com/knowledgebase/articles/683672-my-displaylink-device-does-not-work-on-ubuntu](https://support.displaylink.com/knowledgebase/articles/683672-my-displaylink-device-does-not-work-on-ubuntu)

---

