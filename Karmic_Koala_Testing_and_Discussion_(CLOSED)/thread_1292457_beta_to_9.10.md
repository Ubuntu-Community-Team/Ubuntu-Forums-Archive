---
title: "beta to 9.10?"
date: 2009-10-15
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by NastyDee on 2009-10-15
Hey,

Will i be able to upgrade from Beta to 9.10?

---

### Post by rifak on 2009-10-15
im assuming you mean upgrading 9.10 beta to 9.10 official. if you keep up with the updates, it will become the official release.

---

### Post by Johnny B on 2009-10-15
update manager will notify you of the official release, or you can do it manually (once its released) with > sudo apt-get dist-upgrade

---

### Post by NastyDee on 2009-10-16
> **Johnny B said:**
> update manager will notify you of the official release, or you can do it manually (once its released) with


Ohh ok so if i do that it will just update to the official version? (not now but when its released ofcourse^^)

Edit: Nvm a friend just told me that it wont update everything. :'(
So i can better wait 13 days

---

### Post by zzzBrett on 2009-10-16
> **NastyDee said:**
> Ohh ok so if i do that it will just update to the official version? (not now but when its released ofcourse^^)

Edit: Nvm a friend just told me that it wont update everything. :'(
So i can better wait 13 days

The way I understand it, if you install 9.10 beta, and keep updating as updates become available, it will automatically become 9.10 official.

---

### Post by NastyDee on 2009-10-16
> **zzzBrett said:**
> The way I understand it, if you install 9.10 beta, and keep updating as updates become available, it will automatically become 9.10 official.


yea but some things wont be updated?

---

### Post by rifak on 2009-10-16
ummmm im not sure what wouldn't be updated? when doing updates in beta, you get new kernels, new core system files, new core programs, and updates to manually installed programs. what else is there really?

ive asked this question on here before and some pretty knowledgeable people said that all you need to do is keep up with updates. also, im not sure why you would have to run 'sudo apt-get dist-upgrade' because you are already using that distribution...you essentially have ubuntu 9.10 on your computer. when someone downloads the official release, its basically just your up-to-date system. the difference between beta and official is that in the beta, you are seeing the active development and changes happening and you're keeping up with those by installing them. eventually, your system will match what the official release is going to be in a couple weeks.

if im wrong, then please someone correct me. this has been my impression the whole time and if it is wrong, i would definitely like to know.

---

### Post by NastyDee on 2009-10-16
Well i'm just a beginner with linux ubuntu... I'm now on windows but i just want to switch quick as possible... But a friend told me some bugs wont be fixed if i upgrade from beta so... don't really know what to do now

---

### Post by rifak on 2009-10-16
well i would definitely give it a try. ive been running the beta for a little more than a week, and have completely switched over to it. ive had no problems, and it has been, by far, the best release for me and my computer. i am really impressed and happy with it...and i think a lot would agree.

also, if you want to give it whirl, download the beta, install it and use it until the official release comes out then do a reinstall (of course, you dont have to to do this, as i said before, but if you dont trust it or want to be sure, you can do it).

---

### Post by Slim Odds on 2009-10-16
> **Johnny B said:**
> update manager will notify you of the official release, or you can do it manually (once its released) with

This would be true if you were using 9.04.

The transition from beta to official is NOT a "version" change. So you will not be notified.

---

### Post by Slim Odds on 2009-10-16
> **NastyDee said:**
> yea but some things wont be updated?

Is this a question?

Why to you think that "some things" won't get updated?

Like what?

---

### Post by NastyDee on 2009-10-16
I don't know, i'm new to linux so i don't know anything^^
But a friend told me.. thats all i can say

But it looks like all of you disagree with that

---

### Post by bodhi.zazen on 2009-10-16
> **NastyDee said:**
> Hey,

Will i be able to upgrade from Beta to 9.10?

Yes.

If you are already running the Best, you can upgrade with any numbner of tools.

Update Manager is preferred.

```
update-manager
```

You can also

```
sudo apt-get update && sudo apt-get -y dist-upgrade
```

Be warned, 9.10 is still in Beta and there have been bugs (even this close to the release) so be prepared for breakage.

If you are new to Ubuntu probably you should stay with 9.04.

---

### Post by NastyDee on 2009-10-16
Why? Isnt Ubuntu 9.10 alot faster?

---

### Post by andrewabc on 2009-10-16
If 9.10 works on your computer, I'd use it instead of 9.04. I would not recommend installing default 9.04 now, and upgrading to 9.10 in 2 weeks. There are lots of changes. Mostly ext4 and grub2(?) which will not be transferred to 9.10 if upgrading.

Yes it is possible there are some minor differences between installing beta and updating, and the final, but you probably won't notice them much.

If you have no problem formatting drive, then you could always install 9.10 final when it comes out. Install the beta now, make sure everything works and keep using it and keep up to date (update manager). If you notice any problems at any point in future that can't be solved, then install 9.10 final. So when 9.10 final is released, download and burn to cd-rw to have in case something bad happens. Instead of having the beta on cd.

---

### Post by bodhi.zazen on 2009-10-16
> **NastyDee said:**
> Why? Isnt Ubuntu 9.10 alot faster?

The boot times are faster, when they work (booting has broken in 9.10 twise in the last month or so).

9.10 is in Beta testing. That is fine if you are wiling to accept and fix bugs, but not optimal, IMO, if you are new to Ubuntu.

