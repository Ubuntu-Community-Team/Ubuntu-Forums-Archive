---
title: "[SOLVED] Installing / running LightScribe"
date: 2008-07-12
forum: Installation &amp; Upgrades
---

### Post by bilijoe on 2008-07-12
According to the Synaptic Package Manager, I have both the LightScribe System Software, and the LightScribe Applications packages installed, both from HP.  However, I cannot seem to find any way to configure the software or run any of the applications (primarily, SimpleLabeler).  I have found what looks like a shell script to configure the software (/usr/lib/lightscribe/elcu.sh), but nothing I do will get it to run--the system insists on treating it as if it were an installable package, or a Windows executable, rather than a shell script.  If I try to run it from a terminal window, even when logged in as ROOT, I get the message "bash: elcu.sh: command not found", although there it sits, plain as day, when I run "ls".  Maybe this is not where I should start, but it sure looks to me as if this is a configuration script that needs to be run before the system can find and access my LightScribe drive.  I've heard that LightScribe is notoriously hard to get up and running.  At this point, I believe it.  It's sure got me perplexed.:confused:  If anyone knows the secret, or can direct me to a good "how-to" I'd surely appreciate it.  I have a brand new LiteOn LightScribe-capable CD/DVD burner, which, unfortunately I bought as an OEM item, so no software came with it, but everything I've read seems to point to the software and application packages I downloaded from HP as the "official" solution to getting a LightScribe-equipped drive to do it's thing, i.e. to function.  I'd be extremely grateful to anyone who can help me out of this dilemma.  I've tried everything I can think of, and my brain is beginning to smoke.  Just to paint a complete picture, I don't know if it has anything to do with anything I did (I don't think I did anything particularly unusual) the "Places" item in my main menu (this is a 7.10 system) seems to have quit working.  If, for example, I click on "Computer", I get a tag in the bottom panel that says "Starting Computer", accompanied by the little whirly thing that shows the system is working, but after 5 seconds, or so, the tag  just disappears, without a window opening.  This is by far the strangest behavior I have ever encountered from Linux--the ONLY really strange behavior I have ever experienced, since I began using Ubuntu Linux, months ago.  I'm at my wits end.  I hope somebody has figured LightScribe out, and can lend me a hand.

---

### Post by em3raldxiii on 2008-07-12
I have an LG SATA lightscribe burner.  I had a similar issue trying to figure out how to burn with Lightscribe.

I eventually found a little program by Lacie that does the job nicely.  It's a pretty simple GUI with very few options, so what I do is create an image in The Gimp, then open it with the Lacie lightscribe burning app.

Unfortunately, I am at work, so I can't even look up the name of the program on my computer.  Perhaps using your favorite search engine (or even these forums) we could find the app.

EDIT:  Here are three links that will help.

[https://help.ubuntu.com/community/LightScribe](https://help.ubuntu.com/community/LightScribe)

[http://www.lacie.com/products/product.htm?pid=10803](http://www.lacie.com/products/product.htm?pid=10803)  <--- This one says the application is somehow compatable with K3B.  I am not sure what they mean because I have never noticed any "communication" between K3B and this app, but either way, it's good to see a company that actually knows a bit about Linux (the fact that they even know the name of an application is interesting).

[http://www.lightscribe.com/downloadSection/linux/index.aspx](http://www.lightscribe.com/downloadSection/linux/index.aspx)

---

