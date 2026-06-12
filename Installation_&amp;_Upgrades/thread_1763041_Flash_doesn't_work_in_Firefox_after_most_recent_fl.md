---
title: "Flash doesn't work in Firefox after most recent flash plugin update (10.10)"
date: 2011-05-19
forum: Installation &amp; Upgrades
---

### Post by astropunkin on 2011-05-19
Flash is no longer working in Mozilla Firefox after the most recent flash plugin update.  I don't know if anyone else has had this problem.  I couldn't find any information on it.  Can anyone point me to the previous release maybe?  Any help would be appreciated!

---

### Post by lovinglinux on 2011-05-20
Get the latest version of [Flash-Aid]("http://www.webgapps.org/addons/flash-aid") and run it. It will detect installed flash plugins, remove them and install the best option according to your system architecture and version. Additionally, it will apply some tweaks that should improve performance.

---

### Post by astropunkin on 2011-05-21
I tried that and I still get errors on websites saying I don't have the correct flash plugin installed.

---

### Post by Frogs Hair on 2011-05-21
I have seen this error as a result of my NoScript settings , which were blocking elements I needed view the contents of the site.

Post the links so we can test them .

---

### Post by astropunkin on 2011-05-21
[http://gawkernet.com/rapture/rapturelive.html](http://gawkernet.com/rapture/rapturelive.html)  This is one site i can't view.

I also cannot watch any videos on the BBC new website or on my facebook page.  

Thanks!

---

### Post by astropunkin on 2011-05-21
I never added a NoScript add-on to Firefox.  Does it come standard now or something?

---

### Post by lovinglinux on 2011-05-21
> **astropunkin said:**
> I tried that and I still get errors on websites saying I don't have the correct flash plugin installed.

Which version of Flash-Aid are you using?

Go to the extension Help section, generate a report and attach it here.

---

### Post by astropunkin on 2011-05-21
The one in the link you sent me. So I guess the most recent one.  I tried it a few days ago too with whatever version that was.

---

### Post by lovinglinux on 2011-05-21
> **astropunkin said:**
> The one in the link you sent me. So I guess the most recent one.  I tried it a few days ago too with whatever version that was.

Then click the menu, select the Help sub-menu, click Generate Report and attach the generated file so I can check your system information.

---

### Post by astropunkin on 2011-05-21
I'm not sure what Menu you are referring to ..... :(

---

### Post by lovinglinux on 2011-05-21
> **astropunkin said:**
> I'm not sure what Menu you are referring to ..... :(

The Flash-Aid menu in your Navigation Toolbar.

---

### Post by astropunkin on 2011-05-21
Not sure if you can see this but the only way I could see the reports is by submitting a bug [https://bugs.launchpad.net/ubuntu/+source/firefox/+bug/786226](https://bugs.launchpad.net/ubuntu/+source/firefox/+bug/786226)

---

### Post by astropunkin on 2011-05-21
Oh ok here you go.  Sorry.

---

### Post by lovinglinux on 2011-05-21
> **astropunkin said:**
> Oh ok here you go.  Sorry.

You are using the 32bit flash from the repositories with the 64bit wrapper. Use Flash-Aid to install the 64bit beta plugin from Adobe.

Click the same menu you used to generate the report, select "Wizard Mode", select "Adobe Beta, from Adobe Labs" in the installation option step, then click "Next" until the extension asks if you want to "Execute" the script. Click "Finish". The script will be launched in a terminal and will remove the current flash version and install the 64bit beta.

Restart Firefox. Generate a new report and attach here. Test it to see if it works fine.

---

### Post by astropunkin on 2011-05-21
There doesn't seem to be a next button after I check the Expert Mode box and select the Adobe Beta, from Adobe Labs under Installation Options.  I do not have a Wizard Mode, only Expert.

---

### Post by astropunkin on 2011-05-21
Ok I think I got it.  I hit the Execute button on the first tab.

---

### Post by astropunkin on 2011-05-21
And now it works!!  Thank you so much for your help :)

---

### Post by lovinglinux on 2011-05-21
> **astropunkin said:**
> There doesn't seem to be a next button after I check the Expert Mode box and select the Adobe Beta, from Adobe Labs under Installation Options.  I do not have a Wizard Mode, only Expert.

That's because you are using the old version of Flash-Aid. Get the latest (2.1.1) from [https://addons.mozilla.org/en-US/firefox/addon/flash-aid/versions/](https://addons.mozilla.org/en-US/firefox/addon/flash-aid/versions/)

---

### Post by Frogs Hair on 2011-05-21
> **astropunkin said:**
> I never added a NoScript add-on to Firefox.  Does it come standard now or something?

No , you would had to have installed NoScript . The site works for me with 64 bit flash installed with the latest version of Flash Aid.

---

