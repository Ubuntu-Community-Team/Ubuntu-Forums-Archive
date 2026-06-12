---
title: "update problems"
date: 2011-02-02
forum: Installation &amp; Upgrades
---

### Post by red40y on 2011-02-02
i updated my laptop after not using it for a few weeks and when prompted to restart, i get a white crash screen on boot after restart.  
i have ubuntu 10.04 64 bit installed on my laptop with wubi

---

### Post by bcbc on 2011-02-03
See the [Wubi megathread]("http://ubuntuforums.org/showthread.php?t=1639198") for problem shooting Wubi installs. 

I haven't heard of a 'white screen'. Is it when you select Ubuntu - or just whenever the computer boots? Is there any text, error message?

---

### Post by red40y on 2011-02-04
after i choose ubuntu on boot( there's win7 and ubuntu) and after i select from grub i get a white screen. no tex just a white screen. 
 i had a problem with an update in the past, you would have to look at my older posts to see the details.

---

### Post by bcbc on 2011-02-04
> **red40y said:**
> after i choose ubuntu on boot( there's win7 and ubuntu) and after i select from grub i get a white screen. no tex just a white screen. 
 i had a problem with an update in the past, you would have to look at my older posts to see the details.

What happens when you hit 'e' on the entry in grub - then delete 'quiet splash' and then hit CTRL+X to boot.

When that freezes, note what it says on the screen and then write it back here.

Also mention computer brand/model/graphics card.

---

### Post by red40y on 2011-02-04
the laptop is a toshiba satellite l305d with a amd ati radion chip-set. 
but the oddest thing happened, i went to do what you sayd and every thing booted normal w/o having to do anything. strange...

---

### Post by bcbc on 2011-02-04
I have an ATI radeon x1300 and I find with 10.04 - every now and then it freezes on bootup. When I'm booting 10.04 installs on it, I just use 'nomodeset' as a boot option and it seems to prevent this problem.

[This post]("http://ubuntuforums.org/showthread.php?t=1613132") explains how to add nomodeset as a permanent boot option (ignore the fact the the poster added "(not for wubi)" - it is the same for wubi).

---

### Post by red40y on 2011-02-05
i will do that, thank you for the help. :popcorn:

---

