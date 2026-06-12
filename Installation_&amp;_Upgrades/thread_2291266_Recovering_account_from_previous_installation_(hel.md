---
title: "Recovering account from previous installation (help!)"
date: 2015-08-18
forum: Installation &amp; Upgrades
---

### Post by hueyafrosamurai on 2015-08-18
So  I've had a dual boot system, windows 7 and Ubuntu 12.04 for a while  now. Been having some issues with windows, so a friend helped me try to  fix it. He accidentally then messed up the boot loader (I think?), so  then couldn't access linux at all.
  So after more messing around, he re-installed windows and Ubuntu, but  this time we upgraded Ubuntu to 14.04. It seemed all fine, except, I  was at class when he upgraded it, so I wasn't around for one error he  made.
  He named my home/user/account wrong. It's usually "Palmares", but he  named it "Palmero". So then I thought perhaps I have lost that account  and all the associated files. But then just as a desperate experiment, I  attempted to create an account from system settings (within the Palmero  account) with the right name (and password). It worked. To a degree. I  knew it was the account I was looking for, from the account image (a  wolf). However, when I then tried to log in with that account, it would  briefly seem work, then return to the login screen. Changing the two  profiles between admin and standard made no different.
  And this is where I'm stuck....
  Can someome help me? I don't want to lose my files, and I know it's  my fault for not backing them up in the first place... I trusted my  friend a bit too much, and I guess too lazy to backup in the long run  anyway... But yeah, the files are surely still there, I just need to  figure out how to get to them. Perhaps I need to re-install the upgrade?  Or?
  Cheers in advance!

---

### Post by hueyafrosamurai on 2015-08-19
PS Apologies, didn't realise swearing wasn't allowed here. Haven't posted here in a few years eh...

---

### Post by steeldriver on 2015-08-19
It may just be a matter of UIDs/GIDs - log in to the account that works, then post the outputs of

```

ls -l /home

awk -F: '$3>999' /etc/passwd

```

or use the `id` command to find the user and group information IF you know the actual usernames, rather than just the display names

---

### Post by Bucky Ball on 2015-08-19
You can also boot from live media (usb or disk), Try Ubuntu, and back up your files before going much further. If you didn't back them up previously, do it now, if they're there. :)

---

### Post by hueyafrosamurai on 2015-08-24
> **steeldriver said:**
> It may just be a matter of UIDs/GIDs - log in to the account that works, then post the outputs of

```

ls -l /home

awk -F: '$3>999' /etc/passwd

```

or use the `id` command to find the user and group information IF you know the actual usernames, rather than just the display names

drwxr-xr-x  34 palmares palmares  4096 Aug 20  2014 guest
drwxr-xr-x 170 palmero  palmero  32768 Jul 30 21:32 palmares
drwxr-xr-x  18 palmero  palmero   4096 Aug 24 14:01 palmero


and

nobody:x:65534:65534:nobody:/nonexistent:/usr/sbin/nologin
palmero:x:1000:1000:Palmero:/home/palmero:/bin/bash
palmares:x:1001:1001:Palmares,,,:/home/palmares:/bin/bash


I vaguely figured out the first bit before, but I'm a n00b, I don't really know how to use this info to help me. Any ideas?

EDIT: I'm not sure how to have that second lot of info without the smilies... Soz!

---

### Post by hueyafrosamurai on 2015-08-24
[QUOTE=Bucky Ball]You can also boot from live media (usb or disk), Try Ubuntu, and back up your files before going much further. If you didn't back them up previously, do it now, if they're there. :)[/QUOTE]


I guess this is part of the problem, that I believe my files are still there somewhere, but I'm not sure how to access them. If I could access my old admin account from previous installation, I feel they would still be there. However, it there a way for me to access them to back them up from my current situation if I am not able to recover my previous admin account?

Cheers!

---

### Post by steeldriver on 2015-08-24
Well the 'palmeres' home directory seems to still be there, and is owned by 'palmero'

So you should be able to log in as the new user 'palmero' and simply browse to '/home/palmeres' to access your old files

---

### Post by hueyafrosamurai on 2015-08-25
[QUOTE=steeldriver]Well the 'palmeres' home directory seems to still be there, and is owned by 'palmero'

So you should be able to log in as the new user 'palmero' and simply browse to '/home/palmeres' to access your old files[/QUOTE]

Thank you so much!

As you said, I've been able to find all the files in that location. Infact, since they are all there, there's no real need for me to move them right? Though, I guess it wouldn't hurt to back them up, which would have saved me all this stress in the first place.

Thanks again!

---

### Post by Bucky Ball on 2015-08-25
> **hueyafrosamurai said:**
> Though, I guess it wouldn't hurt to back them up, which would have saved me all this stress in the first place.



You got that right! Always keep good backups and I suggest you do one now if you're not already doing it or have done it. :)

See the first link in my signature and please mark the thread as solved. Good luck.

---

