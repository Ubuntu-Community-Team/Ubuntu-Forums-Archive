---
title: "Kernel Panic on mythbuntu-diskless client"
date: 2009-11-29
forum: Installation &amp; Upgrades
---

### Post by gurtnamona on 2009-11-29
A few weeks ago I upgraded my main machine to 9.10 and found that Mythbunutu Control Centre no longer contained the diskless server plugin. I then followed the instructions at 
[Mythbuntu Diskless on Karmic]("https://help.ubuntu.com/community/MythTV/Install/Karmic/Diskless").

Since then I have not been able to get my (previously booting) diskless client to boot. I receive the error:
> run-init: /sbin/init: No such file or directory
[   8.114217] Kernel panic - not syncing: Attempted to kill init!

I have reinstalled mythbuntu-diskless-standalone and rebuilt /opt/ltsp/* and /var/lib/tftpboot/ltsp/* with no change.

I have seen some mention to this error occuring with bad RAM so I have swapped out with known good RAM with also no change.

I have not attempted a diskless client other than with Mythbuntu so I am ignorant as to whether this has anything to do with Mythbunutu 9.10. I have scoured forums for the past few days attempting to resolve this but have had no luck. Any help would be greatly appreciated. Please let me know what additional information might aid in diagnosing the issue.

-Gurntamona

---

### Post by gurtnamona on 2009-12-01
I have been spinning my wheels here. After re-chmoding the /opt/ltsp/ and /var/lib/tftp/ltsp/ directories the error has changed to

> /sbin/init: relocation error: /sbin/init: symbol __abort_msg, version GLIBC_PRIVATE not defined in file libc.so.6 with link time reference
[ 7.864197] Kernel Panic - not syncing: Attempted to kill init!

I don't know if there was an access issue with those directories or if this is just coincidence. 

Since my first post, I have built a new computer for my girlfriend. Its a Core2Quad 2.66GHz that I changed to boot over the LAN in order to test my configuration. Much to my surprise, it worked. Mythfrontend crashed but that is not my focus at the moment.

The client that has been giving me the issue is a Zotac ION with 4GB of RAM.

Again, if there is any other information that may be useful, please let me know. If anyone has any suggestions on what to try, I am at a loss.

---

### Post by gurtnamona on 2009-12-02
Wow. The silence is deafening. So here is where I am:

Since the only semblance of resolution that I could find in other "kernel panic" posts were regarding hardware failure, I opened up the lid on my girlfriend's new computer and my (non-booting) diskless client and plugged the HD from the computer into the client. Voilà! Everything boots perfectly.

Next step, I put everything back together and now configure my girlfriend's computer as the diskless server. Surprise #3, everything boots! 

In summary,
My diskless server will NOT boot my diskless client.
My diskless server will boot her computer configured as a diskless client.
My "diskless" client will boot with the HD attached from her computer.
Her Computer configured as a diskless server will boot my diskless client.

Given that I have neither the skill nor assistance to troubleshoot this further, it looks like I will be reinstalling Ubuntu as a fresh install in hopes that it removes whatever gremlins are causing me issue. I was hoping to avoid a fresh install since I have gotten by with just upgrades for a couple years now. 

Ah well, I do suppose that starting over after a failure is the way by which I've learned most of what little I know about linux.

Take care,

-gurtnamona

---

