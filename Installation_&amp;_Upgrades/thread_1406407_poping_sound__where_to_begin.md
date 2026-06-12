---
title: "poping sound?  where to begin"
date: 2010-02-13
forum: Installation &amp; Upgrades
---

### Post by greenwom on 2010-02-13
So I have 9.10 installed on my dv9000 laptop. (HP 9201ca)

Audio device 
```
00:10.1 Audio device: nVidia Corporation MCP51 High Definition Audio (rev a2)
```

The system pops at random and it does seem to do it more if I am actively opening and closing windows.  It happens with the headphone jack plugged in or with it unplugged.

I've muted the mic with no change.

I don't know where to begin diagnosing this one.  I've read the sticky's for 9.10 and googled but can't find anyone else with the problem.

The system is dual booted with Vista, with no problems on that end

---

### Post by greenwom on 2010-02-14
I've also tried different revisions of the driver

---

### Post by blackdalek on 2010-02-18
I have the same laptop and audio. I have the same problem. I can't find an answer.

---

### Post by blackdalek on 2010-02-18
this fix worked [http://ubuntuforums.org/showthread.php?t=1314834](http://ubuntuforums.org/showthread.php?t=1314834)
Apparently there is some frankly bizarre option to turn off power to the speakers after 10 seconds/minutes/whatevers....

---

### Post by greenwom on 2010-02-18
Looks great, I'll try it and post my outcome... Makes sense.

I love Ubuntu but 9.10 has really stressed the relationship... :)

I've had to Vista a lot

---

### Post by presence1960 on 2010-02-18
> **greenwom said:**
> So I have 9.10 installed on my dv9000 laptop. (HP 9201ca)

Audio device 
```
00:10.1 Audio device: nVidia Corporation MCP51 High Definition Audio (rev a2)
```

The system pops at random and it does seem to do it more if I am actively opening and closing windows.  It happens with the headphone jack plugged in or with it unplugged.

I've muted the mic with no change.

I don't know where to begin diagnosing this one.  I've read the sticky's for 9.10 and googled but can't find anyone else with the problem.

The system is dual booted with Vista, with no problems on that end

[http://swiss.ubuntuforums.org/showpost.php?p=8099760&postcount=12](http://swiss.ubuntuforums.org/showpost.php?p=8099760&postcount=12)

The above worked for me, I had popping noises also from my audio on a desktop I built. The problem seems to be with the powersave function of HDA audio cards. If you have an HDA audio card do what the link suggests.

---

