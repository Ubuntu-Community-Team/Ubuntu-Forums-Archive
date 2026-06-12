---
title: "Can you set &quot;hot keys&quot; in terminal?"
date: 2009-12-20
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by ranch hand on 2009-12-20
For some reason I had the idea you could set hot keys.  I have tried the help file but there is some "rendering" problem on the page I need.

All I can find are preset keys and now way to add them.

Now that I have finally got the chroot script stuff working, I am getting lazy.  I am tired of typing "apt-get update" for six OS' and would like a short cut.

Please advise if I am dreaming.

Please advise if it is possible, with direction if you can, or a place to look.   I am plumb out.

Yes I know I am a noob.  I may advance to juornyman on this testing cycle.

---

### Post by Hiram on 2009-12-20
> **ranch hand said:**
> For some reason I had the idea you could set hot keys.  I have tried the help file but there is some "rendering" problem on the page I need.

All I can find are preset keys and now way to add them.

Now that I have finally got the chroot script stuff working, I am getting lazy.  I am tired of typing "apt-get update" for six OS' and would like a short cut.

Please advise if I am dreaming.

Please advise if it is possible, with direction if you can, or a place to look.   I am plumb out.

Yes I know I am a noob.  I may advance to juornyman on this testing cycle.


have you tried aliases? There not realy hotkeys but basicly allow you to remap commands to other commands

like:
alias up="sudo aptitude update"

im sure some warnings apply and i am not sure if i got the syntax right but you should be able to find stuff in man pages (most of the are online to if they are broken or missing) or bash tutorials

You can do even more tricky stuff with bash functions (bash is basicaly a scripting language and i assume turing complete so you would be able to do almost everything from your terminal)

most of the stuff goes to .bashrc and/or .bash_profile and i think there are some expamples already in there

---

### Post by ranch hand on 2009-12-20
> **Hiram said:**
> have you tried aliases? There not realy hotkeys but basicly allow you to remap commands to other commands

like:
alias up="sudo aptitude update"

im sure some warnings apply and i am not sure if i got the syntax right but you should be able to find stuff in man pages (most of the are online to if they are broken or missing) or bash tutorials

You can do even more tricky stuff with bash functions (bash is basicaly a scripting language and i assume turing complete so you would be able to do almost everything from your terminal)

most of the stuff goes to .bashrc and/or .bash_profile and i think there are some expamples already in there
Do you have a .bash_profile file?

There is some stuff that I need to study in the .bashrc file.  I will not be trying this on this install.  That is what I have the others for.

I am sure that once you get it sorted it is easy but it looks tough to me right now.

Also some of the files mentioned as you start to track them down are "broken".  When I saw this in 10.04 I was not to concerned and went and looked in a 9.10 install I have on the test drive.  Broken there too, notably /usr/share/doc/completion-contrib.  At least I think that is one I am supposed to look at.

A couple others just do not exist.  I think this may be due to the lag in 9.10 documentation that we pissed and moaned about during the last testing cycle.  I will have to check in 9.04 and see if that stuff is there.

Can't from here, those drives are turned off to protect them from contact with these testing OS'.   Don't want them getting funny ideas about the acceptable level of stability, or just get screwed.

---

### Post by zika on 2009-12-20
> **ranch hand said:**
> For some reason I had the idea you could set hot keys.  I have tried the help file but there is some "rendering" problem on the page I need.

All I can find are preset keys and now way to add them.

Now that I have finally got the chroot script stuff working, I am getting lazy.  I am tired of typing "apt-get update" for six OS' and would like a short cut.

Please advise if I am dreaming.

Please advise if it is possible, with direction if you can, or a place to look.   I am plumb out.

Yes I know I am a noob.  I may advance to juornyman on this testing cycle.With Lucid came Byobu Window Manager. As far as I could see, it has option for keyboard shortcuts. I, myself, prefer aliases stored in ~/.bash_aliases (do not forget to enable them in .bashrc, uncomment alias part of code). Have fun.

---

### Post by ranch hand on 2009-12-20
Well, I have got to try this when I have time to be calm and remember to breath when doing something absolutely new and strange to me.

Also in one of my other installs.

Could be FUN.  It will certainly be neat if (when) I get it going.

---

