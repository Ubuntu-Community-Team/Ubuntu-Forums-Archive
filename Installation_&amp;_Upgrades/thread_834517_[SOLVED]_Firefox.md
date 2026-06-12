---
title: "[SOLVED] Firefox"
date: 2008-06-19
forum: Installation &amp; Upgrades
---

### Post by Fertech on 2008-06-19
how can i upgrade my browser firefox, to the lastes version. i did download it but can't seen to install it. im using ubuntu 6.06

---

### Post by ENigma885 on 2008-06-19
u can open [COLOR="black"]**Synaptic Package Manager**[/COLOR] *(system >> administration)* and then click reload (up left)  to make sure that ur package manager has the latest available packages ..
by then search for Mozilla Firefox and install the latest version available.

One last thing...if there's an update for ur Mozilla it will be included in the system updates.

---

### Post by aysiu on 2008-06-19
> **Fertech said:**
> how can i upgrade my browser firefox, to the lastes version. i did download it but can't seen to install it. im using ubuntu 6.06
Try [this](http://www.psychocats.net/ubuntu/firefox#terminal). Since you're using 6.06, be sure to read the Notes section.

---

### Post by Ryklou on 2008-06-19
```
sudo apt-get install firefox
```

This should install the upgrade (i think)

---

### Post by aysiu on 2008-06-19
> **Ryklou said:**
> ```
sudo apt-get install firefox
```

This should install the upgrade (i think)
Only on Ubuntu 8.04. The OP is using 6.06.

---

### Post by Fertech on 2008-06-20
i did open Synaptic Package Manager (system >> administration) and then click reload (up left) to make sure that ur package manager has the latest available packages, but in the Synaptic Package Manager i only found version 1.5.0

---

### Post by Fertech on 2008-06-20
fertech@fertech-desktop:~$ sudo apt-get install firefox
Password:
Reading package lists... Done
Building dependency tree... Done
firefox is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
fertech@fertech-desktop:~$
problem is that i can't find the newest version 
how do i check what version i'm running

---

### Post by avtolle on 2008-06-20
As you are using 6.06, it will not be in Synaptic nor can you do the apt-get commands to get it as has been suggested. Please see Aysiu's first post (post #3 in this thread) and click on the link provided. You're going to have to do some work to install it on 6.06, and the link provides detailed instructions.

---

### Post by aysiu on 2008-06-20
See post #3.

---

### Post by Fertech on 2008-06-20
aysiu i follow the steps in your link for firefox from mozilla: > If you have a deathly fear of the terminal, you can follow these point-and-click instructions, but it's considerably more involved than either of the other two options, as you'll see below:


Visit the Mozilla Firefox website and click the appropriate download button. You'll be asked what to do with the file. Choose to open it with the Archive Manager.


Wait for it to download.


Once the Archive Manager opens, click the Extract button.


Find a good location to extract the archive to. In this case, I picked the desktop. You can pick whatever directory you want in your home directory, as long as you can find it later.


Then go to that location. If you selected the desktop, you can reach that by going to Places > Desktop. A new file browser window should appear.


In the new window that appears, right-click the firefox folder and select Cut.


While keeping the new window open, press Alt-F2. This will bring up a Run Application dialogue box. In that dialogue box, paste the command gksudo nautilus and then click Run.


Since you'll be launching a new file browser window with system-wide administrative privileges, you'll be prompted for your password. Enter it.


When the new window appears, go to the /opt directory. You can do this by pressing the Up arrow and then double-clicking on opt. You can also press Control-L and then type /opt. Once you're in the /opt directory, right-click on the empty space and select Paste. You can now close the old file browser window (the one showing your desktop).


In the remaining window (the one focused on /opt/firefox), go to File and select New Window.


Leave that window in the background (it should be focused on the /root/Desktop folder). Go back to /opt and double-click into the firefox folder. Inside, there should be a folder called plugins. Rename (F2) that folder to plugins.old.


In the other window, go to /usr/lib/firefox and find the plugins folder there. Right-click it and select Make Link. This will create a new file called Link to plugins.


Right-click Link to plugins and select Cut.


In the /opt/firefox window, right-click on some empty space and select Paste.


Then rename Link to plugins to just plain old plugins.


In the other window, go to /usr/bin and find the file called firefox. Rename is to firefox.ubuntu.


In the /opt/firefox window, right-click on the firefox file and select Make Link.


Find the new Link to firefox file, right-click it and select Cut.


In the other window, right-click on some empty space, select Paste, and then rename Link to firefox to just plain firefox.


In the /opt/firefox window, go up one directory (click on the Up button) and right-click the firefox folder and select Properties.


The properties window will appear, and you should use the Owner drop-down menu to select root.


Change the Group permissions to root as well, and Apply Permissions to Enclosed Files. Then click Close.


Launch Firefox with the Firefox icon, as you normally would. Accept the licensing agreement.


You should now have the Mozilla version of Firefox running.  and now i can't open my browser. if i close this browser im not going to be able to open it again. i need need asap!

---

### Post by aysiu on 2008-06-20
> **Fertech said:**
> aysiu i follow the steps in your link for firefox from mozilla:  and now i can't open my browser. if i close this browser im not going to be able to open it again. i need need asap!
That's odd. It worked for me (that's how I got the screenshots).

