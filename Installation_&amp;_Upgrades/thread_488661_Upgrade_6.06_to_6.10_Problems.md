---
title: "Upgrade 6.06 to 6.10 Problems"
date: 2007-06-30
forum: Installation &amp; Upgrades
---

### Post by kencoburn on 2007-06-30
I used the gksu "update-manager -c" route to update Ubunto 6.60 to 6.10 and got the following error message:

Failed to fetch [http://givre.cabspace.com/ubuntu/dists/dapper/Release.gpg](http://givre.cabspace.com/ubuntu/dists/dapper/Release.gpg) Could not connect to givre.cabspace.com:80 (65.175.85.100), connection timed out

I have tried a number of times and each time I get this time-out message.  Any advice please.:(

---

### Post by nickbooker on 2007-06-30
Sounds like your selected Ubuntu mirror isn't working properly.  I tried to access that URL and I got no response either.  Try selecting a different mirror from the Software Sources utility and try again.

---

### Post by kencoburn on 2007-07-01
Thanks - I got rid of one of the repository entries and that stopped the error.  However, I now have an even greater problem.  The update from 6.06 to 6.10 seemed to go okay (took about an hour) but the /boot/grub/menu.1st file was changed and I can only boot into Linux now.  I have lost the capability of booting into Windows XP - even after using the 'Repair Installation" option from my Window XP Pro installation disc.

Can anyone tell me what modification I need to make to the menu.1st file to get back into Windows?

---

