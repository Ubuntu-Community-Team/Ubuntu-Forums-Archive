---
title: "seperate partition for /home?"
date: 2007-05-20
forum: Installation &amp; Upgrades
---

### Post by Mets on 2007-05-20
hey guys,

I've decided to go with a fresh, clean install of Feisty Fawn instead of just upgrading, but I recently heard that it's a good idea to have two separate partitions - one for /home and another for the rest of the file system.  The  idea is, my friend said, was that you could reinstall the operating system as much as you wanted, but you'd have all of your files safe on the /home partition.  Sounds reasonable I suppose.

I was just wondering though - how does this work, and is this a good idea?  If you were to reinstall Ubuntu at some later time in the future, I'm assuming you'd just have to reinstall the programs you were using and all of the config files in your /home would be reused, saving setup time?

I currently dual boot with windows also, but I find myself using Ubuntu a lot more, which is why I'm considering taking this approach and doing a fresh install.  Thanks for the help.

---

### Post by Titus A Duxass on 2007-05-20
Having a separate /home is the way to go.

Then you can reinstall at will. Just remember, during the reinstall when you get to partitioning, do not format the /home partition.

I usually have 10-12gb for /, a swap of 2gb and the rest (approx. 140gb) as /home.

This allowed me to update from breezy through to feisty without data loss.

Remember to back-up your Thunderbird mailbox and address book (if applicable) and firefox favourites.

---

### Post by tact on 2007-05-20
Hey there...  I did as you have done when I upgraded from edgy to fiesty.  Did a full clean install and separated out /home to its own partition.

I gave "/" 6GB and (weeks later) there is still 3GB free.  I have 1.5GB RAM so gave away another 2GB for Swap.  The rest to /home

It proved its worth.  After a few days I had tinkered too much and needed to reinstall the OS.  You do have to be careful choosing the right partitions so that "/" installs back to the same place, format that partition - but not the /home partition.

Yes all the configs for programs remained intact.  Had to reinstall applications but it was very cool to fire them up the first time after reinstallation and find all the settings and data just as it was before reinstallation.

---

### Post by Mets on 2007-05-20
great thanks a lot guys, I guess it's worth it.  I'll give it a go as soon as I get some free time.  Thanks again!

---

