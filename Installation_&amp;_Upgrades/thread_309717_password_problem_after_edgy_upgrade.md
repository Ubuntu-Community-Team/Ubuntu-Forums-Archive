---
title: "password problem after edgy upgrade"
date: 2006-11-30
forum: Installation &amp; Upgrades
---

### Post by jabberwoki on 2006-11-30
Well... after much work managed to upgrade to edgy unfortunatly I used the unofficial method of editing the sources.list, The only problem left though I think is that I cant open a package as root say synaptic when I enter the root password It says "password incorrect" as it does with the user account password. I'm lost with this one have no ideas I tried password root to change4 the password but it still does not recognise it. please help](*,) any help is much appreciated. Lovin Ubuntu though.

P.S I am running kubuntu but also have xubuntu-desktop installed which runs gnome and works good... just checked though and I have same problem opening synaptic there too.

---

### Post by bapoumba on 2006-11-30
Hi,
could you post the output of **groups** ?

---

### Post by jabberwoki on 2006-11-30
thanks for the reply,
I issued command groups root and groups ryan got the following
root : root   ryan : ryan

dont know how to get a full list of groups

this is a message in "user management" -  
"the module user management could not be loaded

The diagnostics is:
Possible reasons
  [LIST]
[*]An error occured during your last KDE upgrade leaving an orphaned control module
[*]You have old third party modules lying around
[/LIST]

Check these points carefully and try to remove the module mentioned in the error message. If this fails consider contacting your distributer packager."

Should I really remove the control module?
How do I do that on the command line?

---

### Post by bapoumba on 2006-11-30
Well, if ryan is the first user created upon installing Ubuntu, it should be in the admin group to be allowed to use sudo. ryan should also be in :

adm dialout cdrom floppy audio dip video plugdev lpadmin scanner
(this is my groups output, running on edgy, no modifications after upgrade).

You will have to check your /etc/sudoers file. It should look like :
> # Defaults
Defaults        !lecture,tty_tickets,!fqdn

# User privilege specification
root    ALL=(ALL) ALL

# Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL


As you do not have root access, you have to reboot in recovery session (second line in grub menu). Be carefull, you will be root (# prompt). Then :
**# cat /etc/sudoers**

Make sure your sudoers file is OK (there is some other commented stuff above the lines I quoted).
[B]add ryan admin
reboot[/B]

Then log back into your session, you should be fine.

Now, if the sudoers file is different, you will have to edit it with visudo. Please read **man visudo** and **man sudoers** ans add yourself in the admin group.

---

### Post by jabberwoki on 2006-12-01
Thanks for your help but I just cant get it to work, AFAIK ryan is a member of group admin, I think there is just a problem with the packages you see I can su as root on the command line and also run apps from there its just if I try alt+f2 to run an app as root or select synaptic(example) from the kmenu then my password is rejected "failed to make su conversion" is the error I think.

Well I intend to download xubuntu edgy and install kubuntu-desktop as a secondary desktop environmrent, as much as I want to learn the intricacies of linux It is just taking to much time to fix this install and I want to get on with tweaking it for my friend Ryan who is dying to try out his new Linux machine!

Thanks for all your help with this

---

### Post by bapoumba on 2006-12-01
Okay. From your previous post, it was not obvious that ryan was in the admin group ;)

Then check :
[B]ls -la .X*
ls -la .ICE*[/B]

Ryan should be the owner of .Xauthority and .ICEauthority.

---

### Post by benteveo on 2007-01-25
Hi jabberwoki

"password incorrect" error on a correct password is likely to be caused by bad permissions on  **/usr/bin/kcheckpass**. The correct perms are:

> -rwsr-xr-x 1 root root 11604 Dec  6 23:39 /usr/bin/kcheckpass

If you don't have the setuid-bit set ('s' after the first 'rw') you may fix it this way:

   $ sudo chmod u+s /usr/bin/kcheckpass

This may solve your synaptic won't start and bad-password problems.

---

