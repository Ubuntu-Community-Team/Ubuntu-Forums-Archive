---
title: "Hibernate = Lock Screen"
date: 2007-05-10
forum: Installation &amp; Upgrades
---

### Post by roboa1983 on 2007-05-10
Hi
I recently updated from 6.06 all the way to Feisty Fawn (passing through Edgy Eft). I had the same problem a lot of people were facing (tty not loading, etc etc). I managed to work this problem out thanks to a post here at ubuntu forums.
However, when I tried to put hibernate for the first time, it directly shut down. Now, for some reason, it has changed and all it does is lock the screen.
I have no idea why this is happening, help is greatly appreciated...

---

### Post by digitalramble on 2007-05-11
I've got the same issue here, any suggestions?  Suspend seems to work fine, hibernate does not, it goes to the lock screen.

I've got a swap file, not partition, and I've checked the swap file, the system knows about it and is using it.

First I used the synaptic package manager and installed the package "hibernate"

Then I edited the /grub/boot/menu.lst file to include resume=(swapfile)
where i put the actual path name and file name of the swapfile for (swapfile)

I don't think the resume is the problem since it doesn't even seem to get to the point where it saves anything off (eg, directly to lock screen).

This is a Gateway laptop, the 200X series...oldie but goldie.  Haven't tried to get hibernate to work before.

---

### Post by roboa1983 on 2007-05-12
> **digitalramble said:**
> 
I've got a swap file, not partition, and I've checked the swap file, the system knows about it and is using it.

First I used the synaptic package manager and installed the package "hibernate"

Then I edited the /grub/boot/menu.lst file to include resume=(swapfile)
where i put the actual path name and file name of the swapfile for (swapfile)


I downloaded hibernate, and when I tried to run it on the terminal, the next output showed:
```

roberto@copilco:~$ sudo hibernate
/bin/echo: write error: Cannot allocate memory
```

Could you specifically tell me where you changed that in the /boot/grub/menu.lst file? Has it worked for you yet?

---

### Post by digitalramble on 2007-05-14
I really don't know about that hibernate message.  My guess would be it looked for a swap partition or file.  You can go to the systems monitor and see if it mentions any swap usage, if not then I'd guess that's the problem.  If you search on swap partition (more fiddly) or swap file (easier) creation, you'll find posts that address how to do this.

Just in case it wasn't clear from my message, hibernate goes to the lock screen for me, too.  I have not resolved it, and I described what I have done so far in order for someone else to have a better idea of what I have already tried or not tried :-)  Hopefully some solution will come up, although I'll continue to poke at it as I get time.  Since Suspend works for me, I can use that in the interim.

Oh, as for where I added that resume command in the menu.lst, I searched for the term "resume" and added it under the comment that contained it. I don't get the impression it's important where it goes in the file though.

---

### Post by roboa1983 on 2007-06-12
Hi
I started this thread a month or so ago.
I have been trying to fix the problem that hibernate does not work. What happens is that it locks the screen.
Digitalramble posted that it might be problems with the swap, but I really haven't gotten around solving the problem.
Is this a general problem of 7.04?

Thanks for the help

---

### Post by i60t on 2007-08-29
Would be really interesting to solve this Problem - on Laptop it works, or?
- so why not for my Workstation..? :(

best,
i60t

---

### Post by roboa1983 on 2007-08-29
Hi

> **i60t said:**
> Would be really interesting to solve this Problem - on Laptop it works, or?
- so why not for my Workstation..? :(

best,
i60t

Are you saying it doesn't work on your Workstation, but it does on your laptop? I haven't hibernated on my workstation for a while...

thanks for the interest

Roberto

---

