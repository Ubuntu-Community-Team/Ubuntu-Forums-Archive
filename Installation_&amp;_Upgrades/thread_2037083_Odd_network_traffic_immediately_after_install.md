---
title: "Odd network traffic immediately after install"
date: 2012-08-03
forum: Installation &amp; Upgrades
---

### Post by khea_actua on 2012-08-03
I recently installed Ubuntu 12.04 on my system over CentOS 5.7.

I later received a report from shadowserver.org that the system had accessed irc.undernet.org (IP   208.83.20.130 ) basically at the time the install likely finished.  That IP is some system in Tampa, Florida, USA that seems well known on the internet to be malicious.

At this point, there were no user accounts on the computer other than mine (which had just been created), though files from the earlier system persisted.

I have no idea when or how my system could have been compromised.. I've even seen that IP show up on these forms ( [http://ubuntuforums.org/showthread.php?t=1403787&highlight=208.83.20.130](http://ubuntuforums.org/showthread.php?t=1403787&highlight=208.83.20.130) )

I hate to suggest this, but is it possible that the image I used to install had code in it to access this IRC server?  I only ask because it happened so soon after (minutes) the install.

---

### Post by cortman on 2012-08-03
Did you [check the iso md5sum]("https://help.ubuntu.com/community/HowToMD5SUM/")? If they don't match up, that's a dead giveaway.

---

### Post by khea_actua on 2012-08-03
I confess I didn't...  I don't have the original .img file I used anymore though.

I downloaded it from the Ubuntu site.  (not sure what mirror) and just assumed it'd be fine.

Would I be able to check from the USB stick I burned the image onto?

---

### Post by cortman on 2012-08-03
> **khea_actua said:**
> I confess I didn't...  I don't have the original .img file I used anymore though.

I downloaded it from the Ubuntu site.  (not sure what mirror) and just assumed it'd be fine.

Would I be able to check from the USB stick I burned the image onto?

Not that I know of- how hard would it be to download a new ISO (and check it) and reinstall? That may be your best option.

---

### Post by khea_actua on 2012-08-03
It'd be easy.  I'll do that now.  Just... If I did happen to download a compromised ubuntu iso off of some mirror, what are the odds that I'd download the same one?

---

### Post by cortman on 2012-08-03
> **khea_actua said:**
> It'd be easy.  I'll do that now.  Just... If I did happen to download a compromised ubuntu iso off of some mirror, what are the odds that I'd download the same one?

Don't know the odds, but you can be absolutely sure it's not corrupt by checking the md5sum. You can check that in any OS including Windows.

---

### Post by Cheesehead on 2012-08-03
It seems easy enough to test if an install image has been compromised. Install into a VM, and let the hosts's firewall log any packets to/from that address.

If a test of this sort returns positive, please file a bug in Launchpad and add the Ubuntu Securty Team to the bug.

---

