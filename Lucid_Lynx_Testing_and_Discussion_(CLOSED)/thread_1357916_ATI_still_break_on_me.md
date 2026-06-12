---
title: "ATI still break on me"
date: 2009-12-17
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by Vanishing on 2009-12-17
My old sony vaio laptop fried..
Got a lenovo thinkpad t500, with ati mobility radeon hd 3650..
Yay!
Time to get Linux on it..so I installed lucid daily build(17th, today), everything was working fine except for compiz, so I went to hardware drivers and enabled the ATI/AMD proprietary FGLRX graphics driver, reboot.. then I got the famous "low graphics" problem..and running on low graphics mode gives me blank screen instead of the actual "low graphics mode"...
I tried the ".run" file on ati site, does not work.

anyone have any solution to this problem? or temp work arround for it?

Thanks a million!

Happy holidays everyone!

---

### Post by n0glu3 on 2009-12-17
The only advice would be never use ATI with Linux. I gave up on those suckers ages ago.

---

### Post by Vanishing on 2009-12-17
> **n0glu3 said:**
> The only advice would be never use ATI with Linux. I gave up on those suckers ages ago.

I can't just throw the laptop out can i..lol

Still hope I can get it to work somehow..

---

### Post by xir_ on 2009-12-17
> **Vanishing said:**
> My old sony vaio laptop fried..
Got a lenovo thinkpad t500, with ati mobility radeon hd 3650..
Yay!
Time to get Linux on it..so I installed lucid daily build(17th, today), everything was working fine except for compiz, so I went to hardware drivers and enabled the ATI/AMD proprietary FGLRX graphics driver, reboot.. then I got the famous "low graphics" problem..and running on low graphics mode gives me blank screen instead of the actual "low graphics mode"...
I tried the ".run" file on ati site, does not work.

anyone have any solution to this problem? or temp work arround for it?

Thanks a million!

Happy holidays everyone!

Yea i have the same problem, luckly though the new opensource ati drivers (default drivers) are brilliant, the only thing they don't do well is power management, which will change in lucid +1.

I think that the ati driver hasn't been set up for lucid yet, maybe try on alpha 2 or stick with the opensource driver.

---

### Post by n0glu3 on 2009-12-17
> **Vanishing said:**
> I can't just throw the laptop out can i..lol

Still hope I can get it to work somehow..

You could at least try.... :P

---

### Post by xir_ on 2009-12-17
> **n0glu3 said:**
> The only advice would be never use ATI with Linux. I gave up on those suckers ages ago.

that's terrible advice, ati are doing an amazing job with their opensource drive. Nvidia will be playing heavy catch up by the end of next year.

Ati have given out the full spec of their cards to the community to foster open source drivers. Nvidia have said they have no interest in helping the community.

---

### Post by n0glu3 on 2009-12-17
> **xir_ said:**
> that's terrible advice, ati are doing an amazing job with their opensource drive. Nvidia will be playing heavy catch up by the end of next year.

Ati have given out the full spec of their cards to the community to foster open source drivers. Nvidia have said they have no interest in helping the community.

Hey the open source driver is great except for Xpress chips when KMS is enabled, I meant FGLRX sucks hard.

---

### Post by DougieFresh4U on 2009-12-17
You could try the [edgers-ppa]("https://launchpad.net/~xorg-edgers/+archive/ppa")
Worked great for my ATI Radeon HD3200

---

### Post by xir_ on 2009-12-17
> **n0glu3 said:**
> Hey the open source driver is great except for Xpress chips when KMS is enabled, I meant FGLRX sucks hard.


you should have said that then :P
i do have to agree nvidias blob is better, but i will only ever recommend AMD now they are properly supporting the community.


DougieFresh4U

I always try to avoid moving to far away from the stock repositories when testing, otherwise what is the point?


to op, just in case you are wondering i see a 8 watt penalty on my laptop using the opensource driver right now

---

### Post by Vanishing on 2009-12-17
> **DougieFresh4U said:**
> You could try the [edgers-ppa]("https://launchpad.net/~xorg-edgers/+archive/ppa")
Worked great for my ATI Radeon HD3200

Hmm..that is what i'm using right now..

Yes..I have to admit the open source driver is okay, but not THAT great..lol

Thank you

