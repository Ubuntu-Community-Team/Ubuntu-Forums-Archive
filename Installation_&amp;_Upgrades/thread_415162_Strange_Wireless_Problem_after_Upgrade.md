---
title: "Strange Wireless Problem after Upgrade"
date: 2007-04-20
forum: Installation &amp; Upgrades
---

### Post by DRHamp on 2007-04-20
I upgraded yesterday from 6.10 to 7.04.  I used the recommended method -- Update Manager.

It took awhile, but all appeared to be fine.  After the upgrade was complete and the laptop rebooted - everything appeared to work fine.  Both the wired ethernet connection and the wireless connection worked as before, and as expected.

When I turned the machine on this morning, -- no wireless.  The wired ethernet connection is fine, just no wireless.  

This is a dual-boot machine and the wireless continues to work fine under XP.

Anyone have any thoughts?

---

### Post by elmerfud on 2007-04-20
I've got the same setup and the same problem.  I had to do a few ifup and ifdowns as well as a /etc/init.d/networking stop, starts and now it works.  There is a bug in there somewhere.

---

### Post by DRHamp on 2007-04-20
> **elmerfud said:**
> I've got the same setup and the same problem.  I had to do a few ifup and ifdowns as well as a /etc/init.d/networking stop, starts and now it works.  There is a bug in there somewhere.

Thanks - I'll give that a try

---

### Post by DRHamp on 2007-04-21
Ok, the wireless is now working ok --- but there is still a minor nusiance.

My machine is an HP Pavilion ZD7020.  There is a wireless on/off button/indicator on the laptop which allows you to enable and disable the internal wireless adapter.  It also serves as an indicator it that it lights up when you have a wireless connection.  With Edgy, this indicator would light when the connection was made.  Now, with Feisty -- the indicator doesn't light even though it has a good connection.

Also, at the top information bar(Ubuntu) there is a network icon which lights up when there is network activity -- This was a good indicator in Edgy, but doesn't show any activity in Feisty even though there is network activity happening.

There is a network indicator for eth0(the wired connection) and for eth1(the wireless connection)  The indicator for the wired connection shows activity when it's enabled -- the wireless indicator does not.

Like I said, I'm happy that both wireless and wired networking are working good -- the indicator issue is a relatively minor nusiance -- but it still bugs me -- I'd like to fix it ----------- anyone have any ideas?

Otherwise - the Edgy to Feisty upgrade was flawless and I'm very happy with it.

---

