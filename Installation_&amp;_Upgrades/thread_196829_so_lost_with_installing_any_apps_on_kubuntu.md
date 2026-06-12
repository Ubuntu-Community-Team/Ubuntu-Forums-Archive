---
title: "so lost with installing any apps on kubuntu"
date: 2006-06-14
forum: Installation &amp; Upgrades
---

### Post by litbynature on 2006-06-14
hello....

i need a little direction.   i feel so stupid right now.  installed kubuntu and everything worked perfectly.  

however, i cannot find a way to install any apps.  i am not being lazy.  i searched and searched the web and followed everyones tutorials and wiki how-to docs....

nothing is installing.

for example, i tried to install firefox, thunderbird, automatix, flock, etc. etc.

using adept or through the konsole..... nothing.

can anyone be super COOL / KIND and provide me with some direction.

anything?  i dont care....i just want to install something

kubuntu has the most amazing concept.  i just have not been able to tap into its full potential....  i cant wait.

have a wonderful day.... : )
michel

---

### Post by aysiu on 2006-06-14
Adept and the Konsole are the way to go.

Can you post a bit more about the problems you've encountered? Is it that you have installed it and it's not showing up? Or you've installed it and when you try to launch it, it doesn't launch? Or does the installation actually fail? And if so, what error message did you get?

Please, be as specific as possible (use only one example for now) about what you did and how you came to conclude that the installation didn't work.

For example, post back the output of these commands: ```
cat /etc/apt/sources.list
sudo aptitude update
sudo aptitude install firefox
firefox
```

---

### Post by litbynature on 2006-06-14
thank you so much for the quick reply AND sorry for not being specific enough.

let's start here....

i have download several installations in tar.gz format.  i extract them, but then what?  i understand this would be 'installing from source' approach.  i went to some tutorial that directed me to use the konsole.  it had some standard commands and usually result in package not found, etc....

i have gone to adept and typed in different things i would like to install such as firefox, thunderbird, flock, etc.... and nothing comes up?

i go to add/remove programs and the softwares that i am interested in are in gray.  it will not allow me to select/install them....

i hope this information is helpful.....if not, then please let me know and i will try to dig deeper.

thank you again for your time.

---

### Post by litbynature on 2006-06-14
based on the commands you provided me, here is the result:

```
# Line commented out by installer because it failed to verify:
#deb http://us.archive.ubuntu.com/ubuntu/ dapper main restricted
# Line commented out by installer because it failed to verify:
#deb-src http://us.archive.ubuntu.com/ubuntu/ dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
# Line commented out by installer because it failed to verify:
#deb http://us.archive.ubuntu.com/ubuntu/ dapper-updates main restricted
# Line commented out by installer because it failed to verify:
#deb-src http://us.archive.ubuntu.com/ubuntu/ dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb http://us.archive.ubuntu.com/ubuntu/ dapper universe
# deb-src http://us.archive.ubuntu.com/ubuntu/ dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://us.archive.ubuntu.com/ubuntu/ dapper-backports main restricted univ                                                              erse multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ dapper-backports main restricted                                                               universe multiverse

# Line commented out by installer because it failed to verify:
#deb http://security.ubuntu.com/ubuntu dapper-security main
# Line commented out by installer because it failed to verify:
#deb-src http://security.ubuntu.com/ubuntu dapper-security main
# deb http://security.ubuntu.com/ubuntu dapper-security universe
# deb-src http://security.ubuntu.com/ubuntu dapper-security universe
micho@micho-desktop:~$ sudo aptitude update
Password:
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
Reading package lists... Done

```

That looks good to me. :)

---

### Post by David_T on 2006-06-14
Greetings,
I know nothing of the Kubuntu tools, and there may be an easier way to do this using those graphical tools, but here is my suggestion:
Run this command:

sudo pico /etc/apt/sources.list

And in pico, delete all the # signs from in front of the lines that start with "deb" or "deb-src".   Type ctrl-s to save and ctrl-x to exit.   Then type the other commands in turn:
sudo aptitude update
sudo aptitude install firefox
firefox

---

### Post by ltmon on 2006-06-14
OK... for a beginner don't bother downloading anything of the web in tar.gz format.  They are usually source code, and fun to play with, but will just be confusing for now.

You install applications in Kubuntu by downloading them from special repositories and installing them with a single special command ("apt-get").  The list of repositories is the top bit of the output in your last post.  You can add more repositories later for a greater selection of software to be available.

Back to "apt-get" (there is also the similar-but-different "aptitude" which others here have been recommending).  It's a command line tool, but luckily there is a nice graphical frontend to it, called "Adept".  It's in your menu.  Launch it and type in your password.

You should be able to search for a package (e.g. "firefox") and expand it's listing to see details about it.  There will be a button to "Mark for installation".  Before it is actually installed you then have to "Commit" the change (a button in the toolbar).  This will fetch firefox, install it.  You then can quit, and should have firefox installed.

For a more elaborate (and probably better written) see the documentation at:

