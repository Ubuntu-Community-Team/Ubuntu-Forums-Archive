---
title: "The Process of Making an Image to use on University Laptops"
date: 2008-02-14
forum: Installation &amp; Upgrades
---

### Post by mlapaglia on 2008-02-14
My university requires all new students to buy laptops through the IT department when they come as freshman. We all have some version of a Compal laptop, my class has the Compal Hel80/81, divided into three variants (power, superlight, and the regular notebook).

I'm focusing on the power notebook:

15.4" lcd screen
intel core duo processor (2.0 ghz)
nvidia geforce go 7600
1 gb ram
100 gb hdd
dvd/cd burner

I have been converting quite a few people from Vista and XP over to Ubuntu. After they saw the cool visual affects their computer can do, along with virtualization of windows, people pretty much jump right on. The ease of upgrades and the quickness of the system really astounds everyone.

The only problem is: it takes forever to get Ubuntu set up right. From the drivers to compiz to configuring evolution to work with our school's lotus notes email client and address book, it takes multiple hours to get everything working smoothly.

I am making an image of a default installation once it is completely stable, has all the drivers installed, and it setup for our school. When I put this image onto a student's laptop, is there an easy way to change the: username, computer name, setting up evolution for that specific user, etc. etc?

Our IT department simply runs a script for XP that configures everything, all they type in is the users school email address and password. What's the best way to do this for Ubuntu?

Thanks for your help!

---

### Post by mlapaglia on 2008-02-14
i've been searching google for a while but haven't found much.

does anyone know how to make a script/program that will:

ask for the users name and password, then automatically go through a program (like thunderbird) and configure it to work with that user?

---

### Post by mlapaglia on 2008-02-14
found it.

[http://www.cfengine.org/](http://www.cfengine.org/)

---

### Post by mlapaglia on 2008-02-14
guess i said that too soon..

anybody have any ideas?

---

### Post by plucky on 2008-02-14
mlapaglia,

Maybe you can lookin to what OEM mode on the install CD does.!!!!

---

### Post by Whiffle on 2008-02-14
Its old, but it might point you in the right direction:
[https://help.ubuntu.com/community/InstallCDCustomization](https://help.ubuntu.com/community/InstallCDCustomization)

---

### Post by mlapaglia on 2008-02-15
well, if i did an OEM install, would that let me automatically configure thunderbird for _each_ user?

I need to set up an IMAP email address, along with a connection to our school's LDAP server to use for the address book...

I'm going to try the OEM install, to get all the video drivers and such installed and working though.

basically i'd like the user to log in, and it would have a popup asking

"whats your email address and password"

and then have a bash script go through and choose the appropriate IMAP server and LDAP string needed.

---

### Post by mlapaglia on 2008-02-15
i found [http://developer.mozilla.org/en/docs/MCD,_Mission_Control_Desktop_AKA_AutoConfig#Central_Configuration_File](http://developer.mozilla.org/en/docs/MCD,_Mission_Control_Desktop_AKA_AutoConfig#Central_Configuration_File) 
for thunderbird, will report back later

---

### Post by mlapaglia on 2008-02-20
ok i've given up on the thunderbird configuration.. it's not too hard to do by hand. i have a question about the OEM install option.

If i install compiz-fusion, conky, or envy drivers by myself (outside of synaptic), the OEM making process won't pick that up will it, or is it just for synaptic installs and what not?

---

### Post by mlapaglia on 2008-02-20
Since the laptops this is being installed on are all the same, can i:

make an oem installation, configure everything the way I want it, issue the OEM install command (to make it ask for user options the next time it boots up, and then create an image of the hard drive to use on other computers?

---

### Post by dstew on 2008-02-20
There is the [clonezilla]("http://clonezilla.sourceforge.net/") program. You could make a generic installation with a user "ubuntu" password "ubuntu", clone it, let people put it on their laptops, then add their own user account with admin privleges, then login to that account, and delete the "ubuntu" account. I have never used clonezilla though. Maybe search through the forums to find someone with hands-on experience with it.

---

