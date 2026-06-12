---
title: "Upgrade 22.04 to 24.04-01 - New kernel failure"
date: 2024-09-01
forum: Installation &amp; Upgrades
---

### Post by Davey_Burgess on 2024-09-01
Post rejected twice, so boiling this down to bare essentials:
[LIST]
[*]I've been running 22.04 for a couple of years. 
[*]Upgraded last night to 24.04 (after backup!) 
[*]On reboot, system stopped after grub menu, 2nd monitor, keyboard and mouse all powered off. 
[*]Left all night in case it 'came back' - nothing. 
[*]Power cycled computer, tried twice more from default, still sits at the 'Dell' screen with the Ubuntu Unity logo 
[*]Rebooted again, selected advanced, and selected 5.15.0-119-generic instead of 6.8.0-41-generic and was able to boot from that. 
[*]Ubuntu still reports it is running 24.04 despite the older kernel. 
[/LIST]

Since then:
[LIST]
[*]Downloaded and ran 'boot repair' - pastebin is at [https://paste.ubuntu.com/p/ppVYCVXgJw](https://paste.ubuntu.com/p/ppVYCVXgJw) 
[*]Retried boot on the 6.8.0-41 and still get the same system stop. 
[/LIST]

Further testing:
[LIST]
[*]booted from USB with ubuntu-24.04.1-desktop-amd64.iso - exact same problem 
[*]booted from USB with ubuntu-22.04.4-desktop-amd64.iso - booted just fine 
[/LIST]

Any constructive suggestions would be appreciated!

---

