---
title: "youtube can't play in Opera browser"
date: 2010-01-12
forum: Installation &amp; Upgrades
---

### Post by hoboy on 2010-01-12
I have just installed Opera browser, but youtube video can play.
I am getting the following error
 you either have JavaScript turned off or an old version of Adobe's Flash Player.
I am using Linux ubuntu 2.6.31-17-generic #54-Ubuntu SMP Thu Dec 10 17:01:44 UTC 2009 x86_64 GNU/Linux

---

### Post by tommcd on 2010-01-12
> **hoboy said:**
> 
I am getting the following error
 you either have JavaScript turned off or an old version of Adobe's Flash Player.
I am using Linux ubuntu 2.6.31-17-generic #54-Ubuntu SMP Thu Dec 10 17:01:44 UTC 2009 x86_64 GNU/Linux
Do you have the java plugin installed? Open a terminal and run:
```
aptitude search sun-java6
```
Look at he output. I "p" before the package means it is not installed. An "i" before the package means it is installed. Make sure you have sun-java6-jre, sun-java6-bin, and sun-java6-plugin installed. If you do no then install them:
```
sudo apt-get install sun-java6-jre sun-java6-plugin

```
Of course, make sure you have the flash plugin installed as well.

---

### Post by gradinaruvasile on 2010-01-12
Ummm.. you need flashplayer, not java for youtube...

sudo apt-get install flashplugin-installer

---

### Post by hoboy on 2010-01-12
> **gradinaruvasile said:**
> Ummm.. you need flashplayer, not java for youtube...

sudo apt-get install flashplugin-installer

It is not working still after i have tried the suggestions.
great browser but hard to find flash player for youtube videos

---

### Post by Linuxforall on 2010-01-12
Are you on x64 Ubuntu or x32?

---

### Post by pricetech on 2010-01-12
If I'm reading correctly, you have a 64 bit OS.  The process is a little different.  From my "notes to self":

Download the 64 bit Flash Player from Adobe Labs
[http://labs.adobe.com/downloads/flashplayer10_64bit.html](http://labs.adobe.com/downloads/flashplayer10_64bit.html)

Unzip it and copy it to the following locations:
/usr/lib/mozilla/plugins
/usr/lib/opera/plugins
/home/username/.mozilla/plugins

NOTES:
You won't have an opera folder if you don't have Opera installed.
The word "username" refers to your username.
The .mozilla folder is hidden so you'll need to view hidden files to see it.

After that it should work.

---

### Post by Linuxforall on 2010-01-12
If you have installed the non free adobe plugins from the repository, make sure to mark complete uninstall before you do anything and also make sure nspluginwrapper is removed. Then just untar and copy libflashplayer.so to /usr/lib/mozila/plugins and Opera picks it up from that folder.

---

### Post by hoboy on 2010-01-13
It seemed like one can not have bough Firefox and Opera installed on the same computer then make bough play youtube videos, when if any body has done it i will like to know how.

---

### Post by Sef on 2010-01-13
> It seemed like one can not have bough Firefox and Opera installed on the same computer then make bough play youtube videos, when if any body has done it i will like to know how.


Flash 64-bit works for me in both.   I have 64-bit Ubuntu with Opera 10.10 and Firefox 3.5.7.

---

### Post by hoboy on 2010-01-13
> **Sef said:**
> Flash 64-bit works for me in both.   I have 64-bit Ubuntu with Opera 10.10 and Firefox 3.5.7.

Please tell me how you have install Flash 64-bit ?
and a link to the download ? 
Flash 64-bit works for me in both. I have 64-bit Ubuntu with Opera 10.10 and Firefox 3.5.7.

---

### Post by Linuxforall on 2010-01-13
I have alpha x64 Flash working fine on FF, Opera and Google Chrome here.

---

### Post by hoboy on 2010-01-13
> **Linuxforall said:**
> I have alpha x64 Flash working fine on FF, Opera and Google Chrome here.

How did you installed it specifically ?
then I will try that.
where is the link to the flash version you have intalled

---

### Post by Linuxforall on 2010-01-13
Make sure you have removed all previous flash including nsplugin wrapper. Then download flash alpha x64 and untar, then in terminal do a mv libflashplayer.so /usr/lib/mozila/plugins 

Thats as simple as is.

---

### Post by hoboy on 2010-01-13
> **Linuxforall said:**
> Make sure you have removed all previous flash including nsplugin wrapper. Then download flash alpha x64 and untar, then in terminal do a mv libflashplayer.so /usr/lib/mozila/plugins 

Thats as simple as is.

Ok tks I think my question do you know the console command to remove all the flash ?

---

### Post by Linuxforall on 2010-01-13
Go to synaptic and check all references to flash and mark then complete uninstall and also make sure nsplugin is marked as well.

---

### Post by hoboy on 2010-01-13
> **Linuxforall said:**
> Go to synaptic and check all references to flash and mark then complete uninstall and also make sure nsplugin is marked as well.

tks for your time I will do that.

---

### Post by Linuxforall on 2010-01-13
You are welcome, post back your success or failure.

---

### Post by hoboy on 2010-01-13
> **Linuxforall said:**
> You are welcome, post back your success or failure.
when I run this 
/Desktop/install_flash_player_10_linux$ ./flashplayer-installer 
errors
ERROR: Your architecture, \'x86_64\', is not supported by the
       Adobe Flash Player installer.


/Desktop/install_flash_player_10_linux$ sudo mv libflashplayer.so /usr/lib/mozila/plugins
then errors
mv: cannot move `libflashplayer.so' to `/usr/lib/mozila/plugins': No such file or directory
but when I use Ctrl h I can see 
where did you download your flash version ?

---

### Post by Linuxforall on 2010-01-13
> **hoboy said:**
> when I run this 
/Desktop/install_flash_player_10_linux$ ./flashplayer-installer 
errors
ERROR: Your architecture, \'x86_64\', is not supported by the
       Adobe Flash Player installer.


/Desktop/install_flash_player_10_linux$ sudo mv libflashplayer.so /usr/lib/mozila/plugins
then errors
mv: cannot move `libflashplayer.so' to `/usr/lib/mozila/plugins': No such file or directory
but when I use Ctrl h I can see 
where did you download your flash version ?


[http://download.macromedia.com/pub/labs/flashplayer10/libflashplayer-10.0.42.34.linux-x86_64.so.tar.gz](http://download.macromedia.com/pub/labs/flashplayer10/libflashplayer-10.0.42.34.linux-x86_64.so.tar.gz)

Sorry for typo, should be double l for mozilla mv libflashplayer.so /usr/lib/mozilla/plugins

---

### Post by hoboy on 2010-01-13
> **Linuxforall said:**
> [http://download.macromedia.com/pub/labs/flashplayer10/libflashplayer-10.0.42.34.linux-x86_64.so.tar.gz](http://download.macromedia.com/pub/labs/flashplayer10/libflashplayer-10.0.42.34.linux-x86_64.so.tar.gz)

Sorry for typo, should be double l for mozilla mv libflashplayer.so /usr/lib/mozilla/plugins

I don't know who you are and where you are in this world, but tks so much you safe my day.. it is working perfectly.

---

### Post by Linuxforall on 2010-01-13
> **hoboy said:**
> I don't know who you are and where you are in this world, but tks so much you safe my day.. it is working perfectly.

:) Glad it worked out for you, now enjoy the flash movies.

---

