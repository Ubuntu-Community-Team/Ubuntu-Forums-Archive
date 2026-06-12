---
title: "Problem with Installing Firefox 4"
date: 2011-03-22
forum: Installation &amp; Upgrades
---

### Post by powerusers on 2011-03-22
I am using Ubuntu 10.10, I have already installed Firefox version 3.6.15. I want to update it to latest version but I am not able to upgrade it.
There is no option in Firefox's Help menu to Update Firefox, and also no option in Preferences > Advanced > Update > Firefox.
I tried to download and install Firefox package from shell but it failed also.
Please help me to update it.

Thanks.

---

### Post by linuxsyst on 2011-03-22
```
sudo apt-get upgrade
```
and wait you will upgrade packages.

---

### Post by sikander3786 on 2011-03-22
You'll need to add the Firefox PPA for installation of Beta 4. But that will update your current stable Firefox 3.x to testing release also. Be careful, beta and alpha releases are not that much stable.

[http://ubuntu4beginners.blogspot.com/2011/01/how-to-install-firefox-4-beta-on-ubuntu.html](http://ubuntu4beginners.blogspot.com/2011/01/how-to-install-firefox-4-beta-on-ubuntu.html)

---

### Post by Kilron on 2011-03-22
> **sikander3786 said:**
> You'll need to add the Firefox PPA for installation of Beta 4. But that will update your current stable Firefox 3.x to testing release also. Be careful, beta and alpha releases are not that much stable.

[http://ubuntu4beginners.blogspot.com/2011/01/how-to-install-firefox-4-beta-on-ubuntu.html](http://ubuntu4beginners.blogspot.com/2011/01/how-to-install-firefox-4-beta-on-ubuntu.html)

He's referring to FF4 Final, not the beta.  Final was supposed to be released as an update today.  However, I haven't seen anything telling me to update either.

---

### Post by Smallwheels on 2011-03-22
> **Kilron said:**
> He's referring to FF4 Final, not the beta.  Final was supposed to be released as an update today.  However, I haven't seen anything telling me to update either.

This is my situation too. I downloaded it and it is a read only file. I tried clicking on it and nothing really happens. I tried clicking extract files and it just opened a new window with all of the locations of other files. 

Once it is in my downloads folder what needs to be done with it to make it open and get installed?

All of my browsers were slug slow when I downloaded Ubuntu 10.04. After some time I updated Opera and it began to work quickly. I downloaded Chrome and it worked fast too. I tried updating Firefox but it was already the current version. It did speed up to being tortoise slow. I thought if I could install the latest version it would recreate the proper pathways or whatever and become as fast as the others did when they were upgraded. 

Opera and Chrome are as fast as the browsers on my Mac Book (I'm using a HP with a 2.3 AMD Sempron with 2 GB RAM). Firefox 3.6.whatever is like using a dial-up modem with a 26 kbps speed. 

Having Firefox as a slow browser is one of the last things preventing me from using Ubuntu 10.04 as my main OS. Help.

---

### Post by Kilron on 2011-03-22
I figured it out, you have to add the firefox-stable-ppa repository first:

```
sudo add-apt-repository ppa:mozillateam/firefox-stable
sudo apt-get update
```Then it should show there are updates available in update manager.

Edited to add:  If you want FF4 to look more like FF3, follow the tips at:

[http://redherring2.wordpress.com/2011/01/17/firefox-4-restoring-firefox-3-ui/](http://redherring2.wordpress.com/2011/01/17/firefox-4-restoring-firefox-3-ui/)

---

### Post by Smallwheels on 2011-03-23
Thank you Kilron. I applied your code and the latest Firefox is working beautifully. This new installation has fixed the slowness problem with Firefox that was unique to my computer. 

I haven't visited many sites yet. One site was very magnified. I don't know why. I used the ctrl + - to shrink the page to its normal size. 

Yahoo.com seemed to appear normally. 

Thanks again. 

Smallwheels

---

