---
title: "Editing config files"
date: 2012-04-20
forum: Installation &amp; Upgrades
---

### Post by xworld on 2012-04-20
Hello, I am attempting to configure privoxy on ubuntu 12.04. Apparently I'm suppose to use ```
$ sudo vi /etc/privoxy/config 
```
When I enter that in the terminal it opens up the config file. I am supposed to append ```
forward-socks4a   /               127.0.0.1:9050 .
``` 
To the config file. However I am not really sure how to do this. I figured it was going to be simply copying and pasting it into the file and then save. I am not sure where to put it. Also I paste it in to the terminal but I can't save and close it. Any ideas?

Thanks

---

### Post by darkod on 2012-04-20
vi is a bit complicated editor, especially for first time users. Try nano.
sudo nano ......

You can move the cursor with the arrows and add/remove what you need.

When you are done, you save the file with Ctrl + O, change the name (or just hit Enter to save with same name, like in most cases you would), and Ctrl + X to exit nano.

See if that's easier.

---

### Post by xworld on 2012-04-21
Thanks a bunch

---

