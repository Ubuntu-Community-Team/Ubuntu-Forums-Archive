---
title: "Change in the way GRUB handles 'savedefault'"
date: 2007-11-29
forum: Installation &amp; Upgrades
---

### Post by coady on 2007-11-29
Hi
I am often playing around with partitions which means I find myself looking at GRUB and the 'menu.lst' quite a lot. I have noticed that there has been a change to GRUB and the way it handles 'savedefault'. It appears that GRUB no longer adds a line 'savedefault' to each bootable entry, like this:```
title
root
kernel
initrd
**savedefault**
boot
```
The following is now included in GRUB's automatic setup```
## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false
```I have looked at the following link which seems to be related:
[Update-grub does not add savedefault anymore]("https://bugs.launchpad.net/ubuntu/+source/grub/+bug/131858")

However, I am still confused now about how to use 'savedefault'. Should I set a global option (i.e. 'savedefault=true') and delete the entries where I have manually added 'savedefault', or do I leave the global option set to false and add 'savedefault' to each entry?

Also, do I need to add the 'boot' line, which is no longer added automatically. It is not a big problem but I would appreciate some advice on this. Thanks for any help.
coady

---

### Post by logos34 on 2007-11-29
The default in my Feisty menu.lst is "true" while it's "false" in my x64 Gutsy.  I prefer manually adding it to entries.

No, you don't need the 'boot'--it's implied in menu entres.
[http://www.gnu.org/software/grub/manual/grub.html#boot](http://www.gnu.org/software/grub/manual/grub.html#boot)

---

### Post by meierfra on 2007-11-29
> However, I am still confused now about how to use 'savedefault'. Should I set a global option (i.e. 'savedefault=true') and delete the entries where I have manually added 'savedefault', or do I leave the global option set to false and add 'savedefault' to each entry?


Neither. If you want to use "savedefault" for  your ubuntu items , use "#savedefault=true" and do NOT delete the manual added "savedefault"s


"#savedefault=true" is an instruction for the program "update-grub". It is not used by "grub" itself.  If you use "savedefault=false" all the "savedefault"  in your ubuntu entries will disappear during the next kernel  update.

And if you set  "#savedefault=true" but delete the "savedefault" from the ubuntu entries, grub won't use the "savedefault" option for the ubuntu entries. (But during  the next kernel update  "savedefault" will be added to all your ubuntu entries)


What is "default" set to? To you use "default 0" or "default saved"?

---

### Post by logos34 on 2007-11-29
> **meierfra said:**
> #savedefault=true" is an instruction for the program "update-grub". It is not used by "grub" itself.  If you use "savedefault=false" all the "savedefault"  in your ubuntu entries will disappear during the next kernel  update.

And if you set  "#savedefault=true" but delete the "savedefault" from the ubuntu entries, grub won't use the "savedefault" option for the ubuntu entries. (But during  the next kernel update  "savedefault" will be added to all your ubuntu entries)

hmm...so that's how it works (I guess the reason I didn't notice the savedefaults getting stripped out on my gutsy install last time I ran update-grub was that I'm now using '0' instead of 'saved'.  But I should have seen the change all the same)

---

