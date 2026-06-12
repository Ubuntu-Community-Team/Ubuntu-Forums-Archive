---
title: "Karmic installation does not detect HDD"
date: 2009-12-08
forum: Installation &amp; Upgrades
---

### Post by khadland on 2009-12-08
Been running 9.10 for a little while installed within windows. Have decided to step things up and have cleared a hard drive to dedicate to Ubuntu. Its an 80gb Seagate sata.
 

When I try and install it detects my other 3 drives but not this one. I've tried disconnecting the other drives, swapping sata ports, formatting it and nothing makes a difference.
 

If I boot off the livecd or liveusb the drive appears just fine.  I've searched the net and can't find any solutions.
 

Appreciate any ideas....


Kyle

---

### Post by raymondh on 2009-12-08
> **khadland said:**
> Been running 9.10 for a little while installed within windows. Have decided to step things up and have cleared a hard drive to dedicate to Ubuntu. Its an 80gb Seagate sata.
 

When I try and install it detects my other 3 drives but not this one. I've tried disconnecting the other drives, swapping sata ports, formatting it and nothing makes a difference.
 

If I boot off the livecd or liveusb the drive appears just fine.  I've searched the net and can't find any solutions.
 

Appreciate any ideas....


Kyle

Kyle,

Try :

1.  Boot into the liveCD and go live session (try ubuntu ...).  Access a terminal and type

```
sudo apt-get remove dmraid
```

Close terminal and proceed to install.

2.  Another tip provided by presence1960 is to make sure in step 4 of the install process that the proper HD is selected in the upper right Box.

Regards and good luck.

---

### Post by khadland on 2009-12-08
Thanks Raymond!

I'll give it a go this evening.

---

### Post by raymondh on 2009-12-08
> **khadland said:**
> Thanks Raymond!

I'll give it a go this evening.

Like always, have a working/tested back-up of your files.   Working on the HD and partitioning always has inherent risks.

Regards,

---

### Post by khadland on 2009-12-09
Removing dmraid did the trick.  Thanks heaps!

---

### Post by raymondh on 2009-12-09
> **khadland said:**
> Removing dmraid did the trick.  Thanks heaps!

You're welcome.

Happy ubuntu-ing :)

---

### Post by Hugolp on 2009-12-26
> **raymondh said:**
> Kyle,

Try :

1.  Boot into the liveCD and go live session (try ubuntu ...).  Access a terminal and type

```
sudo apt-get remove dmraid
```

Close terminal and proceed to install.

2.  Another tip provided by presence1960 is to make sure in step 4 of the install process that the proper HD is selected in the upper right Box.

Regards and good luck.

Just want to say thanks. This thread and specially this answer saved me from going nuts installing my new Ubuntu. I usually dont say anything and but, seriously, thanks for taking the time of answering.

---

### Post by raymondh on 2009-12-26
> **Hugolp said:**
> Just want to say thanks. This thread and specially this answer saved me from going nuts installing my new Ubuntu. I usually dont say anything and but, seriously, thanks for taking the time of answering.

You're welcome.  Happy holidays :)

---

### Post by Skipper' on 2010-01-04
> **raymondh said:**
> Kyle,

Try :

1.  Boot into the liveCD and go live session (try ubuntu ...).  Access a terminal and type

```
sudo apt-get remove dmraid
```Close terminal and proceed to install.

2.  Another tip provided by presence1960 is to make sure in step 4 of the install process that the proper HD is selected in the upper right Box.

Regards and good luck.

Hello, I have this same problem.
Only I'm triying to install the OS from a usb stick.
and it won't detect my hard drive.
80GB HD

I'm a noob at installing OS so mind explaining this where I can understand it?:KS

---

### Post by raymondh on 2010-01-04
> **Skipper' said:**
> Hello, I have this same problem.
Only I'm triying to install the OS from a usb stick.
and it won't detect my hard drive.
80GB HD

I'm a noob at installing OS so mind explaining this where I can understand it?:KS

Similar to above ...

- Boot into the USB stick (that is, plug the USB then make the USB stick first to boot in BIOS ).
- Select 'TRY UBUNTU WITHOUT ANY CHANGES'.  That is called a live session
- When the live session desktop loads, navigate to applications > accessories > terminal
- In the terminal, type (or copy-and-paste this command) :

```
sudo apt-get remove dmraid
```

- Let it do it's thing.  Once done, close the terminal.  In the desktop, you'll see an INSTALL icon.  Click on it to instal and see if your HD is detected in step 4.

If not, post back any error message.

---

### Post by Skipper' on 2010-01-10
Well I figured and did that but still won't work.

---

