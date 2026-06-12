---
title: "Grub or Grub2??"
date: 2010-02-25
forum: Installation &amp; Upgrades
---

### Post by blan on 2010-02-25
I'm new at this, so please bear with me.  When the 9.10 version was released, I decided to download it and give it a try.  Over a two week span I was just overwhelmed.  I learned (I think) that a load program called Grub2 set up my dual boot install of Vista and Ubuntu, but there seemed to be some annoyance from long time ubuntu users that there had been a switch to the new Grub2 with the release of ubuntu 9.0.  They didn't understand the newer Grub2 and could help me do what I wanted to do. All I wanted to do was have Vista and ubuntu on my computer and either have it give me the choice at bootup which OS I wanted to use, or, at the very least, boot into Vista as the primary while giving me the option to get into Ubuntu.  No one understood Grub2 enough to help me make that happen.  I got frustrated and gave up on Ubuntu.  
 
I still want to get away from MS, but my wife is not willing to even try linux.  I occassionally keep trying to read up on linux on Distrowatch.  While looking at Ubuntu's components today, I noticed that it says it uses Grub.  My question is:
 
Did Ubuntu give up on Grub2 and switch back to Grub?

---

### Post by darkod on 2010-02-25
No, it didn't give up.
Unfortunately, during this "transitional" period from grub1 to grub2, on lots of places people will just say grub, because until recently there was only the initial version of grub. They might also just say grub when in fact they are talking about grub2. When reading instructions or tutorials, and especially before executing any commands related to grub, you need to be careful for which version are they. If not sure, ask.

Otherwise, 9.10 is still with grub2, and the new 10.04 LTS (Long Term Supported) version coming out late April will be with grub2.

After many years, grub got upgraded to grub2 and there will be no going back I think.

You are welcomed to try ubuntu again and this time there should be much more people available to help with grub2. Setting the default OS in particular is very easy.

---

### Post by n0dix on 2010-02-25
for now grub2 in ubuntu and grub in arch. 
I don't think Ubuntu give up. The grub is a tricky component that take time to used to.

---

### Post by Sef on 2010-02-25
> Otherwise, 9.10 is still with grub2....If you upgraded from Jaunty to Koala, then grub1 is used.   If a clean install of Koala was done, then grub2 was installed.

---

