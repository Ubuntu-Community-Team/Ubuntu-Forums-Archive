---
title: "Clean install from 9.04 keeping home folder?"
date: 2010-05-29
forum: Installation &amp; Upgrades
---

### Post by jjdelc on 2010-05-29
I have 9.04 in my laptop and I want to make a clean install of Lynx.

My home partition is sda7 (ext4), so in the partition step during the install I'm telling the installer to use the partition as ext4 but don't format it (I'm explicitly checking sda6 as / mount point and set to format as ext4).

On the next step I see disabled options regarding the access to my home folder and "Require my password to log in and decrypt my home folder" is checked.

My current home partition is not an encrypted partition, so I am not sure of what will happen. I just want it to mount it and access it as Ext4, not encrypt it.

I also have a Private folder in my home partition, what will happen to it? Will I be able to mount it afterwards?

---

### Post by darkod on 2010-05-29
In that next step, can you select another option? I don't clearly remember how the screen looks like.

---

### Post by darkod on 2010-05-29
Got it. Doesn't it look like this? Can you select Require my password to log in option?

---

### Post by jjdelc on 2010-05-29
Yes, but the options are disabled and the last one is checked.

---

### Post by linfidel on 2010-05-29
I think you should do an upgrade in your situation.  It's basically the same thing you are trying to do - it will replace most all the system files that are not in your home directory.  It will prompt you about some /etc files, which you can choose to replace (be careful, replace is not the default).  Most configuration is in your home directory, though.

FWIW, I've done both upgrades and new installs a lot for the last few versions, and the upgrades usually work out better than new installs.

But, if you have enough room, I'd recommend keeping your old home directory separate, and create a fresh one for the install.  Then, you can mount the old home directory, and copy over any configuration files you want, a few at a time, and check to make sure nothing breaks.

---

### Post by jjdelc on 2010-05-30
Thanks, At the end I did a clean regular install on a single partition, now I'm about to set up manually my home partition on fstab.

---

### Post by linfidel on 2010-05-30
> **jjdelc said:**
> Thanks, At the end I did a clean regular install on a single partition, now I'm about to set up manually my home partition on fstab.Well, good luck - you may need it.  You can't assume that throwing away the new home directory will work, as it's possible the upgrade might have a different format, and it would know how to translate your settings.  

I don't know if this is the case, but unless you know for sure, assuming is dangerous.

---

