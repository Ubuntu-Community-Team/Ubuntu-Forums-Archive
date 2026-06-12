---
title: "Black terminal and black edges after 13.10 upgrade"
date: 2013-10-29
forum: Installation &amp; Upgrades
---

### Post by will547_us on 2013-10-29
Greetings,

I wanted to upgrade from Ubuntu 13.04 so I burned an iso. The upgrade failed with this message: 
*Can not run the upgrade This usually is caused by a system where /tmp is mounted noexec. Please remount without noexec and run the upgrade again.*

So I remounted: *remount /tmp without noexec ubuntu 13.04* and upgraded: *sudo do-release-upgrade*.

I have a System76 Sable-Complete and I installed the System76 driver:
[I]sudo apt-add-repository ppa:system76-dev/stable
sudo apt-get update
sudo apt-get install system76-driver
[/I]
I went to System Settings and clicked on System76 Driver and my machine locked up and I had to power off.
When I restarted some apps have black edges and my terminal opens with a black screen. I have to close these items from Dash.
I then did a search and read: [I][https://wiki.ubuntu.com/Mir/Installing](https://wiki.ubuntu.com/Mir/Installing) 

[/I]System Settings will no longer open so I am unable to check for listed PPA. I can use xterm, I have Unity, and Dash[I].
[/I]
When I:[I] ps aux | grep unity-system-compositor
[/I]I get:[I] grep: compositor: No such file or directory

[/I]When I: [I]grep -i xmir /var/log/Xorg.0.log
[/I]I get nothing.When I: [I]ls -l /var/log/lightdm/unity-system-compositor.log 
[/I]I get:* ls cannot access **/var/log/lightdm/unity-system-compositor.log *[I]No such file or directory

[/I]I tried restarting lightdm and had to retype this message.I don't know what else to do, suggestions please!

TIA, Will

---

