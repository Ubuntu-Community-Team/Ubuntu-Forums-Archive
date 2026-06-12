---
title: "The power went out when I was updating!!"
date: 2008-04-10
forum: Installation &amp; Upgrades
---

### Post by delsydebothom on 2008-04-10
I upgraded to the Beta 8.10 version a few days ago, and haven't had any problems until today. This isn't the fault of Ubuntu, though; I was upgrading (I think there were 180 some-odd files), when the power went out. When I tried to log in to by profile, a simple beige screen came up--no error dialog, nothing. I let it set for 10 minutes or so before I turned it off, and booted 7.10 from my other partition up. It works fine. 

My question is: is there anyway for me to repair the damage that took place during the power outage? I want to be able to log back in to 8.10, because it is the only version in which wine has worked on my computer. Of course, I want to stay up to date, too. Help!!

---

### Post by PmDematagoda on 2008-04-10
Boot Ubuntu in Recovery Mode and then execute:-
```
sudo apt-get install -f
```
and 
```
sudo dpkg --configure -a
```

See if those commands can solve your problems.

---

### Post by delsydebothom on 2008-04-10
> **PmDematagoda said:**
> Boot Ubuntu in Recovery Mode and then execute:-
```
sudo apt-get install -f
```
and 
```
sudo dpkg --configure -a
```

See if those commands can solve your problems.

Thanks. I ran sudo dpkg --configure -a, and it seemed to work at first (except 1 thing which said wouldn't be fixed until all X sessions were closed. I didn't catch the whole message). Then I ran sudo apt-get install -f, which looked like it was going to work, but then didn't; it couldn't set up a lot of packages, and the last line said /usr/bin/dpkg returned an error code (1) :confused:

Then I tried logging in normally again, but it did the same thing; just the blank beige screen. :(

---

### Post by delsydebothom on 2008-04-10
Anybody out there?:confused:

---

### Post by PmDematagoda on 2008-04-10
After running:-
```
sudo apt-get install -f
```
did you try running the other command I provided?

---

### Post by delsydebothom on 2008-04-10
> **PmDematagoda said:**
> After running:-
```
sudo apt-get install -f
```
did you try running the other command I provided?

Yes, I tried both. Neither worked :(.

---

### Post by PmDematagoda on 2008-04-10
If possible, could you post the error messages here? If you can do that then it would help immensely.

---

### Post by delsydebothom on 2008-04-10
> **PmDematagoda said:**
> If possible, could you post the error messages here? If you can do that then it would help immensely.

Okay! 

When I ran *sudo apt-get install -f,* it gave me this message several times: *dpkg: error processing [program] (--configure): dependency problems - leaving unconfigured.* (just replace [program] with the programs I will list below as part of the third error message) 

[I]dpkg: dependency problems prevent configuration of sound-juicer; soundjuicer depends on hal; however: package hal is not configured yet.

[I]Errors were encountered when processing:
hal
gnome-power-manager
gnome-session
hal-cups-utils
sound juicer[/I]
[I]
E: sub-process /usr/bin/dpkg returned an error code (1)[/I]

When I run *sudo dpkg --configure -a*, it gives me (as far as I can tell) the same error message.

---

### Post by confused57 on 2008-04-10
Herman's reply #3 in this thread may help:
[http://ubuntuforums.org/showthread.php?t=737295](http://ubuntuforums.org/showthread.php?t=737295)

---

### Post by delsydebothom on 2008-04-10
> **confused57 said:**
> Herman's reply #3 in this thread may help:
[http://ubuntuforums.org/showthread.php?t=737295](http://ubuntuforums.org/showthread.php?t=737295)

Well, I'm running from the live CD right now. None of those commands seemed to do anything, though...

---

### Post by delsydebothom on 2008-04-12
Thank you both for your efforts. In the end, I simply saved all my files on CDs, and then reinstalled Ubuntu.

---

