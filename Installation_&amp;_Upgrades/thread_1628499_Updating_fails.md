---
title: "Updating fails"
date: 2010-11-22
forum: Installation &amp; Upgrades
---

### Post by george3095 on 2010-11-22
Just during the last three days, when running Update Manager, clicking Check, downloading all available updates, then Clicking Install Updates, the Downloading Files window pops up but it is blank. and it stays blank. The little rotating icon indicates something's going on but, NO. Nothing has happened, even after a couple of hours. Trying to close Downloading Files brings up a window to Force Quit. Then trying to close Update Manager has no effect. to shorten the story, finally a window pops up saying that the "AT SPI Registry" is not responding. I'm sure trying the same thing will not yield different results.

How serious is this. I'm running 10.04.

---

### Post by sikander3786 on 2010-11-23
Please post the output of

```
sudo apt-get update
```

```
sudo apt-get upgrade
```

There has been a bug regarding your issue.

[https://bugs.launchpad.net/ubuntu/+source/at-spi/+bug/577113](https://bugs.launchpad.net/ubuntu/+source/at-spi/+bug/577113)

---

### Post by tanvi on 2010-11-24
hi...
 i am also having the similar issue..  

Result i get , aftr sudo apt-get update is ---


sudo: /etc/sudoers is mode 0442, should be 0440
sudo: no valid sudoers sources found, quitting


plz help.....

---

### Post by srikanth.gundaz on 2010-11-24
> **tanvi said:**
> hi...
 i am also having the similar issue..  

Result i get , aftr sudo apt-get update is ---


sudo: /etc/sudoers is mode 0442, should be 0440
sudo: no valid sudoers sources found, quitting


plz help.....
Hi tanvi, 
Your user account permissions has been changed. Dont worry. Here is the solution. 
Open terminal and type the following, 
sudo chmod -R 0440  /etc/sudoers
For further problems refer, 
[http://www.srikanthkabadi.blogspot.com/]("http://www.srikanthkabadi.blogspot.com/")

---

### Post by srikanth.gundaz on 2010-11-24
> **george3095 said:**
> Just during the last three days, when running Update Manager, clicking Check, downloading all available updates, then Clicking Install Updates, the Downloading Files window pops up but it is blank. and it stays blank. The little rotating icon indicates something's going on but, NO. Nothing has happened, even after a couple of hours. Trying to close Downloading Files brings up a window to Force Quit. Then trying to close Update Manager has no effect. to shorten the story, finally a window pops up saying that the "AT SPI Registry" is not responding. I'm sure trying the same thing will not yield different results.

How serious is this. I'm running 10.04.
Hi george3095, 
try using this.
Open terminal and type
sudo apt-get install -f
After this type 
sudo apt-get update

---

### Post by george3095 on 2010-11-24
I appreciate the responses to fix the problem. What I did (which did not turn out as GREAT as I expected) was to start all over forget 10.04, and install 10.10. Even this was not a easy and smooth as I expected. In fact, I've been forced to install it a second time because the first time had weird and bizarre results. Instead of being more refined, it was clunkier.

---

### Post by tanvi on 2010-11-26
> **srikanth.gundaz said:**
> Hi tanvi, 
Your user account permissions has been changed. Dont worry. Here is the solution. 
Open terminal and type the following, 
sudo chmod -R 0440  /etc/sudoers
For further problems refer, 
[http://www.srikanthkabadi.blogspot.com/]("http://www.srikanthkabadi.blogspot.com/")




Hi..

I tried the cmnd but again got the same error:

sudo: /etc/sudoers is mode 0442, should be 0440
sudo: no valid sudoers sources found, quitting

Also, read ur blog bt cudnt find solution to this issue..  :(

Need more suggestions....

---

### Post by srikanth.gundaz on 2010-11-27
> **tanvi said:**
> Hi..

I tried the cmnd but again got the same error:

sudo: /etc/sudoers is mode 0442, should be 0440
sudo: no valid sudoers sources found, quitting

Also, read ur blog bt cudnt find solution to this issue..  :(

Need more suggestions....

Here is perfect solution. Open terminal and type **su**. It will ask for your password. Enter your password and now the terminal prompt changes to **#** from **$**.
Now type the following.
[B]chmod 0440 /etc/sudoers
chmod 777 /etc/sudoers.d/
chmod 0440 /etc/sudoers.d/README[/B]

That's it.  Your problem is solved :)

---

### Post by srikanth.gundaz on 2010-11-27
> **tanvi said:**
> Hi..

I tried the cmnd but again got the same error:

sudo: /etc/sudoers is mode 0442, should be 0440
sudo: no valid sudoers sources found, quitting

Also, read ur blog bt cudnt find solution to this issue..  :(

Need more suggestions....

Here is perfect solution. Open terminal and type su. It will ask for your password. Enter your password and now the terminal prompt changes to # from $.
Now type the following.
chmod 0440 /etc/sudoers
chmod 777 /etc/sudoers.d/
chmod 0440 /etc/sudoers.d/README

That's it. Your problem is solved :)

---

### Post by tanvi on 2010-12-06
> **srikanth.gundaz said:**
> Here is perfect solution. Open terminal and type su. It will ask for your password. Enter your password and now the terminal prompt changes to # from $.
Now type the following.
chmod 0440 /etc/sudoers
chmod 777 /etc/sudoers.d/
chmod 0440 /etc/sudoers.d/README

That's it. Your problem is solved :)



Hi, when i type 'su' , it doesnt accept the password (simply says authentication failure);

I came to know that the sudo has broken. but donno hw to fix it. :-/

---

### Post by srikanth.gundaz on 2010-12-06
> **tanvi said:**
> Hi, when i type 'su' , it doesnt accept the password (simply says authentication failure);

I came to know that the sudo has broken. but donno hw to fix it. :-/

If you have root access, then login as root and carry out same procedure as given in my last reply. That will surely solve your problem :)

---

### Post by george3095 on 2011-02-13
OK, here are the results of "sudo apt-get update" (It's a lot of stuff - hope it helps:

george@Presario-Ubuntu:~$ sudo apt-get update
[sudo] password for george: 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security Release.gpg
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid Release.gpg                  
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid Release.gpg                   
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/main Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/restricted Translation-en_US
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/main Translation-en_US
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/restricted Translation-en_US
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/universe Translation-en_US
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/multiverse Translation-en_US
Ign [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) lucid/partner Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/universe Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/multiverse Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates Release.gpg
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/main Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/universe Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/multiverse Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security Release                
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid Release                       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid Release                       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/main Packages                    
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid/partner Packages              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/restricted Packages              
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid/partner Sources               
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/main Packages                 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/multiverse Sources
Reading package lists... Done

---

### Post by george3095 on 2011-02-13
And here are the results of "....upgrade"

george@Presario-Ubuntu:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
george@Presario-Ubuntu:~$

---

