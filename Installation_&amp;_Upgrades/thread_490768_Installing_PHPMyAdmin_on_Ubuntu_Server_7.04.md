---
title: "Installing PHPMyAdmin on Ubuntu Server 7.04"
date: 2007-07-02
forum: Installation &amp; Upgrades
---

### Post by textguru on 2007-07-02
I have successfully installed Ubuntu Server 7.04 using this instruction: 

[http://www.ubuntugeek.com/ubuntu-704-feisty-fawn-lamp-server-setup.html](http://www.ubuntugeek.com/ubuntu-704-feisty-fawn-lamp-server-setup.html)


How can I install phpmyadmin and configure on Apache, MySQL and PHP?

---

### Post by textguru on 2007-07-02
have found solution: [http://ubuntuforums.org/showthread.php?t=474761](http://ubuntuforums.org/showthread.php?t=474761)

:KS

---

### Post by RTrev on 2007-07-03
If I could just offer a word of advice, together with a question....

The advice is that my little site gets hit every single day by bots trying to break in, and the most common target seems to be PHPMyAdmin.  If you'd like to see an example of the kind of attacks the bots make, check out this page:

[http://rtrev.com/display_bots.php](http://rtrev.com/display_bots.php)

I was intending to record each attack and post them all publicly, which blocking the I.P. addresses, but soon realized that was impossible.  They come constantly, from all over the planet, relentlessly, and it would be inconceivable to keep up with them let alone to block each one.

The question is, if I wanted to install PHPMyAdmin, or MySQLAdmin, or other common targets of these bots, can I do it without using any of the common names for the directories?  You'll see from the lists on the page referenced above that these bots are all looking for pretty much the same thing, so using weird names instead of the conventional ones would seem to make a lot of sense.  I'm just not sure it's possible without a lot of work.  If it *is* possible, I'd strongly recommend doing this.

The same goes for any other commonly used software such as forum and blogging tools.

The bots are clearly shooting in the dark, but they use many variations of the commonly used names, and they probably know most of the vulnerabilities of each software package.

I was naively amazed at the number of attacks on my little unheard of site.. so I can only presume that virtually *every* server on the web is subject to the same thing.

Regards,
Bob

---

### Post by textguru on 2007-07-04
> **RTrev said:**
> If I could just offer a word of advice, together with a question....

The advice is that my little site gets hit every single day by bots trying to break in, and the most common target seems to be PHPMyAdmin.  If you'd like to see an example of the kind of attacks the bots make, check out this page:

[http://rtrev.com/display_bots.php](http://rtrev.com/display_bots.php)

I was intending to record each attack and post them all publicly, which blocking the I.P. addresses, but soon realized that was impossible.  They come constantly, from all over the planet, relentlessly, and it would be inconceivable to keep up with them let alone to block each one.

The question is, if I wanted to install PHPMyAdmin, or MySQLAdmin, or other common targets of these bots, can I do it without using any of the common names for the directories?  You'll see from the lists on the page referenced above that these bots are all looking for pretty much the same thing, so using weird names instead of the conventional ones would seem to make a lot of sense.  I'm just not sure it's possible without a lot of work.  If it *is* possible, I'd strongly recommend doing this.

The same goes for any other commonly used software such as forum and blogging tools.

The bots are clearly shooting in the dark, but they use many variations of the commonly used names, and they probably know most of the vulnerabilities of each software package.

I was naively amazed at the number of attacks on my little unheard of site.. so I can only presume that virtually *every* server on the web is subject to the same thing.

Regards,
Bob
For an intranet site, probably its safe to use phpmyadmin. If you want to publish it on the intranet, make sure that you do web publishing on your firewall to control web paths that web users are accessing. ;)

---

