---
title: "Upgradation"
date: 2012-05-26
forum: Installation &amp; Upgrades
---

### Post by siddhantsinha on 2012-05-26
I was upgrading my Ubuntu to 12.04 LTS...during upgradation my laptop suddenly shut down...and when i restarted it there is one recovery console coming and i tried to do many things..bt there was no result...please help me..!!!

---

### Post by kc1di on 2012-05-26
> **siddhantsinha said:**
> I was upgrading my Ubuntu to 12.04 LTS...during upgradation my laptop suddenly shut down...and when i restarted it there is one recovery console coming and i tried to do many things..bt there was no result...please help me..!!!

you didn't give us much to go on here. but this is what I would do
get a copy of the 12.04 live cd. 

when it boots up got to /etc/apt/sources.list and comment out everything but the cd disk.

then in a terminal type the following:

```
sudo apt-get update
sudo apt-get dist-upgrade
```
it should upgrade from the disk and they you can uncomment the other repositories and you should be fine. 

here the ubuntu documentation that may be of help.

[https://help.ubuntu.com/community/AptCdrom]("https://help.ubuntu.com/community/AptCdrom")

Here is what the apt/sources.lists file looks like.
[IMG]http://ubuntuone.com/5okOPDnDXl1nNidWPVZJ55[/IMG]

you will have to go to a terminal and type: 
```
sudo gedit
```
enter you password when asked and then navigate to and open the /etc/apt/sources.list file and modify it. You comment out lines by place an # in front of it uncomment the CD lines and comment out all other save the file and run the commands above.

---

