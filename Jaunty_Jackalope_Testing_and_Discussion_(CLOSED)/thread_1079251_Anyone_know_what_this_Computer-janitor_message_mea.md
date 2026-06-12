---
title: "Anyone know what this Computer-janitor message means?"
date: 2009-02-24
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by mdurham on 2009-02-24
(fstab mount option realtime missing)
"The 'realtime' mount option is missing for filesystem mounted at /"

It gives this message for all my mounted drives. Obviosly something is wrong with my fstab, but what?

> LABEL=P2	 	/ ext3 rw,errors=remount-ro 0 1

LABEL=P1	 	/media/sda1 vfat rw,users,gid=users,umask=0002,uid=1000,utf8=true, exec,dev,auto 0 	0

LABEL=P4	 	/media/sda4 ext3 defaults 0 0

LABEL=P5	 	/media/sda5 ext3 defaults 0 0

LABEL=P6	 	/media/sda6 ext3 defaults 0 0

etc...


---

### Post by ssam on 2009-02-24
change to

```

LABEL=P2 / ext3 rw,errors=remount-ro,relatime 0 1

```

it will make disk reads faster. have a read of [http://kerneltrap.org/node/14148](http://kerneltrap.org/node/14148) or [http://lwn.net/Articles/244829/](http://lwn.net/Articles/244829/)

ps: i m sure i have read that mounting by label is not recommended. the default in ubuntu is to mount by uuid.

---

### Post by obscur156 on 2009-02-24
Hi,i just want to say that i dont understand Computer-janitor... 

The only thing it wants to clean is all the packages that are not native from ubuntu.So it only shows packages that i downloaded from getdeb or whatever other sites.For me its not cruft or something that should be remove so i have uninstalled it. 

If you want something to clean your system without risking to screw your installation you can try BLEACHBIT its in the repositorie or have a look before.  

[http://bleachbit.sourceforge.net/]("http://bleachbit.sourceforge.net/") 

Best regards.  ;)

---

### Post by mdurham on 2009-02-25
Thanks for the info ssam.
I also agree with obscur156, what is the point? I only tried Computer-janitor to see what it did.
Cheers, Mike

---

