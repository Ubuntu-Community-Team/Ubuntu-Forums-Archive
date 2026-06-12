---
title: "Problems with installation"
date: 2008-08-17
forum: Installation &amp; Upgrades
---

### Post by Exile32r4 on 2008-08-17
I am currently using hardy heron and am having some installation problems
I tried to do a manual install of Songbird (because i didn't check if there was a .deb package or not)
I've been using ubuntu for a while, but this my first manual installation because ive never needed to do it before, so basically im still a noob :(

So what I did was extract the tar.gz file in /opt and i got a Songbird directory in /opt (/opt/Songbird)
I also changed the permissions of the folder by using ```
sudo nautilus
```

From the same nautilus browser i launched songbird and it worked like a charm.
So I make a launcher in the applications tab, look for an icon...blah blah

When Im finished I try launching it from the launcher and it seems to work...except it shows me the end user agreement license over and over and over again, until i decline it

so basically the problem is that i am only able to use songbird with root privileges, even though i checked the permissions like 3 times...

Any suggestions would be greatly appreciated

---

### Post by Pumalite on 2008-08-17
Did you check this?:
[http://www.howtoforge.com/installing-songbird-on-ubuntu8.04-p2](http://www.howtoforge.com/installing-songbird-on-ubuntu8.04-p2)

---

### Post by Sef on 2008-08-17
> 
Code:

sudo nautilus



With a graphical interface from the terminal, you should use 

```
gksudo nautilus
```

Otherwise you may be unable to log in.

---

### Post by Exile32r4 on 2008-08-17
yes i checked the link, but it didnt help....
my temporary solution is to make it run in terminal, but its kind of bothersome to have to put in the password every time i use songbird because i would use it frequently

i was thinking maybe because the first run was made with user privileges or something like that..

btw thanks for the gksudo i didnt know that command :)

---

