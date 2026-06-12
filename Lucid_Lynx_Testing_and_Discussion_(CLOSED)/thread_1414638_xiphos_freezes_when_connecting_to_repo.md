---
title: "xiphos freezes when connecting to repo"
date: 2010-02-23
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by malachi1990 on 2010-02-23
Hi!

I'm thinking about filing a bug report with ubuntu for Bibletime and Xiphos, as on my machine, both will freeze whenever I attempt to connect to a repository. But before I do that, I want to make sure it's not something on my end that's causing the problem.

If you could, please let me know if you're experiencing a similar issue.

Thank you for your time.

---

### Post by k3lt01 on 2010-02-24
> **malachi1990 said:**
> But before I do that, I want to make sure it's not something on my end that's causing the problem.I'll be honest and tell you I haven't used either in a while so I'm not sure what the situation is.

Can I ask what are your system specs? What else is happening when you are using Xiphos etc? Why are you using them and connecting to repositories at the same time?

What I am trying to see is the possibility of you overloading your system and in doing so is that causing your problem.

---

### Post by malachi1990 on 2010-02-24
I have a 64bit AMD Turion processor, and 3 GB ram.

Everything runs normally when just reading text, or anything else for that matter.  But when I try to download any extra modules, Xiphos freezes, so that I have to force it to shutdown.

I'm not running Xiphos and Bibletime simultaneously, but both use the same backend to access online repositories (at least I'm pretty sure they do).

I don't think the problem is on my hardware, as this has only been happening for about a week.  It could be, though.

---

### Post by k3lt01 on 2010-02-24
How are you downloading he modules? are you using Synaptic or doing it natively through Xiphos and/or Bibletime?

---

### Post by Ibidem on 2010-02-24
Xiphos does not freeze up when downloading here.  libcurl3-gnutls is the common network backend; Xiphos but not Bibletime also uses libnspr.
On Xiphos I'm current.
It can't be that you have too much running for your system, as I have an Atom/1GB ram.
The network might be an issue, but I thought recent Xiphos versions were supposed to avoid the old "freeze main screen while managing packages" issue.
So I, for one, have no idea.

---

### Post by malachi1990 on 2010-02-25
@k3lt01:

I'm using Xiphos to install the extra modules.  But I have used Synaptic to install modules before.  Even on a fresh install, Xiphos freezes, so i have to use Synaptic (or manually download and install it).


@lbidem:

It may be a 64 bit issue, then.  I wish I knew.

---

### Post by k3lt01 on 2010-02-25
Malachi, I just did a fresh install of Karmic, just for the fun of it (pathetic I know). I shall try and see what happens when I reinstall Xiphos and load modules later today. It may be tomorrow morning my time before I can get back to you.

---

### Post by malachi1990 on 2010-02-26
That's fine, I recently did a clean install of lucid, so I know the fun that is.  

But as I'm on lucid, I don't know how much info that will give. 

Just enjoy your weekend.

Thanks again for your time.

---

### Post by k3lt01 on 2010-03-04
Sorry for taking so long to get back to you. As your last post reminded me you were on Lucid I had to wait till my Lucid was stable enough to actually work with. I got it fixed today so I just tried Xiphos and through Xiphos I installed a couple of Bible texts. It worked very well, even in Gnome-Shell which slows my little laptop down badly it connected, downloaded and displayed everything as it should.

I shall try a few more over the next few days and see if anything happens that shouldn't.

---

