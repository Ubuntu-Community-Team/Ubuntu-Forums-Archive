---
title: "Kubuntu 6.0.6 - post 'install' problems"
date: 2006-05-14
forum: Installation &amp; Upgrades
---

### Post by shergill on 2006-05-14
Hi guys. I have searched the forums; but was unable to find someone with such a similar problem. I am trying to install kubuntu 6.0.6 using an install cd. It goes through 'phase1' of the install process fine. It goes through the grub process; installs grub and then prompts me to take out the cd and reboot. I do that and then I see the 'grub menu'. I chose 'Ubuntu, kernal 2.6.15-21-386' and I am on my way then. Btw; I see my XP pro listed in there too.

This is where things get weird. It goes to a black screen with 'kubuntu' logo and a progress bar. Then it does the 'loading esesentional drivers. mounting root.. configuring network.. hp image.. blah blah blah'.. all those end up as 'OK'. Then it again comes back to a black screen with a 'kubuntu' written in the middle. There is a progress bar underneath the big 'kubuntu' sign. After this; nothing happens for the longest time. The progress bar does not move. The only thing I see after a 'looong time' is a message that says 'restarting system log'. That is it.. 

Any ideas? If I log in using the 'recovery' mode; I can login using my newly created account. So the problem seems to be with the 'Windowing' system??

Thanks!

---

### Post by Herman on 2006-05-14
Does it drop to a shell with a black background with white typing and prompt you for your login (username) and then password? That's what mine did. If it does, do this, (after logging in), try typing: ```
# startx
``` just in case that works. If that doesn't work, (probably it won't, but try anyway), type: ```
# sudo dpkg-reconfigure xserver-xorg
``` If you an, be prepared with notes on the make and model of your video card if you can find that out somehow.
 You will be run through a series of grey panels asking questions about your video card, monitor and keyboard. 
The first panel will ask you something like 'autodetect video hardware? Answer 'Yes'.
 It will ask you a lot of technical questions, just read them all and try to answer as best you can.  If you don't know all the answers don't worry. Just press enter to acccept the default, that will probably be right anyway. The brand of your video card might be the only key question, I suspect.
When all the questions finish , you will be dumped back at the same black screen and #_ prompt you were at before.
Type ```
# startx
``` again and your new Kubuntu Dapper login screen will appear! 
That's if your problem is the same as the one I experienced, it sounds very similar.
Good luck, Regards, Herman :D

---

### Post by shergill on 2006-05-15
That did the trick. Thanks!

---

### Post by Herman on 2006-05-15
Okay, thanks for the feedback, I'm glad you got it working, all the best, Herman :D

---

