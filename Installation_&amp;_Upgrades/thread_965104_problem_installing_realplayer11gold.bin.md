---
title: "problem installing realplayer11gold.bin"
date: 2008-10-31
forum: Installation &amp; Upgrades
---

### Post by Jim156 on 2008-10-31
Hi guyz! I am new to Ubuntu as I installed 8.04 only a week ago!
I download RealPlayer11GOLD.bin. I used "chmod a+x RealPlayer11GOLD.bin" to make it executable and it worked. But, when I type "./RealPlayer11GOLD.bin" i get: "bash: ./RealPlayer11GOLD.bin: No such file or directory".

Any suggestions??!

---

### Post by oldos2er on 2008-10-31
What directory did you download it to? You need to "cd" to the proper directory in terminal before running "sudo ./RealPlayer11GOLD.bin"

---

### Post by ario on 2009-06-09
Hi everyone
I tried to cd to correct directory of realplayer an typed:
```

ario@ario-desktop:~$ sudo su
[sudo] password for ario:
root@ario-desktop:/home/ario# **cd Desktop**
root@ario-desktop:/home/ario/Desktop# **sh RealPlayer11GOLD.bin**
RealPlayer11GOLD.bin: 6: &#65533;4&#65533;~4: not found
RealPlayer11GOLD.bin: 6: ELF: not found
RealPlayer11GOLD.bin: 7: **Syntax error: word unexpected (expecting ")")**
root@ario-desktop:/home/ario/Desktop# 
root@ario-desktop:/home/ario/Desktop# 

```
And as you see it gave me above error message. Any Suggestions?
Thanks for your attention guides.


---------------------------------------
But i tried to type:
```

./RealPlayer11GOLD.bin

```
instead of placing a "sh" before main command and it worked like a charm:D so it solved for me!

---

### Post by xmaicox on 2009-10-08
Do this steps:

1.) sudo chmod 777 RealPlayer11GOLD.bin "Enter password if asked..."
2.) sudo ./RealPlayer11GOLD.bin 

Note: The installation is in a terminal wizard so just follow the instructions.. It might look like something like this:

"Welcome to the RealPlayer (11.0.1.1056) Setup for UNIX
Setup will help you get RealPlayer running on your computer.
Press [Enter] to continue..."

After this your RealPlayer11 will show up in Applications>Sound&Video

---

