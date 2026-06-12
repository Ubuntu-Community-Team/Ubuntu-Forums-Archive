---
title: "Which GRUB have I got?"
date: 2009-09-22
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by The Cog on 2009-09-22
I installed Karmic and it replaced my GRUB with GRUB 1.97. 

Reasons for thinking it's GRUB 1:
* It says GRUB 1.97
* Karmic isn't supposed to install GRUB2 if there's another Ubuntu there already, and I dual boot with Jaunty

Reasons for thinking it's GRUB2:
* It uses grub.cfg
* It didn't add my Jaunty to the boot choice list so maybe thought it was alone

So is it GRUB 1 or 2? If it's 1, how do I install GRUB2?

---

### Post by LKjell on 2009-09-22
You are using grub 2.

But to be sure you can
Run "grub-install -v" in a terminal. If it says 1.97 you have grub 2. Use that command to install grub 2. For example 

```
sudo grub-install /dev/sda
sudo update-grub
```

Be sure to check which device to install it on.

---

### Post by jocko on 2009-09-22
> **The Cog said:**
> I installed Karmic and it replaced my GRUB with GRUB 1.97. 

Reasons for thinking it's GRUB 1:
* It says GRUB 1.97
* Karmic isn't supposed to install GRUB2 if there's another Ubuntu there already, and I dual boot with Jaunty

Reasons for thinking it's GRUB2:
* It uses grub.cfg
* It didn't add my Jaunty to the boot choice list so maybe thought it was alone

So is it GRUB 1 or 2? If it's 1, how do I install GRUB2?
1.97 is grub2. Grub1 is 0.97.

---

### Post by The Cog on 2009-09-22
Thank you.

---

### Post by kansasnoob on 2009-09-22
> Karmic isn't supposed to install GRUB2 if there's another Ubuntu there already, and I dual boot with Jaunty

Is not true. If you upgrade a Jaunty w/legacy grub to Karmic you'll still have legacy grub.

If you do a fresh install of Karmic in any multi-boot arrangement you'll get grub 2.

I've played around enough to know that you can hand control back to grub legacy and chain-load to grub 2 from legacy grub, although that results in much, much slower boot time.

You can also revert from grub 2 to legacy grub if you wish, but I only suggest doing so if you're really proficient with legacy grub, that is installing and setting up legacy grub and creating/editing a menu.lst.

Of course, as always, you can click on "advanced" in the Ubiquity installer when it reviews your selected partitioning and installation info and choose not to install a boot-loader at all. Of course then you must add the proper entry to your existing boot-loader to boot Karmic.

I think grub 2 is going to be absolutely great! Right now it's just unfamiliar to most of us.

---

### Post by ranch hand on 2009-09-23
> **kansasnoob said:**
> Is not true. If you upgrade a Jaunty w/legacy grub to Karmic you'll still have legacy grub.

If you do a fresh install of Karmic in any multi-boot arrangement you'll get grub 2.

I've played around enough to know that you can hand control back to grub legacy and chain-load to grub 2 from legacy grub, although that results in much, much slower boot time.

You can also revert from grub 2 to legacy grub if you wish, but I only suggest doing so if you're really proficient with legacy grub, that is installing and setting up legacy grub and creating/editing a menu.lst.

Of course, as always, you can click on "advanced" in the Ubiquity installer when it reviews your selected partitioning and installation info and choose not to install a boot-loader at all. Of course then you must add the proper entry to your existing boot-loader to boot Karmic.

I think grub 2 is going to be absolutely great! Right now it's just unfamiliar to most of us.
I hope the OP reads and understands this.  Good post.

Grub2 is already pretty neat.  Os-prober still needs work.  It is FUN.

---

### Post by Starks on 2009-09-23
GRUB 2 is 1.97. GRUB 1 is 0.97.

---

### Post by sports fan Matt on 2009-09-23
Is the only way to get grub 2..to burn a latest alpha cd?

---

### Post by psyke83 on 2009-09-23
> **sox fan Matt said:**
> Is the only way to get grub 2..to burn a latest alpha cd?

[No.]("https://wiki.ubuntu.com/KernelTeam/Grub2Testing")

---

### Post by sports fan Matt on 2009-09-24
no issues upgrading grub here at all.

---

### Post by dadedo123 on 2009-09-24
mine says "(GNU GRUB 1.97~beta3)" Is GRUB2 still in beta? Will my update manager upload GRUB?

---

### Post by ranch hand on 2009-09-24
Yes grub2 is still beta.  We started with 1.96.

Synaptic would be the place to find grub-legacy if that is what you are asking about.

---