more advice please:)

---

### Post by zengeos on 2009-12-17
The ATI drivers work great on my laptop in karmic. I have had the same exact problem as described in the initial post, btw, on Lucid.  As someone else suggested, I think the proprietary driver just hasn't been setup for Lucid yet.

---

### Post by Vanishing on 2009-12-17
> **zengeos said:**
> The ATI drivers work great on my laptop in karmic. I have had the same exact problem as described in the initial post, btw, on Lucid.  As someone else suggested, I think the proprietary driver just hasn't been setup for Lucid yet.

Hmmm..
I'll just stick with metacity for now...
but compiz is not just an eye-candy, sometimes its features are very helpful..T.T

---

### Post by zika on 2009-12-18
> **Vanishing said:**
> Hmmm..
I'll just stick with metacity for now...
but compiz is not just an eye-candy, sometimes its features are very helpful..T.TJust a suggestion, try xorg-edgers PPA ... and stay away from fglrx ... (ATI user)

---

### Post by Seren on 2009-12-18
Don't use fglrx when you are on development branch, because the driver aligned to the kernel must be supplied by ATI and most of the time they supply the correct closed source driver a few months after the kernel has been released.

On the other hand, the open source driver is always updated on time.

---

### Post by Vanishing on 2009-12-18
> **zika said:**
> Just a suggestion, try xorg-edgers PPA ... and stay away from fglrx ... (ATI user)

Hmm, okay.
I'm really an ATI nub here, this is the first time i ever used an ATI card in ubuntu, used to be intel.

Ok, so how do i not use fglrx? what should i put in xorg.conf?

Thank you!

---

### Post by andrek on 2009-12-18
I had the same situation after upgrading some xorg and xserver packages, which were shown as 'held'. Downgrading them to the karmic versions solved the issue.

---

### Post by Vanishing on 2009-12-18
> **andrek said:**
> I had the same situation after upgrading some xorg and xserver packages, which were shown as 'held'. Downgrading them to the karmic versions solved the issue.

Can you check the logs and tell me which packages?
thank you!

---

### Post by andrek on 2009-12-18
Oh I did it several days ago. I completely wiped out all the xorg-related packages, changed my repository list from lucid to karmic, apt-get update and then installed xorg and xserver-xorg. Reboot and after a successful boot-up I reverted sources.list back to lucid. From that time all the xorg packages are held back from being upgraded.

---

### Post by Pasdar on 2009-12-18
> **Vanishing said:**
> I can't just throw the laptop out can i..lol

Still hope I can get it to work somehow..

I have ATI 4570 on my vaio, works quite well with the new 9.12 drivers. Using Kubuntu 64bit, With the 9.10 drivers (on kubuntu 32bit) I had more trouble (the ones in the ubuntu repository are the 9.10 drivers).

Download the latest one from the ati website and install it... if that doesn't function well install the drivers with the program called "envy".

If none of these methods work, try the open source drivers, but dont enable desktop composition.

---

### Post by markbuntu on 2009-12-18
Currently, up to the 9.12 driver fglrx does not support xorg 7.5. it will sometime soon, maybe 10.1 or 10.2 next year. That is why it does not work yet with lucid.

---

### Post by Gina on 2009-12-18
> **n0glu3 said:**
> The only advice would be never use ATI with Linux. I gave up on those suckers ages ago.I'm afraid that is NOT helpful!  Most people have to put up with whatever graphics they find in their machines, particularly with laptops!

Anyway, it isn't true that ATI chips don't work with Linux.  In fact I have two ATI machines running Lucid.  My best one (self built with Linux and Ubuntu in mind) with nVidia is having great problems.

---

### Post by zika on 2009-12-18
I think we made it work ... I leave to OP to report. And mark this thread as "solved" ... No fglrx ...

---

### Post by Vanishing on 2009-12-18
> **zika said:**
> I think we made it work ... I leave to OP to report. And mark this thread as "solved" ... No fglrx ...

Yup, removed all fglrx related packages and cleared out xorg.conf, reboot, and everythings working now...
I even got compiz to work.yay

---

### Post by t.alex on 2009-12-18
> **xir_ said:**
> 
i do have to agree nvidias blob is better, but i will only ever recommend AMD now they are properly supporting the community.


same here :)

---

