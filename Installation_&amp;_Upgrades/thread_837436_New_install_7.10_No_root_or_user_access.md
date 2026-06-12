---
title: "New install 7.10 No root or user access"
date: 2008-06-22
forum: Installation &amp; Upgrades
---

### Post by jerry7 on 2008-06-22
I installed 7.10 as the only os on a master hd.  Later I installed on the slave hd to see if the problem would go away.  I can log in only as "ubuntu" password: "ubuntu".  I was asked for a name and password prior to the install.  I used different names and passwords on each of the installs.  Neither of the names and passwords will get me in as a user, and neither of the passwords will allow me root privileges.  What am I missing here, if you would be so kind?  I have limited linux knowledge.:confused:

---

### Post by dakal on 2008-06-22
The username and password you entered during the installation should let you in. You may want to try switching caps lock, as these are both case sensitive.

Ubuntu comes with the root account disabled on a standard installation. You either have to manually assign a password to it, or use sudo.

---

### Post by jerry7 on 2008-06-22
My problem seems to be that I haven't seen any opportunity to establish a root password using the gui menu's and I haven't been able get anywhere with sudo because it always queries me for the root password, which there isn't one established.  I can't search the folders which would contain the password information because I don't have root permissions.  It seems rediculous.  I looked carefully on the second install for any place to establish a root password, but it won't even let me use the name and password I provided during the install to sign on as a user.

---

### Post by jerry7 on 2008-06-22
Thanks for your response.  I forgot to say that I was careful to have caps off for both the username and password, but I have tried to second quess the logon with dozens of variations on the theme.  With two installs it must be something else.

---

### Post by dakal on 2008-06-22
> **jerry7 said:**
> My problem seems to be that I haven't seen any opportunity to establish a root password using the gui menu's and I haven't been able get anywhere with sudo because it always queries me for the root password, which there isn't one established.

Are you positive? sudo can be configured to require the root password, but I believe all versions of Ubuntu are set to have it ask for the current user's password. 7.10 certainly does.

---

### Post by jerry7 on 2008-06-22
When I try the "ubuntu" which is the only way I can get into 7.10, I get an error message that it is incorrect.  I have tried the passwords which I created prior to (both) installs and they both result in invalid password messages.  For example i tried to have 107 available updates installed but I get hung up on the administrator password.

---

