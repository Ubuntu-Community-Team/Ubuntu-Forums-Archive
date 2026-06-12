---
title: "Installing Linux on my Pentium M laptop"
date: 2015-01-23
forum: Installation &amp; Upgrades
---

### Post by gordie692 on 2015-01-23
I'm trying to help my friend out he has a Pentium M Laptop older of coarse and I couldn't instal Ubuntu or Mint I was able to install 32 bit Mageia but wanted something for newbie because had Windows XP on and no wifi when I tried Ubuntu or Mint it started the purple screen of Ubuntu then that was it and with Mint it took me too the count down. When I googled the laptop it something about PAE and CPU support so I was going to Mint Debian it said it was non PAE support any help on this can't figure out why Mageia works though

---

### Post by sudodus on 2015-01-23
Pentium M may or may not have a PAE flag. Most of those processors lack a PAE flag, but have PAE capability. Lubuntu 14.04.1 LTS works fairly well, but must be installed with the boot option forcepae according to this link

[https://wiki.ubuntu.com/Lubuntu/AdvancedMethods#Pentium_M_and_Celeron_M](https://wiki.ubuntu.com/Lubuntu/AdvancedMethods#Pentium_M_and_Celeron_M)

But there can be other problems too. Please specify your computer

- Brand name and model
- CPU
- RAM (size)
- graphics chip/card
- wifi chip/card

And it will be easier to give relevant help. See also the following link
[URL="http://ubuntuforums.org/showthread.php?t=2130640"]
Old hardware brought back to life[/URL]

---

### Post by gordie692 on 2015-01-23
Its a friends and doesn't say much on it but the model number on back is CL51 sorry I tried Lubuntu 32 bit but didn't work

---

### Post by QIII on 2015-01-23
Is this the one?

[http://www.amazon.co.uk/gp/aw/d/B008YXJ470/ref=redir_mdp_mobile/280-3796890-4709131](http://www.amazon.co.uk/gp/aw/d/B008YXJ470/ref=redir_mdp_mobile/280-3796890-4709131)

---

### Post by tokyobadger on 2015-01-23
looks like it might be an Acer Travelmate of some type;
Celeron M 1.3GHz also with Pentium M to 1.6GHz
RAM 512M - 1G

Ball's in your court - load up a livedvd/usb and find out what's in there.

Out of interest does your friend actually want linux/ubuntu/lubuntu?

---

### Post by sudodus on 2015-01-23
> **gordie692 said:**
> Its a friends and doesn't say much on it but the model number on back is CL51 sorry I tried Lubuntu 32 bit but didn't work

Please give us more details: How far did it reach in the boot process? How did it fail?

Knowing a bit more makes it possible to give better advice.

Otherwise we can only give very general advice like this:

Try ***Wary Puppy***, which is known to work well with really old hardware. ***TahrPup*** might work well too, but might need slightly newer computers. When Puppy linux is running it will also be possible to get more information about the computer ...

---

### Post by gordie692 on 2015-01-23
that last post of of picture is correct and it had a 40 gig gig hard drive but I put in a 80 gig and its got 2 512's in for ram mageia 4 runs good in but anyways when I put the 32 Ubuntu 14.04 in it started the like purple screen with icon on bottom then blank when I put Mint 17.1 32 in it started with Mint count down to 10 then the screen freezes I was was going to try Mint Debian 32 due to its a non pae distro or so it says

thanks guys

---

### Post by sudodus on 2015-01-23
So there is 1 GB RAM? That should be good for Lubuntu.

If Ubuntu gets to 'the like purple screen with icon on bottom' you don't have any problem with PAE (because it would stop earlier if the PAE issue would stop it).

There might be problems with the graphics. You could try with the boot option **nomodeset**. See this link [BootOptions - Official Ubuntu Documentation]("https://help.ubuntu.com/community/BootOptions")

There might also be problems because of too low RAM for standard Ubuntu. You should really ***try Lubuntu instead of standard Ubuntu***. Stay with the version 14.04.1 LTS  (32-bit) also with Lubuntu.

---

### Post by gordie692 on 2015-01-23
tried Lubuntu 32 but didn't but I tried the Linux Mint Debian edition 32 and it's installing as we speak

---

### Post by MAFoElffen on 2015-01-24
No matter the brand-- if you can post the results of:
```

cat /proc/cpuinfo

```
Under the "flags" section will display the cpu features, like this example:
```

flags	: fpu de tsc msr [COLOR=#ff0000]pae[/COLOR] cx8 apic sep cmov pat clflush acpi mmx fxsr sse sse2 ss ht syscall nx lm constant_tsc rep_good pni ssse3 cx16 sse4_1 lahf_lm

```
The Dothan series was mod'ed in 2005 to add PAE (Sonoma chipset). Previous versions didn't have PAE.

---

### Post by sudodus on 2015-01-24
Let us hope that Mint will work :-)

 But I think Mint Debian is a rolling release, which makes it more prone to break - it takes more skill to run it and repair it than standard Mint or standard Lubuntu.

> **Upstream issues**

      LMDE is based on Debian Testing. Make sure to read the [known issues related to it]("http://bugs.debian.org/release-critical/").



---

### Post by gordie692 on 2015-01-24
Well to the drawing boards this laptop is giving me grieve I thought it installed linux mint debian 32 bit but didn't tried lubuntu, xubuntu and keeps saying something cpu not supported I even tried W7 disk I have and it said the same aslo. Tried my vista and it loads aswell as my xp but no security of coarse.

---

### Post by sudodus on 2015-01-25
I think Lubuntu 14.04.1 LTS will work fairly well, but it must be installed with the boot option **forcepae** according to this link

[https://wiki.ubuntu.com/Lubuntu/Adva..._and_Celeron_M]("https://wiki.ubuntu.com/Lubuntu/AdvancedMethods#Pentium_M_and_Celeron_M")

You need forcepae also in order to run Lubuntu 14.04.1 LTS live
[URL="http://ubuntuforums.org/showthread.php?t=2230389"]
Try Ubuntu (Kubuntu, Lubuntu, Xubuntu,  ...) before installing it[/URL]

---

### Post by gordie692 on 2015-01-29
Good news guys, I got the mint debian working on this pentium M laptop it was my error on the partitioning part but its working great I really didn't want to put vista on this and I put my W7 32 bit Home premium disk on and it didn't support it either so anyways working awesome like a linux machine thanks guys

this linux mint debian that should be a support OS due to it's from debian it should be like debian and have rolling release right

---

### Post by sudodus on 2015-01-29
> **gordie692 said:**
> ...
this linux mint debian that should be a support OS due to it's from debian it should be like debian and have rolling release right

Yes.

I'm glad it works well for you :-)

Please click on **Thread Tools** at the top of the page and mark this thread as SOLVED

---

