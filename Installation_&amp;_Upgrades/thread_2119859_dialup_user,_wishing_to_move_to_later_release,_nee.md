---
title: "dialup user, wishing to move to later release, need some advice."
date: 2013-02-25
forum: Installation &amp; Upgrades
---

### Post by ramidavis on 2013-02-25
Hello everyone!
Not really had a reason to post here in a while, but now...
I am in a bit of a situation here, and need some advice.
Currently, I am at Ubuntu 11.04, been using it since it came out ... and it is time to move on I believe.

I am on dial-up now, so I had to find a post on some blog explaining how to get dial-up setup for 11.04, download everything I needed in windows, and install it after a fresh 11.04 install by hand.

I go to town and use the Wi-Fi at the library about twice a month, so hopefully on my next trip there, I can get everything in order for my move to 12.10 / 12.04 .

Now that I am thinking about going to 12.10 (or possibly 12.04 since that one is LTS), what all should I download and have ready to go?

This is not going to be an upgrade, but a clean fresh install. I always prefer a fresh install. Clean slate to work with.

I am assuming I will need the latest versions of gnome-ppp, libuiconf, libwvstreams-base, libwvstreams-extras, and wvdial (At least, that is what I had to download for 11.04 to get my USRobotics usb modem working.)

I would prefer installing from USB again this time, as i am pretty much out of discs... 11.04 had a usb-creator.exe right on the disk, and I just used that (after mounting the .iso to a virtual cd drive in windows) to write the .iso I downloaded at the library to a usb stick, and install off that.

Looking at the .iso of 12.10 I just got (got back from the last library trip, did not get 12.04 downloaded yet), I am not seeing an usb-creator.exe . I know there is "system> administration> startup disc creator" here in 11.04 , will that make a proper usb image for 12.04 / 12.10, or is it just meant for 11.04?

Sorry for so many questions at once, but I just want to have everything ready to go, no hassles, especially since I am on dial-up now, and that does not seem to work with Ubuntu out-of-the-box.

Hope that is clearer for everyone now?

---

### Post by meteorrock on 2013-02-25
TL: DR

What going on? You need help with something but I can not figure it out in that large block of rambling. Please simplify for me and others.

---

### Post by ramidavis on 2013-02-25
I am planning to move to either ubuntu 12.04 because it is LTS, or ubuntu 12.10 because it is newer.

I am on dial up, so i will not have any internet after i install.
What do i need to go download so i can get on line with ubuntu 12.04 or ubuntu 12.10?

---

### Post by ramidavis on 2013-02-25
Really? No one has anything to say and try to help me?

---

### Post by Bashing-om on 2013-02-25
ramidavis; Hi !

As I understand it, dial up capabilities are available on the installation.
see:
[https://help.ubuntu.com/community/DialupModemHowto/SetUpDialer](https://help.ubuntu.com/community/DialupModemHowto/SetUpDialer)

Do the homework and then:
```
sudo pppconfig
``` to start the dial up service.
[INDENT][INDENT]just try'n to help

[/INDENT][/INDENT]

---

