---
title: "Feisty Live CD setup nukes some DVI monitors"
date: 2007-04-20
forum: Installation &amp; Upgrades
---

### Post by guv on 2007-04-20
Hi guys

I installed a fresh Feisty last night and encountered a problem with my DVI monitor as a result, but fortunately eventually resolved it and thought I&#8217;d post the solution which worked for me in case it&#8217;ll work for anyone else having the same problem.

I booted and inserted the Feisty Live CD (386 version), chose the test/install option, and all was going fine but when the X server was due to appear&#8230;my 20&#8221; Viewsonic widescreen LCD monitor, which uses a DVI to DVI connection from my Ati 850XT, stopped receiving a signal.

I reset my PC but to my horror the monitor was still receiving no picture whatsoever, NOT even during the bios boot stage! This WASN&#8217;T a case of the ati/radeon/whatever driver not working, I wasn&#8217;t even getting a picture whatsoever before Grub kicks in!

I then plugged my monitor into my top-end laptop with an Nvidia 7950 running Vista. Usually Vista recognises the monitor and asks me if I&#8217;d like to use a dual screen setup (along with the laptop&#8217;s display), but no, Vista didn&#8217;t recognise the monitor was connected at all. So, Feisty has fried my expensive LCD monitor, I thought. Great.

Fortunately I had a spare VGA-DVI cable, so tried that. Putting the DVI connector into my PC and the VGA connector into my monitor worked. So, Feisty has somehow specifically fried the DVI connector of my monitor. Great.

I tried all manner of tricks to figure out the problem but nothing worked; I was left with the monitor&#8217;s VGA connection working, but not DVI.

A quick Google using my laptop revealed quite a few people suddenly losing their picture when using a DVI input, and not just specifically with this Viewsonic model (other models were mostly Dells.) A few solutions were proposed (sorry, didn&#8217;t think to bookmark the link), and the one which worked for me is as follows, and fortunately very easy and quick to try out:

1) Turn the PC and monitor off.
2) Remove power cables and the DVI cable from the back of both the monitor and PC.
3) Press the monitor&#8217;s &#8220;on&#8221; button (yes, without the monitor plugged in) to drain any residue power from the monitor. Repeat a few times if necessary to ensure no residue power is left.
4) Reconnect everything and boot up.
5) Voila, DVI works again!

I also have an older PC with a 7 series Nvidia card which uses a DVI connection to a Dell LCD monitor, and as a test I tried that with the Feisty Live CD. Sure enough, that nuked the DVI connection too, and again, the above process worked to get it back working again. Seems like something in the Feisty Live CD X server setup is making some DVI LCD monitors have a hissy fit.

Other solutions which worked for people in various forum threads I read involved booting with BOTH VGA-VGA and DVI-DVI cables connected to your PC and monitor, powering off, removing the VGA cables (leaving just the DVI connected), then booting up again. There is also a firmware update which worked for some people.

I hope I&#8217;ve provided enough info for the forum search to pick up if anyone else has the same problem. I&#8217;m now up and running with Feisty with no other problems. Apart from the DVI problem I had, initial impressions seem like it&#8217;s an excellent job by the Feisty team. :)

Cheers.

---

### Post by zotz on 2007-04-24
Hi,

Thanks for this thread.

I have this problem but the solution you give does not work for me.

If you could find the url of the page with the solutions you are talking above, this would be great :)

(i'm not the only one with this problem : [http://www.sapphiretech.com/en/forums/showthread.php?t=12659&page=1&pp=10](http://www.sapphiretech.com/en/forums/showthread.php?t=12659&page=1&pp=10) )

Thanks :)

---

### Post by ogiso_akpolokpolo on 2008-04-29
Thanks guv!!
I spent a whole day trying to figure out why I was getting no output on the dvi connection. I had installed Ubuntu 8.04 on my new PC using my older viewsonic lcd monitor connected via VGA. After setting everything up, I then set up my new Dell 2408WFP monitor, connected it to the PC using the DVI connector and nothing showed up, not even the BIOS screen info. when I switched to VGA using the DVI-to-VGA adapter provided by Dell, I was able to get normal output on the monitor. I spent a whole day trying to figure out what was wrong with no luck.
Initially your suggestion seemed a little far out but after a day of playing with nvidia driver settings etc I finally tried your solution and voila, problem solved!!
Thanks!!

---

