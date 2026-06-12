---
title: "will ubuntu fix grub error 15"
date: 2008-06-27
forum: Installation &amp; Upgrades
---

### Post by ripin1 on 2008-06-27
hi, i got the dreaded grub error 15 and i was wondering if i could fix it by simply re installing ubuntu. but i looked at all the solutions on google and now my solution looks a bit too simple. it seems like you would be able to, right?

ps i might get win xp tomorrow so would installing that do it?

---

### Post by chewearn on 2008-06-27
> **ripin1 said:**
> hi, i got the dreaded grub error 15 and i was wondering if i could fix it by simply re installing ubuntu. but i looked at all the solutions on google and now my solution looks a bit too simple. it seems like you would be able to, right?

Yes, it easy to fix without reinstalling, if you know what to do.  But some info needed, like how many harddisk you have, etc.  Post output of:
```
sudo fdisk -l
```

> ps i might get win xp tomorrow so would installing that do it?

No, installing winxp will kill grub.

---

### Post by ripin1 on 2008-06-27
> No, installing winxp will kill grub.
at this point, i dont care. but anyway, that wasnt what i was asking. if i installed ubuntu with a cleen live cd and cleen every thing, will it work or would i have to do some kind of fancy steps.
> Yes, it easy to fix without reinstalling, if you know what to do. But some info needed, like how many harddisk you have, etc. Post output of:
Code:

sudo fdisk -l


i cant get a command line

---

### Post by chewearn on 2008-06-27
> **ripin1 said:**
> at this point, i dont care. but anyway, that wasnt what i was asking. if i installed ubuntu with a cleen live cd and cleen every thing, will it work or would i have to do some kind of fancy steps.

i cant get a command line

Yes, wipe everything and install clean will fix grub automatically.

---

### Post by ripin1 on 2008-06-28
thank you! i am sick of this linux stuff but it makes me proud i can do it. im only eleven

---

### Post by chewearn on 2008-06-28
Good luck.

---

### Post by ripin1 on 2008-07-01
ok, i have more problems.for some reason, windows vista is having an extremely hard time burning an xubuntu iso to a cd. im using infra recorder to do it, like you do on ubuntu, but it still wont work. i think its a problem with the recorder but i could be wrong. and second, i have this xp cd that when i pop it in to the drive and do all the stuff, it says: "setup is inspecting your computers hardware." and it hangs there. forever. so, what do i do? i was told that ubuntu would fix it and i asked about windows but no reply, just yeah, ubuntu will fix grub and blah blah blah! but it seems no one on this freakin web site knows how to give a specific answer.

im sorry.

---

### Post by chewearn on 2008-07-02
> **ripin1 said:**
> ok, i have more problems.for some reason, windows vista is having an extremely hard time burning an xubuntu iso to a cd. im using infra recorder to do it, like you do on ubuntu, but it still wont work.
Can't help you there, I'm not using Vista.

>  i think its a problem with the recorder but i could be wrong. and second, i have this xp cd that when i pop it in to the drive and do all the stuff, it says: "setup is inspecting your computers hardware." and it hangs there. forever. so, what do i do? i was told that ubuntu would fix it and i asked about windows but no reply, just yeah, ubuntu will fix grub and blah blah blah! but it seems no one on this freakin web site knows how to give a specific answer.Come on, if someone in Ubuntu forum know about WinXP, and help you out, great.  But it's unfair to complain if nobody can help; this is not a Windows support forum after all.

And about the grub question, I was about to help you, but then, you said you're going to wipe the harddisk, so I thought you don't need to recover grub anymore.

---

### Post by Sef on 2008-07-02
> ok, i have more problems.for some reason, windows vista is having an extremely hard time burning an xubuntu iso to a cd. im using infra recorder to do it, like you do on ubuntu, but it still wont work. i think its a problem with the recorder but i could be wrong. and second, i have this xp cd that when i pop it in to the drive and do all the stuff, it says: "setup is inspecting your computers hardware." and it hangs there. forever. so, what do i do? i was told that ubuntu would fix it and i asked about windows but no reply, just yeah, ubuntu will fix grub and blah blah blah! but it seems no one on this freakin web site knows how to give a specific answer.

Post your Windows question in the Windows Discussion Forum (under 'other os talk'.)

---

### Post by ripin1 on 2008-07-31
> Come on, if someone in Ubuntu forum know about WinXP, and help you out, great. But it's unfair to complain if nobody can help; this is not a Windows support forum after all.

meany. anyways, i didnt get around to that. any suggestions?

---

### Post by ripin1 on 2008-08-20
yay! fixed it! all i had to do was reinstall ubuntu.

---

### Post by pezmanlou on 2008-10-23
The XP installer will hang like you mentioned if a Linux partition on one of your drives is encrypted.  I had this problem myself.  If you use an Linux livecd and delete or reformat the partition (for this try gparted, it's easy), the XP installer starts fine.

---

