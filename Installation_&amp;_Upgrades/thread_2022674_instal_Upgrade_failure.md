---
title: "instal Upgrade failure"
date: 2012-07-11
forum: Installation &amp; Upgrades
---

### Post by Bryan McMahon on 2012-07-11
Can someone please help?i ran upgrades using sudo apt commands and the power went off half way through,and now i cant install or upgrade anything i have tried all of the commands that the error reports tell me and always get an invalid command,I am New to ubuntu but am experienced computer user,can someone help before i wipe and reinstall?
Thanks
Bryan McMahon

---

### Post by QIII on 2012-07-11
Could you cut and paste what happens in the terminal, please?

Put the text between code tags by clicking the "#" symbol above the input box when you post back.

---

### Post by raja.genupula on 2012-07-11
give a try as this 

after getting the login  screen Press CTRL+ALT+F1 and Login.Then type as this 

```
sudo dpkg --configure -a
```

give us the error report if anything you got .

---

### Post by Bryan McMahon on 2012-07-11
Yeah,tried it error is invalid command:



E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.




bryan@bryan-Extensa-4420:~$ dpkg-configure-a
dpkg-configure-a: command not found
bryan@bryan-Extensa-4420:~$ 
this is what happens when i run this command???
and this is what happens when i run package mgr
Software index is broken

It is impossible to install or remove any software. Please use the package manager "Synaptic" or run "sudo apt-get install -f" in a terminal to fix this issue at first.


bryan@bryan-Extensa-4420:~$ sudo apt-get install-f
[sudo] password for bryan: 
Sorry, try again.
[sudo] password for bryan: 
E: Invalid operation install-f
bryan@bryan-Extensa-4420:~$ 
this is what happens when i run this command????
confused!!!

---

### Post by jmfal on 2012-07-11
Try

```
   sudo dpkg --configure  -a    
```

---

### Post by hufemj on 2012-07-11
(Ed. Moved my question to a new thread)

I don't know if it's appropriate to piggyback on this thread or start a new one. I too had an upgrade failure from 11.10 to 12.04, but it wasn't due to a power failure. The system comes up with a login screen. The splash screen says 11.10. When I try to login, it looks like it accepts my password and then immediately logs me out.

I tried booting from a LiveCD because another thread indicated there would be a repair upgrade command, but I don't see that. It tells me 12.04 is already installed.

I ran the command suggested above,

sudo dpkg --configure -a 

after logging on to a recovery session and it tells me,

"dpkg: error: parsing file '/var/lib/status' near line 21798 package 'xmind' : blank line in value of field 'Description'"

But, I don't know what to do about it. Edit it with vi and delete the blank line?

---

### Post by QIII on 2012-07-11
It's not considered polite to hijack someone else's thread because it confuses things.  You'll get more action in your own thread.  But the staff may balk at a repeat post, so edit your post above to say something like "Moved my question to a new thread"

---

