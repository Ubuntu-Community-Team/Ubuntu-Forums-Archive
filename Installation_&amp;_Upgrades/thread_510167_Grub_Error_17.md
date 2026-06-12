---
title: "Grub Error 17"
date: 2007-07-26
forum: Installation &amp; Upgrades
---

### Post by feisty_fawn on 2007-07-26
Hi. I've recently been using Ubuntu 7.04.[http://ubuntuforums.org/images/smilies/star.png](http://ubuntuforums.org/images/smilies/star.png)
:KS I installed it a few weeks back, and fully formated the disk on installation. 

Now i've tried to get back to windows, i've sued the system restore cd's that i got with the computer, after doing the restore and on boot it get

grub 1.5
please wait
error 17

How can i fix this?
[http://ubuntuforums.org/images/smilies/confused.gif](http://ubuntuforums.org/images/smilies/confused.gif)
:confused:
I have an acer aspire 3610

---

### Post by rbmorse on 2007-07-26
Apparently, when you applied the system restore CD to your machine, it removed/erased/overwrote your Ubuntu installation. It's gone. This s typical of the way "restore CDs" work.

Error 17 is GRUB's (the bootloader) way of telling you it can't find the selected operating system. 

The real question is why the system restore CD didn't also overwrite GRUB (the bootloader installed by Ubuntu) with the bootloader that came on the machine when new.

---

### Post by feisty_fawn on 2007-07-27
Thanks. To be honest, i'm pretty annoyed by that. 

The thing is, I was considering upgrading to Vista, so if I purchase a Vista cd (not the upgrade edition) and install that, will it replace Grub and everything will load correctly?

---

### Post by mikewhatever on 2007-07-27
[Super Grub Disk]("http://supergrub.forjamari.linex.org/") can restore the boot loader for XP, there is no need for Vista monster.

---

### Post by Gremlinzzz on 2007-07-27
Error17 : "Invalid device requested"
This error is returned if a device string is recognizable but does not fall under the other device errors.

---

### Post by Pumalite on 2007-07-27
From Super Grub:

17 : Cannot mount selected partition
    This error is returned if the partition requested exists, but the filesystem type cannot be recognized by GRUB.

---

### Post by Gremlinzzz on 2007-07-27
[http://www.uruk.org/orig-grub/errors.html#stage1_5](http://www.uruk.org/orig-grub/errors.html#stage1_5)

---

### Post by Pumalite on 2007-07-27
> **Gremlinzzz said:**
> [http://www.uruk.org/orig-grub/errors.html#stage1_5](http://www.uruk.org/orig-grub/errors.html#stage1_5)

Thanks for the link.

---

### Post by logos34 on 2007-07-27
> **mikewhatever said:**
> [Super Grub Disk]("http://supergrub.forjamari.linex.org/") can restore the boot loader for XP, there is no need for Vista monster.

Yes, that's what you can do in the meantime. (contrary to what you think, you'll actually be 'downgrading' to Vista, it's such a bloated beast).

---

### Post by Pumalite on 2007-07-27
> **logos34 said:**
> Yes, that's what you can do in the meantime. (contrary to what you think, you'll actually be 'downgrading' to Vista, it's such a bloated beast).

Not only that but is full of holes and is a fraud on top.

---

### Post by logos34 on 2007-07-27
> **Pumalite said:**
> Not only that but is full of holes and is a fraud on top.

Amen.

---

### Post by Herman on 2007-07-28
> Quote:[quote]
                                                                      Originally Posted by **Gremlinzzz**                     [[IMG]http://ubuntuforums.org/images/uf/buttons/viewpost.gif[/IMG]]("http://ubuntuforums.org/showthread.php?p=3092974#post3092974")                 
                 *[http://www.uruk.org/orig-grub/errors.html#stage1_5](http://www.uruk.org/orig-grub/errors.html#stage1_5)*Thanks for the link.[/quote]:) Hey, wait! That link is good for [Erich Boleyn's]("http://www.uruk.org/%7Eerich/") original GRUB, version 0.5. 

We're using [GNU GRUB]("http://www.gnu.org/software/grub/") in Ubuntu now, which has been developed from Erich Boleyn's GRUB.

Some of the error messages are the same, but some of them are out of date now, and may be misleading.

Here's the link for the [GNU/GRUB manual]("http://www.gnu.org/software/grub/manual/grub.html"), that's the one we *should *be looking in these days! :)

Regards, Herman :)

EDIT: I don't know anything about Vista...

---

### Post by Pumalite on 2007-07-28
' Hey, wait! That link is good for Erich Boleyn's original GRUB, version 0.5.

We're using GNU GRUB in Ubuntu now, which has been developed from Erich Boleyn's GRUB.

Some of the error messages are the same, but some of them are out of date now, and may be misleading.

Here's the link for the GNU/GRUB manual, that's the one we should be looking in these days!

Regards, Herman '

Thanks, Herman

Regards, Puma

---

