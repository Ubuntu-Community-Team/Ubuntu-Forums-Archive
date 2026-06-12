---
title: "No new packages"
date: 2010-08-02
forum: Installation &amp; Upgrades
---

### Post by Richardarkless on 2010-08-02
Hi I moved tmp, /var/tmp and /var/log to ram to increase battery life and performance for my netbook

I used the tutorial on webupd8 here, [http://www.webupd8.org/2010/07/improve-your-netbook-performance-and.html](http://www.webupd8.org/2010/07/improve-your-netbook-performance-and.html)

Anyway today I noticed that my desktop was getting many new packages each day while the netbook hasnt had any since I moved those folders into ram

Both have the same sources

Ive tried removing the mount points from fstab and removing the folders but still no new packages

Does anyone know how to fix this problem

---

### Post by snowpine on 2010-08-02
Hi there, please copy & paste the output of:

```
sudo apt-get update && sudo apt-get dist-upgrade
```

That will help us figure out what is actually going on here. :)

---

### Post by Richardarkless on 2010-08-02
> **snowpine said:**
> Hi there, please copy & paste the output of:

```
sudo apt-get update && sudo apt-get dist-upgrade
```

That will help us figure out what is actually going on here. :)

It goes through all my sources then this

Fetched 77.5kB in 44s (1,730B/s)
Reading package lists... Done
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
richard@ubuntu-netbook:~$

---

### Post by snowpine on 2010-08-02
Looks like your system is up to date, I see no problem here. If you feel you are missing out on updates, maybe you can try using a different mirror?

If you want me to take a look at your software sources, you can post the output of:

```
cat /etc/apt/sources.list
```

Also of course it goes without saying that what you are doing (moving your tmp and logs to a ram disk) is completely unsupported. I hope you trust this guy whose tutorial you followed. ;)

---

### Post by Richardarkless on 2010-08-02
> **snowpine said:**
> Looks like your system is up to date, I see no problem here. If you feel you are missing out on updates, maybe you can try using a different mirror?

If you want me to take a look at your software sources, you can post the output of:

```
cat /etc/apt/sources.list
```

Also of course it goes without saying that what you are doing (moving your tmp and logs to a ram disk) is completely unsupported. I hope you trust this guy whose tutorial you followed. ;)

I know its not the sources as its fine on my desktop however I just typed in sudo apt-get autoclean then refreshed in synaptic and -5 -No address associated with hostname keeps popping up

What does that mean?

---

### Post by snowpine on 2010-08-02
That explains why there are no new packages. :) Make sure you are connected to the internet, maybe try a different mirror as I suggested above, and post the content of your sources.list if you want me to take a look.

Unless you have more details for me I am tempted to say "mounting /var/log to ram was a bad idea; your package manager relies on files in that folder to function correctly" as my final analysis of the situation. ;)

---

### Post by Richardarkless on 2010-08-02
> **snowpine said:**
> That explains why there are no new packages. :) Make sure you are connected to the internet, maybe try a different mirror as I suggested above, and post the content of your sources.list if you want me to take a look.

Unless you have more details for me I am tempted to say "mounting /var/log to ram was a bad idea; your package manager relies on files in that folder to function correctly" as my final analysis of the situation. ;)

Im connected to the internet and tried other mirrors still nothing

Like I said its not the sources.list as I use the exact one between my computers and the others are fine

So what do you suggest I do, can I copy /var/log off a live cd then paste onto the netbook, will that work?

---

### Post by snowpine on 2010-08-02
Based on the level of detail you have provided, my analysis is: Don't mount important system files like /var/log to ram. Revert the fstab change and hope your system is recoverable.

---

### Post by Richardarkless on 2010-08-02
> **snowpine said:**
> Based on the level of detail you have provided, my analysis is: Don't mount important system files like /var/log to ram. Revert the fstab change and hope your system is recoverable.

I did remove the entries in fstab and still nothing

So I need to reinstall, good job I got home on a different partition then?

---

### Post by snowpine on 2010-08-02
Maybe the situation can be salvaged. :) Is the person who gave you this advice in the first place available to help you?

---

### Post by Richardarkless on 2010-08-02
> **snowpine said:**
> Maybe the situation can be salvaged. :) Is the person who gave you this advice in the first place available to help you?

Well the website which I got it off is webupd8 and all he did was link to the tutorial which is here [http://www.fewt.com/2010/07/move-your-logs-and-temp-files-to-ram.html](http://www.fewt.com/2010/07/move-your-logs-and-temp-files-to-ram.html)

I spoke to the one that linked to the tutorial and he said moving those 3 folders didnt cause the problem and maybe there werent any updates and he left it at that

---

### Post by Richardarkless on 2010-08-02
Sorry for the double post but a little update

I done a test by adding another source and I reloaded and it showed the upgrade for that source

so I took all of the sources out of the sources.list except the official sources, saved it, refreshed then edited it and pasted the sources back in

Now its detecting new packages, dunno why it was ignoring existing sources

Thanks snowpine for the help

I guess moving those folders was just a coincidence

---

### Post by Yarekku on 2010-08-03
I've got the same problem after [that]("http://www.webupd8.org/2010/07/improve-your-netbook-performance-and.html") changes:( Could you clarify how do you resolved this?

---

