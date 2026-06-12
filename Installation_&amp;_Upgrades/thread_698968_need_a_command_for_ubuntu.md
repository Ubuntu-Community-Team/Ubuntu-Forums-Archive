---
title: "need a command for ubuntu"
date: 2008-02-16
forum: Installation &amp; Upgrades
---

### Post by confused1 on 2008-02-16
My computer says that alternate CD is installed on my computer, but I have serious reservations.

When I boot up I get the login then password. What do I type next to get it going- yes a noob:confused:

---

### Post by overdrank on 2008-02-16
> **confused1 said:**
> My computer says that alternate CD is installed on my computer, but I have serious reservations.

When I boot up I get the login then password. What do I type next to get it going- yes a noob:confused:

HI and you mean you get the login screen that is tan and user name and password or you mean a black and white screen with command prompt? Could you give us some system specs and you can try the command startx.

---

### Post by confused1 on 2008-02-16
800MHz P3 
528MB RAM
32MB Diamond Stealth Video Card

I get the command line black on white.

I will try that command thanks. I'm burning the ISO again at a 2X speed- the system is still getting hung on base installation- but it says it ready to boot?

---

### Post by overdrank on 2008-02-16
> **confused1 said:**
> 800MHz P3 
528MB RAM
32MB Diamond Stealth Video Card

I get the command line black on white.

I will try that command thanks. I'm burning the ISO again at a 2X speed- the system is still getting hung on base installation- but it says it ready to boot?

Ok it sounds like are installing the sever edition not the desktop version. You may also try  the command if you have internet access ```
sudo apt-get install ubuntu-desktop
``` or if you were wanting kubuntu, xubuntu. then replace ubuntu.

---

### Post by confused1 on 2008-02-17
the commands did not work and my my reburning of alternate CD and 2X speed was somewhat better.

But, I have taken a different tack. I saw an article on pychocats at 

[http://www.psychocats.net/ubuntu/minimal](http://www.psychocats.net/ubuntu/minimal)


about a mini download (10MB) of Ubuntu, so I give it a try. I got the install completed but, I went to far and I think I have a gdm and a wdm that are in conflict and also I might have my resolution set too high because, my monitor will cut on and off and after the 6th time the screen stops and I get the message that something is bad wrong with the setup and to wait 2 minutes before I click "OK"

I tried running recovery and now my username and password aren't recognized-

any suggestions? :confused:

---

### Post by Lord Landis on 2008-02-17
In GRUB, select the emergency recovery console and put in your root password.  From there, you can create a new user account with the command 'adduser' (code 'man adduser' for help regarding the command) and set the password with the command 'passwd'.  Once those are done, reboot the system.  This should let you log in normally.

As for being stuck in the terminal, code 'ifconfig' and let us know what your network card configuration is.  If apt-get didn't work, you may not have a properly configured connection.

---

### Post by confused1 on 2008-02-17
thanks Lord Landis for the info. I had went ahead and reformatted the harddrive and started all over.

What I have now is a Ubuntu light install, which has begun to look like a full blown Ubuntu.

I'm having a problem with screen flicker. Which drivers or package would I use to control a Diamond Stealth 32MB video card. I need to get the freq. up above 60Hz.


i appreciate the help

---

### Post by Raistlin355 on 2008-02-17
If you are merely trying to get to a gui, at the command prompt type "init 5" and it will take you to the gui.

---

### Post by confused1 on 2008-02-17
Are you talking about the command prompt in the Ubuntu termina? I can get to the one in aplications>screen resolution, but its locked at 60Hz-

---

### Post by confused1 on 2008-02-18
thanks Raistlin 355 I guess that did it the freq. is up to 75Hz

---

### Post by Raistlin355 on 2008-02-18
Sweet, glad I could help!

---

