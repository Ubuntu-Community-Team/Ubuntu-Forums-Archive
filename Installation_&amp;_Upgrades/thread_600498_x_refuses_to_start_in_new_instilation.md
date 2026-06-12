---
title: "x refuses to start in new instilation"
date: 2007-11-02
forum: Installation &amp; Upgrades
---

### Post by MyKal on 2007-11-02
ok heres the deal 

i start out using linux mint but i dont like it 

so gutsy is finally released and im all like "YES" i go ahead and installit in my girlfriends hp laptop and it works AWESOME 

then im like ok il kill mint for it 

i go to install it on my homebrew (asus motherboard 1 gig ram AMD Opteron dual64 and nvidia 7950GT with 512 onboard) i get past the loading screan and for only a moment i see my curser then it quites and goes to command line the last command being running boot scripts it does this over and over and over again untill finally i see lins version of the blue screan of death (the one with the grey fram surrounding the message telling you something failed) 

normally this is ok if been dealing with nix system s for years and i have yet to come head on with a problem i cant fix but this time i just dont know 

the screan wich usually gives some kind of informative insite into why x didnt start just says "x has restarted  6 times this may mean that something is wrong wait to minutes and try again?" 

"this may mean that something is wrong" something is wrong??? 

REALLY???

thats it?

oh well i do as it says and i wait to minutes this time it boots into the system and i am able to test everything cool 

it all works (other then the fact that compiz didnt start wich i figured a little odd with my particular video card being about ten times what should be required but i just figured it was the cheep buntu drivers fault) 

ok so like i said i test everything its all good 

i start installation i set up my partitions and i do the import from windows (everything but the wallpaper)

it installs without a hitch 

BUT

after i restart for the first time 

same problem again 

only this time 
the whole two minute wait thing dosnt fix anything 

it just loops and restarts x 

over 

over 


over

and over again until i am slamming my bloodied face into my keyboard with frustration

and now here i am 

typing away in the forums from my (gasp) windows partition 

oh how the mighty have fallen

anyway any help you guys can provide would be really great 

thanks alot

---

### Post by Pumalite on 2007-11-02
Did you try:
sudo dpkg-reconfigure xserver-xorg

---

### Post by MyKal on 2007-11-02
not yet but il give that a try

---

### Post by Pumalite on 2007-11-02
Good luck.

---

### Post by MyKal on 2007-11-02
ok that got me into a very very low graphics mode desktop and from there i was able to get my nvidia drivers installed and now everything seems fine accept for one thing 

i cant get dual monitor support through nvidia setting 

it works when i set it up manually using xinorama but that breaks compiz and we just cant have that

---

### Post by Pumalite on 2007-11-02
Start a new thread.

---

