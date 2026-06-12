---
title: "HOW TO: Install Eternal Lands."
date: 2007-09-03
forum: Installation &amp; Upgrades
---

### Post by kvarley on 2007-09-03
I tried to install the linux version of eternal lands and I couldn't work it out, however I then had a brainwave and brought you this HOW TO: so other people who struggled can use this alternative method, this way does work because I installed my el client this way! Please post a reply if you have any problems!

1.) Download the latest **windows** version of Eternal Lands.

2.) Install wine from terminal using aptitude.

> sudo apt-get install wine

3.) Install the .exe file using wine.

>  wine /home/**username**/Desktop/**filename**.exe

4.) Install game data only, **no shortcuts**.

5.) Close the install window and terminal window.

6.) Open your home folder and type this address in, move to a dir called games in your home folder.

> /home/**username**/.wine/drive_c/Program Files

7.) Open terminal and type.

> cd /home/**username**/games/el

8.) Now type the following.

> wine el.exe

Now you should have el up and running!

Problems I had:

Eternal Lands doesn't detect my ALSA sound system. 

*Solution: Enable sounds from within the game.*

Eternal Lands runs, then crashes, then runs and works fine.

*It only does this the first time.*

I can't create a launcher. (help please!)


Hope you liked this HOW TO:

Kev
Ubuntu Feisty user.

---

### Post by Subudhinath on 2007-10-13
Why would you want to use the Windows version when there's one available for Linux?

---

