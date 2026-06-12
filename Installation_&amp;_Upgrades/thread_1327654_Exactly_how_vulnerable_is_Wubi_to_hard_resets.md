---
title: "Exactly how vulnerable is Wubi to hard resets?"
date: 2009-11-15
forum: Installation &amp; Upgrades
---

### Post by Fzang on 2009-11-15
I've been wanting to try Wubi for some time now, because I'm afraid that Windows 7 will break something together with a dedicated install of Ubuntu. Then, today I just found out that Wubi appears to be vulnerable to hard resets because of its nature.

My question is, how vulnerable is Wubi? I have a couple of times with Ubuntu experienced super glitchy behavior from applications like Compiz, where I would not hesitate to do a hard reset, and nothing bad ever happened. But will Wubi corrupt, go insane, break my Windows partition or some other amok behavior if I shut it down by holding the power button?

---

### Post by benj1 on 2009-11-15
> **Fzang said:**
> I've been wanting to try Wubi for some time now, because I'm afraid that Windows 7 will break something together with a dedicated install of Ubuntu. Then, today I just found out that Wubi appears to be vulnerable to hard resets because of its nature.

My question is, how vulnerable is Wubi? I have a couple of times with Ubuntu experienced super glitchy behavior from applications like Compiz, where I would not hesitate to do a hard reset, and nothing bad ever happened. But will Wubi corrupt, go insane, break my Windows partition or some other amok behavior if I shut it down by holding the power button?

ubuntu, wubi or not can be knackered by not shutting down properley, windows is the same, its best to view yourself as lucky if you don't have problems, rather than expecting it to go without problems.
the issue has nothing to do with wubi, its to do with writing changes to disk, if you half write something to disk you have problems.

---

### Post by Fzang on 2009-11-15
I've had many many hard resets in my life, without ever losing anything.

So let's say I'm browsing the web with Firefox. Completely random, my computer decides to freeze up. Would this hurt anyone? Or do you almost have to time the hard reset to hit a disk write?

---

### Post by benj1 on 2009-11-15
ive never had problems with a hard reset either, that doesn't mean they are risk free, and that risk has nothing to do with wubi.

---

### Post by wilee-nilee on 2009-11-15
If you install with wubi you are more in danger of losing both OS. A dual boot would allow you to access W7 from Ubuntu. I would go dual boot, I have W7 and Karmic with no problems. 

Personally I would dual boot and always be backed up off the computer so at the worst you can just reinstall both.

---

### Post by Fzang on 2009-11-15
I just don't have an external disk (nor can I afford one), so I thought it would be easier to go with Wubi, since it's "risk free".

---

### Post by wilee-nilee on 2009-11-15
> **Fzang said:**
> I just don't have an external disk (nor can I afford one), so I thought it would be easier to go with Wubi, since it's "risk free".

Risk free where did you get that information. A dual boot is much safer if you know what your doing. Like I suggested if the W7 goes down for the count you lose the Wubi to. ;)

---

### Post by benj1 on 2009-11-15
plus its vunerable to all the viruses that would affect windows

---

### Post by Fzang on 2009-11-16
1. I'm not afraid to lose Wubi as such. It would be a shame to lose it, but I'm only using Linux to freely customize my system the way I want it, not anything serious.

2. I'm more afraid that Wubi will drag Windows down, not the other way around.

3. I've never ever had a virus before, counting since Win98 >_>

---

### Post by benj1 on 2009-11-16
> **Fzang said:**
> 1. I'm not afraid to lose Wubi as such. It would be a shame to lose it, but I'm only using Linux to freely customize my system the way I want it, not anything serious.

2. I'm more afraid that Wubi will drag Windows down, not the other way around.


wubi is exactly as vulnerable to hard resets as any other program, if you are still worried, dual boot.

> 3. I've never ever had a virus before, counting since Win98 >_>
youve never had a virus, that you know of.

---

### Post by Fzang on 2009-11-16
I still have my money and I don't get calls from Nigeria. Yup, I'm safe. :D

---

### Post by Fzang on 2009-11-16
Double post.

How about I give Wubi its own partition? Yes, I know I could just install Ubuntu the normal way, but I'm not even thinking about doing actual partition messing unless I have a backup source.

So this will kind of minimize the chances of anything crashing? (by ~2-3%?)

---

### Post by Romanrp on 2009-11-16
I never had any problems with hard resets.
Except the time I did I hard reset while running a kubuntu live cd.
Windows did not boot again.

