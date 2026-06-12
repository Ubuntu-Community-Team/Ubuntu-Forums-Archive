---
title: "Disk I/O light on all the time."
date: 2008-05-01
forum: Installation &amp; Upgrades
---

### Post by rwynns on 2008-05-01
I just upgraded to 8.04 last night and now my disk I/O light stays on all the time.  I can hear that it is accessing the drive doing reads and/or writes continously.  It is on all the time starting about the time the Login screen pops up.  Hardware is a Sony Vaio model PCG-FX250.

What is it doing and how do I stop it? (short of doing a shutdown)

---

### Post by CoeusTitan on 2008-05-01
Same thing here.

I upgraded to hardy ubuntu, and my drive just starts randomly getting accessed for 5 or 10 minutes at a time....making it very hard to browse the internet, or to use any programs.

Any suggestions anyone?

---

### Post by CoeusTitan on 2008-05-01
Oh, and I know it's not the indexing service, because I disabled and removed its entry from startup.

So....what besides indexing could cause my HDD to be read from at completely random and lengthy times like that?

---

### Post by rwynns on 2008-05-01
I just upgraded to 8.04 last night and now my disk I/O light stays on all the time. I can hear that it is accessing the drive doing reads and/or writes continously. It is on all the time starting about the time the Login screen pops up. Hardware is a Sony Vaio model PCG-FX250.

What is it doing and how do I stop it? (short of doing a shutdown)

---

### Post by Rallg on 2008-05-01
Not good. In most cases when something like that happens, the loader is searching for something that it expects to find on your hard drive, but it's not there.

You didn't say whether you could log in, with the disk I/O still going. I assume that you could not log in, and that the loader hung at the point where the orange bar shows load progress (rather than at the login screen, as you wrote)? If so, one possibility is that the UUID of your Ubuntu partition was changed during update, but that the Grub bootloader doesn't know it. That might happen if you re-formatted the partition (clean install from CD rather than update from command line), and you have a previous Grub in a place where the installer did not update it.

You can expose the UUID of your hard drive's partitions using the live CD (I forget the command code, but it's on this forum somewhere). You can also look at the installed Grub menu.lst. Do they match? If not, edit menu.lst. Also be sure that if you have more than one Grub, you are using the one you expect to be using.

---

### Post by rwynns on 2008-05-02
The laptop only has Ubuntu on it.  I am able to login but every thing that I load from the drive is very slow to load.  Most things seems to be operating normally just slow when programs are loaded.  I have looked in the logs and see no problems there. (at least nothing stands out to me)  it seems to be working normally up to just before the login screen opens, on my laptop there is a solid blue screen just before the orangie/brown login screen opens.  I believe that it stays lit at that point on.  It does flicker but never really goes off.

---

### Post by rwynns on 2008-05-02
And to answer your other question... I have been using 7.10 since I upgraded it from 6.??.... I have always upgraded from the synaptic package manager when a new release was available, never from an .iso.

---

### Post by rwynns on 2008-05-04
Found the problem... It has something to do with MythTV...I removed it and everything is back to normal...

---

### Post by rwynns on 2008-05-04
Found the problem... It has something to do with MythTV...I removed it and everything is back to normal...

---

### Post by p_quarles on 2008-05-04
Duplicate threads merged.

Glad you solved the problem. Please don't cross-post again.

---

### Post by julianmag on 2008-05-06
> **CoeusTitan said:**
> Same thing here.

I upgraded to hardy ubuntu, and my drive just starts randomly getting accessed for 5 or 10 minutes at a time....making it very hard to browse the internet, or to use any programs.

Any suggestions anyone?


I'm having this problem but I didn't have MythTV installed.

I'm on Ubuntu 8.04, just upgraded from Gibsy and running on a Toshiba Satellite. I've Compiz and Firefox 3 beta 5.

It's hard to browse Internet explorer, because the hard disk is continuosly reading something.

Any thought?

---

### Post by thoughtbox on 2008-08-27
This doesn't have anything to do with MythTV. I'm having disk "lock" issues if I start another process that requires a lot of disk I/O.

For example, if I bring a suspended VMware image back online and then e.g. load nessus (sudo /etc/init.d/nessusd start), any other process that requires disk I/O will hang, even a simple "sudo su -".

I have never experienced this before running 8.04, but I have not been running the 64 bit version of Ubuntu before either, so I don't know if this is a 8.04 issue or just a 64 bit issue.

If someone has an idea about what is going on, that would be great.

/tb

(I forgot to add: this is a Lenovo T61p with the Ubuntu build running from a SATA disk in the modular drive bay.)

---

