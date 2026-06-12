---
title: "Printing fails in Kubuntu Karmic"
date: 2009-09-02
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by awam66 on 2009-09-02
Hi All,

Since upgrading from Kubuntu Jaunty to Karmic I can longer print yo my Epsom R220 Printer. The printer is recognised but CUPS says "waiting for printer to become available" which it is. This is the sys log:

2009-09-02 18:58:05	kubuntu	kernel	[ 4267.434539] type=1503 audit(1251914285.423:116): operation="open" pid=3667 parent=2815 profile="/usr/sbin/cupsd" requested_mask="r::" denied_mask="r::" fsuid=0 ouid=0 name="/dev/bus/usb/"

Anyone else had this or do I need to post a bug?

---

### Post by forumache on 2009-09-02
yes, it was a bug, fixed with the recent cups update 1.4.0-3.1
[https://bugs.launchpad.net/ubuntu/+source/cups/+bug/420015](https://bugs.launchpad.net/ubuntu/+source/cups/+bug/420015)

Update, restart (there are some changes to apparmour) and you should be ok. If not, add your comment to the bug.

---

### Post by awam66 on 2009-09-03
Ah Thanks,
Looked at the bug, applied "sudo aa-enforce cupsd" and now all working.

---

