---
title: "Installed Fine but Freezes when Booting - Please Help!"
date: 2006-08-11
forum: Installation &amp; Upgrades
---

### Post by SuperBeaver on 2006-08-11
Hi

I'm actually using Ubuntu 5.10 - Breezy Badger.  I have the new one on the way in the post.  

I'm using an AMD laptop.  Memory and everything should be ok.  The installation went fine.  I had the program format the entire harddrive and everything installed perfectly.  The computer restarted and installed the remaining software ok.

Then it began to boot up the OS.  A screen with the Ubuntu logo appeared where it runs thro' the various tasks below and an "ok" appears next to the task when done.  This was fine too.  After this a black screen loads up and the hard drive activity slowly stops and becomes in active.

I've tried pressing all sorts of keys and key combinations but nothing happens.  Now if i press the laptop power button once a black screen comes up with "Ubuntu - Breezy badger editions" then below that my username and a cursor asking for a password.  I am not able to type anything onto this line and because i had pressed the power button it quickly shuts down.

So it looks to me like i managed to get to the log in screen and it freezes. 

I've had a quick look at some of the posts on the forum and none seem to match my issue.

Thanks for any help!

---

### Post by Seaman on 2006-08-11
When the Ubuntu logo first appears, press **ctrl + alt + F1**, this will take you in to text mode which hopefully will give you more info about what's wrong. Post here what you'll find out.

---

### Post by SuperBeaver on 2006-08-11
Thanks.  I'll give it a go.

---

### Post by SuperBeaver on 2006-08-11
> **Seaman said:**
> When the Ubuntu logo first appears, press **ctrl + alt + F1**, this will take you in to text mode which hopefully will give you more info about what's wrong. Post here what you'll find out.

Hi again. Ok, i tried what you said. I pressed ctrl alt f1. Up came a screen asking for a login and then a password. So i entered those and up pop a couple of standard messages about no warranty etc. Finally a line with superbeaver@SuperBeaver:~$ comes up with a blinking command line cursor. I tried ctrl alt f7 but the screen is still blank. The command line seems to work fine. I typed help and a list of commands came up. Thanks

---

### Post by Seaman on 2006-08-14
When you are logge in on the command line, write:
**sudo apt-get update**
*Enter your password*
**sudo apt-get dist-upgrade**
This will update all packages and hopefully remove known bugs which could cause this problem. Reboot and see if you notice and difference.
**sudo reboot**

Good luck!

---

