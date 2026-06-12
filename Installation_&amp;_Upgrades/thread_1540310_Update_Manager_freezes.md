---
title: "Update Manager freezes"
date: 2010-07-27
forum: Installation &amp; Upgrades
---

### Post by _glook on 2010-07-27
Hey all,

I'm running 10.04 LTS, Lucid Lynx 64 bit. Kernel: 2.6.32-21-generic on an hp touchsmart tm2t.

The issue here is this: The update manager starts and has a list of updates. I click "Install Updates" and it asks for my password. I type it in and then a window with the title "Downloading Package Files" appears, but no content is displayed in the window. It hangs here indefinitely. When I go to restart or shut down, it tells me that the program "AT SPI Registry" is not responding.

The workaround I found was to simply do it from the command line ('sudo apt-get update; sudo apt-get upgrade') however there are still updates that show up in the Update Manager and it looks like some of the updates are to the kernel itself.

Anyone got any suggestions?

---

### Post by AshRice on 2010-07-27
If apt-get doesnt work, I'd try aptitude. It usually fixes the stuff that apt-get cant.

are you getting any issues with packages being held back in apt-get?

```
sudo aptitude update && sudo aptitude upgrade
```

---

### Post by _glook on 2010-07-28
Thanks, that seemed to work!

A slight bit of a pain having to do it from the terminal instead of the gui, but this is Linux after all. :p

---

