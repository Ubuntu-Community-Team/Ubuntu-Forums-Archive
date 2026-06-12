---
title: "Ubuntu business remix 64bit installs a 32bit system"
date: 2012-05-22
forum: Installation &amp; Upgrades
---

### Post by damko on 2012-05-22
I downloaded twice and reinstalled twice the Ubuntu Business Remix 1204 64bit but all the time I get a 32bit system

```
cat /etc/issue
Ubuntu 12.04 LTS \n \l
```

```
uname -a
Linux nitro 3.2.0-24-generic #38-Ubuntu SMP Tue May 1 16:21:07 UTC 2012 i686 i686 i386 GNU/Linux
```

```
md5sum /home/dam/Downloads/ubuntu-12.04-business-desktop-remix-amd64.iso
db6e25ca88e87e5470ca6b12f73bfca8
```

```
getconf LONG_BIT
32
```

Unfortunately I couldn't find the MD5 on the ubuntu hashes page [https://help.ubuntu.com/community/UbuntuHashes](https://help.ubuntu.com/community/UbuntuHashes) so I can't check if my iso MD5 is matching the 32bit business version.

Did it happen to someone else?

I'm going to download and reinstall for the third time but this time I use the plain 64bit desktop version

Dam

---

### Post by sudodus on 2012-05-22
Have a look at the following link

