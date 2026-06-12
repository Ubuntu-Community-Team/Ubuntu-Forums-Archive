---
title: "problem with a .bin file"
date: 2006-12-14
forum: Installation &amp; Upgrades
---

### Post by tsallinia on 2006-12-14
hello guys. I am really glad that I am now to the community of ubuntu. I used suse for 2 years and I sick and tired of themhttp://ubuntuforums.org/images/smilies/eusa_wall.gif

now, i have one problem. I downloaded a free game, named planeshift, and  I tried to install it. Its a bin file. I double clicked it and it says an error message:failed to open.no application suitable for automatic installation. 

In the read me file, it says to go to the terminal and do the run command. so I typed  ./plainshft.bin.run and nothing happened. can you please help me? by the way planeshift is a free mmorpg, 3d,very good and with 300.000 people.try it:)

---

### Post by andreas64 on 2006-12-14
Hi,

change to the directory, where the file resides and try './plainshift.bin'

Andreas

---

### Post by anubhavrocks on 2006-12-14
do a chmod +x plainshft.bin
and then try ./plainshft.bin

> **tsallinia said:**
> hello guys. I am really glad that I am now to the community of ubuntu. I used suse for 2 years and I sick and tired of themhttp://ubuntuforums.org/images/smilies/eusa_wall.gif

now, i have one problem. I downloaded a free game, named planeshift, and  I tried to install it. Its a bin file. I double clicked it and it says an error message:failed to open.no application suitable for automatic installation. 

In the read me file, it says to go to the terminal and do the run command. so I typed  ./plainshft.bin.run and nothing happened. can you please help me? by the way planeshift is a free mmorpg, 3d,very good and with 300.000 people.try it:)

---

### Post by _simon_ on 2006-12-14
With .bin's I just do 

```

sh plainshft.bin

```

---

### Post by tsallinia on 2006-12-14
thank you all. the solution was the one that  anubhaverocks  described. when i wrote this in the terminal it was installed with no problem

---

