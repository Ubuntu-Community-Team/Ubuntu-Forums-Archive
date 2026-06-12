---
title: "how to upgrade Ubuntu 18.04 to Ubuntu 18.10"
date: 2019-02-17
forum: Installation &amp; Upgrades
---

### Post by Saovry on 2019-02-17
Could you tell me how to upgrade from Ubuntu 18.04 to Ubuntu 18.10 in Lunux?

If I used Ubuntu 18.10, it will support webmin with the latest version, PHp 7.3, mysql 8 and latest Apache2 or not?

Please tell me..

---

### Post by Impavidus on 2019-02-18
Ubuntu 18.10 will give you Apache 2.4.34 instead of 2.4.29. PHP will still be at 7.2. I don't know about the others, I just got an internal server error.

The software you get on any release of Ubuntu is usually the latest version a few weeks before release plus bugfixes, so 18.10 has slightly newer software than 18.04. The downside is that 18.10 only has 9 months of support, which is less nice for servers (and new users). Upgrades don't always work and there's no undo, unless you can restore your entire system from a backup.

Are you still sure you want to upgrade? Then open the settings for your software sources, set "prompt for a new release" to "any release". After successfully installing all pending upgrades, the upgrade manager should offer the release upgrade. Alternatively, use the command line.

---

### Post by Saovry on 2019-02-22
When I go to ternimal and type code to see my Ubuntu version, it told me 18.10 but when I go to myphpadmin, the Web server is say like this
[COLOR=#444444][FONT=sans-serif]
[LIST]
[*]Apache/2.4.34 (Ubuntu)
[*]Database client version: libmysql - mysqlnd 5.0.12-dev - 20150407 - $Id: 7cc7cc96e675f6d72e5cf0f267f48e167c2abb23 $
[*]PHP extension: mysqli[[IMG]https://seekkhmer.com/phpmyadmin/themes/dot.gif[/IMG]]("https://seekkhmer.com/phpmyadmin/url.php?url=https%3A%2F%2Fsecure.php.net%2Fmanual%2Fen%2Fbook.mysqli.php") curl[[IMG]https://seekkhmer.com/phpmyadmin/themes/dot.gif[/IMG]]("https://seekkhmer.com/phpmyadmin/url.php?url=https%3A%2F%2Fsecure.php.net%2Fmanual%2Fen%2Fbook.curl.php") mbstring[[IMG]https://seekkhmer.com/phpmyadmin/themes/dot.gif[/IMG]]("https://seekkhmer.com/phpmyadmin/url.php?url=https%3A%2F%2Fsecure.php.net%2Fmanual%2Fen%2Fbook.mbstring.php")
[*]PHP version: 7.3.2-3+ubuntu18.04.1+deb.sury.org+1
[/LIST]
[/FONT][/COLOR]
so which version of Ubuntu that I am using now, it is 18.10 or 18.04 because they show different result in there.

---

### Post by Impavidus on 2019-02-22
Looks like 18.10, but I think you got your php from a PPA designed to provide php7.3 on Ubuntu 18.04. If the PPA also works on Ubuntu 18.10, nice for you.

---

