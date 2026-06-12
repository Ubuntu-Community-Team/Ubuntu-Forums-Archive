---
title: "sudo problem"
date: 2005-04-27
forum: Installation &amp; Upgrades
---

### Post by hack_benjamin on 2005-04-27
I installed 64 bit version... everything went swimmingly.
Got into the desktop opened a gnome-terminal and typed:

#sudo -u root -s

and the error read

<my user> is not in the sudoers file. This incident will be reported.

problem is i cant log into it as root (thats been turned off) so i cant edit the file to add hope to the sudoers file...?! help!
i just want to be able to change to su and do things...

cheers G

---

### Post by fordfan753 on 2005-04-27
Are you logged in using the username and password you supplied during the install?

---

### Post by hack_benjamin on 2005-04-27
indeed i am,its the only username i supplied... there is only me using this computer.

 :???:

---

### Post by fordfan753 on 2005-04-27
If you can't use sudo then you're pretty much stuffed, there's nothing I can think of to fix that short of reinstalling. You could try "$ sudo su" but that will probably return the same message.

---

### Post by hack_benjamin on 2005-04-27
Then a reinstall will do =D

(thankfully hoary picks up pcie gpu- nothing else i tried did (this includes gentoo!!!!))
cheers anywho.

---

### Post by XDevHald on 2005-04-27
Did you create a password for root? I know that when you install Ubuntu, it does give you a password, but it is scrambled. 

Only way to get the user to have a password so you can login is **System > Administration > Users and Groups**

Then select **root **click **Properties **and then you'll notice that the password is already set, you can delete the password, set a new one and select **Ok**.

Also do **su **instead of the command you tried before and then enter your password and then try the command you did before while being as root. 

I know this is a little off balance to what you're asking, but try this out and see what it does for you.

---

### Post by hack_benjamin on 2005-04-27
I just got through a new clean install- everything works great (at least the install only takes about half an hour- beats gentoo's DAYS!).

cheers

---

