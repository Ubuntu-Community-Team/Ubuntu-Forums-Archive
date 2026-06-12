---
title: "jave problems"
date: 2008-04-26
forum: Installation &amp; Upgrades
---

### Post by adiron on 2008-04-26
So I tried to install Java using 
sudo apt-get install sun-java6-bin sun-java6-fonts sun-java6-jre sun-java6-plugin

and then it brough up a screen that said whether or not I agree to java liscence. I didn't know how to continue forward because I could figure out how to click ok. So I canceled out of the screen. Now it's saying 
"dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem."
but when I try to run this in the terminal it says  
dpkg: requested operation requires superuser privilege

But I thought I already had superuser privileges.

So what do I do?

---

### Post by Pumalite on 2008-04-26
sudo dpkg --configure -a
sudo apt-get install -f
sudo apt-get update
sudo apt-get upgrade

Let me know how it goes.

---

### Post by adiron on 2008-04-26
Worked perfectly

Thanks!

---

### Post by Pumalite on 2008-04-26
You are welcome. Good luck.

---

