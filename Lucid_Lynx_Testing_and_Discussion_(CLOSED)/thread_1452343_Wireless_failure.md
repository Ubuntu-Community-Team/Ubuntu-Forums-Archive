---
title: "Wireless failure"
date: 2010-04-11
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by lduperval on 2010-04-11
Hi,

I installed beta 2 on an old Toshiba laptop, which uses a DLink WNA-2330 card to connect to a D-Link router.

I have at least two problems:

1) Th nm-applet never displays anything. It is running but it doesn't show up in the notification area so I can't use it

2) When I configure a new wireless network, it I try to make it available to all, the information does not get saved (i.e. the new connection does not appear in the wireless link)

Any idea what is happening and how to correct it?

L

P.S. Wired networking seems to work fine.

---

### Post by gordintoronto on 2010-04-11
According to this page:
[https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsDlink#PCI](https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsDlink#PCI)

your wireless adapter works "out of the box."

You should see an icon for network manager, near the volume control on the top-right of your screen. Right-click on it, select "edit connections," select the wireless tab and "add." Enter your SSID, encryption type and passphrase, and you should connect.

Also, when you use a beta, you should expect it to break.

---

### Post by lduperval on 2010-04-11
That's just it, I don't see the applet icon. When I start it from the command line (I had to because I needed to make sure it was running), I see a flicker in the panel, but the icon never shows up. The applet is running, though.

I'll have to log a bug, I guess.

L

---

### Post by ranch hand on 2010-04-11
You might try re installing the applet.  Might do the trick.

It might be good t ofile the bug first and then if re installation works add a comment to the bug.

That way all the info gathered and sent by apport will apply to the problem.

---

### Post by Ancanus on 2010-04-13
@lduperval: I have exactly the same issue as you. Different network card though.
When I right click on the place where the flicker occurs, I get the context menu for nm-applet.
So the nm-applet IS in the notification area, it's just not drawing the icon for some reason. I tried switching themes and it still doesn't work. >: (

Let me know when you file a bug report and I'll dive in as well.

@ranch hand: re-installation doesn't work. =/
[I]
EDIT:[/I]
Bug report /w workaround:
[https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/553115](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/553115)

---

