---
title: "How to reinstall the entire system using apt-get?"
date: 2010-05-19
forum: Installation &amp; Upgrades
---

### Post by Calmarius on 2010-05-19
I tried to upgrade my Ubuntu 9.10 to 10.04 but upgrade-manager failed to do that complaining about "broken held packages".
(It was the xorg-server which I upgraded from the xorg's ppa due to the issues with the Mono few months ago. )

So I tried do it manually by setting every karmic entries to lucid in the /etc/apt/sources.list

The I executed apt-get update and then apt-get dist-upgrade

It looked like it wound work but it didn't do what I expected... After reboot I got tons of error messages somehow I got the splash and it disappeared immediately and just a blank screen waits. After 4-5 reboot I'm able to get to the login screen somehow but my keyboard disabled.

So I effectively killed my system... In grub I can boot from the recovery kernel and can access the root prompt and it seems the network is ok.

I don't have any CD's at the moment to burn the ISO to. And my old Intrepid minimal install disc is lost...

In this situation is it possible to make apt to delete everything and download everything again from the net with the default settings?

---

