---
title: "Failed to start session after upgrade to 14.04"
date: 2014-04-18
forum: Installation &amp; Upgrades
---

### Post by prashanta2 on 2014-04-18
Hello,

I just did an upgrade to 14.04 Ubuntu. I had 13.10 with Mate Desktop. After upgrade and reboot, the system does not log in anymore. It just says "Failed to start session"

I guess mate crashed and know the system can't log in. What can I do?


Big thanks,
Pedro

---

### Post by prashanta2 on 2014-04-18
One additional info.
In the log in screen I go to terminal Ctrl+Alt+F1
after sudo su code I type password and get - login incorrect

---

### Post by prashanta2 on 2014-04-18
Somehow I got it to work... don't know what I did...

---

### Post by Abhilash_Nayak on 2014-04-19
I faced the same problem after the upgrade.. I tried to install Gnome env. and surprisingly this got fixed.

$ sudo apt-get install gnome
$ sudo reboot


After the reboot I selected Gnome environment first, but then I tried my luck with Ubuntu env. and wola! I was able to login..

---

### Post by charlyoleg2 on 2014-04-22
I face the same issue after updating from 12.04 to 14.04. Your workaround doesn't work in my case :( 

I have seen this debug messages in the lightdm log:
> sudo cat /var/log/lightdm/lightdm.log
DEBUG: Seat: Failed to find session configuration ubuntu
DEBUG: Seat: Can't find session ubuntu

I'm still looking for a solution!

---

### Post by ivan-janes on 2014-04-22
Try to install ubuntu-session package as suggested on [http://osdir.com/ml/ubuntu-bugs/2014-04/msg13063.html](http://osdir.com/ml/ubuntu-bugs/2014-04/msg13063.html)
```
sudo apt-get install ubuntu-session
```

If it is installed try to reinstall it with:
```
sudo apt-get install --reinstall ubuntu-session
```

---

### Post by moorkai on 2014-04-22
Tried ivan-janes' solution. Sadly, it didn't work for me. Changing user-session from ubuntu to mate in /etc/lightdm/lightdm.conf did the trick instead.

---

### Post by ron20 on 2014-05-14
I had the same problem and this solution worked for me.

> **ivan-janes said:**
> Try to install ubuntu-session package as suggested on [http://osdir.com/ml/ubuntu-bugs/2014-04/msg13063.html](http://osdir.com/ml/ubuntu-bugs/2014-04/msg13063.html)
```
sudo apt-get install ubuntu-session
```

If it is installed try to reinstall it with:
```
sudo apt-get install --reinstall ubuntu-session
```

---

### Post by Tony_Pellicccio on 2014-07-16
Thanks to all of you. I went from 12.04LTS to 14.04LTS. The upgrade was a nightmare. I mean are they that clueless at Canonical that they couldn't do a proper upgrade? Really? Now I just have to get my networking running again and I'll be back in business. But being out of service for a few days, that wasn't cute. Making me really re-think using Ubuntu.

---

### Post by rafael.lopez011 on 2014-07-23
Once I pressed ctr+alt+F1 or F2 .....or F6 the command line appear but request me the login and password. Once I entered the username and password it request me the password. Then 'Login incorrect' message appear. if I put the sudo and rest of the commands it does not work. 

Please help.

Also have tried booting from the USB with Ubuntu 14.04 LTS then open the terminal and then I'm able to execute the lines but after reinstall the session it is doing the same.

Please help

---

### Post by rafael.lopez011 on 2014-07-23
do you figure out what did you do? I have the same problem?

---

### Post by Jeton_Sinoimeri on 2014-07-24
I had the same problem, I upgraded from 12.04 to 14.04. I pressed CTR-ALT-F3 and then logged in using my credentials, then typed in sudo apt-get install, and put in my password. I let it finish then restarted the computer and was able to log in

---

### Post by derrick3 on 2014-10-23
When it says Login "Incorrect" you probably typed something wrong. Remember capitaliztion matters on both USER and PASS and make sure you type in the right password.

---

### Post by jiwon21c on 2015-01-28
This made it clear the problem in my case.
Thanks a lot.

---

### Post by Kuan-Hsun on 2015-08-05
It is still work for me as well. My case is that after updating the system as usual, I cannot log in the system.
[COLOR=#000000] Originally Posted by **ivan-janes** [[IMG]http://ubuntuforums.org/images/ubuntu-VB4/buttons/viewpost-right.png[/IMG]]("http://ubuntuforums.org/showthread.php?p=12997801#post12997801")[/COLOR]
[COLOR=#000000][I]Try to install ubuntu-session package as suggested on [http://osdir.com/ml/ubuntu-bugs/2014-04/msg13063.html](http://osdir.com/ml/ubuntu-bugs/2014-04/msg13063.html)
Code:
sudo apt-get install ubuntu-session
If it is installed try to reinstall it with:
Code:
sudo apt-get install --reinstall ubuntu-session
[/I][/COLOR]

---

### Post by mmercado on 2015-08-06
None of these options worked for me. In case it helps someone, what I did was I downgraded my NVIDIA graphics package and it worked. It is strange that this solved the issue because I could see the login screen and for a second my custom background before it would go back to the login screen.

---

