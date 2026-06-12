---
title: "HELP: Stuck at Language Prompt during Install"
date: 2006-07-12
forum: Installation &amp; Upgrades
---

### Post by scottgriz on 2006-07-12
I am attempting to install Xubuntu on a Toshiba Satellite 335CDT. Yes, and old laptop. Ubuntu v5 worked fine but was horribly slow. I was hoping that Xubuntu might have a bit more pep. In any case, I am getting stuck on the install at the Language prompt. 
The screen only goes to 800x600 and when the language window comes up, it will not let me scale it to fit the window. So, I can not see the "OK" or "Continue" button after selecting English from the list. I have tried pressing return to acknowledge, but that didn't work. 
Does anyone know of a way past this?
Can it be installed from a command line rather than from the install icon within the "Live" CD desktop.
Thanks.

---

### Post by taurus on 2006-07-12
Install the server version and then install XFce4 later with
```

sudo apt-get update
sudo apt-get install xubuntu-desktop

```

---

### Post by scottgriz on 2006-07-12
So I understand this correctly. I install the full Ubuntu 6.0.6 Server version and not Xubuntu? I am inclined to think this is what you mean because I don't see a server version of Xubuntu. 
Can you clarify what XFce4 is? Sorry, but I am a Ubuntu Nubie.

---

### Post by mi_were on 2007-03-12
> **scottgriz said:**
> I am attempting to install Xubuntu on a Toshiba Satellite 335CDT. Yes, and old laptop. Ubuntu v5 worked fine but was horribly slow. I was hoping that Xubuntu might have a bit more pep. In any case, I am getting stuck on the install at the Language prompt. 
The screen only goes to 800x600 and when the language window comes up, it will not let me scale it to fit the window. So, I can not see the "OK" or "Continue" button after selecting English from the list. I have tried pressing return to acknowledge, but that didn't work. 
Does anyone know of a way past this?
Can it be installed from a command line rather than from the install icon within the "Live" CD desktop.
Thanks.

I am also installing Xubuntu on the 335CDT. Try installing the Alternate CD, that should solve that problem. Also at the fist stall set the display to 600x800. How that will be helpful to someone out there.

I am now working on get my sound up and running.

---

