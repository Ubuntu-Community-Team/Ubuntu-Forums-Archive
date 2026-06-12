---
title: "Computer won't power up after failed ubuntu installation"
date: 2018-01-06
forum: Installation &amp; Upgrades
---

### Post by greystoke2 on 2018-01-06
I tried to install ubuntu via USB flash drive and something failed.  
The computer is an older PC, a Dell Studio Slim.
Now, the computer won't even power up. 
I have tested the power supply, after shorting ATX connector pins 15 & 16, and it's still working.
I have replaced the CMOS battery and verified the new battery is 3V (unloaded).
What could have gone wrong, and what could the fix be?
Could I have "bricked" the PC?

---

### Post by yancek on 2018-01-06
What does 'something failed' mean?  Did the install not complete successfully?  Did you get any error/warning messages during the install?  If so, what?
Are you saying that pushing the power button on the computer no longer starts it?  Sounds like a hardware failure of some kind.

---

### Post by greystoke2 on 2018-01-06
If I remember correctly, the display just froze and the computer became unresponsive. 
I don't remember an error message. 
After a while, I think I powered the computer off and decided to try to work on it later. Later ... the computer wouldn't power up.  
Full disclosure: I thought the power supply may have failed, so I bought a replacement.
In the process of installing the new power supply I learned how to test a power supply and determined the original power supply was OK after all.
It seems the motherboard isn't grounding the power supply "PS_ON#" pin, so the power supply doesn't provide DC to the computer.
Could the failed unbuntu install somehow have corrupted the BIOS?

---

### Post by RobGoss on 2018-01-06
> Could I have "bricked" the PC?

That is not likely, I've never seen Ubuntu brick any computer, It must be something wrong with that machine or maybe the power supply or a loose power cable. I would check this options first.

What version of Ubuntu are you trying to install?

---

### Post by greystoke2 on 2018-01-06
Ubuntu 16.04.3 LTS "Xenial Xerus"

---

