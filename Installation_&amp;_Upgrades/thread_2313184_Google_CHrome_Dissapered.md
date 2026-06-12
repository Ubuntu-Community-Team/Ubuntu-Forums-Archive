---
title: "Google CHrome Dissapered"
date: 2016-02-10
forum: Installation &amp; Upgrades
---

### Post by St_Vi on 2016-02-10
Was trying to watch Netflix with chrome.
For some reason tonight I was told to go to crome://componets and update widvieCMD.
couldn't find it in the components, CHROME page tells me to uninstall and re-install.

After Un-Installing it, I reboot, go to Synaptic and search for Google Chrome...

It's not there.

1) What Happened?
2)Where is CHROME
3) how can I watch Netflix

Thanks

---

### Post by ellisistfroh on 2016-02-10
Do u have 32-Bit or 64-Bit system Architecture?

---

### Post by Vladlenin5000 on 2016-02-10
Google Chrome isn't and never was in the Ubuntu repositories, Chromium is. The usual installation process for Google Chrome is to download the deb file. Installing the said deb file also adds an additional repository and that why it is updated automatically like any other installed software but when uninstalled, depending on the method, such software source is also removed thus preventing any further (re)installation through apt of which Synaptic, Ubuntu Software Centre and others are just frontends.

In a nutshell, you have a fundamental misunderstanding and/or confusion. If you need Google Chrome again then please just do what you did in the first place: Download and install the deb file from Google.

---

### Post by ellisistfroh on 2016-02-10
@Vladenin5000: Correct! see bugreport -> [https://bugs.launchpad.net/ubuntu-website-content/+bug/1516374](https://bugs.launchpad.net/ubuntu-website-content/+bug/1516374) 
[h=1]Title: Google Chrome is listed as available app on website[/h]Why am I asking for the Architecture? Think I read recently Google will stop support for 32-Bit Chrome. Just can't remember where and when.

---

### Post by Vladlenin5000 on 2016-02-10
Indeed: [http://www.omgubuntu.co.uk/2016/01/google-chrome-linux-32-bit-discontinued](http://www.omgubuntu.co.uk/2016/01/google-chrome-linux-32-bit-discontinued)
This however doesn't affect Chromium.

The issue in the OP is uninstalling and then being unable to reinstall.

---

### Post by deadflowr on 2016-02-10
Chrome adds repositories when installed.
Look at the Software and Updates program and see if those are still there.
They would be listed in the other software section.

---

### Post by nothingspecial on 2016-02-10
> **St_Vi said:**
> Was trying to watch Netflix with chrome.
For some reason tonight I was told to go to crome://componets and update widvieCMD.
couldn't find it in the components, CHROME page tells me to uninstall and re-install.

After Un-Installing it, I reboot, go to Synaptic and search for Google Chrome...

It's not there.

1) What Happened?
2)Where is CHROME
3) how can I watch Netflix

Thanks

Hi :)

Help others help you. The latest updated chrome plays netflix fine.

Who/What told you to go to  chrome://components ? And what errors did you get before this?

Who/What told you to reinstall Chrome ? And what errors did you get before this?

How did you install chrome in the first place and which one did you install (stable/beta) ?

In order to get the speediest help on these forums include as much detail as you can as what has led to the problem, what you have changed since/before the problem started, what you have tried and any error messages you have had.

---

### Post by St_Vi on 2016-02-11
Thank you everybody for the replies.
What got me confused was the fact that i could un-install chrome-stable from synatic. I was then surprised I couldn't find it to re-install it.
After a search of my HDD i found the original DEB package and re-installed it. now all is good.

How this all started was, in the afternoon i did a software update. Then at night when i tried to watch a Netflix show i got a page saying:

> Woops, something went wrong...
Missing component
We cannot find all the riquired components to play Netflix on this device. Please visit
chrome://components, locate the WidevinCdm component, and click the "check for update"
buton
Error code: M7702-1003


Anyway all is good now 
Thank you all

---

### Post by Vladlenin5000 on 2016-02-11
Make sure your system is fully updated whenever such weird messages pop up. With the Google repository, added when you installed the deb, Google Chrome will be updated like any other software.

---

