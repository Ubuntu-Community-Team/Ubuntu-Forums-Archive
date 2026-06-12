---
title: "[SOLVED] Incredibly slow update process..."
date: 2008-06-06
forum: Installation &amp; Upgrades
---

### Post by Kronie on 2008-06-06
Hey guys, i have one question here.. Whenever i am updating my hardy heron, downloading stuff from Add/Remove applcation or from synaptic, the download rate of updates could go as slow as 1k-2k B/s(bytes per second) out of my 320kB/s. most of the time its 5000B/s, and sometimes it can go up to my full speed, but that happens for about 10 seconds... it took me 2+ hours to update my fresh installed ubuntu(124 updates). so the question is, is that just me who's expireincing the problems or its just the server overload?

---

### Post by iaculallad on 2008-06-06
You could let Ubuntu choose the faster server for you: Navigate to System->Administration->Software Sources. Under "Ubuntu Software"->"Download From" select on the drop-down menu and select "Others", a window will open and click "Select Best Server". If you wish you could try clicking 3 times to get an accurate faster download site.

---

### Post by talktoari on 2008-06-06
This could be the server overload. I had updated my system with the updates and everything happened very quick. The system downloaded with full speed.

Since Ubuntu 8.04 is just now released, many people are downloading and using the same. So more people are actually downloading updates.

Meanwhile can u even compare other downloads in ubuntu with ur internet connection?

---

### Post by Kronie on 2008-06-06
thanx for advice :D that helped..for now..

---

### Post by Harald Franzen on 2009-04-21
I had the same problem and used this solution to solve it, so thank you for that.


However, I fail to understand the cause in my particular case. I have two servers, both running Hardy Heron. Both use(d) the same update server. For one of my servers, the update process was superfast (using all the bandwith I have available), for the other, it was massively slow, most of the time at bytes per second, with a maximum of around 32kB/sec for a few seconds here and there. 

Using the solution provided in the previous postings, I ended up updating from a server in Thailand -half the planet away. That runs at reasonable speed.

What I don't understand is that one of the servers updates fast from a source, where the other consistantly doesn't (or didn't). 

Any thoughts are welcome ;)

Anyway, thanks again for the tip: it worked for me !

---