[[COLOR="Red"]https://help.ubuntu.com/community/UbuntuHashes[/COLOR]]("https://help.ubuntu.com/community/UbuntuHashes")

*Edit: sorry, I see now, that you know that page already, but your particular edition is not there. Anyway, I agree it is a good idea to try the regular desktop flavour of Ubuntu and install whatever extra programs you need*

---

### Post by damko on 2012-05-22
> **sudodus said:**
> *Edit: sorry, I see now, that you know that page already, but your particular edition is not there. Anyway, I agree it is a good idea to try the regular desktop flavour of Ubuntu and install whatever extra programs you need*

That's what I did. It's "running" now but that situation is particularly disappointing though, mainly because it's the "business" version. I picked it on purpose for several reasons: one of those is that I thought they put more care on it...

Cheers
Dam

---

### Post by sudodus on 2012-05-22
What do you want and what did you get?

What help do you need?

---

### Post by damko on 2012-05-23
> **sudodus said:**
> What do you want and what did you get?

What help do you need?

?? what do I want ??
I want to download a 64bit version and get a 64bit os. I think it's fair, isn't it?

Unfortunately I don't need any help because I had to go back to Fedora 13 (I made a disk clone before the installation). 
I'm extremely disappointed by what happened to me during this installation process:
[LIST=1]
[*]I have a certified workstation (HP Z600) and there was no way to start the installation. I hade to add acpi=off at boot and this took me some time to figure it out. (So why is it considered "certified hardware"?)
[*]I downloaded a 64 bit os and I got a 32 bit os. I tried it twice to be sure
[*]I have 3 24" monitors 2 pivoted but there is no way to make them work. X works but unity has troubles, even the 5.2 version.
[/LIST]
It's obvious that Ubuntu is not ready for a professional environment this year and it can be understandable somehow because there are huge news on the user interface side.
Pity that I wasted so much time a this turn.
I'll give a try again next year in June (I install only LTS)

So, to answer your question I don't need any help, cause I went back to Fedora (no other option as far as I can see)

Cheers
Dam

[http://www.venturin.net](http://www.venturin.net)

---

### Post by sudodus on 2012-05-23
I'm sorry that you had such a bad experience with Ubuntu. But I think you should not blame the people behind the main version(s) because the 'Ubuntu Business Remix 1204' is none of them. I think it is supplied by some [probably enthusiastic] people in the Ubuntu Community.

I think this is also the reason why you could not find the md5sum on the UbuntuHashes web page.

---

### Post by damko on 2012-05-23
> **sudodus said:**
> I'm sorry that you had such a bad experience with Ubuntu. But I think you should not blame the people behind the main version(s) because the 'Ubuntu Business Remix 1204' is none of them. I think it is supplied by some [probably enthusiastic] people in the Ubuntu Community.

I think this is also the reason why you could not find the md5sum on the UbuntuHashes web page.

Actually it's a Canonical official release meant for businesses ... [http://www.ubuntu.com/business/desktop](http://www.ubuntu.com/business/desktop)
Now you see why it's disappointing?

Beside that I'm a developer and a business owner so I know how tough is this job: that's why I do not blame anyone. But of course I can't say I'm happy. I posted the message just to avoid other people to waste so many hours as I did.

---

### Post by sudodus on 2012-05-23
Yes I see now, and you are right being critical. Obviously the business remix or the web page about it was released too early.

It may seem strange, that I was not aware of the business remix after more than 1000 posts, but I guess most people at the Ubuntu Forums are running Ubuntu on our private computers and therefore asking about standard Ubuntu, [KLX]ubuntu, Ubuntu Studio, Edubuntu or Mythbuntu.

Anyway I'm glad you stay with linux. As a matter of fact, it makes no big difference for me what distro it is. Way back in time I dual booted a 350 GHz PC with Red Hat and Windows 98 ;-)

---

### Post by mastablasta on 2012-05-23
so the amd64.iso you downloaded gives a 32bit OS (794MB ISO disk image (64 bit))? that is a very strange thing or a very serious mistake which could happen if someone copied same file into amd64 image. hm...
 
have you contacted cannonical about it?
 
regarding certified hardware - if you look at certificaiton pages they sometimes have notes. and sometimes they are certified for certain version only. still i agree - acpi = off shouldn't be necessary on certified device.
Edit The device is certified with notes and for the following versions:
  
Ubuntu releases:
[LIST]
[*]11.10 (with notes)
[/LIST]11.04 (with notes)
 
 
Unity not working nicely with multiple screens is a known issue. i am not sure what fedora 13 uses as DE. if it's gnome 2 then you would need to try gnome fall back and see how that goes. or use kde.
 
edit: fedora 13 uses a much older kernel, so this might be the reason you needed noacpi. it is also an EOL release from 2010. Ubutnu 10.04 LTS is form that year.

---

### Post by jadtech on 2012-05-23
> **damko said:**
> Actually it's a Canonical official release meant for businesses ... [http://www.ubuntu.com/business/desktop](http://www.ubuntu.com/business/desktop)
Now you see why it's disappointing?

Beside that I'm a developer and a business owner so I know how tough is this job: that's why I do not blame anyone. But of course I can't say I'm happy. I posted the message just to avoid other people to waste so many hours as I did.

Actually  and factually if you go to ubuntu.com you can down the 32bit or 64bit desk top system and in stall it once installed  you will find the  management service purple Icon  bottom center that can be clicked  and it opens up asked if you want to install and offers a free 30day trail at which point you can choose to subscribe 

if you go to this link [http://www.ubuntu.com/download](http://www.ubuntu.com/download) and click cloud infrastructure this sets up the server cloud and then  go set up the management service  you have the complete package  with a 30 day free trail  before you have to subscribe.. 

but  what more is when you down load  these files and you try to  do the check sum you will find the numbers on the official list :)

---

### Post by jadtech on 2012-05-23
ubuntu is built and supported by its community , Canonical supports  ubuntu  how ever   either  supports other programs or drivers these are supported by the people who make then there job to make sure they are ported  to ubuntu and work as advertised.. 

just like if you had a company  that offered a system to make fords run on apple juice  Ford is not  going to support  your product  and warrant it works and they are not going to pay to train how your product works how to repair tune, this would be your job Ford makes the car it runs on gas not apple juice :)

---

### Post by damko on 2012-05-23
> **mastablasta said:**
> so the amd64.iso you downloaded gives a 32bit OS (794MB ISO disk image (64 bit))? that is a very strange thing or a very serious mistake which could happen if someone copied same file into amd64 image. hm...

exactly but I don't have the MD5 so I can't check myself. (it's possible that the 64bit link points to the 32bit version: simple mistake, horrible consequence)

> **mastablasta said:**
>  
have you contacted cannonical about it?

No but, well, I hope that someone in Canonical follows the forums. Honestly
I don't have so much time to invest in this.

> **mastablasta said:**
>   
regarding certified hardware - if you look at certificaiton pages they sometimes have notes. and sometimes they are certified for certain version only. still i agree - acpi = off shouldn't be necessary on certified device.

That's what I did. I've read the notes and I remember they say: "you might need NVIDIA proprietary drivers" which is fine.

> **mastablasta said:**
>   
Edit The device is certified with notes and for the following versions:
  
Ubuntu releases:
[LIST]
[*]11.10 (with notes)
[/LIST]11.04 (with notes)

Unity not working nicely with multiple screens is a known issue. i am not sure what fedora 13 uses as DE. if it's gnome 2 then you would need to try gnome fall back and see how that goes. or use kde.
 
edit: fedora 13 uses a much older kernel, so this might be the reason you needed noacpi. it is also an EOL release from 2010. Ubutnu 10.04 LTS is form that year.

Yes F13 is very old that's why I would like to update but with all the changes currently happening and preventing me to have at least the same  quality in my working environment I really can't update.  I have no other option than wait hoping that I won't step into any problem due to the old sofware I'm currently running.
I only wish we linux people could focus more our attention on business needs.

I'd be glad to pay 250$ dollars per year just to have a linux distro (even without phone assistance) but which works out of the box on a set of professional hardware meant to be used by developers or IT professionals (don't even mention RH ok? :) ). What I don't know is if there are many people like me around.

