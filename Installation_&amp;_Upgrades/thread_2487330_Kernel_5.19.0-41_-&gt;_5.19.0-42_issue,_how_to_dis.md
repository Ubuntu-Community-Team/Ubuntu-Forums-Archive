---
title: "Kernel 5.19.0-41 -&gt; 5.19.0-42 issue, how to disable point release updates?"
date: 2023-05-30
forum: Installation &amp; Upgrades
---

### Post by piper984 on 2023-05-30
I have 3 Ubuntu 22.04 based systems that use a specific hardware PCIe card.  I had an issue over the weekend where these systems updated from kernel 5.19.0-41 to 5.19.0-42, and in doing so the drivers for the specific PCIe hardware (Blackmagic DeckLink Quad SDI card) stopped working.  Fortunately I was able to figure out and isolate the issue after a few hours, and as a temporary fix I was able to reboot the machines, enter grub, and select the 5.19.0-41 release to get the system back up and running.

I have some questions that hopefully someone can help me with.

Question 1: What is the best method to make the 5.19.0-41 the default kernel when the systems are cold booted?

Question 2: What is the best method to freeze the system with the 5.19.0-41 kernel and not allow any kernel updates?

Question 3: Is there some auto update agent running by default with Ubuntu 22.04?  We assumed that an operator must have accidentally agreed to an GUI prompt to update the system, but since we've seen 3 system do this, we now believe that some other process updated the kernel.

Thank you for the help here!

---

### Post by MAFoElffen on 2023-05-31
This is how I urned off automatic updates for Ubuntu Server. Understand that I do updates, but want to be there and have control over what is updated, and when... Here is the file to make the changes to:
```

sudo nano /etc/apt/apt.conf.d/20auto-upgrades

```
To disable automatic updates completely, make sure all these option directives are set to &#8220;0&#8221;. When done, save your changes and exit the file.
```

APT::Periodic::Update-Package-Lists "0";
APT::Periodic::Download-Upgradeable-Packages "0";
APT::Periodic::AutocleanInterval "0";
APT::Periodic::Unattended-Upgrade "0";

```
The defaults for those are "1", if you ver want to reset those back to the defualts...

That is how to do that with everything in place. You can also do that by completely uninstalling unattended-updates, and I have those instructions in my notes, but that is like hitting something with a 4x4. If you did that, then you also need to disable the apt-daily-upgrade.timer & the apt-daily.timer, and mask SystemD services apt-daily-upgrade.service & apt-daily.service.

What I usually do if I have a problem for a server with a kernel version, then I unistall that version and 'pin' the last kernel that worked okay... For example for something like yours
```

sudo apt remove --purge linux-5.19.0-42-generic linux-headers-5.19.0-42-generic linux-modules-5.19.0-42 linux-modules-extra-5.19.0-42-generic
sudo apt-mark hold linux-5.19.0-41-generic linux-headers-5.19.0-41-generic linux-modules-5.19.0-41 linux-modules-extra-5.19.0-41-generic

```
The do
```

sudo update-grub

```
To generate a good version of the Grub Menu, for it to boot that kernel by default...

But remember that I said that I 'only' feel that something like this is a temporary solution. I feel the long term solution is reporting it both to Launchpad, so that they can report upstream that there "is" a problem that needs to be resolved, AND reported to the device Vendor, to let them know there is a problem. Why both, because I need security and kernel updates. I don't want to be dead-ended. I want things to be resolved by the next update (or sooner.) New Kernels and Security updates are a reality. Sometimes I can get a fix by downloading a proposed patch, before there is an update.

---

### Post by piper984 on 2023-05-31
Thank for you the information.  This is very helpful.  As an additional learning I've made, it's possible to disable the auto apt updating service via:

sudo systemctl disable apt-daily.timer
sudo systemctl disable apt-daily-upgrade.timer

But modifying entries from xxauto-upgrades.conf seems to be the best move.

Thank you!

---

### Post by MAFoElffen on 2023-05-31
Just for your notes... Remember what I said, If you went that route:
> **MAFoElffen said:**
> You can also do that by completely uninstalling unattended-updates, and I have those instructions in my notes, but that is like hitting something with a 4x4. If you did that, then you also need to disable the apt-daily-upgrade.timer & the apt-daily.timer, [COLOR=#ff0000]and mask SystemD services apt-daily-upgrade.service & apt-daily.service[/COLOR].

If you disable apt-daily-upgrade.timer & the apt-daily.timer...
> **piper984 said:**
> Thank for you the information. This is very helpful. As an additional learning I've made, it's possible to disable the auto apt updating service via:
```

sudo systemctl disable apt-daily.timer
sudo systemctl disable apt-daily-upgrade.timer

```

Then also do this to complete what I said...
```

sudo systemctl mask apt-daily-upgrade.service
sudo systemctl mask apt-daily.service

```
Otherwise those two services will cause errors.

---

