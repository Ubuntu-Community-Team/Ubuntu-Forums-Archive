---
title: "Firefox flash plugin broke after upgrade to 10.04"
date: 2010-05-25
forum: Installation &amp; Upgrades
---

### Post by hreichgott on 2010-05-25
I had the Adobe flash plugin working under 09.10 in Firefox; now after the upgrade to 10.04, it doesn't work.

When I go to a web page with flash video, I get the message "Some plugins are not installed" and video will not display.  I click on the button to install the plugins and select Adobe Flash.  I get the message "Package is already installed."  I go back to the web page and the same thing happens again.

In Ubuntu Software Center I see that package restricted-extras is installed.

I tried going through Tools / Add-ons in Firefox, but the list of add-ons wouldn't load at all that way.

I also tried going to Adobe's web site, but for versions of Ubuntu 09 and later it offers an "APT" file instead of a .deb.  Firefox asks what application to use to open an "APT" file and I don't know what to tell it... I'd be fine downloading a .deb or using apt-get or Ubuntu Software Center though.

Thanks for any help you can provide.

Ubuntu Studio version 10.04 on a Lenovo Thinkpad T60
Firefox version 3.6.3 for Ubuntu

---

### Post by jerrrys on 2010-05-26
have you been here?

[ATTACH]158382[/ATTACH]

---

### Post by hreichgott on 2010-05-28
OK, I went there and it says "No proprietary drivers are in use on this system."
How does that help?

---

### Post by jerrrys on 2010-05-28
no help if theres no choices...

---

### Post by hreichgott on 2010-05-28
Fixed this one myself.
Just had to reinstall the flashplugin--even though Firefox showed it as installed already.

sudo apt-get install adobe-flashplugin

---

### Post by jerrrys on 2010-05-28
good show

---

