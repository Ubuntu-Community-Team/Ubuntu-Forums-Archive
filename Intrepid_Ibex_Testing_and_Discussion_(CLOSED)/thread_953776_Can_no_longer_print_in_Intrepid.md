---
title: "Can no longer print in Intrepid"
date: 2008-10-20
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by katanacb on 2008-10-20
Hi there,

I've been using Ibex for the last few weeks --- I must say I really like it and I'm looking forward to the final release in a few weeks.  There's just 1 thing though, and I figured that the problem I was having was just something that would be flushed out with an update eventually but I"m starting to think it may only be me.

Simply put, I'm not able to print to any printer, period, whether it's a shared printer by CUPS, it's a JetDirect printer, etc.  Everything's worked fine in every version of Ubuntu for the last few years, but Ibex refuses to print anything, period.

Right now, I'm trying to print to a printer on port 9100, but every time I try to print something I get an error message saying "Stopped - No%%Pages: comment in header!".  This printer is setup exactly the same as in all prior versions of Ubuntu; I even booted Hardy's liveCD and setup the printer in exactly the same way -- I was able to send a test page just fine.  Not in Ibex, so it's something specific to this release that I haven't figured out yet.

I'm using the same .ppd file as before.  Searching launchpad now but in the meantime thought I'd post here as well.  Oh, and I've tried setting thins up from the CUPS webGUI and the problem persists.

Any ideas?

---

### Post by katanacb on 2008-10-20
Ok, I've figured out something on this ... I can at least print now.

I turned on diagnostics, and CUPS spit out an error that somehow it could not resolve the hostname of my printer (strange, because I can ping it from the command line by hostname -- even short hostname).  I finally changed the "socket" line in the printer config from the hostname to the IP address of the printer and everything's working now.

Strange, this is different behavior in IBEX than in Hardy but at least I'm working now.  Any ideas why CUPS wouldn't be able to resolve a DNS name (while everything else on the system can)?

---

