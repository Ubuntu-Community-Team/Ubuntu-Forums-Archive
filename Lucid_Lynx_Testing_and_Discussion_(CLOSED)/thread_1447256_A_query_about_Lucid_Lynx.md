---
title: "A query about Lucid Lynx"
date: 2010-04-05
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by Laxman_prodigy on 2010-04-05
Hi.

I just downloaded Lucid Lynx beta 1.

Now, since the official stable release is going to be on 29th April; now if I install it now, can I update/upgrade to the then-release?

I guess the system status will show now "Ubuntu betaLucid Lynx 1". Will it show "Ubuntu lucid lynx" then if I install it now?:lolflag:

---

### Post by manoriax on 2010-04-05
I suppose the answer is yes.

---

### Post by Paqman on 2010-04-05
> **Laxman_prodigy said:**
> if I install it now, can I update/upgrade to the then-release?


Yes.

However, i'd advise against running a beta version of Ubuntu if you're new to Linux. Lucid will still be getting as much as 100MB of updates to install every day, and any of them could cause unforseen problems. Unless you're confident with how to do things like manage packages from the command line, chroot, and troubleshoot problems then just stick to the stable release. Also bear in mind that any 3rd-party apps you have currently installed may not work under Lucid (yet).

---

### Post by Laxman_prodigy on 2010-04-05
> **Paqman said:**
> Yes.

However, i'd advise against running a beta version of Ubuntu if you're new to Linux. Lucid will still be getting as much as 100MB of updates to install every day, and any of them could cause unforseen problems. Unless you're confident with how to do things like manage packages from the command line, chroot, and troubleshoot problems then just stick to the stable release. Also bear in mind that any 3rd-party apps you have currently installed may not work under Lucid (yet).


Currently, I only listen to music, watch movies and surf web.

The only thing I need to do is get medibuntu repository and install those codecs and install official nvidia drivers.

Is there any problem with these in Lucid?

---

### Post by Laxman_prodigy on 2010-04-05
Anybody installed medibuntu codecs in Lucid and Nvidia official drivers?

---

### Post by overdrank on 2010-04-05
Moved to Lucid Lynx Testing and Discussion :)

---

### Post by manoriax on 2010-04-05
> **Laxman_prodigy said:**
> Anybody installed medibuntu codecs in Lucid and Nvidia official drivers?

What Medibuntu codecs exactly? The only thing I installed from there was the libdvdcss2, because some of my DVDs refuse to run without. And yes, I've installed the official nVidia drivers.

---

### Post by dino99 on 2010-04-05
> **Laxman_prodigy said:**
> Anybody installed medibuntu codecs in Lucid and Nvidia official drivers?

all goes well at time

---

### Post by howefield on 2010-04-05
> **Laxman_prodigy said:**
> The only thing I need to do is get medibuntu repository and install those codecs and install official nvidia drivers.

That might be all you need to do, but it isn't all that you need to run the operating system. You can still have issues not connected to the above.

As long as you can get back to where you currently are and your data is safely backed up, there is little to lose except some time.

To your original question, yes, using update manager will take you through to the final release. If you install the Beta and run the following command

```
lsb_release -a
```

You will get something like

Distributor ID:	Ubuntu
Description:	Ubuntu lucid (development branch)
Release:	10.04
Codename:	lucid

Running it after the full release should drop the (development branch).

---

### Post by Paqman on 2010-04-05
> **Laxman_prodigy said:**
> Currently, I only listen to music, watch movies and surf web.

You don't need Lucid for that, Karmic will work fine.

> 
Is there any problem with these in Lucid?

My point is that your whole system will be receiving updates daily. Hopefully this late in the cycle there won't be any major car crashes, but it's entirely possible that you'd get an upgrade that would stop your machine from booting, or drop you to the command line, or uninstall important parts of the system. If you're confident that you could deal with that, then go for it. Testing is a great way to give back to the project, but you need to be fairly familiar with how to handle (and report!) bugs effectively to be a good tester.

---

### Post by 23meg on 2010-04-05
> **Laxman_prodigy said:**
> Hi.

I just downloaded Lucid Lynx beta 1.

Now, since the official stable release is going to be on 29th April; now if I install it now, can I update/upgrade to the then-release?

I guess the system status will show now "Ubuntu betaLucid Lynx 1". Will it show "Ubuntu lucid lynx" then if I install it now?:lolflag:

Your question is answered in the sticky threads in this forum; please read them. 

Lucid is not recommended for any usage other than testing until the final release. There have been rare but serious problems as late as the Beta 1 stage, and it can happen again.

---

