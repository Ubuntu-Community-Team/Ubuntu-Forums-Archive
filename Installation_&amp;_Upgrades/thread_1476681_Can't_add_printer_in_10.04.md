---
title: "Can't add printer in 10.04"
date: 2010-05-08
forum: Installation &amp; Upgrades
---

### Post by PeregrinGo on 2010-05-08
Perhaps this is some minute detail, or maybe I'm just missing the obvious. But I can't add a printer in Ubuntu 10.04 -- not even when logged in as root.

And if I hit F1 to "resolve problems" (My interface is actually in Spanish.) I get the following message: > Cups Service Detained (Stopped) The CUPS print administrator seems to be detained. To correct this, select Sistem -» Administration-»Services from the main menu and look for the "cups" service. 

Of course, this is all in Spanish, so I'm not certain exactly how the message would read in English. At any rate, if I select System, Administration ... that's as far as I get, because I don't see "Services" anywhere.

Why did I upgrade again? With this and all its other bugs, I'm starting to wonder if Lucid Lynx was really ready to be rolled out.

---

### Post by P4man on 2010-05-08
I guess you could have a look in bootup-manager (its in the repo) to view your services. But you shouldnt have to.

---

### Post by AlexDudko on 2010-05-08
Are you trying to add a printer in browser ([http://localhost:631)?](http://localhost:631)?)

---

### Post by mehehool on 2010-05-08
I am also having the same or a similar issue ... I can get to the place where I should be able t add a printer but all optios are greyed out except add new group and even if I do that nothing changes

  I have an epson 8610 
   
I tried connecting wirelessly but still nothing 
  I also tried a network cable 
   I dont have any usb cables

---

### Post by scarhill on 2010-05-08
I fixed this by doing 

sudo service cups start

Then I was able to see the printer I have set up. I'm not sure why cupsd was not running. Also what happened to the Gnome Service Administration app?

---

### Post by grapedaddy on 2010-05-08
My printers disappeared and my add printer option was greyed out and it was because CUPS was not started.  Here is what I get when I try to start CUPS:

gd@auditor:~$ service cups start
 * Starting Common Unix Printing System: cupsd                                  cupsd: Child exited on signal 15!
                                                                         [ OK ]
                                                                       
gd@auditor:~$ cat /var/log/cups/error_log
E [08/May/2010:00:02:22 -0400] Unable to remove temporary file "/var/spool/cups/tmp/.hplip" - Is a directory
E [08/May/2010:00:12:25 -0400] Unable to remove temporary file "/var/spool/cups/tmp/.hplip" - Is a directory
E [08/May/2010:00:16:24 -0400] Unable to remove temporary file "/var/spool/cups/tmp/.hplip" - Is a directory
E [08/May/2010:00:20:28 -0400] Unable to remove temporary file "/var/spool/cups/tmp/.hplip" - Is a directory
gd@auditor:~$

---

### Post by grapedaddy on 2010-05-08
whoops!  . . .didn't type sudo
sudo service cups start     worked
but that doesn't explain why cups wasn't already started

---

### Post by reedk on 2010-05-09
See:
[https://bugs.launchpad.net/ubuntu/+source/upstart/+bug/554172](https://bugs.launchpad.net/ubuntu/+source/upstart/+bug/554172)

For some people, reinstalling cups* packages work, and you need to make sure /etc/network.interfaces contains:
auto lo
iface lo inet loopback

---

### Post by PeregrinGo on 2010-05-10
> **P4man said:**
> I guess you could have a look in bootup-manager (its in the repo) to view your services. But you shouldnt have to.


**I tried this, but cups appears to be activated in services. Nevertheless, it is not "on," and telling boot-up manager to start the service doesn't work. It does give me a message saying it's on, but the "light bulb" indicated that the service is in execution remains off, and printers are still unable to be added. Thanks for the suggestion, though.**

---

### Post by PeregrinGo on 2010-05-10
> **scarhill said:**
> I fixed this by doing 

sudo service cups start

Then I was able to see the printer I have set up. I'm not sure why cupsd was not running. Also what happened to the Gnome Service Administration app?

[B]This doesn't work for me either. I am given the following error message in response to that command (which I had tried previously after doing searches for potential solutions):

> Warning: Fake initctl called, doing nothing.


Again, thanks for the suggestion. But for now, the problem remains unsolved.
[/B]

---

### Post by PeregrinGo on 2010-05-10
> **reedk said:**
> See:
[https://bugs.launchpad.net/ubuntu/+source/upstart/+bug/554172](https://bugs.launchpad.net/ubuntu/+source/upstart/+bug/554172)

For some people, reinstalling cups* packages work, and you need to make sure /etc/network.interfaces contains:
auto lo
iface lo inet loopback

[B]I tried re-installing CUPS, but that failed to resolve this issue. I also examined my interfaces file in /etc/network/, and it contained the items you mentioned. Thanks for the suggestions

Problem status: unresolved.[/B]

---

### Post by P4man on 2010-05-10
Please refrain from bolding all your text. It wont get your problem solved any faster, its just more tiresome to read.

Have you looked at the bug report linked by reedk ? its a duplicate of this bug:
[https://bugs.launchpad.net/ubuntu/+source/ifupdown/+bug/497299](https://bugs.launchpad.net/ubuntu/+source/ifupdown/+bug/497299)

And probably your issue. Post the output of:
```
cat /etc/network/interfaces 
```

---

### Post by PeregrinGo on 2010-05-10
> **P4man said:**
> Please refrain from bolding all your text. It wont get your problem solved any faster, its just more tiresome to read.

Have you looked at the bug report linked by reedk ? its a duplicate of this bug:
[https://bugs.launchpad.net/ubuntu/+source/ifupdown/+bug/497299](https://bugs.launchpad.net/ubuntu/+source/ifupdown/+bug/497299)

And probably your issue. Post the output of:
```
cat /etc/network/interfaces 
```

Thank you for your response. I would encourage you to refrain from making assumptions about why people use text formatting features, as my purpose was to make what I had written more salient and, thus, distinguishable from that which preceded it.

---

### Post by whvw on 2010-05-10
Yes, I just tried Scarhill's suggestion, et voici! It works! But will it work when next the computer is turned on? Stay tuned for the next exciting episode!

---

### Post by P4man on 2010-05-11
starting cups manually is more a workaround then a solution. Try the other suggestions posted and linked to make it "stick" (ie reinstall cups and check etc/network/interfaces).

---

### Post by whvw on 2010-05-12
> **whvw said:**
> Yes, I just tried Scarhill's suggestion, et voici! It works! But will it work when next the computer is turned on? Stay tuned for the next exciting episode!
The plain and simple answer was...No. Also tried that "ipstart" thing, and that didn't work either. Now I'm using a Winders 98 drive. No printing is serious issue...is there any way to revert back to the 9.1 files?

---

### Post by bondo101 on 2010-05-12
Oh i can add the printer alright but it won't print,  its a network printer used the ip address of the printer , still won't print. email didn't work with evo and thunderbird. lucid is fast and easy . but too many bugs right now. I put in the karmic koalal 9.10 cd re did every thing,  prints no problem 
email with thunderbird no problem. I hope they fix all the problems with lucid its damn fast op sys. I still believe in it .:P

---

### Post by lonetree on 2010-05-14
I think the recent updates in 10.04 has caused the cups not starting automatically on boot. My printers were working fine until this morning after I did an updates and all my printers were not present after reboot. 

sudo service cups start solved the problem and after reboot, all printers are present. Printing is not a problem also.

regards

---

### Post by PeregrinGo on 2010-05-14
:) I decided to re-format and install the English variant of Ubuntu given that the problem was present in both installs in Spanish. This may mean that the bug (that is NOT solved but sudo service cups start -- or even the Spanish translation of it) is present in other language packs for which the described workaround is ineffective. What do you guys think?

Ah, and printing works just fine in the English version.

---

### Post by AlexDudko on 2010-05-15
CUPS functions, which add/configure printers receive there arguments in the way of a GET request. The parameters which are passed to cups are taken from the interface language, which may differ from English - the only language that CUPS functions understand. This can be easily seen in browser, where URL is formed in the way of a GET request and consists of parameters in the interface language.
This must be a bug in CUPS, which mustn't depend on a system language.
Unfortunately, I can't reproduce the bug since I have the only printer at the moment, which CUPS adds automatically. 
If someone can test CUPS behavior in [http://localhost:631](http://localhost:631) in several languages and the mentioned bug really exists, please, report it.

---

### Post by dan501 on 2010-05-21
I am experiencing the same problem randomly. CUPS fails to start for unknown reasons. Even after restarts of the machine,it does not start. Once I start the service from terminal, it works for a few days (restarts) and the stops again.
Dan

---

### Post by thecityofgold2006 on 2010-05-25
Ditto here. I was puzzled as to why my printer wasn't showing up.

No CUPS!

```
sudo service cups start
``` works temporarily.

---

### Post by Georgia boy on 2010-05-25
I got my printer to work by doing this sudo service cups start also. However, I notice that when I restart the PC I am missing the printer again and have to redo the sudo service cups start again. What gives? What's the permanent fix? Is there an update in the making for curing this problem that a lot of us seem to be having with the printers? 

Thanks 

Tom

---

### Post by fattyz on 2010-06-25
Since I had the same problem, "sudo service cups start" made my laptop find the hp photosmart connected to a windows 7 machine.  Have not re booted yet but it prints fine.

Also the network seems to be working which it never really did in 9.04.  It always said "couldn't mount location."  9.04 had no problem printing however.

FattyZ

---

### Post by gammonjosh on 2010-07-06
> **Georgia boy said:**
> I got my printer to work by doing this sudo service cups start also. However, I notice that when I restart the PC I am missing the printer again and have to redo the sudo service cups start again. What gives? What's the permanent fix? Is there an update in the making for curing this problem that a lot of us seem to be having with the printers? 

Thanks 

Tom

I had the same problem.  This is what I did and it seems to be working.

1.  Go to System>Administration>Synaptic Package Manager
2.  In the "Quick Search" bar type "Cups"
3.  Right click the package "Cups" (Common UNIX Printing System(tm) - server) and "Mark for reinstallation".
4.  Click "Apply" then reboot.

So far cups is starting for me on bootup.

---

