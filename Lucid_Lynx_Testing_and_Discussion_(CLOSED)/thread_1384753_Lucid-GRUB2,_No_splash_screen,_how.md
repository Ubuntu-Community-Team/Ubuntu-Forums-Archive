---
title: "Lucid-GRUB2, No splash screen, how?"
date: 2010-01-18
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by emarkay on 2010-01-18
This is what I have in : /boot/grub/grub.cfg.

GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet"
GRUB_CMDLINE_LINUX=""

Which one is it, or do I need to add a line or two?

---

### Post by vishalrao on 2010-01-18
GRUB_CMDLINE_LINUX_DEFAULT="quiet **splash**" 

That is what I have by default, so add that bit and run sudo update-grub ?

You may then need to look at other issues with plymouth etc if you still dont see the boot splash.

---

### Post by cariboo on 2010-01-18
Have a look [here]("http://ubuntuforums.org/showthread.php?t=1371288"). It might be worth your while to have a look through this sub-forum, as most of your questions have been asked and answered. I know the forum search function isn't that great, but is is useful to find what you are looking for.

---

### Post by emarkay on 2010-01-18
> **cariboo907 said:**
> Have a look [here]("http://ubuntuforums.org/showthread.php?t=1371288"). It might be worth your while to have a look through this sub-forum, as most of your questions have been asked and answered. I know the forum search function isn't that great, but is is useful to find what you are looking for.

Thanks - that's a mighty big thread there.

I'll bet this particular Q will be asked a lot in the coming months, so how about a quick answer?  :)

---

### Post by ranch hand on 2010-01-19
Unfortunately the shortest answer is to read that thread.  There are a number of things that can cause your problem that we have encountered sith different hardware or just different days as things change.

Like Grub2, last time around, the documentation is lagging and folks are just making it up as we go.  Documentation will probably come out of this.  Right now you will have to read there or ask some one take a lot of time to do it for you.

---

### Post by emarkay on 2010-01-19
> **ranch hand said:**
> Unfortunately the shortest answer is to read that thread.  There are a number of things that can cause your problem that we have encountered sith different hardware or just different days as things change.

Like Grub2, last time around, the documentation is lagging and folks are just making it up as we go.  Documentation will probably come out of this.  Right now you will have to read there or ask some one take a lot of time to do it for you.


Thanks, a great and appropriate answer.  I appreciate the sincerity.  Will do some investigating and hopefully get an answer; will post results.

BTW, does this have anything to do with "Plymouth"?

---

### Post by ranch hand on 2010-01-19
Yes it is all about plymouth.  That is where your initial splash screen comes from.

The default screen should be a Ubuntu circle logo and the Ubuntu text logo on a black screen.

As you are having trouble with plymouth you are probably just getting a black screen untill the login screen.

Activating one of the other themes may help.  At least you can check your plymouth files and see if thay are all there.

---

