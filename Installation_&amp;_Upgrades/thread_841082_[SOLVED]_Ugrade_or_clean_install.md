---
title: "[SOLVED] Ugrade or clean install?"
date: 2008-06-26
forum: Installation &amp; Upgrades
---

### Post by juky on 2008-06-26
Hello folks,

I would like to upgrade my dual boot machine (XP + 7.10 Gutsy) to 8.04 Hardy Heron. 

So here goes the question (what would be wiser):

To do the upgrade, or a clean install?

Thanks in advance,
juky

---

### Post by iaculallad on 2008-06-26
Doing an Ubuntu upgrade would be better since you can keep your settings and installed programs. 
Doing the fresh install would require you more time on installing applications and configuring settings. But this option will always work since its a clean installation.

---

### Post by juky on 2008-06-26
Thanks for quick response. But still have a doubt what to do. 

Suppose I would do a clean install. What would be a best way to do it? Boot a DVD, format linux partition and then do a clean install or some other way?

Thanks
juky

---

### Post by iaculallad on 2008-06-26
> **juky said:**
> Thanks for quick response. But still have a doubt what to do. 

Suppose I would do a clean install. What would be a best way to do it? Boot a DVD, format linux partition and then do a clean install or some other way?

Thanks
juky

That will do it, but be sure to backup all your important data (on your home directory maybe) before doing the format thing.

---

### Post by cdtech on 2008-06-26
I agree, doing an upgrade means you get to keep your current settings and programs.

If you want to upgrade using GUI use the following command:
update-manager -c

---

### Post by juky on 2008-06-26
> **cdtech said:**
> I agree, doing an upgrade means you get to keep your current settings and programs.

If you want to upgrade using GUI use the following command:
update-manager -c

Thanks everyone for the support. Guess I will try an upgrade first via update-manager -c command.

Just  a short question regarding this command: does it use a install DVD as a source or an internet?

If it doesn't work, I can always do a clean install.

Of course, backup first!

---

### Post by iaculallad on 2008-06-26
> **juky said:**
> Thanks everyone for the support. Guess I will try an upgrade first via update-manager -c command.

Just  a short question regarding this command: does it use a install DVD as a source or an internet?

If it doesn't work, I can always do a clean install.

Of course, backup first!

The NET.

---

### Post by juky on 2008-06-26
> **iaculallad said:**
> The NET.

Is there a way to do it via local files on a HDD or from cd/dvd?

Sorry for bothering so much.....

---

### Post by iaculallad on 2008-06-26
> **juky said:**
> Is there a way to do it via local files on a HDD or from cd/dvd?

Sorry for bothering so much.....

Try to get/download Hardy's Alternate CD.

---

### Post by mikjp on 2008-06-26
If you have /home on a separate partition, do the fresh install. If you don't have a separate /home, either

a) backup everything, repeartition, give system a separate /home, and do the fresh install

or

b) upgrade

Usually one encounters all kinds of strange behaviour after upgrade.

Greetings,

m

---

### Post by juky on 2008-06-27
Hello all, 

will try upgrade and/or clean install and let you know how it went.

Cheers,
juky

---

### Post by juky on 2008-07-05
Guys,

if I do a clean install (reformatting linux partition), wwhat will happen with grub? Note that I have also an WinXP as dual boot.

Thanks
juky

---

### Post by juky on 2008-07-07
Final note:

I have tried both upgrade and clean install.

After upgrade, screen res. was messed up and could not fixed it,in general did not work as I have expected. Did not notice more issues cause I have decided to do a clean install (reformat linux partition during install). It went perfectly!

The only thing I had to do after install was to change the driver for R8187 wireless chipset (aircrack version) and install ATI drivers via Envy. All went flawlessly and now I am happy ubuntu user :-)

Cheers,
juky

---

