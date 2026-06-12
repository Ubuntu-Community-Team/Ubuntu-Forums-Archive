---
title: "can't upgrade"
date: 2010-05-14
forum: Installation &amp; Upgrades
---

### Post by ezens on 2010-05-14
i'm using ubuntu 8.04 on hp dv6600 laptop 
today i wanted to upgrade it to 8.10 
downloaded alternate .iso and realised cdrom IS NOT working i have so many cd's but none works 
no errors no nothing like there is no cd in drive 
so hove can i upgrade ??????
i seted up usb boot stick and what a surprise installer looks for cd (but hove can there be cd if it's USB ) 
so what to do now ????
btw. this is my last call for help since every time i ask i just get ignored 
p.s. if i woud wrote review on ubuntu today it woud sound WORSE than Windows VISTA what was a total fail, so thanks for nothing as usual

---

### Post by davidmohammed on 2010-05-14
... try the following [link]("http://www.linuxconfig.org/install-ubuntu-lucid-lynx-linux-from-usb-stick") which describes upgrading to lucid via usb stick.

Why do you want to upgrade 8.04 to 8.10? 8.10 is not supported anymore.

I would recommend you backup your /home partition to a usb stick.  Then use the above method on another stick to completely overwrite (not upgrade).  Then copy back what you need from you backup stick.

---

### Post by ezens on 2010-05-14
backup 160gb of data to usb flash drive what i have only one and it's 1gb 
i want 8.10 because i wan't skype and it's stable 
btw support is no argument didn't have any for 9.10 
no one helps with 8.04 either so why even bother to care about that ?

---

### Post by davidmohammed on 2010-05-14
[this guy]("http://ubuntuforums.org/showthread.php?t=831332") had a similar issue and worked around the issue as described.

---

### Post by ezens on 2010-05-14
so unetbootin is no good for this kind of thing ?

---

### Post by davidmohammed on 2010-05-14
I've have read mixed reports with that tool.  Most threads I've read all have the similar "need a cd" problem with the alternate CD.  You will probably need to use the workaround described in the thread in my previous post to fool the alternate install in believing there is a CD when there isn't.

---

### Post by ezens on 2010-05-14
i might be stupid but i kinda din't get that hole thing and btw it don't let me to get in terminal 
and don't alow to wrote the cd path 
will try to create usb boot like in that manul
and btw (releated question in other way) if i get in terminal at part where i can enter cdrom path manualy 
so i wrote ls -l /dev (i think this was the one) 
the drops the list and all i see is tty (ore stuf like that)
HOVE to scroll the list to top ?? 
so i can see others (it's for server same no cd thing and no usb ports ) all i know ubuntu detects cdrom as hdd

---

### Post by davidmohammed on 2010-05-14
sorry - I'm trying my best to understand, but either your english is not your native tongue or you are using text-based english that I'm too old to understand :)

Can you please rephrase ?  What have you tried and what error messages are being displayed?

---

### Post by ezens on 2010-05-14
sorry i'm from latvija
when i boot from usb it freezes for moments 
at step where it looks for cdrom it shows there isn't one 
and asks "if i wan't to try looking for it again" but don't give me a chance to do anything else 

for server i got furder where it alows to manualy enter location ore use "alt+f2" for terminal and use "ls /dev " comand to locate it 
when i do "ls /dev " comand it brings up the list but i can see only end of it so i wanted to know hove to see top of it

---

### Post by davidmohammed on 2010-05-14
for commands that display more than one screen of information then use the | more
This will stop at each screen waiting for you to press space-bar for the next screen.

e.g. ls /dev | more

---

### Post by ezens on 2010-05-14
ok thanks for that 
still no luck booting from usb 
tomorow will buy some cd's and try to write them i hope cdrom will detect them because i have clear dvd's what it doesn't 
and it's 01:53 at night so i'm going to sleep 
any way great thanks for wasting you're time with me

---

