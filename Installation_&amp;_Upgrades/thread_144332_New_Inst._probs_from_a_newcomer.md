---
title: "New Inst. probs from a newcomer"
date: 2006-03-14
forum: Installation &amp; Upgrades
---

### Post by rightsaidfred on 2006-03-14
Hi,Just taken my first steps into Linux.

Downloaded Ubuntu 5.10 ISO and  burnt it onto a CD OK.

Apparently loaded it OK onto my spare system, ie it went through all the stages without failing.However when it got to the stage where the CD was taken out and a reboot onto the hard disk occured we have problems.

It asked for user ID, entered OK, then password entered OK. But instead of booting into a desktop as I thought, it went to a command prompt, and of course I have no idea what command to enter,if any.

From a previous thread on here I did try to enter a SUDO command ending in install-desktop which asked for a password,but when I tried to enter one my keyboard appeared not to work!!
Thanks for any help.

---

### Post by PsychoTrauma on 2006-03-14
In the terminal you would want to do:
```
sudo apt-get update

sudo apt-get install ubuntu-desktop
```

As for the keyboard not working do you happen to have another around it might not be compatable....I used to have a windows keyboard that just wouldn't work with linux at all.

---

### Post by rightsaidfred on 2006-03-14
Hi psycho, thanks for quick reply.Tried your solution but still no joy when I try to enter password after typing "sudo apt-get update"

Does the fact I can type sudo etc mean my key board is compatible, also is the password the same as i used to log onto ubuntu?
Thanks.

---

### Post by fmo on 2006-03-14
Hi rightsaidfred

Do you actually have a graphical login or is it a text mode one ?

If text mode, what is your graphics card?

---

### Post by rightsaidfred on 2006-03-14
Hi, sorted my own problem with help from ubuntu.( I think )

When entering password on sudo it is not echoed onto the screen so gives the impression the key board not working. I entered my pword (nothing appeared on screen) then pressed enter and it appeared to start working. As I said earlier I am a complete newbie but does what I have just said make sense?

---

### Post by timas on 2006-03-14
Yup!

It seems like Linux considers not showing a password being typed more securely, from what I know, all linux distro's hide the password in a console mode while its being typed.

---

### Post by rightsaidfred on 2006-03-14
hi again and thanks for your support.

To FMO, before I sorted my keyboard prob I had  atext mode login ie command line.Now I have carried out psychotrauma's instruction to load the desktop I have  agraphical one and most things appear to be okwith one exception.

My graphics card is  a S3 trio 64v which works ok except I cannot get higher than 640x480 resolution.How can I make sure I have the correct driver and if not how do I get one.Thanks,Fred.

---

