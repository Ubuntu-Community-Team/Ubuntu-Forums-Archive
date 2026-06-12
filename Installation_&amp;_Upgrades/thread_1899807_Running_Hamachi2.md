---
title: "Running Hamachi2"
date: 2011-12-24
forum: Installation &amp; Upgrades
---

### Post by drklunk on 2011-12-24
Alright, Im trying to run Haguichi by following this guide here: [http://www.webupd8.org/2010/10/install-hamachi2-and-haguichi-gui-for.html](http://www.webupd8.org/2010/10/install-hamachi2-and-haguichi-gui-for.html)

My issue is when I try to connect using Haguichi it cannot connect through Hamachi. When I open it and click connect, it goes through the attempt and ends in disconnect. PLEASE HELP

This is the output of the installation:
> william@HAL:~/Source$ sudo dpkg -i logmein-hamachi_2.1.0.17-1_i386.deb
(Reading database ... 177495 files and directories currently installed.)
Preparing to replace logmein-hamachi 2.1.0.17-1 (using logmein-hamachi_2.1.0.17-1_i386.deb) ...
Stopping LogMeIn Hamachi VPN tunneling engine logmein-hamachi * 
 Removing any system startup links for /etc/init.d/logmein-hamachi ...
   /etc/rc0.d/K49logmein-hamachi
   /etc/rc1.d/K49logmein-hamachi
   /etc/rc2.d/S11logmein-hamachi
   /etc/rc3.d/S11logmein-hamachi
   /etc/rc4.d/S11logmein-hamachi
   /etc/rc5.d/S11logmein-hamachi
   /etc/rc6.d/K49logmein-hamachi
Unpacking replacement logmein-hamachi ...
Setting up logmein-hamachi (2.1.0.17-1) ...
 Adding system startup for /etc/init.d/logmein-hamachi ...
   /etc/rc0.d/K49logmein-hamachi -> ../init.d/logmein-hamachi
   /etc/rc1.d/K49logmein-hamachi -> ../init.d/logmein-hamachi
   /etc/rc6.d/K49logmein-hamachi -> ../init.d/logmein-hamachi
   /etc/rc2.d/S11logmein-hamachi -> ../init.d/logmein-hamachi
   /etc/rc3.d/S11logmein-hamachi -> ../init.d/logmein-hamachi
   /etc/rc4.d/S11logmein-hamachi -> ../init.d/logmein-hamachi
   /etc/rc5.d/S11logmein-hamachi -> ../init.d/logmein-hamachi
Starting LogMeIn Hamachi VPN tunneling engine logmein-hamachi * 

Processing triggers for ureadahead ...
william@HAL:~/Source$


---

### Post by drklunk on 2011-12-25
I have Haguichi installed and running, I also have Hamachi installed (I think), but I need help figuring out why Hamachi wont allow Haguichi to connect.

---

### Post by drklunk on 2011-12-26
Seriously, this has to be easy to fix, all I need is a little guidance. I really need to get this going

---

### Post by Stayfun on 2012-01-02
What's the response when you run **hamachi login** from the terminal?

---

