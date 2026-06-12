---
title: "[SOLVED] System gets hanged after few minutes"
date: 2008-11-18
forum: Installation &amp; Upgrades
---

### Post by trendyabinash on 2008-11-18
I am using a HUAWEI EC325 modem to connect to net.
i have followed the following steps to connect to net in ubuntu but it is hanging after 3 to 4 mins of connection what shall I do??
> step1. booted the PC Linux and logged in as root
step2. plugged in the usb cable attached to the modem (connected the USB modem to computer)
step3. in the command prompt just issued:
       prompt> dmesg | tail
  it showed me messages like kernal deteted the USB modem.
  now 50% of the work is over.

step4. issued the following command
       prompt > wvdialconf /etc/wvdial.conf
  this program probed my modem and collected all the informaton requied and kept it in /etc/wvdial.conf

step5. opened the /etc/wvdial.conf and added the phone number (#777 for reliance) to dial and username, password
    prompt> vi /etc/wvdial.conf
    You need not add any more lines, already corrsponding lines will be there in the file (as commented)
    You just need to edit them.
step6. Now you are ready to connect to internet.
    prompt>wvdial
    it will take few seconds to get the ip address using DHCP. and corresponding info will be displayed
    in your terminal.
    Now you can open your browser and start browsing.

Enjoy the Internet!.

Oh forgot to tell how to disconnect.
step 1. once wvdial is connected, it won't give back the prompt. (unless if you are not running it as a background job)
    just press ctrl+C to terminate the program.
    this will send the interrpt to wvdial program. and it will do all clean up and stop the connection.
step 2. Now you can pull out the USB cable.

---

### Post by mikewhatever on 2008-11-18
Can you describe the hanging in more details. Don't be vague, elaborate a bit.

---

### Post by trendyabinash on 2008-11-18
> **mikewhatever said:**
> Can you describe the hanging in more details. Don't be vague, elaborate a bit.
Sir I am new to ubuntu, so I can not be so specific.
EC325 is a CDMA modem used to connect to the NET.

In Linux there is no driver for the device so it is guided to be used as an internal modem, thats the reason it is being used via wvdial.

what else do I have to mention please ask me in detail.

---

### Post by mikewhatever on 2008-11-18
> **trendyabinash said:**
> Sir I am new to ubuntu, so I can not be so specific.
EC325 is a CDMA modem used to connect to the NET.

In Linux there is no driver for the device so it is guided to be used as an internal modem, thats the reason it is being used via wvdial.

what else do I have to mention please ask me in detail.

I simply asked to describe the hanging in more details.:confused: Anything wrong with that? Can you use the mouse? Can you open/close/move windows? Can you logout/reboot?

---

### Post by trendyabinash on 2008-11-18
Oh ho sorry Sir, Hang means completely hang, nothing works at all
Neways I got it correct. I installed ubuntu 8.04, it is working perfectly fine with this distro.

If someone wants then I can specify the steps that I have followed to make it right

---

### Post by mikewhatever on 2008-11-18
Glad to hear the problem is solved, and yes, you are more then welcome to detail the steps taken, so that the community can benefit from your experience.

---

### Post by trendyabinash on 2008-11-20
These are the steps that I followed in ubuntu 8.04 to get connected to the net on my HUAWEI EC325:-
Here&#8217;s how you can configure a BSNL CDMA data modem to work in Linux. The device I have is a*HUAWEI EC325*meant for the 144 Kb/s connection, but this guide should work fine for other BSNL devices as well (2 Mb/s device, for eg.)
Let&#8217;s start off by installing the software. We&#8217;ll be needing*wvdial*and*gnome-ppp. So let&#8217;s install that. On a Debian based system (Ubuntu, Mint, Elive etc.), do:
$ sudo aptitude update
$ sudo aptitude install wvdial gnome-ppp
Note: Since the net connection isn&#8217;t up and working just as yet (duh), make sure your installation CD/DVD is in the apt sources list before you issue the above commands. Use*apt-cdrom add*for that.
The next step is to setup wvdial. Follow these steps:
1. Make sure the device is plugged in.
2. Type the following command (as root)
# lsusb
3. You&#8217;ll see a bunch of lines of the form:
Bus XYZ Device XYZ: ID AAAA:BBBB [Name of Device]
4. Note down the*AAAA*and*BBBB*part of your BSNL device. In case no such device is listed, unplug all USB devices except your data card and run the command again. All entries except one will have AAAA and BBBB values of 0. Note this down.
5. Alright, now we have the vendor and product ID of the device. Type the following command:
#modprobe usbserial vendor=0xAAAA product=0xBBBB
(Here replace AAAA and BBBB with the ID you wrote down earlier)
6. Now we can configure wvdial. We&#8217;ll need to edit the*wvdial.conf*file. So do this:
$ sudo nano -w /etc/wvdial.conf
7. Edit it so that the*[Dialer Defaults]*section looks like this:
[Dialer Defaults]
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Stupid Mode = 1
Modem Type = USB Modem
ISDN = 0
Phone = #777
New PPPD = yes
Modem = /dev/ttyUSB0
Username =*Your BSNL username here
Password =*Your BSNL Password
Baud = 460800

There. Make sure you save the file*
8. Let&#8217;s test if everything&#8217;s working. Type:
$ sudo wvdial
9. If everything&#8217;s configured properly, you should see a series of lines in the terminal and the connection should be successful. You might want to fire up the browser and visit a site to check if it&#8217;s working&#8230;
10. Now let&#8217;s configure gnome-ppp. Start it up by running*Run -> &#8216;gnome-ppp&#8217;
11. Click Setup
12. In the Modem page, set Device to &#8220;/tty/USB0&#8221;, Type -> USB Modem, Speed -> 460800, Volume -> Off, Wait for Dialtone -> Checked.
13. Leave the Networking page as it is. The Options page should look something like this:

gppp Options
dock in notification area - ticked
autoreconnect - ticked
check carrier line -ticked
check default route - ticked
ignore terminal strings(stupid mode) - ticked
14. Close the Setup page, type your username and password in the respective boxes and click connect. If you did everything right, the connection should get established.
15. All done! Now you can create a shortcut to*&#8216;gnome-ppp&#8217;*and configure it to start at system startup (using Sessions manager in Gnome/KDE).
There you go&#8230; configuring a BSNL data card is a piece o&#8217; cake**In case you have any doubts/suggestions ask me.

---

### Post by romainclair on 2009-01-02
With reliance EC325 on Ubuntu 7.1 :
I have used Internet many hours, days; without problems. But now, I can not connect anymore.
PPP daemon has died = A modem hang up the phone (exit code = 16). Var/log/messages = warning: secret file /etc/ppp/papsecrets has world and/or group access. Please, can u help me to reconnect ?

---

