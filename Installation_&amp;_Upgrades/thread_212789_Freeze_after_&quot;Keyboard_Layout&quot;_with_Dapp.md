---
title: "Freeze after &quot;Keyboard Layout&quot; with Dapper &quot;Desktop&quot; installation CD"
date: 2006-07-10
forum: Installation &amp; Upgrades
---

### Post by mjkaye on 2006-07-10
Hi folks.

Haven't seen this one in the forums already, but I'm sure I may have missed it.

I'm trying to install Dapper on my machine, using the Live/Desktop/Installation CD. I'm actually installing over Breezy, but I always used to do a fresh install with Debian.

Anyway, I start the installation process, by double-clicking on the install icon, and get as far as the "Keyboard Layout" step. I select "UK English" and try to move on to the next step, but nothing happens. I go away and leave it for a while, but nothing has happened when I come back. There is the occasional flash from the HDD light, but not much more sign of life.

Am I right in thinking that hardware detection is the stage after keyboard layout? Am I just being too impatient? It is an older machine (Duron 850), but Breezy installed no problem.

TIA

Michael

---

### Post by WesleyWex on 2006-07-10
I'm having the same problem, but with "Português Brasieiro (br-abnt2)"... setup hangs on step 3...

---

### Post by mjkaye on 2006-07-11
Well, we don't seem to be on our own.
These two threads were started, on the same topic, in the last day:
[http://ubuntuforums.org/showthread.php?t=213261](http://ubuntuforums.org/showthread.php?t=213261)
[http://ubuntuforums.org/showthread.php?t=213199](http://ubuntuforums.org/showthread.php?t=213199)

I wondered if it might be a machine spec issue, but the second of those threads suggests that it isn't. Perhaps it's an issue with choosing a non-US layout. I wonder if it's the case with all non-US layouts.

Michael.

---

### Post by ukk on 2006-07-11
Hi,

> **mjkaye said:**
> Hi folks.

...
I'm trying to install Dapper on my machine, using the Live/Desktop/Installation CD. I'm actually installing over Breezy, but I always used to do a fresh install with Debian.

Anyway, I start the installation process, by double-clicking on the install icon, and get as far as the "Keyboard Layout" step. I select "UK English" and try to move on to the next step, but nothing happens. 
...
Michael

This  happened to me too when installing on a Thinkpad
X600 P3 128 MB RAM with an existing Debian installation. I
left it over the  night to install but it didn't help either.
No hints in /var/log/installation, it just says that
keyboard is selected.

My (uneducated) guess is that the installation stops because
of lack of memory. I will next try to find out how to manually
configure swap space for the live CD. Any hints are appreciated.

Cheers, Urpo

---

### Post by ukk on 2006-07-11
> **ukk said:**
> Hi,

This  happened to me too when installing on a Thinkpad
X600 P3 128 MB RAM with...

I will next try to find out how to manually
configure swap space for the live CD.


Adding swap didn't seem to help. There should be 256 RAM of course
but funny that installation just dies.

---

### Post by ukk on 2006-07-12
> **ukk said:**
> Adding swap didn't seem to help. There should be 256 RAM of course
but funny that installation just dies.

I was able to solve this installation problem by 
installing from the Alternate install CD instead
of the normal one ([http://ftp.funet.fi/pub/mirrors/releases.ubuntu.com/6.06/](http://ftp.funet.fi/pub/mirrors/releases.ubuntu.com/6.06/) , choose a server nearby). And indeed the text to the
alternate CD says "installs on systems with less than about 192MB of RAM" -
like mine.

Urpo

---

### Post by WesleyWex on 2006-07-13
Thanks for opening my eyes, I've missed the third release type... hehe

It's interesting that Ubuntu desktop works perfectly after I manually configure my serial mouse, but now that I was able to (finally) install Ubuntu, I'm having [_network problems_](http://www.ubuntuforums.org/showthread.php?t=215292)...

---

