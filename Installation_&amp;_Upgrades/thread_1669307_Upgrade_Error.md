---
title: "Upgrade Error"
date: 2011-01-17
forum: Installation &amp; Upgrades
---

### Post by 1chess2u Christian on 2011-01-17
When distribution upgrade happened on Mon. Jan. 17, 2:29 PM, I tried to update, but a dialog box came up, saying "Error authenticating some packages

It was not possible to authenticate some packages. This may be a transient network problem. You may want to try again later. See below for a list of unauthenticated packages.
compiz
compiz-core..."
There were others, but I forgot them. please tell me what is wrong! :confused:

---

### Post by muut on 2011-01-20
I just got warning 'You are about to install software that can't be authenticated!...'

The three packages are dbus, dbus-x11, and libdbus. Version 1.2.16-2ubuntu4 will be upgraded to version 1.2.16-2ubuntu4.1.

As a new user, just learning Ubuntu, I hesitate to go it on my own by ignoring the ominous message that 'Doing this could allow a malicious individual to damage or take control of your system.' - something that is all to common with MS! - and why I want to change my OS to Ubuntu.

Hope I'm in the right thread. If not, maybe someone could move this post (or tell me where I should be posting this upgrade question).

---

### Post by oldos2er on 2011-01-20
Both of you might want to read [https://help.ubuntu.com/community/SecureApt](https://help.ubuntu.com/community/SecureApt)

Try running ```
sudo apt-key update
```

---

### Post by muut on 2011-01-21
Thank you for the response. I am reading now... but the first thing that caught my eye was the paragraph starting with 'Each time you add another apt repository...'
I did not add anything. I fact the machine had been off for about a week and when I started it up the update notification came up and I let the download/update run. After downloading and installing 10 of 13 updates I got the message about the dbus, dbus-x11, and libdbus-1-3.

I have to wonder what caused the change in the repository list?

In the section Validation of Release File and Packages 'Secure apt now verifies the Release file...' - What went wrong? and how do I find the GPG error? The Update Manager Summary does not give me that info...

Lastly, what is the SOP when getting this error? Should it be ignored and install the unauthenticated updates ( doesn't sound good)? or cancel and start trying to find repository changes, key changes, etc??

Now I'm even more confused... I canceled the update on the 3 packages and Update Manager gave me a notice that there were more updates... 13... I clicked Check and the number changed to 14... I clicked install and there were no error messages and I think I saw the dbus files go by... Ubuntu wanted a reboot so I did... now I'm at the desktop... ran Update Manager, did a Check and now it says the system is up-to-date... good! But now I have no idea why!

So was there some 'problem' with Ubuntu servers??

---

### Post by oldos2er on 2011-01-21
> **muut said:**
> So was there some 'problem' with Ubuntu servers??

 That's possible. Hard to say now though, since it seems to be fixed for you.

Whenever there are problems like that, running a command like ```
sudo apt-get update && sudo apt-get upgrade
``` will give you more info about the problem; for example it should name the repository having authentication problems.

---

