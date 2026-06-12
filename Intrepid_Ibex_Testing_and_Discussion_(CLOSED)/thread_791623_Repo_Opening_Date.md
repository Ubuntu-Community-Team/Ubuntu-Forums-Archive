---
title: "Repo Opening Date?"
date: 2008-05-12
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by Trueno22 on 2008-05-12
Anyone know when the Ibex repos come online?  Anxious to see what breakarage will cause me to pull what's left of my hair out. :lolflag:

---

### Post by smartboyathome on 2008-05-12
I think they already are online, but are just a clone of Hardy's repos.

---

### Post by Quikee on 2008-05-12
> **smartboyathome said:**
> I think they already are online, but are just a clone of Hardy's repos.

No.. there are already some updates (btrfs 0.14, openarena 0.76, wesnoth 1.4.2, GCC 4.3, new libc) and some new programs merged from debian - but generally it is not yet worth to upgrade as it might only break some things (the new xulrunner breaked my firefox for example) and a lot of things trigger can trigger to remove half the programs in the system so you have to be really careful.

---

### Post by olskar on 2008-05-12
How would you recommend me to do if I wanted to install Ibex in a virtual machine?

---

### Post by bobbocanfly on 2008-05-12
> **olskar said:**
> How would you recommend me to do if I wanted to install Ibex in a virtual machine?

There are no daily CD builds yet so you need to download a Hardy CD (i recommend the alternative so you can do a minimal install, change to Intrepid and grab all the packages straight from Intrepid instead of upgrading lots).

Once you have a Hardy system running in the VM change all the mentions of 'hardy' in /etc/apt/sources.list to 'intrepid' and run "sudo apt-get update && sudo apt-get upgrade".

There are probably easier ways but thats the way that worked for me.

---

### Post by ibuclaw on 2008-05-12
> **bobbocanfly said:**
> There are no daily CD builds yet so you need to download a Hardy CD (i recommend the alternative so you can do a minimal install, change to Intrepid and grab all the packages straight from Intrepid instead of upgrading lots).

Once you have a Hardy system running in the VM change all the mentions of 'hardy' in /etc/apt/sources.list to 'intrepid' and run "sudo apt-get update && sudo apt-get upgrade".

There are probably easier ways but thats the way that worked for me.

Nope... lol
I've already found this hack and broken systems!:lolflag:
[read here.]("http://ubuntuforums.org/showthread.php?t=787829")

Perhaps if you find and download the [Hardy-Minimal ISO]("https://help.ubuntu.com/community/Installation/MinimalCD"), install that (and only that). And then upgrade. You may "just" stand a chance.
Although, I would personally make an extreme implementation on AptPinning the Intrepid repositories first.

ie: Put this in your "**/etc/apt/preferences**" file.
```

 Package: *
 Pin: release a=intrepid
 Pin-Priority: 10

 Package: *
 Pin: release a=hardy
 Pin-Priority: 900

```

And make a two copies of all repository lines in your /etc/apt/sources.list file. Then rename the copy set from hardy to intrepid. So you still have hardy as a repo to keep your synapse strong and standing.

That should also prevent the auto-installation (or upgrading) of packages unless you specifically choose them from intrepid:
```
apt-get install gcc/intrepid
/*OR*/
apt-get -t intrepid install gcc

```

Regards
Iain

---

### Post by aamukahvi on 2008-05-12
I installed Hardy in VB and after switching apt sources to II, made a snapshot. If it breaks I can always go back and dist-upgrade again.

---

### Post by plun on 2008-05-12
Well, we had a discussion in another thread about breakage.

This package is broken and must be downgraded to Hardys version
(credits to Eclipse)

[http://packages.ubuntu.com/search?suite=default&section=all&arch=any&searchon=names&keywords=libxfont1](http://packages.ubuntu.com/search?suite=default&section=all&arch=any&searchon=names&keywords=libxfont1)

Otherwise no GUI....

There is also a little perl mess and **libdigest-sha1-perl** breaks GIT


[B]
The Intrepid mailing list[/B] is maybe  important to follow for crazy Ibex users..:)

[https://lists.ubuntu.com/archives/intrepid-changes/2008-May/thread.html](https://lists.ubuntu.com/archives/intrepid-changes/2008-May/thread.html)


and perhaps Psychocats manual for .**/home on a separate partion**.
[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)


Up and running on kernel 2.6.25....  "home brewed"  :)  :lolflag:

---

### Post by disturbedite on 2008-05-12
yeah, the updated repo has been in place for over a week.

---

### Post by ibuclaw on 2008-05-12
Well...
I've successfully installed these list of programs on a real system (using my apt-pinning trick).
They are all the upgradeable packages that come under "**base**" in the aptitude package listings.
```

sudo aptitude -t intrepid install adduser base-files base=passwd bsdutils fdutils ftp grep hostname libslang2 libstdc++6 libwrap0 makedev mount perl-base sed tar tcpd util-linux

```
Accept the first solution that aptitude gives to, reboot.
Now, when you log back in and open up a terminal.
Type in lsb_release -d to see your wonderful new output:
[PHP]
$ lsb_release -d
Description:    Ubuntu intrepid (development branch)
[/PHP]

I suppose all future bugs I report will be effectively defunct on launchpad now...

Regards
Iain

---

### Post by Amaranth on 2008-05-13
No no no no. Don't do that.

---

### Post by ibuclaw on 2008-05-13
> **Amaranth said:**
> No no no no. Don't do that.

Why not?

