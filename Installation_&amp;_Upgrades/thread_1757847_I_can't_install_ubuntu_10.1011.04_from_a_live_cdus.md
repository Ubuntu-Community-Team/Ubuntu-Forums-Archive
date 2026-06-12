---
title: "I can't install ubuntu 10.10/11.04 from a live cd/usb"
date: 2011-05-13
forum: Installation &amp; Upgrades
---

### Post by Dannysbkn on 2011-05-13
Hello to everyone. I'm Daniel and i had have a account in ubuntu forums since 2009 or 2008, i don't remember(in my settings says that i joined in on 2008...well it doesn't matter xD).
The point is, that i've never had a install problem with ubuntu or some derivate, from 7.10 to 10.04...until 10.10, and only in this PC(Take note that the only version i'd use in this PC was 10.04).
Everything started last summer(winter for northern hemisphere). I deleted all from my hdd to do a clean installation, i'd put the cd and appears something that i'd never seen before in a live cd, the login screen. I'd think that the user was 'ubuntu' and the password 'ubuntu' too, or nothing, letting the camp in blank. But it didn't works. I searched in internet for similar cases, but for that persons it worked, for me not.
Then i'd try to install kubuntu, and happened the same; i'd try with ACPI mode off(and/or with other options from the F6 menu) and i'd can enter!, but it'd freeze at the installation screen. That was so strange, and more when i tried with 32 bits versions...it worked!(the live cd. I don't know if worked the installator, i don't want to install a 32 bits version).
Later of that, i told me, it should be a version problem, or kernel, maybe on the following one it will be fixed.
This week i donwloaded the image of the 11.04 version and later of pass it to an usb, i started this pc with the usb in, it started to load and...the login screen again... =/

Actually i don't know what is causing this problem, but i see that it stills on the new version.
I don't remember exactly what messages appears on the without splash's start up(i forget the name xd...quiet splash?), but if they are needed i'll upload them(That will be the most probable, but i don't know how to copy them from that part to a .txt or similar).
My PC Settings:
·Motherboard: Intel DX58SO
·Cell: Intel Core i7 920
·RAM: Kingston 4 GB 1333 mhz
·Video Card: EVGA GTX 275
·I think that there isn't more important information, if i forget something, told me.

Too, like extra information, i didn't try with the alternate's versions or with another distribution.
I will be really grateful if you can help me to solve this problem that don't let me use ubuntu for half year!
Thanks in advance!

P.S.=If there is some problem with some word, tense or similar. I apologize, i'm not native english speaker. I'm spanish native speaker, and english and portuguese(So so so so basic XD) learner :D.
Si alguien habla español, mejor, así le cuento un poco mejor la situación. (Ou tambén se fala no português...é uma piada XD, Mesmo eu não posso falar muito bem(*Thanks google translate for the last part xD)).

---

### Post by Hedgehog1 on 2011-05-13
Dannysbkn,

Because a number of LiveCDs and the LiveUSB all give you the same result, I think that you are not actually booting from any of them. Instead, I think that you did not get your hard drive cleaned and are getting a remnant of your earlier installed OS coming up off the hard drive each time.

To actually get the PC to boot off the LiveUSB or LiveCD, you may need to use a function key during right after the Bios POST (Power On Self Test) 'Beep' to get the 'Boot Selection' Menu from the BIOS of this motherboard.

The boot selection menu will list your hard drive(s) and any CD or Bootable USB drive you have inserted. You will then have to select the LiveCD or LiveUSB you want.


***The Hedge***

:KS

---

### Post by Dannysbkn on 2011-05-13
Thanks for reply so fast Hedgehog1
It isn't exactly the same problem with all the live cds and usb, and sometimes i can "log"(the automatic log) in, but on the installator screen it freezes.
I have cleaned my hdd several times, now it have windows 7 installed and no rastre from an old linux partition. In fact, i did tried to log in without the hdd inside.
I think the problem goes by other part.

---

