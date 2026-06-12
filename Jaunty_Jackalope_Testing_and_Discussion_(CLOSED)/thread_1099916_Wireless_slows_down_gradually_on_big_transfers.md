---
title: "Wireless slows down gradually on big transfers"
date: 2009-03-18
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by scaine on 2009-03-18
Can someone using their wireless connection try this for me?  I just transferred the Jaunty alpha 6 ISO file (600Mb or so) from my little server box upstairs to my laptop using wireless.

Around 400Mb or so in, the transfer rate drops from 3Mb/sec to around half that.  Then over the next few minutes keeps gradually reducing in speed.  I've tried this three times now so it appears to be reproducible.

The same copy over ethernet is very quick (the server has a Gig connection so can typically transfer at around 14Mb/sec over ethernet).

Actually quite cool - during the third copy, I just plugged the ethernet into the laptop and once Network Manager confirmed eth0 was connected, the 400k/sec transfer rate just shot straight up over the next few seconds until the transfer completed shortly thereafter.  I had no idea that an active file copy would transition from one NIC to another (regardless of WIFI) so seamlessly.  Very nice.

So, can someone give a large samba file copy a try over wireless and report back here.  If there's other's affected, I'll raise a bug.  In fact, I'll go searching now - I've already searched the Jaunty forum itself.

[EDIT : Looks like this bug *may* be relevant :
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/190515?comments=all](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/190515?comments=all)
But I'm away from my lappie at the mo.  I'll test it later (add the backports module).]

---

### Post by Bert Mariën on 2009-03-21
I have the same problem with my laptop (Dell).

This fixes it:

Add to /etc/rc.local

ifconfig wlan0 up
iwconfig wlan0 rate 54M fixed

exit 0

---

### Post by scaine on 2009-03-21
Thanks - a few people suggested that in the bug report I posted, but I haven't been on my laptop on the past couple of days to test it out.  I'll give it a shot, although I'm not sure that 54M is the right setting for an N-based card... it should be connecting at a higher rate.

---

### Post by Bert Mariën on 2009-03-21
Maybe the speed is not realy what you want, but it is better than a slow (4 k) speed.

---

