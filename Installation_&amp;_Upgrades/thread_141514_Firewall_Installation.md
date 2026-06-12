---
title: "Firewall Installation"
date: 2006-03-08
forum: Installation &amp; Upgrades
---

### Post by Slurm on 2006-03-08
Hello,

I recently installed Ubuntu and it is running very well on my system.  In my haste to get it on my computer (and the fact that I did not have internet at home at the time), I skipped the procedure to set up my firewall during installation.  NOW, I will be going online at home at the end of the month.  I am trying to find how to install the firewall but it does not seem to exist.  I guess I need to go back to the CD and load that module it into the system.  Can anyone tell me how does one do that?  I am thinking that it will be a simple setup after that. 

Thanks,

SLURM

---

### Post by munga_bill on 2006-03-08
Yes, it's a lot simpler than you think, in fact, you already have the best firewall automatically built right in to Ubuntu already but you don't even know it! Don't worry about it, Ubuntu is all sealed up tight as a nut, it's just that the firewall doesn't annoy the heck out of us with alerts every two or three minutes. That doesn't mean it's not there working. It's a silent one. Relax! If you don't believe me, as soon as you get on-line try going to a firewall testing site like Shields Up! or Sygate and I'll bet Ubuntu will pass every test you can subject it to! (Click links below) [https://www.grc.com/x/ne.dll?bh0bkyd2]("https://www.grc.com/x/ne.dll?bh0bkyd2")[http://scan.sygatetech.com]("http://scan.sygatetech.com")

---

### Post by Slurm on 2006-03-08
Munga_bill,

Thanks for the information.  The 3rd edition of "Linux Firewalls" is out.  I am still a little curious as to how a firewall works and how to harden a system more.  Would you recommend this book or is there another book that you found  useful.

Slurm

---

### Post by munga_bill on 2006-03-08
[http://www.seifried.org/security/index.php/Linux_Firewalling_Overview](http://www.seifried.org/security/index.php/Linux_Firewalling_Overview)

[http://www.seifried.org/security/index.php/Linux_Security](http://www.seifried.org/security/index.php/Linux_Security)

Regards, munga_bill

Edit: One easy step you can take to improve security is to open your /home/slurm folder and go up one level (to /home), and right-click on your /home/slurm folder, click 'properties'. In 'properties' click permissions, and uncheck (clear) all checkboxes for read, write and execute except the for owner (you).

---

