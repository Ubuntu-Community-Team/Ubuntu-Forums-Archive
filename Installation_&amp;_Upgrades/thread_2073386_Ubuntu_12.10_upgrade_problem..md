---
title: "Ubuntu 12.10 upgrade problem."
date: 2012-10-19
forum: Installation &amp; Upgrades
---

### Post by prasantrai on 2012-10-19
Hi,

Just now have upgraded my laptop from Ubuntu 12.04 to 12.10. Upgrade process went fine, but after that i cant see any thing except my default desktop. I tried login as a guest too but issue is same. I am not able to open unity launcher also. Nothimg is  working. Can amy one help me out in this problem.

Thanks.

---

### Post by Frogs Hair on 2012-10-19
Hello and Welcome
 
If I am understanding correctly the desktop is visible but frozen. You can try the following

_Unity Not Working_ 

Login to Ubuntu use Ctrl + Alt + F1 to enter TTY. Next enter user name, password, and run the following command.

 ```
setsid unity
```
Wait until the process is complete and your user name appears again. Use Ctrl + Alt + F7 to renter the desktop environment.

If there is error reporting wait until finished. If Unity doesn't appear within a minute or two restart and login to Ubuntu.

---

### Post by Supaiku on 2012-10-20
> **Frogs Hair said:**
> Hello and Welcome
 
If I am understanding correctly the desktop is visible but frozen. You can try the following


I suspect this may not be the problem, though perhaps **prasantrai **can confirm.

I have a (I think) similar problem. After upgrading to 12.10, unity does not start. Instead, xorg runs, and the wallpaper is visible, with some windows (for instance, programs which are set to start on startup, like deluge, and my sensor dock app) start up. I can even start a terminal with Ctrl+Alt+T. However, these windows lack their Unity GUI components, like close, maximize and minimize. Also, the Unity bar etc. are not there.

**prasantrai**, what hardware do you have?

My amd64 system has an onboard Radeon HD4250. looking at logs from trying to start unity confirm there is a problem with opengl for me. I suspect, it may be related to the Radeon drivers, and the update to xorg 1.13 and Opengl 3.0, as described here: [www.ubuntuvibes.com/2012/10/how-to-enable-opengl-30-support-for.html](www.ubuntuvibes.com/2012/10/how-to-enable-opengl-30-support-for.html)

However, I haven't solved this problem for me yet (partially due to not having access to the computer in question ATM.)

Does my problem sound similar to your problem **prasantrai**?
Does anyone else have any input for this problem?

EDIT:
For me this problem was fixed simply by removing fglrx

'sudo apt-get autoremove fglrx --purge'

[http://askubuntu.com/questions/202752/upgrade-to-quantal-unity-top-bar-side-bar-and-window-declorations-missing/202782](http://askubuntu.com/questions/202752/upgrade-to-quantal-unity-top-bar-side-bar-and-window-declorations-missing/202782)

---

### Post by rbscycle on 2012-12-18
> **prasantrai said:**
> Hi,

Just now have upgraded my laptop from Ubuntu 12.04 to 12.10. Upgrade process went fine, but after that i cant see any thing except my default desktop. I tried login as a guest too but issue is same. I am not able to open unity launcher also. Nothimg is  working. Can amy one help me out in this problem.

Thanks.

I just updated 12.10 with the new updates and have the same problem.  I also had Docky installed, so I could get to my files, but no Unity!  I just wiped the system and re-installed everything.  I'll try the update with no Docky...

---

### Post by rbscycle on 2012-12-18
> **rbscycle said:**
> I just updated 12.10 with the new updates and have the same problem.  I also had Docky installed, so I could get to my files, but no Unity!  I just wiped the system and re-installed everything.  I'll try the update with no Docky...


After re-installing 12.10, I dad a: sudo apt-get update, then a sudo apt-get upgrade, from the command prompt.  Now Unity is there.  Everything seems to be working.

---

### Post by hans12345 on 2013-03-29
Sounds like my problem
"Just now have upgraded my laptop from Ubuntu 12.04 to 12.10. Upgrade process went fine, but after that i cant see any thing except my default desktop. I tried login as a guest too but issue is same. I am not able to open unity launcher also. Nothimg is working. Can amy one help me out in this problem."

On startup, I have my wall paper, I have my Icons, but NOTHING else. No header, no footer, no sidebar. I cannot even do a shutdown - I have to use the power switch!

This sounds familar "My amd64 system has an onboard Radeon HD4250"

I'll try some of the above ideas and post results.

---

### Post by hans12345 on 2013-03-29
I tried this but it did not work, still no Unity:
"After re-installing 12.10, I dad a: sudo apt-get update, then a sudo apt-get upgrade, from the command prompt. Now Unity is there. Everything seems to be working."

But I found this solution:
[http://www.unixmen.com/ubuntu-12-10-and-amd-catalyst-problem-solved/](http://www.unixmen.com/ubuntu-12-10-and-amd-catalyst-problem-solved/)

I followed this advice:
Quote
use a 3rd-party repository created by Tomasz Makarewicz for this purpose only. (I personally recommend it)

sudo add-apt-repository ppa:makson96/fglrx
sudo apt-get update
sudo apt-get upgrade
sudo apt-get install fglrx-legacy

finally reboot your PC
Endquote

Perfect!

Shall I have to do the same thing for every Ubuntu upgrade?

---

### Post by enderforce on 2013-05-26
I seem to have this same problem. I recently realized I still had 12.04, so I upgraded to 12.10, then upgraded to 13.04. I tried the download from [http://www.unixmen.com/ubuntu-12-10-and-amd-catalyst-problem-solved/](http://www.unixmen.com/ubuntu-12-10-and-amd-catalyst-problem-solved/) and ```
sudo apt-get autoremove fglrx --purge
```as well as other things, but still no luck. Any ideas? Should I not have upgraded to 13.04 until fixing this? Thanks.

P.S. I think my graphics card is a Mobility Radeon HD 3000 series in case you are wondering

---

### Post by enderforce on 2013-06-02
I just decided to back up and reinstall. Everything seems ok now (well there are still some minor and probably not directly related problems).

---

### Post by virtual_m on 2013-06-03
> **Supaiku said:**
> 
.....
For me this problem was fixed simply by removing fglrx

'**sudo apt-get autoremove fglrx --purge**'

[http://askubuntu.com/questions/202752/upgrade-to-quantal-unity-top-bar-side-bar-and-window-declorations-missing/202782](http://askubuntu.com/questions/202752/upgrade-to-quantal-unity-top-bar-side-bar-and-window-declorations-missing/202782)

This works for me too... 
[graphic card on mine Toshiba laptop is ATI Mobility Radeon HD 5145]

---

### Post by mostafijur-rahman75 on 2014-05-22
i also upgrade from ubuntu 12.04 to 12.10.but after upgrade and restarting my laptop till the 'welcome ubuntu' everything gone fine but after that a black screen appears,its not allowing me to go to the login option.im not able to do anything,no key is working.please help me.
thank you.

---

