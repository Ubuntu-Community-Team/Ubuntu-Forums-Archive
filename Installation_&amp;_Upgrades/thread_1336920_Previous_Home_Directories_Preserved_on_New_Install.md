---
title: "Previous Home Directories Preserved on New Installation?"
date: 2009-11-25
forum: Installation &amp; Upgrades
---

### Post by AleatoricConsonance on 2009-11-25
Hi!

I'm going to do a fresh install of 9.10 over my previous 9.04 install.

I have all of my user directories on a separate partition to make this easier. Given this scenario, I clearly do **not** format the partition so my user data is preserved.

During the install process, when I am prompted create an account, what would happen if I used my original name?

For example, if my name is "joe", and I typed in "joe" as a user name, would it wipe out the original "joe" user directory, and replace with a new, empty one? Or would it recognise that there's an existing directory named "joe" and just use it without wiping out anything?

It's not clear to me from the documentation and help screens.

Thanks.

---

### Post by AleatoricConsonance on 2009-11-25
Bump.

Surely not a difficult question? Is there some other place I might be able to seek an answer?

---

### Post by audiomick on 2009-11-25
Hi,
I'm surprised you haven't had an answer to this, it's easy.
When you say all your user directories, do you mean /home?

If so, all you have to do is mount that without formatting during the install during the partitioning stage. To do this, you need to choose the "manual" option.

If you don't mean /home, it is worth creating a partition for /home in the new install, for just this purpose. You can also mount any other pre-existing partition at mount point of your choice.


You should use exactly the same user name as you had in the last install, and I think it should be the same password, although I am not sure of that.

---

### Post by AleatoricConsonance on 2009-11-25
> **audiomick said:**
> 
You should use exactly the same user name as you had in the last install, and I think it should be the same password, although I am not sure of that.

Thank you! That's great.

I have /home on it's own partition, and I always choose the "manual" option. I was just concerned that if "/home/joe" existed already, then creating user "joe" on the reinstall will wipe away the existing directory/data.

---

### Post by audiomick on 2009-11-25
> **AleatoricConsonance said:**
> I was just concerned that if "/home/joe" existed already, then creating user "joe" on the reinstall will wipe away the existing directory/data.

No, it's fine. I've done it a couple of times. If all works well, the computer comes back just like it was (once you have all your prgorams back on), but in the new Ubuntu version.

---

### Post by doas777 on 2009-11-25
agreed. you won't have any trouble if you jsut tell the partitioner that you want to mount the home partit as /home (and don't format). you will find on first login that many of your settings are already applied. it's great.

---

### Post by AleatoricConsonance on 2009-11-25
Thank you everyone for your help.

---

