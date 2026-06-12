---
title: "You are not authorized to perform this action"
date: 2009-12-17
forum: Installation &amp; Upgrades
---

### Post by cigtoxdoc on 2009-12-17
I just installed a new video card.  I checked to see if it wanted a special hardware driver.  My pc is calling for NVIDIA accelerated graphics driver (version 173) [recommended].

When I go to activate this driver, Ubuntu 9.10 tells me,"You are not authorized to perform this action."

This is MY PC.  I am the ONLY user.  Why does Ubuntu give such nonsense?

What do i need to do?????  All my user and group settings are greyed-out so I cannot change my own PC.

What gives???  What do I need to do to fix it?  I can get to ROOT through a terminal window.

john

---

### Post by itang sanjana on 2009-12-17
Hello, I hope this could help you fix the problem.
[http://ubuntuforums.org/showthread.php?p=8377782](http://ubuntuforums.org/showthread.php?p=8377782)

---

### Post by cigtoxdoc on 2009-12-17
john@john-desktop:~$ sudo apt-get dist-upgrade
[sudo] password for john: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages have been kept back:
  adobe-flashplugin
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
john@john-desktop:~$ 

As you can see, this did not do anything. i still get same error message.

Also, I still cannot manage users and groups

---

### Post by darkod on 2009-12-17
When you say you're the only user that doesn't mean there was another firs user, you then created your user, and deleted the previous one? I am just asking because the first user would have admin privileges by default which is not the case with subsequent users.
Also, this might mean corrupted sudoers file (the file keeping the sudo permissions). Take a look here at the bottom, Default Sudoers File:
[https://help.ubuntu.com/community/Sudoers](https://help.ubuntu.com/community/Sudoers)

I'm not sure what else to recommend.

---

### Post by cigtoxdoc on 2009-12-17
I solved this one myself by shear luck.

Ubuntu 9.10 lets you log into gdm as root.  Once I was in as ROOT, i could make the video driver upgrade. ALSO, I checked users and groups.  Yes, I had set myself up with all the permissions as i thought i had.  However, even though I gave myself permission to administer the system, i still CANNOT do users and groups with my normal login.

john

---

### Post by oldos2er on 2009-12-17
Which new Nvidia card did you get? It seems odd to me that the system would recommend older drivers (v173) for a new card.

---

### Post by cigtoxdoc on 2009-12-17
Video card is NV34 [GeForce FX 5200].  I had a board fail on a legacy system.

John

---

### Post by linuxford on 2010-04-01
> **cigtoxdoc said:**
> I solved this one myself by shear luck.

Ubuntu 9.10 lets you log into gdm as root.  Once I was in as ROOT, i could make the video driver upgrade. ALSO, I checked users and groups.  Yes, I had set myself up with all the permissions as i thought i had.  However, even though I gave myself permission to administer the system, i still CANNOT do users and groups with my normal login.

john

Thanks. I had the same exact problem, and your solution worked beautiful.

---

### Post by jeSah8ci on 2010-04-18
> **linuxford said:**
> Thanks. I had the same exact problem, and your solution worked beautiful.

Another solution is to try the following commands:

```
sudo su
/usr/bin/jockey-gtk
```

That should allow you to install the drivers.

---

### Post by derek1234 on 2010-05-23
I have the same problems. I have not figured out the solution, but I may be able to shed some light on what caused it. 

In my case I re-installed 9.10 and used the same user name and password for the primary user. This allowed me to pull in all my settings because I set up the /home directory on a separate partition which was not formatted (this worked fine on previous versions). 

Ever since then I have been unable to perform certain administrative functions for which the root credentials are automatically entered, e.g. Ubuntu Software Center, Users and Groups, and installing the Nvidia drivers to name a few. 

Also, I recently upgraded to 10.04. I thought I could solve the problem by doing a fresh install and ignoring my old settings. So I booted from the CD and changed the name of the primary user in the home folder from derek to derek01. Well Ubuntu is getting too smart because somehow it still pulled in all my old settings. 

So with this new information, does anyone have any suggestions on how to resolve this issue?

---

### Post by derek1234 on 2010-05-26
I solved my problem. I was logging into a Gnome Fail-safe session. Once I changed to a standard Gnome session, everything started working.

---

### Post by pombe on 2010-07-06
> **derek1234 said:**
> I solved my problem. I was logging into a Gnome Fail-safe session. Once I changed to a standard Gnome session, everything started working.

^^^ This ^^^

Just managed to do the same thing to myself...  And now everything works again...  \\:D/

---

