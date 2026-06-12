---
title: "Hardy, very slow and runs really hot??"
date: 2008-05-20
forum: Installation &amp; Upgrades
---

### Post by Oliver Acevedo on 2008-05-20
First of all, thank you for taking your time to read this. These forums have been so great, even though I haven't posted that much I've read a lot and have been able to see the kind of talent we have in our Ubuntu community. Thanks for all your wisdom and advice that has helped myself and others in the past. 

I know that there have been quite a few people that have had a successful upgrade to Hardy but I've been experiencing some problems. Here are my specs:
Pentium 4 3.2 
30gb HD
1 GB RAM
HP Pavillion zd7000 (laptop)
64mb Video

Before I upgrade, my laptop was pretty much ok. It just ran hot when the screen saver would come on (probably due to my video card). When I went to upgrade it, the installation went smoothly up until the end when it went to install the bluetooth. I'm not sure if it's because my laptop isn't integrated with bluetooth or when but it just got stuck at that point. It didn't do anything so I was forced to shut it down after a few hours of it being stuck on the same spot. After that I booted it up and found it to be incredibly slow. Firefox 3 was barely even usable so I downgraded to Firefox 2 and that has helped a little. I've checked my system resources and the memory seems fine, the CPU Usage stays above 90 most of the time, even after I shut down processes that are high in usage such as the wineserver. One time i got it down to the 30's and 40's but the fan was still on at full blast. It sounds like it's at the highest speed and feels very hot. I know this may sound like the vents being clogged but it would just seem too much of a coincedence for it to be clogged again (I cleaned them not too long ago) and right after I upgraded. 

I've search google trying to find a way to reinstall this without have to burn the ISO, but I'm not even sure if reinstalling it would solve the problem. Has anyone ran into anything similar with Hardy? Any tips or advice as to what might be going on? Thanks, any comments are always appreciated.

---

### Post by joseardzm on 2008-05-21
i hava a similar issue in my inspiron 1420, i just have emesene, and firefox open, and while in the processes tab, they just consume less than 10%all together, in resources my cpu is way above 10% , like average of 20-25% on both cores, with peaks of 50%, when i m clearly not doing anything  extraordinary.  :S (i have less than a week with hardy and my first time i use ubuntu, this has happened since installation)

---

### Post by Rebelde on 2008-06-21
I am having the same problem. I found some improvement by doing the following:

   1. Open a new tab by typing Ctrl-t
      (That’s the Ctrl key on your keyboard and the letter t key at the same time)
   2. Enter about:config in the address bar of Firefox
   3. Enter ip into the Filter: text box
   4. Look for the network.dns.disableIPv6 entry in the table below the Filter: text box
   5. Double click the network.dns.disableIPv6 entry
   6. Restart Firefox

I found this tip in a [post]("http://techxplorer.com/2007/02/22/slow-browsing-using-firefox-on-ubuntu/") a year old so I suppose is not fully adequate for Firefox 3.0. I hope there is someone who could help to improve it more since when I tried Firefox in Vista (I have a dual boot) the speed using the same connection is far quicker than using Ubuntu which kind of disappoints me.

---

### Post by capleton on 2009-06-18
So, I know this is an old thread, but I did a google search for this same problem and this was one of the first threads that popped up, I thought I'd share my fix for it.

Flashblock.  

That's all it took, one simple extension for firefox.  Aparently flash uses a lot of resources in Ubuntu?  anyway, flahblock is a godsend; temperatures when firefox is running are back to normal.  Hope this helps someone.

---

