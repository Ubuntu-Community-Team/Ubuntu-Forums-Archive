---
title: "Install problems"
date: 2013-03-28
forum: Installation &amp; Upgrades
---

### Post by Terryl2 on 2013-03-28
Howdy all,

I have a Dell Vostro 1510 that has a widows vista problem, and without the install disks is worthless, I am trying to install Ubuntu on it an it is having some problems.

I have installed Ubuntu on other Dells and have never had a problem.

I have downloaded the ISO file to a DVD and it runs, but after about ten or so it comes up with the following error.

"General error mounting file system"

"A maintenance shell will now be started"

"Control D will terminate this and reboot the system"

"root@ubuntu:~#"


And just sits there, what next?

---

### Post by fantab on 2013-03-28
Sounds like a bad burn. 
First of all check the integrity of the downloaded ubuntu.iso with [MD5SUM Check]("https://help.ubuntu.com/community/HowToMD5SUM")... then reburn the .iso to disk, burn it at the slowest speed possible.

---

### Post by Terryl2 on 2013-03-30
> **fantab said:**
> Sounds like a bad burn. 
First of all check the integrity of the downloaded ubuntu.iso with [MD5SUM Check]("https://help.ubuntu.com/community/HowToMD5SUM")... then reburn the .iso to disk, burn it at the slowest speed possible.


OK, thanks Fantab that did the trick, it's up and running.

Now the only problem I have is that it will not see the USB modem, I have gone through the site and found a bunch of stuff about adding this and adding that and doing some programming on how to enable the modem but I am a hardware guy, the programming is beyond me.


Is there a simple way to see the modem? In windows you look at the system hardware, there you see all the hardware that has a problem, maybe I am missing some thing but I do not see the same type of section or folder.

---

### Post by darkod on 2013-03-30
Are you talking about 3g usb modem for mobile internet?

Depending on the chipset it should usually work, but sometimes the problem is that these modems are designed for windows (like most other hardware, thank the manufacturers for that), and have parts that try to launch when plugged in. Linux doesn't work in that way, and this can often interfere with using the modem.

The first thing you could try is opening Network Manager and in the Mobile tab simply create new connection with the correct APN according to your mobile provider. See if it can establish the connection. I'm not sure if it's best to have the PIN disabled on the SIM, or it doesn't matter.

---

### Post by Terryl2 on 2013-03-30
No, it is a USB modem that connets to a phone line, it is a Conexant RD02-D400 from Dell.

I have gone through all the posts about this type of modem, and have done my best to try and get it to work following those instuctions, or even be seen by the system and show up somewhere to set it up.

But have got no where fast, is there something I am not doing right?

How do I even see this modem?

When I do the "lsusb" command in that terminal program I get this back.

Bus 001 Device 002: ID 0c45:63e0 Microdia Sonix Integrated Webcam
Bus 006 Device 002: ID 0572:1324 Conexant Systems (Rockwell), Inc. 
Bus 006 Device 003: ID 19ff:0226 Dynex 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


So the modem is showing up somewhere.

---

### Post by darkod on 2013-03-30
I don't remember all the options in Network Manager right now, but I think there is an option similar to Dial-Up in windows. Because a usb modem would actually be like dial up, you have your username/password from the provider. There will be fields you need to fill up with the data from your ISP, and that should be it.

For further instructions you can google how to set it up in ubuntu going by the manufactuer and model code ID: 0572:1324. But I think you simply need to make the dial up connection, the modem seems recognized all right. Even in windows you need to set up the dial up connections for usb modems.

---

### Post by Terryl2 on 2013-03-30
OK I will check into that, but where in the heck do I even see this modem, without going to that terminal program?

---

### Post by darkod on 2013-03-30
What exactly do you want to see? It's there, it's working. What else do you need?

To be honest, I have never searched for any program/menu similar to Device Manager in windows, where it lists all hardware. There is something like System Info I believe, but I'm not sure it lists literary all hardware.

The modem is there, if you don't need any special drivers and if ubuntu can use it by default, you only open Network Manager and enter the details of your ISP, case closed.

---

### Post by darkod on 2013-03-30
I just double checked: If you click the Network Manager icon top right (close to the time on the top bar), select Edit Connections... After that select the DSL tab, click Add and look around in the options. There are fields for username and password, also there are more options in the PPP and IPv4 tabs, but usually you wouldn't need to touch those options.

Try first by entering only the username and password, and see if it connects. If you need to add or change anything, you can edit the connection later again.

---

### Post by Terryl2 on 2013-04-01
OK something crashed, I'm having to re-install the system, it went to a totaly black screen and sat there for about an hour, restarting the laptop did the same thing and did nothing.

I can't be leave that trying to install or getting this system to recognize and display anywhere it the system settings, network settings or anywhere a simple Dell provided _USB dial up modem_ can be this difficult.

But maybe I should be asking this in the hardware section of this forum as my original problems seam to be fixed. (other then the crash part)

---

### Post by arpanaut on 2013-04-01
Have you seen this:
[https://help.ubuntu.com/community/DialupModemHowto/Conexant](https://help.ubuntu.com/community/DialupModemHowto/Conexant)

It's a little outdated but you may be able to contact Dell and see if they have an updated driver.
Too bad Conexant does not supply linux drivers, good for Dell for trying to provide such.

---

### Post by Terryl2 on 2013-04-01
Ok it's back, I had to do a clean re-install to get it back.

And I just cant be leave that installing a simple external USB dial up modem can be so difficult.

---

