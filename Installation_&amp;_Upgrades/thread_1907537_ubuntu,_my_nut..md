---
title: "ubuntu, my nut."
date: 2012-01-11
forum: Installation &amp; Upgrades
---

### Post by jamstir on 2012-01-11
Hi boys and girls.. glad i joined this site, for some reason i think your not going to be so happy.. hahah
I got an old system single core bla bla,, needs  hole and a shovel but does me for my needs at the min.

Now, i tried to install on unbuntu 10.04 Nessus, now i not new to pc,s but new to linux , and after what i can only call near 16 hours of trying to install this software my jack is breaking.
Here,s what i done.. went and got the software, downloaded for 10.04, installed it. Then went to terminal to turn it on and give it the old command lines..  well its now working.
I then went to the site and reg.. my key, and downloaded a lot of other files, manly plug ins, i dont know if they installed or not? but i got them.
Then followed near every line in command, nothing working, then i read something about ROOT, and i thought.. thats me.. lol
So i then set about trying to open this ROOT, and hey, turns out i not have root on my pc, so then i got it, downloaded it though the terminal,  And i know some off you are laughing right now, and please carry on, cause i know i was close.. hahaha
Bottom line is, Nessus and the commands, its doing nothing.:mad::mad::mad::mad::mad::mad:

Anyone throw some light my way??
Thanks guys/ girls.
Jamstir.

---

### Post by PapaGary on 2012-01-11
What's your question?

---

### Post by Buntumatic on 2012-01-11
My guess is he succeeded installing Ubuntu and probably Nessus, now he is trying to start Nessus and Nessus is not cooperating. :confused:

---

### Post by jamstir on 2012-01-11
> **Buntumatic said:**
> My guess is he succeeded installing Ubuntu and probably Nessus, now he is trying to start Nessus and Nessus is not cooperating. :confused:
  Ubuntu was the easy one to install, been using it for near a year now for business, but this Nemuss as me in aright state. lol
Any of the commands are not working, its like its not there.
I get message telling me its  a tempfile. Or wrong input command.
I took it of and installed it again, once again i followed the book to the point of getting it started, its not doing jack.
Anyone know why?

