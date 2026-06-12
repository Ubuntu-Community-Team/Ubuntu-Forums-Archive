---
title: "Slow netbook with 11.10"
date: 2011-10-21
forum: Installation &amp; Upgrades
---

### Post by smssms on 2011-10-21
I don't expect to get much help as I am just too annoyed to give enough detail of the problemS or trawl the resources at the moment but:

I just upgraded to 11.10 and my Toshiba NB250 is hardly coping at all. It has gone sssllloooow, each click takes a second or two to happen, windows stutter open and shut, programs take seconds to open. I had it all FAST, nice and minimalist with 11.04. Despite getting the Gnome fallback desktop to make it look a bit better the performance has gone.

It also seems to have filled my (8GB) System file to the brim.

As you can tell, I'm new to Linux and annoyed! I had my netbook running really well on 11.04 and now it is just a pile of pants!

[rant over]

---

### Post by vajorie on 2011-10-21
> 
It also seems to have filled my (8GB) System file to the brim.


I wonder if the software cache is doing that. Try a 

```

sudo apt-get clean

```

and see if that empties your hdd a bit. I don't think that would have an effect on performance (unless it is literally full), but still... 

I also wonder if the symptoms you describe might be due to an overuse of memory... Though, it can actually be due to many other things, such as problems accessing the filesystem or even faulty drivers/modules in use or need to pass special options to the kernel or to specific modules and so on. 

In terms of memory, take a look at what this code gives you

```

free -m

```

Its output is a bit strange, so here's an example:

```

             total       used       free     shared    buffers     cached
Mem:          5844       2024       3820          0        185        734
-/+ buffers/cache:       1104       4740
Swap:         4766          0       4766

```

According to this, I have 5844MB ram. Of this, 1104MB is in use while 2024MB-1104MB is being used as cache. I seem to have 4766MB of swap available, none of which the system is using. Note that whenever my system starts using swap actively, I have serious performance issues (brief moments of system freezes, windows not responding or responding after a lag, etc).

---

### Post by smssms on 2011-10-22
Thank you Vajorie.

I tried apt-get clean, autoclean,  autoremove; deb orphan, looking for big Trash or temp files, removing residuals with Synaptic, etc. They made small improvements in the space used on / but not much. Strangely, just leaving the computer alone for a couple of hours took the System partition used down to 4.5GB, so now I have a couple of GB free - don't know why... (I have also calmed down a bit)

I assume 4.5GB is a normal sort of size for 11.10?

BUT, the computer performance is still SLOW as hell. The "free -m" output is as follows:

```
             total       used       free     shared    buffers     cached
Mem:           991        456        535          0         62        237
-/+ buffers/cache:        155        836
Swap:         1906          0       1906
```I have no idea if this is normal, good or bad.

My CPU load is at around 50%, with the cooling fans on, with just system monitor and (an idle window of) Firefox open. System Monitor show the only active Process as itself...

 seems

If anyone can help me get my netbook back up to speed now it is on 11.10 it would be much appreciated

---

### Post by mörgæs on 2011-10-22
Have you thought of Xubuntu?

---

### Post by goldshirt9 on 2011-10-22
fuduntu is designed for netbooks

---

### Post by smssms on 2011-10-22
I hear what you are saying and am on the train of thought myself.

I did try an xfce desktop environment a while ago and that REALLY did not agree with my computer i.e. was super super slow.

But, I am in the process of downloading Lubuntu to a USB to have a play with that... (first attempt did not work - some sort of gfxboot error????)

Not heard of Fuduntu but will have a look.

Thanks.

EDIT - Bye bye Ocelot, I'm now running Lubuntu.

---

### Post by vajorie on 2011-10-22
> **smssms said:**
> 
EDIT - Bye bye Ocelot, I'm now running Lubuntu.

