---
title: "Startup applications accidentally deleted"
date: 2010-04-10
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by TaTaE on 2010-04-10
Is there a possibility to restore some startup applications that I accidentally removed ?

I think there should be a "Restore defaults" button there.

---

### Post by ranch hand on 2010-04-10
I would try apt-get install if you actually deleted them.  If not there is an add button.  Just put them back.

---

### Post by wilee-nilee on 2010-04-10
> **TaTaE said:**
> Is there a possibility to restore some startup applications that I accidentally removed ?

I think there should be a "Restore defaults" button there.

You can use the add function the command is the important part. So hit add then the browse then file in home then user then bin or sbin and the command for many programs are there just click on the one you want then open then name it, and your set, if the command is correct.

Also if any of the ones you removed are still in the menu you can right click the menu hit edit menus then right click on the program then properties and the command you need is there.

And as ranch hand suggests make sure the programs are actually installed to begin with, it is hard to ascertain exactly what went down. ;)

---

### Post by TaTaE on 2010-04-10
Thanks for the feedback, guys. Of course anyone can use the Add button in the Startup Applications window, but what can you do when you simply don't remember what you deleted ?

I can tell when a custom entry made by me is missing, but you cannot expect me to learn by heart all of the default entries, so that I can tell when a certain entry is missing.

Maybe they should make them unremovable, disabling the remove button for the system default entries OR they better provide a "Restore defaults" button.

---

### Post by SevenMachines on 2010-04-10
hi, to 'reset' autostart entries try removing 
~/.config/autostart

you could also copy all entries (i think!) from 
/etc/xdg/autostart/
to 
~/.config/autostart
if you dont want to delete any custom entries in you might have

---

### Post by TaTaE on 2010-04-10
Thanks a lot, buddy. Your hint worked.
Nevertheless, there is place for interface improvement as I said earlier.

---

### Post by SevenMachines on 2010-04-10
> **TaTaE said:**
> Thanks a lot, buddy. Your hint worked.
Nevertheless, there is place for interface improvement as I said earlier.
i agree, theres probably a few areas a 'Restore Defaults' functionality in some way or other would be useful

---

### Post by wilee-nilee on 2010-04-10
> **TaTaE said:**
> Thanks a lot, buddy. Your hint worked.
Nevertheless, there is place for interface improvement as I said earlier.

You know it seems strange that somebody who wants to replace wait they don't remember wants a better interface.

All you should of done in the first place is tick the programs off, this was a useless thread.

Everybody has opinions and they are most always crucial to them alone in some way or another.

---

### Post by SevenMachines on 2010-04-10
Certainly not a useless thread! In the lesser case if only a few people have this problem then they will be able to solve it easier if the information is available, which is very important if you are one of those people, something i've needed many, many times.
In the more general case, interface usability issues are always something worth being discussed, politely (as was the case here :) ), frightening amounts of money are spent on research, both academic and commercial on exactly this kind of thing, here you can get it for free!

---

### Post by TaTaE on 2010-04-10
Well, we certainly must help Ubuntu, even by pointing out even small issues, because they can draw the developers' attention and can be easily fixed, as the case was here.

Believe me, please, that I can't learn by heart all those things listed at "Startup Applications". And have no intention to.

Cheers,

:)



TaTaE
Join Date: Feb 2006

---

### Post by QLee on 2010-04-10
[QUOTE=TaTaE]
Believe me, please, that I can't learn by heart all those things listed at "Startup Applications". And have no intention to.[/QUOTE]

Gosh no, I don't think anyone would expect things from memory. I will offer a small piece of advice for the next time you are testing a beta. Keep yourself a written system log at hand and record any changes you make explicitly, then, if you need to roll them back you will have a record of what you did to break the system and a way to restore it, that is, if you choose to test without a backup to roll back to.

---

### Post by cariboo on 2010-04-10
When modifying configuration files, whether by hand, or through a gui, make a backup of the configuration file first, before making any changes. Even Microsoft suggest this when modifying the registry.

---

