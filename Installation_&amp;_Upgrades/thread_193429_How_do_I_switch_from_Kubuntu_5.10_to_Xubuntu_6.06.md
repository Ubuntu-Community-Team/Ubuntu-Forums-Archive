---
title: "How do I switch from Kubuntu 5.10 to Xubuntu 6.06?"
date: 2006-06-10
forum: Installation &amp; Upgrades
---

### Post by pbmax on 2006-06-10
I've decided I didn't like Kubuntu 6.06 as much as I thought, but Xubuntu 6.06 is very nice.  I like it clean.

I couldn't figure out how to downgrade back to Breezy Kubuntu, so I just reinstalled from CD.

Is there a way to upgrade from Breezy Kubuntu to Dapper Xubuntu without reinstalling everything again?

Thanks
pb

---

### Post by aysiu on 2006-06-10
You can go from Kubuntu Breezy to Kubuntu Dapper and then install Xubuntu on top of that.

Or if you're working off a clean Breezy install, reinstall Breezy but use a *server* install and install Xubuntu from there: [http://www.psychocats.net/ubuntu/xubuntu](http://www.psychocats.net/ubuntu/xubuntu)

---

### Post by pbmax on 2006-06-10
That did it. Thanks!

First I did apt-get install xubuntu-desktop

then I modified the repository from breezy to dapper
apt-get update
apt-get dist-upgrade

went to bed.

then used the "pure xfce" instructions on the (awesome) psychocats tutorials

thanks
pb

---

