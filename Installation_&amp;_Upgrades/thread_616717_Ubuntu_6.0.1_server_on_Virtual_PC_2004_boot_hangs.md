---
title: "Ubuntu 6.0.1 server on Virtual PC 2004 boot hangs"
date: 2007-11-18
forum: Installation &amp; Upgrades
---

### Post by jlynker on 2007-11-18
Is there an online boot troubleshooting guide somewhere?

I'm trying to install 6.06.1 under Virtual PC 2004 SP1 on a fujitsu notebook (with VPC notebook upgrades applied) and after what appears to be a successful install, boot hangs at 'uncompressing...ok booting...'

I've read scores of blogs, tried all the VGA settings and also these options:  acpi=ht noapic nolapic
I"ve tried redirecting the netconsole; I think it might be booting, but outputing to the wrong tty..?

I can boot via CD into repair a broken install and get a prompt, but many of the directories are empty. For instance, /boot is empty, yet, there's a grub - which makes me think the rescue is mounting someting different than the normal boot.

I'm new to ubuntu, my desktop system works great! :) but I want to take a system on the road and can't dual boot this notebook.

Any suggestions much appreciated.

---

### Post by jlynker on 2007-11-26
These instructions:

[http://ubuntuforums.org/showpost.php?p=1170190&postcount=17](http://ubuntuforums.org/showpost.php?p=1170190&postcount=17)

fixed it on my notebook via non-VM (Virtual PC) install. It's likely the same fix for my VMs.

---

