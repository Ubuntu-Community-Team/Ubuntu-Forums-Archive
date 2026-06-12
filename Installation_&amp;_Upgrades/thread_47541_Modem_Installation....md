---
title: "Modem Installation?..."
date: 2005-07-09
forum: Installation &amp; Upgrades
---

### Post by Downtown on 2005-07-09
I'm fairly new to Linux, and completely new to Ubuntu (I just got my CDs in the mail today).  I can't configure my Actiontec GT701-WG DSL modem to work properly.  When I was using Slackware before, it'd run fine, but now it doesn't on Ubuntu.  All the lights on the modem turn on, except the "Internet" one.  I can type my IP address into Firefox and access my modem.  I can only access Actiontec's website, but no other ones.  Is there somthing in particular that I need to do to get it running right?  If you need more info to help, let me know.  I really don't want this to keep me from enjoying Ubuntu, because it seems like a really great distro.

---

### Post by mingus on 2005-07-09
[QUOTE=Downtown]All the lights on the modem turn on, except the "Internet" one.  I can type my IP address into Firefox and access my modem.  I can only access Actiontec's website, but no other ones.[/QUOTE]

A bit of clarification . . . the IP address you are typing in Firefox; that is the modem's IP, not your computer's, right?  And you are sure you are accessing the Actiontec website, not just the modem device interface?

Try entering this in Firefox:  216.109.118.66

Then get in a terminal and do both of these:
$ping -c 4 216.109.118.66
$ping -c 4 [www.yahoo.com](www.yahoo.com)

If you got Yahoo in Firefox, go to System/Administration/Networking and add your ISP's DNS servers (you should find these via your modem interface).

If you got a reply to your ping to [www.yahoo.com](www.yahoo.com) but did not see Yahoo in your Firefox test, the problem is probably with the Firefox configuration.

If you got a timeout or no host found when you pinged the yahoo 216... address, then the problem is probably with your network adapter configuration or dsl setup.

---

### Post by Downtown on 2005-07-10
> **mingus]A bit of clarification . . . the IP address you are typing in Firefox said:**
> www.yahoo.com[/url]

If you got Yahoo in Firefox, go to System/Administration/Networking and add your ISP's DNS servers (you should find these via your modem interface).

If you got a reply to your ping to [www.yahoo.com](www.yahoo.com) but did not see Yahoo in your Firefox test, the problem is probably with the Firefox configuration.

If you got a timeout or no host found when you pinged the yahoo 216... address, then the problem is probably with your network adapter configuration or dsl setup.
 Thx for the help.  I had to try this a few times, but it works now.

---

### Post by mingus on 2005-07-11
Great!  Was the fix setting up your DNS servers in Ubuntu networking?

---

