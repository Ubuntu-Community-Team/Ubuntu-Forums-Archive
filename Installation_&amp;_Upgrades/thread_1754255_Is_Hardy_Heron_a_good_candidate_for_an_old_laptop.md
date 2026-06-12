---
title: "Is Hardy Heron a good candidate for an old laptop"
date: 2011-05-09
forum: Installation &amp; Upgrades
---

### Post by ThatCoolGuy220 on 2011-05-09
So my problem is that i installed 10.04 on my compaq nx6315 and it crashes too much i did it like 7 times getting same results even with new downloads.

IDK if i would run on troubles cause is an old release?:KS

---

### Post by collisionystm on 2011-05-09
> **ThatCoolGuy220 said:**
> So my problem is that i installed 10.04 on my compaq nx6315 and it crashes too much i did it like 7 times getting same results even with new downloads.

IDK if i would run on troubles cause is an old release?:KS


You will run into issues with obsolete software, repostitores, old kernels, drivers...etc. you may as well hop in your Delorean. What happens in your 10.04?

---

### Post by ThatCoolGuy220 on 2011-05-09
Ok my laptop reboots too much and some app get closed suddenly

---

### Post by K_45 on 2011-05-09
Check out Debian:

[http://www.debian.org/CD/netinst/](http://www.debian.org/CD/netinst/)

You won't need more than 128MB, preferably 256MB for XFCE .. . .  Hardy Heron is obsolete.

---

### Post by ThatCoolGuy220 on 2011-05-09
I tell you ok

---

### Post by collisionystm on 2011-05-09
> **ThatCoolGuy220 said:**
> Ok my laptop reboots too much and some app get closed suddenly


You have a pretty recent computer. Did you make sure to grab the right video card drivers? Its ati right?

---

### Post by ThatCoolGuy220 on 2011-05-09
lol idk how to check that pretty newb in some stuff but i had run ubuntu before on this PC from were im writing wich is a destop PC

the thing is i installed i386.iso

but mi on laptop  when I type

```
uname -a
```

on the terminal i get This

```
i686
```

IDK if this could be the issue

---

### Post by collisionystm on 2011-05-09
i looked at your laptop specs. It says its an athalon x2 ? It should be 64 bit. Install 64 whenever possible. It has a much better hardware advantage.

---

### Post by IWantFroyo on 2011-05-09
Check your BIOS's chipset voltage. It's likely that it's okay, but still worth a try...
Amp it up as high as the BIOS will let you. I had this problem, and it was fixed like this.

---

### Post by ThatCoolGuy220 on 2011-05-09
:popcorn:You are right its ATI.

im downloading the i686 now in an hour or less i will update 

"Wow these Forums are Fast:popcorn:"

IDK if to change my Thread title...... i will update soon

---

### Post by ThatCoolGuy220 on 2011-05-09
@IWantFroyo

OFFTOPIC:
i would like too on my android 

IN TOPIC:


what should be right voltage and how i check it, My Bios look like this:


Computer Setup                                                        1.20
--------------------------------------------------------------------------
|File|    |Security|    |Diagnostics|    |System Configuraration|
--------------------------------------------------------------------------







                             (Blue Screen)




--------------------------------------------------------------------------
|Configure Systems IDs                                         |<F1=About>
--------------------------------------------------------------------------



IDK where it is and i dont want to get a new laptop soon Please tell me where i should go on that menu

---

### Post by collisionystm on 2011-05-09
You have a compaq. That menu doesn't exist. Put on your ruby slippers dorothy. Run 64 bit 11.04. Yeah it gets a bad rep, but it has the most updated drivers. It works great for me.

---

### Post by irv on 2011-05-09
I have one old laptop I had issue trying to get 10.04 and 10.10 installed on, Then I tried booting with 11.04 live CD and it ran OK. At the time I was booting with the beta release. I tried the install and the OS worked OK, but I ran it in classic desktop. I had some issues with Audacity, and I use this laptop on a sound system so I tried 10.10 again and now it is running great so I am going to leave it just the way it is.

Edit: I would recommend using 11.04 if it will run on your machine. I have it running on a Dell Inspiron 1521 and it runs great.

---

### Post by ThatCoolGuy220 on 2011-05-09
@collisionystm

Roger!.


so my Laptop is powerfull after all, I judged wrong by running an older Distro thinking a new one wouldn`t run.

---

### Post by collisionystm on 2011-05-09
Yes. There is nothing wrong with it lol. I just installed 11.04 on a dell latitude d610. Now that's old. 512 mb of ram and a 1.2ghz intel centrino

---

### Post by ThatCoolGuy220 on 2011-05-09
Hahaha ok its downloading i will mark this as solved after testing it.

---

### Post by irv on 2011-05-09
I always try running the newer releases on old machines, because if I have speed problems I just use a cut down desktop like Xfce. Works for me.

---

### Post by ThatCoolGuy220 on 2011-05-09
@irv

Yes but its not that Old.

---

### Post by irv on 2011-05-09
> **ThatCoolGuy220 said:**
> @irv

Yes but its not that Old.
I know not in this case, but if other have older computers don't be afraid to try the latest releases of any Linux. The point being you can always use a light desktop on older machines.

---

### Post by ThatCoolGuy220 on 2011-05-09
Its copying Files idk if to press forward now

---

### Post by ThatCoolGuy220 on 2011-05-09
Oh! installer crahsed NVM i gonna try to do it again with Unetbootin

---

### Post by ThatCoolGuy220 on 2011-05-09
Done!, Now to give it a drive test

---

### Post by collisionystm on 2011-05-10
> **ThatCoolGuy220 said:**
> Done!, Now to give it a drive test


success?

---

### Post by ThatCoolGuy220 on 2011-05-10
Nope bro 

it runs but it Reboots too much 

with kernel panics and bugs

---

### Post by ThatCoolGuy220 on 2011-05-10
@K_45

Debian wont install its damn hard makes too many questions and at the end stucks at 98%

---

### Post by ThatCoolGuy220 on 2011-05-10
@collisionystm


I have notice something weird if you ask.

After every install i made i get an message telling me that some package arent availble 


I will write them down next time i think have something to do with that

---

### Post by ThatCoolGuy220 on 2011-05-10
Allright i reinstalled 11.04 

And the message disappeared  Also i run it on clasic without efects and i Erased Firefox and installed Ephiphany Browser instead...........


Its very Stable i admit Thx Guys.

---

### Post by collisionystm on 2011-05-10
> **ThatCoolGuy220 said:**
> @collisionystm


I have notice something weird if you ask.

After every install i made i get an message telling me that some package arent availble 


I will write them down next time i think have something to do with that


It probably could not get on the internet to update

---

