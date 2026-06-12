---
title: "can't do admin after fresh install"
date: 2005-08-07
forum: Installation &amp; Upgrades
---

### Post by Tux on 2005-08-07
I just installed Ubuntu 5.04, which apparently went fine.
However, I cannot run any of the maintenance progams under the System;Admin menu.  After I enter the password (either that of my personal account or the root password), after a long time an alert pops up with (for example):
"Failed to run network-admin: Child terminated with 1 status."

I find nothing in the logs under /var/log .

Same under the Applications;System tools;Root Terminal menu:
"Failed to run /usr/bin/x-termical-emulator: Child terminated with 1 status."

I can open a normal terminal screen from Applications;System Tools, and do su to become root.  However, I wouldn't like to poke around any config files manually.

Anyone have an idea what is going on?

---

### Post by Tux on 2005-08-08
[QUOTE=Tux]I just installed Ubuntu 5.04, which apparently went fine.
However, I cannot run any of the maintenance progams under the System;Admin menu.  After I enter the password (either that of my personal account or the root password), after a long time an alert pops up with (for example):
"Failed to run network-admin: Child terminated with 1 status."
[/QUOTE]

For the record: apparently my login user had not been configured as a sudo-er.  I repaired by hand and now this usr can run the GUI admin tools.

---

### Post by ITrainDogs on 2005-08-09
I am having the same problem could you please post what you did to fix. ](*,) 

Thanks

---

### Post by ITrainDogs on 2005-08-09
I have added my user account to the sudo group-did not help

I edited  /etc/sudoers/ and added the following to the end of the file:  system_username	ALL=(ALL) ALL

That did not help

I have read documentation but find nothing on this.

Anyone have an idea

---

### Post by grahamwhiteman on 2005-09-21
I modified the /etc/sudoer file using visudo -f sudoers adding the following line after:

root   ALL=(ALL) ALL
bill   ALL=(ALL) ALL

Then it all worked... 
Strange, anyone know why?

---

### Post by Björn on 2005-10-08
No, i have no idea, because it did'nt work for me :( Tryed to reeinstall the whole system but it didnt work either, if you want to know, i have win xp home installed in another partition, and if it's to any help (thoght it might be) i am using shadow passwords(what it is, i have not a clue actually ;P). thanks for any help :)

---

