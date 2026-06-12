---
title: "A bug so weird I have *no* idea how to report it (network/WiFi?)"
date: 2009-08-30
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Jim March on 2009-08-30
Gather round y'all and hear my tale of woe:

I'm helping a friend install a camera monitoring setup at their small biz.  They have a DSL connection via Qwest running through an Actiontech combination DSL modem/router/WiFi hotspot critter.

I brought my laptop down so I could, well, screw around during download/compile times and such stuff.  (When I'm not ready to strangle the sick SOB that invented Zoneminder.)

Lappy is running Karmic A4, WiFi chipset is the Atheros 5007 which has been solid as a rock in Karmic and prior.  Should be using the Ath5k drivers, right?  At my home 'net where I am now (Comcast cable going through an Apple router) everything has been fine, and other WiFi hotspots too.

Get to the Qwest DSL setup, everything is NOT fine.  On my lappy that is.  Internet is WAY slow, bogs to a crawl and then dies, and then weirdly enough starts mixing up URLs - go to "digg.com" and it pulls up a webforum I visit.

Whaa?

The WinXP box they own on hardwire has no such issues.  The Arch Linux camera monitoring station I'm building (also hardwired) is doing just fine.  Thinking Firefox 3.5 maybe lost it's mind, I fire up Chrome and Epiphany.  Both are slow, both are seeing the same scrambled URLs.  On a lark, I fire up VirtualBox and my Windows XP virtual machine right there on my lappy - and it's FINE - 100% normal, no scrambled URLs, speed is normal for that connection.  Even double-checked that at speedtest.net.

Mrf?  It's supposed to be Ubuntu feeding Virtualbox it's "NAT routed signal" (yeah, that's the settings, normal default Virtualbox stuff).  So if Ubuntu was hosed in terms of basic network functionality, the virtual machine should have been too.  Right?

Get back to my home net, everything is fine.

I'm going back there tomorrow.  ANY clue as to what I should check?

Note: the router is set up to serve DHCP to the first 52 addresses, static IPs start at .53 and go up (with the first three actually used).  So I'm thinking I ought to try a static IP.  Oh, and I did confirm it works fine under Ethernet, so this is somehow related to WiFi.

Maybe it's "bell book and candle" time, hold a sceance and pray to Charles Babbage or something?

---

### Post by knarf on 2009-08-30
Weird it is. Before you pull out the ouiji board to contact Babbage your might want to start a sniffer (wireshark comes to mind) to see what sort of traffic goes over the line/aether, look for weird ARP messages, change your hwaddr and check if it still happens?

---

### Post by hugmenot on 2009-08-30
What is the wireless access point at the business?
Look up the MAC address of the access point by using "iwconfig" then find out the manufacturer [using this website]("http://www.coffer.com/mac_find/"). Then proceed to Google to research this combination of station and access point.

That&#8217;s what I would do. My hunch is that DNS is somehow broken. You could try to override the DNS you get from DHCP.

---

### Post by martijntje on 2009-08-30
My gut is telling me it has something to do with ipv6. Try disabling that in about:config.

---

### Post by Jim March on 2009-09-01
Going to a static IP solved it.  Didn't try tweaks to IP6 yet, I will if I have time.

---

