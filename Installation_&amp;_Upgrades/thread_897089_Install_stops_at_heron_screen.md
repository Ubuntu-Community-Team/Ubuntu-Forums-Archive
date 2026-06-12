---
title: "Install stops at heron screen"
date: 2008-08-21
forum: Installation &amp; Upgrades
---

### Post by IchBin on 2008-08-21
So I'm having the same problem that this guy had in this topic.
[http://ubuntuforums.org/showthread.php?t=881701](http://ubuntuforums.org/showthread.php?t=881701)

I tried the same fix of acpi=off but that didn't do the trick for me. The install still stops at the screen where the desktop picture of the orange/red heron appears. I see the mouse cursor but nothing further than that. Not sure what else to try. Anyone have any suggestions?

I threw in a Slackware12 disk a friend gave me and it seems to go through with an install just fine. But, I don't want to run Slack. :)

TIA

--edit-- 
I should also note that I've done the CD check, as well as tested it on another computer and the CD is fine.

Computer specs:
AMD X2 6800
2GB Ram
onboard hardware via chipset

---

### Post by Partyboi2 on 2008-08-22
Maybe try updating your bios if you are able to. Another thing you could try is to disable  ACPI in your bios if you have that option.

---

### Post by IchBin on 2008-09-06
Hmmm... I didn't seem to get an email when you replied. Didn't think anyone had in the mean time. So I just updated my bios tonight and it seemed to help. I now get to the point where it shows some services being started. It halts on Starting the bluetooth services. Done a search around there and haven't seen much suggested other than to try the alternate CD which I'll download tonight. :)

---

### Post by Crafty Kisses on 2008-09-07
You can try using the alternate CD, [here]("http://users.bigpond.net.au/hermanzone/") is some great information and tutorials on the alternate CD.

I'm thinking hardware is not the problem seeing as how your specs are better than enough to run Ubuntu, but you never know.

There could be a lot of issues, I'd run a memtest, you can do this by running this in the Terminal: ```
memtest
```

If I were you I'd definitely try the alternate CD, if that doesn't work please post back, and I'll try to figure something out for you, but I'm betting the alternate CD will work.

One last thing, I'd also check the **md5sum** and see if they match, because that can very well be an issue with the Ubuntu installation, also make sure you selected the right architecture for your download, I hope this helped.

---

