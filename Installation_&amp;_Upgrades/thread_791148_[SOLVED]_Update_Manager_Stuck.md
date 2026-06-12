---
title: "[SOLVED] Update Manager Stuck"
date: 2008-05-11
forum: Installation &amp; Upgrades
---

### Post by DocHoliday52090 on 2008-05-11
I've been using Hardy since before release, and have been enjoying update after update with no problems.

Now, however, update manager seems to do nothing after I tell it to install updates, stuck right after the phase I click 'Install'.

I have to manually kill the process. What can I do?

EDIT: Synaptic doesn't start either
EDIT2: Something's wrong with Sudo too:

DocHoliday@laptop:~$ sudo 
sudo: unable to resolve host laptop


FIXED: Some more googling found the solution. 

Here's how to fix:


**HOW TO**

1.) Start Terminal
2.) Enter "sudo gedit /etc/hosts" - ignore the sudo error and enter password
3.) When in gedit, find the second line:

127.0.1.1 [name of your computer][COLOR="Red"].[name of your workgroup/domain]
[/COLOR]

Simply delete the .workgroup (that is, everything that's red in the example above) and save. Exit out of gedit. 

Fixed.

---

### Post by NIT006.5 on 2008-05-12
In my case, it would kick out after the error so I couldn't use sudo to edit /etc/hosts and I couldn't use sudo to set the root password. You can however, manually make the change in network properties. Thanks for the above solution.

---

### Post by gene spiller on 2008-05-12
Thanks, this actually got me going.  It's important to note, though, that you have to remove "WORKGROUP" both in the Domain Name field under the General tab and in the computer name under the Hosts tab.  (In the Hosts tab, make sure to also remove the leading dot.)

---

### Post by SIlvio77 on 2008-05-14
Hey there, it seems i've got the same problem. I've tried pretty much everything mentionned above. I've tried removing the "workgroup" in domain, but there is no domain name. When I try the other command lines in the terminal it tells unable to find host.
I also cannot install updates anymore or remove any installed software. I tried to uninstall Samba and the system just froze.
I was thinking of re-installing but that would really tick me off since the machine runs the office server.
Any suggestions?

thanx

---

### Post by SIlvio77 on 2008-05-15
ok sorted i just had to add my username as local host in the network settings.

---

### Post by VALDOR on 2008-06-21
Sudo does not work so i could not do it in terminal,,,, but it worked when i edit the hosts in network settings,,  Thanks


// sorry for grammar i dont speak en //

---

### Post by Biased turkey on 2008-06-22
Thanks a lot DocHoliday52090 for that valuable information.
Now I can install all the updates ( 150 + ).
I would like to know why removing the group from the /etc/hosts solved the problem ? I never thought that etc/hosts could have such a big influence on the Update Manager.
Ah the mysteries of Linux :)
Is the bug fixed in "Update Manager" now ? Ca I reedit my etc/hosts file and add my workgroup ?

Jacques

---

### Post by redcow on 2008-06-25
Thank you Doc. I had 163 Updates. And all the update manager would do was turn grey and make me reboot, without any updates taking place.

---

