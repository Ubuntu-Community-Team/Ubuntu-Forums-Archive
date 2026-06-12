---
title: "distro upgrade probem 12.04lts to 12.10: glibc lockfile create free, and memory"
date: 2013-12-11
forum: Installation &amp; Upgrades
---

### Post by kinetonat on 2013-12-11
I have been running 12.04lts on a compaq dc7600 for a couple of years. It seems over the past few months to have begun to hang. I'm using both Chrome and Firefox, and FF often just fades to a shadow, and hangs. Sometimes it will work ok for a few hours and then this starts, and when it does it fades back into use for a few seconds...enough to get it to respond and I can finish what i was doing. I tend to force-quit the app and restart, usually a few times and then get a for more hours before the problem comes back.

So, I decided to go for the upgrade of the distribution to 12.10.

I left it several hours to prepare the upgrade, set new software channels, get new packages and now it has stopped at 'installed python-libtorrent, with the following error [pictured]:

glibc detected   lockfile-create: free(): invalid next size (fast)
And,   glibc detected lockfile-create: malloc() memory corruption (fast)


I have looked at some other bugs reported but have not seen how to deal with it eg that the host name might be too long...there was no solution however, and at this stage in the upgrade I do not want to abort it...i don't know how to safely anyway, when there may have been changes made that will be unfinished. I am posting this from the same machine which is still fully working as before - EXCEPT shockwave is not working so no videos are playing or shown from the start. Hopefully someone can come along and help rescue this, at least back to how it was in 12.04.

It was bust and i'm trying to fix it! :popcorn:

I've loads of applications and settings I wish to keep. I do not want a fresh installation here. I am keeping the window open with the distribution upgrade below

---

### Post by Bucky Ball on 2013-12-11
You would have been much better to fix the problems in 12.04 than to bother upgrading, one reason being that 12.10 is only supported for another six months, 12.04 for another three and a half years. 12.04 can be upgraded directly to 14.04 (and so can 12.10, of course). There is no guarantee the problem will be fixed with an upgrade, especially if there was a problem when you started the upgrade. That will probably just carry on through.

You may have gone done a path of no return here and left yourself few options. If the machine is still booting as normal, open a terminal and:
```

sudo apt-get update
sudo apt-get upgrade
```

That WON'T upgrade to 12.10. Post the exact error message back here.

Just out of curiousity: You had been doing regular updates in 12.04?

