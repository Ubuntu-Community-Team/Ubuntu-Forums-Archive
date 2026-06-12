---
title: "anyone else hate grub2?"
date: 2009-09-17
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by sena_akada on 2009-09-17
it seems to cause sooooooo many problems

---

### Post by VMC on 2009-09-17
> **sena_akada said:**
> it seems to cause sooooooo many problemsWhat problems? It's working ok for me. Just need to understand what files work with it. There's plenty of tutorials to read up on if your having problems.

The only thing I have problems with and I have filed a bug report, is update-grub misses Fedora's initrd string. Also vga=773 is deprecated so I must use gfxpayload=1024x768, and that doesn't work the same way that the kernel line of vga did.

It's going to change that's why its in the 1.97 version and not 2.0.

---

### Post by krausest on 2009-09-17
I agree - there's no love for grub2 in me.
Grub2 takes about a minute until I acutally get the boot menu. The  configuration is way too complicated for my personal taste and just updating the grub installer takes longer that it should take to boot...

---

### Post by mudi on 2009-09-17
Hmm, grub2 works great for me.  Boots instantly unless I hold down shift, just like it should.

---

### Post by sena_akada on 2009-09-17
whats the point in grub2 anyway?

---

### Post by jocko on 2009-09-17
> **krausest said:**
>  Grub2 takes about a minute until I acutally get the boot menu. The  configuration is way too complicated for my personal taste and just updating the grub installer takes longer that it should take to boot...

The delay is probably the same as in [this bug]("https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/420933"). In short, it looks like it happens when grub2 is on another hard drive than the / partition (or perhaps the /boot folder/partition), so you may fix it by installing grub 2 to the drive that contains the / filesystem and changing your bios to boot from that drive instead.
Unfortunately it doesn't seem like anyone is trying to fix the bug, (still listed as incomplete) so if your problem is the same, you should add to the bug report and hope that this gets to the developers' attention before the final release of karmic.
Other than this bug, I've had less problems with grub2 than I ever had with grub1, I think jaunty was the first release when grub1 installed to the mbr of the correct hard drive during a normal live cd install, and also the first release where I didn't need to edit my menu.lst to set the grub root (the "groot" option) to the correct drive after install to get rid of "error 15" or whichever error it gave when it looked for the /boot folder on the wrong hard drive...
With grub2 I've had no such problems. So, no. I don't hate grub2. If anything I love it, or at least like it more than grub1.

