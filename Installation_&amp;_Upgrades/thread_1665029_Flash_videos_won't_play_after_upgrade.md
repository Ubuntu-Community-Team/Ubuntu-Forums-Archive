---
title: "Flash videos won't play after upgrade"
date: 2011-01-11
forum: Installation &amp; Upgrades
---

### Post by beelissa on 2011-01-11
I upgraded to maverick over the weekend. Now videos won't play in my browser, like YouTube or on CBS.com or NBC.com, or embedded in Facebook (these are the ones I've tried so far).

I'm using Xfce 4.6.2 and Firefox 3.6.13. I uninstalled the Adobe Flash plugin and reinstalled it using the Ubuntu Software Center. That didn't help. I've restarted the computer also.

I'm not an absolute newbie, but I don't have a lot of experience with Linux yet.

If someone could give me an idea of how to fix this or diagnose what is wrong, I would appreciate it.

Thanks!

---

### Post by lovinglinux on 2011-01-12
Get [Flash-Aid]("https://addons.mozilla.org/en-US/firefox/addon/161939/") and run it. It will detect installed flash plugins, remove them and install the best option according to your system architecture and version. Additionally, it will apply some tweaks that should fix your problems. If you still get that issue after running Flash-Aid, then go to the extension Help tab, click the "Generate Report" button and send me the results so I can analyze your situation.

---

### Post by beelissa on 2011-01-12
I use both Firefox and Chromium and the problem seems to be happening with both browsers, not just Firefox.

---

### Post by lovinglinux on 2011-01-12
> **beelissa said:**
> I use both Firefox and Chromium and the problem seems to be happening with both browsers, not just Firefox.

The extension runs on Firefox, but the flash installed by it works for any browser. However, if you are running Chrome 32bit, then it has it's own plugin that can be turned off.

---

### Post by beelissa on 2011-01-12
Wow, thanks. This was easy to install and it seems to have fixed all my problems. Very helpful program!

---

### Post by lovinglinux on 2011-01-13
> **beelissa said:**
> Wow, thanks. This was easy to install and it seems to have fixed all my problems. Very helpful program!

You are welcome.

---

