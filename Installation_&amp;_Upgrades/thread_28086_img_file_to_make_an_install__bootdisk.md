---
title: "img file to make an install  bootdisk"
date: 2005-04-18
forum: Installation &amp; Upgrades
---

### Post by yhotg on 2005-04-18
i can't find an img file to make a bootdisk to install from hard drive, specially from the xp hard drive partition.
someone can point me in the right direction?

ty
yhotg

---

### Post by andvaranaut on 2005-04-18
[QUOTE=yhotg]i can't find an img file to make a bootdisk to install from hard drive, specially from the xp hard drive partition.
someone can point me in the right direction?

ty
yhotg[/QUOTE]
 As far as I know, Ubuntu must be installed from the CD. Why aren't you able to do a regular CD install? 

Cheers, andvaranaut

---

### Post by yhotg on 2005-04-19
because i don't have a cd wr where to make the cd installer.
and i didn't tried to get the free cd's because i live in israel and didn't think they'll go here.

must be some way to make an install from hard drive from xp, come on people!

 ](*,) 

yhotg

---

### Post by andvaranaut on 2005-04-19
[QUOTE=yhotg]because i don't have a cd wr where to make the cd installer.
and i didn't tried to get the free cd's because i live in israel and didn't think they'll go here.

must be some way to make an install from hard drive from xp, come on people!

 ](*,) 

yhotg[/QUOTE]
 Let's see. I think your best bet is installing a very minimal Debian system (Debian does have bootdisks which allow you to install over the net, if I'm not mistaken) and then updating to Ubuntu. You might experience some glitches, though.

See [http://www.ubuntulinux.org/support/documentation/faq/upgrade-sarge](http://www.ubuntulinux.org/support/documentation/faq/upgrade-sarge). Specially the last comment (**install Debian via floppy, upgrade to Hoary**) seems to be exactly what you want.

Please report on your progress - it might be an interesting thing to write a mini-HOWTO about.

By the way, why do you think your CD's won't be sent to Israel? AFAIK they do get sent worldwide.

Good luck!! :)

---

### Post by andvaranaut on 2005-04-19
By the way, once you have your mini-Debian system, I think that the next step would be copying your .debs from the XP partition to the /var/cache/apt/archives dir. Note that you will need NTFS support in the kernel to do that.

Best regards

---

### Post by yhotg on 2005-04-19
Devian????!!??? :roll: 
i was thinking to make a minimal mandrake and try again with the lilo install.
i was thinking to to buy a cd wr.  ](*,)  maybe it's time to have one, (in the store they tried to sell me a dvd wr... and i ran away lol)

i will look to that link with the devian thing, the only problem is, and here's a big one, is that here in israel set up internet is something of a headache, and i don't have any idea how to set it up before the system is installed. 

and about the free cd, i'll give it a try, don't know what i'll do with 10 cd ....

yhotg

er.. the last post i didn't understand no word.
but let's go step step. if i get there i'll ask u what was that again. ok?
i'm reading the post of that link and looks pretty advanced, pretty for brave souls, and with too much critical errors while installing that i have no idea what to do with them .
but what i said. i.m looking at it.
(and maybe tomorrow ill buy that cd wr.
or the dvd wr? what's the practical diference? lol

---

### Post by andvaranaut on 2005-04-19
> **yhotg]Devian????!!??? :roll: 
i was thinking to make a minimal mandrake and try again with the lilo install.[/quote]

What is 'the lilo install'? :P

If you must install Ubuntu from anything non-Ubuntu, Debian is the way to go. Ubuntu is Debian-based, so that your chances of success are much higher (ie. not zero :P) Mandrake is rpm-based, so you are basically stuck if you want to update to something apt-based. Then again, I might be wrong :P

> 
i was thinking to to buy a cd wr.  ](*,)  maybe it's time to have one, (in the store they tried to sell me a dvd wr... and i ran away lol)

