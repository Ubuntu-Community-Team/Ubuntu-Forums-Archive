---
title: "installation problem [Resolved]"
date: 2007-02-27
forum: Installation &amp; Upgrades
---

### Post by AAJ on 2007-02-27
Hi,

when i try to install any software by aptitude  or apt-get, I got this error.

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
E: Could not get lock /var/lib/apt/lists/lock - open (11 Resource temporarily unavailable)
E: Couldn't lock list directory..are you root?


Note: i am login with root by (su) but still it gives me the same  error. 

Please advice,

---

### Post by johnc4510 on 2007-02-28
Do you have Synaptic Package Manager open at the same time?

---

### Post by aysiu on 2007-02-28
Any chance you have another program (like Add/Remove Programs, Synaptic Package Manager, Adept Package Manager) open when you're using *apt-get* or *aptitude*?

---

### Post by AAJ on 2007-02-28
Hi guys,

first of all thanks for replying but i got another error now :)  i did that but when i try to do apt-get update  I got this error in the end

Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security/restricted Packages                                                                  
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security/universe Packages                                                                    
Hit [http://sa.archive.ubuntu.com](http://sa.archive.ubuntu.com) edgy-updates/main Sources                                                                       
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security/multiverse Packages                                                                  
Hit [http://sa.archive.ubuntu.com](http://sa.archive.ubuntu.com) edgy-updates/restricted Sources                                                                 
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/multiverse Packages                                                                           
Hit [http://sa.archive.ubuntu.com](http://sa.archive.ubuntu.com) edgy-updates/multiverse Packages                                                                
Fetched 1364B in 13s (98B/s)                                                                                                     
[COLOR="Red"]E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
[/COLOR]

---

### Post by AAJ on 2007-02-28
I think that means i can not run to administration tools in the same time. :(

---

### Post by aysiu on 2007-02-28
> **AAJ said:**
> I think that means i can not run to administration tools in the same time. :(
You can run two administrative tools at the same time, but you can't run two of the same package managers at the same time--because all the "different" package managers are all actually just different interfaces for the same package manager.

---

### Post by geakMonkey on 2007-02-28
> **AAJ said:**
> Hi guys,
                                                                                              
[COLOR="Red"]E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
[/COLOR]

When you are installing/upgrading the files are locked. It has been suggested above that you might have Synaptic running at the same time because it locks the files it is installing/upgrading. If that is happening, turn it off and retry the apt-get.

---

### Post by AAJ on 2007-02-28
I did refresh the Synaptic Package Manager after that i closed it then i run the aptitude and it is works fine now how i don't know :D

I am using only aptitude for anything install or remove this tool the best it remembers every package install not like apt-get.

thanks all

---

### Post by aysiu on 2007-02-28
I moved your next problem to [its own thread](http://ubuntuforums.org/showthread.php?t=372293)

---

### Post by magicfab on 2007-02-28
That happens whe synaptic or another package update / installation application is already running. Close any other package managers (including Add/Remove application, language pack installer, etc.) and retry.

If you have automatic updates activated, that may also interfere.

---

