---
title: "changing rights on home made desktop get lost"
date: 2009-12-05
forum: Installation &amp; Upgrades
---

### Post by pelgrim on 2009-12-05
apparently I did something very stupid.

I changed the rights to my user home.
I kept having a message that it wasn't right,
so I changed all with
chown username:username /home/username

problems increased only.
After searching on forums and trying out
I have now only a background when I start up,
no menu.
In console I can see that my user owns all files,
except all .dirs => permission denied

can someone help me te regain my system again ?

---

### Post by phillw on 2009-12-05
> **pelgrim said:**
> apparently I did something very stupid.

I changed the rights to my user home.
I kept having a message that it wasn't right,
so I changed all with
chown username:username /home/username

problems increased only.
After searching on forums and trying out
I have now only a background when I start up,
no menu.
In console I can see that my user owns all files,
except all .dirs => permission denied

can someone help me te regain my system again ?


Hi,

well, on the scale of 1 to 10 ..... ;-)

Not to worry, you're not the first - and you won't be the last.

head over to --> [http://swiss.ubuntuforums.org/showthread.php?t=976610](http://swiss.ubuntuforums.org/showthread.php?t=976610)

That should get you back running

Regards,

Phill.

---

### Post by pelgrim on 2009-12-05
> **phillw said:**
> Hi,

well, on the scale of 1 to 10 ..... ;-)

Not to worry, you're not the first - and you won't be the last.

head over to --> [http://swiss.ubuntuforums.org/showthread.php?t=976610](http://swiss.ubuntuforums.org/showthread.php?t=976610)

That should get you back running

Regards,

Phill.

thanx, but I just solved the problem.
Guess what, I saw that post allready ...

What did I do ?
Perhaps something that would make you laugh, but hey,
it worked for me ;)

here it is:
logged on in console (what else :D)
create new user
make new user sudo'er
log on in X with new user
upen nautilus with sudo
select all .whatever maps in my original home page
and set the security properties the way they should be.
Normal reboot again with my original user
Stop sweating

---

### Post by phillw on 2009-12-05
> **pelgrim said:**
> thanx, but I just solved the problem.
Guess what, I saw that post allready ...

What did I do ?
Perhaps something that would make you laugh, but hey,
it worked for me ;)

here it is:
logged on in console (what else :D)
create new user
make new user sudo'er
log on in X with new user
upen nautilus with sudo
select all .whatever maps in my original home page
and set the security properties the way they should be.
Normal reboot again with my original user
Stop sweating

Don't use sudo for things like nautilus, FireFox, OpenOfice or ANYTHING that is a GUI (Available from the menu bar) - ALWAYS use gksudo.

I nearly suggested making a new user - but thought that thread but be more str8 forward - as i don't know how much experience you have - Well, you have more, now ;-)

Glad you got up & running.

Phill.

---