Do. A DVD writer will also allow you to write CD's, by the way. It is the simpler solution  said:**
> 
i will look to that link with the devian thing, the only problem is, and here's a big one, is that here in israel set up internet is something of a headache, and i don't have any idea how to set it up before the system is installed. 


Don't know anything about Israeli Internet, but you could always copy the configuration files over. They will probably be short.
> 
and about the free cd, i'll give it a try, don't know what i'll do with 10 cd ....

Use 1 to install Ubuntu, and give 9 out to friends and relatives ;)

> 
i'm reading the post of that link and looks pretty advanced, pretty for brave souls, and with too much critical errors while installing that i have no idea what to do with them .

It is, but then again is the only thing I can think of :P

Good luck!

---

### Post by yhotg on 2005-04-19
to use devian means i have to download it, and see if there is a hd installation, because if not no way.
then i need to learn to use devian
and then put kubuntu
mandrake iso is already in my computer and i know a little of it.

the problem with the dvd wr is that the price is 3 times the price of the cd wr

it looks like a lot of money and can't yet imagine for what i want to copy to dvd

---

### Post by andvaranaut on 2005-04-19
[QUOTE=yhotg]to use devian means i have to download it, and see if there is a hd installation, because if not no way.[/quote]

There is a HD installation, I'm rather sure of it. You could also use debootstrap.
> 
then i need to learn to use devian
and then put kubuntu

Agreed. You don't need much knowledge of debian, though. 
> 
mandrake iso is already in my computer and i know a little of it.

If you don't feel comfortable with messing with the command line and with the internals of the installation process, I'd just stick with Mandrake until your CD arrives.
> 
the problem with the dvd wr is that the price is 3 times the price of the cd wr

it looks like a lot of money and can't yet imagine for what i want to copy to dvd

Then buy a cd writer if you can. They are rather cheap these days and are very useful for backups.

Other options include getting some friend of you, or a nearby cybercafé, to burn the ISO for you.

I have seen a method which allows you to install Ubuntu starting with Knoppix  at [http://www.ubuntulinux.org/wiki/InstallFromKnoppixHowto](http://www.ubuntulinux.org/wiki/InstallFromKnoppixHowto), but it seems rather complex. And maybe you don't have the Knoppix CD, to start with.

Finally, what do you have to do to connect to the Internet? Maybe it is easier than you thought. Then you might be able to use the Debian net installer, after all..

However, I repeat again: *If you don't feel comfortable with messing with the command line and with the internals of the installation process, I'd just stick with Mandrake* for the time being. Installing an OS is a complex task, specially when done from within another. I agree that it would be nice if Ubuntu could be installed from the HD, but unfortunately its installer was not designed to do it, AFAIK. Maybe this possibility will arrive someday - for now, it looks like a rather advanced task (but not impossible if you are adventurous).

Cheers

---

### Post by yhotg on 2005-04-19
thanks for your help.
i read the knopix post, really complex, and againg, don't have the cd.
yes tomorrow i'll buy the cd and learn how to make a cd installer form the kubuntu.iso

i think i'll do that and in the meantime stick to mandrake.
yeah.
i have a nice feeling for it, it was the first one i got to install without problems and starting understanding it. i like the rpm too. 
that's something that bother me, i don't know how is the kubuntu way of managing packages, if there r any but if it is suppouse to be easier then there musn't be a lot of compile from source right?

well ty very much

yhotg

---

### Post by andvaranaut on 2005-04-22
Hey yhotg

See [http://www.ubuntuforums.org/showthread.php?t=28948](http://www.ubuntuforums.org/showthread.php?t=28948) , it might be what you want.

Cheers

---

### Post by yhotg on 2005-04-25
man! thank u that roks.

lolllllll
i just finished before the weekend to burn the cd installer after i finally bought the cd wr. lol

so now i am ready to go for the normal cd install...., but i am so so tempted of trying that hd installation. after i wanted it so much lol
that was good.

thank you very much andvaranaut.
I think  i'll go for the "normal" cd installation and then i'll come here to say what happened.

wow life's so funny some times.

yhotg
ty very much again.

---

