---
title: "linux-ubuntu-modules-2.6.24-21-generic update not authenticated"
date: 2008-10-22
forum: Installation &amp; Upgrades
---

### Post by Denny Johnson on 2008-10-22
Update mgr showed the linux-ubuntu-modules-2.6.24-21-generic update.
When I clicked the buttons to apply, the summary said that the "software can't be authenticated"
First time I've seen the warning, want to update w/o creating problems.
Advice?
Thanks

---

### Post by Denny Johnson on 2008-10-22
here's a screenshot

---

### Post by steveneddy on 2008-10-22
Most of us are avoiding the -21 kernel for a while.

It has been known to cause some issues.

---

### Post by Denny Johnson on 2008-10-23
Thanks for the reply.
I've been running the -21 kernel since it came out as an update, if there were any problems, I've fixed them. 
..............mmmmmmmmmmm.........as I'm looking for some detail, I see that the current update I'm concerned about, "linux-ubuntu-modules-2.6.24-21-generic", is only an "other update" as opposed to the 20 other "recommended updates" that were also just now in the Update Mgr.
The description for the update in question is:
"This package contains modules supplied by Ubuntu for Linux kernel 2.6.24 on x86/x86_64.
You likely do not want to install this package directly. Instead, install the linux-generic meta-package, which will ensure that upgrades work correctly, and that supporting packages are also installed." 
Looks like it updates the current installed version 2.6.24-21.32 to 2.6.24-21.32Dell1
thought perhaps I would install the "linux-generic meta-package" as suggested in the description, but a search for it in Synaptic does not turn up anything that I can recognize as a linux-generic meta-package

---

### Post by floborg on 2008-11-04
I have the same update pending.  I'm running 8.04 on a Dell-buntu Inspiron 530.

In the update manager, the Changes tab of the details area always reads

[INDENT]The list of changes is not available yet.  Please try again later.[/INDENT]

The weird thing is that I've since accepted newer updates to this package and, yet, it still appears in the update manager.  I don't feel like installing something with no description and no authentication.

---

### Post by David Jenkins on 2008-11-05
I too have the same problem - 4 upgrades 'not authenticated'.

(same kernel, AMD-64 version).

As above - I have no intention of loading them until I know they're kosher.

David

---

### Post by floborg on 2008-11-05
Okay, so I disabled the "dell-team" hardy sources on the Third-Party Software tab of the Software Sources dialog.  The kernel update went away.  Re-enabling those sources causes it to return.  Clearly, an issue with this particular Dell-provided package.  It would still be good to know how to resolve this anyway in case other packages from the official sources do the same thing.

---

### Post by David Jenkins on 2008-11-06
Today the problem packages installed/upgraded without complaint...

...maybe someone's read this thread! :)

Thanks, whoever you are...

---

### Post by floborg on 2008-11-06
> **David Jenkins said:**
> Today the problem packages installed/upgraded without complaint...

...maybe someone's read this thread! :)

Thanks, whoever you are...

Hey, me too!  Speak up whomever fixed that package.

It would still be nice to know if there is a way to resolve this sort of thing on our own.

---

### Post by allan.w.macdonald on 2008-11-18
Hey, folks.

I am having the same problem.  An update has been showing up in my update manager for quite a while now, and I have also been encountering the dire sounding warning when I click on "Install Updates".

Now, I haven't actually installed it.  When other new updates arrive, I have always been unchecking this particular update and installing all the others.  As a consequence, whenever I start up my machine, I get an annoying new updates notification balloon.

I read a previous post to this thread suggesting that this update has been fixed... It sure hasn't been made so for me.  I have noticed, though, that the update has completely disappeared on occasion, only to re-appear later with the same warnings and missing information.

My question is this: I do NOT want to install anything that will damage my system.  Will anybody out there who actually knows what the problem is be able to respond to this thread?  Will this update ever get authenticated like its supposed to?

Allan

---

### Post by magicfab on 2008-11-18
This is a known problem.

Currently Dell updates come from a PPA repository in Launchpad which by design can't be signed:
[https://bugs.launchpad.net/soyuz/+bug/125103](https://bugs.launchpad.net/soyuz/+bug/125103)

This is being worked on, meanwhile you can safely ignore the warning.

---

### Post by Denny Johnson on 2008-11-19
Thanks magicfab.
I updated the questionable update noted in the original post.
That was a few hours ago, no apparent problems, will post back if I do see any.

---

### Post by floborg on 2008-12-05
> **magicfab said:**
> This is a known problem.

Currently Dell updates come from a PPA repository in Launchpad which by design can't be signed:
[https://bugs.launchpad.net/soyuz/+bug/125103](https://bugs.launchpad.net/soyuz/+bug/125103)

This is being worked on, meanwhile you can safely ignore the warning.

Is the update going to be put in the Hardy repositories?

---

### Post by juniper on 2009-03-21
I also got this error.  Magicfab says that we can ignore the error about the packages not being signed, but what about the warning that we should install the linux-generic-meta-package instead.

---

### Post by Denny Johnson on 2009-03-21
mmmmm...........that was back in Nov for me,............ IIRC.........I just proceeded w install w/o worry and there have been no problems.

---

### Post by floborg on 2009-03-25
Well, I don't know about the rest of you, but a while ago something changed and I started getting an error that the key was not available.  It was the Dell team key, which I acquired, and I haven't seen the Not Authenticated warning since.  I still have issues with the list of changes not showing up for kernel updates, but that's about it.  When the list isn't available for other types of updates, I just wait and, presto, they download some time later.

---

### Post by iaswni on 2009-04-06
Hey guys,
I installed sexy ubuntu again last night and its beautiful. Im having though the same problem with this file.
What I cant understand is, my processor is 32bit and I have the impression that this one is for 64..If it is so should it even be in my updates?? :confused::confused::confused::confused:](*,)](*,)](*,)
Should I just remove the dell-team from the sources?

Thanks a lot for your help 
Iason

---

