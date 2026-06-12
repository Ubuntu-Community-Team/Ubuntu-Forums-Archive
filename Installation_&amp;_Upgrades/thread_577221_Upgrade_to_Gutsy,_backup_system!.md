---
title: "Upgrade to Gutsy, backup system?!"
date: 2007-10-16
forum: Installation &amp; Upgrades
---

### Post by jasdparker on 2007-10-16
I am really anxious for Gutsy to come out on Thursday...  Here's my problem though, I have messed my system up doing what seem to be very simple things (trying to get my video card to work the way I want using methods in the here in the forums).  It took a lot of wishing and hoping to get it back to running the way I want it to.

I'm worried the upgrade to Gutsy might cause major problems and I'm worried about losing a lot of the other configuration stuff I have going on.

I hear a lot of things like backup your system, etc.  Makes perfect sense to me, but I have a few questions.

1)  What do I need to back up?  Is it just everything in my /home/<username> directory?  Or is there more?

2) If the upgrade completely hoses my system and I re-install Feisty, can I simply just copy the above mentioned home directory over and have everything work correctly (for some reason, I don't think it's that simple).  I'm wondering about a lot of config files like xorg.conf, etc that I would miss if I only copied the home directories over.

Is there an easy to use tool to do exactly what I'm talking about, or is it just a leap of faith?

Also, what's the best method for installing Gutsy?  Is the Synaptic upgrade going to do it, or is a fresh install best?

If the fresh install is best, again, how do I get all of my settings back?

I know, a lot of questions there, and thank anyone in advance for helping me out here.

Thanks much!

---

### Post by FredB on 2007-10-16
Save your /home/username is the main part of backuping your datas.

Xorg.conf and other system config files are not in your home directory.

Your settings are saved in your /home/username directory. Just do this. In a console, type :

ls -alh

And in all .name directory, you'll get your own config files.

The safest way to upgrade : clean install. But you can try upgrading directly with update manager.

Anyway : SAVE your home directory.

---

### Post by wolfen69 on 2007-10-16
im from the other school of thought. get another drive, then backup all files(mp3's, documents, photos, etc.) then do a clean install. reconfiguring is no big deal to me. (is a few extra minutes too much to reconfigure?) i have never saved my home directory.

---

### Post by Tlon on 2007-10-16
FWIW, I did a fresh install of Gutsy, and I'm loving it.  In particular, I didn't have to do a THING to get the drivers working for my nVidia 8800GTX.  I've switched kernels once (from -12 to -14), and recompiled -14 four times for various reasons, and not one of those times did I have to do anything with the video drivers.  Not.a.thing.  For the first time EVER, my nVidia drivers Just Work.  Kudos to the Gutsy team.

---