---

### Post by mastablasta on 2012-05-24
> **damko said:**
> exactly but I don't have the MD5 so I can't check myself. (it's possible that the 64bit link points to the 32bit version: simple mistake, horrible consequence)
 
the name of file says amd64. :-O sorry but didn't have time to test it. if i find some time i will download it too. i actually wanted to give it a spin when i read about it in an article.
> 
No but, well, I hope that someone in Canonical follows the forums. Honestly
I don't have so much time to invest in this.
.
they don't . even developers are rare sight. forums are only free communuty support.
 
> 
That's what I did. I've read the notes and I remember they say: "you might need NVIDIA proprietary drivers" which is fine.

yes it does but for version Ubuntu 11.04 32-bit. though it should matter as much. But on the other hand 12.04 does have a different kernel. additionally there is a bug in nvidia drivers in 12.04. not sure if it has any effect on your specific card.

 .> 
Yes F13 is very old that's why I would like to update but with all the changes currently happening and preventing me to have at least the same quality in my working environment I really can't update. I have no other option than wait hoping that I won't step into any problem due to the old sofware I'm currently running.
I only wish we linux people could focus more our attention on business needs.
 
I'd be glad to pay 250$ dollars per year just to have a linux distro (even without phone assistance) but which works out of the box on a set of professional hardware meant to be used by developers or IT professionals (don't even mention RH ok? :) ). What I don't know is if there are many people like me around.
 
i know what you mean. LTS is preety much useless in this regard. :-) well actually i know this second hand. my bro needs about 2 work days to fully install it. since he needs to chase down all older dependencies and test them. and then it doesn't work or he needs to use new ones and the progs he made are affected... to him it's a nightmare.
 
and biggest issue here is that LTS means that same bugs exist for those 5 years.

---

### Post by damko on 2012-05-24
> **mastablasta said:**
> yes it does but for version Ubuntu 11.04 32-bit. though it should matter as much. But on the other hand 12.04 does have a different kernel. additionally there is a bug in nvidia drivers in 12.04. not sure if it has any effect on your specific card.


I tried 5 different drivers, even the 302 which actually works quite fine (Xinerama on 3 screens is just a dream though) and I decided to use it on F13 :) *[be aware the syntax of xorg.conf changes a bit from previous versions, read the readme.txt attached to the NVIDIA package]*

Anyway as I said the main problem is with the DE not with X

> **mastablasta said:**
>  
i know what you mean. LTS is preety much useless in this regard. :-) well actually i know this second hand. my bro needs about 2 work days to fully install it. since he needs to chase down all older dependencies and test them. and then it doesn't work or he needs to use new ones and the progs he made are affected... to him it's a nightmare.
 
and biggest issue here is that LTS means that same bugs exist for those 5 years.
lol
Anyway this is a serious problem:
2 days ~ 10 hours * 2 = 20 hours * 50$ = 1000$ wasted for a company.
That's why I think it would be fine to have a company like Canonical copying what's Apple's currently doing: deliver a qualitative OS for a small set of hardware which works out of the box for 3 / 5 years. It makes sense to me even in the case there were some limitations.

---

