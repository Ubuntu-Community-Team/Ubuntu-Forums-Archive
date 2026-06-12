---
title: "Can't get phpsysinfo to work."
date: 2016-04-18
forum: Installation &amp; Upgrades
---

### Post by Raymond Day on 2016-04-18
Got a new install of **Ubuntu 16.04 LTS (GNU/Linux 4.4.0-18-generic x86_64)** or this name of it "**Lubuntu 16.04 (Xenial Xerus)**".

I did a **apt install phpsysinfo** and did a aliases from /phpsysinfo to /usr/share/phpsysinfo in Apache.

When I got to it's [http://192.168.2.109/phpsysinfo](http://192.168.2.109/phpsysinfo) it changes the URL to [http://192.168.2.109/phpsysinfo/index.php?disp=dynamic](http://192.168.2.109/phpsysinfo/index.php?disp=dynamic) and says:

The 192.168.2.109 page isn&#8217;t working

192.168.2.109 is currently unable to handle this request.
500

For a sec looks like Apache displays it but then gives this error.

Been working on this for hours looking on Google for help and still can't fix it. So I came here to ask.

This my help the last line in Apache error log says this:

```
[Mon Apr 18 03:08:51.570634 2016] [:error] [pid 10763] [client 192.168.2.81:56835] PHP Fatal error:  Uncaught Error: Call to undefined method Error::singleton() in /usr/share/phpsysinfo/includes/output/class.Output.inc.php:40\nStack trace:\n#0 /usr/share/phpsysinfo/includes/output/class.Webpage.inc.php(61): Output->__construct()\n#1 /usr/share/phpsysinfo/index.php(56): Webpage->__construct()\n#2 {main}\n  thrown in /usr/share/phpsysinfo/includes/output/class.Output.inc.php on line 40
```

Any one know what is wrong?

-Raymond Day

---

### Post by wind_racer on 2016-04-19
I just ran into the same problem. Looks like it's fixed in a newer version of phpsysinfo:

[https://github.com/phpsysinfo/phpsysinfo/issues/117](https://github.com/phpsysinfo/phpsysinfo/issues/117)

---

### Post by Raymond Day on 2016-04-20
I went there just said to update phpsysinfo but I don't know how. I did this command:

git clone [https://github.com/phpsysinfo/phpsysinfo.git](https://github.com/phpsysinfo/phpsysinfo.git)

But it's still the same "page isn't working" error.

How do I install the newer version of phpsysinfo?

-Raymond Day

I went there just said to update phpsysinfo but I don't know how. I did this command:

git clone [https://github.com/phpsysinfo/phpsysinfo.git](https://github.com/phpsysinfo/phpsysinfo.git)

But it's still the same "page isn't working" error.

How do I install the newer version of phpsysinfo?

-Raymond Day

I got it working!

renamed the /usr/share/phpsysinfo folder to phpsysinfo~ then cd to /usr/share and did a **git clone [https://github.com/phpsysinfo/phpsysinfo.git](https://github.com/phpsysinfo/phpsysinfo.git)** Then copied the link in phpsysinfo~ of phpsysinfo.ini to the new phpsysinfo and now it works!

I guess a apt upgrade would of worked with time.

Thank you.

-Raymond Day

---

### Post by mörgæs on 2016-04-20
Good, please mark the thread 'solved'.

---

