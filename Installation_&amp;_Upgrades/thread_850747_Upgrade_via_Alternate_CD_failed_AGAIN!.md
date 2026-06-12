---
title: "Upgrade via Alternate CD failed AGAIN?!"
date: 2008-07-05
forum: Installation &amp; Upgrades
---

### Post by bsmith1051 on 2008-07-05
Why is it such an ordeal every time I try to upgrade from the Alternate CD?  I'm trying to use the CD (instead of the Internet) to make things _easier_!  Except that it never seems to work.  Instead, the upgrader will start, run for about 30 seconds, then disappear without any warning or error.  And now my system thinks there are 634 updates available but I'm afraid to let it update -- since I need an upgrade, not individual package updates.

I've tried checking the file, /var/log/dist-upgrade/main.log, but again there's no error -- just an abrupt end to the file.

I've tried reburning the CD and running a read-check afterwards.
The upgrade prompt no longer appears automatically so I've been manually starting it with 
```
> gksu "sh /cdrom/cdromupgrade"

```
I've tried selecting both Yes and No for "Download updates from Internet?"
I've tried resetting the Repositories in Synaptic, and just leaving them on the new Hardy ones.
I've tried uninstalling the 'Restricted Driver' for my Nvidia card.
I've even tried doing the default upgrade from the Internet.
Nothing works.

P.S.  I've had similar problems with the last 3 upgrades (starting the 6.06) and with multiple computers.
___________

Is there a way to **reset all the Synaptic settings** so that I can just try the upgrade from scratch?

Is there another way to **identify the error** (since the program doesn't see fit to report one)?

Any help is appreciated!

---

### Post by bsmith1051 on 2008-07-06
P.S. I'd also waited for the 8.04.1 'service pack' before trying to upgrade my main computer.  Fat lot of good that did me.

---

### Post by bsmith1051 on 2008-07-06
Now, a day later, it seems to be working?  I don't know what else I did that might have fixed it.  I know I tried running,
```
> sudo dpkg --configure -a

```
but it immediately returned to the command-line prompt and without any message.  So I assumed it hadn't accomplished anything.

I unchecked all the repositories, then clicked Add CD (under "3rd-party" tab) and let it scan the Alternate CD again.  Then I loaded the Update Manager and again clicked on Upgrade... and now it's working??

---

