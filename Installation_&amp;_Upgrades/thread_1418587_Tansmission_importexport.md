---
title: "Tansmission import/export"
date: 2010-02-28
forum: Installation &amp; Upgrades
---

### Post by PepeLapiu on 2010-02-28
Hi all
I run two machines and both are running Transmission to download/upload torrents.
I am selling one of them but not all the torrents will have the time to finish downloading before the buyer picks up the machine. How can I transfer my partially downloaded torrents from one machine to the other?
I have an external drive but I don't know how to do this.

Thanx,
PepeLapiu :D

---

### Post by tommcd on 2010-03-02
Just copy both the Whatever_Stuff.torrent file and the partially downloaded Whatever_Stuff file or directory to your new computer or external drive or whatever. Put them both in the directory that you have configured transmission to download to on the new computer (home, desktop, or wherever). Then open transmission on the new computer, load the Whatever_Stuff.torrent file, and it should detect the partially downloaded Whatever_Stuff torrent and pick right up where it left off.
I have started downloading a torrent in Ubuntu, and then booted Slackware and finished downloading the torrent in Slackware (on the same computer) and vice versa. The torrents just pick up where they left off and finish downloading. I have also downloaded a torrent in Ubuntu, and then continued seeding it in Slackware, and vice versa. It always works.

---

