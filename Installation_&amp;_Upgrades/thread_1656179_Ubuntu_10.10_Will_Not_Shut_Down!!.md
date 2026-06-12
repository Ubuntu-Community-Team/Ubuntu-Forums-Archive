---
title: "Ubuntu 10.10 Will Not Shut Down!!??"
date: 2010-12-30
forum: Installation &amp; Upgrades
---

### Post by mildenhall on 2010-12-30
I have installed Ubuntu 10.10 on my touch screen O2 Joggler. Everything works fine apart from when I try to shut down. Everything closes and then the joggler just returns to the login screen. I have to pull the power to turn it off.

All I have done is "apt-get remove indicator-me" and "apt-get install indicator-session" so I have a smaller power icon in the top panel.

Does anyone have any ideas please? Thanks

---

### Post by darlid01 on 2010-12-30
I have run across this too on my old laptop. If I shut it down from command prompt, it stays shut down and works fine from then on.

Go to terminal (Applications->accessories->terminal and type or copy paste the following

```
sudo shutdown -h now
```

After the laptop shuts down, reboot normally and try and shut down normally

---

### Post by mildenhall on 2010-12-30
Thanks, that worked perfectly!!

---

### Post by milkmiruku on 2011-01-02
this is happening for me also, when using the option from the panel. i'll try the command line suggestion, which'll probably work, but might this be a known bug for the panel shutdown method?

---

### Post by ruimarto on 2011-05-21
Is there a way to make this happen permanently? Or do I have to put the "-h" every time I want it to shutdown?

---

