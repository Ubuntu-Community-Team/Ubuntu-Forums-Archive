---
title: "Simple Grub Edit Problem"
date: 2010-01-01
forum: Installation &amp; Upgrades
---

### Post by garywright on 2010-01-01
Greetings all. I am a new user with little knowledge about linux but am trying. I have installed Ubuntu 9.10 on an acer laptop and everything is fine except that the fan doesn't work.

After checking a few threads here I found that I could make it come on continuously (which I reluctantly accept as OK and is better than not working at all) if I edit the grub commands from the grub startup menu by adding the line "acpi=off" and then ctl X to boot. 

This works fine but I don't want to have to do this every time I start. Can someone please tell me if I can automate this by editing some special file? I forgot to say that I am dual booting with Vista.

---

### Post by zine92 on 2010-01-01
You can edit the /etc/default/grub file and add acpi=off to the command line settings.  The line would look like this:

```
GRUB_CMDLINE_LINUX_DEFAULT="acpi=off quiet splash"
```

Must be edited as root.

Go to terminal and copy and paste in terminal
```
sudo gedit /etc/default/grub
```


Then run:


```
sudo update-grub
```


Then reboot.

Hope this solves your problem.

Solutions from [HTML]http://kubuntuforums.net/forums/index.php?topic=3108939
[/HTML] but edited by myself

---

### Post by SecretCode on 2010-01-01
I'm a beginner with grub but I'll give this a try.

I assume you are using grub2, if this is a fresh install of 9.10.

Make a backup copy of /etc/default/grub. Then edit this file (with your favourite text editor in sudo/gksudo mode). Change the line ```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
``` to ```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi=off"
``` Then run ```
sudo update-grub
```

eta ... while I was typing that zine92 posted the same solution!

---

### Post by JoeFriday49 on 2010-01-05
> **garywright said:**
> Greetings all. I am a new user with little knowledge about linux but am trying. I have installed Ubuntu 9.10 on an acer laptop and everything is fine except that the fan doesn't work.

After checking a few threads here I found that I could make it come on continuously (which I reluctantly accept as OK and is better than not working at all) if I edit the grub commands from the grub startup menu by adding the line "acpi=off" and then ctl X to boot. 

This works fine but I don't want to have to do this every time I start. Can someone please tell me if I can automate this by editing some special file? I forgot to say that I am dual booting with Vista.

Hope that worked better for you than it did for me...  LOL  It was time for a fresh install anyway...  : (

---

