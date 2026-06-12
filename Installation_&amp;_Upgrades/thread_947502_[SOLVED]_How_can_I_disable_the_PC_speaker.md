---
title: "[SOLVED] How can I disable the PC speaker?"
date: 2008-10-14
forum: Installation &amp; Upgrades
---

### Post by BetterSense on 2008-10-14
I just installed Hardy on my laptop and when I reboot or shut down, I get a surprisingly loud system beep. I have disabled the system beep in the gnome sound mixer, and and added 'blacklist snd_pcsp' to my /etc/modprobe.d/blacklist file. But it still does it. It's too loud for use in class rooms.

---

### Post by aurelieng on 2008-10-14
In the BIOS ?

---

### Post by spd106 on 2008-10-14
Try adding this to the blacklists file too
```

blacklist pcspkr
```

---

### Post by lukydude on 2008-10-14
go to applications->accesories-->terminal

in the terminal type sudo apt-get install gnome-alsamixer press enter type your password.

when it's finished close terminal and go to applications-->sound & video---> gnome ALSA Mixer then you can control volume for everything.

---

### Post by BetterSense on 2008-10-15
blacklisting pcspkr seems to have done the trick.

---

