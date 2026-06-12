---
title: "after installing upgrades I am locked out of edgy"
date: 2007-07-19
forum: Installation &amp; Upgrades
---

### Post by campobello on 2007-07-19
I will read the other posts but will state my problem first. Yesterday july 18  was advised by the update manager to install 13 updates. It seems that the Linux Headers Files ...16? could not be installed. I recieved a message stating that disk space was zero or 100%, something along those lines. I ran "sudo apt-get install -f" as instructed. After being instructed to restart the computer I entered my username and password only to be returned to the same set of screens. I tried changing sessions but to no avail. The result was that the only way I could log in was in a recovery mode from the grub loader.Not knowing my way around the terminal I could not make any real headway here except to be notified that my pnpBios needed an upgrade. And that I could not install or remove any software, somehow related to "x authourization." I am running edgy eft on a 750 celeron with 256m ram, and two 13g harddrives. It is aold system but has been running flawlessly with the eft since january 2007. A possible related problem is my inability to upgrade to 704 over the internet, I recieve a message that the temporary download folder is full. I have used "sudo apt-get clean" to empty the cache file but have not been able to make the temporary folder larger. Could the two problems be related. Thankyou for reading this and I hope it makes sense to someone, I would hate to return to xp you have produced a wonderful product.

---

### Post by scrooge_74 on 2007-07-19
looks like your disks are full

log in again and type df

that should tell you how much space there is

go to your /home/user/.Trash/ folder and empty it

do sudo apt-get autoremove to make some space

go to /var/log and get rid of all the .gz, log.* files and things like that

---

