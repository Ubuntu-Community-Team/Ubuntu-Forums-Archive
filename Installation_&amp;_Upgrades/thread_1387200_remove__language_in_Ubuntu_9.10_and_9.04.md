---
title: "remove  language in Ubuntu 9.10 and 9.04"
date: 2010-01-21
forum: Installation &amp; Upgrades
---

### Post by Costas100 on 2010-01-21
My normal update came up with a security update for Thai language. I am not using Thai anywhere so I tried to delete the two files (libthai-data and libthaiO) using synaptic. The answer came back that the system will also delete almost half of my computer, such as:
**adobe-flashplugin, alarm-clock, avidemux, avidemux-plugins, childplay, compriz-gnome, abiword and a zillion other things.** So I canceled the delete and came here to search for help but found nothing yet.
Any help will be appreciated, otherwise I either have to accept the update or keep un-marking it for ever.
Thank you all
Costas
PS: I have Ubuntu 9.04 in another computer and the same thing happened there

Addendum: When I checked under System/Administration/Language support and then Language/Install-Remove languages I only have two languages marked up: English and Greek and they work fine. There are also many many more languages in the table, all unmarked. Good this be simply a bug???

---

### Post by jripple on 2010-01-22
I have exactly the same question.  Hopefully someone will provide an answer.
:D:D:D

---

### Post by damonO on 2010-01-23
see this post to remove the libraries:
[http://ubuntuforums.org/showpost.php?p=1482380&postcount=2](http://ubuntuforums.org/showpost.php?p=1482380&postcount=2)
note: step 2 (dpkg --configure localepurge) of this appears to auto-run on installation, so if you get an error on this step, don't worry about it.


i found that this did not remove the entries / dependencies in the package manager, so they still show up as needing to be updated. to work around this:

[LIST]
[*]go to synaptec package manager
[*]filter by upgradeable
[*]select the libthai
[*]go to edit: lock version
[*]repeat for any other language packs
[/LIST]

---

### Post by Costas100 on 2010-01-23
> **damonO said:**
> .....
i found that this did not remove the entries / dependencies in the package manager, so they still show up as needing to be updated. to work around this:

[LIST]
[*]go to synaptec package manager
[*]filter by upgradeable
[*]select the libthai
[*]go to edit: lock version
[*]repeat for any other language packs
[/LIST]

Thank you damonO the filter and lock version worked fine. The two language packs have disappeared and nothing else was deleted. Only in ubuntu 9.04 the lock version command is under Package and not Edit.
Thank's a lot
Costas
This is now solved.

---

### Post by nikkkko on 2010-02-10
Hi,

A similar problem here in that I have just about every language pack installed after an upgrade, except that the language pack installation also appears to be corrupt.

localepurge does nothing and removing 400 odd language libraries from synaptic is going to take a very long time.  Any suggestions?

Thanks,

Nick

---

### Post by nikkkko on 2010-02-10
Scratch that.  My installation is in French and localepurge does work, bien sûr. However, something is not right somewhere because 
 
Système>Administration>Prise en charge des langues 

(don't know what that is in English but it's the language administration thing), hangs.

---

