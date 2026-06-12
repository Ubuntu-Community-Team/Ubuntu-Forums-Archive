---
title: "Upgrade Edgy to feisty"
date: 2007-03-01
forum: Installation &amp; Upgrades
---

### Post by stchman on 2007-03-01
Hello all, i have a laptop with Edgy on it right now.  I downloaded Herd 4 of Feisty and the wireless portion works.  I am going to wait for Feisty (April 07) and the re-install on my laptop.

My question is when Feisty is released should I wipe the drive and do a fresh re-install or should (or can) I just upgrade from Edgy to Feisty.  Which would be the better route.

Thanks

---

### Post by Jonne on 2007-03-01
If you have your home directory on a seperate partition, i think it's safe to install from the cd (so you have a 'clean' slate).

But if you don't just upgrade it when Ubuntu tells you it's available, it should work ok.

---

### Post by stchman on 2007-03-01
> **Jonne said:**
> If you have your home directory on a seperate partition, i think it's safe to install from the cd (so you have a 'clean' slate).

But if you don't just upgrade it when Ubuntu tells you it's available, it should work ok.

I periodically backup everything on my /home/bob folder so that is not an issue.  So what you are saying is that when Feisty come available Ubuntu will prompt me to update?  If so that is awesome.  I see that your profile says you are a Dapper user, did Dapper tell you to upgrade to Edgy.

Also I am going to convert over to Ubuntu here very soon for everyday tasks.  I will keep my windows machine for playing games and such.  I find surfing the net with Ubuntu just as nice as with Windows except that Ubuntu linux seems far more resistant to viruses/spyware and such.  Also is there a way to convert your Thunderbird email to evolution?

Thanks

---

### Post by stchman on 2007-03-01
It looks as though you can type type following command:

gksu "update-manager -c -d"

and this will upgrade you to the latest distro.

---

### Post by Jonne on 2007-03-01
Actually, i use Edgy. I forgot to update my profile ;).

Ubuntu will indeed notify you, and if it doesn't you can start system>administration>update manager , and there will be a button to upgrade.

---

### Post by stchman on 2007-03-01
> **Jonne said:**
> Actually, i use Edgy. I forgot to update my profile ;).

Ubuntu will indeed notify you, and if it doesn't you can start system>administration>update manager , and there will be a button to upgrade.

Excellent, it seems to be a more automated process.  I feel when linux gets driver installation down to an easy process Windows watch out.

---

### Post by pkslot on 2007-03-03
Can i use the gksu "update-manager -c -d if mount the image of feisty and set the reposetory to read from the "cd"?

I just downloaded the image yesterday, and dont want to delete anything on my harddrive. Also i'm planning on updating more than one pc, if this way works for me, and there's no sence in updating through the internet more than i have to, cause i dont have the best connection, only 512kbps

By the way, how do i mount an iso image :)

---

### Post by erok on 2007-03-06
Hi there!

I do not know about upgrading from a CD, but to mount an iso image you can just type at the shell:

"sudo mount -o loop <iso_image> <directory to mount>"

and should be done (without the quotes, of course).

;)

---

### Post by flyinggreg on 2007-03-12
> 

Also I am going to convert over to Ubuntu here very soon for everyday tasks.  I will keep my windows machine for playing games and such.  I find surfing the net with Ubuntu just as nice as with Windows except that Ubuntu linux seems far more resistant to viruses/spyware and such.  Also is there a way to convert your Thunderbird email to evolution?

Thanks

I saved the heartache of NOT having a windows boot or machine!  There's only a few programs I need Win-blows for - so I installed QEMU.  

Great posting here!  All I got to say is Ubuntu rocks...and hearing about how it upgrades itself...watchout MS!  I can't wait to see that upgrade button!!

BTW...Bill Gates is the computer era antichrist. :lolflag:

---

