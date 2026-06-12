---
title: "Freezing with 8.04"
date: 2008-05-12
forum: Installation &amp; Upgrades
---

### Post by vbjustin on 2008-05-12
Hello, I had a question.  I wondered if anyone else here has had the same issue that I have with the new Hardy Haron install.  I was able to upgrade my OS from 7.11 to 8.04 with no problem, it worked great for about a week or so, then I started to have it freeze up on me.  Eventually it wouldn't even go past the login screen, it would give me the music in the beginning, and then stopped, having green lines on the bottom of the screen.  I would have to shut down manually, then try again with the same result.

After that went on for a day or two, I decided to give a fresh install a try.  Also had a few problems with the install, had to go in safe graphics mode to install it, but had no problems installing it after that.  Still didn't get anywhere with the fresh install, it froze at the same point.

Some other information is that I have a dual boot with Windows XP, so I know the hard drive is fine.  I also know my Graphics card is working fine as well because I have no problems with XP on my graphics card, I have a NVidia GeForce 7800GT.

Should I just go to 7.11 again, or should I give 8.04 one more try?  Is there something else that I can try, I was installing 8.04 off of a live CD, if that makes any difference, which I doubt.  I really liked 8.04, when it worked!  Right now I have 7.10, but am having issues with the wireless, which worked great with 8.04.  Thanks in advance!

Justin

---

### Post by prshah on 2008-05-12
> **vbjustin said:**
> Hello, I had a question.  I wondered if anyone else here has had the same issue that I have with the new Hardy Haron install.  I was able to upgrade my OS from 7.11 to 8.04 with no problem, it worked great for about a week or so, 

EDIT: Just realised that you are now not on 8.04; OK, does the live CD work? In that case, the below to be done from the live CD 8.04

Considering that one important difference between 7.10 and 8.04 is PulseAudio, I'd say you are having audio driver issues. Can you post the following files after a (failed) login?

> 
/var/log/messages
/var/log/Xorg.0.log
/proc/interrupts



as well as the output of the commands:
```

lspci | grep audio
lsmod | grep snd

```

It will serve as a starting point for troubleshooting.

---

### Post by housam on 2008-05-12
Did you gave ubuntu enough space to work ? enough RAM ? 
check your cd for errors and reburn it at slow speed as 2x - 4x .

---

### Post by vbjustin on 2008-05-12
> **prshah said:**
> EDIT: Just realised that you are now not on 8.04; OK, does the live CD work? In that case, the below to be done from the live CD 8.04

Considering that one important difference between 7.10 and 8.04 is PulseAudio, I'd say you are having audio driver issues. Can you post the following files after a (failed) login?




as well as the output of the commands:
```

lspci | grep audio
lsmod | grep snd

```

It will serve as a starting point for troubleshooting.

The Linux version I upgraded first was 7.11.  I did a check on the LiveCD and it didn't give me any errors.  The login seems to work, but it doesn't completely load the OS once I log in.  I will run the LiveCD and see if I can get the output of the files and run the commands as well.  I am currently at work, so I will do this once I get out.

---

### Post by sudo panda on 2008-05-28
I'm having similar issues with my ubuntu box aswell.
Mine would freeze up at random times, the keyboard would flash..and that was that. I had to revert to 7.10 just because i couldn't do anything for too long before i had another horrid crash.

---

