---
title: "X server error when install ubuntu"
date: 2007-09-17
forum: Installation &amp; Upgrades
---

### Post by qkwing on 2007-09-17
Hi all,

    I'm a newbie in Linux and I've tried to install ubuntu in my new laptop (a Hp 8510w). I've got many problems :

    First, I got an error before getting into the graphic mode :

   ```
 /bin/sh can&#8217;t access tty; job control mode off
```

   And I tried this solution :

  ```
At the LiveCD initial boot screen:
o Select F6 for more options
o Add the following option to the beginning of the options list:
break=top
o Press enter to start booting
Ubuntu will start booting, but kick you out to a command prompt; at the prompt type these two commands:
modprobe piix
exit
```

    It works, I can pass the first phase,but when loading gnome desktop, I got another error :

    ```
x server error:
screen found, but not found a usable configuration
```

    So my question is : is this error normal? I've not found much info about this kind of error. And is it possible to install Ubuntu in text mode only?Thanks for your replies.

Wei.

---

### Post by w4ett on 2007-09-18
Here is the Alternate Install CD download link...(be sure to tic the box below the "Start Download" to select the Alt Install CD:

[http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)

---

### Post by ibison on 2007-10-09
> **qkwing said:**
> Hi all,

    I'm a newbie in Linux and I've tried to install ubuntu in my new laptop (a Hp 8510w). I've got many problems :
...

    It works, I can pass the first phase,but when loading gnome desktop, I got another error :

    ```
x server error:
screen found, but not found a usable configuration
```

    So my question is : is this error normal? I've not found much info about this kind of error. And is it possible to install Ubuntu in text mode only?Thanks for your replies.

Wei.

I am in the same position with a new hp 8510w and had no response from the CD at install time. (The solution proposed above is just a link to the (standard) download of Ubuntu 7.04 which is what I am already using.) Wei: did you find a solution to the X server error?

---

### Post by forestpixie on 2007-10-09
> The solution proposed above is just a link to the (standard) download of Ubuntu

only if you don't do as instructed

> be sure to tic the box below the "Start Download" to select the Alt Install CD

---

### Post by ibison on 2007-10-09
> **forestpixie said:**
> only if you don't do as instructed

You are quite correct. I was wrong. Sorry!

---

### Post by forestpixie on 2007-10-09
don't be sorry :) - I assume you've got it sorted

---

### Post by ibison on 2007-10-10
Thanks - but not yet. The alternative text-based installation certainly did help in getting me further down the path. But the installation failed at partition time, returning with "an unknown error". I'll try doing the partition myself beforehand and then try again. Thanks for your help.

---

### Post by forestpixie on 2007-10-10
i do my partitioning using the [gparted]("http://gparted.sourceforge.net/") livecd

if you can I'd suggest having 3 partitions if you have room 

one for root, mount as / in the install
one for home, mount as /home
one for swap,

I have 8Gb for root, 1Gb for swap and rest as home - just an idea though

---

### Post by ibison on 2007-10-11
Thanks, I am repartitioning right now using the gparted livecd ...

---

