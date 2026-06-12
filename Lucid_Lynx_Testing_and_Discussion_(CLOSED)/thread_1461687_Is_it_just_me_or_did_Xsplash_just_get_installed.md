---
title: "Is it just me or did Xsplash just get installed?"
date: 2010-04-24
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by jrothwell97 on 2010-04-24
So running all updates earlier led to xsplash and the associated artwork being installed.

However, as far as I can tell, the artwork is left over from Karmic, and xsplash doesn't actually show up during login (unless this is a change they plan to make shortly.) Additionally, assuming this is deliberate and not some accident, it's a bit late to be making such alterations, a week before release... (not that I object to this particular one ;))

---

### Post by Owen.C93 on 2010-04-24
> **jrothwell97 said:**
> So running all updates earlier led to xsplash and the associated artwork being installed.

However, as far as I can tell, the artwork is left over from Karmic, and xsplash doesn't actually show up during login (unless this is a change they plan to make shortly.) Additionally, assuming this is deliberate and not some accident, it's a bit late to be making such alterations, a week before release... (not that I object to this particular one ;))
I expect it is just a failsafe for people who cant get plymouth to work.

---

### Post by screaminj3sus on 2010-04-24
Good, cause plymouth is *** ugly with fglrx.

---

### Post by ranch hand on 2010-04-24
I am not sure why we still have it but it has never been removed by any update.

I do know that it is not present in my B2 or RC clean installs and there was not update for it there.  Ii is in the repo.

Kind of weird but good.  I am having a progressively worse experience with plymouth.  Shut down, when it happens at all takes more than a minute.  Boot takes more than a minute.

There is a package to replace mountall that speeds up my boot considerably (from 1:10 to :40) but with it installed shut down just freezes and requires Alt+Sysreq+b to reboot.

I am going to do a minimal install with xsplash and he gnome desktop environment and see what that does.

My boots were faster on earlier versions of this kernel when we were using xsplash still.  

I do not care about the ugly part.  I want my box to boot.

---

### Post by jrothwell97 on 2010-04-24
Well, Plymouth is still working on this system (albeit in low-res mode, thank you binary blobs) but it strikes me as odd that Xsplash was installed, given that it doesn't seem to be being run at any point during the boot/login process.

I imagine that its purpose *would* be to provide a more graceful segué between the login screen and the desktop.

---

### Post by ranch hand on 2010-04-24
xsplash was not installed in any recent update.  It was on your system from before and never removed.

We started the test cycle using xsplash.  It was removed from the ISO sometime that I did not notice but I know it was not there for B2.

So, if your system predates B2 it probably would have xsplash and would, therefore, get updates.  If you remove it you will not get those updates.

---

### Post by VMC on 2010-04-24
From an installed RC:

```
$ aptitude show xsplash
Package: xsplash
**State: not installed**
Version: 0.8.5-0ubuntu2
Priority: optional

```

---

### Post by Starks on 2010-04-24
RC iso doesn't have xsplash because today's updates installed it.

---

### Post by ranch hand on 2010-04-24
> **Starks said:**
> RC iso doesn't have xsplash because today's updates installed it.
Hmm.  I must not have gotten that one.  It is not on my newest installs at all.  Just the old ones.

I got some updates for them.

I am messing with my partitions on my test drive right  now from my main drive.   I will have to run updates again when I can go back and see what I screwed up.

Got to be ready for the Mangy Moose.

---

### Post by tokyobadger on 2010-04-24
I've been using lucid since Beta1, upgrading from that install to now, staying vanilla as much as possible; I can also confirm that yesterday pulled in an upgrade to xsplash:
```
less /var/log/apt/history.log | grep -C 1 xsplash
Start-Date: 2010-04-25  00:10:04
Upgrade: xsplash (0.8.5-0ubuntu1, 0.8.5-0ubuntu2), ubuntu-xsplash-artwork (0.8.5-0ubuntu1, 0.8.5-0ubuntu2)
End-Date: 2010-04-25  00:10:11
```

---

### Post by VMC on 2010-04-24
xsplash changelog: [https://lists.ubuntu.com/archives/lucid-changes/2010-April/011075.html](https://lists.ubuntu.com/archives/lucid-changes/2010-April/011075.html)

---

### Post by fedexnman on 2010-04-24
lets keep our fingers crossed here, hoping the ubuntu devs ditch plymouth for xsplash of course !

---

### Post by jrothwell97 on 2010-04-25
> **fedexnman said:**
> lets keep our fingers crossed here, hoping the ubuntu devs ditch plymouth for xsplash of course !

Dream on. ;)

