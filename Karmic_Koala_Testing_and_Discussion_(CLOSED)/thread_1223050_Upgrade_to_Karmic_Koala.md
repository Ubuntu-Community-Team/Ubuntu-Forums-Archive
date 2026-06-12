---
title: "Upgrade to Karmic Koala??"
date: 2009-07-25
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Chris_21 on 2009-07-25
I just installed Ubuntu jaunty via live CD, without any experience in Ubuntu Linux. I figured out I can upgrade to Karmic via upgrade-manager -d (run panel) Should I run the risk of coming into bugs in Alpha 3 or should I stay with jaunty??

---

### Post by mikewhatever on 2009-07-25
Karmic is still an alpha, you should not be using it.

---

### Post by Anzan on 2009-07-25
No, don't use it. I'm testing it but that's because I have lots of machines.

Wait until the RC and even then, not on something you need to work.

---

### Post by deadspider187 on 2009-07-25
> **Chris_21 said:**
> I just installed Ubuntu jaunty via live CD, without any experience in Ubuntu Linux. I figured out I can upgrade to Karmic via upgrade-manager -d (run panel) Should I run the risk of coming into bugs in Alpha 3 or should I stay with jaunty??

I wouldn't recommend anything but a final release to someone with no Linux experience.  Do you have any experience with other distros?  You will absolutely run into bugs in Alpha 3.  Do not use it unless you are comfortable with the innerworkings of a Linux system, and are not using on a machine you need to be reliable.

---

### Post by Arup on 2009-07-25
Stick to Jaunty, Karmic is in alpha stage and you will invariably run into issues.

---

### Post by Ericj1186 on 2009-07-27
Other than reiterating that Jaunty is your best bet, if you are interested in at least trying out Koala, go ahead and get Virtual Box.  With VB, you allocate a spot on you hard drive (make sure to give it enough for an actual installation), and VB will install a boxed version of the OS of your choice there.  It's a cool way to safely test things like Alpha versions or Windows 7 or anything like that.

Other than this option, I'd say wait until it's released.  Welcome to the boards.

---

### Post by xx58 on 2009-07-27
:rolleyes:I had Ubuntu 8.10 and everything was working like a charm. Then I made clean Installation to Ubuntu 9.04 and next 3 month I just have problem after problem, but on end everything was work just fine. I had Ext4 and I like it. So, Yesterday I had again some problems with Ubuntu 9.04 and I was thinking to try Ubuntu 9.10 (test) and I did. Everything just work out nicely. Everything work very well. SO, my advice is stay with Ubuntu 8.10, because that work without any problems or try Ubuntu 9.10, may be it will work out for you too.....

---

### Post by chakebubu on 2009-09-18
I currently use 9.04 on an offline computer. I want to download the ISO of Karmic and was wondering how I can upgrade using the cd?

---

### Post by psyke83 on 2009-09-18
> **chakebubu said:**
> I currently use 9.04 on an offline computer. I want to download the ISO of Karmic and was wondering how I can upgrade using the cd?

You cannot upgrade using the desktop CD (the CD doesn't contain the original .deb packages). You need to download the "alternate" CD which can be added as a repository source with "apt-cd" (I also think that a GUI prompt can do it automatically).

Be sure to read the descriptions here: [http://cdimage.ubuntu.com/releases/karmic/alpha-6/](http://cdimage.ubuntu.com/releases/karmic/alpha-6/)

---

### Post by Nickedynick on 2009-09-18
I think it's possible using the alternate disk. However, I wouldn't advise it in your case. There are loads of bugs (fairly obviously) in alphas, and unless you want to upgrade from CD every few days you'd need an internet connection to get fixed packages. Aside from this, you could end up reporting bugs that have already been sorted out.

Of course, go ahead if you're sure you want to - but be warned :)

---

### Post by slakkie on 2009-09-18
> **chakebubu said:**
> I currently use 9.04 on an offline computer. I want to download the ISO of Karmic and was wondering how I can upgrade using the cd?

Make a backup first though. Especially on an off-line PC.

---

### Post by chakebubu on 2009-09-18
Thanks for the reply. Just a by the way question. can I use apt-cd with the cds that I have requested from Ubuntu or do I have to download the alternate cd once Karmic is officially released?

---

### Post by psyke83 on 2009-09-18
> **chakebubu said:**
> Thanks for the reply. Just a by the way question. can I use apt-cd with the cds that I have requested from Ubuntu or do I have to download the alternate cd once Karmic is officially released?

I haven't used the ShipIt service in a while, so I'm not certain.

If they're only sending you the "desktop" CD, then you'll need to download the alternate CD yourself. If they're sending the DVD version, then I think you can use it to upgrade (as it contains the contents of both the desktop and alternate CDs).

---

### Post by chakebubu on 2009-09-18
Thanks for that Information and will take your advice and wait for the official release and download the alternate cd

---

