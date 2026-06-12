---
title: "XOrg Update"
date: 2006-11-04
forum: Installation &amp; Upgrades
---

### Post by jgcamp99 on 2006-11-04
Hosed the default Ubuntu Edgy sudo user. Computer tries to boot into default userid and then crashes. kicking back out to the login screen. I'm glad I reenabled root, otherwise I'd be in deeper do do than this already is.

Anyway to uninstall those updates from root ?

---

### Post by pay on 2006-11-04
What video drivers are you using. I have had alot of problems with the ati video drivers after updating xorg. you need to reinstall them after the update (with the fglrx driver not the radeon driver.

---

### Post by jgcamp99 on 2006-11-04
> **pay said:**
> What video drivers are you using. I have had alot of problems with the ati video drivers after updating xorg. you need to reinstall them after the update (with the fglrx driver not the radeon driver.

I am using ATi's 8.29.6.

What's strange, is that I did the 2 updates this AM, I get the sudo password prompt, dl and install. Shut the computer down and run errands, play golf and then comeback. Turn the computer on and the sudo default user won't boot as the default auto login. The computer then goes back to the login screen, where the default user can't login manually. I am able to login as root though. I blew away the account and then shut down and restart. Recreate the account and it now logs in, but the refinements and settings of that profile are no longer in effect.

Oh well, I'll just recreate the profile and move on.

Thanks though for your response.

---

### Post by jgcamp99 on 2006-11-04
> **jgcamp99 said:**
> I am using ATi's 8.29.6.

What's strange, is that I did the 2 updates this AM, I get the sudo password prompt, dl and install. Shut the computer down and run errands, play golf and then comeback. Turn the computer on and the sudo default user won't boot as the default auto login. The computer then goes back to the login screen, where the default user can't login manually. I am able to login as root though. I blew away the account and then shut down and restart. Recreate the account and it now logs in, but the refinements and settings of that profile are no longer in effect.

Oh well, I'll just recreate the profile and move on.

Thanks though for your response.

Nope, still doing it to my newly created user/profile too. The desktop keeps locking up. I go into Firefox and then close it and a few minutes later retry Friefox, it tells me it's already open and I need to close it ? WTF ? I get gnome desktop lockups too.

But Root login appears to be fine ?

---

### Post by jgcamp99 on 2006-11-05
> **jgcamp99 said:**
> Nope, still doing it to my newly created user/profile too. The desktop keeps locking up. I go into Firefox and then close it and a few minutes later retry Friefox, it tells me it's already open and I need to close it ? WTF ? I get gnome desktop lockups too.

But Root login appears to be fine ?

The Firefox glitch, finally appeared to have figured that out, I tried my workaround and installed the Mozilla version of Firefox over the version that Ubunut provides so I could get the update capability enabled for FF.

I reinstalled the ATi drivers, that seems to have added some stability to the default user profile without any freezes or crashes. And just when I get done with that, ATi/AMD comes out with 8.30.3. In the last week, it's been 8.28.8, then to 8.29.6 and now 8.30.3.

---

### Post by jgcamp99 on 2006-11-05
Well, 8.30.3 has hosed things again. For the longest time I was stuck with getting kicked backed to the login screen. Since, I've been able to reload 8.29.6 and root will take to staying logged in on the 2nd attempt, the first attempt kicked me back tot he login screen.

Can't understand for th elife of me, why this is an issue in Edgy and not in Dapper ? ATi driver upgrades went so smoothely in Dapper, I do one for Edgy and the default user is unusable, root is even a 2nd attempt to login. 

Anyone else getting the weird behavior ?

I used to have the Ubuntu default sudo user login automatically, with this latest round of issues, that user locks up the computer before the desktop loads. The root account, starts to load then goes to black screen and eventually kicks back to the login screen with a brief delay. The 2nd attempt succeeds and here is where I am, a crippled Edgy install with no sudo user.

I'm happy that I reenabled root, this Edgy would suck worse than it does if I couldn't get anything to login period.

---

### Post by jgcamp99 on 2006-11-05
Solved !

This line of code was set to [COLOR="Black"]**"off"**[/COLOR] in my:

/etc/x11/xorg.conf

file.

The solution, before reloading the xserver with this command,

sudo /etc/init.d/gdm force-reload, edit the xorg.conf for opengloverlay to be set to "on" in this section.

Section "Device"
	Identifier  "aticonfig-Device[0]"
	Driver      "fglrx"
	Option	    "VideoOverlay" "on"
	Option	    "OpenGLOverlay" "**[COLOR="Red"]on[/COLOR]**"
EndSection

I was wondering if Edgy was a mistake to upgrade to as this went down again after the upgrade hosed dapper, I've since vaccilated back the "love" Edgy in the bi-polar, "love/hate Edgy" relationship. I'm learning new things every time that a minor issue crops up. For the most part there isn't much I'm changing here with either Dapper or Edgy, that's why the autoupdate feature has to work perfectly. This nonsense takes a day to figure out. The first thing I thought, were corruptions with files or even user profiles, not minor text entry changes.

---

