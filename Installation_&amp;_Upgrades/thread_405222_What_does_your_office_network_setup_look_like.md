---
title: "What does your office network setup look like?"
date: 2007-04-09
forum: Installation &amp; Upgrades
---

### Post by tropicflite on 2007-04-09
Hi to all my ubuntu family.  I am in the unbelievable position of creating a 15 seat linux only network with essentially an unlimited budget.  I am coming from the world of rescuing the computers people leave at the ends of their driveways, so this is something very new to me.  My question is, what is your preferred network setup when cost is NOT a limiting factor?

Some of the options I'm considering:

Buying an enterprise level server and stuffing it with ram so I can run virtual machines (for apache, mail, mysql, apps (if necessary), etc.) 

Getting separate physical servers.

Getting fat-client desktop machines to for each of the users (keeping /home and ldap on a NAS or Openfiler machine)

Getting thin clients and using ltsp and freenx (makes my life easier).

What would you do if you were me?

TIA

---

### Post by rufius on 2007-04-09
Well a recent study showed that virtualization cut down efficiency of servers by around 40%. That said I've always been partial to separate physical servers. Virtualization is for development in my opinion, not production. Its a convenient tool for developing and saving money so you don't have to setup a server.

Now, that said, I'm a Sun guy. I like Sun's hardware and I feel it more than adequately does the job everytime. Though I don't claim to know Solaris well, I tend to use linux on the Sun hardware that I use. I like the Sun Ray thin clients and think they're great for offices to use if its pure Linux. Here's a link to the latest Sun Ray, I don't have them yet, but in my experience they're great: [http://www.sun.com/sunray/sunray270/index.xml](http://www.sun.com/sunray/sunray270/index.xml). The Sun Ray's use software released by Sun and this software is compatible with Linux.

For your servers, this is what I would setup for each situation:

**Web serving:**
Assuming a pretty heavy load, you're going to benefit a lot from a server like the [Sun T1000](http://www.sun.com/servers/coolthreads/t1000/). One of the big file servers (I think esat.net) tested it out as their server. Now I think they're absolutely nuts because they use one server to serve all their data, but they tested out the Sun T2000 (big brother to the T1000) and it performed quite well and sometimes out matching their current Xeon servers. I have one of these running our internal database/web server which gets high intranet traffic. Its not available to the public but it still gets  pretty good traffic. These, despite the fact they're UltraSPARC T1 processors, are supported by linux and in fact Ubuntu has a version that will work fine with them.

**Terminal serving:**
I would go for (depending on the number of clients) one or two of the Sun T1000's big brother, the [T2000](http://www.sun.com/servers/coolthreads/t2000/index.xml). This server is a bit beefier and will handle well having several clients connected. We've never maxed out our clients before, but we've got 8 Sun Ray clients now I believe hooked up to a T2000 and they've been running fine.

**Mail serving:**
Again, I would go with the Sun T1000, that is a second one dedicated to mail serving, it scales well with its 8 cores and 32 threads so it will run beautifully. 

**Database serving:**
Again, I would go with the Sun T1000, these servers are just plain awesome for what they can do and for the price. At 3500 a piece you can't really beat their performance in my opinion. 

**File serving:**
For this area, I'm gonna recommend a [Sun StorageTek 6140 Array](http://www.sun.com/storagetek/disk_systems/midrange/6140/). You can pack up to 56TB in it and it interfaces nicely with the other systems I've recommended thus far.

Now then all the above systems are certified to work with Linux. All of the T1000 and T2000 servers are very eco-friendly, so you'll save a lot of money compared to other setups for the performance you get. Ubuntu is a certified distribution for the Tx000 servers and I've run them on there and they work great. As far as networking goes, I don't deal with that much at my job, but we use Juniper Networks, not Cisco (like most companies) for our infrastructure. I know the network guys like it, but I pretty much stick to my computers :). Hope that helps.

---

### Post by tropicflite on 2007-04-09
Thanks for the recommendations.  The Sun gear looks great, though maybe overkill for just 15 users.  I'm leaning towards the thin client solution, and even though as I mentioned price isn't too big a factor, I woder if it's necessary to buy the Sun 20 seat license for almost $1800 when it seems LTSP can be had for free.  I have to admit, the Sunray's ability to resume sessions from any terminal by use of a card is a neat feature.

It's an adjustment making the move from commodity hardware to the 'real thing'!

---

### Post by rufius on 2007-04-10
Its really just having the integrated thin client that would be the point of going with Sun. Otherwise you'd have to buy/construct a bunch of different thin clients. I'm personally a lazy person and prefer to have all my hardware from one brand so that they theoretically "should" work together in harmony. 

If you're concerned about overkill, then I would get two Sun Fire T2000's and run Web & Database on one, and run the Terminal Server and Mail on the other. That way you're cutting costs and reducing hardware. I have nothing but praise for the Sun Cool Threads servers (T1000 & T2000). The datacenter I work in has saved a lot of money on electricity since we switched the majority of our racks to those servers. They run ubuntu great and the 4 threads per core makes the multiprocessing great. Like I said, nothing but praise!

---

