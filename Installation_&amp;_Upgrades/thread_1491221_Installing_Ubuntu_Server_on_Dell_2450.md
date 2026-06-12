---
title: "Installing Ubuntu Server on Dell 2450"
date: 2010-05-23
forum: Installation &amp; Upgrades
---

### Post by iamgeniusrnti on 2010-05-23
Hi again--

I've been using Ubuntu nearly exclusively for about 6 months and loving it.  Recently, I've been buying up old rack servers and installed Smoothwall and now I'm trying to install Ubuntu server on a Dell PowerEdge 2450.

If you run searches you'll find a lot of pissed off people who couldn't do it but I did run across this thread: [http://ubuntuforums.org/showthread.php?t=528408&highlight=dell+2450&page=2](http://ubuntuforums.org/showthread.php?t=528408&highlight=dell+2450&page=2)

This guy says he pulled it off using a MiniCD.  My only question is, if I go here [https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD) and make a CD, boot up and get to a prompt, how do I tell it to install the SERVER edition?  Or am I misreading something here?  It seems "CLI" would just install a desktop?

---

### Post by darkod on 2010-05-23
I am under the same impression. MinimalCD doesn't have a server version.

Despite all the problems reported, did you actually try to install the server version yourself?

---

### Post by iamgeniusrnti on 2010-05-23
> **darkod said:**
> I am under the same impression. MinimalCD doesn't have a server version.

Despite all the problems reported, did you actually try to install the server version yourself?

Yep.  And after several hours of building my confidence that my CD I used is perfect, I put the CD Rom in this dinosaur, it gets to about 17%, stalls and says the CD is corrupt.

I've already read that Ubuntu won't install to this machine unles I back down to 6.04.  But before I resort to spending weeks upgrading 6.04, i was thinking about a net install.

---

### Post by dino99 on 2010-05-23
[http://ubuntuforums.org/showthread.php?t=976014](http://ubuntuforums.org/showthread.php?t=976014)
[http://ubuntuforums.org/showthread.php?t=505990&page=2](http://ubuntuforums.org/showthread.php?t=505990&page=2)

---

### Post by iamgeniusrnti on 2010-05-23
> **dino99 said:**
> [http://ubuntuforums.org/showthread.php?t=976014](http://ubuntuforums.org/showthread.php?t=976014)
[http://ubuntuforums.org/showthread.php?t=505990&page=2](http://ubuntuforums.org/showthread.php?t=505990&page=2)

Thank you for those.  I don't recall seeing the 1st link but the second link may be the answer.  I desperately hope I don't have to upgrade firmware.  I don't feel like dinking around with floppies... this $20 server is turning into a lot more work than I originally was hoping for.

There is another server for sale $150, a 2650.......

---

### Post by iamgeniusrnti on 2010-05-25
> **dino99 said:**
> [http://ubuntuforums.org/showthread.php?t=976014](http://ubuntuforums.org/showthread.php?t=976014)
[http://ubuntuforums.org/showthread.php?t=505990&page=2](http://ubuntuforums.org/showthread.php?t=505990&page=2)

Installing the dinosaur Ubuntu server now.  Looks like it's going to take it.  Then I just need to google this "direct path" to 6.06 --> 8.04... wish me luck!  LOL!

---

### Post by iamgeniusrnti on 2010-05-25
> **iamgeniusrnti said:**
> Installing the dinosaur Ubuntu server now.  Looks like it's going to take it.  Then I just need to google this "direct path" to 6.06 --> 8.04... wish me luck!  LOL!

For reference I used this: [https://help.ubuntu.com/community/HardyUpgrades](https://help.ubuntu.com/community/HardyUpgrades)

And now it's upgrading 142 packages... yep that'll take a while.  Then I just need to get gnome up and running so I don't have to google terminal commands.  Wow... have I mentioned how much I love Ubuntu lately?  LOL!

---

### Post by darkod on 2010-05-25
> **iamgeniusrnti said:**
> Installing the dinosaur Ubuntu server now.  Looks like it's going to take it.  Then I just need to google this "direct path" to 6.06 --> 8.04... wish me luck!  LOL!

Don't count too much on upgrade. From what I have seen with the desktop version, if a newer version doesn't want to install, usually there is some reason for it. People who went ahead and upgraded, in most cases the system stopped working.

However, that doesn't mean you shouldn't try. After all, it will be brand new empty install so even if it breaks because of the upgrade, you'll just install the old version again. :)

---

### Post by iamgeniusrnti on 2010-05-25
Going from 6.06 to 8.04 LTS was a breeze.  Now trying 8.04 to 10.04 direct...

Wow... 343 packages?!?  Dear God!

---

### Post by iamgeniusrnti on 2010-05-25
> **darkod said:**
> Don't count too much on upgrade. From what I have seen with the desktop version, if a newer version doesn't want to install, usually there is some reason for it. People who went ahead and upgraded, in most cases the system stopped working.

However, that doesn't mean you shouldn't try. After all, it will be brand new empty install so even if it breaks because of the upgrade, you'll just install the old version again. :)

99% of the time, I'd agree with you if for no other reason than because I've only been dabbling with Linux for about 8 months and cannot hold a candle to any other user :)...  

But my research has led me to believe the reason this old thing wouldn't install was because of a minor glitch in the distributed image which most newer CD Roms can get past.  My computer hung at 17% because it couldn't read one package.  This was consistent with other results from other people.  

I will know very shortly if I cannot run 10.04 on an old Dell 2450......

---

### Post by darkod on 2010-05-25
> **iamgeniusrnti said:**
> 99% of the time, i'd agree with you if for no other reason than because i've only been dabbling with linux for about 8 months and cannot hold a candle to any other user :)...  

But my research has led me to believe the reason this old thing wouldn't install was because of a minor glitch in the distributed image which most newer cd roms can get past.  My computer hung at 17% because it couldn't read one package.  This was consistent with other results from other people.  

I will know very shortly if i cannot run 10.04 on an old dell 2450......

=d>

---

### Post by iamgeniusrnti on 2010-05-25
> **darkod said:**
> =d>

WOOT!  Do I need to say more??  LOL!

Now I gotta research putting up Gnome desktop so I don't have to do terminal all day

---

### Post by CharlesA on 2010-05-25
```
sudo apt-get install gnome-core
```

---

### Post by iamgeniusrnti on 2010-05-25
> **CharlesA said:**
> ```
sudo apt-get install gnome-core
```

WOW Thanks!  I hadn't even begun searching yet!  Now that's quick LOL!!!  355 packages... this server is having a busy day today after rotting in a garage for countless years!!

---

### Post by iamgeniusrnti on 2010-05-25
It almost worked!  The graphics came up but both the login and the desktop are hard to see, there is a bunch of lines running up and down vertically and the screen is blurry.

This has to be an easy fix right?  LOL!

---

### Post by iamgeniusrnti on 2010-05-25
After some more googling I discovered I needed to edit /etc/X11/xorg.conf which led me to a new problem...

Xorg.conf doesn't exist in 10.04.

So Google told me to xrandr which was silly as it returned a can't open monitor error... a complete waste of time and I will never do this again.

Then I tried [http://hydtech.wordpress.com/2009/02/26/gnome-display-manager-problems-error-setting-mtrr-in-ubuntu-intrepid-810/](http://hydtech.wordpress.com/2009/02/26/gnome-display-manager-problems-error-setting-mtrr-in-ubuntu-intrepid-810/)

This looked like it was doing some really good stuff but it too was a complete waste of time.

Then Google told me to run xorg -configure.  This generated me a .conf file which I promptly placed in the X11 dir.  Then I edited one line under the monitor subsection below depth 24; modes = "800x600" and badda bing, badda boom, my server is finally ALIVE!!!

Therefore; I do solemnly swear by the grace of the Ubuntu Gods that yes Ubuntu Server 10.04 LTS, fully updated WILL run on a Dell PowerEdge 2450, Gnome and all!  

Just don't try to install directly from a CD because this machine will poop on itself.

---

