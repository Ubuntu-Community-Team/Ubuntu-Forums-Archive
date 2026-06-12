---
title: "Clone Ubuntu to multiple PC's?"
date: 2006-11-04
forum: Installation &amp; Upgrades
---

### Post by valnar on 2006-11-04
I would like to clone an installation of Ubuntu to multiple identical computers (same hardware, same model).  In the Windows world, I could use Ghost or Acronis for this, and I believe I could do the same for Linux.

In Windows, I know I would need to change the SID, PC name and user accounts.  I could then migrate some user desktop settings between them if I had it layed out in a certain fashion.

What do I need to change or do in Linux to accomplish the same thing?  I don't want to simply run the Ubuntu install on multiple computers at the same time if I can avoid it, because I've customized some preferences and apt-get installed other software already.

Is there a specific procedure for doing this?  Does anyone have a list of /etc/ files that need to be changed per PC so that they don't conflict with each other?  SSH keys?  Name on PC?  Other settings?

Thanks,
Robert

---

### Post by ajgreeny on 2006-11-04
Have a look at *partimage,* that should do the trick.

---

### Post by valnar on 2006-11-04
Huh?  Partimage doesn't do anything I want.

The question is what do I need to change AFTER I make an image or copy to another machine, to make it unique enough from the original?

Robert

---

### Post by BungaMan on 2006-11-04
I'm no expert at this but what I would ask is how unique do they have to be?  What exactly do you mean with not conflicting?  If you mean network wise then all that is required is a different computer name with dhcp and off you go.

---

### Post by valnar on 2006-11-04
Yah, that's what I meant.  But doesn't each machine also create .SSH keys that are unique?  Anything equivalent to the SID or something else?  Changing the name is easy enough, and yep, I'll use DHCP.  But I don't know enough about the inner workings of Linux to know what else I need to change.

Robert

---

### Post by BungaMan on 2006-11-12
I don't see how that could be conflicting.  That key is only used to set up an encrypted channel.  Not to authenticate a user or computer.  And if SID means session id's on websites... they have a timeout (usually 30 minutes) after which they become invalid due to no activities so don't worry about it either :)

---

### Post by aysiu on 2006-11-12
If you need a guide to PartImage, here's one:
[http://www.psychocats.net/ubuntu/partimage](http://www.psychocats.net/ubuntu/partimage)

You can also use the *dd* command to make exact copies of partitions and drives.

---

### Post by valnar on 2006-11-12
OK, here's an easier way of asking the question.

If I were to take two identical PC's - same hardware - and install Ubuntu on them each with a different PC name, what exact files would be different?  Is everyone telling me only a single file out of the entire multigigabyte installation would be different?  Cuz in Windows, that's certainly not true.  :confused: 

-Robert

---

### Post by louieb on 2006-11-12
I believe most of the people that frequent this forum are Linux hobbyist. Probably not many know much about enterprise computing using Linux. If you look at the Ubuntu home page you will see that Canonical offers commercial support services. Or if you insist on finding out all you can for free check out the Linux-Enterprise forum at [http://www.linuxquestions.org](http://www.linuxquestions.org).

---

