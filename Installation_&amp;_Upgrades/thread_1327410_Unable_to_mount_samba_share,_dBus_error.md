---
title: "Unable to mount samba share, dBus error"
date: 2009-11-15
forum: Installation &amp; Upgrades
---

### Post by jbox78 on 2009-11-15
Recently upgraded from Jaunty to Karmic, and when I try to mount a samba drive on my Ubuntu 8.10 server, which worked before, I now get the error message below:

DBus error org.freedesktop.DBus.Error.NoReply: Message did not receive a reply (timeout by message bus)

Any ideas?

---

### Post by spagaggum on 2009-11-19
how is this solved??

I got same problem..

Though... it was working even after the up to 9.10 than the power went out and my laptop shut down, upon turning it back on I can see windows shares on my network, but not access them.

---

### Post by mcab on 2009-11-21
I am also puzzled by this showing as 'Solved' when no solution has been presented.

I have the same, or very similar, problem. Since upgrading to Karmic I have been unable to access one particular share on my network. All others appear to work fine.

If someone actually does have a solution for this problem it would be appreciated if it could be posted.

---

### Post by analyst2009 on 2009-12-13
Exactly the same message with Ubuntu 9.10 (My "OneTouch4 Plus" USB Hard drive is mounted on Belkin N+ Wirless Router, and works with my other Windows Machines XP and Windows 7)

Would appreciate any insight into this matter.
Thanks.

---

### Post by jcmhunting on 2009-12-15
Same error message with no network access.  Any ideas?

---

### Post by rinki1121 on 2009-12-19
I had the same problem.
In my case,  I could mount samba share by using IP address of the samba server not the name.

---

### Post by franciscodavid on 2010-02-17
I had this problem, too.

What I did was to remove all the passwords stored in my user keyring related to the samba host. I think nautilus was trying to use the username & password I had in the keyring which didn't have permissions to access that concrete samba folder.

In my opinion, nautilus does not handle very well different samba users on the same samba server.

---

### Post by johnh10000 on 2010-02-21
Well I have had hassels too.  So far an iffy soloution:

on your firewall open the folowing ports

137-139
445
5353    <- not documented everywhere

if that don't do it i find letting your local lan have free reign so
192.168.1.0/24  should do it.

but samba does seem a bit flaky in karmic.  I sometimes still have to just turn the firewall off !!!!!

looking for a more secure solution

---

