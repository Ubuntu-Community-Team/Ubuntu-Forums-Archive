---
title: "How to install the new update"
date: 2006-08-11
forum: Installation &amp; Upgrades
---

### Post by okok on 2006-08-11
A couple of days ago a new update to Ubuntu was announced, but I saw no instructions on how to install it on machines running 6.06 (is it just because I don't know where to look for such things?).

Do I just burn the CD, run it and hope it updates my system without causing any damage?

---

### Post by bonjun on 2006-08-11
if you have internet connection you can run from terminal:

> sudo apt-get update && sudo apt-get upgrade

or run 

> synaptic

---

### Post by A2A on 2006-08-11
Hi okok, and welcome to the forums.

Do NOT burn the CD and install anything.  Typically the update icon shows up on the top right side of your screen, once you click on it, it will start the update process and take care of itself.

On the other hand, you could update the system manually.

System -> Administration -> Update Manager  You will have to enter your password to proceed.

Could you type the following code in the terminal window and paste the output here as well?
```
lsb_release -a
``` This will tell you what version of ununtu you are running.

Let us know how it all works out for you.

Regards,

---

### Post by okok on 2006-08-11
Thank you both. According to System Update, my system Is up to date, although I do not recall downloading any substative amount of updates in the last couple of days.

Is the newly announced version (6.06.1) made just of a cummulative set of updates that should already be intalled on my system if I check for updates regularly?

---

### Post by A2A on 2006-08-11
Yup, if you make updates from time to time, your system will reflect all of them and there is no need to install the new CD.

I put some code in the post above, can you please execute that and paste the output here?

Regards,

---

### Post by okok on 2006-08-11
what I get in response to [FONT="Fixedsys"]sb_release -a[/FONT]  is:

command not found

---

### Post by A2A on 2006-08-11
you're missing the lower case "L"

lsb_release -a
Cheers!

---

### Post by okok on 2006-08-11
Oh, sorry. Well, I am new to linux. I still don't know even many basic commands.. the output is:

No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 6.06.1 LTS
Release:        6.06
Codename:       dapper

So I indeed have the current version.  But what does "No LSB modules are available" mean?

---

### Post by A2A on 2006-08-11
LSB is Linux Standard Base.  You can read more about it here:
[http://en.wikipedia.org/wiki/Linux_Standard_Base](http://en.wikipedia.org/wiki/Linux_Standard_Base)
There is nothing to worry about if you have no LSB Modules :-)
Regards,

---

### Post by okok on 2006-08-11
Thanks you very much for your help and explanations!

---

