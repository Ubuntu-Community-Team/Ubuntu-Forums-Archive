---
title: "Installing a new partition"
date: 2006-07-18
forum: Installation &amp; Upgrades
---

### Post by MishMich on 2006-07-18
Hi,

I used to be a UNIX SA many years ago, and have avoided linux because I always found it so frustrating whenever I did install it, and last time I looked was about 6 years ago.  I've not touched UNIX in about 5 years - and was mainly an SVR4-variant admin.

I installed ubantu DD over the weekend on and old Dell because I needed Apache & php & MySQL to run on a separate system from my main PC (XP).  first I installed as a desktop, then as a server, on separate partitions of an 8GB drive on an old Dell PC.  I did this because I needed a LAMP server.  I then installed the destop modules over the server to give the graphical interface.  I have got apache2, php5, mysql, phpmyadmin, etc. all running.  I could not get proftp working, and ended up using the one ubantu refer to in the page on setting up LAMP (vsftp?), creating symbolic links myself to the directory I have set up to ftp to for the development web stuff.  I need to push stuff across from dreamweaver on the PC, and don't want to use samba.

Anyway, I now find that this has all filled up the 4GB partition, and when I went to pull up the 4GB partition I originally set up for the desktop, using the gui, it asks for a mount point - obviously.  But, I really cannot remember how all that stuff worked anymore, and it's not the sort of thing to fiddle with really.  It defaults to /boot, but I seem to remember that in my unix days, the thing to do was to set up a directory, and mount to that.  Thing is, I would like to use it for /usr /home /var or whatever directories are likely to get filled up more quickly, leaving the core /etc /bin /lib behind.  My mind is a blank on all this.  If I mount it as /usr, how do I access the stuff in /usr and move it across?  Or is all this unnecessary on linux (/unix) these days?  Can I just mount it to / and it uses it as more space?  I'd rather have it done clean, rather than spreading files across partitions, but do I need to?  If I do, though, how on earth do I set it up and migrate the directory/ies across.

I've searched through the obvious pages, but can't see any guidance on this.  I am a bit concerned that it wanted to mount as /boot, and have set it to /, but don't really want to do a reboot and find it has messed the whole installation up and start again.

I am very pleased with ubuntu, and although it is still a bit frustrating, it is a real pleasure to work with.  I have avoided linux in the past because I simply have never had the time to mess about with it - and the 4 days I have had to take out of my PhD were hard to spare, but it has been well worth it.

I did find I had to do a lot of re-installation of the packages before I got the sequence and configuaration right - it certainly didn't work along the lines the ubuntu site gives for setting up a lamp in 15 minutes! Thanks to them for making this available - I looked at about 6 other types of linux, and only did this one because a friend recommended it - I really do like this version better than any I have seen before, and it feels almost as comfortable to me as SCO or HP-UX or straight SVR4.

Mish

---

### Post by T700 on 2006-07-18
Take a look at the Psychocat link in my sig.  Lots of information on partitioning, among other things.

Paul

---

### Post by MishMich on 2006-07-18
Thanks Paul,

I think the new /home is going to be the best solution, along with removing some unnecessary packages - as I can't resize the partition because of the way it was set up (no room either side).

Mish.

---

### Post by mejohnsn on 2006-07-18
> **T700 said:**
> Take a look at the Psychocat link in my sig.  Lots of information on partitioning, among other things.

Paul

Your Psychocat link is great! I don't regret the time spent reading it, even though it didn't quite answer my own outstanding partitioning questions, which arein another thread in this forum (Installation), titled "Installing Ubuntu for DualBoot WinXP machine w/ C: and D: Drives".

But if I am reading your Psychocat guide correctly, what I will need to do is resize /dev/hda5 smaller, and make at least one, and preferably two more partitions for Ubuntu's exclusive use. But then what will happen as hda5 is resized? Which of drives C: and D: will get shrunk? Or do I need to independently resize both hda3 and hda5?

Finally, I have to apologize in advance for the poor formatting of the Parted table output: I composed it offline, formatting with tabs. THen I discovered the hard way that the tabs are lost when cutting-and-pasting into the Forum's built-in editor](*,)

---

### Post by MishMich on 2006-07-18
Hi Paul,

thanks a lot, the new /home worked fine for the time being, and gave me plenty of room to grow for now.  As I decided to put that area on a different disk completely, it leaves me with more space to grow a couple of other directories onto their own filesystems by splitting the spare partition into two 2GB drives - maybe one for /www & a new one for /dev or something.  Great, easy to follow & no glitches - never was that easy on UX 10 years ago as I recall (memories of taking my life in my hands when doing this with old SCSII disks).

I am really sold on ubuntu - my 6/7 year old Dell PIII with under 400 MB RAM (now) runs faster than my 2 year old P4 with 500MB running XP.  I love the GNU interface much more than KDE, and having vi, sed, awk, etc. & a UX-feel under the hood of a tidy GUI makes this my dream system.  I hope I can find ways of contributing myself in the future.

Mish

---

### Post by MishMich on 2006-07-20
By the way, on the psychocats link - I did this again for the /usr dir, as I ran out of space v. quickly.  I repeated the steps as I had noted the first time - and it took me a while to figure out why I couldn't suid to root again.  NoSuid on the fstab file for a /usr mount is best avoided!

Mish

---

### Post by az on 2006-07-20
Unless you have a particular need to have several partitions, there is an advantage to putting everything on one partition, which is the default behaviour of the installer.

---

### Post by MishMich on 2006-08-10
I reinstalled, and other things also work much better now as well. Thanks.

---

