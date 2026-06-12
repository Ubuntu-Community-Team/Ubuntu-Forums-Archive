---
title: "migrating to new hard drive"
date: 2007-05-02
forum: Installation &amp; Upgrades
---

### Post by toecutter on 2007-05-02
Currently I'm running (K)Ubuntu on a system with two hard drives, but I've finally got a new SATA drive and I want to set it up for dual booting XP and Ubuntu, then move the two old hard drives to a MythTV box and NAS box. I haven't got much in my /usr directory, but I want to keep my bookmarks, user account, etc., and would like to keep my installed programs intact if possible.

[INDENT]The steps for a brand new install for dual booting, as I understand them, are:
1. run a LiveCD with GPartEd and set up the partitions as follows: 
[INDENT]first 10gb for XP, NTFS
50gb (or so) for Windows games, NTFS
...and the rest of the drive for /home in EXT3
10gb for Ubuntu (is this too much?), EXT3
2gb for swap file (I have 1gb of RAM at present) as the last partition
[/INDENT]
2. install XP into the first partition
3. install Ubuntu into its partition (does the install CD ask where you want to install to? I forget)[/INDENT]

Once this is done, ideally I'd like to 'simply' (if it is that simple) to copy my /usr directory to the new /usr partition and copy everything else over, then wipe the old drives and install them in their new homes. 

What do I need to do to make this work?

---

### Post by aysiu on 2007-05-02
Might something like this help?
[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

---

### Post by toecutter on 2007-05-02
OMG is that you that does the Psychocats site? :) I had no idea until I saw the logo on the site :D I've been through several of your pages over the past couple of months! 

That link does help explain to me why a separate /home partition is desirable, but since I'm starting with a fresh new drive I think your guide here: [http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning) is more applicable, right? Any ideas how big the /home partition should be? should I not bother with a separate /usr partition?

---

### Post by aysiu on 2007-05-02
I wouldn't bother with a separate /usr partition. I'd use this instead:
[SCRIPT: Get a list of packages you've installed since the initial installation](http://ubuntuforums.org/showthread.php?t=393615&highlight=installed)

And make the /home partition as big as possible--that's where most of your files (documents, movies, pictures, music) go.

Yes, it's me that does the Psychocats site. Hope you've found it helpful.

---

### Post by toecutter on 2007-05-02
It's been enormously helpful to me and many others I'm sure :)

Final question (I think) - once I make the partitions and install both OS's, am I able to just copy everything from my current /home to the new /home partition?

---

### Post by aysiu on 2007-05-02
Well, my idea was kind of just moving the /home partition over without reinstalling any OS.

---

### Post by toecutter on 2007-05-02
Ah I see - but I want to install XP and Ubuntu on a totally blank, new hard drive, which is why I need to set up partitioning, etc. 

I did use that script you suggested also, it gave me a nice long list of packages and such :)

---

### Post by toecutter on 2007-05-07
sorry to bump this but I just need a quick answer if I can just copy the /home folder on my existing drive to the /home partition on my new drive... just want to get things installed and get going! :)

---

### Post by aysiu on 2007-05-07
Yes, but you should use the proper copy method--the one outlined in [http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome), or the use of PartImage, or the use of *tar*.

A regular drag-and-drop or *cp* will not work.

---

### Post by toecutter on 2007-05-07
OK cool, thanks very much :)

---

### Post by toecutter on 2007-05-09
Hi again...

I started everything tonight. On your page for creating a new /home partition, Gparted gets stuck at this command: ```
find . -depth -print0 | sudo cpio --null --sparse -pvd /new/
```

The first thing is that 'sudo' doesn't work, the bash shell in 0.3.4 doesn't like it for some reason - I was able to do the earlier commands without it, though, so that's okay. However, the 'cpio' command is also not recognized for some reason. I'm downloading the latest Gparted (0.3.4.6) to see if that can correct the situation but I don't really know what's happened. 

Alternately, I can give PartImage a try - I've looked through the FAQ but can't see how to save the /home partition using it? 

The final option you mention, the *tar* command - do I basically follow the directions on this page to do this? [http://www.tech-recipes.com/unix_tips115.html](http://www.tech-recipes.com/unix_tips115.html) If so this seems the easiest option but would everything work properly?

Sorry for what sound like basic questions! :)

---