### Post by NormanFLinux on 2011-05-13
Confirmed bug with Ubiquity:

Installer won't advance. This affects ALL versions of Ubuntu desktops.

---

### Post by Hedgehog1 on 2011-05-14
> **Dannysbkn said:**
> Thanks for reply so fast Hedgehog1
It isn't exactly the same problem with all the live cds and usb, and sometimes i can "log"(the automatic log) in, but on the installator screen it freezes.
I have cleaned my hdd several times, now it have windows 7 installed and no rastre from an old linux partition. In fact, i did tried to log in without the hdd inside.
I think the problem goes by other part.

OK - based on that addition information, I would agree that my first guess was wrong.

If **NormanFLinux** is correct, can you use the alternate installer CD to load Ubuntu?  It has no 'try' option, so it might get you past the 'bug' and let you install.

***The Hedge***

:KS

---

### Post by Dannysbkn on 2011-05-14
I'll try it. I didn't use it because, by my computer settings, i think that the problem have no relation with that and i discarded it. That is why i'd lose a lot of time searching for a solution for install ubuntu with the live cd.
If it works, then the new ubuntu's live cds come with a problem, although, how i said, i didn't find someone with this problem too and with 10.04 version and olders it don't happend.
Tomorrow i'll donwload it.
Goodnight

---

### Post by Dannysbkn on 2011-05-21
I have been a little busy this week, the following one i'll be free on wednesday's afeternoon.
I have to backup the bit information that i'd save on the PC those months with windows 7 installed, that's the problem. So next wednesday i'll try it and tell you what's going on.

Oh, i'd forgotten, i'd try to enter with the alternate cd, and i can go until the installer section...but i don't if it works for the reason i told above.

Bye

---

### Post by Dannysbkn on 2011-07-21
Hello to everyone again
Later all this time(Since May) i have time enough to solve this problem...
I have been playing with different options, but it still doesn't work, with 10.10 and 11.04, although with 11.04 have happened so strange thing, such: With **Ubuntu** the first time i used the Live USB it works! at least the "live" mode, because i didn't try the "install" mode, but all only in the first boot(well there's was 2), in the followings it doesn't work anymore until now. With **Kubuntu** it works too, but only "live" mode, i try to enter to "install" mode and it seems like it is loading, but nothing happens(i'd let it about 20-30 minutes and nothing...).
This is so strange, because i donwloaded the last versions of Fedora, openSUSE and Debian. All works...But with ubuntu(kubuntu too) works all versions(9.10, 10.04 i have tried) except 10.10, 11.04.
-Like additional information:
On the loading screen appears lines like:
·"invalid user 'ubuntu'"
·"unknown user 'ubuntu'"
·After all loads, appears "Authentication Failure"
Before the "authentication failure" line, the system load the nouveau driver(i'd supposed this would be the cause of the problem, i tried forcing with 'xforcevesa' but, or i puted it in the wrong place or it doesn't work) and the wireless mouse & keyboard.

This it's coming frustrating...much time has passed since this problem began, i can't find a solution!
What could it be =/?
Thanks for your answers in advance :)

PS=No, i haven't try with alternate cd yet

---

### Post by Dannysbkn on 2011-07-23
UPDATE: I have finally tried the alternate cd...it doesn't work =/, i could only get to the Hour Settings screen, after that, the "window" dissapears, leaving only a blank screen.
I tried to see the "log"(I don't know, it something like that, appears at pressing Alt+Fx...don't remember what number :B) and in the last lines appears something like "Partman: Detecting(or Analazing) physical drives. This may take a while" and over that "Not Matching Physical drives".
I don't know if that have some relation with the error, but i expected to reach at least to the HDD Settings Screen or get it installed with some error or similar...
Again i ask, What could it be?

UPDATE 2: I have just remember something, before(or after...) i try to install ubuntu 10.10, i updated my BIOS. Now i updated it again, to the last version, maybe it going to make it works...i'm going to see now

UPDATE 3: No...It doesn't work =/

---

