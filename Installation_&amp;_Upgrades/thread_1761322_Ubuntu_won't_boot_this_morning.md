---
title: "Ubuntu won't boot this morning"
date: 2011-05-18
forum: Installation &amp; Upgrades
---

### Post by eekfonky on 2011-05-18
I turned on my computer this morning and it's stuck at the purple boot up screen before login. WTF! Please help

I'm running 11.04 64 bit

---

### Post by Rubi1200 on 2011-05-18
Hi,
could you please provide some more details. Did you shutdown normally prior to this? Have you applied any updates/added software recently?

What are the specifications, especially graphics card?

Thanks.

---

### Post by eekfonky on 2011-05-18
I am using on board graphics Intel 9xxx. I installed the latest updates last night and this morning it won't boot. Can I use a live CD/USB to recover it or is there a solution to try to install more updates from today? Please help

---

### Post by Rubi1200 on 2011-05-18
I think the best idea right now is to use the LiveCD/USB to boot the computer and rescue any important data just in case.

While on the live medium, please download and run the boot info script so we can take a look if this is a booting issue:

```
wget -O boot_info_script.sh 'http://bootinfoscript.git.sourceforge.net/git/gitweb.cgi?p=bootinfoscript/bootinfoscript;a=blob_plain;f=boot_info_script.sh;hb=HEAD'
```

Once downloaded, follow the rest of the instructions found in the link at the bottom of my post please.

Thanks.

---

