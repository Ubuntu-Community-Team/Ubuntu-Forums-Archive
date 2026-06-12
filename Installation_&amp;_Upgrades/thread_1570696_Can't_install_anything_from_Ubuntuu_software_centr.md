---
title: "Can't install anything from Ubuntuu software centre"
date: 2010-09-08
forum: Installation &amp; Upgrades
---

### Post by M_Mynaardt on 2010-09-08
I keep getting "Unknown Error; this should not happen" every time I try to install something from the Ubuntu Software centre.

My computer in question is an Acer Aspire One Netbook.  I recently put a double install on it: Ubuntu 10.04 Netbook edition, and Mint Linux 9 XFCE.  Everything else seems to be working just fine on both Ubuntu and Mint, except downloading software seem to be temperamental at best.

The Internet connection is fine.  I've tried wireless, ethernet, and broadband.  All the connections are fine.  No problems with email or browsing, but it just won't install any software from the software centre.  I type in my password, and after about 5-10 seconds I get that error message.  Nor do I seem to have this problem on either my desktop nor my older laptop on Ubuntu.  This is rather annoying!

Would anyone know what gives?

Or did I just pick a bad time and day when the software centre wasn't quite up to scratch?

-------------------------------------------------------------------------------


The details given with the error message are:

Traceback (most recent call last):
  File "/usr/lib/python2.6/dist-packages/aptdaemon/worker.py", line 126, in _process_transaction
    self.install_packages(self.trans.packages[0])
  File "/usr/lib/python2.6/dist-packages/aptdaemon/worker.py", line 207, in install_packages
    self._commit_changes()
  File "/usr/lib/python2.6/dist-packages/aptdaemon/worker.py", line 551, in _commit_changes
    changes = self._cache.get_changes()
  File "/usr/lib/python2.6/dist-packages/apt/cache.py", line 179, in get_changes
    for pkg in self:
  File "/usr/lib/python2.6/dist-packages/apt/cache.py", line 161, in __iter__
    yield self[pkgname]
  File "/usr/lib/python2.6/dist-packages/apt/cache.py", line 154, in __getitem__
    pkg = self._weakref[key] = Package(self, self._cache[key])
KeyError: 'X(\xc0\xa8'

---

### Post by mörgæs on 2010-09-08
Try to boot the machine and install your programs through Synaptic. Unlike the software centre, it always works.

---

### Post by M_Mynaardt on 2010-09-08
**[COLOR="Red"][SIZE="4"]It works now!![/SIZE][/COLOR]**

Timing is everything, you know.  Less than one whole _minute_ after I posted that bit about the software centre not working, I got a message from the download centre.  It told me that it couldn't work because my computer was running on battery power.

_That_ never occurred to me!  Mostly because the batter was almost fully charged, so I didn't bother plugging it in!  Oh well...

So, anyway, I plugged in the netbook, opened up the software centre and ... voila!!  It works!!

Note to self (and maybe others); make sure you have your netbook (and laptops too?) **_plugged in_** when you download lovely new software!

I'd like to say I solved this one by being so smart I should be twins, but nope!  It was just a fluke of timing!

---

