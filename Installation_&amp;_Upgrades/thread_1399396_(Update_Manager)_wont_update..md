---
title: "(Update Manager) wont update."
date: 2010-02-05
forum: Installation &amp; Upgrades
---

### Post by Unix-Man on 2010-02-05
Hey guys! 

So a couple days ago Update Manager popped up, I clicked install update. 

It says 
Reading Package List... 
Reading Dependency Tree... 
Reading State Information... 

Than the little window closes and nothing happens. 
I can click install updates again and does the exact same thing. 

I've tried restarting. Nothing. 

Also tried 

```
sudo apt-get update
```

It says 

```
sudo: /etc/sudoers is mode 0777, should be 0440
Segmentation fault 
```

I tried 

```
sudo chmod 0440 '/etc/sudoers'
``` 

It says the same thing. 

```
sudo: /etc/sudoers is mode 0777, should be 0440
Segmentation fault
``` 

I don't get it. 
Hope you guys can help! 

Thanks
Unix-Man

---

### Post by Unix-Man on 2010-02-05
Bump? 
Anyone got anything?

---

### Post by Unix-Man on 2010-02-06
Well, It's solved...

```
sudo: /etc/sudoers is mode 0777, should be 0440
Segmentation faul
```

Was the problem. 

I booted in recovery mode, drop to a root shell and 

```
chmod 440 /etc/sudoers
``` 

Got it working :) 
SOLVED!

---

