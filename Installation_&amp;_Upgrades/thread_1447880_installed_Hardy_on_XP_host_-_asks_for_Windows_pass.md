---
title: "installed Hardy on XP host - asks for Windows passwd!!!!!"
date: 2010-04-05
forum: Installation &amp; Upgrades
---

### Post by smartsmokey on 2010-04-05
We installed 8.04 on a laptop running XP, and created the ubuntu users/passwords, am able to log in at start up, but when we click network setting it shows the Windows username on the host OS...WTF? Can't figure out what to do. Can log in fine in XP as a user, but not admin. I'm thinking ubuntu is asking me for the admin password for the XP. That's exactly what it's doing. Uh....anyone ever run into this?

---

### Post by smartsmokey on 2010-04-05
Installed ubuntu on machine already running XP. Kept the Windoze on it. Created ubuntu user/root and password, am able to start ubuntu and log in succesfully. However, when I try to click unlock on network connections/manager, it shows the Windows admin username and requires that password. Any ideas? Incan not enable wireless with this going on

---

### Post by themusicalduck on 2010-04-05
It's very unlikely that Ubuntu will be asking for the login details of your Windows install! Generally if you need to unlock something, you will need to give the password you gave when installing Ubuntu. Assuming you are logged in your username, you should use whatever password you set when you installed Ubuntu.

> Created ubuntu user/root and password you don't actually set a password for user root when installing Ubuntu, only for the user account. Unless you did something out of the ordinary to gain access to the root account which isn't a great idea.

My only other guess is that you're thinking of a WEP or WPA key or router access login? Those are the only things related to networking that may need a different password.

---

### Post by lisati on 2010-04-05
Duplicate threads merged.

---

### Post by oldefoxx on 2010-04-05
Not sure, since I haven't tried your setup.  I suspect that you are running Ubuntu as an application under Windows, and it is the Windows timeout and Screen Saver that is being activated, so naturally the Windows UserID and Password are involved.  I could be wrong, but it makes a kind of sense.

---

### Post by themusicalduck on 2010-04-05
Now I've seen the merged posts I'm pretty confused by your problem. Do you mean the password is being asked for in the host Windows or guest Ubuntu?

---

### Post by smartsmokey on 2010-04-05
Hey guys thanks for the responses. Yeah, I'm in Ubuntu, and when I do something like system>administration>network, I can't unlock it - for users it gives me the Windows XP username! Yeah.

Edit: I think the only solution is to reinstall by writing over Windows so it's standalone Ubuntu machine all the way. Then reinstall XP via virtualbox...argh!!!!

---

