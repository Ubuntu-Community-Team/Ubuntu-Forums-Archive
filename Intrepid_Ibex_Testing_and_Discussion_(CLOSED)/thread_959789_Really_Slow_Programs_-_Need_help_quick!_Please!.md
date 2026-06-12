---
title: "Really Slow Programs - Need help quick! Please!"
date: 2008-10-26
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by mlissner on 2008-10-26
Hi all - I upgraded to Ibex yesterday, and since then, Firefox and Evolution have been having serious speed issues. As I use them, seemingly randomly, they gray-out for a moment, processing stops, and then in about 30 seconds, they bounce back. 

I've tried looking at the logs, and reverting to my old kernel, but so far nothing has helped. I also tried running firefox from within a terminal, and uninstalling all my unnecessary add-ons (I have about ten left). 

Are there any other ideas as to what I can do to fix it? I have a midterm tomorrow, and a speedy computer is quite necessary...

---

### Post by tuxxy on 2008-10-26
thats strange Ibex runs super quick here, did you upgrade or fresh install?

---

### Post by mlissner on 2008-10-26
Upgrade. 

And it's only certain programs...or to be more precise, it's only certain parts of certain programs. Like Konqueror is fine, and the only part of Evolution that freezes/thaws is the new email window...

---

### Post by jdbaok on 2008-10-26
I, too am having the grey out problem. Mine is with Firefox on 7.10 (I think that's gutsy). It started after I did an normal software upgrade after being advised to by the computer. FF ran fine before this. I am also having an issue with my wireless connection just dropping for no reason.
To me it looks sort of like a virus.
jb

---

### Post by luziva on 2008-10-26
Same for me, my Laptop is completely unusable since the last upgrade. 10 minutes just to load Konqueror and then it still won't accept any input. Other programs are also not working.

---

### Post by dustint83 on 2008-10-26
im getting the gray hangs on emerald everytime i click any check boxes or change the theme

after about 2 minutes it comes back and is useable again, fresh install of the latet beta

---

### Post by forger on 2008-10-26
Create a new user from System > Administration > Users and Groups ("Unlock" and "Add user")

Then log out and log in with that user. Does everything work properly in that user?
If so, your problem is configuration files, which means you might have to reset your mozilla profile in order to use it properly
[COLOR="Red"]Warning:[/COLOR] If you reset (remove) your .mozilla folder, you **[COLOR="Red"]will lose[/COLOR]** passwords, bookmarks and personal information in mozilla firefox, unless of course you backup properly).

---

### Post by mlissner on 2008-10-27
Hmmm...well, I used the new fast user switching tool to switch the guest user, and I noticed no lags while logged in there. I also created a new Firefox profile for the problem user (firefox -ProfileManager), and that seems (for the moment) to be working without the freeze ups.

I don't particularly mind tossing a profile away, though it seems like a hatchet when a scalpel is needed. 

I'm trying to figure out how Firefox and Evolution are related, because those are the only programs (so far) that seem to have this problem. I guess they both run on GTK, but I can't think of much else.

---

### Post by mlissner on 2008-10-27
Something else that's really slow is sudo and gksudo. I'm baffled as to why, but gksudo doesn't seem capable of working at this point, and sudo takes about 45 seconds before prompting for a password.

Very strange.

---

### Post by forger on 2008-10-27
> **mlissner said:**
> 
I don't particularly mind tossing a profile away, though it seems like a hatchet when a scalpel is needed.
You asked for "help quick!" :D

You can backup and revert your profiles:
- Bookmarks: menu Bookmarks > Organize bookmarks > Import and Backup > Backup (and then use restore to revert).
- Passwords: [https://addons.mozilla.org/en-US/firefox/addon/2848](https://addons.mozilla.org/en-US/firefox/addon/2848)
Edit > Preferences > Security > Import/Export passwords.
- Add-ons are easily reinstallable, if you have more than one, well.. make a list or find an addon that backs them up. :)
and... that's it, I hope this is an explainable scalpel for you :)

