---
title: "Software and Update Server Best Selection"
date: 2021-01-02
forum: Installation &amp; Upgrades
---

### Post by nikos-21 on 2021-01-02
I have recently moved over to Ubuntu 20.04.1 from Windows 10 and I'm just completing the configuration of everything and I was wondering what the best option would be for an update server.

By default, in the Software and Updates application, the **Download From: **field has "**Server for Cyprus**" and this makes sense because that's the country I am in.
However, when I select **Other** **--> Select Best Server **it returns different results each time. The first time was Belarus, now it's the Netherlands. It might also be worth mentioning that the protocol differs too. Belarus was **http** and now the Netherlands is **ftp**.

So, I was just wondering, should I leave it as it is which is "**Server for Cyprus**" or should I just select the best server it spits out?

Thanks.

---

### Post by SeijiSensei on 2021-01-02
They're all mirrors so there's really little to differentiate them. I often choose a repository based in a nearby university since universities have pretty large bandwidth.

---

### Post by TheFu on 2021-01-02
Some things aren't worth worrying about until there is a problem.

I've never worried about it. Actually don't know which mirrors have been selected.  I do know that when I download a new distro ISO file, I go to the CS server farm at a local university school. 

If you only have 1 or 2 Ubuntu systems, then I'd let the system pick.  

If you have 5+ systems, then you might want to look into a package proxy system like apt-cacher-ng.  I use it. Basically, it caches packages for any APT-based distro, assuming that APT has been configured to use that cache on each client. This means that the first system to pull a new version of the kernel is the only time it gets pulled over the internet. All the other systems installing it pull the kernel from the local cache at GigE speeds.

---

### Post by nikos-21 on 2021-01-03
Ok, so all servers get the updates at the same time or do some get them before others? 
This was the main reason I asked really, to make sure I'm on a server that won't get updates a week after everybody else. Might be a silly question but thought I'd ask.

---

### Post by Impavidus on 2021-01-03
They all get the updates at approximately the same time. There may be a few hours difference, but not days.

---

### Post by deadflowr on 2021-01-03
In general the select best server option just pings all the mirrors and selects the mirror with both the fastest ping and probably the fewest hops.
But while most of the time that can be the best mirror it is not always the case.
I remember one time someone posted about slow connection and it turned out the mirror it selected was across the ocean.
So take it with a grain of salt.
 
As far as how often mirrors are updated you can look at the mirror listing and check out when the last update was here:
[https://launchpad.net/ubuntu/+archivemirrors]("https://launchpad.net/ubuntu/+archivemirrors")
Note that you may want to click on a particular mirror to see the true status.
If the main page shows as out of date it might be only a single release archive, most likely the development version archives.

---

### Post by ActionParsnip on 2021-01-03
If you have a lot of systems you could setup a local apt mirror and point all of your systems to that. As stated above, the packages are updated and pushed out to all mirrors. They are hours apart, not days

---

### Post by TheFu on 2021-01-03
> **deadflowr said:**
> <snip>
I remember one time someone posted about slow connection and it turned out the mirror it selected was across the ocean.
<snip>


I hadn't considered that.  Since the OP in in Cyprus, wouldn't every mirror be over the ocean if it isn't on Cyprus?
U of Cyprus has a mirror.

---

### Post by nikos-21 on 2021-01-03
Great, thank you all for your time.

---

