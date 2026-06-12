---
title: "Hoary Hedgehog upgrade."
date: 2007-06-21
forum: Installation &amp; Upgrades
---

### Post by dannycab on 2007-06-21
My lab is sufficiently behind the times and we haven't upgraded any of our linux boxes in a long time. I recently upgraded a few boxes (Dapper -> Feisty) and all went well. I have one last machine, the one that has all the data (of course), which is running Hoary! How can I get it to Breezy and then to Dapper safely? Thanks for any help.

---

### Post by Soybean on 2007-06-21
Well... I'm not sure what your second step should be, but your first step should definitely be "back up the data somewhere else." I mean, like, a *really thorough* backup -- the kind of backup that you fully expect to use, not one of those "just in case of disaster" backups. ;)

---

### Post by dannycab on 2007-06-21
Thanks Soybean. I had starting doing that this morning. It'll be done this afternoon.

---

### Post by Soybean on 2007-06-22
Hmmm... no more responses, eh? I guess there aren't a lot of Ubuntu historians here. ;) 

Honestly, if you're confident in your data backup, I'd recommend a format and clean install of Feisty. It will be faster (the alternative being essentially 4 full OS installs), and less error-prone. The 4-stage update would be more interesting as an exercise, but if you actually need it to work, the clean install seems like your best bet.

---

### Post by dannycab on 2007-06-22
That's what I think I am going to have to do. First, I have to dump everything to another drive. Thanks. Would you recommend Feisty or Dapper with LTS?

---

### Post by tgalati4 on 2007-06-22
If it's a file server then Dapper should be fine.  If it's a workstation machine using lots of different applications, then Feisty would be more current.

---

### Post by Soybean on 2007-06-22
Oh, yes, sorry... I guess I just assumed you were going Feisty because you mentioned it with the other computers. I'm keeping Dapper on all of my server systems at least until there's another LTS release. Your lab seems to be the sort of place where people like to get something working and then leave it that way, so Dapper is likely a good choice for your server too, unless Feisty has some new feature that you need/want.

---

