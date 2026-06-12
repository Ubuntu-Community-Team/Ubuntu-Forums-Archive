---
title: "need help: wireless wont connect if encrypted"
date: 2009-02-27
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by Kenobi on 2009-02-27
Hi,

I have a fresh Alpha 5 and installed the driver with ndisgtk without any problems and the wireless connections found pop up. But whenever I want to connect to an encrypted connection it tries and tries but cannot connect. Tried nm-applet and the built-in new network manager. Here is the output of iwevents:


ubuntu@ubuntu:~$ iwevent
Waiting for Wireless Events from interfaces...
22:14:47.748272   wlan0    Set Mode:Managed
22:14:47.748398   wlan0    Set Frequency:2.412 GHz (Channel 1)
22:14:47.756981   wlan0    Association Request IEs:000B4469676765722D4E657...201000050F20201000050F202
22:14:47.757901   wlan0    Association Response IEs:010882848B...432043048606C
22:14:47.758045   wlan0    New Access Point/Cell address:00:04:0E:38:55:A9
22:14:47.758045   wlan0    New Access Point/Cell address:Not-Associated
22:14:47.748272   wlan0    Set Mode:Managed
22:14:47.748398   wlan0    Set Frequency:2.412 GHz (Channel 1)
..(and so on) ...

On an Xubuntu 7.10 laptop I can access the net perfectly with nmapplet, and iwevent stops rightfully in line "Cell address:00:94..." Also I can connect to an unencrypted net and it ends at the same line.


Any ideas?
Thanks you so much,
Kenobi

---

### Post by Peter09 on 2009-02-28
What wireless driver are you using, I had this problem on an Aspire one running Intrepid, turned out to be a rubbish wireless driver.

---

### Post by trendyabinash on 2009-02-28
Ya it is a problem of jaunty with ndisgtk.

Kubuntu has said in it's release notes that after the first update it will work but I don't know how can I get the first update without any network connection.

Lets hope ubuntu guys will get it fixed soon, or else jaunty will be a JUNK for me

---

