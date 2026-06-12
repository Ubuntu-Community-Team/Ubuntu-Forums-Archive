---
title: "Kubuntu Crashes on Shutdown/Restart/Logoff"
date: 2010-01-09
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by VMC on 2010-01-09
*Current(01/09/10) Kubuntu 10.04*:
On every Shutdown/Restart/Logoff I get a crash dialog. Apparently nothing useful is provided. What's the purpose of it to begain with?

I opened a bug report [#504375]("https://bugs.launchpad.net/ubuntu/+bug/504375"), and was ask to provide more detail:
```
can you reproduce the bug with **debug symbols** installed? the backtrace is
more or less useless like this. (except that one can see that the crash
is in the systray).
```

This is where it gets hairy and complicated:  

 First off,Why isn't "debug symbols" inserted into all testing distro in the first place. After all it is testing and would make life easier. It could then be removed on final release.

I found this [link]("https://wiki.ubuntu.com/DebuggingProgramCrash"), but have no idea what to search for or what or how to install the thing effectively.

Does anyone have experience with using "debug symbols" ?

Thanks.

---

### Post by Asraniel on 2010-01-09
i already replied on the bugreport, but simply install kdebase-workspace-dbg and you get the debug symbols for the plasma desktop (you can see in the crash that it crashes in the systray widget).

If you get this i can check in the kde bug reports if it matches any bug reported upstream

---

### Post by slakkie on 2010-01-09
I just wanted to create a thread for Kubuntu users, received this today on the kubuntu-devel maillinglist:

> 
Currently mesa in Lucid is broken and so no packages that build-depend on it 
can be built.  As a result, Lucid is currently a mix of 4.3.85 (Beta 2) and 
4.3.90 (RC 1) packages.  Getting mesa fixed will not be just a matter of a few 
minutes (hopefully today).

My recommendation is don't update any Lucid systems now.  It's unlikely we 
will see 4.4 RC1 fully built until at least Sunday and possibly Monday even on 
the fast architectures.

Scott K


Source: Message-Id: <201001091111.48796.ubuntu@kitterman.com>

---

### Post by VMC on 2010-01-09
> **Asraniel said:**
> i already replied on the bugreport, but simply install kdebase-workspace-dbg and you get the debug symbols for the plasma desktop (you can see in the crash that it crashes in the systray widget).

If you get this i can check in the kde bug reports if it matches any bug reported upstream

I just finished installing "kdebase-workspace-dbg_4%3a4.3.85-0ubuntu1_i386.deb". I saved that file in case I re-install kubuntu I don't have to download it again.

Ok, so now I just logoff, shutdown or restart and this will log some info? Where and how do I get it?

Edit: Ok a restart didn't reveal anything. I checked var/logs nothing there.

---

### Post by VMC on 2010-01-09
> **slakkie said:**
> I just wanted to create a thread for Kubuntu users, received this today on the kubuntu-devel maillinglist:



Source: Message-Id: <201001091111.48796.ubuntu@kitterman.com>

This has nothing to do with my problem since it started long before these updates. It started on day one of Kubuntu 10.04.

---

### Post by slakkie on 2010-01-09
Ok, then ignore my posting :)

---

### Post by VMC on 2010-01-09
> **slakkie said:**
> Ok, then ignore my posting :)

That's not to say that come Monday, if that's when it appears, the fully built 4.4 RC1 won't fix my errors.

 Regardless, I will re-install 01/14, when A1 comes along. Hopefully this will all be cleared up by then.

---

