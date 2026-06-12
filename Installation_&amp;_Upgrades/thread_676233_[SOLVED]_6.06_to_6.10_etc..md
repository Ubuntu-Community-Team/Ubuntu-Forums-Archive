---
title: "[SOLVED] 6.06 to 6.10 etc."
date: 2008-01-23
forum: Installation &amp; Upgrades
---

### Post by joshdudeha on 2008-01-23
I want to upgrade from Dapper Drake to Edgy Eft
But when running the command 
'gksu "update-manager -c"'
I get the following error message:
 "  warnings.warn("apt API not stable yet", FutureWarning)
"
It will not notify me that i can have an upgrade.

Can someone please elaborate?
Thanksx

---

### Post by Jonne on 2008-01-23
I'm not sure how it works, but I think you can only upgrade to Hardy that way (which is released in April).

what happens if you run update-manager -p?

---

### Post by joshdudeha on 2008-01-23
ooer when i did that command
"  warnings.warn("apt API not stable yet", FutureWarning)
" came up, but software updates opened saying i could upgrade to 8.04
but ive heard its not wise to upgrade just like that
What shall i do?

---

### Post by joshdudeha on 2008-01-23
Oh!
I've got to go now
¬_¬
Be back tomorrow afternoon
thanks for helping atm Jonne

---

### Post by zvacet on 2008-01-24
> but ive heard its not wise to upgrade just like that

In general it is truth,but this is something else.For the first time you can upgrade from one LTS to other,so you can do it this time.Do it in april when 8.0.4 will be released.If you want to upgrade to Edgy do it with alternate CD.In my opinion it is better for you to wait until april and then upgrade to next LTS.

---

### Post by joshdudeha on 2008-01-24
Ah!
So normally this would be frowned upon?
But because 8.04 is a LTS, I should jump the whole upgrade process and upgrade straight to that?!
Bring on April!!
Thanks, please reply.

"warnings.warn("apt API not stable yet", FutureWarning)
" But what does that mean?!
If I upgrade in April, it won't damage my system will it?
Thanks again

---

### Post by zvacet on 2008-01-24
> But because 8.04 is a LTS, I should jump the whole upgrade process and upgrade straight to that?!

Yes,and like I said this is for a first time,because Hardy will be second LTS and you will be able to skip all upgrades and go directly to Hardy.

---

### Post by joshdudeha on 2008-01-24
Ah that's great!
Thanks
but can someone please explain what is meant by "warnings.warn("apt API not stable yet", FutureWarning)"?
Just a bit cautious about that.
Thanks again ^_^ joshie

---

### Post by Jonne on 2008-01-24
It probably means that updating is planned for the future, but it doesn't work now.

---

### Post by joshdudeha on 2008-01-24
Ok, thanks
You've all been a great help, can't wait for April!

---

### Post by joshdudeha on 2008-01-24
hmm one **more** question (:
when i upgrade to 8.04 in april
will it keep my home folder?
and all of the current installations?
Thanks again
gtg though
Byexx

---

### Post by zvacet on 2008-01-24
Make separate home partition if you don´t have one allready.Follow [this](http://www.psychocats.net/ubuntu/separatehome) and you should be fine.

---

### Post by joshdudeha on 2008-01-25
hmm
i kinda have no partition space left :/

---

### Post by joshdudeha on 2008-01-25
i can't upgrade then?

---

### Post by Jonne on 2008-01-25
Yes you can. Upgrading will work fine. Just make sure you back up your stuff to make sure (you should always do that anyway). All your application settings and files are in one place (/home/yourusername/), so it's easy to back up.

I've upgraded my box from edgy over feisty to gutsy without significant (*) problems and without needing to reinstall.

* the upgrade to gutsy b0rked my sound output, but that was relatively easy to fix

---

### Post by joshdudeha on 2008-01-25
Oh thank god for that, Ill just put my home onto some CD's
As long as it doesn't bugger up my installation what with Dual Boot, 
Thanks !

---

