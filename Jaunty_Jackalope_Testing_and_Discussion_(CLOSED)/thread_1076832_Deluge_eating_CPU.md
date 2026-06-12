---
title: "Deluge eating CPU"
date: 2009-02-21
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by OliW on 2009-02-21
As of yesterday, deluge's favourite past time is eating my CPU. Averages 3-second long bursts every 20 seconds. But it's really variable. And annoying.

Anyone else noticing this?

---

### Post by mdurham on 2009-02-22
> **OliW said:**
> As of yesterday, deluge's favourite past time is eating my CPU. Averages 3-second long bursts every 20 seconds. But it's really variable. And annoying.

Anyone else noticing this?

Take a look with the System Monitor to see which process is hogging the CPU. If I turn System Sounds on, PulseAudio hoggs it.

---

### Post by OliW on 2009-02-22
When I said deluge was eating the CPU, I *meant* deluge was eating the CPU.

---

### Post by olskar on 2009-02-22
> **OliW said:**
> As of yesterday, deluge's favourite past time is eating my CPU. Averages 3-second long bursts every 20 seconds. But it's really variable. And annoying.

Anyone else noticing this?

Is this when downloading or all the time? If downloading, big or small files?

---

### Post by OliW on 2009-02-22
Downloading only (CPU usage drops right off when I pause).

The only thing downloading at the moment (and has been for a couple of weeks) is a monster torrent consisting of about 160x 350meg files.

I filed [a bug]("http://dev.deluge-torrent.org/ticket/814") in case the creators have any better ideas...

---

### Post by ronacc on 2009-02-22
what version are you running ? I have deluge 1.1.3 here and am uptodate , I'm not seeing anything more than 3% cpu from deluge with one coming down and one seeding . I am getting my cpu usage from TOP rather than system-monitor .

---

### Post by ronacc on 2009-02-22
update : when I made my last post deluge had only been running about 20 minutes , now after 2 hrs it has started to act as you describe with the exception that my bursts are longer 10>30 seconds every 2>5 minutes , also it seems to be deluged that is acting up .

EDIT: I added a comment to your bug , file one on LP also and I'll confirm it .

---

### Post by OliW on 2009-02-22
Yes, that was a mistake on my part. It's deluged that's running out of control here too.

---

### Post by ronacc on 2009-02-22
update , after the torrent I was d/ling finished I shut down deluge then restarted it and removed the torrent I was seeding and the one I had 
d/l'd  and then started a new torrent , without seeding ( although it is shareing the one I am d/ling ) I have had no instances of bursting in just over 2 hrs so far . It is past the time that bursting had started before I will add that comment to your bug if this torrent completes without any bursting , see my edit in my last post .

---

### Post by ronacc on 2009-02-22
ok that finished with no bursts , I let it go to seeding but still got no bursts with seeding only after 1 hr ,  so it may only occur with a combo of the 2 or it may have to do with torrent size , the one I just d/l'd was kind of small <300mb , its late tomorrow I'll try seeding a larger torrent and then if nothing adding a larger d/l .

---

### Post by ronacc on 2009-02-23
added another comment to your bug , it is definately related only to download size regarless of seeding or not . the lower limit for it to occur is somewhere between 255mb and 500mb .
file an ubuntu bug on LP or would you rather I go ahead and file one ?

---

### Post by nichomerri on 2009-02-25
Seems like it's related to LSD, or Local Service Discovery. Check your firewall logs when deluge starts acting up, and you'll see it's blocking multicast-related traffic. Then disable LSD in deluge, and voila!

If you can't live without LSD (no pun intended), maybe try configuring your firewall, or something. I'm too lazy to try myself.

Edit: Oops, I spoke too soon, deluge acted up again. I guess correlation does not imply causation after all.

---

