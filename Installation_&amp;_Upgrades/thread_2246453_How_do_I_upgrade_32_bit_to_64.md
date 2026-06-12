---
title: "How do I upgrade 32 bit to 64?"
date: 2014-09-30
forum: Installation &amp; Upgrades
---

### Post by hai3 on 2014-09-30
I just installed Ubuntu last Sunday. I downloaded the iso by clicking download button on YUMI. I though i was 64bit. I just installed some 64bit software and it wont run!!! I checked and i saw i have a 32 bit OS!!!! I WANNA UPGRADE IT TO 64 NOW!!!!

---

### Post by Bucky Ball on 2014-09-30
Clean install. There is no upgrade from 32bit to 64bit.

Save all data, download 64bit ISO, create install media, boot from it, install. That's it. ;)

---

### Post by hai3 on 2014-09-30
I am an idiot. I need to be in asylum...

---

### Post by hai3 on 2014-09-30
Btw the iso i downloaded end with "amd64" why is it install 32?

---

### Post by sammiev on 2014-09-30
I would suggest downloading from a site like [this]("http://www.ubuntu.com/download/desktop") only.

---

### Post by grahammechanical on 2014-09-30
Why are you so sure that it is a 32bit OS? When I run this command

```
uname -a
```

I see this result

> 3.16.0-6-generic #11-Ubuntu SMP Mon Jul 28 01:59:56 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux

Your kernel will be different but if you see x86_64 then it is 64 bit Ubuntu and perhaps there is another reason why those applications will not run.

Regards.

---

### Post by Bucky Ball on 2014-10-01
> **grahammechanical said:**
> Why are you so sure that it is a 32bit OS? When I run this command

```
uname -a
```

I see this result



Your kernel will be different but if you see x86_64 then it is 64 bit Ubuntu and perhaps there is another reason why those applications will not run.

Regards.

There is this. Check with 'uname -r' in a terminal, as advised ...

---

### Post by hai3 on 2014-10-01
hai@hais-dead-PC:~$ uname -a
Linux hais-dead-PC 3.13.0-36-generic #63-Ubuntu SMP Wed Sep 3 21:30:45 UTC 2014 i686 i686 i686 GNU/Linux
hai@hais-dead-PC:~$

---

### Post by slickymaster on 2014-10-01
> **hai3 said:**
> hai@hais-dead-PC:~$ uname -a
Linux hais-dead-PC 3.13.0-36-generic #63-Ubuntu SMP Wed Sep 3 21:30:45 UTC 2014 **[COLOR=#ff0000]i686 i686 i686 GNU/Linux[/COLOR]**
hai@hais-dead-PC:~$

There you go, it's a 32 bit OS
For your reference```
x86_64 ==> 64-bit kernel
i686   ==> 32-bit kernel
```

---

### Post by Bucky Ball on 2014-10-01
Like the slickymaster states, 32bit. Please reinstall using a 64bit image. There is no way of upgrading 32bit to 64bit.

---

