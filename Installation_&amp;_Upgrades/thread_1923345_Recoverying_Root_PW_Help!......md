---
title: "Recoverying Root PW Help!....."
date: 2012-02-10
forum: Installation &amp; Upgrades
---

### Post by VcDeveloper on 2012-02-10
I know this is a sensitive task to discuss on a forum, but I just spent hours installing Ubuntu Studio 10.04 LTS all night and when I entered the password a missed type it somehow.  I discovered this when doing a sudo command to install Aegir Hosting System.

I'm still logged as my install user, so other than re-installing all over again, is there a way to recover or reset it?

Argh! I stayed up until 2am................

---

### Post by oldos2er on 2012-02-10
The root account is locked in Ubuntu. [http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)

---

### Post by collisionystm on 2012-02-10
> **VcDeveloper said:**
> I know this is a sensitive task to discuss on a forum, but I just spent hours installing Ubuntu Studio 10.04 LTS all night and when I entered the password a missed type it somehow.  I discovered this when doing a sudo command to install Aegir Hosting System.

I'm still logged as my install user, so other than re-installing all over again, is there a way to recover or reset it?

Argh! I stayed up until 2am................

if your sudo passwd is not working and you need a reset

reboot computer

hold the shift key down

at the grub menu select RECOVERY MODE

choose the option to mount the file system

select option to go to root command line

type

passwd YOURUSERNAME  and hit enter

re enter your passcode

type reboot and hit enter

try it out

---

### Post by VcDeveloper on 2012-02-10
Thanks for your help! I don't exactly would I did, but after I logged out I was able to log in with the password I created during installation.  There seems to be a problem when I past text from the internet into the CLI, I now first paste into a Text Editor and everything is fine.

Didn't have a problem like this in Ubuntu 10.04 LTS,  I also tested UbuntuStudio 11.10 and had the same problem and that is why I went to 10.04, now I will see if this occurs in 10.10.

Thanks Again!...

---

### Post by collisionystm on 2012-02-10
> **VcDeveloper said:**
> Thanks for your help! I don't exactly would I did, but after I logged out I was able to log in with the password I created during installation.  There seems to be a problem when I past text from the internet into the CLI, I now first paste into a Text Editor and everything is fine.

Didn't have a problem like this in Ubuntu 10.04 LTS,  I also tested UbuntuStudio 11.10 and had the same problem and that is why I went to 10.04, now I will see if this occurs in 10.10.

Thanks Again!...


Pasting text from the internet can include hidden HTML

when you paste into a text editor you are essentially clearing out the hidden html and leaving plain text. You may also be including a space in your pasted password

---

### Post by VcDeveloper on 2012-02-10
Hi, well. instead I installed the original Ubuntu 11.04 because having problem successfully installing Aegir.  But, still having problems with this one paste in from the Aegir instruction.  Can you tell me why this command is causing me to be unsuccessful in logging in sudo?

sudo echo "deb [http://debian.aegirproject.org](http://debian.aegirproject.org) stable main" | sudo tee -a /etc/apt/sources.list.d/aegir-stable.list

I should be able to just add this to my package source like this "deb [http://debian.aegirproject.org](http://debian.aegirproject.org) stable main" in the "Settings"|"Software Sources" and no need for the second command?

---

### Post by collisionystm on 2012-02-11
> **VcDeveloper said:**
> Hi, well. instead I installed the original Ubuntu 11.04 because having problem successfully installing Aegir.  But, still having problems with this one paste in from the Aegir instruction.  Can you tell me why this command is causing me to be unsuccessful in logging in sudo?

sudo echo "deb [http://debian.aegirproject.org](http://debian.aegirproject.org) stable main" | sudo tee -a /etc/apt/sources.list.d/aegir-stable.list

I should be able to just add this to my package source like this "deb [http://debian.aegirproject.org](http://debian.aegirproject.org) stable main" in the "Settings"|"Software Sources" and no need for the second command?

Thats correct. You dont need the 2nd line.

---

### Post by Cookieh on 2012-02-11
Try at your installation account go to gksudo nautilus and go to user permission folder/file, I think there it has some code which you would need to edit to get rid of password.

---

### Post by VcDeveloper on 2012-02-11
Thanks for your help, I appreciate it very much! I added the command and now I'm up and running with Aegir!  Know its time to have to some! :)

---

