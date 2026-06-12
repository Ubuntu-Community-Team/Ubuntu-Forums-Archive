---
title: "Disable all updates"
date: 2018-11-23
forum: Installation &amp; Upgrades
---

### Post by msanders70 on 2018-11-23
Hi!

We run Ubuntu on an embedded touch device. The device is connected to a server system using an EDGE GSM modem. I have to stop all update activities inside the Ubuntu OS. I've already tried all hints I got:

- sudo apt-get purge unattended-upgrades
- sudo apt-get purge update-manager
- Modifying /etc/apt/apt.conf.d/10periodic

But the Ubuntu login message still shows me an increasing number of updates:

144 packages can be updated.
100 updates are security updates.

So, the Ubuntu OS is still looking for updates and offers the new packages to me.

How can I stop this?

Thanks!
Michael

---

### Post by hartman8227 on 2018-11-25
This is the first thing I found for the MOTD message.
[https://www.howtogeek.com/104708/how-to-customize-ubuntus-message-of-the-day/](https://www.howtogeek.com/104708/how-to-customize-ubuntus-message-of-the-day/)

And this is what I found on the update systems:
[https://wiki.ubuntu.com/SoftwareUpdates](https://wiki.ubuntu.com/SoftwareUpdates)

From my digging around, what it looks like is what your seeing is from the update notifier part of the upgrade system.

If you delete all of these systems it shouldn't look for updates or try to install them, I think.
> [https://wiki.ubuntu.com/SoftwareUpdates](https://wiki.ubuntu.com/SoftwareUpdates)
**Packages involved:**update-manager[COLOR=#333333][FONT=&amp] ([/FONT][/COLOR][code]("https://code.launchpad.net/update-manager")[COLOR=#333333][FONT=&amp], [/FONT][/COLOR][bug reports]("https://bugs.launchpad.net/ubuntu/+source/update-manager")[COLOR=#333333][FONT=&amp]), [/FONT][/COLOR]software-properties[COLOR=#333333][FONT=&amp] ([/FONT][/COLOR][code]("https://code.launchpad.net/software-properties")[COLOR=#333333][FONT=&amp], [/FONT][/COLOR][bug reports]("https://bugs.launchpad.net/ubuntu/+source/software-properties")[COLOR=#333333][FONT=&amp]), [/FONT][/COLOR]update-notifier[COLOR=#333333][FONT=&amp] ([/FONT][/COLOR][code]("https://code.launchpad.net/update-notifier")[COLOR=#333333][FONT=&amp], [/FONT][/COLOR][bug reports]("https://bugs.launchpad.net/ubuntu/+source/update-notifier")[COLOR=#333333][FONT=&amp]), [/FONT][/COLOR]ubuntu-release-upgrader[COLOR=#333333][FONT=&amp] ([/FONT][/COLOR][code]("https://code.launchpad.net/ubuntu-release-upgrader")[COLOR=#333333][FONT=&amp], [/FONT][/COLOR][bug reports]("https://bugs.launchpad.net/ubuntu/+source/ubuntu-release-upgrader")[COLOR=#333333][FONT=&amp])[/FONT][/COLOR]

Although if I may play Devil's Advocate, are you sure you want to stop all updates? If the system hasn't been updated it can and will open up large security vulnerabilities, especially if it is connected to any sort of a network. There was recently a few that affected the ssh system: [https://www.cvedetails.com/vulnerability-list/vendor_id-120/SSH.html](https://www.cvedetails.com/vulnerability-list/vendor_id-120/SSH.html)

---

### Post by msanders70 on 2018-11-26
Thanks a lot for your reply!

But I don't want to get rid of the motd, but of searching for updates. I already was aware of the 2nd link, but to be honest I didn't read the whole (very long and detailed) article. May be there's a hint inside.

And yes I'm sure to deactivate all updates. The device is attached via EDGE modem to a VPN. As EDGE has very poor data rates and the VPN is secure, this should be the way to go.

---

