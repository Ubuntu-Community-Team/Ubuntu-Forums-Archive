---
title: "Jaunty Root Terminal not working?"
date: 2009-04-08
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by EZEN on 2009-04-08
Setting up Jaunty on my laptop I am not able to open Root Terminal.](*,)

Regular terminal opens but I cant dpkg to install or chown my usual directoires using sudo or su.

Any ideas?
Anyone else having this problem?

Thanks
B

---

### Post by coffeecat on 2009-04-08
> **EZEN said:**
> Setting up Jaunty on my laptop I am not able to open Root Terminal.](*,)

Regular terminal opens but I cant dpkg to install or chown my usual directoires using sudo or su.

Do you mean that Jaunty is working differently for you than earlier releases, or that you didn't realise [you can't su to root in the same way as with other distros]("https://help.ubuntu.com/community/RootSudo")?

Jaunty gnome terminal is working fine for me. I prefer to sudo when needed, but I've just tried 'sudo -i' and that's given me a root terminal.

---

### Post by EZEN on 2009-04-08
What I mean is that the standard root terminal that I always prefer simply will not start up in Jaunty. (crashes?) (I usually enable it in the main menus)

I find root much more to my liking when messing with tons of data. I also backup and clear my archives in stages so I can clone to 11 other systems that are offsite.
So you can see where messing with sudo and permissions may make things much slower for me.

Upnote is: 'sudo -i' does work...YAY and I'll study up on sudo as a refresher course.

Thanks for the problem solve and the link.
You saved my day!
:)
B)

---

### Post by FuturePilot on 2009-04-08
[https://bugs.launchpad.net/ubuntu/+bug/326158]("https://bugs.launchpad.net/ubuntu/+bug/326158")
Bug

---

### Post by Reiger on 2009-04-08
This is strange, but maybe manually setting a password for root fixes it? I've done that (sudo passwd root) on my Hardy/Intrepid machines which I subsequently upgraded to Jaunty and I can drop to root shells and the like.

---

### Post by autocrosser on 2009-04-08
Manually setting a password has not changed things for me (anytime I install, I setup a passwd for root soon after)--I got around it with a custom launcher that will do a gksudo nautilus as I tend to much around with nautilus quite a bit.....

---

