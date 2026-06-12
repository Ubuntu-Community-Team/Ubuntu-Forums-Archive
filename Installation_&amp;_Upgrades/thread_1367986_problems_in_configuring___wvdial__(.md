---
title: "problems in configuring   wvdial  :("
date: 2009-12-30
forum: Installation &amp; Upgrades
---

### Post by AM_SOS on 2009-12-30
hi all !
ubuntu 9.10 detects my CDMA modem but does't allow me to finally connect to the net.

i didn't have any difficulty in installing the packages needed for this -  wvdial  ,  libuniconf base , libuniconf extra , and libuniconf .
i have followed no particular order while installing these packages. hope this is not the cause of the problem.

to connect i was trying to configure the  wvdial  application. however, i have run up with some problems and although i can now get it to recognize the modem, i am still not able to connect and reach the final stage which displays for me the DNS server address etc.

first, when i make the changes in wvdial.conf , it doesn't allow me to save these changes. to work my way around this, i saved it as a separate file (Broadband_wvdial) on my desktop.

however, when i ran the   sudo wvdial   command i got the following messages at the end-

OK
--> Modem initialized.
--> Configuration does not specify a valid phone number.
--> Configuration does not specify a valid login name.
--> Configuration does not specify a valid password.

i suspect that it is not even reading the file i have saved on my desktop as   Broadband_wvdial  . This is where i have put in all the relevant settings.
The reason is that the wvdial window that comes up when i type    gedit /etc/wvdial.conf   in a Terminal window says that it is a Read Only file. therefore i am forced to save it as another file on the desktop.

can someone please help! :(

---

### Post by GeorgeVita on 2010-01-01
Hi **AM_SOS**, happy new year!

to edit /etc/wvdial.conf use (from terminal): ```
gksudo gedit /etc/wvdial.conf
```remove semicolons (**';'**) from Phone/user/pass lines and add there the appropriate contents. Usually you must add another line to skip 'old fashioned login': ```
Stupid mode = yes
``` and possibly you must set the APN (name of service for internet connection as your provider suggests). Example below uses APN=internet ```
AT+CGDCONT=1,"IP","internet"
```

Connect using ```
sudo wvdial
``` and post here your /etc/wvdial.conf and ALL terminal output (including your commands) to follow up.

Alternative: after creation of the communication ports (ex. /dev/ttyUSB0) try also the 'standard' way via network manager icon.

Regards,
George

---

