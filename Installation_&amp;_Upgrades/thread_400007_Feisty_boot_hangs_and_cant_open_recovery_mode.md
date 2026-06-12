---
title: "Feisty boot hangs and cant open recovery mode"
date: 2007-04-03
forum: Installation &amp; Upgrades
---

### Post by tmray on 2007-04-03
I'm dual booting vista and kubuntu. 
I just did a clean install of feisty 7.04, which I figured out I had do do from my Intel integrated graphics card instead of my nvidia GeForce fx 5200 card. It installed just fine.

I installed nvidia-glx from adept and then in the konsole entered "sudo nvidia-xconfig"

I rebooted to BIOS set it to use the PCI graphics card instead of the integrated one then rebooted to Kubuntu. 

as it loaded the blue loading bar at the bottom got about 1/4 far when it stalled. well this happened once before when I installed my nvidia card in kubuntu edgy and I had fixed it in recovery mode. 

So I rebooted in to recovery mode to blacklist the intel_agp from loading on boot but when I started the recovery mode boot it was loading as normal then a steady list of numbers and letters started scrolling down the screen and wouldn't stop. after about 5min I just turned off the computer and restarted.

I went back and I rebooted from the integrated card again and choose to load kubuntu from the list of OS's but couldn't open kubuntu but because I had installed the nvidia drivers already, the screen stayed black after it started. 

so I rebooted again and tried recovery mode from the integrated card which loaded but when I typed
"sudo kate /etc/hotplug/blacklist"
it said kate could not access the x-server.

any ideas?

Thanks

---

