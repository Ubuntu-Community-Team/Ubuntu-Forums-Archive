---
title: "Enable Silveright for BT Sport on Firefox"
date: 2015-03-07
forum: Installation &amp; Upgrades
---

### Post by adam_dickens on 2015-03-07
hello,

i have installed PIpelight using the following cmd but it stillswants me to install SIlverlight. I have also tried looking for the installation in about:plugins and it's not there. I have searched the net and it looks as though it's not possible. Is it true?? Also what is Wine?:

sudo apt-add-repository ppa:pipelight/stable
sudo apt-get update
sudo apt-get install --install-recommends pipelight-multi
sudo pipelight-plugin --updatesudo pipelight-plugin --enable silverlight

---

### Post by Mark Phelps on 2015-03-07
You can't install Silverlight in Linux as it is Windows middleware and enforces DRM.  Pipelight is the closest you will be able to get.

Wine is a hack in which Windows OS kernel calls have been replaced by Linux OS kernel calls in a few Windows DLL files.  To the degree that Window apps use only these DLLs, the apps work well.  But more recent Windows apps use middleware like .Net and Silverlight -- which don't work well in Wine.

If you're in a situation where you have to depend on Windows apps, then you really need to use Windows.

---

### Post by yancek on 2015-03-07
Take a look at the site below, all the way to the bottom of the page where it discusses "User Agent Overrider" which may be necessary.

[http://www.webupd8.org/2013/08/pipelight-use-silverlight-in-your-linux.html](http://www.webupd8.org/2013/08/pipelight-use-silverlight-in-your-linux.html)

---

### Post by efflandt on 2015-03-08
I have used real Microsoft Silverlight in Linux before. The netflix-desktop package that I used in 12.04 used wine, gecko (mozilla) as IE supstitute, and installed Silverlight from Microsoft. But I had not used that in 14.04 because Google Chrome now works for Netflix (using HTML5), although, Netflix still says that Linux firefox is not supported.

We use an application for reporting floating holiday, vacation, or sick days called Dayforce that uses Silverlight for some strange reason. So I installed pipelight per [http://pipelight.net/cms/install/installation-ubuntu.html](http://pipelight.net/cms/install/installation-ubuntu.html) including **sudo pipelight-plugin --enable silverlight**, and even after rebooting it does not seem to be working. There is nothing in firefox's Plugins or about:plugins about silverlight. The pipelight silverlight test site [http://bubblemark.com/silverlight2.html](http://bubblemark.com/silverlight2.html) just shows an icon to Install Microsoft Silverlight which actually takes me to a site to install Moonlight. And if I log into the Dayforce website it still says "Silverlight not installed".

"pipelight-plugin --system-check" does say "Libraries: FAILURE" at the end of 32 and 64-bit library lists, but paths to esential libs it requires are listed and the system check does not say what it thinks might be missing.

So something is missing in the instructions. There are no errors launching it because it never launches when going to a site requiring Silverlight.

---

### Post by David D. on 2015-03-08
Some websites will show you an error that your operating system is not supported. To get around this problem, you will need to install an user agent switcher as described here in section 3 of the intructions you followed.

---

### Post by monkeybrain20122 on 2015-03-09
It works for me. If it doesn't work on the bubble test site then it has nothing to do with agent overrider. Maybe you will have better luck asking the developers. [https://launchpad.net/pipelight](https://launchpad.net/pipelight)

---

