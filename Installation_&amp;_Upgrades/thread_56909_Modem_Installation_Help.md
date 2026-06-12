---
title: "Modem Installation Help"
date: 2005-08-14
forum: Installation &amp; Upgrades
---

### Post by ray27 on 2005-08-14
I am a newbie to Linux and have been trying for a week to install a modem.
I have US Robotics 56 K external fax modem model 5686E.
This modem works well on Win 98SE. So far I have run the utility pppconfig. After rebooting and typing sudo pon I get this message.

"/usr/sbin/pppd in file /etc/ ppp/peers/provider: unrecognized option /dev/modem."

Incidentally I took out a Best winmodem because I couldn't get the drivers to load.

This modem is supposed to work with little problem. Help what am I doing wrong or is there an easier installation method.

I have been around computers for 25 years and weathered DOS. Fortran, Windows.
At this rate I may go back to Windows, at least I can install modem there.

At least with dos there was plenty of consistent information and good examples.

Thank You

Ray Fuller

---

### Post by OwlManAtt on 2005-08-14
[QUOTE=ray27]I am a newbie to Linux and have been trying for a week to install a modem.
I have US Robotics 56 K external fax modem model 5686E.
This modem works well on Win 98SE. So far I have run the utility pppconfig. After rebooting and typing sudo pon I get this message.

"/usr/sbin/pppd in file /etc/ ppp/peers/provider: unrecognized option /dev/modem."

Incidentally I took out a Best winmodem because I couldn't get the drivers to load.

This modem is supposed to work with little problem. Help what am I doing wrong or is there an easier installation method.[/QUOTE]
Have you seen the Ubuntu wiki page on setting up modems? 

[DialupModemHowto](https://wiki.ubuntu.com/DialupModemHowto)

It advises you to first attempt to set your modem up with the networking tool. Your problem sounds suspiciously like the modem device is not /dev/modem, or you have a misconfiguration somewhere. The GUI tool should be able to help you out.

---

### Post by ray27 on 2005-08-14
That is the reference I used to try setting it up and the resulting message was as stated.
Ray

---

### Post by ray27 on 2005-08-14
[QUOTE=OwlManAtt]Have you seen the Ubuntu wiki page on setting up modems? 

[DialupModemHowto](https://wiki.ubuntu.com/DialupModemHowto)

It advises you to first attempt to set your modem up with the networking tool. Your problem sounds suspiciously like the modem device is not /dev/modem, or you have a misconfiguration somewhere. The GUI tool should be able to help you out.[/QUOTE]
 It is not /dev/modem if that means internal modem . how do i get that reference out of the system. When i orinally tried setting up the system modem how to said try putting in dev/modem for for an internal modem. Now I cant get rid if the notation.
Ray

What is the gui tool and where do I find it?

---

### Post by OwlManAtt on 2005-08-14
[QUOTE=ray27]What is the gui tool and where do I find it?[/QUOTE]The GUI tool can be found in System > Administration > Networking. The System menu should be right next to Places and Applications in GNOME.

---

### Post by ray27 on 2005-08-14
[QUOTE=OwlManAtt]The GUI tool can be found in System > Administration > Networking. The System menu should be right next to Places and Applications in GNOME.[/QUOTE]
 Thanks
I will give it a try.

Ray

---

