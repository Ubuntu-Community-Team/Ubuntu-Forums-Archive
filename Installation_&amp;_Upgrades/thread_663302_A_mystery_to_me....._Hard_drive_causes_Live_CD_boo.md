---
title: "A mystery to me..... Hard drive causes Live CD boot failure"
date: 2008-01-10
forum: Installation &amp; Upgrades
---

### Post by Multi-Booter on 2008-01-10
OK, I'm bumfuzzled on this one...

I was going to do some experimenting on another system on an older linux drive.

I have a hard drive with Fedora Core 5 on it, and it has a lot of extra space on it. So I figured I'd boot my Kubuntu Live CD on the machine to see how it worked.... which is a known-good disk.

It would not boot... during the process it started throwing back an error due to the hard drive. But the hard drive is also known-good. Fedora Core 5 runs fine on it. 

I tried everything. The live CD works. But no matter what I do, it will not boot with that hard drive hooked up... but will with it unhooked.

Heck, I even moved the hard drive to another tower and tried it.
The live CD will NOT boot on a system with this drive in it.

This makes no sense to me at all. So much so that it actually has me intrigued. The only logical thing I have been able to come up with at all is that maybe it's some security setting in Fedora Core 5. If so, I'm dying to know what it is. But it doesn't really make complete sense, so I doubt it.

Is this not strange?
Or am I overlooking a totally no-brainer explaination?

---

### Post by chewearn on 2008-01-10
I suspect it is the swap partition.  When the livecd load, it try to use an existing harddisk swap partition.

Could it be something about your Fedora Core swap?  Or that, when trying to access the swap, it resulted in borked boot-up?

---

### Post by Multi-Booter on 2008-01-11
Hummm... I dunno....

---

### Post by Multi-Booter on 2008-01-14
I'm still stumped.

I'm going to try another distro's live cd and see what happens.
(when I get a chance)

---

### Post by Multi-Booter on 2008-01-17
OK... so I tried a Puppy 3.01 live-CD

Boots right up no problem at all.

:confused:

---

### Post by chewearn on 2008-01-18
> **Multi-Booter said:**
> OK... so I tried a Puppy 3.01 live-CD

Boots right up no problem at all.

:confused:

When you are in Puppy liveCD, did you check whether is is "borrowing" the swap on your harddisk?

---

### Post by Multi-Booter on 2008-01-18
No I sure didn't.....

---

### Post by Multi-Booter on 2008-01-21
> **AstalaVista said:**
> When you are in Puppy liveCD, did you check whether is is "borrowing" the swap on your harddisk?

I checked just to see today, and no it does not use the swap.

---

### Post by Multi-Booter on 2008-01-22
I blew the disk out.
Then tried again.

The Ubuntu LiveCD still will not boot with this drive connected.

I'm getting something different now though...
It acts like it is going to boot normally.
Then it hangs up and I get an ash shell... yes ash shell.

For a second there I also saw 'frozen' on one line...
And likewise I saw...
Something like.... buffer I/O error block 0 on sda... something to that effect anyways.

---

### Post by torgrot on 2008-01-23
Are they ide drives?  Do you have them hooked to the same port with a single cable?  Is it a cable select cable?  Did you try to set them to master and slave?  Doesn't work reliably.  If they are sata drives forget I said anything.  Could be one distribution attempts to use space on the hard drive and the other doesn't.  As long as only one is using the port it works as soon as the other is accessed it doesn't.

torgrot

---