What's the difference really between doing this, and say mixing Debian Etch with Lenny and Experimental...

---

### Post by disturbedite on 2008-05-14
i did it in a much more simple way.  i did a fresh install of kubuntu 8.04 then changed the sources.list file to intrepid from hardy, updated, & voila: intrepid.

---

### Post by ibuclaw on 2008-05-14
What day did you do that on?

I've tried that, and it broke on my first attempt.

And besides, Pinning Hardy to have a superior leverage over Intrepid is much more efficient.
It means for developers that when they need, say, the closest to bleeding edge python technology. They can safely get it without upgrading their entire system to a Pre-Alpha state.

There is only one flaw in it though. When a new Hardy release comes, most, or all Intrepid packages will be automatically downgraded.
But we can set specific Pinnings for them not to be touched. :)

But anyways, my humble applause to you my good friend for getting it to work!

We should start counting how many Intrepid users there are already out there!

Ok... there is disturbedit, aamukahvi and me.
Thats three people so far...

I hope there's more than that, isn't there?

Regards
Iain

---

### Post by Gina on 2008-05-14
I'm hoping to get Intrepid onto my old (test) desktop soon.  I'm avidly reading the posts to see how to do it.  It doesn't matter about breakages - there's nothing I particularly want on there - I don't care if it wipes the entire hard drive - I can simply reinstall.

I'm also considering building myself a new machine for testing.  I'm looking at an AMD Athlon 64 dual core processor.  [This bundle offer]("http://www.maplin.co.uk/Module.aspx?TabID=1&ModuleNo=222875&doy=14m5") from Maplins.

---

### Post by cecilpierce on 2008-05-14
I am using II on 3 machines and i have broke it lots of times. The only thing that fixes it is to pin libxfont1. Is that still broke ?
I like broken stuff and try to fix it, with help !
Thanks, Cecil

---

### Post by chrismine on 2008-05-14
> **tinivole said:**
> What day did you do that on?

I've tried that, and it broke on my first attempt.

And besides, Pinning Hardy to have a superior leverage over Intrepid is much more efficient.
It means for developers that when they need, say, the closest to bleeding edge python technology. They can safely get it without upgrading their entire system to a Pre-Alpha state.

There is only one flaw in it though. When a new Hardy release comes, most, or all Intrepid packages will be automatically downgraded.
But we can set specific Pinnings for them not to be touched. :)

But anyways, my humble applause to you my good friend for getting it to work!

We should start counting how many Intrepid users there are already out there!

Ok... there is disturbedit, aamukahvi and me.
Thats three people so far...

I hope there's more than that, isn't there?

Regards
Iain
Count me in too!

---

### Post by chrismine on 2008-05-14
> **cecilpierce said:**
> I am using II on 3 machines and i have broke it lots of times. The only thing that fixes it is to pin libxfont1. Is that still broke ?
I like broken stuff and try to fix it, with help !
Thanks, Cecil
It is been fixed, I could not login to GUI and today went into recovery mode and there was a new package. So here I am again.

PS: Recovery mode is getting better al the time!

---

### Post by Eclipse. on 2008-05-14
> **chrismine said:**
> 

PS: Recovery mode is getting better al the time!

Yeah I noticed aswell.

You can now fix broken packages from there along with a few other things.

---

### Post by disturbedite on 2008-05-14
you could *always* fix packages from recovery mode.  you just selected drop to root shell/command line & then you could do it from there.

---

### Post by ibuclaw on 2008-05-14
> **Eclipse. said:**
> Yeah I noticed aswell.

You can now fix broken packages from there along with a few other things.

It's nice to see that it's finally living up to its name! :popcorn:

Don't know about anyone else... But I don't feel like waiting round for Linux 2.6.25 to come for Intrepid...
So I've started compiling it myself :D

[Read Here for more info.]("http://ubuntuforums.org/showthread.php?t=311158")

Bleeding Edge is fun!

Regards
Iain

---

### Post by ibuclaw on 2008-05-14
> **Gina said:**
> I'm hoping to get Intrepid onto my old (test) desktop soon.  I'm avidly reading the posts to see how to do it.  It doesn't matter about breakages - there's nothing I particularly want on there - I don't care if it wipes the entire hard drive - I can simply reinstall.

I'm also considering building myself a new machine for testing.  I'm looking at an AMD Athlon 64 dual core processor.  [This bundle offer]("http://www.maplin.co.uk/Module.aspx?TabID=1&ModuleNo=222875&doy=14m5") from Maplins.

Sounds pretty cool.
ECS GeForce6100SM-M2 motherboard...
That's American Megatrends! So I'd highly recommend it (I don't work for them, I just have a general belief that their motherboards somehow "perform" better with Linux... I mean, they power the ASUS EeePC for Great Uncle Jekubs sake!).

Though, first, try looking through Amazon, they are way cheaper (I got a 2GHz Athlon64 with Motherboard/1GB and a 256MB NVidia Card for £50.)

Regards
Iain

---

### Post by plun on 2008-05-14
> **tinivole said:**
> 

Don't know about anyone else... But I don't feel like waiting round for Linux 2.6.25 to come for Intrepid...
So I've started compiling it myself :D

[Read Here for more info.]("http://ubuntuforums.org/showthread.php?t=311158")



Yup, using that method myself....:) 

Don't forget to check/tick your soundcard,   make xconfig   > Advanced Linux Sound System, look for your card

It takes 2 hours to build a kernel for me so its no fun starting
with a silent kernel....:)

---

