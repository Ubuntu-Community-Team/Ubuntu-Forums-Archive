---
title: "Unusable system after 12.04 upgrade: no mouse, broken window manager(?)"
date: 2012-05-02
forum: Installation &amp; Upgrades
---

### Post by BungaDunga on 2012-05-02
I upgraded to 12.04 overnight last night, and apart from it prompting me to let it restart services, it went fine and prompted me to restart. Upon restart, it boots to the login screen but...

- Low resolution (640x480?)
- Various icons are red error-y Xs
- The mouse cursor doesn't respond

I can type my password and log in, but...

- Still low resolution
- The dock on the left is there but the buttons are blank
- The mouse still doesn't work
- I can get the "start menu" or whatever it's called to pop up by keyboard, and use it to launch Terminal, but it doesn't respond to keystrokes and has no window chrome.

Same results in the rescue mode. I hadn't made any huge changes to the 11.10 installation as far as I know, and it ran fine on my laptop (a Latitude D620). Help!

---

### Post by kc1di on 2012-05-02
What video card are you using?

---

### Post by Tanker Bob on 2012-05-02
See [this thread](http://ubuntuforums.org/showthread.php?t=1969754) for the probable solution if you have an nVidia GeForce 6, 7, or 8800 card.

---

### Post by BungaDunga on 2012-05-02
Oh, no idea. It's whatever integrated thing the D620 has. Er, Intel something or other.

The specs say it's either a GMA 950 or a Quadro NVS 110M. I'm almost positive it's the GMA but I don't know.

Edit: XP says "945GM Express Chipset Family."

---

### Post by Tanker Bob on 2012-05-02
Can you successfully run Ubuntu 2D mode at login?

---

### Post by BungaDunga on 2012-05-02
This is a good question. I don't know if I can pick it without a mouse cursor; I'll give it a try.

---

### Post by kc1di on 2012-05-02
> **BungaDunga said:**
> This is a good question. I don't know if I can pick it without a mouse cursor; I'll give it a try.

if it's the intel gma 950 try what this page suggests:

[http://www.jacoblog.net/2011/10/29/ubuntu-11-10-intel-driver-problem/]("http://www.jacoblog.net/2011/10/29/ubuntu-11-10-intel-driver-problem/")

---

### Post by BungaDunga on 2012-05-02
> **kc1di said:**
> if it's the intel gma 950 try what this page suggests:

[http://www.jacoblog.net/2011/10/29/ubuntu-11-10-intel-driver-problem/]("http://www.jacoblog.net/2011/10/29/ubuntu-11-10-intel-driver-problem/")

No luck putting that thing in by hand in GRUB (haven't tried editing the file).

2D mode behaves more or less the same.

I tried booting an old kernel from grub and the mouse worked but the keyboard didn't, at least not past the login screen. I coaxed it into starting Firefox, but it had no window chrome.

---

### Post by wolfseyn on 2012-05-04
Hi,  I am seeing the same thing after upgrading from Oneiric to Precise.  I thought it might be because of [This Bug]("https://bugs.launchpad.net/ubuntu/+source/taglib/+bug/902603").  I have an ATI video card and was running the proprietary drivers.

I am able to log in and use super key to pull up search. No icons show up on unity.  Search will open any program, but nothing works.  Can't type in the terminal, I can't select anything with the keyboard.  The mouse doesn't work.  Alt+F2 will bring up the run dialog, but enter a program name and nothing happens. Ctrl+Alt+F1, etc produces a blank screen.  
Same as OP describes, except my screen resolution is still normal. 
Hoping someone can make sense of it.  Thanks for any help.

---

### Post by tommy.sean on 2012-05-05
I am experiencing the same issue after upgrading from 11.10 to 12.04 on my Dell Inspiron Netbook. 

*I am also able to log in and use super key to pull up search. No icons show up on unity. 

*Also search will open any program, but nothing works. Can't type in the terminal and I can't select anything with the keyboard. 

*The mouse doesn't work.

Windows just says the the video card is built in Mobile Intel 4 series.
Ubuntu 11.10 worked awesome. ....I shouldn't have upgraded.

---

### Post by wolfseyn on 2012-05-05
I think this is a result of [https://bugs.launchpad.net/ubuntu/+source/taglib/+bug/902603](https://bugs.launchpad.net/ubuntu/+source/taglib/+bug/902603)

I might be wrong on the relation, but this fixed the problem for me.


If you can get to a command line -- I had to boot to the GRUB menu (ESC at boot) and edited the default option to include "text" at the very end of the "linux" command.  I was able to boot into a command prompt and run the commands as described in Bug 902603.

> 
If you did not install the dpkg update prior to upgrade and have hit this bug as a result, you will need to manually recover by running the following commands from a terminal:
 find /var/cache/apt/archives -name 'libjpeg8_*.deb' -name 'libtag1c2a_*.deb' \
     -name 'odbcinst_*.deb' -name 'libccid_*.deb' -name 'libao-common_*.deb' | sudo xargs dpkg -i
 sudo apt-get -f install


Note, the first part, starting with find... ending with " | sudo xargs dpkg -i" is all one line.  in my case the find command found nothing. The second command, sudo apt-get -f install is the one that did the trick, which makes me wonder if it was this bug causing the problem or something else that caused the install to fail.

---

### Post by Doppp on 2012-05-06
I have exactly the same problem as the OP. Anyone managed to solve this yet? If not I'm going to try a fresh install on my Ubuntu partition.

---

### Post by sdyson on 2012-05-08
Thanks wolfseyn, that solved my same problem. 

I was unable to boot into text mode from Grub using the latest kernel, but managed to do it using the previous kernel.

---

### Post by BungaDunga on 2012-05-16
Wolfseyn's suggestion fixed my install, too; same experience (the second line is the one that does anything). Got to text mode from a previous kernel as well.

---

### Post by Doppp on 2012-05-16
Yes, wolfseyn's suggestion worked for me too. I didn't do it via the terminal way, I loaded the Recovery Mode of the previous kernel and did a dpkg update that way. Everything works now. Thanks!

---