The configuration is in no way any more complicated than what you had in grub 1, it's just that you don't configure it directly in the file that also contains the boot menu anymore. The same options are still there (except perhaps some display resolution settings, which I'm sure someone is working on). They just look slightly different and are in other files than what you are used to.

---

### Post by slakkie on 2009-09-17
> **sena_akada said:**
> whats the point in grub2 anyway?

Active development afaik.

But have a look here: [http://www.gnu.org/software/grub/grub-2.en.html](http://www.gnu.org/software/grub/grub-2.en.html)

---

### Post by Regenweald on 2009-09-17
> **sena_akada said:**
> it seems to cause sooooooo many problems

Neither the code nor the developers have done me any great wrong. I tend not to hate that which can not hate back. Wasted emotion.

---

### Post by steeleyuk on 2009-09-17
> **sena_akada said:**
> whats the point in grub2 anyway?

Its actively being developed unlike the original GRUB which hadn't seen much work, other than bug fixes. The original GRUB didn't support ext4 for example, so it had to be patched afterwards.

Breakage, such as that which an upgrade to GRUB2 might cause, is required to advance. If people don't like it, they shouldn't be using development versions.

---

### Post by jerrylamos on 2009-09-17
> **steeleyuk said:**
> Its actively being developed unlike the original GRUB which hadn't seen much work, other than bug fixes. The original GRUB didn't support ext4 for example, so it had to be patched afterwards.

Breakage, such as that which an upgrade to GRUB2 might cause, is required to advance. If people don't like it, they shouldn't be using development versions.

Grub 1.97 beta at this stage seems to have a little bit more function and a lot more complicity.  So long as I can boot sort of and modify things Grub 1.97 doesn't have functioning (maybe not ever), I can put up with it.

At the moment booting an iso in a 1 gb partition is giving me fits.  It worked reliably in jaunty and intrepid and hardy and ... Now it works sometimes depending on the state of updates & dist-upgrades & CD's.

Jerry

---

### Post by mdurham on 2009-09-17
jerrylamos, can you explain what you mean by this please > At the moment booting an iso in a 1 gb partition is giving me fits. 
Thanks, Mike

---

### Post by 23meg on 2009-09-17
> **sena_akada said:**
> it seems to cause sooooooo many problems

[Some people think this thread is pointless]("http://en.wikipedia.org/wiki/Wikipedia:Avoid_weasel_words").

---

### Post by gnomeuser on 2009-09-17
I haven't had any problems with Grub2 on any of my machines but the config file syntax has definitely grown more complex and less readable.. I am unsure if I really care about this since 99.9% of all my interaction is done via tools rather than direct manipulation.

Aside that, no objections to it. I wish there was btrfs support though just because I am glutton for punishment.

---

### Post by sena_akada on 2009-09-17
> **23meg said:**
> [Some people think this thread is pointless]("http://en.wikipedia.org/wiki/Wikipedia:Avoid_weasel_words").

[http://ubuntuforums.org/showthread.php?t=1269012](http://ubuntuforums.org/showthread.php?t=1269012)
[http://ubuntuforums.org/showthread.php?t=1261764](http://ubuntuforums.org/showthread.php?t=1261764)
[http://ubuntuforums.org/showthread.php?t=1267994](http://ubuntuforums.org/showthread.php?t=1267994)
[http://ubuntuforums.org/showthread.php?t=1265270](http://ubuntuforums.org/showthread.php?t=1265270)
[http://ubuntuforums.org/showthread.php?t=1258019](http://ubuntuforums.org/showthread.php?t=1258019)
[http://ubuntuforums.org/showthread.php?t=1222172](http://ubuntuforums.org/showthread.php?t=1222172)
[http://ubuntuforums.org/showthread.php?t=1260512](http://ubuntuforums.org/showthread.php?t=1260512)
[http://ubuntuforums.org/showthread.php?t=1257863](http://ubuntuforums.org/showthread.php?t=1257863)
[http://ubuntuforums.org/showthread.php?t=1255263](http://ubuntuforums.org/showthread.php?t=1255263)
[http://ubuntuforums.org/showthread.php?t=1248679](http://ubuntuforums.org/showthread.php?t=1248679)
[http://ubuntuforums.org/showthread.php?t=1200862](http://ubuntuforums.org/showthread.php?t=1200862)

[img]http://kaweahoaks.com/html/weasel_face01.jpg[/img]

---

### Post by Keyper7 on 2009-09-17
> **sena_akada said:**
> [http://ubuntuforums.org/showthread.php?t=1269012](http://ubuntuforums.org/showthread.php?t=1269012)
[http://ubuntuforums.org/showthread.php?t=1261764](http://ubuntuforums.org/showthread.php?t=1261764)
[http://ubuntuforums.org/showthread.php?t=1267994](http://ubuntuforums.org/showthread.php?t=1267994)
[http://ubuntuforums.org/showthread.php?t=1265270](http://ubuntuforums.org/showthread.php?t=1265270)
[http://ubuntuforums.org/showthread.php?t=1258019](http://ubuntuforums.org/showthread.php?t=1258019)
[http://ubuntuforums.org/showthread.php?t=1222172](http://ubuntuforums.org/showthread.php?t=1222172)
[http://ubuntuforums.org/showthread.php?t=1260512](http://ubuntuforums.org/showthread.php?t=1260512)
[http://ubuntuforums.org/showthread.php?t=1257863](http://ubuntuforums.org/showthread.php?t=1257863)
[http://ubuntuforums.org/showthread.php?t=1255263](http://ubuntuforums.org/showthread.php?t=1255263)
[http://ubuntuforums.org/showthread.php?t=1248679](http://ubuntuforums.org/showthread.php?t=1248679)
[http://ubuntuforums.org/showthread.php?t=1200862](http://ubuntuforums.org/showthread.php?t=1200862)

So your proof that grub2 "seems to cause soooooo many problems" is threads reporting issues.

*In a forum section made for, among other things, reporting issues.*

**On a development version.**

Ok, then.

---

### Post by jocko on 2009-09-18
> **sena_akada said:**
> [http://ubuntuforums.org/showthread.php?t=1269012](http://ubuntuforums.org/showthread.php?t=1269012)
[http://ubuntuforums.org/showthread.php?t=1261764](http://ubuntuforums.org/showthread.php?t=1261764)
[http://ubuntuforums.org/showthread.php?t=1267994](http://ubuntuforums.org/showthread.php?t=1267994)
[http://ubuntuforums.org/showthread.php?t=1265270](http://ubuntuforums.org/showthread.php?t=1265270)
[http://ubuntuforums.org/showthread.php?t=1258019](http://ubuntuforums.org/showthread.php?t=1258019)
[http://ubuntuforums.org/showthread.php?t=1222172](http://ubuntuforums.org/showthread.php?t=1222172)
[http://ubuntuforums.org/showthread.php?t=1260512](http://ubuntuforums.org/showthread.php?t=1260512)
[http://ubuntuforums.org/showthread.php?t=1257863](http://ubuntuforums.org/showthread.php?t=1257863)
[http://ubuntuforums.org/showthread.php?t=1255263](http://ubuntuforums.org/showthread.php?t=1255263)
[http://ubuntuforums.org/showthread.php?t=1248679](http://ubuntuforums.org/showthread.php?t=1248679)
[http://ubuntuforums.org/showthread.php?t=1200862](http://ubuntuforums.org/showthread.php?t=1200862)

[IMG]http://kaweahoaks.com/html/weasel_face01.jpg[/IMG]

You know that the problems in those posts can be divided into these three categories:
1. Bugs that have already been fixed. Like one or two in os-prober, that failed to add other os or to make the other os entry point to the wrong partition.
2. People that are used to configuring grub 1 in menu.lst, and just need to learn the new way.
3. Bugs that may not have been solved yet, but are being worked on.

You are using an alpha version. It does contain bugs, which is why it's important that people test it to find those bugs and report them to the developers. It also contain things that are new to you or just look or work in a slightly different way. You just need to forget the old way of doing things and learn the new way. Don't start hating things just because they are different.

---

### Post by jbernardo on 2009-09-18
I don't hate grub2 - I just [can't get it to work]("https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/425359"). Anyone has been able to use it on a eeepc maintaining the original partitioning structure (XP, EF partition, etc.)?

---

### Post by autark on 2009-09-18
My only major gripe with grub2 is the lack of comprehensive documentation. Also, I sometimes miss the grub shell (the executable), the grub2 equivalent of which I haven't found any mention of in the documentation. But it may just be my googling skills that are lacking.

---

### Post by Nickedynick on 2009-09-18
I don't like how you have to go about manually configuring GRUB2 compared to old GRUB, but it does seem to work well so I can't complain too much. Having said that, I've not used it that much - I have Karmic on a separate partition that I call from Jaunty's GRUB.

---

### Post by MacUntu on 2009-09-18
If you really want to hate a boot loader mess around with Windows 7/Vista. :KS

> **sena_akada said:**
> [http://ubuntuforums.org/showthread.php?t=1269012](http://ubuntuforums.org/showthread.php?t=1269012)
[http://ubuntuforums.org/showthread.php?t=1261764](http://ubuntuforums.org/showthread.php?t=1261764)
[http://ubuntuforums.org/showthread.php?t=1267994](http://ubuntuforums.org/showthread.php?t=1267994)
[http://ubuntuforums.org/showthread.php?t=1265270](http://ubuntuforums.org/showthread.php?t=1265270)
[http://ubuntuforums.org/showthread.php?t=1258019](http://ubuntuforums.org/showthread.php?t=1258019)
[http://ubuntuforums.org/showthread.php?t=1222172](http://ubuntuforums.org/showthread.php?t=1222172)
[http://ubuntuforums.org/showthread.php?t=1260512](http://ubuntuforums.org/showthread.php?t=1260512)
[http://ubuntuforums.org/showthread.php?t=1257863](http://ubuntuforums.org/showthread.php?t=1257863)
[http://ubuntuforums.org/showthread.php?t=1255263](http://ubuntuforums.org/showthread.php?t=1255263)
[http://ubuntuforums.org/showthread.php?t=1248679](http://ubuntuforums.org/showthread.php?t=1248679)
[http://ubuntuforums.org/showthread.php?t=1200862](http://ubuntuforums.org/showthread.php?t=1200862)

A couple of threads vs. hundreds of testers - congratulations! :lolflag:

---

### Post by Podex on 2009-09-18
I don't hate grub2. I've had some problems with it, but it's working fine for me now. I do think Canonical should have put some more people to work on fixing Grub2 issues though. The bug list has a lot of unresolved and new bugs that haven't been looked at (much) yet: [https://bugs.launchpad.net/ubuntu/+source/grub2](https://bugs.launchpad.net/ubuntu/+source/grub2) and there is not too much time left untill Karmic is released.
So do you people think that they should have sticked with patching Grub Legacy? Grub2 does seem to me like the way forward, but maybe they underestimated the amount of work to get it working well enough for all people (read: hardware)

---

### Post by ronacc on 2009-09-18
sofar grub2 has shown me no advantage , I could care less about fancy boot graphics or "bling" and it is more complex and difficult to manipulate on my particular setup . Since some people seem to dislike the word hate I'll just say I strongly dislike grub2 at this point .

---

### Post by philinux on 2009-09-18
Same here ronnac, dual booting is a headache. I'm dreading installing karmic with grub2 on my disk one when the rc comes out.

Maybe it will be ok but I reckon newbies are in for a torrid time.

---

### Post by ronacc on 2009-09-18
> **philinux said:**
> S

Maybe it will be ok but I reckon newbies are in for a torrid time.

I suppose they will get it straightend out eventualy , but in the meantime I can hear the screams for help and there will be fewer of us that feel competent to give it.

---

### Post by sena_akada on 2009-09-18
> **MacUntu said:**
> If you really want to hate a boot loader mess around with Windows 7/Vista. :KS



A couple of threads vs. hundreds of testers - congratulations! :lolflag:

lol i asked the question because i have seen so many grub2 problem threads. ive had problems with it too. 

and that was only about a third of all the grub2 problem threads, and to show the cheesecake who called me a weasel that i wasnt :P

---

### Post by screaminj3sus on 2009-09-18
Grub2 works fine for me... This is an alpha, its gonna have bugs.

---

### Post by Slug71 on 2009-09-18
Havent had any issues with Grub2 here other than trying to chainload with it. Been testing it since Jaunty. 

Only thing i dont really like about it is that there is 2 entries for Memtest and i have 2 for Vista. One of which doesnt work. 
Both these are easilly fixed by editing grub.cfg though.

This is what testing is about though. 
Besides Grub Legacy cant boot XFS or Btrfs where Grub2 can as far as i know.

---

### Post by Regenweald on 2009-09-18
> **philinux said:**
> Same here ronnac, dual booting is a headache. I'm dreading installing karmic with grub2 on my disk one when the rc comes out.

Maybe it will be ok but I reckon newbies are in for a torrid time.

You know, the first iteration of grub could not find my XP, the second update automatically found it and I've had no problems since. Is it grub or some of our complicated boot setups ?

---

### Post by bobince on 2009-09-20
grub2 works fine here. However, the menu doesn't quite appear the way I want.

I'd like the menu to be invisible, and not to slow down the boot process at all, unless I happen to be holding Shift down at the moment it loads. If that's the case I'd like unlimited time to choose an option.

This was how I thought grub2 was supposed to work from the description, but I can't seem to get it to do that no matter what I set the TIMEOUT/HIDDEN_TIMEOUT/QUIET options to. Any tips?

---

### Post by kansasnoob on 2009-09-20
Well, I don't hate anything - some things I prefer more than others, but most recently, after a fresh install of Karmic alpha 6, I was able to boot into only Karmic after install.

Then when I ran 'update-grub' (both before or after applying available updates) I was able to boot into all three of my other operating systems (XP, Jaunty, and Mint 7) but booting Karmic would fail! I even tried some chain-loading techniques, that is restoring grub legacy to another OS and chain-loading into Grub 2 and it also failed. 

I couldn't figure it out so I mounted Karmic's filesystem from either Jaunty or Mint using gui's after installing 'nautilus-gksu' and the "open as admin" option and literally deleted the entire Grub folder (NOT the boot folder - that would break the whole thing).

I then restored grub legacy to either Mint or Jaunty and added the proper boot lines to that existing menu.lst. Similar to this:

> title		Ubuntu 9.10, kernel 2.6.31-10-generic (on /dev/sda3)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.31-10-generic root=UUID=05aed494-04f9-43c6-abd3-de8626294e1f ro   quiet splash 
initrd		/boot/initrd.img-2.6.31-10-generic
savedefault
boot

title		Ubuntu 9.10, kernel 2.6.31-10-generic (recovery mode) (on /dev/sda3)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.31-10-generic root=UUID=05aed494-04f9-43c6-abd3-de8626294e1f ro single 
initrd		/boot/initrd.img-2.6.31-10-generic
savedefault
boot

It booted OK, other than the startup script that we've been talking about here, and I immediately went to Synaptic and removed grub-pc and os-prober. I was later prompted that grub-common was no longer needed so I used autoremove to ditch it.

So far no problems! The point is: it's your computer! You can use whatever boot-loader suits your fancy.

I'm sure Grub 2 will turn out to be the boot-loader of choice soon. It's sort of like the pulseaudio thing. It drove me crazy the first few months after Hardy came out, but now it's getting pretty darn solid.

---

### Post by Seventh Reign on 2009-09-20
I love Grub2 ... so much easier to configure once you actually know what you are doing.  Might not be better for a noob, but its definitely easier once you learn it.

---

### Post by autocrosser on 2009-09-20
> **krausest said:**
> I agree - there's no love for grub2 in me.
Grub2 takes about a minute until I acutally get the boot menu. The  configuration is way too complicated for my personal taste and just updating the grub installer takes longer that it should take to boot...

Then add to my bug report: [https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/420933](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/420933)

---

### Post by autocrosser on 2009-09-20
> **Slug71 said:**
> Havent had any issues with Grub2 here other than trying to chainload with it. Been testing it since Jaunty. 

Only thing i dont really like about it is that there is 2 entries for Memtest and i have 2 for Vista. One of which doesnt work. 
Both these are easilly fixed by editing grub.cfg though.

This is what testing is about though. 
Besides Grub Legacy cant boot XFS or Btrfs where Grub2 can as far as i know.

Same here--I've been using Grub2 from late Jaunty & once you get the hang of it--it is much more powerful--the learning curve is rather steep, but as soon as SUM can work with it most of the problems will be over with.

---

### Post by Slug71 on 2009-09-20
> **autocrosser said:**
> Same here--I've been using Grub2 from late Jaunty & once you get the hang of it--it is much more powerful--the learning curve is rather steep, but as soon as SUM can work with it most of the problems will be over with.

Yep exactly. Like i said in the other thread too, i dont even think Grub2 is officially out of development yet.

---

### Post by hblaw on 2009-09-20
> **jocko said:**
> You know that the problems in those posts can be divided into these three categories:
1. Bugs that have already been fixed. Like one or two in os-prober, that failed to add other os or to make the other os entry point to the wrong partition.
2. People that are used to configuring grub 1 in menu.lst, and just need to learn the new way.
3. Bugs that may not have been solved yet, but are being worked on.


I think no.2 is a bug in itself. People (non-development users) should not need to learn anything for a boot loader. The system should handle it and the users should only see a menu after he/she presses the power button. This should be true for at least 99.999% of the people who are using common hardware. 

hihi

---

### Post by Vanishing on 2009-09-20
> **hblaw said:**
> I think no.2 is a bug in itself. People (non-development users) should not need to learn anything for a boot loader. The system should handle it and the users should only see a menu after he/she presses the power button. This should be true for at least 99.999% of the people who are using common hardware. 

hihi

menu.lst is configure file for grub, same situation for grub2, grub.cfg is its configure file, so that is not a bug. You have to learn how to write menu.lst too just like you have to learn if you need to write grub.cfg.

---

### Post by eznet on 2009-10-15
Is it just me, or is does Grub2 seem slower to load?  

I swear it sits at "Loading Grub" message a good 1 to 2 seconds more than was the case before...

---

### Post by cornflake000 on 2009-10-15
I've been using grub2 for quite some time and I'm pretty good at it.  I know what to do in any circumstance that I come across.  But...I would rather have the old grub any day.  I can just make the changes in a moment or 2 from any partition, distribution, test version... (I run 4 on this machine) no problem.  With grub2.. it's just round and round and round...

It's OK.  It works for me.  I don't like it.

---

### Post by kansasnoob on 2009-10-16
While I'm NOT recommending doing so for others I've figured out how to revert to legacy grub very effectively, and now I even have things set up so I can occasionally change back and forth from legacy grub to grub2 and vice versa just to see how things are progressing after updates and such.

I made some fairly explicit notes, but as it says caution and some prior knowledge is required:

[http://ubuntuforums.org/showpost.php?p=8071880&postcount=18](http://ubuntuforums.org/showpost.php?p=8071880&postcount=18)

I did even discover after that update some time ago where a legacy grub package update removed grub-pc (which is grub2) that /boot/grub contained files for both legacy grub and grub2. After creating a new grub directory and totally reinstalling grub2 things worked better than ever, but being a control freak I still went back to legacy grub:)

---

### Post by Trapper on 2009-10-16
What's irking me with grub2 on ubuntu is that every time I get a kernel update in Karmic it insists on writing to the mbr and I don't want that. I have a multiboot system with several linux flavors, no separate boot partition and have my machine set to boot off the mbr set up by my Fedora 11 install and I use chanloading in grub to boot other installs. Karmic keeps overwriting the mbr though with Karmic's grub2, forcing me to boot up off my fedora install disk to replace the mbr.

This is my machine and I make the decisions. It's not Ubuntu's place to alter my mbr when I choose to have another installation with grub, rather than grub2, control the mbr.

---

### Post by kansasnoob on 2009-10-16
> **Trapper said:**
> What's irking me with grub2 on ubuntu is that every time I get a kernel update in Karmic it insists on writing to the mbr and I don't want that. I have a multiboot system with several linux flavors, no separate boot partition and have my machine set to boot off the mbr set up by my Fedora 11 install and I use chanlinking in grub to boot other installs. Karmic keeps overwriting the mbr though with Karmic's grub2, forcing me to boot up off my fedora install disk to replace the mbr.

This is my machine and I make the decisions. It's not Ubuntu's place to alter my mbr when I choose to have another installation with grub, rather than grub2, control the mbr.

Then why not set things up to boot Karmic with Fedora's bootloader and once it's all working just "purge remove" grub-pc, os-prober, and grub-common from Karmic.

---

### Post by Trapper on 2009-10-16
> **kansasnoob said:**
> Then why not set things up to boot Karmic with Fedora's bootloader and once it's all working just "purge remove" grub-pc, os-prober, and grub-common from Karmic.

I get your point here but when I chainload to the 9.10 install am I still going to have a grub.cfg for 9.10?

Here's what I have to boot my Karmic install:

```
title Ubuntu 9.10 'Karmic' X86_64 Ext4   
rootnoverify (hd0,7)
chainloader +1
```

Am I not in need of grub2 or some sort of grub in my Karmic install?

---

### Post by kansasnoob on 2009-10-16
> **Trapper said:**
> I get your point here but when I chainload to the 9.10 install am I still going to have a grub.cfg for 9.10?

Here's what I have to boot my Karmic install:

```
title Ubuntu 9.10 'Karmic' X86_64 Ext4   
rootnoverify (hd0,7)
chainloader +1
```

Am I not in need of grub2 or some sort of grub in my Karmic install?

I pretty well documented my journey here:

[http://ubuntuforums.org/showthread.php?t=1247994](http://ubuntuforums.org/showthread.php?t=1247994)

At the very bottom of post #18 (nearly tutorial ready) I made note of what "boot verbosity" worked for me adding Karmic to an existing legacy grub in either Jaunty or Mint.

I haven't messed with Fedora in quite some time, but if it's still using legacy grub it's simply a matter of figuring out the exact verbosity that agrees with it's own grub.

Hope that's helpful.

---

### Post by Trapper on 2009-10-16
Okay. I've read your link and will dabble with this although it actually only intensifies my irk. I could give a hoot if Karmic uses grub2 for itself. My complaint is that it hijacks the mbr from Fedora 11, which uses legacy grub. Oddly, Fedora 12 development is using grub2. It does not hijack the mbr.

***Correction to above*** My Fedora 12 install does not utilize grub2.

I've used the setup I have for years. It requires absolutely no maintenance except when I am installing a new flavor or am disposing of one and all I have to do then is make one simple entry in grub.conf or delete one, depending on the case. Other than that I never have to touch the bootloader even though I have a goodly number of distributions. It doesn't get any simpler. Then ubuntu's rendition of grub2 comes along and ......................................! 

I just want 9.10 to not screw around with the mbr bootloader every time a kernel update comes along. How do I prevent that?

---

### Post by kansasnoob on 2009-10-16
[B][COLOR="Red"]Warning to all: the packages 'grub-common' and 'os-prober' must remain installed or it breaks kernel upgrades! Either/or both 'grub' and 'grub-pc' can be removed.
[/COLOR][/B]
To Trapper:

I just did some further testing.

I renamed by /boot/grub to /boot/grub_legacy and didn't even create a new grub directory. I then removed (not purged) grub, grub common, startupmanager, and (since it was still lingering) os-prober.

I then handed grub off to my Mint install and physically updated the kernel #'s (this would be a nuisance you'd have to live with if you have no grub installed on any **nux partition) and all went well! I booted with no problem!

I did however discover that os-prober and grub-common want to remain marked for automatic installation, so every update will want to reinstall those packages. I'll find a way to avoid that in time!

But, the answer is "YES", you can boot Karmic with no grub installed "in it". Of course this only applies if you have a multi-boot with grub installed elsewhere and you know how to add Karmic to that grub.

---

### Post by VMC on 2009-10-16
> **Trapper said:**
> ... My Fedora ...
I just want 9.10 to not screw around with the mbr bootloader every time a kernel update comes along. How do I prevent that?
There's your problem. For some reason grub2 doesn't add the initrd for Fedora. If you look at grub.cfg you will see that it is missing. I have a bug reported on this. I'll try to find it again. They think it has to do with os-prober.

---

### Post by Trapper on 2009-10-16
> **VMC said:**
> There's your problem. For some reason grub2 doesn't add the initrd for Fedora. If you look at grub.cfg you will see that it is missing. I have a bug reported on this. I'll try to find it again. They think it has to do with os-prober.

It picks up a Fedora F11 i686 distro I have in my extended partition but it doesn't pick up the F11 64 Bit I have installed in a primary partition and that's the one with the mbr bootloader. Below is the one it does find. It doesn't find the one at sda3, which is a primary partition. U9.10 is installed on sda1. It's also a primary. sda 2 is my swap and on a primary. My extended is at sda4.

```

# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda5.
menuentry "Fedora (2.6.29.6-217.2.8.fc11.i686.PAE) (on /dev/sda5)" {
    set root=(hd0,5)
    search --no-floppy --fs-uuid --set 1125ee58-946e-4993-91f3-3cb5dc0654d0
    linux /boot/vmlinuz-2.6.29.6-217.2.8.fc11.i686.PAE ro root=UUID=1125ee58-946e-4993-91f3-3cb5dc0654d0 rhgb quiet 
    initrd /boot/initrd-2.6.29.6-217.2.8.fc11.i686.PAE.img
}
```

---

### Post by kansasnoob on 2009-10-17
> **kansasnoob said:**
> [B][COLOR="Red"]Warning to all: the packages 'grub-common' and 'os-prober' must remain installed or it breaks kernel upgrades! Either/or both 'grub' and 'grub-pc' can be removed.
[/COLOR][/B]
To Trapper:

I just did some further testing.

I renamed by /boot/grub to /boot/grub_legacy and didn't even create a new grub directory. I then removed (not purged) grub, grub common, startupmanager, and (since it was still lingering) os-prober.

I then handed grub off to my Mint install and physically updated the kernel #'s (this would be a nuisance you'd have to live with if you have no grub installed on any **nux partition) and all went well! I booted with no problem!

I did however discover that os-prober and grub-common want to remain marked for automatic installation, so every update will want to reinstall those packages. I'll find a way to avoid that in time!

But, the answer is "YES", you can boot Karmic with no grub installed "in it". Of course this only applies if you have a multi-boot with grub installed elsewhere and you know how to add Karmic to that grub.

Just wanted to bring my new warning to your attention. This AM's kernel upgrade would not complete after removing grub-common and os-prober. Obviously why the devs have them packaged as automatically installed!

---

