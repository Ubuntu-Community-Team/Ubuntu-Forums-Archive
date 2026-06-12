---
title: "RANT: IDE Order &quot;Waiting for root&quot;"
date: 2006-06-08
forum: Installation &amp; Upgrades
---

### Post by mlwmohawk on 2006-06-08
I ran into a serious problem with 6.06, and I'm sorry, I completely disagree with the decision that this is not a criticle bug. It should have stopped 6.06 from shipping, and subsequently redering my system unbootable. (I had to search to even find mention of the bug, it wasn't even in the FAQ.)

Here's the problem. I had breezy badger, no problems. I tried to upgrade to Dapper. Unfortunately I have a second IDE controller. This causes the New kernel 2.6.15 to reverse the order in which it finds IDE drives. So, hda becomes hde and hde to become hda. You can this coming, right?

Now guys, wake the hell up. This has been a problem in Linux for a while, there used to be a work around "ide=reverse" which no longer seems to work.

This is NOT a minor problem This is a problem that will sink hours or days of peoples time and force them to reinstall a previous version. There is no easy way to downgrade.

I am seriously disappointed with the Ubuntu project.  If Linux fails it won't be because of SCO or Microsoft, it will be because of this type of utter nonsense. One of the supposed benefits of Open Source is that it doesn't ship until it is ready. Well, you shipped a product that REALLY wasn't ready.

---

### Post by jeremytaylor on 2006-06-08
I have to say I agree entirely. It's a good job ubuntu costs nothing, for me at least, that's all it's worth.
jeremy

---

### Post by pkunal on 2006-06-08
Hello is my configuration related to what you are already seeing? I just posted it a minute ago and saw your posting related on similar subject.

---------------------------------------------------------------------
I built a PC for the first time in my life. (I had experience upgrading).

However, I have an Intel D945GTPLR Motherboard with Pentium D processor.

Question:

There are 2 IDE connectors on board. FDD & Primary IDE. I do not have FDD and will not use that connector. I have configured such that HDD will be the Master Drive and CD/DVD RW will be the Slave on the same ribbon and connected to the Primary IDE. I have read about doing this and am sure atleast it is the right thing to do. Also the BIOS does support such configuration, allowing to BOOT from the Slave device (I READ BUT WILL RE-READ ON THE SAME).

WILL UBUNTU SUPPORT IT? HOW WILL THINGS LOOK ON UBUNTU? ANY IDEAS? Will both drives be detected automatically or will I have to mount the drives myself?

I sill have to start the system but need to do the final checks and pray before I do so.

Please let me know.
----------------------------------------------------------------------

---

### Post by mlwmohawk on 2006-06-08
[QUOTE=pkunal]Hello is my configuration related to what you are already seeing? I just posted it a minute ago and saw your posting related on similar subject.

---------------------------------------------------------------------
I built a PC for the first time in my life. (I had experience upgrading).

However, I have an Intel D945GTPLR Motherboard with Pentium D processor.

Question:

There are 2 IDE connectors on board. FDD & Primary IDE. I do not have FDD and will not use that connector. I have configured such that HDD will be the Master Drive and CD/DVD RW will be the Slave on the same ribbon and connected to the Primary IDE. I have read about doing this and am sure atleast it is the right thing to do. Also the BIOS does support such configuration, allowing to BOOT from the Slave device (I READ BUT WILL RE-READ ON THE SAME).

WILL UBUNTU SUPPORT IT? HOW WILL THINGS LOOK ON UBUNTU? ANY IDEAS? Will both drives be detected automatically or will I have to mount the drives myself?

I sill have to start the system but need to do the final checks and pray before I do so.

Please let me know.
----------------------------------------------------------------------[/QUOTE]

I suspect not, unless you have a separate controller card. In the universe of PC hardware, it is hard to be 100% sure, but typically, IDE controllers have two IDE channels are on one PCI slot. The ones built in to the motherboard work fine. The problem happens when you add an additional controller.

---

### Post by mlwmohawk on 2006-06-08
[QUOTE=jeremytaylor]I have to say I agree entirely. It's a good job ubuntu costs nothing, for me at least, that's all it's worth.
jeremy[/QUOTE]

I wouldn't say it is worthless, no way! I would say that they are being short sighted in being anything strict about "nuke your system" bugs, no matter how few people they may think it affects.

---

### Post by PesVseved on 2006-06-09
This bug is killing me....

In grun I got [COLOR="Red"]hda1[/COLOR]. It works just fine. Until I dock my laptop.....Then It wants to boot from [COLOR="Red"]hde1[/COLOR].

So I changed hda1 to hde1 in grub. But after this it does not have a swap partition.

I'm not really sure what to do......

I would downgrade to breezy If It weren't even more painful.........

Do you know how to solve it???

---