If you think by using a new profile fixes it, it could save you some time not reinstalling add-ons, but it would be wise to reinstall everything, a lot of add-ons can sometimes "be cranky" after an upgrade.

Note that a lot of applications have leftovers, **a lot** of unnecessary leftovers after upgrades. Check out your home account:
```
ls -1da $HOME/.*
```

> **mlissner said:**
> Something else that's really slow is sudo and gksudo. I'm baffled as to why, but gksudo doesn't seem capable of working at this point, and sudo takes about 45 seconds before prompting for a password.

Root/sudo/gksu/gksudo/su have their configuration files too, they're located in /root/ :)
```
sudo ls -la /root/
```

What I would for this is to delete its configuration files as they are _re-created and set to default_ on reboot or on next use of a superuser command.
Here are some safe to delete files ( [COLOR="Red"]not safe if you are really using the root account as a separate user[/COLOR]), first execute in terminal:
```
sudo -i
```
then:```

rm -rf /root/.nautilus /root/.pulse /root/.local /root/.pulse-cookie
rm -rf /root/.config /root/.synaptic /root/.gnome /root/.gnome2
rm -rf /root/.gnome2_private /root/.cache /root/.gconf /root/.gconfd

```
This would clear out most ugly leftovers from previous releases!

And you exit:
```
exit
```
and disable the current sudo authentication
```
sudo -k
```

Now log out and log back in, your superuser commands should be able to "breathe" better :)

---

### Post by mlissner on 2008-10-27
> You asked for "help quick!" :grin:

You're right indeed. This looks like excellent advice, and I'll check these out later today.

---

### Post by jdbaok on 2008-10-27
Note that a lot of applications have leftovers, **a lot** of unnecessary leftovers after upgrades. Check out your home account:
```
ls -1da $HOME/.*
```


OK I found lots of files after running the command above. Which ones should be deleted?:confused:

---

### Post by mlissner on 2008-10-28
> **forger said:**
> 
You can backup and revert your profiles:
- Bookmarks: menu Bookmarks > Organize bookmarks > Import and Backup > Backup (and then use restore to revert).
- Passwords: [https://addons.mozilla.org/en-US/firefox/addon/2848](https://addons.mozilla.org/en-US/firefox/addon/2848)
Edit > Preferences > Security > Import/Export passwords.
- Add-ons are easily reinstallable, if you have more than one, well.. make a list or find an addon that backs them up. :)
and... that's it, I hope this is an explainable scalpel for you :)

OK, I can do that no problem. I'll still lose a lot of information in the form of the Awesome Bar, Cache and cookies, but I think I can live with that. I'm doing it as a new profile, so there's no real loss, I can get back the old profile if I need it.


> **forger said:**
> 
Check out your home account:
```
ls -1da $HOME/.*
```
Not too much in mine...nothing too ugly anyway.

> **forger said:**
> 
Root/sudo/gksu/gksudo/su have their configuration files too, they're located in /root/
I didn't see any sudo/gksu or su config files in /root. 

> **forger said:**
> 
Here are some safe to delete files ( [COLOR=Red]not safe if you are really using the root account as a separate user[/COLOR]), first execute in terminal:
```
sudo -i
```then:```

rm -rf /root/.nautilus /root/.pulse /root/.local /root/.pulse-cookie
rm -rf /root/.config /root/.synaptic /root/.gnome /root/.gnome2
rm -rf /root/.gnome2_private /root/.cache /root/.gconf /root/.gconfd

```
I didn't have any of those files.

So, I made a new Firefox profile, but I still have issues with Evolution being funky. Any advice for that?

---

### Post by mlissner on 2008-10-29
OK, I've now been living with this for almost a week, and I can't seem to find any errors that are causing it. Firefox is just as bad as ever, Evolution is still graying out constantly, and I'm beginning to lose it. 

Any thoughts on how to track this down would be handsomely rewarded with showers of appreciation.

EDIT: I'll also add that I've tried going back to the hardy kernel, and the problem is there too.

---

