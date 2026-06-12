---
title: "firefox 3 does not save cookies"
date: 2008-07-25
forum: Installation &amp; Upgrades
---

### Post by ladyinred on 2008-07-25
Hi. I recently replaced my Ubuntu (Hardy) installation with Xubuntu (also Hardy), and I noticed immediately that Firefox 3 is not saving cookies. I've checked to make sure all the settings are correct, but every time I restart Firefox I have to login again to my Google account (that's not the only site that I'm having this problem with, but it's a good example).

I found a thread from a while back with similar issues. They suggested that the extensions might be the problem. I disabled all extensions, and still the problem remains. Does anyone know what could possibly be wrong or how to fix it? If it helps, I'm running 64 bit.

---

### Post by aysiu on 2008-07-25
It's possible that if you ever ran the commands ```
sudo thunar
``` ```
sudo -s
``` or ```
sudo firefox
``` that the ownership of your Firefox settings folder (or one of its subfolders) got changed to root's. More details about how to properly use *gksudo* and *sudo* [here](http://www.psychocats.net/ubuntu/graphicalsudo).

You can fix that by closing Firefox, typing this command in [the terminal](http://www.psychocats.net/ubuntu/terminal): ```
sudo chown -R *username:username* /home/*username*/.mozilla
``` where *username* is your actual username, and then starting Firefox again.

---

### Post by ladyinred on 2008-08-12
I don't ever recall using those commands. However, I tried your suggestion, to no avail. Any other ideas?

---

### Post by aysiu on 2008-08-12
> **ladyinred said:**
> I don't ever recall using those commands. However, I tried your suggestion, to no avail. Any other ideas?
Double-check that in Edit > Preferences > Privacy you have *Keep until they expire* instead of *Keep until I close Firefox*

and/or

Close Firefox and launch it with the command ```
firefox -safe-mode
``` and see if you experience the same problem.

---

### Post by ladyinred on 2008-08-12
I have double checked;the cookies are set to be kept until the expire. I also have the same problem in safe mode.

---

### Post by ronnieredd on 2008-09-04
It's happening to me too. Multiple machines 32 and 64bit versions. I especially am noticing it when my google results keep showing up with 10 results per page. I go to preferences (google) and change it to 100 and next time I have a new instance fired up, I get 10 results again. Anyone have any ideas? I too tried the above suggestions and haven't changed anything. All the permissions are correct.:confused:

---

### Post by indeterminate on 2008-09-15
You might have some luck deleting the cookies.sqlite file (and cookies.txt if present) in the firefox profile (~/.mozilla/firefox/whatever-your-random-profile-name-is/). You'll lose any saved sessions, but it sounds like they aren't working anyway.

---

