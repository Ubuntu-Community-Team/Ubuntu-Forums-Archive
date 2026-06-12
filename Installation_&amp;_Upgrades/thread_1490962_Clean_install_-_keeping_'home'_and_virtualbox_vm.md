---
title: "Clean install - keeping 'home' and virtualbox vm"
date: 2010-05-23
forum: Installation &amp; Upgrades
---

### Post by rossnixon on 2010-05-23
What do I need to do?
Am going to boot of my 10.04 CD to do a fresh install, replacing 9.04.
- how do I specify that I want to use my old 'home' partition as my new one?
- will my VM work as before, once I reinstall VirtualBox?
- are there any other folders or files that I should copy to a safe place first?

- I just use IMAP for mail, so nothing to save there I think.
- Firefox bookmarks are saved on XMarks

Thanks.

---

### Post by rossnixon on 2010-05-24
If my questions are too hard, I'll find another forum; or see if I can get into IRC.

---

### Post by binary10 on 2010-05-24
No no, your questions are not 'too hard' at all.

What you are suggesting to do was exactly what I did.

Though I did do a few things before hand.

- made sure that I was using separate / /boot /usr /var /home partitions
- take a good backup of /home (in fact I made sure I had a bootable backup :) so that I could always carry on working )
- choose manual for which disk layout you want, and over format your / /boot /usr /var partitions, specify what is to be mounted where, I use LVM so it's easy to see which should be on / , /usr , /var /home etc (don't format HOME ! )
- choose the same password for your account (otherwise you'll get prompted for keys etc on login)

- Yes your Virtual box VMs will work (after you install), again this is what I did.
- Yes firefox bookmarks worked.
- If you use mysql, then make sure you make an export backup of the databases.


The only problems I had were 

 gconf configuration error message on login, because I found my gnucash had placed a reference to /usr/local.. in my .gconf.path file.

 my customised old 9.04 layout and icons etc weren't as good as new 10.04 account, I just renamed my .gconf/desktop to .gconf/desktop.old and let it re-create new ones.

To add more confidence for you. I went from 9.04 (32-bit) to 10.04 (64-bit) and stuck with the same /home.

Of course, everyone is different :)

---

### Post by rossnixon on 2010-05-31
Finally did the install. Didn't bother backing up /home.
All went fine.
- VirtualBox reinstalled fine and found my VMs.
- Evolution still had my email accounts.
- Can't get Java working in Firefox 3.6.3, but not sure if it did before or not. Might have to look for a .deb instead of running a .bin.

---

