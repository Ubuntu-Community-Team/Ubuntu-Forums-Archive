---
title: "Flashplayer doesn't work after 14.04 upgrade"
date: 2014-04-27
forum: Installation &amp; Upgrades
---

### Post by Elderlygent on 2014-04-27
Hi! I listen to the BBC a lot but after upgrading to Trusty Tahr I get an iPlayer prompt asking me to install Flashplayer, which of course I've already got. What's going on? How can I get back on the Beeb?  
Thanks in advance to the kind person who can get me out of this Trusty mess.

---

### Post by fantab on 2014-04-27
Reinstall 'flashplugin-installer'

---

### Post by Elderlygent on 2014-04-27
I did, but it doesn't work. I tried following the BBC's own link to the Adobe site but that won't download either. Is there a way of associating the Flashplayer-installer with the iPlayer? Trouble is I can't remember what I did originally.

---

### Post by Awks_Panda on 2014-04-30
Try this for Mozilla Firefox (for some reason there are two different flash installers):

> 
#Install Adobe Flash Plugin for Mozilla Firefox:
sudo apt-get install adobe-flashplugin


If you are using Google Chromium:

> 
#Install tools to install Adobe Flash Plugin for Google Chrome Browser (Maintained by Google).
sudo apt-get install pepperflashplugin-nonfree

#Install the actual plugin into your Chrome Browser.
sudo update-pepperflashplugin-nonfree --install


You must restart your browser(s) after install.

More information on Pepper Flash can be found here: [https://wiki.debian.org/PepperFlashPlayer](https://wiki.debian.org/PepperFlashPlayer)

---

### Post by SeijiSensei on 2014-04-30
The adobe-flashplugin package is no longer available in 14.04.

Elderlygent, I can see two issues here.  One is that you live in Hungary, and iPlayer is not supposed to work outside of the UK.  There are solutions for this, but you're on your own since help with "circumvention" of such restrictions is not allowed on Ubuntu Forums.  As a hint, try Google.

Second, it could be that the iPlayer site doesn't recognize connections from Linux.  You can try spoofing your User-Agent string with a Firefox plugin like [UAControl]("https://addons.mozilla.org/en-us/firefox/addon/uacontrol/").  I use that to tell Netflix I'm using Windows.

Yet a third possibility is that iPlayer is looking for version 12 of Flash Player which is not, and will not, be available under Linux.  You can actually install some software that will let you run the Windows version of Flash Player.  Take a look at: [http://fds-team.de/cms/pipelight-installation.html](http://fds-team.de/cms/pipelight-installation.html).

---

### Post by monkeybrain20122 on 2014-04-30
> **SeijiSensei said:**
> The adobe-flashplugin package is no longer available in 14.04.

Elderlygent, I can see two issues here.  One is that you live in Hungary, and iPlayer is not supposed to work outside of the UK.  There are solutions for this, but you're on your own since help with "circumvention" of such restrictions is not allowed on Ubuntu Forums.  As a hint, try Google.

Second, it could be that the iPlayer site doesn't recognize connections from Linux.  You can try spoofing your User-Agent string with a Firefox plugin like [UAControl]("https://addons.mozilla.org/en-us/firefox/addon/uacontrol/").  I use that to tell Netflix I'm using Windows.

Yet a third possibility is that iPlayer is looking for version 12 of Flash Player which is not, and will not, be available under Linux.  You can actually install some software that will let you run the Windows version of Flash Player.  Take a look at: [http://fds-team.de/cms/pipelight-installation.html](http://fds-team.de/cms/pipelight-installation.html).

I just went to [http://www.bbc.co.uk/programmes/b041xykb](http://www.bbc.co.uk/programmes/b041xykb) and it played perfectly in Firefox with flash 11.2 (Ubuntu 14.04). There is no pipelight on this installation (so widdivine is not needed) I live outside the UK (Canada) and didn't do anything to circumvent geolocation restriction (though I know how to if needed. :)) It just worked. 
I think the website is correct.

---

### Post by monkeybrain20122 on 2014-04-30
@OP

Try to clear your Firefox cache and delete all the cookies. Also delete the hidden folder .adobe in your home (press ctrl + h to show hidden files) Then restart Firefox. Some settings may have been screwed up because of upgrade.

---

### Post by frank18 on 2014-04-30
> **Elderlygent said:**
> Hi! I listen to the BBC a lot but after upgrading to Trusty Tahr I get an iPlayer prompt asking me to install Flashplayer, which of course I've already got. What's going on? How can I get back on the Beeb?  
Thanks in advance to the kind person who can get me out of this Trusty mess.

Forget Firefox In Ubuntu 14.04 its flash player from the Ubuntu restricted-extras doesn't work right in some  video streams it lags,so do this in the Terminal and install Google Chrome which has it's own flash player and works great on all video streams



wget -q -O - [https://dl-ssl.google.com/linux/linux_signing_key.pub](https://dl-ssl.google.com/linux/linux_signing_key.pub) | sudo apt-key add -
sudo sh -c 'echo "deb [http://dl.google.com/linux/chrome/deb/](http://dl.google.com/linux/chrome/deb/) stable main" >> /etc/apt/sources.list.d/google.list'
sudo apt-get update
sudo apt-get install google-chrome-stable

---

### Post by monkeybrain20122 on 2014-04-30
> **frank18 said:**
> Forget Firefox In Ubuntu 14.04 its flash player from the Ubuntu restricted-extras doesn't work right in some  video streams it lags,so do this in the Terminal and install Google Chrome which has it's own flash player and works great on all video streams


I have no problem. Lagging may have to do with weak cpu. Chrome uses some kind of hardware acceleration whereas FF doesn't, in FF hwacc can be enabled and if it works it works really well (more efficient than Chrome's) but it appears to work only on Youtube.

---

### Post by SeijiSensei on 2014-04-30
> **monkeybrain20122 said:**
> I live outside the UK (Canada) and didn't do anything to circumvent geolocation restriction (though I know how to if needed. :))

According to [this article in last September's *Daily Mail*](http://www.dailymail.co.uk/news/article-2421514/BBC-available-millions-viewers-Europe-Australia-Canada-just-4-month.html), Canadians can use iPlayer for £52 a year.  Maybe they just haven't started charging yet?

---

### Post by monkeybrain20122 on 2014-04-30
> **SeijiSensei said:**
> According to [this article in last September's *Daily Mail*]("http://www.dailymail.co.uk/news/article-2421514/BBC-available-millions-viewers-Europe-Australia-Canada-just-4-month.html"), Canadians can use iPlayer for £52 a year.  Maybe they just haven't started charging yet?

Hmm.. I assure you that I have not paid a penny, either it is bbc incompetence or they stole £52 from me without my knowledge. :o

---

### Post by Elderlygent on 2014-08-02
Finally got around to your fixes, which solved my problem. Belated but very warm thanks, Awks!

---

### Post by Elderlygent on 2014-08-02
SOLVED: thanks to all who contributed.:p

---

