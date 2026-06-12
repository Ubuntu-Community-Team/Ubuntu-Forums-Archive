---
title: "i3 Upgrade + Lucid Upgrade"
date: 2010-04-10
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by jcook793 on 2010-04-10
My Dad's computer finally bit the dust this week.  I've been patching this thing up for years, but a power surge took out his power supply *and* his motherboard so it's time to gut the case and start over.

Since my Dad basically uses Firefox and Thunderbird and not much else, the new Core i3 processor seems like an ideal fit for him.  A dual-core 3GHz CPU that includes a (not sucky) GPU for $100?  Perfect.

I've been reading up on support for the i3's integrated graphics and it seems like Lucid is the way to go.  Dad was running 9.10 before the computer died.

So I'm only going to have access to the computer for a couple of days.  How much of a nightmare is it going to be to try to upgrade the hardware and the OS at the same time?  I'm pretty sure Ubuntu does a hardware scan on every boot so hopefully that will take care of a lot of the driver issues.  I mainly just hope that 9.10 will show me at least some sort of screen so I can run "update-manager -d".  If all else fails I have some ancient video cards lying around that I could use but doing stuff like that always seems to end up with me shaving yaks.

Any advice you'd have is appreciated.  Bonus question: should I even consider complicating my life with a 64-bit upgrade at the same time?

---

### Post by bigsmitty64 on 2010-04-10
If its a new motherboard and the cpu is 64 bit then I would def go with 64 bit OS. No harder to deal with. Other than some folks having a bit of trouble getting flash to work. 
Remember **Lucid is still in the beta 2 testing stage**, and will be buggy.So depending on your dads computer knowledge, you may be better off sticking with a fresh 9.10 install.

---

### Post by uRock on 2010-04-10
> **jcook793 said:**
> My Dad's computer finally bit the dust this week.  I've been patching this thing up for years, but a power surge took out his power supply *and* his motherboard so it's time to gut the case and start over.

Since my Dad basically uses Firefox and Thunderbird and not much else, the new Core i3 processor seems like an ideal fit for him.  A dual-core 3GHz CPU that includes a (not sucky) GPU for $100?  Perfect.

I've been reading up on support for the i3's integrated graphics and it seems like Lucid is the way to go.  Dad was running 9.10 before the computer died.

So I'm only going to have access to the computer for a couple of days.  How much of a nightmare is it going to be to try to upgrade the hardware and the OS at the same time?  I'm pretty sure Ubuntu does a hardware scan on every boot so hopefully that will take care of a lot of the driver issues.  I mainly just hope that 9.10 will show me at least some sort of screen so I can run "update-manager -d".  If all else fails I have some ancient video cards lying around that I could use but doing stuff like that always seems to end up with me shaving yaks.

Any advice you'd have is appreciated.  Bonus question: should I even consider complicating my life with a 64-bit upgrade at the same time?

My most important advice is to not use ```
update-manager -d
``` I have not heard one success story of an upgrade yet. You should be able to boot the system. The kernel should recognize the hardware and boot right up, though maybe in safe graphics mode. If he has the three partition setup already, then doing a clean install of 10.04 should be easy. If he doesn't have the three partition setup, then you will have to back up his personal data.

By three partition setup I mean having a /, /home and a swap partition.

If any drivers are needed for the new hardware, then they should be listed in System> Administration> Hardware Drivers

If you have more questions, feel free to ask.:P

Cheers,
Ronnie

---

### Post by jcook793 on 2010-04-10
> **bigsmitty64 said:**
> Remember **Lucid is still in the beta 2 testing stage**, and will be buggy.So depending on your dads computer knowledge, you may be better off sticking with a fresh 9.10 install.Yeah that has me a bit concerned.  My Dad is like most guys in their 70's - he likes to surf eBay for car stuff and check his email a few times a day and that's about it.

I wish I could wait until the end of April when Lucid goes final but that's just not going to work out.  And I really want the 2.6.33 kernel in there for the improved i3 GPU support (but not enough to deviate from the kernels provided by the maintainers).

---

### Post by jcook793 on 2010-04-10
> **uRock said:**
> My most important advice is to not use ```
update-manager -d
``` I have not heard one success story of an upgrade yet.Hmmmm, OK.  That seemed to be the popular advice when searching via Google.  Thanks for the heads-up.

> **uRock said:**
> If he doesn't have the three partition setup, then you will have to back up his personal data.Yeah, I was lazy during the initial install and it's just a single partition.  I'll just dump /home to a thumb drive.

Thanks!

---

### Post by theozzlives on 2010-04-10
> **jcook793 said:**
> Yeah that has me a bit concerned.  My Dad is like most guys in their 70's - he likes to surf eBay for car stuff and check his email a few times a day and that's about it.

I wish I could wait until the end of April when Lucid goes final but that's just not going to work out.  And I really want the 2.6.33 kernel in there for the improved i3 GPU support (but not enough to deviate from the kernels provided by the maintainers).

Lucid has it's bugs, and it's frustrating. Lucid is more stable then Karmic was on it's release date. If you don't network then go for it.

---

### Post by jcook793 on 2010-04-10
> **theozzlives said:**
> If you don't network then go for it.I really just need to make a DHCP request to the router and have the network speed be faster than the internet speed (in Dad's case that is ~1Mb/s).  All via a wired network so there's no wifi necessary.

---

### Post by uRock on 2010-04-10
> **jcook793 said:**
> I really just need to make a DHCP request to the router and have the network speed be faster than the internet speed (in Dad's case that is ~1Mb/s).  All via a wired network so there's no wifi necessary.

My network with two Lucid machines completes file transfers at about 5MB/s. Not the best, but still decent.

---

### Post by jcook793 on 2010-04-10
> **uRock said:**
> My network with two Lucid machines completes file transfers at about 5MB/s. Not the best, but still decent.I have this *same* problem on my Karmic box at home! I have some magic combo of AMD CPU and LANParty motherboard that just won't let me transfer any faster than that.  So frustrating.

---

### Post by uRock on 2010-04-10
Especially when the NICs on both are rated for gigabit.

---

### Post by damien_d on 2010-04-11
> **uRock said:**
> My most important advice is to not use ```
update-manager -d
``` I have not heard one success story of an upgrade yet. 

Good advice (Lucid Beta 2): I just broke a test box with upgrade-manager -d.  Clean install from CD was OK.

  -- Damien

---

