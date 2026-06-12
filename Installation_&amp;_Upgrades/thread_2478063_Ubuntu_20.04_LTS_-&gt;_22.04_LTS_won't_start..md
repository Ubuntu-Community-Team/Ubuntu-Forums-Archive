---
title: "Ubuntu 20.04 LTS -&gt; 22.04 LTS won't start."
date: 2022-08-15
forum: Installation &amp; Upgrades
---

### Post by John Nagle on 2022-08-15
I have a running 20.04 LTS desktop system. No dual boot or VM; pure Ubuntu. I got the notice that an upgrade was available. So I did the regular update with Software and Updates, to bring the system up to date before the upgrade. Rebooted. Now I'm in a clean state, ready to upgrade.

So, I click on **Software and Updates**, and get

[IMG]https://i.ibb.co/nCgdq8t/ubuntuupgradefail01.png[/IMG]


So, we're good to go, and I click "Upgrade..."

The dialog box disappears. But nothing happens. After waiting a while, I check System Monitor. No network traffic. No compute. No disk I/O light. 

I checked the dpkg log, and there are no new entries.

Puzzled.

---

### Post by John Nagle on 2022-08-15
In syslog, I see

Aug 15 14:25:20 Nagle-LTS update-manager.desktop[7943]: Checking for a new Ubuntu release
Aug 15 14:25:20 Nagle-LTS update-manager.desktop[7943]: Please install all available updates for your release before upgrading.

So the GUI says "up to date", while syslog disagrees.

---

### Post by nibal on 2022-08-15
Hi,

The GUI doesn't say that. An upgrade was available, according to your configuration, and you installed it.
You should also try:
sudo apt update
sudo apt full-upgrade

HTH
Nikos

---

