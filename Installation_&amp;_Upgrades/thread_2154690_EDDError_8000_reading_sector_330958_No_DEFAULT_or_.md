---
title: "EDD:Error 8000 reading sector 330958 No DEFAULT or UI configuration directive found"
date: 2013-06-15
forum: Installation &amp; Upgrades
---

### Post by Metrik on 2013-06-15
Hello,
I am try to install ubuntu 12.04 i386 server. 
but am running into some problems.
first 
i am try to install on a SuperMicro SuperServer6022P-6. 
it has 3 hard drives in it (2 and 3 are the same kind)
1. HITACHI 36 gb
2. IBM 18.4 gb
3.IBM 18.4 gb
it also has Adaptec Raid Controller (asr - 2000s /48 mb).
If you need more info just let me know.
next
i am try to install ubuntu 12.04 i386 from a live boot cd.
i downloaded ubuntu from their web site and burn the iso image to the disc i want to use.
then i place it in the supermicro compact disc slot.
i then boot up the supermicro and it just go to a black screen with the flashing curser and then it give me an ERROR (EDD:Error 8000 reading sector 330958 No DEFAULT or UI configuration directive found!)
and then it sits on a black screen with the word boot: and a flashing curser after it.
not sure on what to do here.
any help would be great.
Thanks Every One!

---

### Post by mörgæs on 2013-06-15
The EDD-error only appears for CD drives. Have you tried booting from USB?

---

### Post by Metrik on 2013-06-15
Ya i have try to but it cant find it on boot. kinda like it does not have the abilities to.

---

### Post by mörgæs on 2013-06-16
Can you install using the [minimal ISO]("https://help.ubuntu.com/community/Lubuntu/Documentation/MinimalInstall")?

---

### Post by Metrik on 2013-06-23
Getting closer!
When i start to install every thing seem to be fine.
1.Select language :ok
2.select location :ok
3.configure keyboard :ok
4.network config :ok
then it gets stuck on a purple screen with nothing in it and a white/black bottom that  it lets me type in but nothing else happens.

---

### Post by mörgæs on 2013-06-24
What exactly did you try to install?

---

### Post by gordintoronto on 2013-06-24
Have you checked the checksum? Have you tried a different CD reader?

---

### Post by Metrik on 2013-06-24
[TABLE]
[TR]
[TD][FONT=inherit]13.04 Raring Ringtail[/FONT][/TD]
[TD][FONT=inherit][32 bit mini ISO]("http://archive.ubuntu.com/ubuntu/dists/raring/main/installer-i386/current/images/netboot/mini.iso")[/FONT][/TD]
[/TR]
[/TABLE]

[TABLE]
[TR]
[TD][FONT=inherit]12.10 Quantal Quetzal[/FONT][/TD]
[TD][FONT=inherit][32 bit mini IS]("http://archive.ubuntu.com/ubuntu/dists/quantal/main/installer-i386/current/images/netboot/mini.iso")[/FONT][/TD]
[/TR]
[/TABLE]

[TABLE]
[TR]
[TD][FONT=inherit]12.04 Precise Pangolin[/FONT][/TD]
[TD][FONT=inherit][32 bit mini ISO]("http://archive.ubuntu.com/ubuntu/dists/precise/main/installer-i386/current/images/netboot/mini.iso")[/FONT][/TD]
[/TR]
[/TABLE]

[COLOR=#333333][FONT=Ubuntu]12.04 Precise Pangolin 32 bit non PAE.
[/FONT][/COLOR][COLOR=#333333][FONT=Ubuntu]
[/FONT][/COLOR]Thanks for the Reply [[COLOR=#C61919]mörgæs[/COLOR]]("http://ubuntuforums.org/member.php?u=939075")[COLOR=#000000][/COLOR]

---

### Post by Metrik on 2013-06-24
How do You use checksum? and no but i will try a different cd reader.
Thanks for the Reply [[COLOR=#000000]gordintoronto[/COLOR]]("http://ubuntuforums.org/member.php?u=507940")[COLOR=#000000][/COLOR]

---

