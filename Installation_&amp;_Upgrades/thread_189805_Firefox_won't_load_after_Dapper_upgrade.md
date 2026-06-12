---
title: "Firefox won't load after Dapper upgrade"
date: 2006-06-05
forum: Installation &amp; Upgrades
---

### Post by Julian David Pitt on 2006-06-05
[FONT="Comic Sans MS"][COLOR="Blue"][SIZE="4"]I have recently upgraded to Dapper and now cannot launch Firefox. This first started after I installed and used Automatix to install a load of programs. I received a message saying that my bookmarks would most likely be screwed up which was fine as I have a back up. When I try to open FF now I get a dialogue saying "There was an error launching the application. Details: Failed to execute child process "firefox" (No such file or directory)" I notice in my home directory that I have one folder called  "firefox" and another called "Firefox". The former has a red padlock icon and contains all the browser files while the latter only has a few extension xpi files in it. I would really appreciate some help to get FF working again. Cheers all in advance.[/SIZE][/COLOR][/FONT]

---

### Post by Sam Lars on 2006-06-05
I would suggest removing and then reinstalling Firefox.

---

### Post by Julian David Pitt on 2006-06-05
Hi Sam
I have tried that already using apt-get remove firefox and then reinstalled but I still get the same problem. Your furthter advice would be greatly received my friend.

---

### Post by jtholmes on 2006-06-05
Yep
Firefox will fail for various reasons. In my case it was missing
gtk2 and even then it gave a bunch of error msgs to the console
but started up and worked just fine.

If you are starting ff from an Icon on the Desktop then start
it manually from the command line to see the X errors that
it is generating.

Isn't it fun working with new releases. I wonder just what the
regression test suite is for something this large. I can only imagine
that there is a lot of pressure to get the thing out the door and then
let the users find some of the bugs. Not that that is the intent but
time pressures often dictate some compromises near the end of
a release cycle.
jt

---

### Post by Julian David Pitt on 2006-06-06
So how do I start FF from the comand prompt then please?

---

### Post by blackjack6.21.91 on 2006-06-06
To open firefox from the command line, just open a terminal and type "firefox"

Tell us what the terminal says back.

You can access the terminal by going to
Applications -> Accessories -> Terminal

---

### Post by Julian David Pitt on 2006-06-06
Will try that when I get home, many thanks.

---

### Post by Julian David Pitt on 2006-06-06
This is what I get at the terminal
"julian@ubuntu:~$ firefox
bash: firefox: command not found
julian@ubuntu:~$ Firefox
bash: Firefox: command not found
julian@ubuntu:~$"
Help ??

---

### Post by blackjack6.21.91 on 2006-06-10
Hey dude.  Sorry I took so long.  It looks like your firefox is pretty completely broken.  I'm gonna link you to a script that should install a new firefox for you.  It wasn't made by me, so let's all thank Aysiu.

[http://pykeylogger.sourceforge.net/wiki/index.php/Ubuntu:Chronicles#Install_Firefox_1.5](http://pykeylogger.sourceforge.net/wiki/index.php/Ubuntu:Chronicles#Install_Firefox_1.5)

---