[http://doc.ubuntu.com/kubuntu/desktopguide/C/index.html](http://doc.ubuntu.com/kubuntu/desktopguide/C/index.html)

Chapter 3 is about installing/removing programs.

L.

---

### Post by litbynature on 2006-06-14
you guys are too cool...and i am loving kubuntu.

so i am making progress based on your suggestions and docs.

i realized that i had to add repositories; specifically, universe.  before doing this, whenever i would type any application, the resulting search provided nothing.

for example, now i typed in kbear; it came up and i installed it successfully.  thanks!

however, i typed in firefox and thunderbird and results came, but they do not seem right.  check this out:

they were all extensions and different locales.... except for one...it was called a firefox dummy transitional package.  would that be it?

do you happen to know which repositories I should add?  through adept, it only gave me the option to add 'universe' and 'universe multiverse'

i really would like to have firefox, flock, thunderbird, and a good ftp client.  it would perfect everything.

thanks again!

---

### Post by ltmon on 2006-06-14
I don't know how advanced your ftp needs are, but you can get at most ftp features by typing:

[ftp://user@host/path/](ftp://user@host/path/)

into the Konqueror address bar.

It also works for "fish://" (files over SSH or SCP), "smb://" (samba) and a whole lot of other protocols ("imap://","pop://","webdav://").

As for firefox, there used to be a package called "mozilla-firefox", but it was renamed to "firefox".  "mozilla-firefox" is the transition package for those still using the old name.  You should install "firefox".

Flock probably isn't in the repositories.  Maybe the flock webpage has hints on the best way to install for ubuntu.

Thunderbird is still called "mozilla-thunderbird", and should be present.

L.

---

### Post by litbynature on 2006-06-14
thank you....  

i have my ftp stuff now....

concerning firefox and thunderbird packages, this is what i have

for "firefox":

firefox-dom-inspector
firefox-webdeveloper
mozilla-biofox
mozilla-firefox-dev
mozilla-firefox-locale-tr
mozilla-venkman

....and a few more that do not match 'mozilla-firefox' or just 'firefox'

for "thunderbird"
mozilla-thunderbird-locale-el
mozilla-thunderbird-locale-es
mozilla-thunderbird-locale-ko
etc. etc....  nothing that matches again.

have you encountered this before?  do i need to install any additional repositories.  I believe I installed all of them.

so i went to the add/remove programs...and thunderbird and firefox show up, but they are 'gray' and will not allow me to select them.....

i was on the firefox website and it says all the required packages that needs to be installed.  i went through them and made sure they were.....

any suggestions will be appreciated.

thank you

---

### Post by ltmon on 2006-06-14
I'm not at my kubuntu box right now, so I can't tell for sure, but try enabling the Universe and Multiverse repositories.  I've had these enabled for ages, so I forget what package is in what repository.

It's pretty easy to do this.  The howto is at [http://doc.ubuntu.com/ubuntu/desktopguide/C/extra-repositories.html](http://doc.ubuntu.com/ubuntu/desktopguide/C/extra-repositories.html)

Cheers,
L.

---

### Post by aysiu on 2006-06-14
[QUOTE=litbynature]based on the commands you provided me, here is the result:

```
# Line commented out by installer because it failed to verify:
#deb http://us.archive.ubuntu.com/ubuntu/ dapper main restricted
# Line commented out by installer because it failed to verify:
#deb-src http://us.archive.ubuntu.com/ubuntu/ dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
# Line commented out by installer because it failed to verify:
#deb http://us.archive.ubuntu.com/ubuntu/ dapper-updates main restricted
# Line commented out by installer because it failed to verify:
#deb-src http://us.archive.ubuntu.com/ubuntu/ dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb http://us.archive.ubuntu.com/ubuntu/ dapper universe
# deb-src http://us.archive.ubuntu.com/ubuntu/ dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://us.archive.ubuntu.com/ubuntu/ dapper-backports main restricted univ                                                              erse multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ dapper-backports main restricted                                                               universe multiverse

# Line commented out by installer because it failed to verify:
#deb http://security.ubuntu.com/ubuntu dapper-security main
# Line commented out by installer because it failed to verify:
#deb-src http://security.ubuntu.com/ubuntu dapper-security main
# deb http://security.ubuntu.com/ubuntu dapper-security universe
# deb-src http://security.ubuntu.com/ubuntu dapper-security universe
micho@micho-desktop:~$ sudo aptitude update
Password:
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
Reading package lists... Done

```

That looks good to me. :)[/QUOTE] Actually, you have no sources in your sources.list.

A # sign at the beginning of the line is called a "comment out." It means basically "ignore the rest of this line."

---

### Post by litbynature on 2006-06-15
thank you.....

i actually have both of those repositories enabled.

i must be missing a small detail....

can anyone confirm? if both the universe and universe multiverse is enabled, then should i see the firefox and mozilla-thunderbird packages?

they are not coming up for me.  anyone experience the same thing?

---

### Post by aysiu on 2006-06-15
Do me a favor? Get a fresh sources.list:
[http://www.psychocats.net/ubuntu/sources](http://www.psychocats.net/ubuntu/sources)

Then do ```
sudo aptitude update
sudo aptitude install firefox mozilla-thunderbird
```

---

### Post by litbynature on 2006-06-15
aahaa!

yes!!  you made it allll happen.  thank you sooooo much! 

i would NEVER have figured that out.  I think I am really going to enjoy kubuntu.

this is great....

take care
-m

---

### Post by aysiu on 2006-06-15
I'm glad it's finally working now.

I have no idea how you ended up with an empty sources.list file, though.

---

