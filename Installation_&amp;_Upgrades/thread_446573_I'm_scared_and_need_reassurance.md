---
title: "I'm scared and need reassurance"
date: 2007-05-17
forum: Installation &amp; Upgrades
---

### Post by jonallport on 2007-05-17
Hi Ubuntu people,

I am about to take the plunge and replace my last non-Ubuntu linux server's OS with FF.  The box in question has a SCSI drive with the O/S (SuSE) and a software raid1 (MD) made from 2 other SCSI drives holding about 14GB of VERY IMPORTANT data.

I know I can backup/restore the data after having re-built the hardware config under Ubuntu, but I'd rather just install FF and drop in the /etc/mdadm.conf from the existing install.

So, the question is:  Will Ubuntu have a big panic if I do that or can I confidently try it (after having made sure that last backup was valid, of course)?

Thanks in advance for your help.

J

---

### Post by Kobalt on 2007-05-17
My last install of a RAID device was under the Dapper Drake and it worked flawlessly out of the box. In your case I would be confident then (making a couple of backups though).

---

### Post by Wim Sturkenboom on 2007-05-17
14GB of VERY IMPORTANT data and not making backups is a contradictio in terminus. With that approach I would also be scared.

If that data is very important, you should have made backups long ago.

---

### Post by jonallport on 2007-05-17
I have backups, and do it nightly (there's an inuendo in there somewhere).  What I want to avoid is having the server offline for hours as I restore the data especially as I would be putting it back where it came from, in the same configuration.

Feisty will take about 1/2 hr to install/setup with samba etc. but restoring the data from tape will take a further 2 1/2 hrs. 1/2 hr I can live with as overtime, 3 hrs and my wife will start to complain.

What I want: Install Feisty, drop raid config onto Feisty, go home to appreciative wife.
I want to avoid: Install Feisty, configure raid, restore from tape to raid, go home to find wife has left me.

---

### Post by hartz on 2007-05-17
Suggestion:

Tell wife you have a big job.  It is going to take 4 hours.  The overtime pay will buy her something nice.

Surprise her by arriving home early.

Still buy her something nice.

---

### Post by Wim Sturkenboom on 2007-05-17
I apologize; from your post I understood that you considered it to much effort. I fyou unly would have mentioned 'restore backup, I would not have replied.

Again, apologies.

---

### Post by jonallport on 2007-05-18
Not a problem, Wim.  Having re-read my post I probably would have made the same assumption.

hartz3, that'd be nice if I got more money for doing it.

Anyway, in summary:  I'll probably be OK if I drop the SuSE mdadm.conf into Ubuntu so that's what I'll do after having made sure I have good copies of the data on DDS and probably external HD.

Thanks everyone for you input.

J

---

### Post by jonallport on 2008-02-16
Thought I'd update this thread with the results.

I finally got around to migrating this server (and banged in a bit more RAM too).  As it happens I'd scp'd all of the data to another temporary server to keep things running should the worst occur.  When I brought the server back online with Gutsy at the helm I just ran mdadm -scan and it remade the /dev/md0 device exactly as it had been under SuSE - cool!  Then it's just a case of adding /dev/md0 and the appropriate mount point (/raid) to /etc/fstab et voila!!!

---

