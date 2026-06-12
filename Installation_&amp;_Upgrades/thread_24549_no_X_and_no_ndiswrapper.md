---
title: "no X and no ndiswrapper"
date: 2005-04-07
forum: Installation &amp; Upgrades
---

### Post by jordanau on 2005-04-07
I just followed the Ubuntuupdate wiki perfectly. I have two problems.

1. I can't get X to start. I got a bunch of error messages when it tried to start and all i can use is command line. 

2. Secondly, Ndiswrapper is no longer working although it says my driver is still installed.

I have to run (I am at a computer lab right now) anything anyone knows would be great thanks.

---

### Post by mthaddon on 2005-04-07
It would be helpful if you could post the output of your xorg log so that we can see what error messages you're getting and/or what card/hardware specs you have.

If you're trying to work out how to do this without having X up and running, if you have postfix running (which by default you probably do) you can do:

cat filename | mail -s "Subject" "email@myemailaddress.com" 

and then you can retrieve the email from a machine that does have a GUI. Or you could just get to this site through links/lynx (console web browser). If you want to copy and paste, open up a two virtual consoles (ctrl+alt+F1 ... ctrl+alt+F2 - switches between virtual consoles, ctrl+alt+F7 is the default console that X will be on when it comes back up) and use the mouse to select/paste the text.

Thanks, Tom

---

### Post by jordanau on 2005-04-07
Thank you very much for the response Tom. I guess right now my priority is to get ndiswrapper fixed because without wireless i can't get anything emailed out. 
I have an ATI 9700 pro All in Wonder video card by the way. Also, before restarting, I ran :
sudo apt-get install xorg-driver-fglrx
before restarting as well. (It is in the comments of the upgrade wiki)

EDIT:
ndiswrapper worked perfectly in warty for the near 2 months i ran warty. 
Don't know how much this matters but.

my connection stayed up after i ran upgrade
it was lost after restarting

I only updated the main restricted repository, should i have upgraded others? I thought I should get main restricted running before I tried anything else.

---

### Post by jordanau on 2005-04-08
Alright! 

I got ndiswrapper fixed by converting all of my repositories over to hoary, not just the restricted main. I then ran apt-get update and dist-upgrade and got my ndiswrapper connectivity back.

The X fix is thanks to dcraven on #ubuntu. my /etc/X11/xorg.conf file somehow had a uppercase "K" in "Keyboard" for the keyboard driver. I made it a lowercase k and everything works great. 

Hope this may help someone else with a similar problem.

---

