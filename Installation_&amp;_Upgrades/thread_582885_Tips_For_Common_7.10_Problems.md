---
title: "Tips For Common 7.10 Problems"
date: 2007-10-20
forum: Installation &amp; Upgrades
---

### Post by watchitman on 2007-10-20
I've hit two big stubling blocks with the Ubuntu 7.10 "Gutsy Gibbon." Fortunately, I've solved or found the solution in other threads for them! I've seen others with the same problems. If you've found a solution to a problem in 7.10, please feel free to post it here!

PROBLEM: Firefox times out.
SOLUTION: From steviemc

> **steviemc said:**
> Hi,
I had exactly the same problem...I found this in the Help...

3.2.7.&#8195;IPv6 Not Supported

   1. IPv6 is supported by default in Ubuntu and can sometimes cause problems.
   2. To disable it, open a Terminal (Applications &#9656; Accessories &#9656; Terminal) and type the command: gksudo gedit /etc/modprobe.d/aliases.
   3. Find the line alias net-pf-10 ipv6 and change it to read alias net-pf-10 off.
   4. Reboot Ubuntu.

This solved my problems.

Cheers

PROBLEM: Can't update software sources.
SOLUTION: In the Software Sources dialog choose "Other" in the "Download from" dropdown menu then click "Select Best Server." It should find the best repository mirror for your location.

---

### Post by watchitman on 2007-10-21
PROBLEM: Can't update software sources part 2 - I've got a D-Link router.
SOLUTION: Use OpenDNS: [https://www.opendns.com/start?device=ubuntu](https://www.opendns.com/start?device=ubuntu)

---

