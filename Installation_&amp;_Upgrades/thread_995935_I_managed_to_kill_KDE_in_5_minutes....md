---
title: "I managed to kill KDE in 5 minutes..."
date: 2008-11-28
forum: Installation &amp; Upgrades
---

### Post by Auraomega on 2008-11-28
Ok joking aside, I've had quite a few problems since installing 8.10, first it wouldn't install, then I got it installed but GRUB refused to boot it, then when it was working the screen flickered, fixed that but it refused to connect to a network to download drivers, finally got the internet working but nVidia drivers refused to work, finally got that fixed and all was calm... so I turned on desktop effects and KDE blanked out on me, and I've been unable to get it booting since :lolflag:

When I log in it just hangs me on either a black or a white screen, pressing ctrl+alt+backspace returns me to the login screen so no PC crashes. I didn't get chance to enable root so I can't log in and create a new acount which is my normal call on situations like this. I've tried the 3 different session types, default, KDE, and failsafe to see if it would boot, obviously default and KDE both hang, and failsafe returns an error saying it cannot find something or other, and gives me no choice but to "abort", upon aborting the screen goes black and gets filled with lots of random charactors and colours. I can access the command line but I've not been using Ubuntu long, and I'm brand new to KDE so I have no clue what to search for to fix.

*Please* help me, I'm having to use Windoze now :mad:

-Aura

---

### Post by Auraomega on 2008-11-28
Sorry, but bump...

-Aura

---

### Post by cataboo on 2008-11-28
Sorry but help from me is doubtful. Im new to the computer, new to Ubuntu,and nearer to nutsville  by the minute.I dont think I'll ever get this down.But at  least I'm not getting it so much faster than with Microdoze as you called it. Good Luck:):lolflag:

---

### Post by AlanR8 on 2008-11-28
Would be useful to know what hardware you're running.....

---

### Post by fifth on 2008-11-28
Can't really help with your problem as such, but if you want to try creating a new account as you suggest, you can still do this from the command line with;
```
sudo useradd -d /home/guest -m guest
```
Where 'guest' is the name of the new user account, and ...
```
sudo passwd guest
```
to set a password for the new account.

---

### Post by Auraomega on 2008-11-28
> **AlanR8 said:**
> Would be useful to know what hardware you're running.....

Various, I've tried it on a couple of PCs (I have the funky USB to IDE cables so its easy for me to do), same problem on them all.

@fifth:

I'll give that a shot now and hopefully that'll work.

-Aura

No luck, created the new account but now theres more errors when trying to boot into it, I think it'll just be easier to restart from scratch... again... Were there many problems with Kubuntu 8.04? I'm tempted to use that instead as I never had any serious issues on that version of Ubuntu.

---

