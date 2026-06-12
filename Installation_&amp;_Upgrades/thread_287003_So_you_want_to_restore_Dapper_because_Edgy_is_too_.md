---
title: "So you want to restore Dapper because Edgy is too troublesome?"
date: 2006-10-28
forum: Installation &amp; Upgrades
---

### Post by davarino on 2006-10-28
This thread is being started so that someone might give a step-by-step on restoring Dapper (or earlier) to Edgy systems that got too messed up. I am stuck (and so are many others), and I have a lot of stuff on my hard drive that I don't want to write over. A "strategic retreat" is in order for some of us until Edgy is a bit less edgy.

[SIZE="1"]As an aside, the many really good suggestions that people have made such as "put your important stuff in a separate partition before you upgrade" *should be scripted as part of the upgrading process*. Yes, make it easy to opt out, but at least make a jet-powered "super safe" upgrade. (Maybe even having a boot-disk-driven reversion utility. :cool:) 

This would ease installation for the "Human Beings", not just for the really clever hacker (also Human ;) ) who can pull him/her/self out of the deepest hole.

IMO, this release should have been *postponed*... it was not "ready for primetime".[/SIZE]

---

### Post by wildutah on 2006-10-28
Before you try upgrading, image your root directory.  

Boot off the liveCD (any live CD, even previous versions or KNOPPIX) and 
```
~> sudo umount /dev/hda5
~> sudo dd if=/dev/hda5 of=/home/user/backupdiskimage bs=64K
```
Where /dev/hda5 should be your root directory's partition.  Remember that you have to have your /home directory mounted on a different partition from your root directory for this to work, as you always should.

Then if your upgrade goes spectacularly bad, as mine and most others have, just copy back the old image
```
sudo dd of=/dev/hda5 if=/home/user/backupdiskimage bs=64K
```
And everything is happy.:cool:

---

### Post by davarino on 2006-10-28
Thanks, wildutah!

I am somewhat puzzled. Will this entire procedure that you listed work if I have *already upgraded* to Edgy?

Unfortunately, I have always followed "official" upgrade and installation instructions pretty much to the letter... which means that I have never put my /home directory on a different partition, nor have I imaged my root directory. (That "as you always should" phrase kinda pokes me with a stick, because if it is so important why isn't it implemented in installation scripts? :confused: )

---

### Post by jem7v on 2006-10-28
> **davarino said:**
> I have always followed "official" upgrade and installation instructions pretty much to the letter... which means that I have never put my /home directory on a different partition...

Actually, if you used the automatic partitioner when you first installed Ubuntu (and it's the default option in both the graphical and text installers, unless I'm mistaken), it should have done that already. I think the only way to put your /home on the same partition as everything else would probably be if you ran the manual partitioner and intentionally put it in the same place as the rest of your stuff.

---

### Post by wildutah on 2006-10-29
> **davarino said:**
> Thanks, wildutah!

I am somewhat puzzled. Will this entire procedure that you listed work if I have *already upgraded* to Edgy?

Unfortunately, I have always followed "official" upgrade and installation instructions pretty much to the letter... which means that I have never put my /home directory on a different partition, nor have I imaged my root directory. (That "as you always should" phrase kinda pokes me with a stick, because if it is so important why isn't it implemented in installation scripts? :confused: )

Sorry, you have to do this before you start the upgrade process.  Then you are guaranteed a restorable system afterward if anything goes wrong.

I thought the default installed did mount /home on its own partition.  Check your partitions by running ```
~> mount
```

---

### Post by handy on 2006-10-29
There is no easy way to get out of your situation that I'm aware of.

You cannot just uninstall the Edgy  upgrade.  So save what is valuable & go again with Dapper.  Having a separate **/home** partition certainly makes upgrading less painful, I can't speak from experience on going the other way.

My only concerns are any configuration files in **/home** that may not like going back?  I think **Aysiu** may know about this?

If some one can verify that a separate **/home** partition is good for your situation then perhaps if your machine functions well enough you can use [these instructions]("http://www.psychocats.net/ubuntu/separatehome") & make a new **/home**?

The default install does not create **/home** on it's own partition unfortunately.

---

### Post by davarino on 2006-10-29
Thanks, everybody, for the suggestions. Unfortunately for me, I upgraded to Edgy according to Ubuntu "official" instructions, and did the same to get to Dapper and the previous. Along the way, it appears, the fresh-installation process *did* change to put root on a separate partition... but the *upgrades* never took care of this. :-k

Some of the problems I have faced with the suggestions so far are:
[LIST=1]
[*]The Dapper LiveCD does not allow root access (at least not the ways I've tried) - can't even mount anything but /home/ubuntu.
[*]Using Knoppix, I have root access, but then I have no root partition to start with, so it's a dead end.
[*]The system that I was left with after trying to install Edgy finally threw up all over itself and doesn't even get up as far as trying to load my nvidia stuff... just worser and worser.
[/LIST]

My present plan is to do one of several things:

[LIST=1]
[*]Reinstall Dapper onto a new partition (let's say about 20Gb or more, the 2Gb "official" recommendation is not enough even to update from: I tried today) carved out of my old Ubuntu partition. Then copy over the "important" stuff and call the remnants of the old partition a junkyard.
[*]Copy the "important" stuff onto CDs, and then kill out the whole Ubuntu installation and reinstall Dapper over it. (And I know I'd hate this, because the Dapper installation process is sloppy, too.)
[*]Just sit on the whole mess until something comes up that makes sense to me.
[/LIST]

I am coming back to those stomach feelings I had back several months ago when Dapper came out: I feel like an utter sucker for falling for the newest, latest, half-baked Ubuntu. Yes, I know that some will say, "But you *know* that the first release of a new version is always filled with troubles." - But does that excuse Ubuntu Central for talking up a clearly deficient new product? Billy Gates used to do *that*.

I see again that open source developments may work, but there's a lot of stumbling in the dark before they do. And yes, ***I*** have the time to sit and wait... but there is no way that open source will ever be accepted by non-geeks if we don't have extensive testing before release. There aren't that many masochists out there.

Quality requires intensive organizational discipline, open source or closed source. M$ fails on quality because of concentration on profitability; it seems open sourcers fail by figuring the piranhas will show us what is inedible, rather than sticking their fingers in the pot lots of times to check to see if things are good enough to set onto the table.

Again, thanks everybody for trying to help. I'm glad at least that 20% of us came out of this with a really nice system.

---

