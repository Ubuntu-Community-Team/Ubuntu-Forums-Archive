---
title: "CUPS username and password"
date: 2006-06-09
forum: Installation &amp; Upgrades
---

### Post by racsw on 2006-06-09
Hi,
   This is a new install, and the username for CUPS should be my Umbutu username and the password should be my system password, at least according to the docs to access
[http://localhost:631/admin](http://localhost:631/admin).
  Problem is, it doesn't work.  So what's the username and password for the CUPS system?
I have been using the Gnome printer GUI, but I prefer the CUPS system.

THanks,
Robert

---

### Post by linear on 2006-06-10
Since no one else has tackled this...

The cups web interface is disabled by default in Ubuntu. If you look on the main page ([http://localhost:631)](http://localhost:631)), there should be a message directing you to documentation that explains how to enable it.

---

### Post by racsw on 2006-06-11
OK, I found that part in README.Debian, but I also see now why CUPS won't see our HP LaserJet printer on our LAN, because that's also disabled by default, as it says here:

By default, cupsys is configured to only allow connections to
   printers from localhost, effectively disabling network printing.
   The previous default was to allow anyone to connect to printers
   from any location.  You can change these defaults by editing
   /etc/cups/cupsd.conf; the access controls are at the end of the
   file.  Be sure you only allow access from the locations you trust,
   or require authentication.

But I don't see any directive or procedure on how to enable my network printers in the cupsd.conf file.  All it says is "...the access controls are at the end of the file."
Can you help?

Thanks,
Robert

---

### Post by ipguru99 on 2006-06-11
It does say that, the part about network printing being disabled.. which makes me feel better ;-)

I am using 'server' and I have added all the 'Allow' statments, I have added the user cupsys to lpadmin and shadow (my user was already in lpadmin)... all of this stuff.. It still doesn't work.  Just to prove it to myself, I was finally able to add a printer (for Samba.. different story) while being on the server.  Then, I actually got a prompt to login and everything was fine.

I can get to [http://u-test:631](http://u-test:631) in a browser from my laptop.. I just can't do anything.  It doesn't ask me to login and I eventually get the '426 upgrade' thing... nice error message..

I have seen a BUNCH of posts on this, but I can't seem to find the answer?

Thanks!

---

### Post by racsw on 2006-06-11
I had the same response.  I added cupsys to my shadow file as instructed, and it still doesn't work.   Hopefully, somebody will figure this out, as I still can't print to my HP network printer, and I can't access the CUPS interface.

Robert

---

### Post by hajk on 2006-06-11
You should add yourself (as user) to group shadow. When logged in at [http://localhost:631](http://localhost:631) you could/should try to configure the printer as an HP JetDirect/AppSocket printer: you only need to give the IP of the printer, the port 9100 has been pre-assigned. Then accept the default driver.

An alternative:  first run (as user) in a terminal the command "hp-makeuri <printer-IP>", where you use the actual IP of the printer on your network. Write down the output, it will be something like hp:/net/<printer-make>?ip=<printer-IP>, where obviously the parts between <....> are specific to your situation. Note the single slash following hp:/.

Then configure the printer as an IPP printer, giving the URI just written down, and select the suggested driver. Now you make use of the HPLIP features, like being able to check ink levels on line. You can activate the HPLIP Toolbox in System -> Administration through Alacarte in the Applications -> Accessories menu. This is what I did myself with an HP DeskJet 5850 network printer.

Edit: I should add that you must "sudo /etc/init.d/restart cupsys" before the change to add the user to group shadow becomes active...

Edit-2: ip=...

---

### Post by garba on 2006-06-11
enable root:

sudo passwd root

and then use the root account login credentials to perform administrative tasks through the web interface, i know this is not very "orthodox" but it works

---

### Post by ipguru99 on 2006-06-12
Thanks.. but I am not even getting a prompt when I hit the page remotely.  Everything works great when I am at the server (explaining to the customer why it has to be done at the server is my real problem ;-)

When I am at my laptop, I can get to [http://server:631](http://server:631)  It doesn't prompt me and I can get almost all the way through adding a printer, but then it gives me the 426 upgrade screen.

When I am on the server, it immediately prompts me for the username and password.  Since I have added myself, I can use my username or root... works great.. just not remotely.

---

### Post by EndPerform on 2006-06-24
Here's how to get rid of that 426 page.  Put the following line in your cupsd.conf:

```
DefaultEncryption IfRequested
```

That will eliminate the 426 error and let you get on with printer configuration.  Note that this is not an encrypted connection, but I'm on a local secured network so I'm not too concerned about it.

---

### Post by ipguru99 on 2006-06-25
Wow!... Thanks!

That did it.  I just installed this at a customer today.  I was using ssh over X to do it from the server (in a browser).  We just tried to install a printer after making the 'DefaultEncryption' change, restarting CUPS.. and it worked!

Nice... wish this was better documented in the changes.  After seeing some people here complaining, it was obviously a problem.

Thanks again, EndPerform!

---

### Post by EndPerform on 2006-06-28
No problem :)  Ended up Googling for the solution.  Been working fine ever since.

---

