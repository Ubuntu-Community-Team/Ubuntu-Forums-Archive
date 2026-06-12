---
title: "Helix Player and Real player whats up?"
date: 2008-02-12
forum: Installation &amp; Upgrades
---

### Post by colddepression on 2008-02-12
I need to know how to get the helix player to play rm files.. Can anyone tell me how toet it to work right. I downloaded a anime from a websitebut its in  a rm file. When I go to use helix it says " This player does not have the capablites to play back this content. This content is supported by real player ". Then I click on deatails and it says this" The following compontent are required audio/x-pn-realaudio " . The I go to the realplayer site it gives and download the realplayer10Gold.bin and then what do I do? "Note: I am using ubuntu 7.10 Gusty Gibbon"

Just tellin yall I am a ubuntu newbie and I jsut want to get this and one other little detail fixed so I can enjoy it. So THANK YOU A WHOLE LOT in advanced.

---

### Post by Partyboi2 on 2008-02-12
Assuming the RealPlayer10GOLD.bin is downloaded to your Desktop
Open a terminal (Applications>Accessories>Terminal)
```
cd Desktop
```then type or paste
```
./RealPlayer10GOLD.bin
``` to install

---

### Post by colddepression on 2008-02-12
It says permission denied

---

### Post by Partyboi2 on 2008-02-12
try changing file permission 
```
 chmod 755 RealPlayer10GOLD.bin 
```

---

### Post by colddepression on 2008-02-12
would I type the cd Desktop agin adn then put that? Cause ifso it did nothing

---

### Post by Partyboi2 on 2008-02-12
can you 
cd Desktop
then post the output to this:
```
ls -l RealPlayer10GOLD.bin
```

---

### Post by colddepression on 2008-02-12
heres what happen brandon@brandon-desktop:~$ cd Desktop
brandon@brandon-desktop:~/Desktop$ ls -l RealPlayer10GOLD.bin
-rwxr-xr-x 1 brandon brandon 5790356 2008-02-12 04:25 RealPlayer10GOLD.bin

---

### Post by Partyboi2 on 2008-02-12
make it executable
```
cd Desktop
``````
chmod a+x ./RealPlayer10GOLD.bin

```then
```
./RealPlayer10GOLD.bin
```:)

---

### Post by colddepression on 2008-02-12
agin a big fat nothing
as in nothing happens

---

### Post by Partyboi2 on 2008-02-12
> **colddepression said:**
> agin a big fat nothing
as in nothing happens
What do you mean nothing happens? After you have made it executable what happened when you try to start the install
```
./RealPlayer10GOLD.bin
```
Did it say permission denied again?

---

### Post by colddepression on 2008-02-12
Its saying installing now for soem reason

---

### Post by colddepression on 2008-02-12
Quick Question accidently installed it on my deskt top how do I move it to sound and video

---

### Post by Partyboi2 on 2008-02-12
Have a look under Applications>Sound&Video it hopefully should be listed. I can't remember if it automatically appears there or if you have to add it. If its not there you can add it by going to System>Preferences>Main Menu and highlight Sound &Video on the left, then on the right choose "new Item" and a launcher will open where you fill in the name of the program. (Whatever you want to call it) next is the "command" to start the program which is realplayer and "comment" leave blank unless you want to add something. After that press ok, then  it should appear under Sound&video

---

