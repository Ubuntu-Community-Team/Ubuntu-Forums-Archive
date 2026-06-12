---
title: "Avast on Natty 64 bit?"
date: 2011-04-24
forum: Installation &amp; Upgrades
---

### Post by jdunn on 2011-04-24
I tried [this guide]("http://ubuntuforums.org/showthread.php?t=781251") for installing Avast.  It has worked for me on past versions of this distro.  The guide does not seem to work for Natty. I'm not sure why but I noticed the libesmtp5 package is a dependency for Avast but the package does not exist in Natty. I can get Avast to run and to scan using the default virus signature file but if I try to update the signatures, Avast displays an error message and quits.  Does anyone know how to get this working?

Please do not ask why I'm trying to install anti-virus on linux.  I have a dual-boot system with Vista...which I transfer files between.  I also access thumb-drives and I am using a few Wine applications.  Hopefully, that explains enough.

---

### Post by howefield on 2011-04-24
Seeing as I am reinstalling next Thursday anyway, I installed Avast as per the guide and it seems ok, have you tried updating via terminal ?

If I use anti virus, I'd normally use Bitdefender which has a 64 bit version available.

---

### Post by jdunn on 2011-04-24
> **howefield said:**
> Seeing as I am reinstalling next Thursday anyway, I installed Avast as per the guide and it seems ok, have you tried updating via terminal ?

If I use anti virus, I'd normally use Bitdefender which has a 64 bit version available.

I updated through terminal and get no error message during the update but when I tried to run Avast:  can not initialize avast engine:  invalid argument

BitDefender sounded like a good alternative until I saw the license has to be renewed every month.

---

### Post by billyfish010 on 2011-04-24
Hi I am using Bitdefender and I can assure you the licence only needs updating yearly. When you initially install Bitdefender it gives you 30 days to get a yearly licence for free.

---

### Post by jdunn on 2011-04-24
> **billyfish010 said:**
> Hi I am using Bitdefender and I can assure you the licence only needs updating yearly. When you initially install Bitdefender it gives you 30 days to get a yearly licence for free.

Oh.  Then now I have a choice to make.  I found what may be the cause of my Avast problem and how to fix it [here]("http://forum.avast.com/index.php?PHPSESSID=6oan7f26ole1i24d1p1rr0ptf5&topic=57775.0").  However, if Bitdefender has a year license and is 64-bit, I may go with that instead.  The downside is I never liked Bitdefenders interface.

---

### Post by yetiman64 on 2011-04-24
> **jdunn said:**
> I updated through terminal and get no error message during the update but when I tried to run [B]Avast:  can not initialize avast engine:  invalid argument
[/B] 
BitDefender sounded like a good alternative until I saw the license has to be renewed every month.

Please check this thread - [http://ubuntuforums.org/showthread.php?t=1518040&highlight=avast](http://ubuntuforums.org/showthread.php?t=1518040&highlight=avast)

Post number 9 has the fix for that. The problem is the Avast definitions file is too big for the default kernel shmmax value (shared memory) in Ubuntu.

Edit: I'm on 64 bit Lucid and installed Avast with "sudo dpkg --force-architecture", with the necessary 32 bit libs installed first. The additional fix in the link is required as well.

---

### Post by billyfish010 on 2011-04-24
Hi Jdun I agree with that I don't particularly like the interface but I use Bitdefender because it is easy to install and use. I used to use Avast when I had 10.04 installed but just never got around to reinstalling. To be honest I ran for months with no protection whatsoever and got no viruses but thought I should protect my computer no sense in taking unnecessary chances.

---

### Post by howefield on 2011-04-24
> **jdunn said:**
> BitDefender sounded like a good alternative until I saw the license has to be renewed every month.

As others have said Bitdefender is no more onerous than Avast in terms of a free licence, ie, no more than an annual email is required.

License page is here, (can be "awkward" to find..)

[http://www.bitdefender.com/site/Products/ScannerLicense/](http://www.bitdefender.com/site/Products/ScannerLicense/)

In any event, looks like you have a fix for Avast and have it installed, so the easiest option would be to keep it.

---

### Post by jdunn on 2011-04-24
> **yetiman64 said:**
> Please check this thread - [http://ubuntuforums.org/showthread.php?t=1518040&highlight=avast](http://ubuntuforums.org/showthread.php?t=1518040&highlight=avast)

Post number 9 has the fix for that. The problem is the Avast definitions file is too big for the default kernel shmmax value (shared memory) in Ubuntu.

Edit: I'm on 64 bit Lucid and installed Avast with "sudo dpkg --force-architecture", with the necessary 32 bit libs installed first. The additional fix in the link is required as well.

Thanks Yetiman.  I already found that fix (see the link in post #5) but I just switched to BitDefender anyway.

---

### Post by yetiman64 on 2011-04-24
> **jdunn said:**
> Thanks Yetiman.  I already found that fix (see the link in post #5) but I just switched to BitDefender anyway.

Ok, you're welcome, I must have missed that bit of info in post 5. Cheers. :)

---

