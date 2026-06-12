---
title: "Removing grub loader password"
date: 2020-08-25
forum: Installation &amp; Upgrades
---

### Post by sddodger5 on 2020-08-25
Hello,
I have a dual boot Ubuntu 18.04 and Windows 10 desktop. Only when booting into the Windows 10 install the grub loader asks for a username and password to continue. How can I remove this so it just boots into Windows 10 when selected?

---

### Post by CelticWarrior on 2020-08-25
Welcome.

Nver seen anything like that. What exactly are those username and password it asks for when selecting Windows 10 from Grub menu?

---

### Post by sddodger5 on 2020-08-25
> **CelticWarrior said:**
> Welcome.

Nver seen anything like that. What exactly are those username and password it asks for when selecting Windows 10 from Grub menu?
Not sure if I select Ubuntu it just goes to the login screen for Ubuntu. If I select Windows 10 it asks for a username and password to continue. If I got to the Windows installation through the BIOS boot options, then I can get into windows fine.

---

### Post by CelticWarrior on 2020-08-25
I asked what those username and password were... Expanding on this idea:

- Is it something you know?
- Is it the same as your Ubuntu login, the same as your Windows login or something else?

Just trying to understand what it is so we can think about where that might have came from because surely it isn't normal.

---

### Post by sddodger5 on 2020-08-25
Not sure what the username and password are. I've tried both the ubuntu and windows credentials but neither worked

---

### Post by ActionParsnip on 2020-08-25
Can you give a screenshot please?

---

### Post by CelticWarrior on 2020-08-25
Can you please post a picture showing the dialog?

---

### Post by sddodger5 on 2020-08-25
[ATTACH=CONFIG]286802[/ATTACH][ATTACH=CONFIG]286803[/ATTACH]

Attached are the boot menu and then the screen I get after selecting the Windows install. Thanks for the help!

---

### Post by tea for one on 2020-08-25
I've never seen this before and it's certainly baffling but I'll offer a **suggestion**:-

Log in to Ubuntu and update grub.

```
sudo update-grub
```

Given the unusual problem, I've no idea what could transpire.

However, do **not** try this unless you have restorable back-ups.

---

### Post by deadflowr on 2020-08-25
That looks like what a grub password would show so as above in a booted Ubuntu run this from a terminal and post back the results
```
grep password /etc/grub.d/00_header /etc/grub.d/30_os-prober /etc/grub.d/10_linux 
```

---

### Post by tea for one on 2020-08-25
> **deadflowr said:**
> That looks like what a grub password would show so as above in a booted Ubuntu run this from a terminal and post back the results
```
grep password /etc/grub.d/00_header /etc/grub.d/30_os-prober /etc/grub.d/10_linux 
```

Good grief - I had no idea that Grub2 had a password facility.

[https://help.ubuntu.com/community/Grub2/Passwords](https://help.ubuntu.com/community/Grub2/Passwords)

@sddodger5 - Please ignore my suggestion in post 9.

---

