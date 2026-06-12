---
title: "Severe performance regression after upgrading to Kubuntu 24.10"
date: 2024-10-22
forum: Installation &amp; Upgrades
---

### Post by talcid on 2024-10-22
Hey everybody,

after upgrading from Kubuntu 24.04 to 24.10 I'm seeing severe performance degradation when multitasking. My system seems to be swapping way more often than before. Even when just switching between the same Firefox window and another window, it is often taking up to ten seconds or more for the window to be responsive again. Almost every time the window is desaturated, which is new with wayland or KDE 6. Windows rarely got desaturated in 24.04 for me.

I'm one of those people who keeps a lot of browser tabs and windows open. I'm using Firefox and I usually have about 60 windows open. That was still managable under 24.04 with ZSWAP. With 24.10 it is bordering on unusable. I haven't increased the number of windows or tabs after upgrading to 24.10 significantly. The lagginess of 24.10 has been apparent from the first boot.

Also, the mouse cursor now lags very often. When I hover over the Firefox icon in the taskbar and the window preview pops up, the system immediately starts swapping + compressing/decompressing as is apparant by the system monitor. The same thing happens when I click on the firefox icon and I get an overview of all the opened firefox windows. For some reason the system then also starts to swap and work like crazy. 

It always feels like the system is running circles around itself. Memory pages that have just been used don't seem to stay in memory. I've used vm.swappiness = 60 per default with 24.04. In 24.10 I've decreased it to 10 but this didn't help.

As you can see in the graphs from munin, something happened with memory consumtion and swapping after upgrading to 24.10. 

What is causing 24.10 to act so differently? Is it a bug, should I report it? If yes, where? In Launchpad or in the KDE bugtracker?

System:
Intel Core i5-4670
16 GB RAM
500 GB Samsung EVO SSD

Images: 

[IMG]https://i.imgur.com/veazCiD.png[/IMG]

[IMG]https://i.imgur.com/UzKmy1h.png[/IMG]
[COLOR=unset][/COLOR][COLOR=unset][/COLOR][IMG]https://imgur.com/veazCiD[/IMG]

---

