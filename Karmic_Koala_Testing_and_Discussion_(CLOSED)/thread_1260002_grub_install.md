---
title: "grub install"
date: 2009-09-07
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by oboedad55 on 2009-09-07
Hi, I want to try out the alpha 5 of Karmic and was wondering about the installation procedure. Does it have the same deal where you can hit "advanced" and not install grub? I like to roll my own.

Thanks,
Jon

---

### Post by dino99 on 2009-09-07
indeed

---

### Post by oboedad55 on 2009-09-07
> **dino99 said:**
> indeed

I like the answer.

Thanks.

---

### Post by dino99 on 2009-09-07
thanks,

as you, i want total control when i install a distro & karmic is designed the same way as previous release.

---

### Post by oboedad55 on 2009-09-07
> **dino99 said:**
> thanks,

as you, i want total control when i install a distro & karmic is designed the same way as previous release.

I had Mepis installed first a long time ago so I prefer to go in and modify the menu.lst there rather than install grub every time I try out a new distro.

---

### Post by VMC on 2009-09-07
Even if it didn't have that feature, you could just "roll your own" right after it. 

I had a similar problem with Fedora and ext4. It would not allow to install without have a /boot partition on ext3. After installed I promptly moved all files to the /boot of the root folder and deleted the /boot ext3 partition.

So far Ubuntu allows more flexibility. Although I am using karmic's grub2 just to get use to it. But even then I edit grub.cfg to my hearts content :)  ...like you said, I too like to "roll my own"

---

### Post by oboedad55 on 2009-09-07
> **VMC said:**
> Even if it didn't have that feature, you could just "roll your own" right after it. 

I had a similar problem with Fedora and ext4. It would not allow to install without have a /boot partition on ext3. After installed I promptly moved all files to the /boot of the root folder and deleted the /boot ext3 partition.

So far Ubuntu allows more flexibility. Although I am using karmic's grub2 just to get use to it. But even then I edit grub.cfg to my hearts content :)  ...like you said, I too like to "roll my own"

That's one feature of Ubuntu and other Debian based distributions that I particularly like. Others that I've tried automatically install grub leaving one no option not to install it. I think it might be better if in Ubuntu there was a clearer option with the grub install. I think a lot of folks, myself included, find this feature by accident. So, are you happy with the new grub? I've read horror stories and conflicting advice about editing the grub.cfg. Do you know if there's a good explanation somewhere for how to do this?

--Jon

---

### Post by VMC on 2009-09-07
> **oboedad55 said:**
> ... So, are you happy with the new grub? I've read horror stories and conflicting advice about editing the grub.cfg. Do you know if there's a good explanation somewhere for how to do this?

--Jon
I don't have any horrors stories regarding Grub2, it just takes some getting use to. It's the future, like UUID's replacing static devices were.

There several good reads about Grub2:
[Grub2 1.97]("https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD")
and
[Grub2 CLI mode]("http://members.iinet.net/~herman546/p20/GRUB2%20CLI%20Mode%20Commands.html#cli_loopback")
Also
[Grub2 Basics]("http://ubuntuforums.org/showthread.php?t=1195275")

---

### Post by dino99 on 2009-09-08
well, grub2 is experimental, beta status, and some surprises can happen !!!

---

### Post by taavikko on 2009-09-08
> **dino99 said:**
> well, grub2 is experimental, beta status, and some surprises can happen !!!

And it's been in development nearly a decade.

---

