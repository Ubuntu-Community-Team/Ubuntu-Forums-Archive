---
title: "Password problem"
date: 2005-06-07
forum: Installation &amp; Upgrades
---

### Post by gustavo.leite on 2005-06-07
When I was installing ubuntu, I got a problem to set up users and passwords, it was not acepting any king of user I tryed. So, I just moved on thinking that I could just setup later, using the root password.. well, I guess I was wrong.. If what I readed is right, there is not a default password for root...

any idea? I got a linux installed with no users seted up...
how can I fix it?

---

### Post by DJ_Max on 2005-06-07
[QUOTE=gustavo.leite]When I was installing ubuntu, I got a problem to set up users and passwords, it was not acepting any king of user I tryed. So, I just moved on thinking that I could just setup later, using the root password.. well, I guess I was wrong.. If what I readed is right, there is not a default password for root...

any idea? I got a linux installed with no users seted up...
how can I fix it?[/QUOTE]
 This has been discussed hundreds of times... But anyway, Ubuntu doesn't come with a root account. You use your intial user password to gain root privileges. Use 'sudo'.
Example
```

sudo useradd namehere

```

---

### Post by gustavo.leite on 2005-06-07
yeah, now I know that ubuntu doesn't come with a root password..  but what if I didn't set up ANY user account on the instalation process? Honestly when I tryed to set up a user account, it fails sayind that could find that user name... So, as I know, I have no users intalled..

Maybe I could use the live CD to edit the file with the users name and paswords..  or something like that.. does anybody knows if that is possible? and by the way, where can i find this file?

---

