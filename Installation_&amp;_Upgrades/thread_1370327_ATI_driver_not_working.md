---
title: "ATI driver not working"
date: 2010-01-02
forum: Installation &amp; Upgrades
---

### Post by s2212874 on 2010-01-02
I am using my ATI Radeon 9550 display card but just can't adjust it to 1920x1080 resolution in ubuntu 9.10.  I can't even start ATI Catalyst Control Center and i believe there is something wrong with the driver. When i try to start ATI Catalyst this message pop up
"There was a problem initilizing Catalyst Control Center Linux edition. It could be caused by the following.
No ATI graphics driver is installed, or the ATI driver is not functioning properly.
Please install the ATI driver appropriate for you ATI hardware, or configure using aticonfig."

Everything works fine in Ubuntu 8.10. Please help.

---

### Post by Mark Phelps on 2010-01-02
> **s2212874 said:**
> I am using my ATI Radeon 9550 display card but just can't adjust it to 1920x1080 resolution in ubuntu 9.10.  I can't even start ATI Catalyst Control Center and i believe there is something wrong with the driver. When i try to start ATI Catalyst this message pop up
"There was a problem initilizing Catalyst Control Center Linux edition. It could be caused by the following.
No ATI graphics driver is installed, or the ATI driver is not functioning properly.
Please install the ATI driver appropriate for you ATI hardware, or configure using aticonfig."

Everything works fine in Ubuntu 8.10. Please help.

That's because there WERE ATI drivers that worked with Intrepid -- but those drivers were retired and there are no ATI drivers that work with your card and Ubuntu versions newer than 8.10.

If you read the link below, you will find directions on removing the ATI restricted drivers (fglrx) and replacing them with the open source drivers:

[http://https://help.ubuntu.com/community/RadeonDriver]("https://help.ubuntu.com/community/RadeonDriver")

---

### Post by complience on 2010-09-23
I'm having the same problem,

I'm using Ubuntu 10.04

I changed the resolution on my 2nd monitor and the ATI drivers fail.

I can't understand why changing the resolution settings would kill the drivers - looks like a major bug to me.


"There was a problem initilizing Catalyst Control Center Linux edition. It could be caused by the following.
No ATI graphics driver is installed, or the ATI driver is not functioning properly.
Please install the ATI driver appropriate for you ATI hardware, or configure using aticonfig."

---

### Post by complience on 2010-09-24
Disactivated and then downloaded and reactived the drivers again.

Resoultion reset to the default and all works again :guitar:

---

