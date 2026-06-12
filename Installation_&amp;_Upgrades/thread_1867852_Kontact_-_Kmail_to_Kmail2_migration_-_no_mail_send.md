---
title: "Kontact - Kmail to Kmail2 migration - no mail sending"
date: 2011-10-23
forum: Installation &amp; Upgrades
---

### Post by swissinvestor on 2011-10-23
Don't even try to do an automatic migration from 11.04 to 11.10, it doesn't work and its a plain mess. For anyone not needing a PIM (I do), this would be the time to switch to another system because it's too much pain.

I finally made it work, by migrating manually and hopefully I am beyond my problems now. I had such a mess on the original machine, that I copied my data to a new computer and started from scratch. I am not a computer nerd and was simply unable to roll back on my initial machine to do a new try (I could not figure out which files to delete safely to do this.

After having succeeded in migrating my date (ca 9 GB), I was unable to send any emails.
"akonadictl restart" solved this problem too. I have no clue why, but it worked.
After migration, only the folders are visible but no emails. A right click on the folders and "update folders and its subfolder" will bring them back. 

I am using Ubuntu 64-bit

---

### Post by dargaud on 2011-10-23
Solved ?!? Well, if so you are [lucky]("http://ubuntuforums.org/showthread.php?p=11383991#post11383991"). My word of advice if you are using kmail on kubuntu would be "DO NOT UPGRADE TO 11.10" if you want to keep your mail. The upgrade process to kmail 2 doesn't work. At all. Oh, yeah, in case you didn't know, [**kmail2 doesn't even work on a fresh install of 11.10**]("http://ubuntuforums.org/showthread.php?p=11384025"). You have been warned.

---

### Post by swissinvestor on 2011-10-23
Well, it worked for ME finally, that is all I can say. I was not at all happy about the process which took me a full day - I believe Kmail2 is Beta-Quality at best - and I believe it is well above any average user ability. I also wish that the Kontact developers would be more verbal in what works and what not and too much is not working.

The automatic migration does NOT work at all. Not making a backup before you start is a suicidal attempt.

PS I am not using Kubuntu, I use Kontact on Ubuntu 64-Bit

this at least was of some help to me: [https://wiki.kubuntu.org/OneiricOcelot/Final/Kubuntu/Kmail2](https://wiki.kubuntu.org/OneiricOcelot/Final/Kubuntu/Kmail2)

---

### Post by jtappin on 2011-11-05
> **swissinvestor said:**
> Well, it worked for ME finally, that is all I can say. I was not at all happy about the process which took me a full day - I believe Kmail2 is Beta-Quality at best - and I believe it is well above any average user ability. 

Beta??? Nearer to pre-alpha!!!

Seriously though--does anybody know of a way to transfer all my folders to thunderbird? And preferably the account settings too. Niehter of the scripts I've found on the net actaully work.

---

### Post by jtappin on 2011-11-05
> **jtappin said:**
> 
Seriously though--does anybody know of a way to transfer all my folders to thunderbird? And preferably the account settings too. Neither of the scripts I've found on the net actually work.

To answer myself, the python script and recipe at: [http://dcwww.fys.dtu.dk/~schiotz/comp/kmail2thunder.html]("http://dcwww.fys.dtu.dk/~schiotz/comp/kmail2thunder.html") did eventually work after I commented out the lines that made it always give the help text because it thought it had the wrong number of arguments. The perl script that comes up first on a search for "kmail to thunderbird" doesn't work -- I think it must be very old and only handles Mbox format so even after editing the paths it only copied the very old folders.

---

### Post by swissinvestor on 2011-11-07
Admittedly,in the meantime I agree with you. It's Alpha after discovering that even BCC does not work and is displayed to all receivers. Wonderful for all those people who still don't know.  Unfortunately, Thunderbird is not an alternative for me as I need the PIM functionality (I am coming from Thunderbird to Kontact through Evolution). I gave up on Evolution and am not that far away from giving up on Kontact either. It is surely ridiculous to release Kdepim in such a dire state. 

However, at least I managed - with a lot of pain - to transfer my data to Kmail2 and just hope that I did not loose data, but I would not bet on that. That I could so far not find a confirmed information where Kmail2 stores it's data so that I can make a decent backup is just one of the things that annoys me. I also have frequent freezes, but am waiting for the 4.7.3 update in the hope the worst bugs are then being ironed out. 



> **jtappin said:**
> To answer myself, the python script and recipe at: [http://dcwww.fys.dtu.dk/~schiotz/comp/kmail2thunder.html]("http://dcwww.fys.dtu.dk/~schiotz/comp/kmail2thunder.html") did eventually work after I commented out the lines that made it always give the help text because it thought it had the wrong number of arguments. The perl script that comes up first on a search for "kmail to thunderbird" doesn't work -- I think it must be very old and only handles Mbox format so even after editing the paths it only copied the very old folders.

---

