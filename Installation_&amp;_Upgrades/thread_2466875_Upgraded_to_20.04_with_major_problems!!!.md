---
title: "Upgraded to 20.04 with major problems!!!"
date: 2021-09-08
forum: Installation &amp; Upgrades
---

### Post by tspcs208 on 2021-09-08
i upgraded and now Chromium, Arduino IDE and Ubuntu Software will not open no errors or anything like that i click the programs i get the spinning wheel then the spinning wheel disappears and the programs never open i had to use sudo apt-get to reinstall firefox just to get back online i tried uninstalling and reinstalling Chromium throw the terminal i still have the same problem 

i am running Ubuntu natively not in a VM as my daily driver OS

---

### Post by ajgreeny on 2021-09-08
Upgraded from what to 20.04?

I think 20.04 was the first version not to have chromium as a .deb install from the repos; officially it is available as a snap only and even running ***sudo apt install chromium*** will give you the snap version, so perhaps that is why an upgrade from, for example, 18.04 to 20.04 has given you that difficulty.

Unfortunately I have no idea about the **Arduino IDE** or **Ubuntu Software** as I've never used either.

---

### Post by tspcs208 on 2021-09-08
i did some research looks like they broke the graphics driver ( people have said to turn off the accelerators and chromium will work but the computer will run slow )all so looks like there is no way to really revert back but the complaints are rolling in after every one came to work after the holiday and updated there computers ( the same thing i did ) i will just suffer with firefox for a bit and give the devs some time to fix it if not it looks like a complete format and reinstall is in my near future i should of known better to update right away that's my fault did not think nothing of it sense i don't use any programs that aren't in the repository i dont know this is very disappointing to me this computer ran so good for so long and then was broken by bad updates...

---

### Post by monkeybrain20122 on 2021-09-08
The thing is "upgrade" is always kind of problematic because from LTS to LTS you have go through a bunch of intermediate releases and changes here and there will break things and you also have old config files and customizations lying around that may mess with the new system. So I think it is not so much that 20.04 "breaks" anything but an inherit problem with "upgrade" especially if you have installed proprietary drivers or have done some unconventional tweaks. That's why my advice is always backup your data and do a fresh install, much faster and safer and you start with a clean slate instead of a bunch of old garbage lying around.

As said Chromium is now offered as a snap and if you install with apt it will just run a script that pulls in the snap. Among other things hardware acceleration doesn't work in chromium snap. To install the .deb version you need this[ ppa]("https://launchpad.net/~saiarcot895/+archive/ubuntu/chromium-beta").
BTW instead of "suffering firefox" it actually works a lot better than chromium and hardware acceleration also works on FF and better (vaapi)

---

### Post by tspcs208 on 2021-09-08
everything google works with chromium all of my book marks and everything syncs with my phone even passwords throw my google account and can automatically log me in to all of my sites  i can even use chrome add ons

firefox basically is just a browser not 100% compatible with some sites kind of crappy like Microsoft edge some people may like it but i consider it trash just my opinion of coarse i will try that ppa thank you

---

### Post by monkeybrain20122 on 2021-09-08
> **tspcs208 said:**
> 
firefox basically is just a browser not 100% compatible with some sites kind of crappy like Microsoft edge some people may like it but i consider it trash just my opinion of coarse i will try that ppa thank you

I don't know about Edge but if FF is not compatible with some sites it is because those crappy sites don't adhere to standard. If you use a lot of google services Chrome and possibly Chromium understandably have an edge because they are owned by the same company. But seriously if you use a lot of google stuffs you may as well use google-chrome. Chromium is neither here nor there and is a perpetual beta, just my opinion.

---

### Post by mikewhatever on 2021-09-08
> **tspcs208 said:**
> i did some research looks like they broke the graphics driver ( people have said to turn off the accelerators and chromium will work but the computer will run slow )all so looks like there is no way to really revert back but the complaints are rolling in after every one came to work after the holiday and updated there computers ( the same thing i did ) i will just suffer with firefox for a bit and give the devs some time to fix it if not it looks like a complete format and reinstall is in my near future i should of known better to update right away that's my fault did not think nothing of it sense i don't use any programs that aren't in the repository i dont know this is very disappointing to me this computer ran so good for so long and then was broken by bad updates...

Don't know who broke what and for whom. I've not seen any complaints, and all of my machines updated without problems.
Perhpas it was a bad update of Chromium, which kind of makes sense, as I don't use it.

---

### Post by tspcs208 on 2021-09-09
i like where your head is at... <br>i manged to install chrome without any problems useing this link https://linuxconfig.org/how-to-install-google-chrome-web-browser-on-ubuntu-20-04-focal-fossa<br><br>im still having problems i cant open the Ubuntu Software center but that is a integrated part of ubuntu so my guess is they will fix it eventuality and as far as my Arduino IDE ( the little program used to flash experimental boards ) ill probably just have to give up on that.

---

### Post by tspcs208 on 2021-09-09
i just found a bug :-) if i right click on Ubuntu Software and click show details it opens ?

i was all so able to get Arduino working as well by uninstalling it and then installing the none snap version looks like all of my problems where related to that snap ( what ever snap was ) i guess snap didn't work out

---

