---
title: "If I install Feisty from live CD, can I save my Dapper home folder prefs/settings?"
date: 2007-05-22
forum: Installation &amp; Upgrades
---

### Post by Carbonfish on 2007-05-22
Hi all,

While I am not a complete N00b, I have a pretty basic question that I think I already know the answer to, but will ask anyway.

If I am happily running Dapper on my IBM ThinkPad (T23) and I want to install Feisty from the live CD, will Feisty recognize my Dapper partition and give me the option of saving my prefs. etc., or will it just overwrite the existing partitions in favor of it's new matrix (a little Star Trek allusion there)? 

If the installer will not recognize my current (Dapper) install, can I back up my Dapper home folder and then "migrate" my prefs. / settings to Feisty? 

I am very happy with Dapper and have everything working fine on the StinkPad, but would kind of like to have the more polished GUI and newer iteration of Firefox etc., but I really don't want to have to go through the process of setting everything up again from scratch.

Maybe the better question is, should I bother installing Feisty at all?

TIA for your insights,

KC

---

### Post by zvacet on 2007-05-22
Select manual way to partition and be sure** not to format** your home partition.You will format just root partition.I belive that I understand you correctly,**you do have** separate home partition,don´t you?

---

### Post by merlinus on 2007-05-22
Sounds like you have a home folder, not a home partition.  So you can back that up, and perhaps when doing the manual install of Feisty, set up a separate partition for /home.

Then copy your backup to that partition, and you should be set.

Good luck!

-merlin

---

### Post by Carbonfish on 2007-05-22
Sorry it took me awhile to get back here. In answer to Zvacet, no, I don't have a home partition, just a standard install of Dapper with a home folder. So let me try to understand. After backing up my /home folder from the Dapper install, I do the manual install of Feisty and create a partition for root, a partition for /home, and a swap partition, and then after the install, copy the /home backup into the partition that I made for it, and that's it?

How will Feisty recognize the /home partition?

Also, I apologize for my ignorance, but have not done any manual partitioning (except on my external drive for the Mac) during install. How much space should I allocate for the /home partition, and how much for the swap? The installer handled that for me up to now.

Thanks again.

KC

---

### Post by merlinus on 2007-05-22
/swap should be around 512M -- roughly double your RAM.  / can be 12-15G, and the rest to /home.  Feisty will recognize each of these after partitioning and installing.  They will probably be something like hda1, hda2 and hda3 (or sda1, sda2, sda3), depending upon your computer hardware, and the partitioning scheme (which can be all primary if you are not dual-booting with windows).  / and /home will be automatically mounted upon boot-up.  /swap will take care of itself.

The only caveat when backing up your current /home folder is to make sure you copy over all of the hidden files and directories, as that is where most of your preferences and configurations live.

Good luck!

-merlin

---

### Post by Carbonfish on 2007-05-23
Thanks for the info Merlin. Should I anticipate any problems with the kernels being different, or dependency issues? Also, will any proprietary drivers and/or codecs that I might or might not have on board migrate along with the home folder,  and what about my sources list, won't all my repositories be tagged for Dapper?

Oh yeah! Can I just save my Dapper /home folder to a jump drive and move it to the /home partition once it's there and can I do that through the Gnome GUI, or will I need to do it through the terminal? 

Sorry if these questions are silly, but I'm ***am*** new to this manual setup thing.

Thanks once again,

KC

---

### Post by Carbonfish on 2007-05-23
Just one bump.

---

### Post by merlinus on 2007-05-23
I am not certain about your questions.  My understanding is that preferences and configurations live in /home.  The apps, libraries and such are in /.

I am the type to leap into things, but also make sure I have current back-ups.

The main thing is to have fun, even if it means some grimacing and teeth-gnashing until everything gets sorted out.

The uncertainty principle at work....

;)

-merlin

---

### Post by apunc1 on 2007-05-23
I think the easiest thing would be to go ahead while you're on dapper and set up your separate /home partition 
here [http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

then when you do a fresh install of feisty, just dont format that partition.
> 
Also, will any proprietary drivers and/or codecs that I might or might not have on board migrate along with the home folder,

maybe. my .gstreamer plugins show up in my /home folder. i'm not 100% sure about codecs and drivers. i think drivers you need to reinstall.

> and what about my sources list, won't all my repositories be tagged for Dapper?

if you do a clean install i don't think this is an issue

---

### Post by merlinus on 2007-05-23
> **apunc1 said:**
> I think the easiest thing would be to go ahead while you're on dapper and set up your separate /home partition 
here [http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)


This is a very good idea, BUT.... I followed the directions at psychocats, and things got messed up.  The What if it doesn't work? directions did not work, for me.

But aysiu -- who wrote the directions -- saved me with a very simple CLI command.

If I were you, I would back up your /home folder, making sure that all the hidden files and folders are included, and then go ahead.

Good luck!

-merlin

---

### Post by apunc1 on 2007-05-23
> **merlinus said:**
> 

If I were you, I would back up your /home folder, making sure that all the hidden files and folders are included, and then go ahead.

-merlin

does backing up the /home folder not always include the hidden files? in the tutorial the /home folder is backed up before it is moved.
do you mean back it up to a different disk/hard drive?

---

### Post by merlinus on 2007-05-23
> **apunc1 said:**
> does backing up the /home folder not always include the hidden files? in the tutorial the /home folder is backed up before it is moved.
do you mean back it up to a different disk/hard drive?

I am not sure.  You can burn it to a cd (or dvd), and then look at the contents.

BTW, in my last post, it was psusi that saved my cakes.  Here is the thread, in case you need it:

[http://ubuntuforums.org/showthread.php?t=429555&highlight=%2Fhome+partition](http://ubuntuforums.org/showthread.php?t=429555&highlight=%2Fhome+partition)

-merlin

---

### Post by Carbonfish on 2007-05-23
Thanks to you both Merlin and Apunc1. I will check out the threads / wikis and figure out which way I want to go. If I am going to have to re-install all of the drivers and proprietary codecs, I may just make a list of the Apps that I use all the time and wipe the drive and do a clean install, and then install the Apps fresh. I can backup my Firefox prefs and bookmarks without any trouble and the rest is just configuration.

On top of that, I still only have a 30 GB HDD in the ThinkPad, so I don't want to get too partition happy. 

The separate /home folder makes good sense though.

Thanks again,

KC

---

### Post by shad0w_walker on 2007-05-24
If memory serves the fiesty installer has a preferences import option. It doesnt cover everything (Mostly just gaim settings, firefox bookmarks, background) but it might be a simpler way of doing things, if not, just backup your whole home folder if you can. Good luck.

---

### Post by Carbonfish on 2007-05-26
Thanks shad0w_walker,

That is kind of what I was hoping to find out originally when I asked the question. I will search the forums and wikis to find out what I can about the import option in the installer. I agree about backing up the home folder though.

Thanks again to everybody who took the time to give their advice. I'm no mindless Linux **or** Ubuntu fanboy, every distro has it's strengths and weaknesses and sometimes things work better than others, but it's the sense of community I love most about Ubuntu. I never feel like I'm trying to solve my learning-curve challenges all by myself.

KC

---

