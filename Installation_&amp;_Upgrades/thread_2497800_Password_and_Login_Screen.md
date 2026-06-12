---
title: "Password and Login Screen"
date: 2024-05-18
forum: Installation &amp; Upgrades
---

### Post by janvi2 on 2024-05-18
My installation is a 22.04 jammy using the Gnome desktop. It comes from updating a version 18 LTS installation. The old version allowed a 3 character trivial password. I like to change this password now for security reasons. Unfortunately, the gnome Settings->Users does not allow trivial passwords any more. For my opinion, automatic logoff from desktop with a trivial password what changes occasionally is more safe than complicated password without auto logoff setup. The login password is critical as we cannot use a password manager therefore.

1) Are there any file based possiblities to change existing trivial password with another trivial password beside the gnome graphic interface  ?

2) How is it possible to change the login screen to "classic" version with 2 input fields what do not display the available user names ?

---

### Post by TheFu on 2024-05-18
If you want to change the passwd for the current username, use **passwd** without any arguments in a terminal.  

If this is a local password, then that command will update the local password DB/shadow file.
If you have centralized password management, usually via LDAP, then you should have another tool that will create and allow modifying the password for end-users.  In my network, our email web-client system modified the LDAP passwords, so users only need to change their password using that specific interface and no other places.  We do training to make it clear to everyone.

Gnome has their own login manager which seems to be tightly coupled to the Gnome desktop.  I don't think any other login manager will work, so you are stuck.  If you didn't use Gnome, then there are multiple other login managers that can be used.
> any file based possiblities (sic) to change existing trivial password
The **_passwd_** command, as stated.
Any password under 12 random characters takes less than 1 hour to crack.  Opinions don't matter. Facts do.

I use **slim**, for example.  
```
NAME
       slim - Simple LogIn Manager

DESCRIPTION
       SLiM  is  a lightweight login manager for X11, allowing the initializa&#8208;
       tion of a graphical session by entring username and password in a login
       screen.

```
It requires typing in both the username and the password. No selection list is provided.  The /etc/slim.conf file has a few options.  A default username can be filled in, if that's desired, using the 
```
# default user, leave blank or remove this line
# for avoid pre-loading the username.
#default_user        simone
```
If there is a default user, it is possible to allow an automatic login - talk about a security nightmare.

---

### Post by currentshaft on 2024-05-18
.d

---

### Post by currentshaft on 2024-05-18
c c ad

---

### Post by janvi2 on 2024-05-18
jv@JamesWebb:~$ passwd
Changing password for jv.
Current password: 
New password: 
BAD PASSWORD: The password is shorter than 8 characters

This are no good news. sudo passwd jv worked with 3 char like before. Practically, any logged in and open desktop is the biggest risk. Of coarse, the second risk are weak passwords. Probably its not accepted, to key in frequently any password with 12 or more characters. 
Finger print, RFID badge or face recognition are obviosly in their functionality and unsecure. Possibly I have to think about any hidden hardware like a YubiKey inside the keyboard or mouse what turns the keyboard or mouse into a compound HID. The custom HW add-on contains a really strong password what is issued to the keyboard interface with any means of simple trigger or key sequence. If this key sequence is used wrong and/or power loss, the addon HW looses its key what requires reprogramming by external administrator using any proprietary HW programmer therefore.

---

### Post by TheFu on 2024-05-18
Ah. You can change the requirements for password complexity in the PAM settings.  I'd have to look up the exact method, but you can do that just as easily.

There are methods for creating long, easy-to-remember, passwords that are random. One is to use 6 dice that are rolled to make a number, which pointed to a huge list of words. Do that 4+ times to get 4 truly random words and join them with some non-word characters and it will be hundreds, in not millions of years for someone to break it.  [https://www.eff.org/dice](https://www.eff.org/dice) should explain the method.

Once you have a long, random, password, there is little need to change it.  Many password change mandates in corporations are there to deal with transient workers or normal attrition of workers or other processes with failures built-in.  

Let's just say, I've worked in environments where changing passwords far to often was mandated.  At 1 point, I had 12 different accounts on 12 completely separate networks, each with different complexity rules and mandated expiration periods. It was a pain to manage and it was a criminal offense if I didn't follow the rules, so I did.

---

