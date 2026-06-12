---
title: "Problems with Synaptic Pakage Manager"
date: 2006-08-15
forum: Installation &amp; Upgrades
---

### Post by meshica7 on 2006-08-15
I have been getting a list of errors when I start Synaptic.This is the list that I get:

[COLOR="Red"]E: Malformed line 31 in source list /etc/apt/sources.list (dist)
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.[/COLOR]

In addition to this,I get the following message in the terminal when I try to install from there...

[COLOR="RoyalBlue"]~$ sudo apt-get install -f
E: Malformed line 31 in source list /etc/apt/sources.list (dist)
E: The list of sources could not be read.[/COLOR]



Needless to say that I cannot upgrade/download software as I am not presented with any lists.Any ideas on how I can fix this?:-k 

Thans!

Juan

---

### Post by crmanski on 2006-08-15
You need to look at the file /etc/apt/sources.list and see what is on line 31. In a terminal type...
```
gksu gedit /etc/apt/sources.list
```
You might have something there that needs to be commented out with a #.  If you do then try it, save the file and try ```
sudo apt-get update
``` in the terminal. If you cannot see the problem just copy/paste the contents of the file here so someone can take a look.

---

### Post by meshica7 on 2006-08-15
Ahhhh...
Thank you so much!That did it !!! :D 
As soon as I saw the list I began to see the problem as you stated.
I am new to Linux so I would like to know:What is the significance of the ## that were missing from my source list file?Each of the repositories was missing it.
thanx!
 Juan

---

### Post by crmanski on 2006-08-16
The ## is used to comment out or disable certian lines and comments in the file. The # symbol should only be removed from the beginning of the lines that have the sources you want to use.

---

### Post by randell6564 on 2006-08-16
> **meshica7 said:**
> Ahhhh...
Thank you so much!That did it !!! :D 
As soon as I saw the list I began to see the problem as you stated.
I am new to Linux so I would like to know:What is the significance of the ## that were missing from my source list file?Each of the repositories was missing it.
thanx!
 Juan

This sounds like you ADDED #'s instead of delete them! You are actually suppose to delete them in order to gain/enable access to the repositories.

But oh well.,if it worked,it worked LOL!  OH and only delete those that are directly next to your repo's!

---

