---
title: "Error During Update"
date: 2006-06-09
forum: Installation &amp; Upgrades
---

### Post by frup on 2006-06-09
In the preparing to update part of the update manager it begins to try download files... starts of around 60kbps... when it gets to around 60 it starts again, slowing down to like 409bps. restarts again and then gives me this message:
 
Failed to fetch [http://theli.free.fr/packages/breezy/./Packages.gz](http://theli.free.fr/packages/breezy/./Packages.gz) 404 Not Found
Failed to fetch [http://koti.mbnet.fi/~ots/ubuntu/breezy/Packages.gz](http://koti.mbnet.fi/~ots/ubuntu/breezy/Packages.gz) 404 Not Found
Failed to fetch [http://koti.mbnet.fi/~ots/ubuntu/breezy/Sources.gz](http://koti.mbnet.fi/~ots/ubuntu/breezy/Sources.gz) 404 Not Found

:(

---

### Post by pellgarlic on 2006-06-09
change the first one in your sources.list to: 

http://theli.free.fr/packages/**dapper**

the other two, i can't figure out - seems like they're totally gone. you need to find an alternative place to get whatever it was you were trying to get from there.

both of these are third-party (non-default) repositories, and the first has moved the breezy  directory (renamed it "breezy-obsolete" or something). the other seems to have gone altogether. perhaps they have just got a new location?


TIP: if you are having trouble with repositories, you can always copy and paste the repository address into your browser address bar, and check it out that way - if you get a 404 error, or another probelm, try deleting the last section of the address, and keep going until you get something. 

so, if 
"http://theli.free.fr/packages/breezy"    doesn't work, try 
"http://theli.free.fr/packages",             then 
"http://theli.free.fr". 

have a look around, and see where the probelme is occurring - for this example, the "breezy" directory had been renamed - that's why you're getting a 404 error. change it say "dapper" and it *should* work. ;)

---

### Post by frup on 2006-06-09
would it be save just to delete those line then?

synaptic is giving me this message too
W: Couldn't stat source package list [http://koti.mbnet.fi](http://koti.mbnet.fi) breezy/ Packages (/var/lib/apt/lists/koti.mbnet.fi_%7eots_ubuntu_breezy_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://theli.free.fr](http://theli.free.fr) ./ Packages (/var/lib/apt/lists/theli.free.fr_packages_dapper_._Packages) - stat (2 No such file or directory)

same things i think?
i've updated the other line

---

### Post by pellgarlic on 2006-06-09
[QUOTE=frup]would it be save just to delete those line then?[/QUOTE]

safe? yes. those repositories are not needed for the ubuntu base system.

but better to just comment them out by adding a "#" (without the quote marks) at the start of those lines, in case you want to try fixing them at some point. if you comment them out, synaptic will just ignore them. if you delete them, and you want to add them back at some point, you'll have more trouble than just having to delete a "#" or two. :)

a consequence of commenting out those lines will be that whatever program(s) you installed from those places will not be able to be updated. if you know what program(s) are affected, you could try googling for an alternative repository for them - maybe they have just moved. if you are unconcerned about not being able to update those programs, and they work properly, there will be no other consequence.

---

### Post by frup on 2006-06-09
i have no idea what program theyre for. 
i went ahead and unticked them in synaptic... it worked and now im on dapper :D

---

