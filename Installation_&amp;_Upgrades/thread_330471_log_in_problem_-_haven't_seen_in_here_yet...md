---
title: "log in problem - haven't seen in here yet.."
date: 2007-01-03
forum: Installation &amp; Upgrades
---

### Post by flir48 on 2007-01-03
After I was able to install and finally view ubuntu.. I ran the
sudo oem-config-prepare

on the next reboot, it prompts for keyboard, timezone, country, and now your name.
I Fill in all fields and click forward.
Nothing Happens! - It just sits there. It's been 5 mins and nothing...

anyone know what gives?
I've read here you can create the account at the prompt... but was curious if anyone else
ran across this..

BTW... for my first time back to trying linux after 5 years.. it's not been a pleasent experience.....  and this is why it really isn't hitting mainstream.

---

### Post by bapoumba on 2007-01-03
Hello,
I've installed both dapper and edgy with alternate CDs, and recommended it to many people, and I have never seen this. Is there a "back" button to start the procedure over (I just cannot remember) ?

---

### Post by flir48 on 2007-01-03
> **bapoumba said:**
> Hello,
I've installed both dapper and edgy with alternate CDs, and recommended it to many people, and I have never seen this. Is there a "back" button to start the procedure over (I just cannot remember) ?

Yes there is, but it does nothing but start you at the begining.

I tried going to recover mode and manually add my account

useradd -g admin -p password -h /home/brett -m brett

(the useradd line above is off the top of my head, since I'm now at work)....

this command line did nothing for  me. 

I cannot log into the system at all once I removed the OEM stuff....

---

### Post by taurus on 2007-01-03
Are you using Dapper or Edgy?

When you ran that command from a terminal, "sudo oem-config-prepare", it will ask you to create a new account, NOT after you reboot!!!

---

### Post by flir48 on 2007-01-03
> **taurus said:**
> Are you using Dapper or Edgy?

When you ran that command from a terminal, "sudo oem-config-prepare", it will ask you to create a new account, NOT after you reboot!!!

I installed Edgy.. ..............**NOT** after a reboot? 
There is a post here that says do so...

so I have to reinstall then? (yet again..)

---

### Post by bapoumba on 2007-01-03
It's always asked for a new user login and password after reboot, at least to me :/
Now, you can make up a new account. Boot in recovery mode from the grub menu. You'll be root, and in text mode, so careful ;) Your prompt should have a **#** (meaning you are root). This will work if your oem user is stil up and running. If not, you'll have to do it from a live CD. Here is the procedure :

**# adduser <new_login>**
Go through the procedure, give a password (I just left blank real name and other stuff like that).
Then : 
**# adduser <new_login> admin**
**# reboot**

You should be able to login, with that new_login and you should also have root priviledge because in admin group.

---

### Post by flir48 on 2007-01-03
thank you...

I'll give it a go when I get home in a hour or so..

---

### Post by taurus on 2007-01-03
If you are using the Edgy alternate CD, pick the first option (not the second since the second option is the oem install).

---

### Post by flir48 on 2007-01-03
> **taurus said:**
> Are you using Dapper or Edgy?

When you ran that command from a terminal, "sudo oem-config-prepare", it will ask you to create a new account, NOT after you reboot!!!

Hi Taurus...
FYI... it does not ask you to create an account when doing this task....
I just did a reinstall and I can assure you..it did not prompt you at all....

But before I ran the oem-config-prepare i did....
[LIST]
[*]I reenter the root password in the user manager
[*]I created an account for myself and added myself to the admin group
[*]I had to manully create a home directory for my account
[/LIST]

Now when I rebooted, the prompts as before appears, but this time I entered my wifes Info and everything worked...

thanks for you valued input...

now I'm off to learn about how to do basic shell commands and get windows programs to run for those I need to do.....
Games,  NTDomain Admin.. PcAnywhere, Lotus , etc...

if you care to share a tip.....I'd appreciate it.

---

