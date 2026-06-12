---
title: "A quitter never wins"
date: 2007-05-18
forum: Installation &amp; Upgrades
---

### Post by rondackcpu on 2007-05-18
A winner never quits, and a quitter never wins, but ...

After four weeks of trying to get Ndiswrapper to work on my modern laptop with Feisty, I give up.  Back to Edgy, and the whole world is simpler.  Suspend and Ndiswrapper are just the first of it.  Here are some details:

My modern laptop:  Dell 5160, 40 GB, 512MB, BroadCom wired ethernet, PCMCIA NetGear WG511v2 wireless.  With Feisty it had trouble with suspend from the beginning, and I was never able to get Ndiswrapper to work; it freezes, it has s..l..o..o..o..o..w responses at boot; Suspend was a gamble.  Stepping back to Edgy solved all those problems, but removed a lot of the upgrades that I liked.  My hope -- that some of the developers see this post, or that someone will pass this post along to one or more of the developers.  With Edgy and Ndiswrapper, the WG511v2 works better than it ever did with a Windows OS. More on that later. 

My modern desktop:  Dell E310, 80GB, 1GB, wired ethernet.  Feisty has trouble with Suspend:  sometimes cannot connect to the Internet after Resume from Suspend.  I'm about ready to go back to Edgy.

My oldster laptop:  Dell 5000e:  upgraded to 40GB, upgraded to 512MB, PCMCIA WG511(the Intersil Prism chip set).  Dual boot with Windows ME; ME, 10 GB; Feisty 30 GB.  Feisty has suspend troubles, usually resumes from suspend immediately -- without any signal from me.  About to go back to Edgy.

My antique desktop:  iMac Blueberry, 6 Gb, upgraded to 512 MB: I'm running pure Debian 4.0.  Ubuntu Edgy and Feisty turn off the CRT power supply at inappropriate times.  They do not do suspend, even though Ubuntu can turn off the CRT under other conditions.

My antique laptop:  NEC 'Green 735', Pentium II, upgraded to 8 GB, upgraded to 160 MB:  just overwhelmed by any Linux I've tried; running Windows ME, just fine.

More about the WG511v2:  The Dell 5000e came first and got a WG511v1.  It was nice.  The Dell 5160 came next and got the WG511v2.  It was annoyingly slow in connecting to the modem at boot and resume from suspend.  I blamed Windows XP.  Not so; when I tried the WG511v2 in the Dell 5000e with Windows ME, the annoyance went with the device and driver.  Under Edgy, the WG511v2 has no annoying delay at boot or resume.

---

### Post by bodycoach2 on 2007-05-19
On the iMac - only Dapper 6.06.1 has installed for me. I was able to successfully upgrade to Edgy thent to Feisty, but not without doing some xorg configuration. Still not sure how I did it right.

On the antique Laptop: Try Puppy Linux. I installed it on a Pentium 300 MHz. It works just fine. I'm about to try it on a Pentium 150 MHz laptop, but I've got to paint it red first

---

### Post by rondackcpu on 2007-05-20
Thanks, Coach, for the reply.

I tried Puppy on the antique laptop, but it would not recognize any of the PCMCIA internet cards that I have.  Not wanting to do the Ndiswrapper thing again, I gave up.  I don't use it much -- a few card games, TurboTax in the season.

The antique iMac seems to be marginally faster with Debian than any flavor of Ubuntu.  There is suppoed to be a "Ubuntu-lite", but I couldn't find enough parts of it to make a go of it.  If I could find a way to make Mac OS 9.1 work a three button mouse, I would go back to OS 9 as it is faster.  I did find a modern browser for it.

Thanks for your interest.

CRS

---

