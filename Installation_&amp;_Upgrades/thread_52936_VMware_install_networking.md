---
title: "VMware install networking"
date: 2005-07-29
forum: Installation &amp; Upgrades
---

### Post by routerstu on 2005-07-29
hello, i am installing hoary under vmware, and all goes well until it gets to "configuring apt, testing network repository..".  it just hangs there.  are there any sequence of keys i can hit to pass by this?  i am behind a dsl modem and suspect i can only get one ip which is being used by windows.  i can move this to an ethernet network where this will not be a problem but right now i need it installed :)  so are there any keystrokes to get through this hang?


thanks

---

### Post by kosmic on 2005-07-29
Hello, the problem you are describing where is a bug in the Instalation processo of Ubuntu hoary, this problem only happens when you want to install a fresh copy of ubuntu hoary in a computer without internet acess.

You have 2 ways to bypass the problem, the first and the easy one is to start the ubuntu instalation with the comand :
 ```
linux expert | or expert
``` 

The other way is to give Vmware acess in Bridge mode or NAT to your adsl modem in the host system so ubuntu can see the outside world (internet) and pass the testing repository problem.


hope it helps.

---

### Post by routerstu on 2005-07-30
thank you for thr reply!  turns out it did time out after 20 minutes or so.  i do have it configured for "bridged" networking.  i just replied to someone elses post where i can now ping addresses but cant use application with dns.  located here:

[http://ubuntuforums.org/showthread.php?t=53112](http://ubuntuforums.org/showthread.php?t=53112)


im wondering if this install is hosed from the start?  this is very weird, firefox wont work unless i put in IP, apt/synaptic works sometimes, i get "w: couldnt stat...."

thanks

---

### Post by kosmic on 2005-07-30
Hum strange problem, i'm runing vmware on a linux box, i'll try runing vmware on a window$ box and try to see if i get the same problem.

---

### Post by aj123456 on 2006-05-07
I cannot get hoary to install using Vmware either.  It also hangs on the testing repository part.  I have tried with Bridging, but I think it will work with Nat as I have had the same scenario occur using Puppy :/

---

