---
title: "apt-get / proxy / sudo driving me mad!"
date: 2012-03-20
forum: Installation &amp; Upgrades
---

### Post by GreySpike on 2012-03-20
I use a local CNTLM proxy to get through my corporate firewall.

Generally, if I use 
  sudo apt-get update
it fails to download anything, and the CNTLM log shows no activity

However
  sudo -i
  apt-get update
works perfectly every time and the CNTLM log shows exactly the activity I expect

All other applications (that understand the system proxy settings) work perfectly.

I know its minor but it of course stops synaptic working properly and is driving me mad.

Any ideas?

---

### Post by MG&amp;TL on 2012-03-20
```
gksu synaptic
```

(make a shortcut) should solve that problem. Can't think why your network is only accessible by root though, not sudo.

---

### Post by WasMeHere on 2012-03-20
This is what I guess:

The environment will be different when you run ***sudo -i*** compared to plain ***sudo*** with a command as parameter. And your company's proxy server is probably picky that everything should be proper (the environment should belong to the user running the command).

Will it be different between
```
gksudo synaptic
```
and
```

sudo -i 
synaptic

```
and
```

sudo -i synaptic

```

---

### Post by GreySpike on 2012-03-21
thanks for pointing me in the right direction. 

I don't think that the corporate proxy is that picky, and in any case apt-get is not using my local proxy unless I run sudo -i.

It seems that sudo completely replaces the environment with a sudo-specific version (for good security reasons). 

Sudo -i then additionally executes the /env/enviroment so that my proxy settings are restored.

Thanks again.

---

### Post by WasMeHere on 2012-03-21
I'm glad you got it right. If you feel that your problem is solved, please mark this thread as SOLVED, clicking on [COLOR="Red"]**Thread Tools**[/COLOR] at the top of this page.

---

