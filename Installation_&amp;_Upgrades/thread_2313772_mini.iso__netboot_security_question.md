---
title: "mini.iso / netboot security question"
date: 2016-02-15
forum: Installation &amp; Upgrades
---

### Post by jaarvidsen on 2016-02-15
ive been playing around with the mini.iso in vbox, ive got it up and running nicely exactly how i want with cinnamon-core being the main thing i installed, no unity in sight, and i think this will be how i install proper next time around. obviously this way you need to install most things manually.

so im unsure about things under the hood. is there anything in particular i need to install or configure to get the security at the same level as a full ubuntu install? i guess firewall(iptables) etc and anything else related to security is included in the mini.iso? or is there something i need to be aware of if im going this path instead of the regular ubuntu install?

thanks in advance

---

### Post by ian-weisser on 2016-02-15
You can live a long, fruitful life without trashing the enjoyments of others (like their preferred DE).

For the most part, you security process is the same.
Secure your SSH server to use keys only, if you install one.
Check for listening ports.
Check your logs. When possible, don't store your logs on the same system.
Check ps and top for unexpected processes.
Don't install software from the wild, dirty internet.
Uninstall software you don't trust or don't use.
Listen for unexpected network activity bursts.

You know, the usual.


Building from the mini.iso means you might accidentally autoremove your entire system. It's happened to a few over the years, so make sure you safeguard against that.

---

