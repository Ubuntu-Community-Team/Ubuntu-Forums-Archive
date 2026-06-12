---
title: "Possible problem with /dev/*lp* in new installations"
date: 2010-03-23
forum: Installation &amp; Upgrades
---

### Post by colourfullegume on 2010-03-23
I recently installed Ubuntu 9.10 and have been trying to set up a USB printer.

I hit a problem which I eventually diagnosed as being the ownership of /dev/usb/lp0.

First, the symptom:

**~$ cat Test > /dev/usb/lp0**
bash: /dev/usb/lp0: Permission denied

The initial diagnosis:

**~$ ls -l /dev/usb/lp0**
crw-rw---- 1 root **lp** 180, 0 2010-03-23 21:39 /dev/usb/lp0

Notice the **lp** group?  When I checked group properties, this group did not have any members - not even root!!!

The default for CUPS (from the CUPS doc) is **lpadmin**, in any case, so not sure what **lp** is all about. In fact, the 'lp' group has ID=0, the same as the 'root' group.

I fixed it by doing this:

[B]~$ sudo chown root:lpadmin /dev/usb/lp0

[/B]Then I noticed that /dev/lp0 and /dev/parport0 also had group=lp, so I also did this:

[B]~$ sudo chown root:lpadmin /dev/lp*
[/B]**~$ sudo chown root:lpadmin /dev/parport***

Am I correct that this is an installation issue, or have I misdiagnosed?

---

### Post by colourfullegume on 2010-03-24
I can add some more info to this thread.  This issue is totally irrelevant as far as CUPS is concerned - please ignore the references to CUPS.  I can now print through CUPS despite not being able to do something like

echo Test > /dev/usblp0

(CUPS works when the URI is parallel:/dev/usblp0, rather than usb:/dev/usblp0)

However, I'm curious as to why this simple redirection to the device is disallowed until I change the permissions.

---

