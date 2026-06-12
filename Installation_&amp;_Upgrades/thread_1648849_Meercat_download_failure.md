---
title: "Meercat download failure"
date: 2010-12-19
forum: Installation &amp; Upgrades
---

### Post by lupo1939 on 2010-12-19
Running 10.04 tried to upgrade to 10.10. Download ran for 6.5 hours then produced a failure message.  Download speed varied all over the place from 30 kbps to 170 kbps but usually well below 100.  Speedtest shows about 100 kbps in and out.

Is there a way to drop back to 10.04 ad run the 10.10 download from scratch?  Attempts to run the download now produce index error messages.

What should I use as a source location?

---

### Post by sikander3786 on 2010-12-19
No way to drop back to Ubuntu Lucid if the packages were upgraded. Even if some of them failed to...

Do you mean the upgrade was not successful? If so, are you able to boot Ubuntu now? Can you see the desktop?

Regarding the speed of downloads, you can go to Software Center > Edit > Software Sources > Change Server > Choose Best Server.

If you can see the desktop, we would want to see the output of these commands from Applications > Accessories > Terminal.

```
sudo apt-get update && sudo apt-get upgrade
```

```
sudo apt-get dist-upgrade
```

While posting, click the # icon in post menu and paste your text in between the generated code tags.

---

### Post by lupo1939 on 2010-12-19
Thanks for the advice.  The upgrade process seems to have gotten constipated toward the end of the download phase.  Machine still works.

---

### Post by sikander3786 on 2010-12-19
Did you reboot after that failed? Or the process is still running? Did you try the commands mentioned above?

If you didn't reboot after the process failure, DON'T shutdown or reboot your machine until you are sure that all upgrades have been applied successfully.

---

