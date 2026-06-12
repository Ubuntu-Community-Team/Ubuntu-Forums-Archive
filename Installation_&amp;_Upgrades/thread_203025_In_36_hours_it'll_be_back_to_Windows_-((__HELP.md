---
title: "In 36 hours it'll be back to Windows :-((  HELP"
date: 2006-06-24
forum: Installation &amp; Upgrades
---

### Post by jfl on 2006-06-24
I installed Breezy 3 months ago and everything was easy; it was the only Linux box in a W2000 workgroup.
Then, a week ago I "dist upgraded" to Dapper with minimum hacking; long but easy.
BUT ... now I cannot print !!!
My printer, HP laserjet 1200 is connected to a W2000 box on a Windows network. That worked fine with Breezy.
I tried to "add" the printer first as "CUPS" then as a windows printer ( I just couldn't remember what I had done on Breezy); everything looks good, but the jobs stay in the local queue and never print. Samba is installed and running.
I installed several times the recommended driver "pxlmono"; tried some other ones too.
The network connection seems OK, I can transfer files from the W2000 machine to and from the Ubuntu box.
I have spent several days trying to figure it out, read tons of stuff and it is still not working ](*,) 
I **HAVE** to get this machine running by Sunday evening.

I am thinking of doing a "clean" install from the CD; do you think it would help???.

Otherwise I will have to put back the Windows 2000 HD and call Ubuntu a failure for me. 
I am really disappointed; I never liked Micro$oft, been an OS/2 fan since v1.3, but I really wonder about the viability of a system where installing a printer listed as compatible, for which driver exists, become a major problem; from reading the forum, it seems printing is a pretty common problem :confused: 

So somebody **please** tell me if re-installing from the CD is worth spending a few more hours ???

---

### Post by IYY on 2006-06-24
> So somebody please tell me if re-installing from the CD is worth spending a few more hours ???

Why don't you try the LiveCD instead? It's the same as a default installation.

---

### Post by deadgobby on 2006-06-24
> **jfl]I installed Breezy 3 months ago and everything was easy said:**
> (*,) 
I **HAVE** to get this machine running by Sunday evening.

I am thinking of doing a "clean" install from the CD; do you think it would help???.

Otherwise I will have to put back the Windows 2000 HD and call Ubuntu a failure for me. 
I am really disappointed; I never liked Micro$oft, been an OS/2 fan since v1.3, but I really wonder about the viability of a system where installing a printer listed as compatible, for which driver exists, become a major problem; from reading the forum, it seems printing is a pretty common problem :confused: 

So somebody **please** tell me if re-installing from the CD is worth spending a few more hours ???
 I had the the same problem after upgrade too with my HP 3490. All I did was delete/remove the hp printer. Then went to add new printer and it worked fine after.

---

### Post by jfl on 2006-06-24
Thanks for the quick come-back !!!

IYY--- I read so many negatives on the 606 Live CD, every "guru" seems to say to go with the "alternate CD" ???

deadgooby --- I removed and added the printer half a dozen times, didn't do any difference, maybe because it is connected to another machine.

---

### Post by deadgobby on 2006-06-24
[QUOTE=jfl]Thanks for the quick come-back !!!

IYY--- I read so many negatives on the 606 Live CD, every "guru" seems to say to go with the "alternate CD" ???

deadgooby --- I removed and added the printer half a dozen times, didn't do any difference, maybe because it is connected to another machine.[/QUOTE]
Hav eyou tried to directly connect your printer to your Ubie box and see if it works? :-k

---

### Post by jfl on 2006-06-24
No, I did not try a direct connection. It is not easy to move the printer the way it is set-up; I know it works with W2000 now and it use to work with Breezy, so I am not sure what a direct connection would accomplish ???

---

### Post by tseliot on 2006-06-24
Printing works just fine. Try a fresh installation. Alternate installation is just like the old installer (it is safe to use it).

---

### Post by stlutz on 2006-06-24
Before reinstalling from a LiveCD, is is possible to just boot up the LiveCD itself and try to setup your printer and print?  If so, you could just compare the configuration that gets created there with what you have setup on the system you actually have installed on your hard drive before wiping everything out and doing a reinstall.

---

### Post by jfl on 2006-06-25
Thanks for your suggestions.
I reinstalled Dapper from the CD; much better than the "dist-upgrade". Took less than 2 hours; I was surprised to see there was already 92 "updates" which took longer than the install !!!
The machine works much better than with the dist-upgrade; connection to the network are instantaneous from both sides, BUT ...

**still no Printing**.

My network printer Laserjet 1200 (connected to a Windows 2000 box) is not detected.
Not knowing better, I tried both the CUPS and the SMB connection.
It is strange because it seems that the connection with the printer is working, I can change printer settings, it says the printer is ready; when I try to print the test page, it says "printing" than after a while "paused" but nothing comes out of the printer.

It would help me to know whether I should further explore the CUPS or the SMB connection ???

---

