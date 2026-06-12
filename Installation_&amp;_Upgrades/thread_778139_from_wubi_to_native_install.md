---
title: "from wubi to native install"
date: 2008-05-01
forum: Installation &amp; Upgrades
---

### Post by acecase on 2008-05-01
Hello,
 I installed ubuntu 8 on my office box a while back via wubi (wubi right?) I think that's what it's called. Anyway, I nearly always run ubuntu and only run windows for my helpdesk software so I want to somehow migrate ubuntu and all of its settings etc to a native install and run windows in a virtual box.

I have thought of a couple possibilities but I wanted to get some of your ideas on the best/easiest way to do this before I start.
My first idea is to use gparted to cut out the first 10GB or so of my NTFS partition and a swap then dd my ubuntu partition to that and install grub and edit /etc/fstab to compensate. Then reclaim the remainder of the drive with gparted after i boot into ubuntu native. (any problems with that?)

Another idea was to create some type of script that would bring the system back to exactly where it is now (I have no idea if that is even possible but I'm betting it is) Then I could just install ubuntu native using the entire disk and run this script to set the system up the way it is now. Is there a way to do this ?

Thanks for the input.

EDIT: It hit me just after posting this that, since performance is great as is, my main concern is getting more drive space for ubuntu so I can install windows in a virtual machine. Is there a way to just resize the "image" that wubi created for ubuntu when I installed?

---

