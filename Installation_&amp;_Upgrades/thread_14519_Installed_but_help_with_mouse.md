---
title: "Installed but help with mouse"
date: 2005-02-08
forum: Installation &amp; Upgrades
---

### Post by butt on 2005-02-08
I have a MX510 installed through the ps2 port.. I searched the forums and found solutions but i don't know how to get to the point of how to actually do the solution. if u get what i mean. As in I boot Ubuntu up and then what? how do i get to any menus w/o the mouse inorder to fix it?
links i found
[http://www.ubuntuforums.org/showthread.php?t=2661&highlight=mouse+work](http://www.ubuntuforums.org/showthread.php?t=2661&highlight=mouse+work)
[http://www.ubuntuforums.org/showthread.php?t=4357&highlight=mouse+work](http://www.ubuntuforums.org/showthread.php?t=4357&highlight=mouse+work)
[http://www.ubuntuforums.org/showthread.php?t=12159&highlight=mouse+work](http://www.ubuntuforums.org/showthread.php?t=12159&highlight=mouse+work)
[http://ubuntuforums.org/showthread.php?t=3828&highlight=thumb+buttons](http://ubuntuforums.org/showthread.php?t=3828&highlight=thumb+buttons)

obviously im not the only one, I don't think i missed any options to choose my mouse? or select auto? but why wouldn't ubuntu just select auto anyways?


anyways thanks for help in advance

---

### Post by john_spiral on 2005-02-08
Hi,

I think one of your links may solve my very own mouse problem.

If your mouse works under the Live Ubuntu cd this will help you to edit the necessary files on your hard disk using the working mouse, if it doesn't work under the live cd then I think there is an option right at the beginning of the hd boot sequence where you can select the prompt only display.

Someone more clued up will hopefully give the sequence of commands to edit the necessary files using an editor like vi.

caio

---

### Post by butt on 2005-02-08
[QUOTE=john_spiral]Hi,

I think one of your links may solve my very own mouse problem.

If your mouse works under the Live Ubuntu cd this will help you to edit the necessary files on your hard disk using the working mouse, if it doesn't work under the live cd then I think there is an option right at the beginning of the hd boot sequence where you can select the prompt only display.

Someone more clued up will hopefully give the sequence of commands to edit the necessary files using an editor like vi.

caio[/QUOTE]
 actually yes, the Live Ubuntu worked fine, and i could use my mouse and all, but i don't understand howw to get from there to editing the necessary files  on the hard disk? anyone fill me in on a step by step?

---

### Post by butt on 2005-02-08
[QUOTE=butt]actually yes, the Live Ubuntu worked fine, and i could use my mouse and all, but i don't understand howw to get from there to editing the necessary files  on the hard disk? anyone fill me in on a step by step?[/QUOTE]
 I have actually asked around and apparently Ubuntuu uses a very old verison of X and i should go with Redhat debian or fedora.. so looks like ill be doing that until the next release of ubuntuu or something updated comes along

---

### Post by butt on 2005-02-09
[QUOTE=butt]I have actually asked around and apparently Ubuntuu uses a very old verison of X and i should go with Redhat debian or fedora.. so looks like ill be doing that until the next release of ubuntuu or something updated comes along[/QUOTE]
 ok so i installed hoary again.. NOthing worked. So I wanted to know SINCE LIVE Ubuntu works fine and Works great, MOUSE WORKS can i someone copy the config from LIVE to hoary installed on PC ? Or can someone please go over why the F*C* i can't get my mouse to work and help me get it working

---

### Post by butt on 2005-02-09
I found out from going to The IRC channel that if u boot up in recovery mode

then do X in console this should produce something for somepeople, however this did nothing for me
i did this
since just X doesn't work
exec /usr/X11R6/bin/X

... it booted to a blank screen with a X in the middle and froze......... 

anyone?

---

### Post by butt on 2005-02-09
so basically, it came down to this

LOAD UP UBUNTU and then unplug your mouse, and plug it back in...
OMG how ghey, now the question is this

HOW DO I get it to never do that again?

---

### Post by tgoose on 2005-02-28
You mean you literally just loaded up ubuntu, pulled the cable out and put it back in? I think I did that but it didn't work. Mind you, I couldn't get any response from the mouse in the bits of Debian I managed to get on to either when I had that installed briefly. 

When trying to use the xf86cfg mentioned, if I go through the login bit to get to the prompt (sorry, I can't remember the name atm) then it denies me access to writing the config file. If I press esc before ubuntu starts loading properly and go to the prompt from the root user (I think), then it seems to work, but when I reboot no changes have been made.

edit: if it makes any difference, I have an old "bitstar" 3 button mouse. Or an older still 2 button one, but that didn't work either.

---

