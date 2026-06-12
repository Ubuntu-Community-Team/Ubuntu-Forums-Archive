---
title: "upgrading to edgy headlessly (remotely)"
date: 2006-10-13
forum: Installation &amp; Upgrades
---

### Post by frafu on 2006-10-13
Hello, 

I am running a **headless** celeronbox with ubuntu desktop i386 dapper. 

To login remotely, the following servers are running on the celeronbox: 
- vnc server shipped with ubuntu dapper
- free edition of the nx server from nomachine
- openssh server

Now I would like to upgrade the celeronbox to edgy remotely. My question is: 

Will I still be able to login remotely after the upgrade without having to reinstall or reconfigure the servers? In other words, will the servers still be active after the upgrade? 

Thanks in advance for any reply. 

frafu

---

### Post by christhemonkey on 2006-10-13
You would hope they would?


(not a guarentee though)

---

### Post by frafu on 2006-10-14
@christhemonkey

Indeed, I would like the remote logins to remain active after the upgrade (at least one of them). If I understand correctly, you don't know either whether it is the case. 

Nevertheless, thanks for your reply. 

frafu

---

### Post by christhemonkey on 2006-10-15
As far as i remember, the configs are kept through dist-upgrade, so it should keep everything fine.

(but still, i wouldnt trust my word on this...)

---

### Post by frafu on 2006-10-15
> **christhemonkey said:**
> As far as i remember, the configs are kept through dist-upgrade, so it should keep everything fine.

If it kept its configuration, that would the ideal situation. 


Now I am thinking at the following strategy (everything being done remotely): 

As the celeronbox has 2 ubuntu dappers installed on it, both with remote login activated (vino, nx and openssh), maybe I should proceed like this:

I will upgrade one system and, before restarting, alter menu.lst from grub to automatically boot into the second system that has not been upgraded. From there I will mount the partition with the upgraded system and check in its configuration files whether automatic login and remote login for vino (the built-in vnc server) is still enabled. 

Thanks to another thread, I think that, for the automatic login, I have to look whether the /etc/gdm/gdm.conf-custom file of the upgraded system contains the following lines

```
 
[daemon]
AutomaticLogin=<username>
AutomaticLoginEnable=true

``` 

To make it simple, I will compare it to the file on the system that was not upgraded. 

However I don't know yet how to check whether vino is enabled.  

Having finished with both checks, I will edit menu.lst from grub to make it automatically boot into the upgraded system. 

Hoping that this strategy does make sense. 

Any idea or help will be appreciated. 

frafu

---

### Post by christhemonkey on 2006-10-15
That sounds all fine and dandy.

Let us know how it goes.

---

### Post by frafu on 2006-10-15
Reading other threads, I have found: 

Vino's configuration file is located in: 
~/.gonc/desktop/gnome/remote_access/


Yes, I will post the results here.

frafu

PS: Before upgrading, I have to check whether nx is compatible to edgy...

---

### Post by frafu on 2006-10-15
A few words about my upgrade from dapper to edgy: 

During the upgrade, the update manager asked me several times whether I wanted it to install the new configuration file or keep the old configuration file from dapper. (It asked it for the configuration file of my nfs server, for the configuration file of the vnc server,...) 

I told to the update manager to keep the old file (I did so for a few files, but not for every file about which it asked the question) and after restarting, I could connect with the vnc client. 

(As explained in a previous message, before booting to edgy, the computer booted to another system from where I could check edgy's configuration. But this step was useless, as I had nothing to change to the edgy configuration.) 

The upgrade to edgy also kept the remote login by ssh active which also worked right away. 

However the remote nx login did not seem to work anymore. While connecting with the nx client, it did not give me any error message, but the window with the desktop did not appear on the client side. 

So I decided to reinstall nx on edgy, but it gave me a version conflict error. Therefore, I removed the old nx from edgy (sudo aptitude purge nxserver, sudo aptitude purge nxnode, sudo aptitude purge nxclient and deleted the NX directory located in /usr) and after installing the new version of nx, I am again able to also connect remotely through nx. 


Hoping that this can be useful to somebody. 

frafu

---

### Post by Ruskie on 2006-10-20
When I upgraded **to** Dapper, openssh maintained its configuration, no question asked...

---

### Post by frafu on 2006-10-21
I assume it does not ask about the configuration of the openssh server because it is not included in the install cd. 

frafu

---

### Post by monsoon on 2006-10-31
> **frafu said:**
> A few words about my upgrade from dapper to edgy: 


So I decided to reinstall nx on edgy, but it gave me a version conflict error. Therefore, I removed the old nx from edgy (sudo aptitude purge nxserver, sudo aptitude purge nxnode, sudo aptitude purge nxclient and deleted the NX directory located in /usr) and after installing the new version of nx, I am again able to also connect remotely through nx. 


Hoping that this can be useful to somebody. 

frafu


Thanks! This helped me immensely.

-monsoon

---

