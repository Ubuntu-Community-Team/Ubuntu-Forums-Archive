---
title: "using windows 7, trying to install kubuntu 14.04"
date: 2014-04-22
forum: Installation &amp; Upgrades
---

### Post by taylorpIII on 2014-04-22
i'm using windows 7 and instead of upgrading to windows 8, i would rather use kubuntu 14.04.  

during the latter part of the installation i've been getting an error message:
 
"could not retrieve the required installation files"

then it said check rev286.log

is it wubi.exe?  i read somewhere that wubi is no longer compatible with windows 7.

if that's the case then how do i make this installation happen?  

thx and i hope you can help.

-paul

---

### Post by SeijiSensei on 2014-04-22
WUBI is deprecated I believe.  If you want to run Ubuntu on top of Windows 7, your best bet is to install [VirtualBox]("http://www.virtualbox.org/") in Windows.  That will let you create a "virtual machine" into which you can install Kubuntu. Choose the version that matches your machine's architecture from [here](https://www.virtualbox.org/wiki/Downloads).  Make sure to install the Extension Pack listed on that page as well.

---

### Post by oldfred on 2014-04-22
I believe wubi still exists on installer, but last supported version is 12.04. Not even sure kubuntu has wubi still.

Most Windows 7 systems have used all 4 primary partitions, so you may have to backup & delete one primary so you can make an extended partition. The extended partition then can hold as many logical partitions as you want or need.
       My laptop already has 4 primary partitions: how can I install Ubuntu?
[http://askubuntu.com/questions/149821/my-laptop-already-has-4-primary-partitions-how-can-i-install-ubuntu](http://askubuntu.com/questions/149821/my-laptop-already-has-4-primary-partitions-how-can-i-install-ubuntu)
Good advice on how to handle all four primary partitions used. - srs5694
[http://ubuntuforums.org/showthread.php?t=1686440](http://ubuntuforums.org/showthread.php?t=1686440)
Be sure to create recovery DVD(s) first. And a Windows repair CD.
HP tools partition discussion - similar for other vendor utility partitions:
[http://h30434.www3.hp.com/t5/Notebook-Hardware/Hp-Tools-Partion/td-p/228360](http://h30434.www3.hp.com/t5/Notebook-Hardware/Hp-Tools-Partion/td-p/228360)

---

### Post by taylorpIII on 2014-04-22
Thx.  I'm going to try these ideas and see what happens.

---

### Post by taylorpIII on 2014-04-23
One more question for you boss.  i downloaded the virtualbox and loaded kubuntu 14.04.  the installation seemed to be okay.  at the end of the installation, a message appeared that said: "reboot to use kubuntu".  when i hit the reboot button another message appears saying: "virtualbox has stopped working"  "debug or close program".  

when i chose close program, i have to do the installation all over again from the beginning.  this has happened twice.  any thoughts?

thx!

-paul

---

