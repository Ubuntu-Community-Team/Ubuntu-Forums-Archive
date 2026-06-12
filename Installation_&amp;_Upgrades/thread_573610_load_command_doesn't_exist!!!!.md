---
title: "load command doesn't exist?!?!!!?"
date: 2007-10-11
forum: Installation &amp; Upgrades
---

### Post by Stylized on 2007-10-11
hi everybody!

i'm installing now my wireless card's drivers
and there is a step where i should do this:

```

7> $load                
    #[kernel 2.4]
    #    $/sbin/insmod rt61.o
    #    $/sbin/ifconfig ra0 inet YOUR_IP up
        
    #[kernel 2.6]
    #    $/sbin/insmod rt61.ko
    #    $/sbin/ifconfig ra0 inet YOUR_IP up

```

so i typed in the command line:
```

sudo load /sbin/insmod rt61.ko

```

and this what i got:
```

bash: load: command not found

```


how can i fix this problem?
how can i make the load command work on ubuntu 7.04?

PLEASE help me =(

---

### Post by murlosad on 2007-10-11
I don't think you actually need to type 'load', anything locate in /sbin/ is a command in and of itself. so try just typing ```
/sbin/insmod rt61.ko
``` or even just ```
insmod rt61.ko
```

if that works do the same with the ifconfig command

---

### Post by Stylized on 2007-10-11
here what i got:
```

insmod: error inserting 'rt61.ko': -1 operetion not permited

```

and i tried also to type
```

sudo

```

before the function...

do you know what is the problem here?
(by the way thanks for helping anyway..)


p.s.
in this line:
```

/sbin/ifconfig ra0 inet YOUR_IP up

```

which IP address do you think i need to enter?

---

### Post by murlosad on 2007-10-11
it looks like that ifconfig command is trying to set a static ip address, so you should be able to enter whatever whatever you want (e.g 192.168.1.50) or something like that. 

btw, you might be better off posting this question in the wireless subforum: [http://ubuntuforums.org/forumdisplay.php?f=136]("http://ubuntuforums.org/forumdisplay.php?f=136")
that's where all the gurus hangout...

---

### Post by Stylized on 2007-10-11
Ok **_thank you_**!!!!

---

