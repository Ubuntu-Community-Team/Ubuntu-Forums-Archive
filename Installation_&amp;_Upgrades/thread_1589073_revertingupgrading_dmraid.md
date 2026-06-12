---
title: "reverting/upgrading dmraid"
date: 2010-10-05
forum: Installation &amp; Upgrades
---

### Post by MozaicIris on 2010-10-05
Like the fool that I am I clicked "yes" to upgrade to Lucid Lynx without taking the time to back up everything.

For the most part everything works, but it's not recognising my Silicon Images FakeRAID (Raid 5).

After extensive googling I've figured out that I'm missing the metadata format handler for silicon images raid 5, as can be seen from the excerpt from "dmraid -l" below.

> sil: Silicon Image(tm) Medley(tm) (0,1,10)

Since I didn't do anything unusual during installation I assume no such format handler exists in Lucid Lynx, but my RAID worked fine under Karmic Koala so my questions are:

1 - Did Karmic Koala use just dmraid to support fakeRAID? I see from the release notes that it included it but I can't work out whether I want to revert to its version of dmraid of whether there's something else I need to install.

2 - Is it possible to install additional format handlers and does the one I need even exist? If so then since I couldn't find any evidence of how to do this could you point me in the right direction?

3 - any other suggestions?

thanks :)

---

### Post by ronparent on 2010-10-05
This is strange! I booted Karmic to check dmraid status. That currently shows the same thing you found. You might have to examine the update notes on dmraid to see if a regression is likely to revert raid support to level 5. If level 5 support was eliminated, that would explain some other posts of problems with their fakeRAAID 5 on sil chipsets.

---

### Post by MozaicIris on 2010-10-06
If I boot Karmic from DVD I can read the RAID fine. And yet as you pointed out dmraid -l still indicates no  silicon images raid 5 support.

I am now very confused. What feature in Karmic Koala is making the raid work?

Everything google shows me suggests dmraid is the relevant application and  yet dmraid looks like it shouldn't work for either version.

---

### Post by ronparent on 2010-10-06
Unfortunately I am not operating a raid 5 so I cannot see your results. Likewise, the 9.10 live cd shows the same results as yours? Are you sure you used fakeraid to access your raid - type ls /dev/mapper. Or a software raid would be a /dev/dm-# device.

---

### Post by MozaicIris on 2010-10-09
Thankyou for your help ronparent.

I have fixed my problem by reverting dmraid to the karmic koala version, and it now just automagically works. I feel like I should be reporting this as a bug but I'm not sure I understand the issue well enough to articulate it so I will answer your questions in the hopes of figuring out the fault -

currently (after the dmraid rollback)

*ls /dev/dm**
retuns:
> /dev/dmmidil

and *ls /dev/mapper*
returns:
> control sil_baedgacfcce sil_baedgacfcce2 sil_baedgacfcce5

Which seems a little peculiar to  me, but works.

Before the rollback dmraid -vvvv was complaining that I had the wrong number of devices in the raid.

---

### Post by ronparent on 2010-10-09
It sounds all like just another mystery.

There is one other possibility. Which raid controller do you have activated on your MB? I, for instance, have a raid pair I had originally setup in a MB with an nvidia chip set. I later moved them to another MB with an AMD/Promise chip set. As I anticipated the partition tables were wiped. They still retain the nvidia tags and the new partitons are also tagged as nvidia! But they perform as normally as any fakeraid 0 can.

Out of curiosity what are the outputs of sudo dmraid -s or sudo dmraid -r?

---

