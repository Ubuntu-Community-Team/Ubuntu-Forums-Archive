---
title: "How To Run This Script"
date: 2006-07-11
forum: Installation &amp; Upgrades
---

### Post by savilash on 2006-07-11
I need to run a script called setup.lexprint.  File is stored in /usr/local/lexmark/setup.lexprint

My problem is that since this is the first time I have used/installed/or anything linux, I do not know how to run this script.  Double clicking does not work as an error comes up saying "Couldn't display /usr/local/lexmark/setup.lexprint.

Can someone PLEASE tell me how to run this script ?

Thanking you all in advance.

---

### Post by reacocard on 2006-07-11
open a terminal, and enter the path of the script. press enter, and the script should execute.

---

### Post by thingy on 2006-07-11
cd /usr/local/lexmark

sudo chmod 755 setup.lexprint

./setup.lexprint



(i think you will want to run the setup.lexprint using sudo if its going to be installing your lexmark printer drivers or something. in which case try typing in sudo ./setup.lexprint)

---

### Post by savilash on 2006-07-11
A big thank you to you.  Will try it when I get home tonight.



> **reacocard said:**
> open a terminal, and enter the path of the script. press enter, and the script should execute.

---

### Post by savilash on 2006-07-11
A big thank you to you too.  Again, will try it when I get home tonight.


> **thingy said:**
> cd /usr/local/lexmark

sudo chmod 755 setup.lexprint

./setup.lexprint



(i think you will want to run the setup.lexprint using sudo if its going to be installing your lexmark printer drivers or something. in which case try typing in sudo ./setup.lexprint)

---

### Post by scxtt on 2006-07-11
what printer do you have? -- i have a lexmark, linux doesn't like it :(, but i blame lexmark :)

---

### Post by savilash on 2006-07-11
I have a Lexmark E230 Laser but it is connected to a HP JetDirect 300X (I think).  I did find some Debian drivers for the E230 on Lexmark's website.  Being a total newbie to Linux (of any flavour), my problem is I don't know how to install it.  At the end of the day, the whole thing may not work but I am unable to test it at the moment.


> **scxtt said:**
> what printer do you have? -- i have a lexmark, linux doesn't like it :(, but i blame lexmark :)

---

### Post by scxtt on 2006-07-11
well good luck ... i have a photo 3150 which refuses to do anything ln linux ... i don't print much anyway and when i do, i just use my XP VirtualMachine - but that's cheating :(

---

### Post by savilash on 2006-07-11
I'll PM you and let you know how I went tonight.




> **scxtt said:**
> well good luck ... i have a photo 3150 which refuses to do anything ln linux ... i don't print much anyway and when i do, i just use my XP VirtualMachine - but that's cheating :(

---

### Post by xodeus on 2006-07-12
> **scxtt said:**
> well good luck ... i have a photo 3150 which refuses to do anything ln linux ... i don't print much anyway and when i do, i just use my XP VirtualMachine - but that's cheating :(
Tell more about XP VirtualMachine please.

---

### Post by scxtt on 2006-07-12
i use [VMware's](http://www.vmware.com) Server (Player now, since i have already made the 2 VM's i'm using) to emulate other OSs (like XP and Xubuntu) ... using these programs i can install OSs as if they were other boxes and run them 'on top of' a host OS (for me, Ubuntu) ... the guest OSs have no idea that they're not running natively on your hardware ...

---

### Post by xodeus on 2006-07-12
> **scxtt said:**
> i use [VMware's](http://www.vmware.com) Server (Player now, since i have already made the 2 VM's i'm using) to emulate other OSs (like XP and Xubuntu) ... using these programs i can install OSs as if they were other boxes and run them 'on top of' a host OS (for me, Ubuntu) ... the guest OSs have no idea that they're not running natively on your hardware ...
Okay, thanks. I already know about VMWare, but I didn't know that you can connect to a printer that is not seen by linux. I've tried this once before with my Canon i250 but the OS in VMware could not see it... I'll try again, maybe. Thanks.

---

### Post by scxtt on 2006-07-12
VMware has good visibility w/ USB and since my printer is USB, i can connect it and my XP VM figures it's connected as normal ... same goes for my iRiver H300 mp3 player ... i use my XP VM to update the song database anytime it changes ...

---

