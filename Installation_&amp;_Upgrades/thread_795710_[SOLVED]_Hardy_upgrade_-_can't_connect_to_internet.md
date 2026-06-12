---
title: "[SOLVED] Hardy upgrade - can't connect to internet!"
date: 2008-05-15
forum: Installation &amp; Upgrades
---

### Post by Hayesio on 2008-05-15
Hi Guys,

I just upgraded to Hardy Heron from Feisty and now i can't connect to my wireless internet. I think the wireless card is ok, at least it displays my ESSID and everyone elses in the neighbourhood.  When i sellect mine, which has no encryption, nothing happens - their is no signal, nothing, it just says "Disconnected."  If i select someone elses, it asks for the encryption key etc., i put in 000000000000000 and press connect and it displays the signal for there connection (i obviously cant connect without the right key but i at least get a signal strength). If after doing the above, i select my ESSID from the list again, it switched to my connection and this time does show the signal strength - but it still says disconnected!  

The card is RT2500 802.11g Cardbus/mini-PCI.
This card and internet ran flawlessly in Feisty.

A few things i have noticed different: The driver in Hardy is RT2500PCI and the logical name is wmaster0. In Feisty, RT2500STA and logical name ra0.

One last thing, if i try to configure the device through the Network tools program, it says the device doesnt exist!

Does anyone have a clue what the problem might be? Do you think i should try reverting to the RT2500STA driver?

Any help would be greatly appreciated.

---

### Post by EXCiD3 on 2008-05-17
I would try this: [http://ubuntuforums.org/showthread.php?t=784031](http://ubuntuforums.org/showthread.php?t=784031)

Note on Upgrading: almost every time you are bound to see things break. Wireless and video are the two most problematic for upgrading your system. Consider doing a fresh install for each version you change to. Just create a separate /home and then remount it as /home when you do the installation. All your settings will be saved, hardware will be functional (or at least wont break) and all you will need to do is reinstall your software (which will probably be newer versions you would want to upgrade to anyways).

---

### Post by Hayesio on 2008-05-18
Thanks EXCiD3.  Problem solved! :)

---

