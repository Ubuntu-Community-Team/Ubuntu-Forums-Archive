---
title: "reinstall ubuntu and save my data"
date: 2005-08-23
forum: Installation &amp; Upgrades
---

### Post by raakken on 2005-08-23
hi
I've manage to **** up my system and I need it up and running before the weekend. I had plans to reinstall ubuntu over the old, and keep my /home.
Will I get an option under installation, where i get asdked if I want to keep my /home?
And, will it do just that, keep my /home without loosing it??
thanks

---

### Post by henriette_holm on 2005-08-23
Hi.
When you get to this point:

[http://shots.osdir.com/slideshows/slideshow.php?release=305&slide=9](http://shots.osdir.com/slideshows/slideshow.php?release=305&slide=9)

choose "Manually edit partition table". Make sure that you don't thouch the /home partition. It should be possible for you to format only /.
Remember, BACKUP before you start.

-Henriette

---

### Post by c0rderr0y on 2005-08-23
hmm i think your home directory has to be set up as a different parition....

---

### Post by raakken on 2005-08-23
hi and thanks for the answares
but here's the thing, I can't back.up thye data. Thats why I'm re installing to get to the data and then take backup of it...
And I need it before the weekend...
I had som kernel problems(see topic: kernel panic), and no I can't start x....
I see all the data, but it's difficult to move it from there, to the other disk(it ain't partisioned and the disk ain't big enough...) so I have to move some data around my family network, witch I can't from terminal...

What I need is someone who have done this before, and who have done it successful :wink:

---

### Post by henriette_holm on 2005-08-23
[QUOTE=c0rderr0y]hmm i think your home directory has to be set up as a different parition....[/QUOTE]

Ok, minor detail  ;-) 
I didn't think about making that clear - sorry

Do you have /home on a separate partition?

-Henriette

---

### Post by c0rderr0y on 2005-08-23
i would try using a the live version or knoppix 3.9 boot with that then transfer over the network that way  :-P

---

### Post by raakken on 2005-08-23
henriette: my /home was made by ubuntu... It tokk the space it needed for root/swap and the rest was /home

corderroy: I used the ubuntulive-cd to mount my system before, but I can't now for some reason.. bad mountpoint/superblock or somthing somthing
I'm tired and I want an easy way out of this
I can't loose my data, but I want to simply put the ubuntu cd in and change my /home dir, to another name, then the ubuntu will make another and keep my old home untoutched...

---

### Post by c0rderr0y on 2005-08-23
hmm have you tried knoppix 3.9? i think there are some recovery tools for partitions on that im not sure im not at home at the moment....

---

### Post by raakken on 2005-08-24
kind of fixed it... installed ubuntu onmn another hd and moved my data over from there:) time consuming, but safe!
safe as i debian;)

---

