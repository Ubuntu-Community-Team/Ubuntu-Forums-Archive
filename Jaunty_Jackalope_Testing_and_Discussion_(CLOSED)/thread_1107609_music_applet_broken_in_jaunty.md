---
title: "music applet broken in jaunty"
date: 2009-03-26
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by Dawei87 on 2009-03-26
so i have the jaunty beta installed and ive installed music-applet but when i tried to add it to a panel it comes up with an error that says music-applet failed to load. this has happened all the way through the alphas but hasnt been fixed yet. does anyone else have this problem? if so, did you fix it?

---

### Post by Dawei87 on 2009-03-27
so now the applet has magically started loading, but it wont display the song information. just a single scrolling pixel next to the time. does anybody else have this problem?

---

### Post by Dawei87 on 2009-03-27
im the only one with this?

---

### Post by mirko_3 on 2009-03-28
No, I can't get it to work either, same as you. Thought it was python's fault, but now python is fixed and music-applet doesn't work...

---

### Post by Dawei87 on 2009-03-28
thats what i thought at first too. but yea, after several updates the problem persists. im surprised i havent found any other posts about this, i thought music applet was pretty popular...

---

### Post by Bios Element on 2009-03-28
Doesn't work for me either. Not really sure why.

---

### Post by mirko_3 on 2009-03-28
a post here somewhere says it's about porting it to the newwer version of python. In that psot the author says he's finished doing it, however the latest version i can find on getdeb.net doesn't install, and the latest release on the music applet website is from a couple months ago...

---

### Post by deathsshadow77 on 2009-03-28
glad im not alone

---

### Post by mc4100 on 2009-03-29
Missing python dependency. Solution:
```
sudo apt-get install python-numpy
```

---

### Post by IceReaver75 on 2009-03-29
> **mc4100 said:**
> Missing python dependency. Solution:
```
sudo apt-get install python-numpy
```

thank you for that.  After using this command the applet is working again with no problems here

---

### Post by cKGunslinger on 2009-03-29
> **mc4100 said:**
> Missing python dependency. Solution:
```
sudo apt-get install python-numpy
```

Brilliant!  Thanks for this info!

---

### Post by RadicalRaid on 2009-03-29
> **mc4100 said:**
> Missing python dependency. Solution:
```
sudo apt-get install python-numpy
```

Thanks for this! Worked for me. Only problem persisting is that I can't get the song information, it just displays single pixels.
Nothing to be worried about though.

Cheers!

---

### Post by Dawei87 on 2009-03-29
yea, im still just getting the scrolling pixel instead of song information. i didnt realize python-numpy is what fixed it, i installed it while trying to get something else to work. lol. thanks for the info

---

### Post by mc4100 on 2009-03-31
Seems to be fixed, now.
([https://launchpad.net/ubuntu/+source/music-applet/2.5.0-0ubuntu3/+changelog](https://launchpad.net/ubuntu/+source/music-applet/2.5.0-0ubuntu3/+changelog))

> music-applet (2.5.0-0ubuntu3) jaunty; urgency=low

  * Adding dependency on python-numpy (LP: #335492)

---

### Post by Dawei87 on 2009-04-02
hmmm.. im still not getting any song information though. is anybody else still having that problem?

---

