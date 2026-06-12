---
title: "Upgrade to Gutsy or install it new?"
date: 2007-10-18
forum: Installation &amp; Upgrades
---

### Post by bluemech on 2007-10-18
Hi all,

Since the beta of Gutsy I've been reading up on it. Quite excited by the new features put in as defaults, as they should make breaking the system a bit harder to do this time around. :P

That said, I'm still currently running Feisty 64-bit on my box. Should I upgrade to Gutsy, or download an ISO and install it from scratch?

Reformatting my partition and installing it new will probably produce a cleaner system, but I don't really want to go through installing all the applications I have here now... some of them weren't through apt-get.

Your opinions on the matter?

---

### Post by Pumalite on 2007-10-18
Read the threads on the Forum and you'll find out a clean install is a better bet.

---

### Post by rsambuca on 2007-10-18
I see no reason to at least attempt the upgrade!  Back everything up, comment out your non-ubuntu repos, and go for it.

(Let me know if it works as I haven't upgraded yet.)

Actually, I have a bunch of partitions going, so I usually start fresh, and slowly set it up the way I like, I then go and see if my old one is upgradeable.  I have never had any problems with an upgrade (Dapper - Edgy, and Edgy -Feisty).

---

### Post by DaleFarrell on 2007-10-18
I'm in the same boat. I couldn't find any discourse between the beta and the final. I couldn't wait for the discs so I used the beta .iso. Went through hell to get  Broadcom WiFi going. Will be watching your post closely.DaleinSeattle.

---

### Post by rsambuca on 2007-10-18
> **DaleFarrell said:**
> I'm in the same boat. I couldn't find any discourse between the beta and the final. I couldn't wait for the discs so I used the beta .iso. Went through hell to get  Broadcom WiFi going. Will be watching your post closely.DaleinSeattle.

If you installed the Gutsy beta version, then you automatically have the final version, assuming you have been keeping up with your updates.

---

### Post by Pumalite on 2007-10-18
> **DaleFarrell said:**
> I'm in the same boat. I couldn't find any discourse between the beta and the final. I couldn't wait for the discs so I used the beta .iso. Went through hell to get  Broadcom WiFi going. Will be watching your post closely.DaleinSeattle.

I you do the updates you'll have the final release. You should have something like this:

pumalite@pumalite-desktop:~$ uname -a
Linux pumalite-desktop 2.6.22-14-generic #1 SMP Sun Oct 14 23:05:12 GMT 2007 i686 GNU/Linux
pumalite@pumalite-desktop:~$

(to try to upgrade today is crazy. Good luck)

---

### Post by rfruth on 2007-10-18
I went the upgrade route (it took almost 4 hours even with my speedy DSL connection ((2.0 P4, 512 MB RAM ...)) that was last night, so far so good - will do a complete install one of these days cause that is preferred :)

---

### Post by rsambuca on 2007-10-18
If you want to do it quickly, just download the alternate iso using torrents.  You can then use the cd to do a quick upgrade by adding it to your sources list.  The torrents are flying now and it took just over half-an-hour for each iso I downloaded.

---

### Post by Jason.TJ.Johnson on 2007-10-18
This morning, I downloaded the DVD version (via a torrent) and it flew. I averaged almost 800k/sec.

Anyway, after burning the ISO, ubuntu asked if I wanted to update. I figured why not, went along with the update, and here I am. Easy, smooth, no issues what so ever.

---

### Post by TorchlightJay on 2007-10-18
word of advice for updating in general, if you update on a distro that you've done a lot of manual upgrades via source, you may cause more trouble that it's worth. I would recommend a clean install in that case. Otherwise, do an upgrade. I think that it's an easy upgrade from Feisty to Gutsy. You can even do it through the Package Manager.

---

### Post by Pumalite on 2007-10-18
Not tonight!

---

### Post by rsambuca on 2007-10-18
> **Pumalite said:**
> Not tonight!

Yes you can, with the alternate cd as a source for the packages!

---

### Post by Pumalite on 2007-10-18
> **rsambuca said:**
> Yes you can, with the alternate cd as a source for the packages!

Ha...You know I meant the servers.

---

### Post by S1l3nt_Hunt3r on 2007-10-18
Hi. I just downloaded the live-cd. Can I use the live-cd instead of the alternate-cd as a source?

---

### Post by Snocrash on 2007-10-18
I usually upgrade the system myself ( I have not upgraded to Gutsy yet). But I have wiped it and installed clean when there are problems. The most important question is :

*"Are you running software from non-Ubuntu repos?"* (I run lots of it, including generic compiled kernels).

The safest way I have found is to wait a week or three. As with any software release ending in zero, give it some time. Let the third party stuff catch up and patch for the new system. Then upgrade. 2 to 4 weeks is usually all it takes. This also lets Ubuntu itself settle a little, as well as upgrading faster because the entire world is not trying to download the system.

If you are too impatient and answered yes to the above, I would probably backup and install fresh.

Just my $.02

-Sno

---

### Post by rsambuca on 2007-10-19
> **S1l3nt_Hunt3r said:**
> Hi. I just downloaded the live-cd. Can I use the live-cd instead of the alternate-cd as a source?

Nope

---

### Post by bluemech on 2007-10-19
> **Snocrash said:**
> I usually upgrade the system myself ( I have not upgraded to Gutsy yet). But I have wiped it and installed clean when there are problems. The most important question is :

*"Are you running software from non-Ubuntu repos?"* (I run lots of it, including generic compiled kernels).

The safest way I have found is to wait a week or three. As with any software release ending in zero, give it some time. Let the third party stuff catch up and patch for the new system. Then upgrade. 2 to 4 weeks is usually all it takes. This also lets Ubuntu itself settle a little, as well as upgrading faster because the entire world is not trying to download the system.

If you are too impatient and answered yes to the above, I would probably backup and install fresh.

Just my $.02

-Sno

Thanks, this summed up what the others said basically. And after reading through the rest of the threads in this section of the forums (lots of complaints on the upgrade process, mostly cause yes, the rest of the world **is** downloading it), I'm inclined to wait it all out a little bit more, and then just wipe the root partition and start over. Feisty is still working great for me anyways.

Yes, I'm running a lot of stuff outside the repos actually, which is why starting anew is going to be such a pain. >_< It's a good thing I did partition my data away.

Next time I'm doing documentation on all the changes I made to the system that mattered.

---