(PS: You haven't got any other package managers open while attempting this?)

---

### Post by kinetonat on 2013-12-11
Hey thanks...stupidly perhaps I didn't look further into my earlier problem and solution I managed at the time, which has made this upgrade ATTEMPT difficult, but this might still happen come April also....

[http://ubuntuforums.org/showthread.php?t=2174787&highlight=cancel+upgrade+progress](http://ubuntuforums.org/showthread.php?t=2174787&highlight=cancel+upgrade+progress)


For now I'd just like safely to close the terminal and abort the upgrade. what is the best command for that in Terminal?

---

### Post by Bucky Ball on 2013-12-11
'sudo reboot now' and see what it boots to.

---

### Post by kinetonat on 2013-12-11
Terminal will accept the input but there is no response to any sudo commands. The message if I use the keyboard and Ctrl+C is 
'Ctrl-C pressed

This will end the operation and may leave the system in a broken state.  Are you sure that you want to do that?'    it might be the only option however.

---

### Post by Bucky Ball on 2013-12-11
Yep, take that option. Or try 'sudo shutdown' but that probably won't work either.

If you can get out and you get back in to a menu, choose the recovery kernel. At the list of options, choose to fix broken packages, give that a try.

---

### Post by kinetonat on 2013-12-11
Thank you for the support Bucky Ball. I have now upgraded it appears to 12.10

After Ctrl+C I had to switch the PC off (shutdown), and on restarting used recovery mode to check everything first incl. fixing packages. At the end of the fix packages script there was the samthe e problem as this thread. I restarted again in safe mode and again normally and everything appears ok so far, with the upgrade, but I suspect I have to use the fix from the other thread I tried before to continue regular updates to the system - which i had been doing,  and wait until April.

I still have the problem (perhaps it is to do with the NVidia card..the .) of the browsers (I've tried many bu FF is the worst) - ghosting and hanging. I don't know how to report the problem really beyond my introduction.

---

### Post by Bucky Ball on 2013-12-11
Have you run:

sudo apt-get update 
sudo apt-get upgrade

???

As for the graphics problem, yes, that is the stuff of another thread, probably in ***Multimedia & Video***.

---

### Post by kinetonat on 2013-12-11
Yes done that. The only problems seem to be the last part here:

Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) quantal-updates/main Translation-en           
Ign [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/main Translation-en_GB         
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) quantal-updates/multiverse Translation-en     
Ign [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/multiverse Translation-en_GB   
Ign [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/restricted Translation-en_GB   
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) quantal-updates/restricted Translation-en
Ign [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/universe Translation-en_GB
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) quantal-updates/universe Translation-en
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) quantal-updates/main Translation-en_GB
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) quantal-updates/multiverse Translation-en_GB
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) quantal-updates/restricted Translation-en_GB
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) quantal-updates/universe Translation-en_GB
Fetched 1,224 kB in 3min 51s (5,280 B/s)
W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/quantal-security/Release.gpg](http://security.ubuntu.com/ubuntu/dists/quantal-security/Release.gpg)  Something wicked happened resolving 'security.ubuntu.com:http' (-5 - No address associated with hostname)

E: Some index files failed to download. They have been ignored, or old ones used instead.

And from sudo apt-get update: 

only concerns..
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) quantal/main Translation-en_GB                    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/universe i386 Packages         
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) quantal/multiverse Translation-en_GB          
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) quantal/main Translation-en                       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/multiverse i386 Packages       
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) quantal/multiverse Translation-en    
Ign [http://archive.canonical.com](http://archive.canonical.com) quantal/partner Translation-en_GB    
Ign [http://archive.canonical.com](http://archive.canonical.com) quantal/partner Translation-en                
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) quantal/restricted Translation-en_GB          
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) quantal/restricted Translation-en            
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) quantal/universe Translation-en_GB
Hit [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/main Translation-en
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) quantal/universe Translation-en
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) quantal-updates/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/multiverse Translation-en
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) quantal-updates/restricted Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) quantal-updates/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/restricted Translation-en
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) quantal-updates/multiverse Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) quantal-updates/main i386 Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/universe Translation-en
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) quantal-updates/restricted i386 Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) quantal-updates/universe i386 Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) quantal-updates/multiverse i386 Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) quantal-updates/main Translation-en
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) quantal-updates/multiverse Translation-en
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) quantal-updates/restricted Translation-en
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) quantal-updates/universe Translation-en
Ign [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/main Translation-en_GB
Ign [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/multiverse Translation-en_GB
Ign [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/restricted Translation-en_GB
Ign [http://security.ubuntu.com](http://security.ubuntu.com) quantal-security/universe Translation-en_GB
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) quantal-updates/main Translation-en_GB
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) quantal-updates/multiverse Translation-en_GB
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) quantal-updates/restricted Translation-en_GB
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) quantal-updates/universe Translation-en_GB
Fetched 50.5 kB in 2min 23s (350 B/s)
Reading package lists... Done

---

### Post by Bucky Ball on 2013-12-11
What command is the first part with the error from? The update part looks fine.

---

### Post by kinetonat on 2013-12-12
The first part is update; the second upgrade.

---

### Post by kinetonat on 2013-12-12
For anyone looking for a solution to the browser (Firefox) fading and going grey, hanging and requiring many force quits to try to restore it use. I have found the solution on the following thread very useful. It seems to have improved matter considerably:

[http://ubuntuforums.org/showthread.php?t=822923&highlight=browser+fades](http://ubuntuforums.org/showthread.php?t=822923&highlight=browser+fades)
[I]
'Another way to disable the fading is to run "gconf-editor" from the commandline, and then go to:
  apps/compiz/plugins/fade/screen0/options
and untick the "dim_unresponsive" box.

Of course this doesn't make the problem program *actually* responsive,  it just disables the graphical feedback that happens when the program  doesn't respond to compiz messages.[/I]

---

