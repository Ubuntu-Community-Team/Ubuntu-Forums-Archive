---
title: "IE installation on Ubuntu 10.2"
date: 2011-12-13
forum: Installation &amp; Upgrades
---

### Post by processware on 2011-12-13
Is it possible to install IE on Ubuntu 10.2 ?
If so, could you please tell me how ?

Thanks for your help

---

### Post by thatguruguy on 2011-12-13
There is no Ubuntu 10.2.

Although you could try to install IE using Wine, people have had poor luck with that. If you have a copy of Windows sitting around, you can install Windows in a virtual machine (using VirtualBox or VMWare), and then use IE from there.

Is there a reason you need IE, specifically?

EDIT: You may also want to read [this article]("http://www.webupd8.org/2011/09/test-websites-in-internet-explorer-9-8.html").  It explains how to set up a virtual instance of IE in Linux.

---

### Post by processware on 2011-12-13
We have an application which runs only on IE. One of our customers have installed Ubuntu 10.02 on their desktops. Hence, we need to know whether we can install Internet Explorer on Ubuntu 10.02

---

### Post by thatguruguy on 2011-12-13
There is no Ubuntu 10.2, or 10.02.

There is an Ubuntu 10.04, Ubuntu 10.10, Ubuntu 11.04, and Ubuntu 11.10. There are also earlier versions of Ubuntu, which are no longer supported on the desktop.

The link I provided for setting up virtual instances of IE should work for any of the above, I think.

---

### Post by shumifan50 on 2011-12-13
I would strongly advise having a look at your application design to ensure that it at least also runs on Firefox - unless it is a REALLY bad design this should not be to difficult.
The popularity of Linux and Firefox is quite sharply on the increase (I for one do not use IE, even under Windows XP).

---

### Post by thatguruguy on 2011-12-13
> **shumifan50 said:**
> I would strongly advise having a look at your application design to ensure that it at least also runs on Firefox - unless it is a REALLY bad design this should not be to difficult.


This, although I was trying to be too nice to point it out.

---

### Post by Mark Phelps on 2011-12-13
Basically, you don't "install" IE in Ubuntu because it's not a Linux app.

You can run SOME versions of IE with Wine -- but they are the older versions.  

I believe that Wine, or its companion Winetricks, comes with older version of IE already configured.  But, from what I've seen, you can not install IE9 and get it to run with Wine.

The page below is the WineHQ page for IE:  

[http://appdb.winehq.org/objectManager.php?sClass=application&iId=25]("http://appdb.winehq.org/objectManager.php?sClass=application&iId=25")

---

### Post by infamous-online on 2011-12-13
Not being rude here, IE is the LAST browser I would design for because they don't follow the current standards that other browsers do so if I were you, I'd rewrite the site from scratch to where it's compliant with all browsers. I learned the hard way and had to redo my entire website's code, but I will say this it was the best thing that I've ever could of done. :guitar:

---

### Post by Mark Phelps on 2011-12-14
> **infamous-online said:**
> Not being rude here ...

Actually, you ARE -- being rude, that is.

The OP mentioned that they have an app that only works in IE.  They never said anything about having the source, or being able to rewrite it.  All they're trying to do is get that app working in Linux -- so they asked about installing IE.

What they don't need is a lecture on the merits of writing apps using other browsers.

---

