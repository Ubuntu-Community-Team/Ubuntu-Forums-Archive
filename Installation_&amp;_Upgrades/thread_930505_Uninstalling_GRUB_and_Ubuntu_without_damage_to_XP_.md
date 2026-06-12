---
title: "Uninstalling GRUB and Ubuntu without damage to XP and Vista"
date: 2008-09-26
forum: Installation &amp; Upgrades
---

### Post by jjmedem on 2008-09-26
Hello people,

I've been searching for a while but haven't found a step to step guide to remove grub and ubuntu from my pc. does anyone have a link?

I tried going into the recovery console of the XP boot disc. however, it asks me what windows installation i want to launch and it gives me 2 options: C:WINDOWS and E:Windows (do notice the different in capitalized letters). Which one of those is Vista and which is XP? I guess XP should be C: according to the disc right? now once i do that, can I enter fixmbr after that? and how do i restore the vista bootloader so that I have xp and vista bootable at the same time?

thx in advance,

JJ

P.S. I liked Ubuntu but I just didn't use it anymore so I need it removed :)

---

### Post by Elfy on 2008-09-26
If XP was installed first I would guess that it is the one on C: but couldn't be sure. Perhaps you'd be better of dealing with the vista bootloader rather than xp. 

You might be better using easybcd bootloader, never used it myself but it should be able to deal with both wins.

As far  as I am aware it takes over the boot - [http://neosmart.net/dl.php?id=1](http://neosmart.net/dl.php?id=1)

---

### Post by jjmedem on 2008-09-26
> **forestpixie said:**
> If XP was installed first I would guess that it is the one on C: but couldn't be sure. Perhaps you'd be better of dealing with the vista bootloader rather than xp. 

You might be better using easybcd bootloader, never used it myself but it should be able to deal with both wins.

As far  as I am aware it takes over the boot - [http://neosmart.net/dl.php?id=1](http://neosmart.net/dl.php?id=1)

normally, yes, except that Vista calls itself C even when it's Z, so yeah, but I guess the xp disc goes around that, I'm going to try that program u mentioned, thx

---

### Post by Elfy on 2008-09-26
> yes, except that Vista calls itself C that's clever then - unfortunately I have very little experience with vista.

But I've seen easybcd mentioned here for sorting vista booting.

Sorry can't be of more help.

---

### Post by jjmedem on 2008-09-26
that's no problem, the program is already a very good idea, I know the program but I didn't think of it, I'm going to look on their forum and ask the question there to see if easybcd can restore the windows boatlooader so that grub isnt in front of it :)

---

### Post by caljohnsmith on 2008-09-26
If you run "fixmbr" from your Windows XP disk (no need to specify drive letters), then it puts a Windows boot loader in your MBR; all the Windows boot loader does is "chain load" or boot whichever partition on the HDD is marked as "active" or has its boot flag set on. So if I were you, I would go ahead and run fixmbr, and then if you still have your Ubuntu Live CD, you could run Ubuntu's partition editor (gparted) and use that to specify your Vista partition as the "active" one so that it gets booted on start up. After that, you can use that EasyBCD program that forestpixie mentioned to configure your Vista boot loader to boot either XP or Vista, and you should finally be finished.

If you need more details/info, let me know, I'm just giving a general outline of the idea at this point. :)

---

### Post by jjmedem on 2008-09-26
it worked, I got rid of the grub boatloader by using fixmbr on supposedly the winXP partition (based on the capitalizing of the windows folders in xp and vista, xp's is fully capitalized and vista's only the first letter is capitalized)

thx for the help guys, now i just need to expand the winvi partition to use all the space i have for ubuntu :)

---

