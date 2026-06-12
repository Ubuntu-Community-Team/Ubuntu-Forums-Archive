---
title: "Can no longer install or upgrade"
date: 2023-11-05
forum: Installation &amp; Upgrades
---

### Post by meersmankarin on 2023-11-05
Hi,

I posted a thread already but I cannot find it anywhere, so something must have gone wrong. If not, I apologise for using the forum in  the wrong way.

I work on ubuntu 22.04.3

A few days ago I wanted to install LAMP. I was not prompted for any password, something had gone wrong
There was also a message that said some package was missing. Googling it I stumbled on this page :
[https://ubuntu.pkgs.org/22.04/ubuntu-updates-main-arm64/mysql-server_8.0.35-0ubuntu0.22.04.1_all.deb.html](https://ubuntu.pkgs.org/22.04/ubuntu-updates-main-arm64/mysql-server_8.0.35-0ubuntu0.22.04.1_all.deb.html)
downloaded package with wget [http://ports.ubuntu.com/pool/main/m/mysql-8.0/mysql-server_8.0.35-0ubuntu0.22.04.1_all.deb](http://ports.ubuntu.com/pool/main/m/mysql-8.0/mysql-server_8.0.35-0ubuntu0.22.04.1_all.deb) in the command line but that didn't work. 
So I consulted chat GPT. We managed to install the apache server, php and mysql but I got into real trouble with myphpadmin.
More than 3 hours later I gave up. 
Now I can no longer install anything or upgrade. 
If I try to install anything I get : 

E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 

So I do that. And I get into this window I got into when I tried to install phpmyadmin. This is what I see: 

Package configuration

 &#9484;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9508; Configuring phpmyadmin &#9500;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9488;
 &#9474;                                                                           &#9474; 
 &#9474; An error occurred while installing the database:                            
 &#9474;                                                                             
 &#9474; ERROR 1045 (28000): Access denied for user                                  
 &#9474; 'debian-sys-maint'@'localhost' (using password: YES) . Your options are:    
 &#9474;  * abort - Causes the operation to fail; you will need to downgrade,        
 &#9474;    reinstall, reconfigure this package, or otherwise manually intervene     
 &#9474;    to continue using it. This will usually also impact your ability to      
 &#9474;    install other packages until the installation failure is resolved.       
 &#9474;  * retry - Prompts once more with all the configuration questions           
 &#9474;    (including ones you may have missed due to the debconf priority          
 &#9474;    setting) and makes another attempt at performing the operation.          
 &#9474;  * retry (skip questions) - Immediately attempts the operation again,       
 &#9474;    skipping all questions. This is normally useful only if you have         
 &#9474;    solved the underlying problem since the time the error occurred.         
 &#9474;                                                                             
 &#9474;                                  <OK>                                       
 &#9474;                                                                           &#9474; 
 &#9492;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9496; 
                                                                               
Everything is stuck. Chat GPT can't help. Please can you help me? I wanted to learn php,  I don't know much about ubuntu at all. 
I went through an endless concatenation of commands using chat gpt. We purged and killed armies of programs and processes.
It's a really long conversation, I copied it into an .odt file and I'm adding that as an attachment.

Thank you,

Karin Meersman

---

### Post by #&amp;thj^% on 2023-11-05
First everything you need is in the Repos, no need for wget, but can you show us this:
```
*systemctl status avahi-daemon
&#9679; avahi-daemon.service - Avahi mDNS/DNS-SD Stack
     Loaded: loaded (/lib/systemd/system/avahi-daemon.service; enabled; preset:>
     Active: active (running) since Sun 2023-11-05 06:32:07 MST; 1h 43min ago
TriggeredBy: &#9679; avahi-daemon.socket
   Main PID: 937 (avahi-daemon)
     Status: "avahi-daemon 0.8 starting up."
      Tasks: 2 (limit: 8970)
     Memory: 1.2M
        CPU: 63ms
     CGroup: /system.slice/avahi-daemon.service
             &#9500;&#9472;937 "avahi-daemon: running [lvm-ThinkPad-X1-Carbon-7th.local]"
             &#9492;&#9472;992 "avahi-daemon: chroot helper"

```

---

### Post by meersmankarin on 2023-11-05
```
avahi-daemon.service - Avahi mDNS/DNS-SD Stack
     Loaded: loaded (/lib/systemd/system/avahi-daemon.service; enabled; vendor preset: enabled)
     Active: active (running) since Sun 2023-11-05 12:58:05 CET; 3h 21min ago
TriggeredBy: &#9679; avahi-daemon.socket
   Main PID: 800 (avahi-daemon)
     Status: "avahi-daemon 0.8 starting up."
      Tasks: 2 (limit: 9246)
     Memory: 1.3M
        CPU: 176ms
     CGroup: /system.slice/avahi-daemon.service
             &#9500;&#9472;800 "avahi-daemon: running [karin-System-Product-Name.local]"
             &#9492;&#9472;850 "avahi-daemon: chroot helper"

Nov 05 12:58:09 karin-System-Product-Name avahi-daemon[800]: New relevant interface wlo1.IPv6 for mDNS.
Nov 05 12:58:09 karin-System-Product-Name avahi-daemon[800]: Registering new address record for fe80::4b02:9570:c317:32bd on wlo1.*.
Nov 05 12:58:09 karin-System-Product-Name avahi-daemon[800]: Joining mDNS multicast group on interface wlo1.IPv4 with address 192.168.0.214.
Nov 05 12:58:09 karin-System-Product-Name avahi-daemon[800]: New relevant interface wlo1.IPv4 for mDNS.
Nov 05 12:58:09 karin-System-Product-Name avahi-daemon[800]: Registering new address record for 192.168.0.214 on wlo1.IPv4.
Nov 05 12:58:10 karin-System-Product-Name avahi-daemon[800]: Leaving mDNS multicast group on interface wlo1.IPv6 with address fe80::4b02:9570:c317:32bd.
Nov 05 12:58:10 karin-System-Product-Name avahi-daemon[800]: Joining mDNS multicast group on interface wlo1.IPv6 with address 2a02:1810:2f1e:1c00:99d1:6d38:bd78:3e0e.
Nov 05 12:58:10 karin-System-Product-Name avahi-daemon[800]: Registering new address record for 2a02:1810:2f1e:1c00:99d1:6d38:bd78:3e0e on wlo1.*.
Nov 05 12:58:10 karin-System-Product-Name avahi-daemon[800]: Withdrawing address record for fe80::4b02:9570:c317:32bd on wlo1.
Nov 05 12:58:12 karin-System-Product-Name avahi-daemon[800]: Registering new address record for 2a02:1810:2f1e:1c00:9272:9ad5:8e9e:d5cb on wlo1.*.
```

Thank you for the quick reply!

---

### Post by #&amp;thj^% on 2023-11-05
It makes things easier for us if terminal commands are wrapped in code tags. (See my signature for Code Tags)
I can't promise I can help but lets give this a try first:
```
sudo apt autoremove --purge mysql-server phpmyadmin
```
And after that is finished, please run:
```
sudo apt update
```
and paste that back here. (In Code Tags)
I'm going into work for about an hour, but will return when done.

---

### Post by meersmankarin on 2023-11-05
Hi, I'll use the code tags. Is it those three back tics ? I'll look up all the proper behaviour.

No, didn't work. Have done that several time before. 
Greets,
Karin

---

### Post by yancek on 2023-11-05
Code tags are above the window in which you enter text.  The middle row of icons, 3rd from the right:  #
If you are posting a quote and not code, it is the icon immediately to the left of the # and if you mouse over the various icons, they indicate what they are.

---

### Post by meersmankarin on 2023-11-05
thank you!

---

### Post by SeijiSensei on 2023-11-05
If possible, I'd reinstall Ubuntu from scratch, then install apache2 and php manually.
```
sudo apt update; sudo apt install apache2 php
```

If you need a database, I prefer PostgreSQL over MySQL, but either is fine. Don't bother with web-based admin tools. Learn to type SQL commands at the prompt, or use something like LibreOffice Base or Microsoft Access to manage the database with GUI tools.

I suggest creating a virtual machine to try everything out. You can use either [VirtualBox](https://virtualbox.org/) or the native KVM system built into the Linux kernel. [https://phoenixnap.com/kb/ubuntu-install-kvm](https://phoenixnap.com/kb/ubuntu-install-kvm).

---

### Post by meersmankarin on 2023-11-05
I want to do a coursera course (professor Chuck) and they want you to install LAMP with myphpadmin.

Yes, I've been thinking that too.
Installation from scratch, that would be getting a version on a usb stick? There's this technical term for it, I did it once before. 
Could you give me a good link to a page where I can download it? I did it years ago.
I made a backup of all my personal docs so that's ok. 

Greets,
Karin

---

### Post by #&amp;thj^% on 2023-11-05
> **SeijiSensei said:**
> If possible, I'd reinstall Ubuntu from scratch, then install apache2 and php manually.
```
sudo apt update; sudo apt install apache2 php
```

If you need a database, I prefer PostgreSQL over MySQL, but either is fine. Don't bother with web-based admin tools. Learn to type SQL commands at the prompt, or use something like LibreOffice Base or Microsoft Access to manage the database with GUI tools.

I suggest creating a virtual machine to try everything out. You can use either [VirtualBox](https://virtualbox.org/) or the native KVM system built into the Linux kernel. [https://phoenixnap.com/kb/ubuntu-install-kvm](https://phoenixnap.com/kb/ubuntu-install-kvm).

+1
KVM is my preferred choice.
As for Download link here: [https://ubuntu.com/download/desktop](https://ubuntu.com/download/desktop)
Good Luck
And now I've gone fishing for the rest of the day....:)

---

### Post by meersmankarin on 2023-11-05
I found the instructions on chat gpt to reinstall ubuntu from scratch. I remember that.
It's a bit tricky but I did it before I must be able to do it again.

Thank you for the attention and all the support.

Greets,
Karin

---

### Post by #&amp;thj^% on 2023-11-06
FWIW, I was able to replicate your problem yesterday, and it took me an hour or so today to fix my system.
In fact I won't detail that recovery process  in any forum, due to the nuclear method i used.
Dang don't follow that method again please!!!

---

### Post by MAFoElffen on 2023-11-06
LOL!!!

That goes back to: "Just because something is possible, doesn't make it a good idea."

---

### Post by #&amp;thj^% on 2023-11-06
> **MAFoElffen said:**
> LOL!!!

That goes back to: "Just because something is possible, doesn't make it a good idea."

Oh so very true.....and I hope the OP won't repeat the same method described in the .odt attached.
Yuck.

---

### Post by SeijiSensei on 2023-11-08
Why on earth are you using ChatGPT when Ubuntu has an enormous array of documentation?  

Start here: [https://ubuntu.com/tutorials/install-ubuntu-desktop](https://ubuntu.com/tutorials/install-ubuntu-desktop)

---

### Post by yancek on 2023-11-08
> ERROR 1045 (28000): Access denied for user  

What exactly did you do to get that error?  Was it installing something or configuring where you needed sudo or were you setting up or configurin mysql/mariadb?  If the latter, had you set a root password for mysql/mariadb?  If you go through the mysql_secure_installation process explained in the first link below.

I would suggest and agree with the post above to NOT use chatGPT.  It isn't ready for something like this.  Did you get installation instructions from some other site to install the LAMP server?  The link below has detailed and accurate instructions for installing LAMP.  It also includes instructions for installing PhpAdmin but it has been well over a decade since I used it so can't speak to it.  I generally use a terminal to deal with mysql/mariadb also.  You should be able to find any number of sites detailing the installation of a LAMP server on line and they should all be similar to the instructions at the link below.
  
[https://www.tecmint.com/install-lamp-with-phpmyadmin-in-ubuntu-20-04/](https://www.tecmint.com/install-lamp-with-phpmyadmin-in-ubuntu-20-04/)

An even simpler method is at the ubuntu.com site at the link below.  It does not included phpmyadmin but the second link below does.

 [https://ubuntu.com/server/docs/lamp-applications](https://ubuntu.com/server/docs/lamp-applications)

[URL="https://ubuntu.com/server/docs/how-to-install-and-configure-phpmyadmin"]https://ubuntu.com/server/docs/how-to-install-and-configure-phpmyadmin


 

 
[/URL]

---

### Post by meersmankarin on 2023-11-11
Hi,

Thank you for the virtualbox idea but if I install ubuntu inside virtualbox inside ubuntu and get into the same misery after hours of suffering
I'm going to jump out of a window.

I reinstalled ubuntu from scratch, erased everything and lost some stuff. And I unenrolled from that coursera course. 
Still cannot install LAMP.

I just want to learn php. I pay a webhost and I want to make a simple backend for a simple database. 
Nothing really fancy. So, I wonder, maybe I can learn php inside phpfiddle or replit and once I got some
code stick it onto my webhost and  try it out? 

No installation, immediate coding ? 

Or is that naive and should I plough through a digital ocean article that goes into the finest detail?
And, I know, this is another question, but I learned some command line but I always forget it because
I don't really use it. Is there some fun resource to learn more about ubuntu in a way that I it is interesting for
personal and not just professional use? 
 
Anyway, I'm going to learn some php now. Thanks for all the support,

Greets,
Karin

---

### Post by MAFoElffen on 2023-11-11
Backup what you have installed now... That way if you decided, you need to start over again, you can restore to this point of time.... Think of your backups as milestone fallback points... When you get to the next big milestone that is a success, take another backup.

Do you have a Desktop or Server installed right now? The reason I ask, as I have a little time. I could spin up either and show you a basic LAMP install, to get you going on your way to learning what you want to. That is how I learn new things also. By diving in, and being hands on.

What I will do is spin up either, depending on yours answer, and take screenshots and describe what it happening in them.

---

### Post by Tadaen_Sylvermane on 2023-11-11
> **SeijiSensei said:**
> Why on earth are you using ChatGPT when Ubuntu has an enormous array of documentation?  

Start here: [https://ubuntu.com/tutorials/install-ubuntu-desktop](https://ubuntu.com/tutorials/install-ubuntu-desktop)


For something like that you are correct. But for more specific stuff when you aren't exactly sure what you are looking for ChatGPT can narrow it down big time. In many cases it gives me an answer to a problem I have that I was unable to find after googling for an hour or so. Web search is much more efficient with ai.

*EDIT* for that matter while it feels foolish I had the hardest time grasping pointers in c. I still have difficulty from time to time but the way chatgpt explained it to me made it very easy for the most part. I don't ask it to write code for me. But I do ask it to tell me the why / how. Damn thing could probably teach a classroom at some point. It's a bit scary actually...

---

