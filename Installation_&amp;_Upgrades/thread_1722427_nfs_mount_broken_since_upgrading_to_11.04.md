---
title: "nfs mount broken since upgrading to 11.04"
date: 2011-04-05
forum: Installation &amp; Upgrades
---

### Post by GB_Joe on 2011-04-05
Hello!

I've just upgraded to the 11.04 beta, everything working fine to start with (apart from not being able to find anything in the new interface!), but now, a few days later, the nfs mounts to my NAS are broken.

I've had a quick go at manually mounting; for instance, if I try to mount 192.168.1.1/Public to /home/Public (where it usually is) it says that the mount point doesn't exist. It's not true, I can see it, and if I test it by trying a mkdir it confirms it.

This is a pretty big deal, I've got ALL my stuff on the NAS. I can still see it from my phone and the web interface of the NAS, so I know it's there...

Any thoughts?!? Should I just re-install 10.10 and be patient until the final release comes out?

Cheers!
Joe.

---

### Post by Hedgehog1 on 2011-04-05
Just to be sure, did you create a directory in **/home** called **Public**  first?
 
That is needed before you do the mount command.
 
 
***The Hedge***
 
:KS

---

### Post by GB_Joe on 2011-04-06
Yeah - it's been there a couple of years now...!

I did check to make sure it hadn't done a runner, it's still there. I even tried to make it again with mkdir and it told me it was already there.

---

### Post by ~Plue on 2011-04-06
> **GB_Joe said:**
> 
I've had a quick go at manually mounting; for instance, if I try to  mount 192.168.1.1/Public to /home/Public (where it usually is) it says  that the mount point doesn't exist. It's not true, I can see it, and if I  test it by trying a mkdir it confirms it.

well, here's a couple of possible user errors;
1. case sensitive name
2. /home/*<username>*/Public

is it one of those?

---

### Post by areeda on 2011-04-06
I do have nfs working with 11.04, although I haven't been able to get live cd's to work for a couple of days.

Just to be sure you did install the package nfs-common?

sudo apt-get install nfs-common

Joe

---

### Post by GB_Joe on 2011-04-06
I should probably explain that I've got fstab modified to mount my nfs shares on boot; it's been up and running for a good while and it withstood the initial upgrade to 11.04 and first few reboots. I think this should pretty much discount any possible user error (which is good, because in my case it's pretty likely).

I've just tried installing nfs-common, but it's already there.

---

### Post by skralljt on 2011-06-29
My nfs shares stopped mounting too after upgrading to 11.04 and I suspect it may have to do with switching over to nfs version 4.  There are all sorts of new options and lines in new conf files to confuse.  I gave up and now just use scp or ftp.  SMB and NFS now too are such a pain to get working!

---

### Post by asteinmetz on 2011-10-02
I copied my fstab from 8.whatever LTS and it broke as GB-Joe experienced.  installing nfs-common fixed the problem for me.

---

