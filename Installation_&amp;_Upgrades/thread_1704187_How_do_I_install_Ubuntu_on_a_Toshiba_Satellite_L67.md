---
title: "How do I install Ubuntu on a Toshiba Satellite L670D-102"
date: 2011-03-10
forum: Installation &amp; Upgrades
---

### Post by bwallum on 2011-03-10
Hello

I have been trying to load Ubuntu 10.10 (tried both AMD64 and i386  versions of Desktop Edition) onto a Satellite L670D-102 using a Live CD.  The CD spins for a while, there is some activity on the hard drive and  then I get a flashing white cursor (a hyphen) on a black screen. I left  it all night and it remained the same. I tried with a 'live' usb and  again, no boot. The cds and usb work in other machines running both amd  and intel cpus.

The sort of questions that spring to mind are:-
Is there some security or other setting within the cmos that prevents anything other than Windows being loaded?
Are Toshiba simply anti- Linux and I need a new machine?
Do I need a special bios to run Ubuntu?

Any help in resolving the issue would be welcome.

---

### Post by bwallum on 2011-03-10
Found It!

In the cmos menu (press F2 before boot), under the Advanced Tab there is a setting called USB Legacy Emulation. If this is set to 'Enabled' the white flashing cursor as described will flash for ever. If set to 'Disabled' Ubuntu fires up ok. 100% repeatable.

---

### Post by markgw on 2011-04-04
This worked for me too. I'm using a Toshiba Satellite C660-153.

Up to now the only solution that worked for me was to set acpi=off in the kernel options - very unsatisfactory. This is the only solution I've seen posted elsewhere as well, so I suspect this post may be of use to others.

---

### Post by madwoollything on 2011-04-23
Same here with C660 14W ... thanks!

---

### Post by mörgæs on 2011-04-23
Good, please mark the thread 'solved'.

Would also be good, it you could mention the trick in this thread:
[http://ubuntuforums.org/showthread.php?t=1543006](http://ubuntuforums.org/showthread.php?t=1543006)

---

