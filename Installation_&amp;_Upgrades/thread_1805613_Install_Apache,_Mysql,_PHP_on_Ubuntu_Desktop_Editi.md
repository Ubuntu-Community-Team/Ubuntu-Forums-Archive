---
title: "Install Apache, Mysql, PHP on Ubuntu Desktop Edition via Ubuntu Server CD"
date: 2011-07-16
forum: Installation &amp; Upgrades
---

### Post by cazzy on 2011-07-16
Hi,
 
I am running *Windows XP Pro* and the latest edition of *Virtualbox*. I installed Ubuntu 11.04 **Server Edition** on a Virtual Drive within the latest version of Virtualbox. I also installed Apache, Mysql and PHP after selecting the LAMP installation option on the server CD. Unfortunately, I do not have the time to learn how to access and use Apache, Mysql, and PHP via the terminal. I am a GUI person!
 
I therefore _created another virtual drive and installed Ubuntu 11.04 **Desktop Edition** on the new virtual drive in Virtualbox_. I connect to the internet via a mobile phone at expensive rates, so I [COLOR=red]do not[/COLOR] want to [COLOR=red]download the Apache, Mysql, PHP software directly from the repository[/COLOR] via my Ubuntu Desktop Edition. I would prefer to [COLOR=green]install Apache, Mysql and PHP directly from the .iso file that I have for the Ubuntu 11.04 Server[/COLOR].
 
**My Question is:**
[COLOR=darkred]What are the series of commands that I must type into the terminal window within Ubuntu 11.04[/COLOR] **[COLOR=darkred]Desktop[/COLOR]** [COLOR=darkred]**Edition** to retrieve and install the Apache, Mysql and PHP files from the Ubuntu 11.04 Server ISO file[/COLOR] (the .iso file is enabled/mounted in Virtualbox as a CD)[COLOR=darkred]?[/COLOR]
 
I have searched the internet for hours and have yet to achieve my aforementioned objective.
 
I would be most appreciative if you could advise me.
 
Kind Regards,
Cazzy

---

### Post by tgalati4 on 2011-07-16
sudo apt-get install tasksel
sudo tasksel
choose lamp

---

### Post by cazzy on 2011-07-18
> **tgalati4 said:**
> sudo apt-get install tasksel
sudo tasksel
choose lamp
 
Hi, thanks for responding. I tried this, it does not work on the desktop version of Ubuntu. 
 
I need to know the series of commands to grab Apache, PHP and Mysql from the mounted .iso for the Ubuntu server CD and install it on the active Ubuntu Desktop Edition. Do you know how to do this or is this even possible?
 
I look forward to your response.
 
Kind Regards,
Cazzy

---

### Post by cazzy on 2011-07-19
> **cazzy said:**
> 
 
**My Question is:**
[COLOR=darkred]What are the series of commands that I must type into the terminal window within Ubuntu 11.04[/COLOR] **[COLOR=darkred]Desktop[/COLOR]** [COLOR=darkred]**Edition** to retrieve and install the Apache, Mysql and PHP files from the Ubuntu 11.04 Server ISO file[/COLOR] (the .iso file is enabled/mounted in Virtualbox as a CD)[COLOR=darkred]?[/COLOR]
[COLOR=#8b0000][/COLOR] 

 
Does anybody know if this is even possible?

---

