---
title: "cant install 8.04"
date: 2008-06-10
forum: Installation &amp; Upgrades
---

### Post by Hairy_Palms on 2008-06-10
ive been happily using 8.04 since its alpha phase on an upgraded 7.10, just now i decided i would try a fresh install, but funnily enough discovered it wont install, it fails at the same point with this error
```
The installer encountered an error copying files to the hard disk:

[Errno 5] Input/output error

This particular error is often due to a faulty CD/DVD disk or drive, or a faulty hard disk. It may help to clean the CD/DVD, to burn the CD/DVD at a lower speed, to clean the CD/DVD drive lens (cleaning kits are often available from electronics suppliers), to check whether the hard disk is old and in need of replacement, or to move the system to a cooler environment.

```

no idea what im supposed to take from that, its not hardware, i slapped the gutsy disc in to test and the install worked fine, as does the hardy install if i run it in vmware. any ideas? CD passes checksum and was burnt at 4x in my current hardy install.

---

### Post by wpshooter on 2008-06-10
Did you check the integrity of the Ubuntu CD by running the verification function that is found on the initial Ubuntu boot screen menu ?

---

### Post by LeeU on 2008-06-10
This has become a major problem. See: [http://ubuntuforums.org/showthread.php?t=600126&page=6]("http://ubuntuforums.org/showthread.php?t=600126&page=6")

I have burned 6 CDs (Live and alternate), verified the CD, changed hard drives and RAM memory, and changed the CD unit and nothing changes. I get to 85% of loading the software and it produces the above error. The computer ran Ubuntu fine before. I have tried it with Heron and Gutsy. This seems to be a problem that no one is paying attention to.

---

### Post by Hairy_Palms on 2008-06-10
> Did you check the integrity of the Ubuntu CD by running the verification function that is found on the initial Ubuntu boot screen menu ?
yes, as stated in the first post it passes the checksum.
is there an existing launchpad for this bug? if not ill open one.
im not going to upgrade my working partition and start testing ibex until i can get a safe install of hardy,

---

### Post by wpshooter on 2008-06-10
Hmmmmmmmmmmmmm.

I was recently trying to install several versions of Ubuntu to some old IBM netvista workstations and I was seeing something similar to this "can not write files to hard disk" message that is mentioned in this thread.

I had 3 of these machines that had IBM deskstar drives in them and they all exhibited this behavior during the installs.

I had a 4th IBM netvista which had a Western Digital hard drive in it and I (subsequent to the above mentioned problems with the other 3 machines) installed the Ubuntu O/Ss to this 4th machine with zero problems.

I was beginning to believe that the **DESKSTAR** hard drives in the first 3 machines were defective but having read this thread, I think I may go back and beat that horse a bit more before I give up.  What do you think, worth a try or not ?

Thanks.

---

### Post by LeeU on 2008-06-10
Well, the drives I'm using are Western Digital also.

---

### Post by wpshooter on 2008-06-10
> **Hairy_Palms said:**
> yes, as stated in the first post it passes the checksum.
is there an existing launchpad for this bug? if not ill open one.
im not going to upgrade my working partition and start testing ibex until i can get a safe install of hardy,

I have had CDs pass the sumcheck just fine but yet NOT pass the integrity test that is found on the initial Ubuntu boot screen menu.  Therefore, I ALWAYS do both not just one of these test.

---

### Post by LeeU on 2008-06-10
In my case, it passes the sumcheck AND the integrity check.

---

