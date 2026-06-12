---
title: "Xbuntu and screen res??????"
date: 2007-09-02
forum: Installation &amp; Upgrades
---

### Post by keiffee30 on 2007-09-02
I have installed Xbuntu 7.04 on to my main PC now (spec to follow) as "Werdos" crashed on me with yet another virus. So what i had done is to install Xbuntu then run windows in a Vbox and install Windows XP in there 

This i need as i still like to play my games and i have to run a video editing app called pinnical. 

Now to the problem i have. Im running a nvidia 9200 Video card xbuntu is running with it but i can not get a better screen res other that 800x600. I do run my screen res @ 1024x768 or higher. I have look at the nvidia posts but im not sure if i should run with the install as when i look in the /etc/x11/xorg.conf file i said ...

Section "Device"
    Identifier     "ATI Technologies Inc RV280 [Radeon 9200]"
    Driver         "nvidia"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "ATI Technologies Inc RV280 [Radeon 9200]"
    Monitor        "Generic Monitor"
    DefaultDepth    24
    SubSection     "Display"
        Depth       1
        Modes      "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       4
        Modes      "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       8
        Modes      "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       15
        Modes      "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       16
        Modes      "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       24
        Modes      "1024x768" "800x600" "640x480"

so it looks to me that Xbuntu has loaded the Nvidia drivers. the bit i did see that didn't look right was the monitor section .....

Section "Monitor"
    Identifier     "Generic Monitor"
    HorizSync       28.0 - 51.0
    VertRefresh     43.0 - 60.0
    Option         "DPMS"

Im using a NCE MultiSync LCD 1760nx. Is there anything i can do to better my screen res. I would live to start playing X2 again.

---

### Post by banewman on 2007-09-02
In the terminal run sudo dpkg-reconfigure xserver-xorg and slooowly go through the options. The defaults will be right exept for video card and screen resolution. Pick the video card driver that best matches the card and make sure that the screen resolutions are checked to at least 1024x768. lol :)

---

### Post by Pumalite on 2007-09-02
Install from here:

[http://ati.amd.com/support/driver.html](http://ati.amd.com/support/driver.html)

Or here:

[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

(Your card is ATI not Nvidia)

---

### Post by keiffee30 on 2007-09-02
banewman i tried your fix but i must of bugger it up as the xserver will now not run. I have to load puppy 2.17 and mout the /etc/x11/xorg.conf.backup to get things back

as im not very good at the linux bit is there anything else that i could try ?

Pumalite 

Will envy work with Xbuntu. So do you feel that this is still a driver problem and not a LCD problem?


Many thanks for both of your posts

---

### Post by Pumalite on 2007-09-02
Your LCD is certainly a problem. You need a driver that will handle it. It will work with Xubuntu.

---

### Post by keiffee30 on 2007-09-02
ok i have installed envy and all is ok with this 

i tried to install the nVidia driver opition and There was an error in the installation process. You can see the log file **/var/log/envy-installer.log**

the log file said 
[B]
python pulse.py nvidia
root@GamesXP:/usr/share/envy# python pulse.py nvidia
ENVY ERROR: Nvidia card not found[/B]

So i tried the install AIT driver and got the envy terminal window 
[B]
python pulse.py ati
root@GamesXP:/usr/share/envy# python pulse.py ati
Ubuntu Feisty 32bit
Your graphic card has been detected as a AIT Radeon 9250/9200 Series
Your graphic card is supported by the legact Driver
ENVY ERROR: ATI's legacy driver dose not support your operative system
[/B]

so is there anything else i could try ? or should i install Ubuntu or Edbuntu 7.04

---

### Post by Pumalite on 2007-09-02
Post your specs and I'll try to help you choose what's best for you in terms of OS.

---

### Post by keiffee30 on 2007-09-02
ok no problems

Shuttle XPC
P4 3.00Ghz HT
1Gb RAM (i think its PC3200)
82801 PCI Bridge
NetXtreme BCM5705 Gigabit Ethernet
2 x 300 Gb SATA Software RAID 0 ( would you like to know how i have configured the drives
AIT Radeon 9200
AC'97 ALSA Sound card (working nicely)

is there anything else you would like to know about the PC setup ?

---

### Post by Pumalite on 2007-09-02
Try 7.04 with this: [https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)

---

### Post by keiffee30 on 2007-09-02
7.04 is that ....

Ubuntu
Edbuntu
Xbuntu

as i am already using Xbuntu 7.04

as for the RAID that is going to help a lot thanks

---

### Post by Pumalite on 2007-09-02
I would go for Ubuntu 7.04: [http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)
Choose Alternate CD (I think it can be used with Raids)). Mark the box below 'Start Download' ( Alternate because your video card might be a problem)

---

### Post by K.Mandla on 2007-09-02
Note that your card is not an Nvidia card, so you should be using the ATI driver instead. That's probably why you're getting the wrong resolution; the driver is unable to work your card.

---

### Post by keiffee30 on 2007-09-02
ok i have now downloaded ubuntu and just burning it to CD now

i now know that i have got a AIT and not a Nvidia card

many thanks for all of your time in this post

---