It's a probability, of course, that this is a mistake - since the new sound theme was rejected two weeks before release, it's odd that Xsplash ended up getting installed.

(Incidentally, if it *is* deliberate, again I'll reiterate my hypothesis that it'll work alongside Plymouth to display a splash between the login screen and the desktop.)

---

### Post by Owen.C93 on 2010-04-25
> **jrothwell97 said:**
> Dream on. ;)

It's a probability, of course, that this is a mistake - since the new sound theme was rejected two weeks before release, it's odd that Xsplash ended up getting installed.

(Incidentally, if it *is* deliberate, again I'll reiterate my hypothesis that it'll work alongside Plymouth to display a splash between the login screen and the desktop.)
What's wrong with the transition from login to desktop? Seems fine to me, but then plymouth works perfectly for me aswell.

---

### Post by NightwishFan on 2010-04-25
Got it here, did not reboot to test yet.

I do not think Xsplash is a boot splash like Plymouth.

---

### Post by tokyobadger on 2010-04-25
[url=http://en.wikipedia.org/wiki/XSplash]XSplash is a software project in the Ubuntu community that uses the X Window System to replace the scrolling-text screens that appear while booting a Linux-based computer with a graphical splash screen.
XSplash replaced usplash (which uses the Linux framebuffer) in Ubuntu 9.10 (Karmic Koala), bringing Ubuntu closer to its goal of a 10-second boot time by version 10.04 (Lucid Lynx). The improved boot performance over usplash and other boot systems is achieved by prioritizing startup processes related to the X server, and by using a single X server throughout the boot process[/url]

---

### Post by jrothwell97 on 2010-04-25
> **Owen.C93 said:**
> What's wrong with the transition from login to desktop? Seems fine to me, but then plymouth works perfectly for me aswell.
Well, in Karmic, the boot sequence was as such:

[list][*]If it had time to, Usplash would show up before X started. (This was likely, given the regression in Karmic's boot times.)
[*]Once X starts, Xsplash pops up while we wait for GDM to start.
[*]The login prompt appears, and the user logs in.
[*]Xsplash appears again whilst waiting for the desktop to load, and then fades straight through into the desktop.[/list]

In Lucid, Plymouth handles up to GDM starting - presumably (assuming it's not a mistake) Xsplash is there to transition from login to desktop, which, at present, is a plain cut on this system at least.

---

### Post by qamelian on 2010-04-25
> **jrothwell97 said:**
> Well, in Karmic, the boot sequence was as such:

[list][*]If it had time to, Usplash would show up before X started. (This was likely, given the regression in Karmic's boot times.)
[*]Once X starts, Xsplash pops up while we wait for GDM to start.
[*]The login prompt appears, and the user logs in.
[*]Xsplash appears again whilst waiting for the desktop to load, and then fades straight through into the desktop.[/list]

In Lucid, Plymouth handles up to GDM starting - presumably (assuming it's not a mistake) Xsplash is there to transition from login to desktop, which, at present, is a plain cut on this system at least.
On my laptop, it was a smooth fade, even without xsplash.

---

### Post by seeker5528 on 2010-04-26
> **tokyobadger said:**
> I've been using lucid since Beta1, upgrading from that install to now, staying vanilla as much as possible; I can also confirm that yesterday pulled in an upgrade to xsplash:
```
less /var/log/apt/history.log | grep -C 1 xsplash
Start-Date: 2010-04-25  00:10:04
Upgrade: xsplash (0.8.5-0ubuntu1, 0.8.5-0ubuntu2), ubuntu-xsplash-artwork (0.8.5-0ubuntu1, 0.8.5-0ubuntu2)
End-Date: 2010-04-25  00:10:11
```

That's indicating Xsplash was upgraded from 0.8.5-0ubuntu1 to 0.8.5-0ubuntu2, so it didn't 'just get installed'.

I thought Xsplash was already removed before beta1, but I never installed Xsplash to begin with, I stuck with Usplash until conflicts with Plymouth forced it out, but it looks like Plymouth didn't force out Xsplash in the same way.

Maybe this is what the OP is seeing too.

Later, Seeker

---

