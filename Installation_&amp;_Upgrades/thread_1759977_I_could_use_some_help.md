---
title: "I could use some help"
date: 2011-05-16
forum: Installation &amp; Upgrades
---

### Post by cm101 on 2011-05-16
Hi, sorry if this is the wrong way to ask for help or if I've done something wrong... I'm new to this. 
Well I dual booted my hard drive to have windows vista and Ubuntu. 
Ubuntu was working perfectly fine, then I used the Update Manager to update ubuntu, but my laptop randomly shut down during the installation (which my laptop has never done before and hasnt done since). When I turned the laptop back on, and booted Ubuntu, a white box appears in the middle of the screen but rather than asking for my login details, it just says what I named my computer. I am unable to move my mouse or type anything on my keyboard at this stage... should I just leave it for a considerably long amount of time? Or should i do something else?

Thank you for the help in advance :)

---

### Post by zvacet on 2011-05-16
When you see grub choose recovery mode and then login and try 

```
sudo apt-get update && sudo apt-get upgrade && sudo apt-get dist-upgrade

sudo dpkg --configure -a
sudo apt-get -f install
```

P.S. Put more descriptive title next time so you can get help faster and help other people with same problem to find solution.

---

### Post by cm101 on 2011-05-18
Oh thanks for the advise about the title :)

But I understand what you mean by grub recovery but what you sending me the code for? Sorry if I seem stupid. :P

---

### Post by Zero2Nine on 2011-05-18
> **cm101 said:**
> Oh thanks for the advise about the title :)

But I understand what you mean by grub recovery but what you sending me the code for? Sorry if I seem stupid. :P

Once in recovery mode you get a command line where you can enter those commands.

---

