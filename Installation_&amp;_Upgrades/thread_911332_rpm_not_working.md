---
title: "rpm not working"
date: 2008-09-05
forum: Installation &amp; Upgrades
---

### Post by briansykes on 2008-09-05
I'm trying to install java from the java download site i'm not using Adept because it fails and i have to format and reload my computer everytime i try to use it to instal java. I'm not doing it again, so i downloaded this rpm and now i am getting this trying to run it.

rpm: To install rpm packages on Debian systems, use alien. See README.Debian.
error: cannot open Packages index using db3 - No such file or directory (2)
error: cannot open Packages database in /var/lib/rpm

I dont know what this means but i kinda need java to work so if anyone can help that'd be great thank you.

---

### Post by ronnielsen1 on 2008-09-05
Go to Synaptic
Click on Settings > Repositories
Checkmark Universe repository
Install kubuntu-restricted-extras from synaptic.

Ubuntu uses deb files - not rpms. You can run rpm's but that's another story

---

### Post by ronnielsen1 on 2008-09-05
> rpm: To install rpm packages on Debian systems, use alien
Yes it's possible but it's a last resort.

> i'm not using Adept because it fails and i have to format and reload my computer everytime i try to use it to instal java.
Yeah I must have reinstalled 20 times in the beginning. It's not necessary. Use a live cd and ask for help. Adept is a good program - not sure what the problem is

---

### Post by briansykes on 2008-09-05
Well everytime i try to install java from adept it does the terminal emulator thing right and you have to click ok.  Well i cant get the cursor to highlight the ok on the terminal emulator i've tried every damn button on my keyboard it doesnt work.

EDIT:
And now everytime i try to install any program java tries to install through adept and i cant tell it to continue so it just sits there not doing anything.  If someone could please help me with this java needs to be installed on this and why does kubuntu not come with java already installed?

---

### Post by ronnielsen1 on 2008-09-06
Stay away from adept for a minute. I'm suspecting broken packages but you're not giving enough info. Did you try the following? Is Synaptic giving any errors?
>  	 		**Re: rpm not working**
 		Go to Synaptic
Click on Settings > Repositories
Checkmark Universe repository
[COLOR=Red]Install kubuntu-restricted-extras from synaptic.[/COLOR]


>  why does kubuntu not come with java already installed? 	
>   Several rumors have been circulating that claim an esoteric prescience concerning Sun’s intentions toward Java and the free software community. Like shoots of hope that spring from the coldest ground, open source proponents [were reported]("http://www.eweek.com/article2/0,1895,1955448,00.asp") floating the idea that Sun might finally, this time, yes really, make Java open-source.  
  More credibly, CNET [suggests]("http://news.com.com/2100-7344_3-6068852.html") that Sun will alter its licensing on its Java Runtime Environment so that Linux distributions can include it. Currently, a typical Linux user (unless he buys a packaged distribution that has gone through the trouble and expense of getting a JRE license, as Sun’s own Java Desktop System did) has to download and install a JRE himself, should he want Java for use in applets in his web browser or for other purposes. Clearly, it would much more convenient for users (and provide more certainty for developers) if Linux distributions could come with Java built in.  

[http://www.oreillynet.com/etel/blog/2006/05/might_red_hat_benefit_most_fro.html](http://www.oreillynet.com/etel/blog/2006/05/might_red_hat_benefit_most_fro.html)

---

### Post by oldos2er on 2008-09-06
> **briansykes said:**
> Well everytime i try to install java from adept it does the terminal emulator thing right and you have to click ok.  Well i cant get the cursor to highlight the ok on the terminal emulator i've tried every damn button on my keyboard it doesnt work.

EDIT:
And now everytime i try to install any program java tries to install through adept and i cant tell it to continue so it just sits there not doing anything.  If someone could please help me with this java needs to be installed on this and why does kubuntu not come with java already installed?

 Use the arrow and Tab keys to move around the ncurses terminal. Hit Enter for "ok".

---

