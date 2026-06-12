---
title: "Failed to Start Session error"
date: 2019-09-11
forum: Installation &amp; Upgrades
---

### Post by Clueless Wonder on 2019-09-11
Hello!  I need some help with a login issue following an installation.

I did an install of 18.04 mini.iso on a Dell Inspiron 6000 laptop. First, I left the Task-sel  options blank, then, when at a terminal login-prompt on restart, I  installed Lubuntu-core. It worked fine.  Realizing, I wanted something a  little different, I started over, did the same process, but installed  Lxde-core instead.  This time, when I restarted, I got to the login and  password and, when I typed my password, I received a Failed to Start  Session error.  Going back to terminal and typing Startx gets me to the  desktop.  I checked that LightDM was installed and it was.  

I am  wondering if anyone knows anything else to check or any ideas as to  what the problem is causing the Failed to Start Session error.  Is there something else that needs to be installed, or does it sound like it was just bad installation?

Thanks in advance!

---

### Post by cruzer001 on 2019-09-11
Is this 18.04 or 19.04?

---

### Post by Clueless Wonder on 2019-09-11
Good point!  18.04.  I have updated the post.

---

### Post by cruzer001 on 2019-09-11
I have done it in the pass, but with the "LXDE" package and not the core package.  Works nicely out of the box and add some necessary packages.  A better choice IMO.  What do you intend to use it for?

---

### Post by Clueless Wonder on 2019-09-11
Hi Cruzer001 - Thanks for the reply!  I plan on using it for everyday use.  I have installed it before on a different machine without problems.  However, it has been a while and I can't remember if there was another package that need to be installed (like xorg, lightdm, etc) that I am forgetting.

---

### Post by cruzer001 on 2019-09-11
Lightdm includes xserverxorg may be enough without xorg.  
[https://packages.ubuntu.com/bionic/lightdm](https://packages.ubuntu.com/bionic/lightdm)
But I say your mix should work.  Guess I could fire it up and see.

---

### Post by cruzer001 on 2019-09-11
Well I loaded xorg/lightdm/lxde-core and it wouldn't boot.  No startx

I installed xinit just to see and still no startx.

---

### Post by cruzer001 on 2019-09-11
I didn't catch it at first, but there are 404 download errors.  Maybe server troubles today.

I did get it to download proper once.

[ATTACH=CONFIG]283999[/ATTACH]

I suggest trying again later.

---

### Post by Clueless Wonder on 2019-09-13
Hi Cruzer -

thanks for trying it out.  I downloaded a new mini.iso copy and went through all the steps again and came to the same place....needing to enter through startx.    Very strange.  You said you got it to work once without doing startx or anything?

---

### Post by cruzer001 on 2019-09-15
Just to be sure I loaded it up again with just the three packages and it worked out of the box.

xorg: 1:7.7+19
lightdm: 1.26.0-0
lxde-core: 10

And it worked out of the box.  There are two things that I do different from you that may/may not affect the install.

I use the server iso and not the mini iso.  They will both give you a mini install, but the server.iso includes wifi out of the box.

And #2 - I'm doing this in a virtual machine (KVM) which will not always give the same results as a physical install.

I suspect your install in hanging up on lightdm and would suggest you replace lightdm with gdm3.

---

### Post by Clueless Wonder on 2019-09-15
Thanks for trying it again.  I have a few clarifying questions to make sure I understand.  How did you load the three packages?  Was it in the order listed and using apt install when getting to the prompt following reboot from the server install?  And did you specify those specific versions of those packages?  If so, how did you do that?

About the hanging on the install of lightdm....would I see that during the process or would it not be obvious it is doing that?

Thanks again!

---

### Post by cruzer001 on 2019-09-15
That is the order I loaded them in and the versions were taken from the repositories with the install command.  Nothing special done on this end.

You can have both gdm3 and lightdm installed and switch between the two.  If gdm3 works, I bet you could then switch back to lightdm and it would magically work.  Meaning there is a lacking package in lightdm that needs to be traced down.

I mainly use gdm3 on all my installs just to make it easy on me.  In your case of a core install, gdm3 is really too bloated and I would opt for a basic display manager.  In those cases I use "xdm" which will normally work out of the box if startx works.  You could also give it a try.

Gnome-session is also installed with gdm3 which is a ultralight install of gnome-shell.  It can be chosen at the login screen, it should be fast since it also a core install.  Just something else to play with :)

---

### Post by Clueless Wonder on 2019-09-23
Hi Cruzer!  I didn't receive a notification of your reply and just tried to re-install on a Dell Optiplex 3010.  The same issue happened again.  So then I installed xorg.  Lightdm was already installed.  Issue still happening.  I came here to report back and saw that you had replied.  Do you think it would have made a difference if I installed them in the order you listed?  If so, I will re-do it.

It is really weird because I was able to get this to work previously and I don't think I did anything special with the install.

Thanks again for your help!

---

### Post by Clueless Wonder on 2019-09-26
Hey Cruzer -

I decided to bite the bullet and try it.  I installed from the mini.iso.  Restarted.  Installed xorg.  Installed Lightdm.  Restarted.  Installed LXDE-core.  Restarted.  Tried to log-in and got the Failed to Start Session message.  Tried Startx and that no longer works (it had worked when I installed LXDE-core only).

Can you think of why it worked for you and not when I did it?  Should I have re-booted in between xorg and lightdm?  Or, maybe another reason?

---

### Post by cruzer001 on 2019-09-27
Hey CW

Just wanted to let you know I'm still here.  Its Friday morning in my part of the world and a busy day for me.  I do want to see this get resolved, but won't be available until tonight or Saturday.  So please hang in there, I will return.  Maybe someone else might even chime in.

Regards

---

### Post by Clueless Wonder on 2019-09-27
Hi Cruzer -

thanks for checking in.  I wanted to let you know that, after some research, I noticed that there is a drop-down near the login that lets me choose between Openbox and LXDE.  After playing with that a bit, I was able to go straight in with LXDE.  I am hoping to test the other computer I did the install on to see if that is applicable there, too.  I didn't do the re-install with your steps on that one, just the initial install LXDE-core.  I will post back if that dropdown is there and if that resolves things.  If it does, this will be solved and I will feel a bit silly for missing that.  ;)

---

### Post by cruzer001 on 2019-09-28
Yes OpenBox is a dead session, glad you came across that.  So do you now have it working correctly?

Its snowing here and I plan on being around all day if anything else needs to be resolved.

---

### Post by Clueless Wonder on 2019-09-28
Hey Cruzer!  Just checked the other PC and it was the same issue...I think neither LXDE or Openbox were selected by default.  Once I selected LXDE, I was good.  Like I said, feeling silly and apologize for bothering you for something that was due to my oversight.  Thanks for all your time and suggestions.  I definitely learned something!

---

### Post by cruzer001 on 2019-09-28
Your welcome
> feeling silly and apologize
We have all been there and done that.  No need to beat yourself up.

drop in again :)

---