IMO 9.10 has been unstable (the daily desktop builds did not boot for example) and I would not advise it to new users.

There is nothing wrong with 9.04.

---

### Post by the.lost.one on 2009-10-16
when the final 9.10 is released on oct 29 and i am running 9.04 and i upgrade from within 9.04, would that be a smooth transition and as good as fresh 9.10? (assuming no software rot)

coz right now there is this partial upgrade scare

---

### Post by ikisham on 2009-10-16
If I understood, you don't have Ubuntu yet.

C'mon download it and give it a go. Mine is working perfectly and if it works fine for you then you just update and you'll have the final 9.10 when it comes out.

[Torrent]("http://releases.ubuntu.com/9.10/ubuntu-9.10-beta-alternate-i386.iso.torrent") for i686 (32-bit)
[Torrent]("http://releases.ubuntu.com/9.10/ubuntu-9.10-beta-desktop-amd64.iso.torrent") for amd64 (64-bit)

[i686]("http://ubuntu.cs.utah.edu/releases/9.10/ubuntu-9.10-beta-desktop-i386.iso")
[amd64]("http://ie.releases.ubuntu.com/9.10/ubuntu-9.10-beta-desktop-amd64.iso")

If your computer is rather new, go with the amd64.
The torrents are for the alternate cd. They are not live-cd's, they can only be installed. The good of this is that I read that the installer in the live-cd was somewhat buggy, but I can't confirm that because I installed from the alternate cd image (torrent). If you want to try the live-cd then fetch one from the last links.

*edit*- after you install it (ask your friend to help you if you need with the alternate cd, but paying attention you can do it) just pay attention when you run the update manager. Ask here in the forum before doing an update (it most certainly will ask for a partial upgrade since some packages may have to be removed), telling what it wants to remove and you'll be ok. Also set the download servers to Ubuntu's main server.

---

### Post by bodhi.zazen on 2009-10-16
> **the.lost.one said:**
> when the final 9.10 is released on oct 29 and i am running 9.04 and i upgrade from within 9.04, would that be a smooth transition and as good as fresh 9.10? (assuming no software rot)[/code]

In theory yes. On my laptop I have an install that has gone form 8.04 -> 8.10 -> 9.04 -> 9.10 Beta. Now with the Beta I have had to fix a few items manually.

some people will inevitably have problems with the upgrade, and if you do, that is why we keep our data in a separate /home or /data partition, simply do a fresh install.

[quote]coz right now there is this partial upgrade scare

Right not 9.10 is in Beta. There have been several recent problems / bugs. If you do not want to manage bugs and occasional breakage, do not run the Beta.

---

### Post by rifak on 2009-10-16
come on everyone, he's new...remember when we were all there?

so to clear this up: when you have the beta version, everything becomes the official release as long as you keep up with all of the updates...so thats not a problem.

as for it still being in beta, i'll give you my experience: it has been very stable. the installation was a breeze, everything worked out of the box (meaning, all of my hardware was detected right after installation), and no major breaks during the updates (there was some mislabeling of folder icons, but it was fixed in an hour or so). as for people saying things might break and get messed up, usually it is fixed within a couple of hours or the next day, if anything happens at all. also, since its so close to the release day, everything is looking really really nice and working very well. i think a lot of people would agree.

if you are ready to completely give up windows (or do a dual boot), my advice would be to go for it. what's to lose? you are already wanting to do an install, a lot of people are extremely happy with what has been produced for this release, and its a cool/fun learning experience. if you are still having reservations about it all, then just wait 2 weeks and you'll be able to get the official release...no worries.

---

### Post by areteichi on 2009-10-16
why make his transition more complicated than it already is? just wait two weeks and you're good to go. no need to take unnecessary risks. forget the beta and wait for the final.

---

### Post by ikisham on 2009-10-16
> **areteichi said:**
> why make his transition more complicated than it already is? just wait two weeks and you're good to go. no need to take unnecessary risks. forget the beta and wait for the final.

The point is that it's no harm to play with it. The worse that can happen is NastyDee download again the final release to reinstall, and then he'll know already some things.
ND, if you resolve to try to install the beta (as I said, you can always reinstall the final - it's a breeze) only read about how to dual-boot so you don't harm your Windows installation.

---

### Post by mperry on 2009-10-16
I'm not particularly new to debian or ubuntu for that matter. Been kicking around for quite some time; but the 9.10 beta has been quite good. I have had to research and fix a few things like on my laptop, I had no virtual terminals after X launched. I like virtual terminals so I went searching for a fix to that. Secondarily, the pulseaudio drivers would make a popping noise before a sound played. I found a fix for that. I'm not particularly satisfied with the open source radeon drivers with older and legacy radeon cards like the one in my T60. Its something to live with I guess. Wierd part is that with no desktop effects I get a few flashes when opening different things. With normal effects, they all go away and everything is nice. I just run the normal effects; even though I am not normal :)

I would do this though. Experiment, definitely; but do it in VirtualBox on 9.04 or on XP or Windows 7. It gives you a chance to experience the charm and wonder of the beta to release process but you are not locked down. I do this quite often with the debian unstable tree as well. Its a great way to test but not have to really worry about what may happen. You can take a snaphsot in vmware or virtualbox and roll on back if you need to. If you blow it out, just do another virtual install. What's the loss there?

My advice FWIW. Use the virtual iron.

---

