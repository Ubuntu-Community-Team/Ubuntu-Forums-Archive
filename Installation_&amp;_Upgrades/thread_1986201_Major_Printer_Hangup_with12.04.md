---
title: "Major Printer Hangup with12.04"
date: 2012-05-24
forum: Installation &amp; Upgrades
---

### Post by WilhelmGGW on 2012-05-24
Last week I did a clean, fresh, full install of 12.04 on a Dell destop, where I previously ran various iterations and versions of Ubuntu. On previous intalls and upgrades, all worked fine. Now with 12.04, I can't get my network printer to respond as it should. I have tried every imaginable driver setup to make it work, and nothing speeds it up. I'm convinced the printer is set up right.

I think I have a more systemic problem with this. If I open the System Monitor - Resources - CPU History, when I click to print a document, the CPU of one core spikes to 100% and stays there for a long time. Then it drops down, the Network History revs up on the Sending side, and the status light on the printer begins blinking. That goes on for a while, then finally the document will (usually) print. This usually takes 1-10 minutes.

Also.. When the print job is hung up -- hogging resources and "processing" -- I've found that it sometimes suddenly releases from its hung state and prints immediately exactly when I execute some other input command to the system. When that's happened, I've been so wonderfully ecstatic that I've not noted exactly what I did that got things going. But it's like *yes!* there is something that releases whatever processing bottleneck that there is and lets printing proceed as it should.

Once a print job finally clears, everything returns to normal on the System Resource Monitor. Other than this issue with printing, nothing else on the computer seems slow, choked, throtled, or otherwise starved for available cycles.

Is there any tweaking I can do on my end to resolve this, or is it some issue with 12.04 that's still to be resolved?

---

