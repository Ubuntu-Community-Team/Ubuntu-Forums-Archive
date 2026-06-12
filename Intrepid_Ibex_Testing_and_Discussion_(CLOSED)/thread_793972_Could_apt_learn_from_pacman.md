---
title: "Could apt learn from pacman?"
date: 2008-05-14
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by shifty2 on 2008-05-14
Currently, when you try to install/update through the terminal in ububtu you get the flurry of servers etc rushing down the screen and its just a bit chaotic.

In contrast, updating in archlinux with pacman looks like this:
```
:: Synchronising package databases...
 core                      24.5K   78.6K/s 00:00:00 [#####################] 100%
 extra                    312.9K  127.9K/s 00:00:02 [#####################] 100%
 community                335.8K  146.6K/s 00:00:02 [#####################] 100%
 unstable                   4.7K   39.3K/s 00:00:00 [#####################] 100%
 archlinuxfr               22.0K  122.2K/s 00:00:00 [#####################] 100%
 local database is up to date
```
Which is much more clear and concise. Is there a reason this isn't implemented already?

---

### Post by qamelian on 2008-05-14
Personally, I prefer the apt method because it displays the results of specific repositories including any third party repos I have enabled. The results from pacman don't look all that informative to me.

---

### Post by Skarjoko on 2008-05-14
I've always liked the way pacman displayed the servers. I would personally love it if apt did something similar.

---

### Post by shifty2 on 2008-05-14
That is all my repositories :-) In arch each "repository" is given a name, archlinuxfr being my only additional one. It shows exactly the same information as apt but in, i feel, neater way.

---

### Post by qamelian on 2008-05-15
> **shifty2 said:**
> That is all my repositories :-) In arch each "repository" is given a name, archlinuxfr being my only additional one. It shows exactly the same information as apt but in, i feel, neater way.
Then I guess I'm missing something. Are you just talking about the format of the output then? If so, then you're right that is certainly more readable.

---

### Post by cdean on 2008-05-15
> **qamelian said:**
> Personally, I prefer the apt method because it displays the results of specific repositories including any third party repos I have enabled. The results from pacman don't look all that informative to me.

'Twould be cool if apt displayed like pacman, but spat out any lines with errors.

---

### Post by nhandler on 2008-05-15
I also agree. Pacman seems to have a nicer output than apt. Might I suggest adding this to brainstorm.ubuntu.com? That way, you could get feedback from many more users who may not visit the Intrepid Ibex Development forum here.

---

### Post by rubicon on 2008-05-17
Yep, pacman seems to be much cleaner than apt in this way! What should be as informative as apt now, is **logs**, imho :)

But knowing developers' eagerness about changes... Maybe it would be appropriate to add such cleaner view to **aptitude** instead (not sure about apt)? After all, it is considered as user-friendly front-end and definitely need clean interface.

---

