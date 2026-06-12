---
title: "specify partition manually"
date: 2011-04-07
forum: Installation &amp; Upgrades
---

### Post by asd_zxc on 2011-04-07
I uninstall by deleting the partition that Ubuntu was on (tried googling for the proper way but did not find any) and I got the grub rescue error.

I do not have a win XP install disc with me for fixmbr. Theoretically speaking, reinstalling Ubuntu should get me the option to boot into windows again.

I had to choose specify partitions manually (advanced) else it's going to  take space out of my D:\\ for the install alongside other os option.

I got
> No root file system is defined. Please correct this from the partitioning menu.after I add the free partition and proceed to click install now.

Tried googling for the solution again but the first page search are full of people asking the same question but in a complete different scenario.

What should I do now?

---

### Post by Derek Karpinski on 2011-04-07
[http://www.linuxbsdos.com/2010/10/12/ubuntu-10-10-manual-disk-partitioning-guide/](http://www.linuxbsdos.com/2010/10/12/ubuntu-10-10-manual-disk-partitioning-guide/)
 
This helped me out.  Just make sure you're partitioning the right drive!

---

### Post by asd_zxc on 2011-04-07
> **Derek Karpinski said:**
> [http://www.linuxbsdos.com/2010/10/12/ubuntu-10-10-manual-disk-partitioning-guide/](http://www.linuxbsdos.com/2010/10/12/ubuntu-10-10-manual-disk-partitioning-guide/)
 
This helped me out.  Just make sure you're partitioning the right drive!
For the guide, the author recommend creating 4 partitions but from my memory the default (my very first installation) Ubuntu setting created 2 only. Please correct me supposedly I'm wrong.

In the case I'm right, I'm guessing the first and third partition by the author are the 'extras'? My very first installation that takes disk space out from my C:\\ is around 15GB.

Anybody?

EDIT: With the 15GB space left to install Ubuntu, I can't seem to get past after creating partition 2 in the guide. My remaining free disk space is rendered as unusable.

---

### Post by Dutch70 on 2011-04-07
That's not a very good guide really.

All you need is 2, you need a "/" aka "root" partition (that's where Ubuntu lives), and a "swap" partition, which is like a page file.

---

### Post by asd_zxc on 2011-04-07
> **Dutch70 said:**
> That's not a very good guide really.

All you need is 2, you need a "/" aka "root" partition (that's where Ubuntu lives), and a "swap" partition, which is like a page file.
Greetings Dutch70,

Can I still follow the setting (primary, beginning, ext4, swap area) by the guide for the 2 required partitions? With 15GB free disk space how much should I allocate to each of them?

Thank you.

---

### Post by Dutch70 on 2011-04-07
I don't know about the primary, beginning stuff. I don't know your hard drive set up. 

You're swap should be equal to the size of your physical RAM. The rest for "/" (root).

---

### Post by Derek Karpinski on 2011-04-07
I'm new to Ubuntu and Linux so if my advice was bad, I appologize.
 
But I do have to ask:
 
Why would setting up separate partitions be a bad or wrong thing for /boot, /, /home, and swap?
 
I didn't completely follow the guide as far as primary and logical.  I set up my / as a primary partition, and all others as logical inside the primary.
 
I was under the assumption that upgrading in the future to a new release will be easier to manage if my /home was on a different partition.  That way I could not touch /home at all.
 
:confused:

---

### Post by Dutch70 on 2011-04-07
Hi Derek,
Your advice was not bad at all, I didn't mean for it to sound like that. 
As far as you being new, we all were at one time, and helping others is one of the best ways to learn.

It's just that there is no need for a /boot & /home in his case. His 15GB partition is too small to really worry about a /home & /boot is just not necessary for him. 

Also, the main reason I said the guide wasn't very good is mostly because of the size of the swap partition he advised. He said 4-5GB I think, and Swap is not a one size fits all kind of deal. That would be overkill for some, and not enough for others. Kind of made me frown on the entire guide. 

Also, it sounds like you have a very good set up on your machine. That is how mine is set up. You done good!

---

### Post by asd_zxc on 2011-04-07
> **Dutch70 said:**
> I don't know about the primary, beginning stuff. I don't know your hard drive set up. 

You're swap should be equal to the size of your physical RAM. The rest for "/" (root).
I went ahead and install Ubuntu before you reply but I would still like to double check and confirm.

I only installed Ubuntu once and this is the second installation. The first time I went with the 'install alongside other os' option.

The 2nd installation (current) which I'm trying to get the default setting from the first, was those by the guide correct?

Thanks.

---

### Post by Dutch70 on 2011-04-07
Yes, the guide is correct. I also went back and looked and noticed that he didn't advise 4-5GB for swap, he just said that he normally uses 4-5GB. Other than that and the /boot partition, the guide is fine. In fact, if you need a /boot partition and you have about 4-5GB of physical RAM, then the guide is great. :)

---

### Post by asd_zxc on 2011-04-07
Dutch70 do you have any idea why guide like the one Derek Karpinski posted is not being easily found on ubuntu official help? I read a bunch of useless definitions before I decided to signup at the forum.

---

### Post by Dutch70 on 2011-04-07
There are many, many good guides out there, they can't all be mentioned on Ubuntu help. Here is one of the better sites though, imho.
[[COLOR="RoyalBlue"]http://www.psychocats.net/ubuntu/installseparatehome[/COLOR]]("http://www.psychocats.net/ubuntu/installseparatehome")

Ps, I should be more careful how I state things in the future.

---

