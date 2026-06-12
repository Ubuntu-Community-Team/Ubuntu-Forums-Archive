---
title: "claws mail crash with lxde since upgrade"
date: 2011-10-17
forum: Installation &amp; Upgrades
---

### Post by DustofDust on 2011-10-17
i use ubuntu, but with lxde as my pc is too slow to run even ubuntu classic desktop, and since the upgrade from 11.04 to 11.10 claws mail crashes when it tries to connect to pop or when i move the mouse pointer over claws.

any ideas about a solution? i did look into logs but didnt find any crash related. if you need further info please say so i can look after it.

---

### Post by DustofDust on 2011-10-23
[https://bugs.launchpad.net/ubuntu/+source/claws-mail/+bug/877739](https://bugs.launchpad.net/ubuntu/+source/claws-mail/+bug/877739)

this is the bugreport

is there someone working on it?

---

### Post by DustofDust on 2011-10-31
im now since 2 weeks without a working mail program... i get angry...

---

### Post by DustofDust on 2011-11-08
since weeks there is no change! it still crashes and is unusable!

---

### Post by DustofDust on 2011-11-13
and? nothing new?

it still crashes and nothing changed! claws-mail is still unusable as it crashes at start without even get usable!

---

### Post by DustofDust on 2011-11-29
it is still unusable and crashes shortly after start

---

### Post by DustofDust on 2011-12-12
no changes and no responses to the bug report...

---

### Post by amjjawad on 2011-12-12
> **DustofDust said:**
> [https://bugs.launchpad.net/ubuntu/+source/claws-mail/+bug/877739](https://bugs.launchpad.net/ubuntu/+source/claws-mail/+bug/877739)

this is the bugreport

is there someone working on it?

Where is it?


> Lost something?
This page does not exist, or you may not have permission to see it.

If you have been to this page before, it is possible it has been removed.

If you got here from a link elsewhere on Launchpad, sorry about that. We’ve recorded the problem, and we’ll fix it as soon as we can.

Otherwise, complain to the maintainers of the page that linked here.

If this is blocking your work, let us know by asking a question at Launchpad Support. Include the error ID in your message.


---

### Post by amjjawad on 2011-12-12
To continue our discussion ... have you looked at this:
[http://www.claws-mail.org/](http://www.claws-mail.org/)

Check FAQs, report the problem here: [http://www.thewildbeast.co.uk/claws-mail/bugzilla/index.cgi](http://www.thewildbeast.co.uk/claws-mail/bugzilla/index.cgi)

1) Is it the only application that crashed after the upgrade?

2) Try to open the terminal and type:

```
claws-mail

```

then please post the output here and make sure to wrap up the output with "CODE" tags OR highlight the output and click on "#".

[IMG]http://ubuntuforums.org/picture.php?albumid=2161&pictureid=8148[/IMG]


3) Have you considered to remove it and re-install it again? just make sure to backup your emails. I never use such programs, I prefer web-based email.

4) You mentioned that your machine is slow/old so how slow/old is it?
If Ubuntu is slow for you, try Lubuntu as a normal installing, NOT just install the desktop package.

That's all what I can think about right now :)

---

### Post by DustofDust on 2011-12-13
1) the game barrage also crashes but installed it only recently so dont know if its broken since long time like sabre.

2) for claws-mail i did also another bug report which is here and someone did set it to public [https://bugs.launchpad.net/ubuntu/+source/claws-mail/+bug/900656](https://bugs.launchpad.net/ubuntu/+source/claws-mail/+bug/900656)

```
:~$ claws-mail
claws-mail: /build/buildd/cairo-1.10.2/src/cairo-surface.c:1287: cairo_surface_set_device_offset: Assertion `status == CAIRO_STATUS_SUCCESS' failed.
&#65533;y&#65533;y\:\?)Aborted (core dumped)
```

3) i use claws-mail since a year and it worked fine after the 11.04 upgrade but not after this. if you have a lot of mail accounts and some hundreds thousands of mails and sometimes you get 1000 mails a day you dont want webmail ;)

4) amd xp 1700+, 512mb and ati rage2

i would need to make a full backup before i can make a clean install of lubuntu. btw have a look at the browser midori [http://www.twotoasts.de/](http://www.twotoasts.de/) which is more lightweight than chromium

thanks for your help :)

---

### Post by amjjawad on 2011-12-13
> **DustofDust said:**
> 1) the game barrage also crashes but installed it only recently so dont know if its broken since long time like sabre.

Some users got problems when they upgrade and some other don't. Perhaps you are one of the unlucky group but that doesn't mean to give up yet :)
For me, I prefer fresh new installation. I've never done an upgrade.

By the way, do you have a separate /home partition?
 

> 2) for claws-mail i did also another bug report which is here and someone did set it to public [https://bugs.launchpad.net/ubuntu/+source/claws-mail/+bug/900656](https://bugs.launchpad.net/ubuntu/+source/claws-mail/+bug/900656)

```
:~$ claws-mail
claws-mail: /build/buildd/cairo-1.10.2/src/cairo-surface.c:1287: cairo_surface_set_device_offset: Assertion `status == CAIRO_STATUS_SUCCESS' failed.
&#65533;y&#65533;y\:\?)Aborted (core dumped)
```

> claws-mail: /build/buildd/cairo-1.10.2/src/cairo-surface.c:1287: cairo_surface_set_device_offset: Assertion `status == CAIRO_STATUS_SUCCESS' failed.
I put that on google and found many bugs. Honestly, I don't have the time right now to look into each one of them. I suggest to have a look, hopefully you'll find a similar case :)


> 3) i use claws-mail since a year and it worked fine after the 11.04 upgrade but not after this. if you have a lot of mail accounts and some hundreds thousands of mails and sometimes you get 1000 mails a day you dont want webmail ;)
In that case, of course you need such program.


> 4) amd xp 1700+, 512mb and ati rage2

Definitely give Lubuntu a go but make sure to test it and see how good it will be on your hardware. Use Live CD or Live USB. You don't have to install on your HDD to test it with your hardware.

> i would need to make a full backup before i can make a clean install of lubuntu. 

+1

> btw have a look at the browser midori [http://www.twotoasts.de/](http://www.twotoasts.de/) which is more lightweight than chromium

Of course I did and I have used it too with SliTaz but never liked it. Chromium and Firefox has better support and it's a matter of personal opinion. Some prefer Opera, Some prefer Midori and I prefer both Firefox and Chromium.

I'm running Chromium now for 3 days and 10 active tabs on less than 512MB RAM (Lubuntu 11.10) and it never crashed at all.


> thanks for your help :)
You welcome :)

---

