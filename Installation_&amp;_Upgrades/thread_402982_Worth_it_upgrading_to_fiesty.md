---
title: "Worth it upgrading to fiesty?"
date: 2007-04-06
forum: Installation &amp; Upgrades
---

### Post by FrozenFOXX on 2007-04-06
Hello, I was wondering about the general consensus on the state of Fiesty right now.  I've never used a beta of a release before (we didn't exactly have that kinda thing in Gentoo) so I'm unfamiliar with the disadvantages other than having frequent updates.

Would upgrading to Fiesty now just mean that I'd have to upgrade things daily until it's "released" and otherwise is normal?  Is it not stable enough for daily use yet?  Are there any major changes in Fiesty (specifically Kubuntu Fiesty) over Edgy (what I'm running now)?  I hear most people seem to be liking Fiesty a lot more than Edgy.


If it matters I'm on 64-bit Kubuntu, Edgy Eft and due to an interesting crash am looking to do a fresh reinstall (and I'm thinking of trying out ReiserFS again, I always hear good things about it).


I'm not asking for anyone to bash anything, I just want to know if it's a viable option to upgrade now (for this system I'm okay with having a little less stability for more of the cutting edge.  My main server will not be upgrading until after release).  I'm going to be unavailable to do system upgrades when Fiesty is released so I thought perhaps it wouldn't be so bad to get it out of the way now.

---

### Post by tgm4883 on 2007-04-06
Sounds like your in the same boat as me.

I use Feisty on my desktop (64-bit), Laptop (32-bit), and my mythtv box (32-bit version on 64-bit hardware) (also have a fileserver, but that runs edgy).  I think that it is stable enough for daily use, but there are some issues to deal with.  

Some people are having problems with network manager, but nothing that can't be worked out.  There was also some trouble with jmicron controllers where feisty wouldn't boot with them, seems to be fixed (I have a jmicron controller, and it wouldn't boot with feisty.  It got fixed somewhere around the end of march.  I ended up doing a full reinstall of feisty with a daily build of 3-31-07).  I don't think the problem is totally fixed yet, (although I can boot now),  I have random lockups (not really random, it seems to happen when I transfer large amounts of data over samba), and that is only on this one computer, the other two work fine.  

The computer that I do have the few problems is my core 2 duo with a gigabyte ga965p-ds3 motherboard

---

### Post by wpshooter on 2007-04-06
How do you know if you have one of the jmicron contollers ?

On the very first system I ever built, it is using a MSI MS-6341 motherboard with bult-in SCSI Ultra-160 and I am using Seagate 15K rpm SCSI drive and this system exhibits (at least on some occassions) of not wanting to boot with the Feisty beta releases.  Does not exhibit this behavior on early versions of Ubuntu, i.e. Dapper & Edgy.

Thanks.

---

### Post by tgm4883 on 2007-04-06
That is a good question, and the answer is I don't know.  I only found out that mine is cause I googled it.  They call it a GIGABYTE SATAII controller although it is just a relabeled JMicron JMB363 chip.  I checked the MSI website and your IDE chip is made by VIA and your scsi is made by adaptec, so no jmicron that I can see. 

Just noticed your a different poster.  Where is it hanging in the boot?

---

### Post by Neobuntu on 2007-04-06
NO!!!!!!!!!!!!!!!

Not Feisty yet. Edgy doesn't even do things Dapper did.

Wait.

---

### Post by wpshooter on 2007-04-06
> **tgm4883 said:**
> That is a good question, and the answer is I don't know.  I only found out that mine is cause I googled it.  They call it a GIGABYTE SATAII controller although it is just a relabeled JMicron JMB363 chip.  I checked the MSI website and your IDE chip is made by VIA and your scsi is made by adaptec, so no jmicron that I can see. 

Just noticed your a different poster.  Where is it hanging in the boot?

I have had it give the error message related to the jmicron issue when I went to run the integrity check on the Ubuntu CD.

But then I would go back into the boot process again and try the integrity check again and it would proceed and come back with ZERO errors.  I then came back and proceeeded with the boot and then the hard drive install with no problems.  Go figure !!!

Thanks.

---

### Post by tgm4883 on 2007-04-06
> **Neobuntu said:**
> NO!!!!!!!!!!!!!!!

Not Feisty yet. Edgy doesn't even do things Dapper did.

Wait.

Explain.  Of course Dapper will be the most stable of the three (it is Long Term Support), and Feisty +1 will be LTS, but what does dapper do that feisty and edgy cannot do?

---

### Post by FrozenFOXX on 2007-04-06
I have to admit I'm rather curious myself.  What DOES Dapper do that Fiesty does not?

---

### Post by konungursvia on 2007-04-07
I'm still using dapper and loving it. When a distro and kernel are stable, and just dandy, and meet your needs, moving on is not upgrading. It's downgrading.

---

### Post by bulldog on 2007-04-07
I'm using Feisty from Herd4 and beside some minor things with X11,and some kernels who wouldn't boot properly,it runs fine after kernel 2.6.20-9-generic.

No crashes on my AMD X2 4600,32 bit version,with Beryl and Emerald and a nVidia graphics 6800Ultra.

I had the Edgy Beta,but I find the Feisty Beta much better,but that's maybe a personal thing.
I run it on daily base and it isn't been broken, so I think it's stable enough.

---

### Post by Neobuntu on 2007-04-07
> **tgm4883 said:**
> Explain.  Of course Dapper will be the most stable of the three (it is Long Term Support), and Feisty +1 will be LTS, but what does dapper do that feisty and edgy cannot do?

The things still broken in Edgy and Feisty.

I wish it wasn't so but Dapper is the place to be unless you are testing.

I hate that Edgy is called "Released" or whatever. It would be better to have called it an interim testing release or something like that. 

I know, I know, "edgy is working fine for me" and it is stabilizing but using strict "just works" usability;  among the many different uses, a computer can do, naturally, Dapper has much more smoothing.

Then, you have back ports of the newer packages that are popularly requested. If you keep those to the few that YOU probably want, your stability will be better than hearing "Hey, it's called 'Edgy' and it's not an LTS" (which isn't friendly).

YMMV but self control is important when one can do anything they want. Understand?

I don't know how many times I have been exited by the new prospects and know that I can fix anything, only to wish I had WAITED!

My general rule is to test away BUT NOT on my main system where I recommend WAITING until after the next LTS has be already released a few months.

I think what we need is a testing install that would automate cloning what you have and testing with that. Plus, user feedback should be easy, clear, TIMESAVING and unified.

---

### Post by dannyboy79 on 2007-04-17
> **Neobuntu said:**
> The things still broken in Edgy and Feisty.

I wish it wasn't so but Dapper is the place to be unless you are testing.

I hate that Edgy is called "Released" or whatever. It would be better to have called it an interim testing release or something like that. 

I know, I know, "edgy is working fine for me" and it is stabilizing but using strict "just works" usability;  among the many different uses, a computer can do, naturally, Dapper has much more smoothing.

Then, you have back ports of the newer packages that are popularly requested. If you keep those to the few that YOU probably want, your stability will be better than hearing "Hey, it's called 'Edgy' and it's not an LTS" (which isn't friendly).

YMMV but self control is important when one can do anything they want. Understand?

I don't know how many times I have been exited by the new prospects and know that I can fix anything, only to wish I had WAITED!

My general rule is to test away BUT NOT on my main system where I recommend WAITING until after the next LTS has be already released a few months.

I think what we need is a testing install that would automate cloning what you have and testing with that. Plus, user feedback should be easy, clear, TIMESAVING and unified.


I was curious to find out what was "broken in edgy and fiesty" but worked in Dapper and he appears as though he is going to tell us by his first statement and then total disappointment. He doesn't tell us anything useful, just complains about nothing. This kind of ranting doesn't help the developers, the community or anyone for that matter. 

You don't want to upgrade your main system than don't, that's your poragative. If you'd like to help other users make an "informed" decision, than tell us what doesn't work. Otherwise you're just wating your breath.

---

### Post by Buzzygirl on 2007-04-18
I love Dapper, but I had problems running an Edgy Live CD on the same computer; therefore, I didn't upgrade. If I were having problems with Dapper, then I would probably opt for a clean install of Fiesty but, as it stands, everything about Dapper's working for me right now, so I probably won't make the move to Fiesty, at least not right away.

---

