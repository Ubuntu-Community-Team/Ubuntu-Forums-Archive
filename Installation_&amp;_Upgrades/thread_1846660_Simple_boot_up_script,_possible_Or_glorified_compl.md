---
title: "Simple boot up script, possible? Or glorified complexity is &quot;better&quot; LOL"
date: 2011-09-19
forum: Installation &amp; Upgrades
---

### Post by bbiandov on 2011-09-19
Hi everyone,

The simplest task I though? Nooo - no such thing as simple.

I just want to execute bunch of commands on boot up. I do NOT want to run service; etc

[https://help.ubuntu.com/community/UbuntuBootupHowto]("https://help.ubuntu.com/community/UbuntuBootupHowto")

This stuff is uber complicated and it wants to "shut down" the daemons on reboot and there hides the problem. When running just basic scripts there is NO active process remnant as is the case with daemons. So on reboot there is nothing to shutdown and the whole complex chain of boot up scripts mechanism fails.

Isn't there a simple blahblah.sh that gets executed ONCE on boot up and its forgotten forever thereafter?

~B

---

### Post by Lars Noodén on 2011-09-19
Yes, there is.  One place to call such scripts would be /etc/rc.local

---

### Post by bbiandov on 2011-09-19
> **Lars Noodén said:**
> Yes, there is.  One place to call such scripts would be /etc/rc.local

Thanks Noodén, I did know of that but for some reason the command lines remain untouched during boot. And yes I did read the comments in the file and made it executable yet none of the lines are executed upon boot up.

Any ideas? Thank you

---

