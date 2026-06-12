---
title: "black screen on boot after progress bar"
date: 2007-08-25
forum: Installation &amp; Upgrades
---

### Post by mckechan on 2007-08-25
I installed feisty on a IBM thinkpad T22. Went fine, booted fine, ran a lot quicker then XP so great.

THen sometime after the Ubuntu splash on booting the screen just went blank. I thought this was just an upgrade issue but when I selected the previous kernel the same thing happened. I never changed any x settings.

I was following this guide
[http://www.howtoforge.com/the_perfect_desktop_ubuntu7.04](http://www.howtoforge.com/the_perfect_desktop_ubuntu7.04)
(although leaving some parts out to save on bloating)

so it's either something to do with that or a system update


ANyway, how do I fix it???

---

### Post by Pumalite on 2007-08-25
Try Alternate CD. If 256 MB RAM or less>Xubuntu Alternate CD: [http://cdimages.ubuntu.com/xubuntu/releases/feisty/release/](http://cdimages.ubuntu.com/xubuntu/releases/feisty/release/)

---

### Post by mckechan on 2007-08-25
it is only 256MB Ram. It's my girlf's laptop and I'm trying to convince her
it's a good idea to add another 256Mb but she's not that in to it.

Seems like it worked fine while I was setting it all up. Is Feisty really not going to work???

Cheers

---

### Post by Pumalite on 2007-08-25
You could do it setting 500 MB swap ahead of time, but you would end up with a slow system anyway. The beauty of Xubuntu Alternate is that it installs easier and run faster in your system. Light Desktop.

---

### Post by mckechan on 2007-08-25
Thanks, i'll think about giving it a try...

I just booted in recovery mode, logged out of root and did 'startx' and it worked fine

What's the deal with the swap drive. I have 374MB swap partition but i can't change that without reinstalling right? So if i up the RAM i will have to reinstall anyway otherwise the swap partition is wrong?

---

### Post by Pumalite on 2007-08-25
If it worked as you said, you are fine. Consider my piece for future reference, in case you consider your system too slow.

---

### Post by mckechan on 2007-08-25
well i don't know whether it will work next time or whether i have to go into recovery mode and type start x everytime. 

Thanks for the advice, cheers!

---

### Post by mckechan on 2007-09-09
AH! I installed Xubuntu.

I have the same problem! After the splash I get a black screen and a system beep. 
This is really annoying! XP is too slow on this machine and linux won't startx :'(

---

### Post by Pumalite on 2007-09-09
Do you end up with a command line?. If not : Ctrl+Alt+F1, then
sudo dpkg-reconfigure xserver-xorg, choose most defaults, choose 'vesa' as the driver. Them: startx

---

### Post by mckechan on 2007-09-09
great, it works now thanks.

I couldn't get ctrl-alt-f1 to do anything so logged in in recovery mode...

---