I took it of this site,       
[http://www.nessus.org/products/nessus/select-your-operating-system](http://www.nessus.org/products/nessus/select-your-operating-system)

---

### Post by lisati on 2012-01-11
Which one did you use? There's more than one on the website for Ubuntu, sometimes if you install the "wrong" one it will look like it has installed, but it won't work as well.

---

### Post by jamstir on 2012-01-11
> **lisati said:**
> Which one did you use? There's more than one on the website for Ubuntu, sometimes if you install the "wrong" one it will look like it has installed, but it won't work as well.
  hi there i took this down.

[Nessus-4.4.1-ubuntu910_i386.deb]("http://downloads.nessus.org/nessus3dl.php?file=Nessus-4.4.1-ubuntu910_i386.deb&licence_accept=yes&t=00c993c3fda8d5582cd3f6422b6ce842") (12262 KB)
Ubuntu 9.10/ Ubuntu 10.04 (32 bits):
that,s the one for my system as far as i aware of.
I complete lost at this, never before have i been stuck on installing, then again i always had XP or Window,s. but i find unbuntu there more to learn.

---

### Post by Buntumatic on 2012-01-11
How did you install it.
Did you encounter any errors during install.

---

### Post by jamstir on 2012-01-11
> **Buntumatic said:**
> How did you install it.
Did you encounter any errors during install.

When i downloaded it, i looked in the synaptic package manager, and it told me all was installed, i then tried though the terminal command to reg the key with no luck, i tried to start it, no luck. i then went back the site and reg the key manually, it then gave me plugins etc.
I then done a rebot and went back to root to try and start it.

One thing that could be stopping it, i am in China at the minute, but i do have a VPN and have tried with it on and with the VPN off, still no kick.:confused:

Is there anything to go into the repositories??

---

### Post by Buntumatic on 2012-01-11
Alright, we need somebody looking over your shoulder or we need a working crystal ball (mine is broken).

What command did you issue in terminal.

What was the response, if any.

---

### Post by jamstir on 2012-01-11
> **Buntumatic said:**
> Alright, we need somebody looking over your shoulder or we need a working crystal ball (mine is broken).

What command did you issue in terminal.

What was the response, if any.

hahha i thank you for taken the time to help, will try and pass all info..  ok.. commands.. i tried.

# dpkg -i Nessus-4.4.0-ubuntu1010_i386.deb

/opt/nessus/sbin/nessus-adduser

 nessus-fetch --security-center

I get more just using sudo.. lol

/opt/nessus/bin/nessus-fetch --register XXXX-XXXX-XXXX-XXXX-XXXX  with my code of course, but command codes from the nessus hand book, i get messages like.. command not found. Or Interpreter error recovered.. or   tempfile.1.

 /opt/nessus/bin/nessus-fetch --register

now the code commands i have tried with a # infront.. or without.. i have been all over this for hours.. i even tried other sites and other ways and still nothing.

jam@jam-desktop:~$ sudo apt-get install nessus nessusd
[sudo] password for jam: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
nessus is already the newest version.
nessus set to manually installed.
Package nessusd is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  nessus
E: Package nessusd has no installation candidate
jam@jam-desktop:~$ sudo nessus-adduser
sudo: nessus-adduser: command not found
jam@jam-desktop:~$

---

### Post by buckyaustin on 2012-01-11
Ok this may sound stupid, but is Nessus in your working directory.... Is it in your home folder or download folder.... if its download folder do as follows
cd Downloads/
that should get you into ur download folder, then try to run nessus
sudo dpkg -i Nessus-4.4.0-ubuntu1010_i386.deb
password: **********

before the rest of the folder locations make sure you use the command "cd" without quotes.

also before you run an execution command which requires you to be a root user use the command "sudo" then type wat you want.... This in my opinion seems to be your problem... the two commands i have typed there as they are usually (always) needed when installing from the command line.

reply if that was confusing or didnt work.... Im dyslexic and its hard for me to explain things... usually i just jump at the computer and kick the other person off...



to move to the parent directory/folder type "cd .." yes it has to have the space
this shouldnt be a problem in Ubuntu 11.10, just open the .deb with software center.... i keep forgetting what my lecturer said, sometimes its better to use the gui.

---

### Post by Dangertux on 2012-01-11
> **buckyaustin said:**
> Ok this may sound stupid, but is Nessus in your working directory.... Is it in your home folder or download folder.... if its download folder do as follows
cd Downloads/
that should get you into ur download folder, then try to run nessus
sudo dpkg -i Nessus-4.4.0-ubuntu1010_i386.deb
password: **********

before the rest of the folder locations make sure you use the command "cd" without quotes.

also before you run an execution command which requires you to be a root user use the command "sudo" then type wat you want.... This in my opinion seems to be your problem... the two commands i have typed there as they are usually (always) needed when installing from the command line.

reply if that was confusing or didnt work.... Im dyslexic and its hard for me to explain things... usually i just jump at the computer and kick the other person off...



to move to the parent directory/folder type "cd .." yes it has to have the space
this shouldnt be a problem in Ubuntu 11.10, just open the .deb with software center.... i keep forgetting what my lecturer said, sometimes its better to use the gui.

Give you a hint, the nessus commands aren't in your path. Try finding them in 

```


/opt/nessus/bin

```

and

```

/opt/nessus/sbin

```

Also when you figure that out open the following in your browser.

[https://localhost:8834/](https://localhost:8834/)

You'll be presented with the nessus gui. Have fun ;-)

---

### Post by jamstir on 2012-01-12
> **Dangertux said:**
> Give you a hint, the nessus commands aren't in your path. Try finding them in 

```


/opt/nessus/bin

```and

```

/opt/nessus/sbin

```Also when you figure that out open the following in your browser.

[https://localhost:8834/](https://localhost:8834/)

You'll be presented with the nessus gui. Have fun ;-)

THANKS guys for helping, i have tried the commands for Nessus like the ones mentioned and its just not finding it.
What i done the other day was a bit frecky.. i decided to update ubuntu from 10.04 to 10.10 i thought this would be hassle free, turns out after update the system could not boot, the reason i updated was because  the ubuntu i had came of a boot disc i was given and i dont know what was all on the disc.
So after this update to 10.10 and not being able to boot, luck would have it that this tower in wired to the internet and i have another laptop on WIFI at home, so i did some reading and really was getting no where, apart of people talking about a package that,s in the update and its causes this, i tried to find the mentioned package and after 2 hours of looking at all the updates installed i was still no where. I could call sudo and that,s really all i could do.
I used sudo  apt-get     cant remember the rest.. lol but i got the update to 11.04 and everything seems fine now, apart from my mouse pointer that keeps doing a disappearing act. lol

So i going back now today and try and get Nessus, this time i will write all i do and log it here.
Hope all goes well this time.
Thank again guys for the advice.
PS.
I know what you mean by kicking people of a pc and just going to work, i do the same thing to people, when people try and do it to me they need a 24 tonne crane. Hate people that mess with my pc.. lol i sure i not alone here.

---

### Post by jamstir on 2012-01-12
hahahaha..  I think i found the problem, right from the start,, the site i installed nessus from i went back there to take it down again, now on ubuntu 11.04 it installs from the software center, went to intstall it and was told bad package!!  the Nessun is not lower case. Don,t know if this as a big effect on things, but it will not let me install from that site. Back to drawing board.

Before taken the download i got a lot of work to do,,  GLIB, PANGO, ATK, GTK+  hope to be done this year. lol

---

