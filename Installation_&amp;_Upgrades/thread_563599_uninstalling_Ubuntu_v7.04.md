---
title: "uninstalling Ubuntu v7.04"
date: 2007-09-30
forum: Installation &amp; Upgrades
---

### Post by riyadh on 2007-09-30
to uninstall Ubuntu v7.04 from my pc, i formatted the partition it was in.but now i can't seem to boot my computer.when i turn on my computer i get an error message.
> GRUB Loading 1.5

GRUB Loading, please wait...
Error 17

how do i get rid of this so that i can use my pc again.i have Windows XP installed in it.

---

### Post by pyrodrake on 2007-09-30
Right now, your boot sector on the hard drive is still pointed to the partition that Ubuntu was installed on, with GRUB.  You need to have Windows XP re-write your MBR.  To do this, you need to boot off your Windows XP CD and go into the "Recovery Console".  After you log into the command prompt, you should run the following 2 commands:
FIXBOOT
FIXMBR

After you enter these commands in, if I remember correctly, Micro$oft will display some scary confirmation screens asking if you are sure you want to do this.  I've done this myself many times in the past when I mess something up, and have never had an issue,  Microsoft is (not surprisingly) very vague as far as under what circumstances FIXMBR would cause a loss of data...  I would suggest to try JUST running "FIXBOOT" first, reboot the system and see if that works.  If not, then boot into the recovery console again and run "FIXMBR"  Should work like a charm.

Let me know if it works for you, or if you need additional help.  Good luck!  :)

---

### Post by riyadh on 2007-09-30
I knw tht much as to enter the recovery console.but at the console they ask for the administrator password which i don knw cos i never set any such password.is there another way 2 do ths?

---

### Post by pyrodrake on 2007-09-30
When you are logging into the recovery console, if you did not set an administrator password in XP Pro or have XP Home, then you should be able to leave the Password field blank and just hit enter.  It should still log you in.

---

### Post by riyadh on 2007-10-01
> **pyrodrake said:**
> When you are logging into the recovery console, if you did not set an administrator password in XP Pro or have XP Home, then you should be able to leave the Password field blank and just hit enter.  It should still log you in.

i didn't reinstall windows xp after i bought it.and i don't think i ever logged in to the recovery console until now.i tried to leave the filed blank but it does not work.there seems to be a password only i don't know it.now i don't want to reinstall windows xp because i don't want to go through the pain of installing all my software again.and most importantly i don't want to download all the windows updates since there are over a hundred of them.isn't there a way to change the password or bypass this?

---

### Post by pyrodrake on 2007-10-02
Hmmm...  Thats a tough one...  I know for a fact that there IS a way to reset the admin password from some type of Linux boot CD, although I would have no clue as to the process.  My friend had to do that for a server that was XP Pro on a computer at work, so I definitely know its possible.  I Google'd around a bit and found [this link]("http://home.eunet.no/pnordahl/ntpasswd/") that may be useful (I have never tried this/these programs, and cannot be held responsible for any damage done by following their directions).  After a quick overview of their site, it seems fairly safe.
There are two other options you can try that I just thought of as well:
1) If your user account within Windows has Admin privileges, you may be able to use your user name and password to log into the recovery console and do what you need to do.
2) Alternatively, if you still have the Ubuntu install CD, you can re-install Ubuntu temporarily (you don't even have to update it or anything).  This would re-install GRUB, and should make the boot loader have Windows XP as an option.  From their, you can boot back into Windows once, change the Admin password (or create an administrator-level user account), THEN boot into the recovery console and update the MBR/boot sector with Microsofts tools.  At that point, Windows will override the fact that Ubuntu is even installed on the system, and you can delete/remove the partition in Windows with no problems.

Option #2 may be your best bet, and probably a lot safer than downloading a random program from the internet, but if that program really does what it says it does, it may be worth the shot.

Good luck, and let me know how things turn out, or if you need anything else!  ;)

---

