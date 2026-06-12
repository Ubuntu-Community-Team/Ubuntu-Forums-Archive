---
title: "Receiving updates even when offline"
date: 2014-04-23
forum: Installation &amp; Upgrades
---

### Post by robire on 2014-04-23
I know sounds weird, but it's the truth.
happened several times before to me and yesterday again:

My computer was turned off at least for 3-4 hrs.,
turning on my Intel NUC on ubuntu 12.04. ( no wireless, no bluetooth ) modem is turned off conected by netwok cable,
after about 15 minutes update manager appeared and told me there is an update !!

checked again modem -- still turned off, .

Anybody any idea how to figure out what's going on ,.
a minstrel ? :-)

Regards
robire

---

### Post by tgalati4 on 2014-04-23
The package manager downloads a small database with version numbers and compares that with what is installed on your system.  It only takes a few seconds to download.  So if your machine was connected to the network for a few minutes over the past 24 hours, that is enough time to get the updated package information.  When there are differences between what is available and what is installed on your machine, you will get an update notice.

So if your machine is physically connected with an ethernet cable, even though you think the network card is turned off, it's possible that it was turned on long enough to get the update information before you turned it off manually.

---

### Post by robire on 2014-04-24
hmmm, the problem is, the modem has been turned off for hours.
The lookup for updates is running at 6pm at my computer .

I turned off the computer and modem about 4pm and turned on the computer shortly before 8pm.

So if information about updates was a the computers db before 4pm why I did not get that information earlier ?

Definitely, ther was no update manager displayed as I turned off the computer, and there was no update manager
as I turned on the computer.
It appeared approx. 15 minutes after the computer was turned on and the modem was still turned off.

---