---

### Post by Fzang on 2009-11-16
That would be expectable I guess.

---

### Post by Joe Ker1086 on 2009-11-16
This is going back a couple posts but how would i access a windows partition from ubuntu if it is on a dual boot?

---

### Post by garvinrick4 on 2009-11-16
I have never had a problem with WUBI at all. Went through last 6 Alpha's, Beta and
RC of 9.10.  Useing Vista and WUBI and it has been very, very good to me. It is just
as fast as the Windows install, intel dual core. 2 gig of Ram. It uses about 600 meg of
Ram at maxed out. use 20 gig for Ubuntu with pictures and Music up to 10 gig in use.

Is a folder in Windows right next to Users in C:
In UBuntu it is /host and all your windows files can be copied to Ubuntu from
/host/users/login   and drag and drop.  Takes 12 minutes to install from disk. All have
wubi option on them now.  Download .iso of Ubuntu BURN to CD and then just put in
CD drive choose Wubi install, your size, your password and wait 12 minutes.
Here is link pick 32 bit or 64 bit. If 64 bit take it. You can use 32 bit Windows and 64 bit Ubuntu, works like a charm.  Have fun,  Linux stays in its WUBI folder and if it go's bad you can just uninstall it in Windows and reinstall.  Have fun with Linux it is great.

[http://releases.ubuntu.com/karmic/](http://releases.ubuntu.com/karmic/)

---

### Post by Mark Phelps on 2009-11-16
> **Joe Ker1086 said:**
> This is going back a couple posts but how would i access a windows partition from ubuntu if it is on a dual boot?

IF you're not using Wubi, that question is off-topic for this thread.  In that case, please start your own thread having to do with accessing Windows partitions from Ubuntu.

---

### Post by Fzang on 2009-11-16
> **garvinrick4 said:**
> I have never had a problem with WUBI at all. Went through last 6 Alpha's, Beta and
RC of 9.10.  Useing Vista and WUBI and it has been very, very good to me. It is just
as fast as the Windows install, intel dual core. 2 gig of Ram. It uses about 600 meg of
Ram at maxed out. use 20 gig for Ubuntu with pictures and Music up to 10 gig in use.

Is a folder in Windows right next to Users in C:
In UBuntu it is /host and all your windows files can be copied to Ubuntu from
/host/users/login   and drag and drop.  Takes 12 minutes to install from disk. All have
wubi option on them now.  Download .iso of Ubuntu BURN to CD and then just put in
CD drive choose Wubi install, your size, your password and wait 12 minutes.
Here is link pick 32 bit or 64 bit. If 64 bit take it. You can use 32 bit Windows and 64 bit Ubuntu, works like a charm.  Have fun,  Linux stays in its WUBI folder and if it go's bad you can just uninstall it in Windows and reinstall.  Have fun with Linux it is great.

[http://releases.ubuntu.com/karmic/](http://releases.ubuntu.com/karmic/)

I love posts like these. When everything seems dark and hopeless, out comes the knight in shining armor with his sword in his left hand and a live CD in his right.

---

### Post by garvinrick4 on 2009-11-16
What would life be like without the Live CD in your right hand.  Boring, boring boring.
Might as well buy a copy of XP a 30 gig drive with 250 meg of Ram and Norton Utilities.
Sit and check on your bank account 10 times a day. Go to the office and sit and see
how much someone else has to pay for their taxes.

 Anyway any body reading this about WUBI when you shutdown or reboot. Use 
"sudo shutdown -h now" for shutdown and "sudo shutdown -r now" for reboot.
Without quotes.

If you ever get in the position for system maintenance use "fsck"

If you ever just have to reboot for some reason.  I use   alt/sys rq/b  in that order.
You will read it is softer to do the /sys rq/REISUB I believe if you want to use that.

Never had a problem with former.

Every 20 reboots or so it doe's a system "fsck" on boot, not to worry.

Allways remember /host is your C: drive in Windows. You can copy what you want
with drag and drop to Ubuntu.  Ubuntu to Windows copy to external drive and drag
and drop to Windows.  

Do not need to install with CD drive as first boot. Just enter into CD drive and click WUBI install. Later versions all have WUBI as selection on .iso file you download and BURN to a disc.
                                 [http://releases.ubuntu.com/karmic/](http://releases.ubuntu.com/karmic/)

---

