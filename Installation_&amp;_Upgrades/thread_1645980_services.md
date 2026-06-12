---
title: "services"
date: 2010-12-15
forum: Installation &amp; Upgrades
---

### Post by sureshk89 on 2010-12-15
Hi
I am new to ubuntu. I would like to know how to start or stop services and look what services are running.
In terminal i tryed to stop its working,but to list the services is there any command.
There is no services option in my 
System-->administration-->.....
I have all other options other than service.
Should i install any packages for that.

Regards
suresh

---

### Post by ajgreeny on 2010-12-15
The command ```
ps aux >ps.txt
```will produce a txt file in your home called **ps.txt** listing all processes running.  Some of these are the "services" you ask about, but some are applications, so you may not get exactly what you want from that list.

You can also look at bum from the repos (bootup manager) which allows you to stop some things starting at boot, but not all, and the list is getting shorter.

Some services can be started and stopped with ```
sudo service  <name> stop
```(or "start" at the end), but some are still  started and stopped with a shell script in /etc/init.d, so there is no  simple answer to your question, as far as I'm aware.

---

### Post by Rubi1200 on 2010-12-15
For services controlled by [upstart]("http://upstart.ubuntu.com/index.html"), you can use this command to see what is running:
```
initctl list

```
For other services, as ajgreeny said, they still use the old style System-V init scripts in /etc/init.d

---

### Post by sisco311 on 2010-12-15
> **sureshk89 said:**
> 
Should i install any packages for that.


In Ubuntu 10.10 (Maverick) you can install [jobs-admin]("apt://jobs-admin").

---

### Post by Rubi1200 on 2010-12-15
> **sisco311 said:**
> In Ubuntu 10.10 (Maverick) you can install [jobs-admin]("apt://jobs-admin").
Is there currently something similar for 10.04?

Thanks.

Oh, by the way, even though I thanked you before I want to say it again. My friend was so pleased with the script you put together :-)

---

### Post by sisco311 on 2010-12-15
> **Rubi1200 said:**
> Is there currently something similar for 10.04?

Thanks.


Yes, there is a PPA maintained by [[color=red]jpeddicord[/color]]("http://ubuntuforums.org/member.php?u=90021") from where you can install jobs-admin:
[https://launchpad.net/~jpeddicord/+archive/jobs](https://launchpad.net/~jpeddicord/+archive/jobs)


 
> **Rubi1200 said:**
> 
Oh, by the way, even though I thanked you before I want to say it again. My friend was so pleased with the script you put together :-)

Cool!

---

### Post by Rubi1200 on 2010-12-15
Thank you :D

---

### Post by flyingbear on 2010-12-15
With **chkconfig** you can easily manipulate your start up scripts. Other nice tool is **top**. This is a console system monitor for all your processes.

---

