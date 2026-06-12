---
title: "Asterisk reinstall doesn't work"
date: 2010-07-08
forum: Installation &amp; Upgrades
---

### Post by epsolon77 on 2010-07-08
I first installed asterisk using sudo apt-get install asterisk on ubuntu 10.04.  After doing this the SIP packages did not install for some odd reason.

I uninstalled asterisk using sudo apt-get remove asterisk then reinstalled and now none of the asterisk config files are gone. 

I did a 

sudo apt-get --purge remove asterisk
sudo apt-get clean

deleted all files and directories I could find relating to asterisk, rebooted the machine, did a kernal upgrade, and a package update and reinstalled asterisk using sudo apt-get install asterisk, and all the config files are still missing.  What am I missing here!

---

### Post by Sonsum on 2010-07-08
> **epsolon77 said:**
> I first installed asterisk using sudo apt-get install asterisk on ubuntu 10.04.  After doing this the SIP packages did not install for some odd reason.

I uninstalled asterisk using sudo apt-get remove asterisk then reinstalled and now none of the asterisk config files are gone. 

I did a 

sudo apt-get --purge remove asterisk
sudo apt-get clean

deleted all files and directories I could find relating to asterisk, rebooted the machine, did a kernal upgrade, and a package update and reinstalled asterisk using sudo apt-get install asterisk, and all the config files are still missing.  What am I missing here!

Maybe try installing it through aptitude? I've heard its better at handling dependencies.

So your command would be
```
sudo aptitude install asterisk
```

Hope this works!

---

### Post by epsolon77 on 2010-07-08
I will give that a try in the AM when I get into the office.  To clarify I am pretty sure this is not an issue with dependencies, because the working directories for asterisk are empty on the reinstall.  So the directory //etc/asterisk has no files in it, which is VERY unusual.  
I will try aptitude in the morning.  Possibly a different package manager will fix the issue.

---

### Post by epsolon77 on 2010-07-08
Couldn't sleep so I tried aptitude with no luck.  I ran the full battery of aptitude commands, includeing purge, clean, autoremove, forget-new, update, restarted server and ran install, and still no files in the directory.

---

### Post by Sonsum on 2010-07-09
I don't know much about asterisk (even really what it does. haha), so I can't be of a lot of help. I just sorta know my general troubleshooting.

So hopefully someone with some more experience comes on. 

*plays drums in a fashion very similar to the ubuntu startup noise in the hopes of attracting other Ubuntu users*

---

### Post by epsolon77 on 2010-07-09
Thanks for your help Sonsum.  I posted here cuase I don't think asterisk has anything to do with it...

Oh well, I guess I'll format and start from scratch since I'm under a deadline.  Again Sonsum thanks for the input, even though it didn't work it was a direction I hadn't thought about.

And please, if anyone else has encountered this I would still love to see what the solution is.

---

### Post by epsolon77 on 2010-07-09
Ok figured it out.  The issue was two fold.  On my sip.conf file was not coded correctly, so the sip plug in could not load.

Second, there is a dependancy, asterisk-config which loads the config files.  I needed to install then purge that before reinstalling asterisk with a valid sip.conf file in place.

---

