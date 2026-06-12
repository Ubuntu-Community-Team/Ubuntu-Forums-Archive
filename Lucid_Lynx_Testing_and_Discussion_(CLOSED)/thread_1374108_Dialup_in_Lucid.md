---
title: "Dialup in Lucid"
date: 2010-01-06
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by earther on 2010-01-06
I've been following the decline of dialup support since Hardy in these forums. What is the state of dialup in Lucid?  Did a search but no discussion of what to me is a huge roadblock to upgrading.  I'm still on Gutsy (with a Hardy kernel) and really need to upgrade soon.  I'm hoping that Lucid will be friendly to us dialup users.  I have a nice USR serial modem by the way so no need to mess with driver stuff.  Just need to be able to configure a connection. Please give me some good news.  Thanks.

---

### Post by ranch hand on 2010-01-06
I can't tell you about 10.04 but I can tell you that in 8.04 configuration through pppconfig is very easy.  I ran on dialup with and internal USR5610c (hard to get it recognised, unlike your external) and it ran great.

I am hoping to get back on a remote ranch sometime and hope that the support is good in 10.04 too.

---

### Post by earther on 2010-01-06
> **ranch hand said:**
> I can't tell you about 10.04 but I can tell you that in 8.04 configuration through pppconfig is very easy.  I ran on dialup with and internal USR5610c (hard to get it recognised, unlike your external) and it ran great.

I am hoping to get back on a remote ranch sometime and hope that the support is good in 10.04 too.
I have a 5610b and it's internal too.  I also use pppconfig but sometimes use Gnome PPP too.  I've heard from several sources that Hardy was the last version that had reliable dialup.  I'm hoping to get a response from someone who is testing Lucid.

---

### Post by ranch hand on 2010-01-06
I am testing but I am in town with DSL so I am not testing on dialup.

Testing on dial up would be really tough.  I check for updates twice a day.  I just got the second batch and with 10 packages held back by apt the down load is still 17.3MB.  If I want to risk some shaky packages the download runs 18.7.

Yesterday was a big day and there were more updates around 100MB.

Not a thing to do if you want to use your computer.

I may not be on dial up but I want to be (I do not like being close enough for the DSL) so I do follow this stuff.  This is a thread that I think is probably helpful;

[http://ubuntuforums.org/showthread.php?t=1238954](http://ubuntuforums.org/showthread.php?t=1238954)

They are interested in 9.04 but it is a great version.

---

### Post by crjackson on 2010-01-06
> **earther said:**
> I've been following the decline of dialup support since Hardy in these forums. What is the state of dialup in Lucid?  Did a search but no discussion of what to me is a huge roadblock to upgrading.  I'm still on Gutsy (with a Hardy kernel) and really need to upgrade soon.  I'm hoping that Lucid will be friendly to us dialup users.  I have a nice USR serial modem by the way so no need to mess with driver stuff.  Just need to be able to configure a connection. Please give me some good news.  Thanks.

I recently built a system for a friend of mine and installed 9.04.  I managed to get dial-up working perfectly for him, but it was a lot of work for us both.  The working solution wasn't actually that complicated but I had never configured a dial-up connection with Linux, and he had never used Linux.

In the end, he's very happy with Ubuntu 9.04 and dial-up.  It can be done.  If you are already familiar with setting up dial-up in Ubuntu, I would think you could do it without too much trouble.  It's not friendly for beginners though.

---

### Post by earther on 2010-01-07
> **crjackson said:**
> In the end, he's very happy with Ubuntu 9.04 and dial-up.  It can be done.  If you are already familiar with setting up dial-up in Ubuntu, I would think you could do it without too much trouble.  It's not friendly for beginners though.
That's encouraging.  I do want to wait for Lucid LTS though so I won't have to go through this again for a few years.  How is Lucid otherwise?  Is it a winner???

---

### Post by ranch hand on 2010-01-07
I think it is going to be real nice.  There are a lot of little problems right now but that is as it should be.

9.10 had all kinds of new things thrown into it and is still a little rough.  10.04 is the reason that all that stuff was included in 9.10.  They are not putting much new in but being very conservative looking for stability.

The kernel is going to be the one we are using now so things should be pretty stable by the time this is released.

This is going to be a very different animal than what you are using now.  You may want to do some studying on it.

Grub1.97 is not the same at all as grub 0.97.  There is a link in my sig you may want to look at and the links contained in my post.  I think you will like it, I think it is a great boot loader.

Nautilus will give you a split view (hit F3) as of the update today.  A lot of the file structure has been modernized, simplified in many ways.

If you can get to a library or somewhere like that with a faster connection, the betas should be pretty stable (I think).

Here are some links;

[http://fridge.ubuntu.com/node/1916](http://fridge.ubuntu.com/node/1916)

[https://wiki.ubuntu.com/LucidReleaseSchedule?action=show&redirect=LucidLynxSchedule](https://wiki.ubuntu.com/LucidReleaseSchedule?action=show&redirect=LucidLynxSchedule)

---

### Post by earther on 2010-01-07
Thanks for the helpful info.  This is an Ubuntu only box - no more Windoze here!  I'm going to wipe the drive and do a clean install so hopefully everything will just work.  It's going to be a huge job.  Not looking forward to it . . .

---

### Post by Shazaam on 2010-01-07
For me dialup was a breeze until I installed Karmic. Tracking down all of the stuff to get wvdial working was an chore. To add to the ARGH! factor was finding out about pppconfig after finally getting wvdial to work. Hopefully I will be able to avoid the same problem when Lucid final arrives.

---

### Post by earther on 2010-01-07
> **Shazaam said:**
> For me dialup was a breeze until I installed Karmic. Tracking down all of the stuff to get wvdial working was an chore. To add to the ARGH! factor was finding out about pppconfig after finally getting wvdial to work. Hopefully I will be able to avoid the same problem when Lucid final arrives.
Maybe I'll let you be the guinea pig!  Please let me know how it goes for you.

---

### Post by jmmL on 2010-01-07
> **earther said:**
> Maybe I'll let you be the guinea pig!  Please let me know how it goes for you.

One option would be to download (or ask someone with DSL to download) a lucid liveCD. I've never personally configured a dialup set-up, but this should be possible from within the live environment.

---

### Post by earther on 2010-01-07
> **jmmL said:**
> One option would be to download (or ask someone with DSL to download) a lucid liveCD. I've never personally configured a dialup set-up, but this should be possible from within the live environment.
Or I can just install and test it on a spare box.  My local computer guys will download it for me when the time comes.  They'll also let me do the final install there hooked up to their big fat pipe.  :D

---

