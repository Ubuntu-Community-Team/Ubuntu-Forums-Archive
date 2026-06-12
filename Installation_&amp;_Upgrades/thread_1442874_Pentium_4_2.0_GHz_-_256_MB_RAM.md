---
title: "Pentium 4 2.0 GHz - 256 MB RAM"
date: 2010-03-30
forum: Installation &amp; Upgrades
---

### Post by MegaShark on 2010-03-30
Hi guys,

what version of Ubuntu (or k, x, null prefixes on Ubuntu...) would you recommend for this dated machine?

Pentium 4 2.0 GHz
256 MB RAM

Thanks in advance!

---

### Post by wojox on 2010-03-30
Does need to have a GUI? If not run [Minimal CD]("https://help.ubuntu.com/community/Installation/MinimalCD")

---

### Post by Vaphell on 2010-03-30
in theory xubuntu is the lean version, but the reality is that it not much lighter than ubuntu. Lubuntu (LXDE) should run like a champ on such hardware.

[https://wiki.ubuntu.com/Lubuntu](https://wiki.ubuntu.com/Lubuntu)

---

### Post by snowpine on 2010-03-30
Pentium 4 is a good workhorse. I'd recommend increasing your ram (your mobo should be able to take at least 1gb) and then you can run any of the 'Buntu family just fine.

If you're stuck with only 256mb for whatever reason, Lubuntu is probably your best choice, except that it is currently in beta and hasn't had a stable release yet. If you like living dangerously, go for it!

You can also install LXDE (Lubuntu's desktop environment) in 'Buntu 9.10 (the current stable release) with:

```
sudo apt-get install lxde
```

Log out, then from the login screen, choose LXDE from the Sessions menu.

---

### Post by Slim Odds on 2010-03-30
> **snowpine said:**
> Pentium 4 is a good workhorse. I'd recommend increasing your ram (your mobo should be able to take at least 1gb) and then you can run any of the 'Buntu family just fine.

If you're stuck with only 256mb for whatever reason, Lubuntu is probably your best choice, except that it is currently in beta and hasn't had a stable release yet. If you like living dangerously, go for it!
...

I completely agree. I have a P4 2.4GHz with 1.25GB of RAM and it runs Lucid quite well (as it did with Hardy, and Dapper).

RAM is cheap.

---

### Post by rhyz on 2010-03-30
Thats a good machine XD im Pentium 4 1.4ghz and 512mb ram

i ran ubuntu 9.04 fine on 1.4ghz 256ram tho it would slow down if i was running a few programs and update manager came up. Now i have another 256 ram giving me 512mb ram and everything seems fine and it doesn't matter what i have open.

I say go for normal ubuntu!!!!

---

### Post by tripolitan on 2010-03-30
Lubuntu is probably best for that system. 
I installed Karmik (Full) on P4 1.8 w/256 - was extremely slow for me (even with just Internet browsing) but my friend's kids loved it.

I recently upgraded his RAM to 512, it ran adequate for me but they thought it was great. I guess it depends on what you're doing with it.

---

### Post by diablozx9 on 2010-03-30
I recently replaced Ubuntu with Lubuntu on a 3 Ghz machine it is amazingly fast now.
I also loaded Lubuntu on an old 800 Mhz system and it runs quite fast.

A 2 Gig machine will sing with Lubuntu.
Give it a try.

---

### Post by vger7 on 2010-03-31
Actually, I'm testing this myself.

I have a dell with the same specs.
It currently runs Xubuntu with LXDE desktop.
But it still needs to use swap space.
Sometimes Firefox overwhelms it.
I've put my findings in a spreadsheet.

[IMG]http://i44.tinypic.com/fdd21l.jpg[/IMG]

Note: The lowest memory usage is highlighted in green.
The Light yellow is the low spec machines we have.

I also added a bunch of apts to Lubuntu to put in on par with most of the others.
This looks really good.

Note: Your mileage my vary.

I Hope this is useful.

[COLOR=Blue]Clarification and reasoning[/COLOR]:
I put this information together for myself and a young friend who is seeking to
get more performance from his laptop. (he is running Karmic)
I do not have a machine dedicated to testing on real hardware.

All VM's were configured identical.. disk space, memory, and graphic allowances.
All VM's were installed, updated, shutdown, (including VB), then restarted.
The VM's were shutdown and restarted a second time before recording the data.
All used Guest Addition to the best I could configure them.
Karmic was included because I already had it installed and it was a reference point.
Results show that LXDE presents a lighter load that Gnome. This is most evident in
the comparison of data between LUCID and LUBUNTU. They are both ubuntu 10.04
with different desktop environments.
All VM's used the grapics driver in Virtualbox, so that is somewhat an equalizer.
Boot time were not recorded/evaluted.

Is/was my method scientific? NO
Would your results be identical? NO
It is, however,  the best means I have available, and memory readings give me something to *quantify.*
It is: "*This is how this distro worked compared to that one on MY machine ONLY."*
It may not be 'apples to apples', but it it isn't 'apples to armadillos' either.

I apologize if I have given the wrong impression.

---

### Post by MegaShark on 2010-03-31
Thanks guys!

I guess I'll try Lubuntu then on this laptop...
... and stick with Ubuntu 9.10 on my 2.2 GHz (1GB RAM)...

---

### Post by tripolitan on 2010-03-31
I would not count such test as an indication of anything other than a comparison between systems with/without Compiz because the test conditions are not the same for all listed systems:

-Compiz seems to be the only common denominator.
-System behavior in Virtualization is not the same as native.
-Mixed installs (Virtualbox/native)
-Mixed Hardware.
All go into fairness in comparing as it would have been more fair if all systems ran under the same conditions, Compiz was turned off/ON on ALL systems and used the same Ubuntu releases on the very same hardware, using the default-unpatched release.

---

### Post by 98cwitr on 2010-03-31
buy more RAM, it's cheap :)

---

### Post by vger7 on 2010-04-01
> **tripolitan said:**
> I would not count such test as an indication of anything other than a comparison between systems with/without Compiz because the test conditions are not the same for all listed systems:

-Compiz seems to be the only common denominator.
-System behavior in Virtualization is not the same as native.
-Mixed installs (Virtualbox/native)
-Mixed Hardware.
All go into fairness in comparing as it would have been more fair if all systems ran under the same conditions, Compiz was turned off/ON on ALL systems and used the same Ubuntu releases on the very same hardware, using the default-unpatched release.

I added a Clarification at the end of my post.

---

### Post by MegaShark on 2010-04-05
> **tripolitan said:**
> I would not count such test as an indication of anything other than a comparison between systems with/without Compiz because the test conditions are not the same for all listed systems:

-Compiz seems to be the only common denominator.
-System behavior in Virtualization is not the same as native.
-Mixed installs (Virtualbox/native)
-Mixed Hardware.
All go into fairness in comparing as it would have been more fair if all systems ran under the same conditions, Compiz was turned off/ON on ALL systems and used the same Ubuntu releases on the very same hardware, using the default-unpatched release.

So, you're saying that all *buntu versions should be fairly similar in terms of performance if proper visual goodies are turned off?

Thanks.

---

### Post by tripolitan on 2010-04-05
No. I was talking about the test  itself, however, visual goodies are an impediment to any OS with limited resources. I personally consider Compiz as nothing more than eye candy, it serves absolutely no purpose for me + it hogs resources that could be well utilized in running day to day applications.

---

### Post by vger7 on 2010-04-06
Compiz adds about a 33M load to your ram. So unless *you really want* the eye candy just do without it and your machine will perform faster.

As far as desktop environments go, KDE uses the most resources, followed by Gnome, XFCE, and LXDE.

My Xubuntu/LXDE setup on the P4 with 256M ram loads up 102 processes and idles at 125Meg. The Lubuntu Beta, which I'll replace it with when it's final, loads up 111 processes but only uses 66Meg at idle! (see the image in my earlier post)
Mint/LXDE loads up 112 processes and idles at 106M. This I'm keeping on the Xeon. It may work well on the P4 also. The nice thing about Mint is that everything worked out of the box. I didn't have to look for codecs and stuff.
The only thing I needed to load was NTP.

Checkout this video:
This guys got all four desktop environments on his laptop and reviews them.

[http://www.youtube.com/watch?v=xSYxPYv5BTo&feature=fvsr](http://www.youtube.com/watch?v=xSYxPYv5BTo&feature=fvsr)

Also google LXDE.

---

