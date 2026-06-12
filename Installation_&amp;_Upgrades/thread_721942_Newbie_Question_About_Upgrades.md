---
title: "Newbie Question About Upgrades"
date: 2008-03-11
forum: Installation &amp; Upgrades
---

### Post by MountainX on 2008-03-11
Hi,
If I install Hardy alpha now, will I be able to end up with the equivalent of the release version of Hardy simply by doing regular updates?

With Microsoft, any time you installed beta software, they usually recommended that you completely uninstall it when installing the final release. It seems like this isn't required with Ubuntu, but I would appreciate it if someone can confirm that for me.

Sorry if this has already been answered -- a searched didn't turn up that answer for me.

My plan is to do a clean install of Hardy now to replace Gutsy. I want to replace Gutsy because I'm unhappy with my decision to go with the 64bit version. (On my laptop I went with the 32 bit version and it has been much better for multimedia.) Can I expect that the 32bit version of Hardy will also support multimedia better?

I also plan to re-partition my disk so that /home is separate (in order to protect my data in the event I need to reinstall or reformat the OS partition). What kind of performance hit would I expect if /home is on a fast file server over Gigabit ethernet? 

Thanks

---

### Post by zvacet on 2008-03-12
> With Microsoft, any time you installed beta software, they usually recommended that you completely uninstall it when installing the final release.

You don´t work with Windows now.To answer your question **yes** if you keep your current version update you will end up with final release without need to install it again.Enjoy your Hardy! ;-)

---

### Post by MountainX on 2008-03-12
I cannot tell you how happy I am to be using Ubuntu instead of WIndows! I'm happy not only for the upgrade capabilities, but for everything about Ubuntu and the real open source community. It is a breath of fresh air. Thanks to everyone who has supported Ubuntu.

---

### Post by undecidable on 2008-03-12
Can I make a possible suggestion?

Keeping /home on a server means you can't log in properly as yourself if the server is not available.
(I am not sure but you may be only able to log in as root on a virtual teminal).

An alternative is to separate /home and your data.  
By default Ub keeps all your personal files on /home.
I have moved these to another partition /0docs.
So /home now only contains configuration files, and so is much smaller
and more easily fits on the main system. 

 Things to be careful of in keeping /home small:
a.  some progs automatically put data in /home also, but this can usually be configured.  But eg kjots has no way to configure this, so I use knowit instead.  
b.  Some progs put junk in /home, eg the Firefox cache lives there, and I don't know any way to move it out.  

Anyway it is jsut a thought.

---

### Post by MountainX on 2008-03-12
> **undecidable said:**
> Can I make a possible suggestion?


Thanks for the suggestions. I'll take your advice regarding the file server. Could you explain exactly how you moved all your personal docs to another partition? Thanks.

---

### Post by undecidable on 2008-03-13
I have a directory /0docs on/dev/hda6,
and /home/mc is on /dev/hda8.  
(I put the 0 in front so it sorts first on a directory listing of /)

I set up my partitions before I install
and direct the installer to use the partitions as I have set up.  
I use the text based installer (the "Alternate") as I find it easier,
but I believe you can do it with the normal installer as well.
If you found that you had missed it and that
your /0docs was not being mounted,
then you would just add an entry for it in the /etc/fstab file. 

I then just put all my documents in /0docs - it is that easy.

Two things you can do to make it more convenient:

1.  create shortcuts etc so /0docs is as easily accessible as /home.
I use Kubuntu so will use that as an example:

a.  Add an entry to the open/save dialog for /0docs by right clicking on the left side of the open/save dialog window.

b.  Add an entry for /0docs in Konqueror's Navigation panel, again by right clicking there.
Or if you are using Dolphin, add a bookmark for /0docs.

c.  Put a shortcut in /home/<yourname> for /0docs,
that way if you are in /home, you can easily transfer to /0docs.

2.  For some big apps, move the profile to /0docs.
eg Thunderbird: move the profile to /0docs/mail and all you mail will be in /0docs.

It takes about 1/2 hr of setting u when you first install,
but it is worth it to have data separate from profile.

Another advantage is that I have multiple systems on my machines, and each have incompatible home folders (eg Kubuntu and Ubuntu) but all use the same /0docs, so my data is accessible from each system.

Hope this is helpful.
MC

---