### Post by deadgobby on 2006-06-25
Have you check this howto?
[http://www.ubuntuforums.org/showthread.php?t=184838](http://www.ubuntuforums.org/showthread.php?t=184838)

---

### Post by jfl on 2006-06-25
Yeah, I did check this one; when I got to the point where it says:
*"If even that doesn't work, then I can't help you any longer. Sorry!"*
I knew I was in trouble!!!
Still trying ...

---

### Post by dmizer on 2006-06-25
if it was working in breezy ... perhaps you should stick with breezy for the time being until someone can figure out what the problem is with your printer.  i still use breezy on some of my older boxes, and just because it's not the most current doesn't mean breezy is useless.  obviously in your case your printer won't work.

someone will probably eventually solve this problem, but it needs time.  dapper is a fresh new release, and not all the kinks have been worked out yet.  bump back to breezy and keep an eye peeled for answers to your printer issue.  if you see something, try the dapper live cd to test it.

---

### Post by deadgobby on 2006-06-25
I can understand your fluster and I tried to help you. At least you have a brand name that has drivers for the printer. Unlike some other printer main brands. I run windows on one box and Ubie on the other. My printer is run by usb and we use the ubie box to print from. I use a old tact to print what I want from the windows box. That is email myself a doc, open it up with Ubie box and print away. To tell you the truth. Me and the wife like to use our Ubie box over the windows one. You could do the reversal. Print a doc off of Ubie and Email to your addy and print it off your MS Box. It is till the bug fix is cured. This is all I can offer
Gobby

---

### Post by dmizer on 2006-06-25
this is a similar solution to the one i use at work.  i have a separate windows computer that sits in a separate office.  when i want to print, i just drop the file on the windows computer via samba, and vnc into the windows computer to send the file to the printer.

that along with being able to bring the machine out of hibernation via a magic packet (wake on lan) means i never even have to touch that box.

i understand that there is a way to make this happen automagically, but i haven't had the time to nail it down yet.

---

### Post by jfl on 2006-06-26
Thanks again guys, for all your suggestions; being an old OS/2 follower from v1.3 to Warp, I know very well the driver problem !!!

The work-around suggested are not easy in an office environment, trying to convince people that Linux is better than M$...

**My story has a happy ending**; last night, disgusted, I went into "GRUB" and changed the default to the W2000. I gave up on Ubuntu !!!
Then I went on HP website to check the latest drivers for my printer and among the OS list there was Linux; couldn't believe it (the OS/2 syndrome).
Went there, got to choose RPM or Debian !!!
Got redirected and there was a 4 step process (complicated) to make, install, and configure the HP printer driver (including specific steps for Ubuntu)

It worked; I was in total disbelief; it worked again this morning, sooo we are still running Ubuntu on one machine in this business. :) 

However, how can an OS have a chance of becoming a little more than a "hobby" for computers addict when it takes over 20 hours (and a shot week-end) to get a mainstream printer working, especially when it installed like a breeze in Breezy.

Could it be that it was a case of **"meet the deadline at all cost"** ?
That's bad !!!

Bottom line: a week ago, I was gung-ho about Ubuntu, right now, I am kinda wondering.

**Thanks** again to all of you who gave me their input, that was the good part of this ordeal.  :)

---

### Post by dmizer on 2006-06-26
[QUOTE=jfl]However, how can an OS have a chance of becoming a little more than a "hobby" for computers addict when it takes over 20 hours (and a shot week-end) to get a mainstream printer working, especially when it installed like a breeze in Breezy.[/QUOTE]
this is bound to happen in any os with some kinds of equipment.  there was not a scanner to be had on the planet that worked right in win xp when it first came out.  in fact LOTS of hardware had problems working right in xp when it first came out.

but you've landed on probably the most troublesome aspect of peripheral support in linux.  consider yourself lucky to have found a solution.  i certainly sympathize with your trouble.

---

### Post by deadgobby on 2006-06-27
Congrats on finding a simple solution to your problem. I did not think of that K.I.S.S. Keep it simple stupid. HP is very friendly when it comes to Linux and Unix. One of the reasons is that HP makes multi million dollar computer chip testers. HP testers do not use MS O/S. IC testers use Unix as the primary lanquage. Too bad that Sun Micro cannot put tested with Unix. How I know this you may ask. I use to work for a micro chip factory and Unix is the primary software to test the Intell chips inside the box for windows.
Gobby

---

### Post by jfl on 2006-06-28
Thanks for the info. Glad to learn that there are major hardware manufacturers that are UNIX/Linux "friendly".
I will put HP at the top of my list for harware purchases !!!

Any others to recommend or to avoid ?

---

### Post by deadgobby on 2006-06-29
[QUOTE=jfl]Thanks for the info. Glad to learn that there are major hardware manufacturers that are UNIX/Linux "friendly".
I will put HP at the top of my list for harware purchases !!!

Any others to recommend or to avoid ?[/QUOTE]
For other hardware stuff. You can do a few things. Check the manufactor for Linux/Unix drivers if needed. Check Ubie Wiki site for example of vid cards that work well with Ubie. One to aviod in my mind is Canon. I can recall people seaching hi and low for drivers to work their printer. There is some Canon drivers out there for Linux, but the majority is written by a Linux pro. 
 Have fun.
Gobby

---

