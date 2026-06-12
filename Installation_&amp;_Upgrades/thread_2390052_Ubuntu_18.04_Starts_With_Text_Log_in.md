---
title: "Ubuntu 18.04 Starts With Text Log in"
date: 2018-04-24
forum: Installation &amp; Upgrades
---

### Post by mrkeef on 2018-04-24
I just upgraded from 17.10 to 18.04. The upgrade went fine, but instead of going through to the standard log in page (is that gdm?), I just get a test log in. Typing startx gets X and gnome going, and apart from having to enter my password again for the gnome keyring, all is well.

What do I need to do to get the normal log in back?

Keith

---

### Post by Claus7 on 2018-04-26
Hello,

1) in order to check which display manager you are using type:
```
cat /etc/X11/default-display-manager
```

most probably you will be able to see gdm3.

2) you can change that by issuing the command:
```
sudo apt-get install lightdm
```

If you have gdm3 installed it will ask you to choose. It is better to have one display manager installed, so remove gdm3 first.

3) In case you have another display manager would could change your greeter (go to synaptic package manager and install another greeter). I have a nice combination of unity-greeter with lightdm.

4) In case you want to check your greeter type:
```
dpkg -l *greeter*
```

Regards!

---

### Post by mrkeef on 2018-04-28
Thanks, Claus. My son was able to sort this out, and the issue was as you described. Same problem was experienced on my laptop also.

---

### Post by djroff on 2018-04-28
I had a similar problem when I went to upgrade, which I tried multiple times with the same result... rebooting brings me to a completely black-and-white command-line only screen, makes me log in (which I'd always kept as automatic, before), and then just sits there at a prompt.   I went on Stack Overflow to ask about this, and so far the only response I've gotten was to enter "startx" to bring up the normal environment.  But that's called a workaround, it didn't address the fact that I want to FIX the problem, and end up with an 18.04 which boots normally into the GUI.

After messing with it for a day and a half, I decided to wipe the problem upgrade and restore 17.10, which was fully functional.  So in order to try fixing the problem the way suggested here (by making sure it's pointed to the proper graphics adapter, updating to the proper graphics driver, etc.), I will have to re-upgrade -- and before I do that, I want to make sure the "fix" is going to work.  

The following is the screen I see after the final reboot.  If anyone has any further suggestions, please pitch in:

Ubuntu 18.04 LTS BigBoy tty1   [NOTE: BigBoy is my computer's name, no laughing]

BigBoy login:dave

Password:

Welcome to Ubuntu 18.04 LTS (GNU/Linux 4.15.0-20-generic x86_64)

* Documentation:  [https://help.ubuntu.com](https://help.ubuntu.com)
* Management:  [https://landscape.canonical.com](https://landscape.canonical.com)
* Support:  https:ubuntu.com/advantage

* Meltdown, Spectre and Ubuntu:  What are the attack vectors, how the fixes work, 
and everything else you need to know -- https:ubu.one/u2know

0 packages can be updated
0 updates are security updates

You have packages from the Hardware Enablement Stack (HWE) installed that are going 
out of support on 2016-08-04.

There is a graphics stack installed on this system.  An upgrade to a configuration 
supported for the full lifetime of the LTS will become available on 2016-07-21 and 
can be installed by running "update manager" in the Dash.

The programs included with the Ubuntu system are free software;  the exact 
distribution terms for each program are described in the individual files in 
/usr/share/doc/*/copyright.

Ubuntu comes with ABSOLUTELY NO WARRANTY, to the extent permitted by applicable law.

dave@BigBoy:"$

---

