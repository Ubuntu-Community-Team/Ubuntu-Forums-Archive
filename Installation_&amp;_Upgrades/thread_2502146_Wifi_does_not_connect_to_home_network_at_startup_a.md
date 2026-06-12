---
title: "Wifi does not connect to home network at startup after upgrade to 24.04"
date: 2024-11-03
forum: Installation &amp; Upgrades
---

### Post by gja on 2024-11-03
After upgrading to 24.04 the Wifi on my laptop would not connect to my default home network after starting up.

Fix was found here:
[https://www.linux.org/threads/problem-with-wifi-failing-to-reconnect-automatically-in-xubuntu-ubuntu-24-04-solved.49961/]("https://www.linux.org/threads/problem-with-wifi-failing-to-reconnect-automatically-in-xubuntu-ubuntu-24-04-solved.49961/")

In NetworkManager.conf the setting "managed" needs to be set to true.
After that networkmanager needs to be restarted.

>>
Issue not solved.
When laptop is powered off for a long time, at power-up the default wifi network is not immediately found.
On warm reboot however, default network does seem to be found.

---

### Post by grahammechanical on 2024-11-03
This may or may not have something to do with it. Recently, Ubuntu has been using something called Netplan.

[https://netplan.io/](https://netplan.io/)

There should be a yaml file in /etc/netplan the has NetworkManager as the renderer.

Regards

---

### Post by gja on 2024-11-03
Thanks for your quick reply.
Interesting, never heard of netplan.

I just did a cold boot and now my default network did connect immediately.
Will check again on next cold boot.

---

