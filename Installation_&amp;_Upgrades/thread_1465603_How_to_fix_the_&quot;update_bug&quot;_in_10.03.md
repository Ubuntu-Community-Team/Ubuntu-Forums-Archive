---
title: "How to fix the &quot;update bug&quot; in 10.03"
date: 2010-04-29
forum: Installation &amp; Upgrades
---

### Post by Zoronian on 2010-04-29
Some users may be having a hard time using the package manager to update to 10.03 from 9.10 as of now this will freeze you're computer here is a way to update without the freeze.
Pasta copy, give it a shot.


Create an executable file which updates the sources repositories, and upgrades the system, in other words, excecute the next two commands sudo apt-get update and sudo apt-get upgrade using only one command. To do it&#8230; we only need to run the next two lines in a terminal:

   1. echo -e "sudo apt-get update && sudo apt-get upgrade" | sudo tee -a /usr/local/bin/update
   2. sudo chmod +x /usr/local/bin/update

The first one creates a file called update, located in /usr/local/bin, and writes the famous two commands in it, and the second one, gives this file permissions to be executed. From now on we can update the entire system excecuting "sudo update" (without quote marks) in a terminal.

---

### Post by lisati on 2010-04-29
Um 10.03? Do you mean 10.04?

---

### Post by Zoronian on 2010-04-29
> **lisati said:**
> Um 10.03? Do you mean 10.04?

Sorry, my mistake.

---

### Post by Exoskeletor on 2010-04-30
hi guys. i have just update 10.04 from the network from 9.10 and i cant write my login password to login. whatever i press im not seeing any dots, just like im not writing. im using linux from vmware workstation, what am i doing wrong?
i press to use onscreen keyboard and it opens and close instantly.. something must have gone wrong in the update

Also the strange is that when im typing the | is stop flashing which means it can detect input from keyboard right?

---