Well, we can't really troubleshoot the problem if you can't close your browser. So the first thing we should do is temporarily install another browser just so you can get help while trying to fix your Firefox problem. Go to System > Administration > Synaptic Package Manager, search for *epiphany* and mark for installation the *epiphany-browser* package and click *Apply*. Exit Synaptic, and press Alt-F2 and type ```
epiphany
``` It should launch a new non-Firefox web browser. Log into the forums and close Firefox.

Once you've done that, post back here, and we'll try to troubleshoot the Firefox problem.

---

### Post by Fertech on 2008-06-20
i Got it!

---

### Post by aysiu on 2008-06-20
> **Fertech said:**
> i Got it!
So you're on Epiphany now?

Okay. Can you close Firefox, paste these commands in [the terminal](http://www.psychocats.net/ubuntu/terminal) and then post the output of all the commands back here? ```
cat /etc/lsb-release
ls /opt/firefox/plugins -l
ls /usr/bin/firefox -l
firefox &
```

---

### Post by Fertech on 2008-06-20
yes im using Epiphany, but i try making a payment and the website tells me to upgrade my browser, even with Epiphany

ok i reverse every around and now i can open my browser, but im back where i started. i'm still running version 1.5. i try that firefox link from one of the reply post. i never try it from the command line. i was going to try it but then i seen a code something like this: cp -R ~/.mozilla ~/.mozilla.backup
sudo tar -jxvf firefox-3.0.tar.bz2 -C /opt
rm firefox-3.0.tar.bz2
sudo mv /opt/firefox/plugins /opt/firefox/plugins.backup
sudo ln -s /usr/lib/firefox/plugins /opt/firefox/plugins
sudo dpkg-divert --divert /usr/bin/firefox.ubuntu --rename /usr/bin/firefox
sudo ln -s /opt/firefox/firefox /usr/bin/firefox

and from what i know rm stand for remove and i don't want to remove my browser or anything, cause i might just del my browser and may not upgrade nothing browser. i can use another browser but i really like firefox.

---

### Post by Fertech on 2008-06-20
fertech@fertech-desktop:~$ cat /etc/lsb-release
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=6.06
DISTRIB_CODENAME=dapper
DISTRIB_DESCRIPTION="Ubuntu 6.06.2 LTS"
fertech@fertech-desktop:~$ ls /opt/firefox/plugins -l
lrwxrwxrwx 1 root root 24 2008-06-20 12:37 /opt/firefox/plugins -> /usr/lib/fire fox/plugins
fertech@fertech-desktop:~$ ls /usr/bin/firefox -l
lrwxrwxrwx 1 root root 22 2008-06-18 17:26 /usr/bin/firefox -> ../lib/firefox/f irefox
fertech@fertech-desktop:~$ firefox &
[1] 5618
fertech@fertech-desktop:~$

---

### Post by Fertech on 2008-06-21
now i have another problem with my browser. most of the time when i click on a link or enter my logon on a website. the browser will close. any clues.

---

### Post by Dale61 on 2008-06-23
When I upgraded to FF2 when I had 6.06, I went to:
[Install FF2 in Ubuntu 6.06]("http://www.debianadmin.com/install-firefox2-in-ubuntu-and-list-of-recomended-addons.html") 
and never had a problem with it.

---

### Post by Fertech on 2008-06-23
that link fail. this is the error i got. notice at the bottom it says:Permission denied, whats the code to give it permission

fertech@fertech-desktop:/opt/firefox/plugins$ wget -c [ftp://ftp.mozilla.org/pub/mozilla.org/firefox/releases/2.0/linux-i686/en-GB/firefox-2.0.tar.gz](ftp://ftp.mozilla.org/pub/mozilla.org/firefox/releases/2.0/linux-i686/en-GB/firefox-2.0.tar.gz)
--09:38:37--  [ftp://ftp.mozilla.org/pub/mozilla.org/firefox/releases/2.0/linux-i686/en-GB/firefox-2.0.tar.gz](ftp://ftp.mozilla.org/pub/mozilla.org/firefox/releases/2.0/linux-i686/en-GB/firefox-2.0.tar.gz)
           => `firefox-2.0.tar.gz'
Resolving ftp.mozilla.org... 63.245.208.138
Connecting to ftp.mozilla.org|63.245.208.138|:21... connected.
Logging in as anonymous ... Logged in!
==> SYST ... done.    ==> PWD ... done.
==> TYPE I ... done.  ==> CWD /pub/mozilla.org/firefox/releases/2.0/linux-i686/en-GB ... done.
==> PASV ... done.    ==> RETR firefox-2.0.tar.gz ... done.
firefox-2.0.tar.gz: Permission denied
fertech@fertech-desktop:/opt/firefox/plugins$

---

### Post by Dale61 on 2008-06-23
Did the link to the page fail, or did the install as per that page fail?  I've got the page open as I type this reply.

I was a total noob when I found that page, but I was able to get FF2 to work the first time after following those install instructions.

One thing I've found to make it easier is to copy the instructions, then paste them to a terminal.  That way, you won't make a typo which will cause a failure.

Anyway, I'm not as up-to-speed with Ubuntu as someone like aysiu, so maybe it's best I leave it to him to help you resolve your problem.

---

### Post by Fertech on 2008-06-23
i did install it, but at this moment i can't open my firefox i'm using opera browser. i have all my bookmarks in firefox.

---

### Post by Dale61 on 2008-06-23
Until you are able to sort out your FF problem, why don't you import your bookmarks from FF into Opera?  That way, you should then be able to completely remove all traces of FF without losing any of your bookmarks, then when you re-install FF, you can then import them back again.

I was able to import my FF bookmarks for the short period of time I tried Opera, but didn't think it was as good as FF, so I sent them back to FF and removed Opera.

---

### Post by Fertech on 2008-06-25
how can i import all my bookmarks from FF to my other Browser.

---

### Post by aysiu on 2008-06-25
> **Fertech said:**
> how can i import all my bookmarks from FF to my other Browser.
Your Firefox bookmarks are in /home/*username*/.mozilla/*profilename*/bookmarks.html

.mozilla is a hidden directory, by the way.

---

### Post by Dale61 on 2008-06-25
> **Fertech said:**
> how can i import all my bookmarks from FF to my other Browser.

When I first installed Opera, iirc, I had a dialog box pop up and ask if I wanted to import bookmarks from elsewhere.

There must be an import button somewhere within the menu buttons of Opera, but as it's been so long since I used it, I can't remember where it would be.

---

