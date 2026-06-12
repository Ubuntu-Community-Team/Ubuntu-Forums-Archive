---
title: "moving to hardy heron"
date: 2008-05-31
forum: Installation &amp; Upgrades
---

### Post by tropdoug on 2008-05-31
Hello

I have spent the last couple of months getting used to Ubuntu, and in particular trashing a few things and resetting them up, with lots of help in this community. In the last four days I have finally managed to get a beamer and my nvidia drivers working together to give me two displays as clone. Fantastic. 

Now my question is, in the opinion of those that know a lot more than I, would it be a good idea for me to upgrade at this time, or would experience suggest I should perhaps wait until 

a) hardy is less buggy (from what I am reading there appears to be lots of issues)
b) I better understand the technical issues of Linux

Appreciate any views.

---

### Post by trd79 on 2008-05-31
Hi,

My honest opinion would be don't bother (especially if you have things working as you like them). I upgraded to Hardy last week and am now seriously regretting it. Spending the weekend reading through bug reports just to get my NFS shares to work again is not my idea of fun :(

I have a laptop running Gutsy, and that's exactly how it is going to stay!

---

### Post by steveneddy on 2008-05-31
These are just the joys of running Linux.

Once things are set up and running how you like them, just leave them alone.

It took me one weekend and maybe a couple of hours to get everything good on my Hardy upgrade, but now it's good as gold.

---

### Post by Aearenda on 2008-05-31
I would take a full backup first (I use rsync for that) and then upgrade. Or, even better, create an extra partition so that you can choose at boot time whether to go to a new Hardy installation or the old Gutsy one, giving you a chance to try it out first before committing yourself. 

There is a lot of pain in the forums over Hardy's changes, but I think that is partly because we have more users now than before, and we don't hear about the succesful upgrades.

---

### Post by jmontelius on 2008-05-31
Wait, I've upgaded two of my machines and have had problems with the nvidia drivers. Both machines worked fine with 7.10. Iv'e sorted it out with one but the older mahchine (with GeForce4) still doesn't work with glx. 
  J

---

### Post by jmontelius on 2008-06-01
ftr. second machine now ok, nvidia drivers and glx up and running. Don't ask me in what order I had to reinstall things in before working :-)

---

### Post by pkiula on 2008-06-01
If an OS cannot function seamlessly after an upgrade and requires weekend after weekend of support over forums, then it's not ready for prime time. Ubuntu is MUCH slower than alternatives, and while it is pleasant and at least *my* current choice of OS, it should stop making claims of being a sensible alternative to Windows and whatnot. It is NOT a sensible alternative. Windows XP works much faster and with significantly lesser woes than Ubuntu, and I never once need to see a console window. Thanks.

---

### Post by tropdoug on 2008-06-02
> **pkiula said:**
> If an OS cannot function seamlessly after an upgrade and requires weekend after weekend of support over forums, then it's not ready for prime time. Ubuntu is MUCH slower than alternatives, and while it is pleasant and at least *my* current choice of OS, it should stop making claims of being a sensible alternative to Windows and whatnot. It is NOT a sensible alternative. Windows XP works much faster and with significantly lesser woes than Ubuntu, and I never once need to see a console window. Thanks.

Well everyone to their own I guess. The funny thing is I made the switch four months ago, because my XP machine kept getting broken by trojans etc, which got through my firewall. system mechanic 7 pro, and kaspersky virus checker, all very expensive pieces of program that failed to do what they promised. In fact one pesky little trojan lwass.exe could not be destroyed by any of the supposed wonder windows programs. and my brand new vista laptop, got so slow that my wife could literally go and make a coffee whilst it tried to connect at "Blistering speed" yeah right!

Since coming over to Linux, every single program that I need has worked and in most cases a lot better than the windows alternative, including things like scribus which I personally believe not even acrobat pro 7 can touch.  I have enjoyed the learning curve, the challenges and the understanding, support and willing help these forums give. 

So I will re state my question to Linux users who support the OS and ask the knockers to knock somewhere else. Thanks 
:guitar:

---

### Post by tropdoug on 2008-06-02
> **Aearenda said:**
> I would take a full backup first (I use rsync for that) and then upgrade. Or, even better, create an extra partition so that you can choose at boot time whether to go to a new Hardy installation or the old Gutsy one, giving you a chance to try it out first before committing yourself. 

There is a lot of pain in the forums over Hardy's changes, but I think that is partly because we have more users now than before, and we don't hear about the succesful upgrades.

Aint that the truth, its odd isn't it, that the disasters are on the front page of the news and the heroes on the back. an observation of life!

---

### Post by pkiula on 2008-06-02
I quite like Ubuntu. But it does NOT install easily. If you "enjoy" weekend installations and forum chitchat to fix things, sure, it's a good OS for the 0.2% of the PC audience comprised of people like you. The tinkerers. 

And please stop comparing Ubuntu to Vista, just because Vista is the new OS. Compare to Windows XP Pro with SP3, which is a very viable alternative today. Compare it to SuSE.  Compare it to Leopard's latest avatar. All these OSes run faster on the same hardware than Ubuntu does. 

I am not trying to detract, and I certainly very deeply appreciate the help I get here and the effort that goes into making a free OS. I was only making the point that the OS team should probably focus on making the OS faster now (it runs slowly on my 1GB RAM Dell with a Pentium Centrino!) and make sure that at least the market-leading hardware such as nVidia etc are handled easily!

---

### Post by tropdoug on 2008-06-02
I think you must be doing something wrong if it takes a weekend to install and fix your bits and pieces. 

I broke my system myself because of enthusiasm, so that meant re installation a couple of times, each time it was like half an hour, and all running well, with just my personal tweaks to do. The only one issue was with nvidia drivers and that is a propriety issue not the development teams. 

I did compare it to XP, and sorry to you but hundreds of thousands of people were forced into having Vista by MS when it refused to supply oem resellers with anything but. 

get over the  windows thing already bro.

PS no point in a flame war though. I luv my system

---

### Post by pkiula on 2008-06-02
No worries. I don't take your post as a flame war. As I said, I quite like Ubuntu. 

Windows XP Pro is very much a viable alternative. If a person is dumb enough not to know how to circumvent it, then of course he's not in contention for Linux anyway. 

But I speak of the millions of people who do know that they can choose between SuSE, Win XP Pro, Leopard. 

And yes, it took me 30 mins to install Ubuntu, but a very long time to fix nVidia drivers. The machine was dumb without it, and still is very slow and clunky in its interface.  

Anyway, this is a wishlist to whoever is reading this: please do something with the interface. Windows should not take so long to minimize and maximize. At least that bit is instant even in Vista, which helps the visual experience of a modern OS.

---

### Post by tropdoug on 2008-06-02
ahhh, I see your concern (or at least part of it) the Nvidia drivers, well in that I can emphasise. There is a lot here on it, including my own very lengthy and extremely confusing thread at  porjehttp://ubuntuforums.org/showthread.php?t=808694. I don't recommend my one as a fix but perhaps there may be something in there for you. 

I found that once I got the driver working correctly, (and it may seem to be but isn't) then all goes well. Check out the nvidia site as well perhaps pr the many discussions here. Nvidia just released a new driver for geforce cards maybe that would help. 

Cheers

---

