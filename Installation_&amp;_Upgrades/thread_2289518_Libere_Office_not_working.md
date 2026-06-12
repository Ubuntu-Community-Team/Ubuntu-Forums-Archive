---
title: "Libere Office not working"
date: 2015-08-04
forum: Installation &amp; Upgrades
---

### Post by paulravin on 2015-08-04
Hi, I have just installed ubuntu 15 on an acer travel mate, when I try and open office I get this message: 

The application cannot be started. 
User installation could not be completed. 

I un installed and re installed it and am getting the same message.

Help!!!

---

### Post by paulravin on 2015-08-05
Any ideas? Install open office instead?

---

### Post by ruzekle on 2015-08-05
How are you installing it?

Make sure you also do apt-get purge after you remove it.

[http://askubuntu.com/questions/231562/what-is-the-difference-between-apt-get-purge-and-apt-get-remove](http://askubuntu.com/questions/231562/what-is-the-difference-between-apt-get-purge-and-apt-get-remove)

---

### Post by paulravin on 2015-08-06
I have been installing it with commands in terminal. Is that the best way?

---

### Post by paulravin on 2015-08-06
Surely there must be a way to get a basic word program working, every other time I have installed ubuntu it just works.

---

### Post by Vladlenin5000 on 2015-08-06
First things first...

I don't understand how you could have ended in such situation therefore I suspect there were something else you aren't telling us.
Why?
Because the basic LO - Writer, Spreadsheet, Presentation - is always installed by default in standard Ubuntu (other flavors like Lubuntu have other office tools by default).

So, the first question is what version have you installed. You say "Ubuntu 15" and I assume Ubuntu 15.04 but is it the standard Ubuntu or some variant? If any other variant that might not come with LO by default, what was the exact command you used?

---

### Post by vasa1 on 2015-08-06
[http://askubuntu.com/questions/613941/need-help-installing-libreoffice-4-4-on-ubuntu-15-04](http://askubuntu.com/questions/613941/need-help-installing-libreoffice-4-4-on-ubuntu-15-04) may be relevant?

---

### Post by paulravin on 2015-08-06
Hi,

I installed ubuntu 12 and upgraded through to 15.04. No other variants just all done through the updat tool. Yes it is very frustrating, it is a standard feature and does not work. To be honest I forget what commands I used, I just searched for un install Liberoffice. 

Liberoffice did appear to uninstall and seemed to re install again with the same problem persisting.

---

### Post by howefield on 2015-08-06
Try renaming the libreoffice folder in....

```
~/.config/libreoffice
```

May not work but worth such a quick and simple go.

---

### Post by paulravin on 2015-08-07
This works!! My issue is solved, thank you so much all who posted - it makes using ubuntu possible, my alternative was windows 10......... So I re named the folder manually as per [URL="http://askubuntu.com/questions/613941/need-help-installing-libreoffice-4-4-on-ubuntu-15-04"]http://askubuntu.com/questions/613941/need-help-installing-libreoffice-4-4-on-ubuntu-15-04

[/URL]

---

