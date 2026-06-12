---
title: "Wireless inability to connect after 10.15 upgrade"
date: 2008-10-17
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by montini on 2008-10-17
After I made the 2008.10.15 intrepid beta upgrade, I am unable to connect my wireless router (Linksys WRT54GL + tomato firmware).

10.15 at the evening I made the upgrade, wireless dissapeared (meaning - it was working but I couldn't connect due to constant showing dialog box for a security passphrase), but I had no time to figure what's wrong, so yesterday I connected wired connection and made another ("partial") upgrade, and after the reboot I thought everything was in order, as my Network manager icon showed I was connected. But some minutes after, again - I got the dialog box asking me to input my wireless network passphrase. And when I input it - even though the passphrase (40/128bit) showing at the field is correct, ubuntu tries to connect but after trying again gives back the same dialog box asking fore passphrase. Any thoughts?

I am using WEP 128bit encryption with "Open" system.

I am sorry I'm not near my laptop at the moment - so I cannot paste any logs right now, but I will, if necessary, at the evening, when I am at home.

---

### Post by t.rulands on 2008-10-17
I think i may have the same problem. I upgraded from 8.04 to 8.10 yesterday and now the wireless connection wont work. I can see other wireless networks (mine is hidden) but i cant connect to my WPA protected wlan. The dialog box for the security passphrase always pops up and even tho i enter the right pass it wont connect.

I'm on a HP pavillion dv9318ea laptop with a intel 3945ABG wireless adapter (thats what windows tells me it is anway...)

---

### Post by Teamgeist on 2008-10-17
Have you guys tried to connect to an unencrypted network.
Does that work?

Does this sound familiar?
[http://ubuntuforums.org/showthread.php?t=950566](http://ubuntuforums.org/showthread.php?t=950566)

---

### Post by montini on 2008-10-17
> **Teamgeist said:**
> Have you guys tried to connect to an unencrypted network.
Does that work?

Does this sound familiar?
[http://ubuntuforums.org/showthread.php?t=950566](http://ubuntuforums.org/showthread.php?t=950566)

What do you mean by "unencrypted"? Do you mean to use "open" network, event without WEP? Then I haven't tried, as it was operational until 10.15 upgrades. By the way, in the given thread it is said there were problems with WPA, and someone proposes to use WEP, but I am using WEP already. I will try to configure my network as "open" when I come home but You understand it is not a solution as I can't work on a wireless network which is not protected even with WEP.

---

### Post by t.rulands on 2008-10-17
I just updated my system (over a wired connection) but that didn't help. Then i changed my network to unencrypted but i still cant connect to it...

---

### Post by montini on 2008-10-17
I don't know what I did - but one more time I have experienced that phenomenon with NM asking passphrase - then I rebooted, network was up, and I managed to get another bunch of upgrades via Update Manager - and after the reboot everything seems to be ok - no requests for pasphrase. I thought it was something to do with bluetooth manager switching - as I always press "Fn-F5" on my R61 Thinkpad to powerdown bluetooth service as I don't use it everyday. So after the upgrades I switched it off again - and I thought network would go down aswell,- and it have disconnected but surprisingly it reconnected again so I'm not sure if the problem has been solved with the recent upgrades, but now it is working, I'm crossing fingers :)

---

