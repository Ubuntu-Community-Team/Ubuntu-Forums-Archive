---
title: "Noob needs desktop help"
date: 2007-06-08
forum: Installation &amp; Upgrades
---

### Post by Team Scream on 2007-06-08
Noob in every since of the (Ubuntu) word.
Just successfully installed Ubuntu studio on a Dell Latitude D600.

I have read the Ubuntu support pages.

I cannot activate the desktop effects, there is no option to do this in my System/Preferences drop down.
According to the Ubuntu help pages, there should be a: System/Preferences/Desktop Effects pane for me to select "enable desktop effects"
I do not see this option anywhere.

I am just getting started with Linux for the first time ever, so far I like what I see, I am doing this first on the laptop before I move ahead with a triple boot on my main system (XP/Vista/Ubuntu).  

Thanks for any help in advance, please be advised, when I say noob, I really mean noob, I have no idea how to really navigate this system yet so if you could be specific with your replies, I would really appreciate it!

---

### Post by raja on 2007-06-08
Seeing [this thread]("http://ubuntuforums.org/showthread.php?t=458664"), it appears that desktop effects are not in Ubuntu studio. I personally have no experience of studio. However you can do ```
sudo aptitude install desktop-effects
``` in the terminal.

---

### Post by Team Scream on 2007-06-09
Fantastic Raja,
Thanks so much, 
Got that installed, but when i go to enable desktop effects, all I get is a solid white screen which as I read defaults back to the non enabled state after 40 seconds, could it be this laptop is not capable of running desktop effects or should I dig around for more info?
The biggest challenge for me is determining what state the laptop is in with regards to drivers and such, I am just not there yet with Linux.
Again, super Noob, 4 hours into my first Linux experience

---

### Post by raja on 2007-06-09
You might need a driver for the ATI video card. Go to System-Administration-Restricted drivers manager in the menu to see if it can suggest a proprietary driver.

---

### Post by Team Scream on 2007-06-09
Thanks raja,
I get a message which says "your hardware does not need any restricted drivers"

heres a pic of the device manager, maybe this helps?

[IMG]http://farm2.static.flickr.com/1283/536796878_3a464486cc_o.png[/IMG]

---

### Post by raja on 2007-06-09
If you really want to give it a try, my suggestion is to use Beryl. Follow the guidelines for doing it with an ATI card from the Beryl site.

---

### Post by Team Scream on 2007-06-10
is beryl just emulation of what should work in Ubuntu?
just curious, 

i will read up on it tonight and give it a try

---

### Post by raja on 2007-06-10
Beryl is a project that branched off from Compiz, providing similar functionality. The advantage of installing it by yourself, in my opinion, is that you have some clearly defined steps to follow and know what to troubleshoot. With the inbuilt compiz (which is what the 'Desktop Effects' is), there is not much scope to troubleshoot or tweak.

---

### Post by Team Scream on 2007-06-10
raja, 
I do appreciate your help here thank you so much.
I have been poking around on the beryl forums but don't really see a clear tutorial on how to install it for noobs?
any tips you can offer?

---

### Post by raja on 2007-06-10
You can look at [this]("https://help.ubuntu.com/community/Beryl/ATI/Feisty?highlight=%20beryl%20#7672586918996396505") and [this]("http://ubuntuforums.org/showthread.php?t=265678").

---

### Post by Team Scream on 2007-06-10
raja,
thanks again.
followed the first link, and it appears I did it all correctly as I installed and can now can get into beryl settings manager, but when i try to launch beryl manager, i go to the same white screen of death I got with desktop effects.

---

### Post by raja on 2007-06-10
I may not be able to help you much there. On two systems with an Intel card, I have Beryl working beautifully. On one system with an old Nvidia card, I could not get it to work smoothly and gave up. 
However, I found t[his thread]("http://ubuntuforums.org/showthread.php?t=362381&highlight=beryl+white+screen") which seems to suggest a couple of fixes - maybe you can try them.

---

