---
title: "Wierd problem with HTTP / Internet"
date: 2009-01-23
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by rpalyvoda on 2009-01-23
Hi,

I've just installed Alpha 3. Works like a charm except for one issue: http protocol seems blocked.

I.e. I've got internet connexion (both wireless and wired). In every case, I get connected to Internet, Skype works, Apt works etc. Except Firefox for http adresses. Tried other browsers and even wget, http simply doesn't work!

Any ideas?

---

### Post by linux6994 on 2009-01-23
Have you tried to remove and reinstall firefox?

sudo apt-get remove firefox
sudo apt-get install firefox

---

### Post by mrfr0g on 2009-01-23
Since you mentioned other browsers, it sounds less like a firefox issue, and more like a firewall issue. Try to open the http ports using this command in terminal,

sudo ufw allow 80
sudo ufw allow 8080

Then try to access websites

---