(~4GB is normal for Ubuntu, yes; mine's using around 5.5GB) The memory usage looked fine; not even half of your available ram was being used, even with the cache. Is Lubuntu treating you better?

---

### Post by smssms on 2011-10-22
> **vajorie said:**
>  Is Lubuntu treating you better?

Still just exploring, trying to get it populated and set up how I like it. 

But, on initial impressions, it seems to be my kind of distro (fairly minimalist but usable); and best of all it seems to work!

It's annoying that Natty worked so well on my netbook (even better than Lubuntu so far) but the upgrade to Ocelot just killed it and forced me to look for a new distro.

---

### Post by smssms on 2011-11-08
I'm still not at all happy!

My computer was great on Natty, fast, responsive and just worked well.

11.10 just totally ground it to a halt so I changed to Lubuntu

Lubuntu worked but was still noticeably slower than Ubuntu Natty

Now I'm on Debian 6 x64 - guess what - still loads slower than Natty was. Mouse clicks and internet page loads take ages, CPU fan on a lot.! (Boot and shutdown have always been ok on all of them)

**QUESTION** - Are there any major problems with reverting back to (what I assume is the now unsupported) Ubuntu Natty and sticking with it?

Can anyone recommend any other supported distro they KNOW works well on a Toshiba NB250-108 netbook?
[B]

EDIT[/B]: Couple of hours later. Just to keep the story going, I'm trying Puppy Linux on a live UBS at the minute - BRILLIANT! By far the best yet from what I've seen so far. May well end up installing this as the main OS.

---

### Post by angryfirelord on 2011-12-17
> **smssms said:**
> I'm still not at all happy!

My computer was great on Natty, fast, responsive and just worked well.

11.10 just totally ground it to a halt so I changed to Lubuntu

Lubuntu worked but was still noticeably slower than Ubuntu Natty

Now I'm on Debian 6 x64 - guess what - still loads slower than Natty was. Mouse clicks and internet page loads take ages, CPU fan on a lot.! (Boot and shutdown have always been ok on all of them)

**QUESTION** - Are there any major problems with reverting back to (what I assume is the now unsupported) Ubuntu Natty and sticking with it?

Can anyone recommend any other supported distro they KNOW works well on a Toshiba NB250-108 netbook?
[B]

EDIT[/B]: Couple of hours later. Just to keep the story going, I'm trying Puppy Linux on a live UBS at the minute - BRILLIANT! By far the best yet from what I've seen so far. May well end up installing this as the main OS.
It may be KMS. It was introduced in 2.6.33, so Squeeze, which has 2.6.32, wouldn't have it.

---

### Post by buruntu on 2012-03-06
Hi smssms,

I used to love ubuntu till I updated to 11.04, which was pretty slow on my netbook. (an MSI wind replica, with 2 gb of ram and around 20-25 gbs of file system dedicated for ubuntu).

Just downloaded and updated to 11.10, it is unbelievably sloooooooow. 

You're not alone my friend, you're not alone...

---

### Post by smssms on 2012-03-06
I'm still going strong with Debian and Puppy Linux.
Debian is not lightning fast on my netbook but it seems very stable.
Puppy is fast and cool!

---

### Post by kmanpilkers on 2012-03-20
Anyone have any reason for this yet? I just installed Ubuntu on my HP Mini 110. With no extra software installed a free -m from the command prompt tells me I am using 910MB of the total available 990MB of RAM!!!

No wonder it's a bit slow.. this is with me logged in under the Unity 2D desktop. Noticed it's a bit snappier under Unity 2D but nothing like usable really.

I'm pretty disappointed. Previously I'd used Ubuntu prior to unity and had a great experience.

Like others I think I will try Xubuntu or Lubuntu.. but the thing is I actually really like the idea of the unity interface, it's good if you can get it to respond!

---

### Post by BertN45 on 2012-03-20
> **kmanpilkers said:**
> Anyone have any reason for this yet? I just installed Ubuntu on my HP Mini 110. With no extra software installed a free -m from the command prompt tells me I am using 910MB of the total available 990MB of RAM!!!

No wonder it's a bit slow.. this is with me logged in under the Unity 2D desktop. Noticed it's a bit snappier under Unity 2D but nothing like usable really.

I'm pretty disappointed. Previously I'd used Ubuntu prior to unity and had a great experience.

Like others I think I will try Xubuntu or Lubuntu.. but the thing is I actually really like the idea of the unity interface, it's good if you can get it to respond!

This memory occupation is completely normal, since I expect that half of that memory is used by cache and IO buffers. That is the normal behavior of any Linux system, it will use almost all free memory for disk and page cache. For Ubuntu 1GB of memory is on the limit, since it needs around 400-500MB for the OS. Others like the 10.04 use only half that size for the OS.

However if you develop the habit of closing the applications and browser tabs, you do not need anymore in the next couple of minutes, the system will be more responsive again. 1GB will work fine in this way.

---

### Post by kmanpilkers on 2012-03-21
Thanks for the response. OK then, is there anything we can do about it, or like other users would you recommend a different version of Ubuntu like Xubuntu or Lubuntu for users with 1GB of RAM in a netbook?

---

### Post by sheds on 2012-03-22
My machine has almost 2 GBs of available memory, and I am currently running Chrome with a couple of open tabs. Believe me, it's not your hardware, it's unity or perhaps the innards of ubuntu oneiric **[COLOR="Red"]slowcelot[/COLOR]**. I've been trying to find if it's possible to make it simpler, with no special effects but I haven't found those settings yet.

Regardless, I used the last LTS, that last version with gnome and it was lightning quick.

Canonical: please go back to something what works!!!! I don't care if it's gnome or HUD, just don't drive us away from ubuntu.

---

### Post by kmanpilkers on 2012-03-22
I found an old image of 11.04 yesterday and installed that instead. With the same machine and same size swap file it seems to run much better so I will probably just stick to this as others have done!

---

### Post by holytree on 2012-03-22
I believe you should try Lubuntu or puppy linux they are really good OSes to run on netbooks.

why dont u try the 10.10 or 10.04 ???

---

### Post by kmanpilkers on 2012-03-22
> **holytree said:**
> I believe you should try Lubuntu or puppy linux they are really good OSes to run on netbooks.

why dont u try the 10.10 or 10.04 ???

Thanks for recommendation - I will try and stick to Ubuntu 11.04 for now and see how I get on with that, and try another variant if I'm still getting performance issues.

---

### Post by sheds on 2012-03-24
> **holytree said:**
> I believe you should try Lubuntu or puppy linux they are really good OSes to run on netbooks.

why dont u try the 10.10 or 10.04 ???

Hey man, got puppy linux running on my usb key and it works pretty awesome. It's fast, comes with a few things and no lagging at all when typing or scrolling. I read that it loads either entirely or almost entirely on ram, so that would make it really fast.

But hell, if I can keep a few documents I need up on the usb key, ubuntu has some serious problems now cause I may not go back to it.:lolflag:

Thanks for the tip man.

---

