---
title: "screen failer"
date: 2005-05-23
forum: Installation &amp; Upgrades
---

### Post by kransky_dan on 2005-05-23
hey,
i have just installed the new 5.04 ubuntu and it isntalls fine, but when it comes to the login screen it turns to fuzz, like you get when there is no reception on your TV, now i dont know bout any of you but that isnt good from my point of view, so im wondering is this a problem with installation or is it a confliction problem with my video card??? im guessing video card because its a old system.
But it would be good to know what you guys think/
cheers have a good day/night!
cheers

---

### Post by matej on 2005-05-23
I have simillar problem, take a look: [http://ubuntuforums.org/showthread.php?t=36164&highlight=et6000]("http://ubuntuforums.org/showthread.php?t=36164&highlight=et6000")
(You can switch to text mode and back with: Ctrl-Alt-F1 and then Alt-F7)

Or you simply have wrongly configured x.org, so alter your configuration with
 ```
sudo xorgconfig
``` 
or
 ```

sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
sudo nano /etc/X11/xorg.conf

```

---

