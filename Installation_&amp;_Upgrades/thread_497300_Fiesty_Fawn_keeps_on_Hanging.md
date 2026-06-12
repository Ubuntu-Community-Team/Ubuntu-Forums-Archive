---
title: "Fiesty Fawn keeps on Hanging"
date: 2007-07-10
forum: Installation &amp; Upgrades
---

### Post by gbfoxbat on 2007-07-10
Hello,

Im new to Linux and recently replaced my Tablet PC windows XP with Ubuntu
I installed Fiesty fawn 7.04 via Netboot and all went well I have been using Ubuntu for a while and have been more or less happy the big problem that I have is that the KDE and also Gnome keeps on hanging from time to time this means approx 2 to 3 times a day. The only app's that I have installed apart from the usual package is the amsn (instant messenger)

The hardware is Toshiba Protege 3500 laptop with Intel Pentium III and 1 Gig RAM..... Im  lost as else alls well except this repeated hanging which makes life very frustrating, I am happy with Linux despite some issues that I had to overcome as network issues and USB issues which didnt activate after hibernation ( fixed these by browsing here) BUT this hanging is a real bummer and I need to always reboot. If I cant fix this then would have to abandon Ubuntu and get back to Win XP

 Can someone please help
Thxs

---

### Post by phidia on 2007-07-10
Have you looked in /var/log/messages or xorg.log to see if there is anything there that could help pinpoint the problem? What video card and driver are you using. This could be an xserver problem, but without more info or specifics it's hard to know. I wonder if this is happening when you're browsing certain media enhanced sites or using a particular app? If it is browser related you could try using a different browser e.g opera and observing the frequency or lack of hangs.

---

### Post by gbfoxbat on 2007-07-10
> **phidia said:**
> Have you looked in /var/log/messages or xorg.log to see if there is anything there that could help pinpoint the problem? What video card and driver are you using. This could be an xserver problem, but without more info or specifics it's hard to know. I wonder if this is happening when you're browsing certain media enhanced sites or using a particular app? If it is browser related you could try using a different browser e.g opera and observing the frequency or lack of hangs.

thanks for your reply. Im new how do I look at the log files. Plus I tried to install Opera and it was slow and then saw somewhere that its better to install Opera via the repository therefore removed it via adept (earlier had downloaded it from opera site) now the problem is via repository or adept cannot install Opera again i can choose request install but cannot apply changes.....

PS: the video card is Trident Micro systems V82 something saw that when trying to install Google earth and that doesn't work too...keeps on flashing. On the forum saw that one needs to install the latest Open source Trident driver downloaded that BUT I dont know how to install that on Linux...

Thanks for any help

---

### Post by gbfoxbat on 2007-07-10
> **phidia said:**
> Have you looked in /var/log/messages or xorg.log to see if there is anything there that could help pinpoint the problem? What video card and driver are you using. This could be an xserver problem, but without more info or specifics it's hard to know. I wonder if this is happening when you're browsing certain media enhanced sites or using a particular app? If it is browser related you could try using a different browser e.g opera and observing the frequency or lack of hangs.

Ok I figured out how to look at the /var/log/messages what should I look for there?

---

### Post by Odrodzona-Sarmacja on 2007-07-10
in the terminal:

>gksudo mousepad /etc/gamin/gaminrc

then add on the end of the file:

fsset ext3 poll 30

then save the document and your computer shouldn't hung so much often, even if it still does so.

The bug in this case is gam_service. Longer computer is on then more and more cpu it eats. Gam_server is a system service, so removing it is not advisable. However its function, which is to look to ext3 drives if any file changed on them can be effectively altered from couple trillions times per second (170% cpu on dual core cpu) every while or so to just 1 time every 30 secs. The standard delay time is just 10sec, as you can see yourself in gaminrc.

---

### Post by gbfoxbat on 2007-07-10
> **Odrodzona-Sarmacja said:**
> in the terminal:

>gksudo mousepad /etc/gamin/gaminrc

then add on the end of the file:

fsset ext3 poll 30

then save the document and your computer shouldn't hung so much often, even if it still does so.

The bug in this case is gam_service. Longer computer is on then more and more cpu it eats. Gam_server is a system service, so removing it is not advisable. However its function, which is to look to ext3 drives if any file changed on them can be effectively altered from couple trillions times per second (170% cpu on dual core cpu) every while or so to just 1 time every 30 secs. The standard delay time is just 10sec, as you can see yourself in gaminrc.

Thanks for the tip..i have done what you mentioned lets see if there are any differences in behavior

Thxs again

---

### Post by gbfoxbat on 2007-07-12
> **gbfoxbat said:**
> Thanks for the tip..i have done what you mentioned lets see if there are any differences in behavior

Thxs again

Well I found out that the main reason for this hanging or Crash is Evolution mail which is configured to get MS exchange server and was not running ( process were running despite that the app wasnt running) I have removed Evolution and Voila all's well so far at least..

Ubuntu hasnt crashed on me so far BTW used to crash approx 3 to 4 times a day at least no matter which app I was in

Not good news but for for me at least was a reliever.

---

### Post by fox_bat on 2007-07-15
> **gbfoxbat said:**
> Well I found out that the main reason for this hanging or Crash is Evolution mail which is configured to get MS exchange server and was not running ( process were running despite that the app wasnt running) I have removed Evolution and Voila all's well so far at least..

Ubuntu hasnt crashed on me so far BTW used to crash approx 3 to 4 times a day at least no matter which app I was in

Not good news but for for me at least was a reliever.
 

Well tried everything and then today switched to Debian 4. That doesnt crash ubuntu in my experience has been a nightmare to get it working on a laptop with 1.7Mhz CPU and 1 gig RAM plus 40 Gig harddisk....:(

---

