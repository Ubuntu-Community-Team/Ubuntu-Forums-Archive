---
title: "Install Hoary without booting the CD?"
date: 2006-12-22
forum: Installation &amp; Upgrades
---

### Post by ScotBoy on 2006-12-22
Hello,

Hopefully and easy answer to this. I have an official CD with a Hoary distro. I want to put this on a laptop which has no CD drive. I have an XP desktop on a wireless network which has a router providing DHCP. However, due to crap XP networking I cannot bridge my wired network adaptor in the desktop to the wireless network. Therefore I don't have DHCP on the wired lan. I am trying to resolve this fault but not getting anywhere.

I don't have tftp or bootp on the xp machine, so I can't boot from the network on the laptop. I think that setting this up would prove timeconsuming and may not be successful.

Can I boot the laptop using a linux floppy and map the CD drive on the XP machine via my lan (I have achieved this using a DOS boot disk with lan support)? if so, can I then initiate the install using this CD share without having to boot?

---

### Post by Sef on 2006-12-22
Check out the [Netboot]("https://help.ubuntu.com/community/Installation/Netboot?highlight=%28install%29") page, if you have a way to access the net.

> due to crap XP networking I cannot bridge my wired network adaptor in the desktop to the wireless network.

Home edition has the networking stripped out of it.

---

