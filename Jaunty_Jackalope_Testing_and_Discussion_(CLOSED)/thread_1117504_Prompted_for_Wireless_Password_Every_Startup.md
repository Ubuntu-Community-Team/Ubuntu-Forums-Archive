---
title: "Prompted for Wireless Password Every Startup"
date: 2009-04-06
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by novafluxx on 2009-04-06
Every time I boot up, instead of connecting to my wifi network automatically, like it always has done, now it prompts me for the passkey.

Anyone else experiencing this? Anyone have a solution?

---

### Post by netJackDaw on 2009-04-06
It might be that you have changed your password recently. Have you? Ubuntu stores passwords for services associated with the login in a special keyring. If you change your login password the password for the login-keyring wont change automatically. To change the password for the login-keyring so that it matches you login password you should run: "Passwords and Encryption Keys" from Applications -> Accessories. Select: Edit -> Preferences -> Password Keyrings. Select login keyring and click: Change Unlock Password.

Hope this helps!

At least this worked for Intrepid....

---

### Post by novafluxx on 2009-04-06
Haven't changed my wifi password since I set it up! Maybe I'll try a router/modem soft reset just in case somethings wacky there.

Thanks!

---

### Post by Favux on 2009-04-06
Hi novafluxx,

I hope you don't have this old NM/Intrepid bug.  I can't tell from your description.  But if you can't get it working you could take a look at this work-around:

[http://ubuntuforums.org/showthread.php?t=1010650](http://ubuntuforums.org/showthread.php?t=1010650)

And see if it applies to you.

---

### Post by lcohen999 on 2009-04-06
get rid of your password from gnome keyring and you should be OK

---

### Post by novafluxx on 2009-04-07
Should I just delete the wireless network and re-set it up?

---

### Post by lithorus on 2009-04-07
I had the same problem, but it was fixed in the latest update to gnome-keyring. I might have re-entered the password in network-manager's profile for the wireless profile.

---

### Post by netJackDaw on 2009-04-07
What I meant earlier was: Have you changed your Linuxlogin password, not the wifi password. There is no point in removing and setting up the wireless network again. As I tried to say earlier I think the problem is mismatch in Linuxlogin password and login keyring password...

---

### Post by vanadium101 on 2009-04-07
the way i got round the key ring manager etc was to install wicd, which is now in the jaunty repository

---

### Post by olskar on 2009-04-07
> **lcohen999 said:**
> get rid of your password from gnome keyring and you should be OK

Yep, that worked for me in Intrepid

---

### Post by novafluxx on 2009-04-07
Never had a password in Gnome keyring fellas ;)

---

### Post by novafluxx on 2009-04-08
Anyone else have a solution? My keyring says:

None. Prompt for a key

---

### Post by Westmeath on 2009-04-09
I am also still having this problem on 2 installs that I did with Alpha 6.

Another laptop that I also put Alpha 6 on, & didn't update until Beta came out, doesn't have the problem.

---

### Post by novafluxx on 2009-04-10
When I get home for the weekend, I'll make sure I dist-upgrade and check it out.

---

### Post by jmmL on 2009-04-11
This is the best solution I've come across so far, taken from [http://ubuntuforums.org/showpost.php?p=6933958&postcount=5](http://ubuntuforums.org/showpost.php?p=6933958&postcount=5)

> Open a terminal and do this :
     ```

sudo -i
polkit-gnome-authorization 
```Scroll down to "network-manager-settings" / "system" / "Modify system connections"

Click on that last one and the right-hand side where it says "Explicit Authorisation", hit the "Grant" button, then choose your username. No need to add any constraints - just leave it on "none".

Now, right-click on network manager and choose "Edit Connections", then find the WIFI network you want to be the default. Edit it and put a tick in the "Available to all users" box.

---

### Post by novafluxx on 2009-04-13
I haven't had the issue for the past few days. I'm guessing an update corrected it.

Thank you for all the help!

---

