---
title: "Login screen wont show up"
date: 2007-06-18
forum: Installation &amp; Upgrades
---

### Post by sent17inel on 2007-06-18
Im having a serious problem!!!! I've had to re-install linux completely three times and i finally figured out whats messing it up but i dont know how to fix it and i sure as hell dont want to re-install it again.... im gettin stressed out. Anyways after updating to feisty fawn i go into the login screen option and check the box that says Allow adminstrators to login locally. Dont ask me why i checked that it just seemed like the right thing to do... My bad... but as soon as i log out the login screen never shows up. it just has that thing that says the computers thinking or loading. I retart several times and still nothing. When i just tap the power button when its loading it brings up a black screen with a few lines of directories and it says something about no image selected or something im not sure cuz it would only flash that for a second right before it shuts down. If anyone can plz help me. I dont want to have to re-install it cuz  it usually doesnt install until about my third try... I love ubuntu and i hope there is a way.......... I tried to boot up using that recovery mode thing but that just brang up a command line and i dont know any commands so im stuck... plz help me... Thank you in advance.

---

### Post by sent17inel on 2007-06-18
Another thing i just remember.... i'd always recieve this error when installing linux but it still installed fine... it was something like TTY 13 unknown stanza... dont know if that has anything to do with my problem but im just trying to get all the info out there....

---

### Post by xopher_mc on 2007-06-18
have you tried pressing Crtl+Alt+Backspace when it goes blank? this should restart the x-window manager and bring you the login screen :)

---

### Post by xopher_mc on 2007-06-18
Having re-read your post i see that will not actualy help sorry!

Load in recovery mode but don't go into command line when it asks just let it boot and post at what point it gets stuck

---

### Post by sent17inel on 2007-06-18
I did control alt backspace right now... it definetly restarted the the x-window manager but it will still hang... but it definetley did restart i noticed that.... ummm i dont unerstand i thought the recovery mode was just a command line... wut is it actaully supposed to do? because i dont touch anything and it gives me a command line.....

---

### Post by stchman on 2007-06-18
> **sent17inel said:**
> Im having a serious problem!!!! I've had to re-install linux completely three times and i finally figured out whats messing it up but i dont know how to fix it and i sure as hell dont want to re-install it again.... im gettin stressed out. Anyways after updating to feisty fawn i go into the login screen option and check the box that says Allow adminstrators to login locally. Dont ask me why i checked that it just seemed like the right thing to do... My bad... but as soon as i log out the login screen never shows up. it just has that thing that says the computers thinking or loading. I retart several times and still nothing. When i just tap the power button when its loading it brings up a black screen with a few lines of directories and it says something about no image selected or something im not sure cuz it would only flash that for a second right before it shuts down. If anyone can plz help me. I dont want to have to re-install it cuz  it usually doesnt install until about my third try... I love ubuntu and i hope there is a way.......... I tried to boot up using that recovery mode thing but that just brang up a command line and i dont know any commands so im stuck... plz help me... Thank you in advance.

I had something similar with my laptop.  Try this:

[http://www.stchman.com/feisty_tips.html](http://www.stchman.com/feisty_tips.html)

Whenever I restarted the workspace I was greeted with a black screen.

[daemon]
AlwaysRestartServer=true

---

### Post by sent17inel on 2007-06-18
True it is similar but your problem was turning your laptop off... mine will turn on and hang at the login screen menu... it just shows all black....

---

### Post by sent17inel on 2007-06-18
ok i saw the black screen flash some words and stuff...  and i think the computer hangs when its loading etc/rc.local    ..... i hope that helps...

---

### Post by sent17inel on 2007-06-18
also when i went into reconvery mode i saw it say:

mounting local filesystems . . .
[mntent]: warning: no final newline at the end of /etc/fstab

also i tried to follow stchmans advice but the sudo gedit isnt working... i dont understand how to use it.... plz help.

---

### Post by xopher_mc on 2007-06-18
I don't think that the laptop advice is your problem.  gedit is a gnome program so you can't get to it from command line. You should be able to get pico up however. 

When it seems to hang what happens when you press CTRL+ALT+F1. This should give you a bash login screen (bland and white text). Login, but not as root, what happens? Does it let you log in?

---

### Post by shawnw on 2007-09-17
I just hit this same exact problem and Im stuck.  Does anyone know how to resolve this issue. 

 Please help!!!!

---

