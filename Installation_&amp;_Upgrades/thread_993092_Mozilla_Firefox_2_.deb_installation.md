---
title: "Mozilla Firefox 2 .deb installation?"
date: 2008-11-25
forum: Installation &amp; Upgrades
---

### Post by Teniser on 2008-11-25
I need Mozilla Firefox 2 .deb instalation (not .rpm or tar.gz). I tryed to get it from Synaptic packet manager, but that installation have a problem. Thank you.

PS: My version is Ubuntu 8.10

---

### Post by aheckler on 2008-11-25
Why do you need a .deb? You can download the .tar.gz from [here]("http://www.mozilla.com/en-US/firefox/all-older.html") and run Firefox straight from the folder, no compiling needed.

I'm not sure if a .deb is available in the Intrepid repos any more.

---

### Post by Teniser on 2008-11-25
What i have to click to run Mozilla 2 installation?
In folder which i downloaded from Mozilla website, there is so much files.
Please, help me.

---

### Post by spawn. on 2008-11-25
download medibuntu respository and after you install this, update your stuff, then open synaptic package manager and search for FireFox 2.

Google: Ubuntu Medibuntu

---

### Post by aheckler on 2008-11-25
You would use the file just named "firefox".

---

### Post by Teniser on 2008-11-25
OMG...None of this is not helpful:(

Actually, I have a problem with Firefox 3.0. When I run Firefox 3.0, does not appear barline where is the exit, minimize and maximize bar. Couple of weeks before I download Firefox 2 from the Synaptic packet manager and the problem disappeared, and now I the problem is here again. :(

Sorry for my bad English!

---

### Post by aysiu on 2008-11-25
Sounds like a corrupt Firefox profile to me.

Your best bet is to export your bookmarks, close Firefox, rename the /home/*username*/.mozilla folder to /home/*username*/.mozilla.old, start Firefox again, and then import your bookmarks again.

There is a .deb for Firefox 2, but it's not available for Intrepid.

If that fresh profile still gives you the same problem, I can walk you through step-by-step on using the .tar.bz2 of Firefox 2.

---

### Post by Teniser on 2008-11-25
This is not helpful.

Can you walk me step-by-step on using tar.gz of Firefox 2? Thank you!

---

### Post by aysiu on 2008-11-25
Paste these commands into [the terminal](http://www.psychocats.net/ubuntu/terminal): ```
wget -c http://mirror.yandex.ru/mozilla/firefox/releases/2.0.0.18/linux-i686/en-US/firefox-2.0.0.18.tar.gz
sudo tar -xvzf firefox-2.0.0.18.tar.gz -C /opt
sudo mv /opt/firefox/plugins /opt/firefox/plugins.bak
sudo ln -s /usr/lib/xulrunner-addons/plugins /opt/firefox/plugins
sudo dpkg-divert --divert /usr/bin/firefox.ubuntu --rename /usr/bin/firefox
sudo ln -s /opt/firefox/firefox /usr/bin/firefox
``` Then close Firefox completely. Wait two seconds. And then click on the Firefox icon again. It should launch Firefox 2.0.0.18

---

### Post by aheckler on 2008-11-25
> **Teniser said:**
> Actually, I have a problem with Firefox 3.0. When I run Firefox 3.0, **does not appear barline where is the exit, minimize and maximize bar**. Couple of weeks before I download Firefox 2 from the Synaptic packet manager and the problem disappeared, and now I the problem is here again.

This actually sounds like a Compiz or window manager problem, aysiu. I'm not really sure how to go about fixing it though.

---

### Post by Teniser on 2008-11-25
@aysiu, omg thank you so so much...i did it..
But now, i want to upgrade to Firefox 3. In the Synaptic packet manager Firefox 3 iz marked as installed application, and i have only option to reinstal Firefox 3. I am asking you now: click to REINSTAL or do something other..? :/

---

### Post by Teniser on 2008-11-25
I need now repository for updating Mozilla Firefox...  :)

---

### Post by Teniser on 2008-11-28
> **aysiu said:**
> Paste these commands into [the terminal](http://www.psychocats.net/ubuntu/terminal): ```
wget -c http://mirror.yandex.ru/mozilla/firefox/releases/2.0.0.18/linux-i686/en-US/firefox-2.0.0.18.tar.gz
sudo tar -xvzf firefox-2.0.0.18.tar.gz -C /opt
sudo mv /opt/firefox/plugins /opt/firefox/plugins.bak
sudo ln -s /usr/lib/xulrunner-addons/plugins /opt/firefox/plugins
sudo dpkg-divert --divert /usr/bin/firefox.ubuntu --rename /usr/bin/firefox
sudo ln -s /opt/firefox/firefox /usr/bin/firefox
``` Then close Firefox completely. Wait two seconds. And then click on the Firefox icon again. It should launch Firefox 2.0.0.18

Do you have a uninstall commands for Firefox 2.0.0.18? Thanks!

---

### Post by aysiu on 2008-11-28
> **Teniser said:**
> Do you have a uninstall commands for Firefox 2.0.0.18? Thanks!
Yeah, they're [here](http://psychocats.net/ubuntu/firefox#remove).

---

