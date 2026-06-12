---
title: "US Robotic 56k Modem Problem"
date: 2007-01-07
forum: Installation &amp; Upgrades
---

### Post by kd5lwu on 2007-01-07
Am I posting in the wrong place on the forum? 45 readers of the post but not one answer! Please its been 3 days and no help. Could someone who is having the same problem please tell what you have done so far and perhaps that would help me. I need to get my Linux box up on the Internet and any little bit of help would be much appreciated! As I said the US Robotics external 56k modem works great in xp but in Ubuntu I can connect but it will not browse. I am sure this is a setting in Ubuntu but not sure where to go...DNS server on Ubuntu...or? Thanks for the responses - Johnny KD5LWU I did resolve the modem lock error....


First I love the Ubuntu OS!!! Next I get this message when I try to install the modem using Kppp...

Unable to create modem lock file,,,, Can someone give me a clue as to what this means and what to do? Thanks in advance Johnny KD5LWU Cortez, Colorado....... This is resolved but.....

**** New problem**** - I had set this modem up at home to test but did not dial in because at home I have cable modem. Brought the robotic to work this morning and it connect just fine but I cannot browse the internet. I think I have checked everything including the browser settings and the proxy setting but still cannot browse. The machine is a dual boot with XP pro so I setup the modem in XP and it works fine so it must be a config issue in Ubuntu. Please can someone give me some suggestions to resolve this? Thanks Johnny KD5LWU

---

### Post by kd5lwu on 2007-01-07
Any thoughts would help! Thanks

---

### Post by kd5lwu on 2007-01-07
I did the  following Command and discovered I was looking in he wrong place...

wvdialconf /etc/wvdial.conf


Scanning your serial ports for a modem.


ttyS0<*1>: ATQ0 V1 E1 -- OK

ttyS0<*1>: ATQ0 V1 E1 Z -- OK

ttyS0<*1>: ATQ0 V1 E1 S0=0 -- OK

ttyS0<*1>: ATQ0 V1 E1 S0=0 &C1 -- OK

ttyS0<*1>: ATQ0 V1 E1 S0=0 &C1 &D2 -- OK

ttyS0<*1>: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0 -- OK

ttyS0<*1>: Modem Identifier: ATI -- 5601

ttyS0<*1>: Speed 4800: AT -- OK

ttyS0<*1>: Speed 9600: AT -- OK

ttyS0<*1>: Speed 19200: AT -- OK

ttyS0<*1>: Speed 38400: AT -- OK

ttyS0<*1>: Speed 57600: AT -- OK

ttyS0<*1>: Speed 115200: AT -- OK

ttyS0<*1>: Max speed is 115200; that should be safe.

ttyS0<*1>: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0 -- OK

Modem Port Scan<*1>: S2 S3

Then I ran Kppp and set it for the correct port but I am not browsing yet. Johnny KD5LWU

---

### Post by Shortspan on 2007-01-16
I am using a US Robotics Modem (external, serial, 28800) as I write here.  But I haven't been able to get it working in Ubuntu 6.10 either.  I am presently using Kubuntu with the kppp dialer and all works well (no drivers needed.)  I had to set the dialler to port dev/ttyS0 since I am connected to the "first" serial port.  And, it is set to "hardware" rather software configuration (sorry if the wording isn't exact I am typing from memory. I can't access the info while I use the dialer.)  If you figure out how to get it going in Ubuntu it would be nice.  I can access the internet with kppp dialer through Kubuntu, Knoppix, and Freespire on the Live CD's.  I am using the Live CD now.  Ubuntu doesn't have a dialer on the Live DVD so and I can't figure out how to set it up with the software supplied.  There is a Gnome ppp dialer and Wvdialer (sp?) on the DVD but I can't access them.  I think I have to install Ubuntu first to be able to load the dialers.

---

### Post by kd5lwu on 2007-01-16
Sorry I have not got it going yet (taking a rest from frustration) you should be able on the live CD to log into a terminal window then type su then the root password (to set new root password type sudo passwd root and follow prompts) once in the root terminal type wvdialconf /etc/wvdial.conf  and this will look for your modem the write a new wvdial.conf file for you. hope that helps a little. What I am needing is the info to put in for the KPPP config window for the modem. have searched the internet but no joy yet. I think once I am able to input the correct commands in that window all will be well as I am now able to see the modem but when I connect (which it does) it just sits there in stall with no browsing happening. Johnny KD5LWU

---

### Post by Shortspan on 2007-01-16
Ok.  These are the Kppp settings I use:
Under **Accounts** tab *Connection*:"type your Isp's name, whatever you want."
In *Phone Number*: Click *Add*, then "type your phone number"
In *Authentication*: Chose "PAP/CHAP"
In *Callback*: Chose "Administrator defined"
Under **IP** tab: indicate "Dynamic"
Under **Gateway** tab: indicate "Default Gateway"
check "assign the default route to this gateway"
Under **DNS** tab: indicate "automatic"
Leave tabs **Login Script**, **Execute**, and **Accounting** as they are.
Back to the front of Kppp
Under **Modem** tab / then *Device* tab: 
*Modem Name*: "Whatever you call your modem... i.e. USROBOTICS"
*Modem Device*: "/dev/ttyS0" 
This is for serial port 0 or the first serial port. I think you would use /dev/ttyS1 for serial port 2 or the second port.)
*Flow Control*: "Hardware [CRTSCTS]"
*Line Termination*: "CR"
*Connection Speed*: "Whatever your modem can handle... 56000?"
("lock file" is checked")
Then back under *Modem* tab 
(check "wait for dial tone before dialing")

Those are my settings.  Hope it helps.  My Isp does all of the DNS settings on login automatically.  

Michael

---

### Post by _duncan_ on 2007-01-18
> Then I ran Kppp and set it for the correct port but I am not browsing yet.

sounds like a domain name server issue. check if the file /etc/resolv.conf contains the dns ip address from your isp. It should look like this:

```
nameserver xxx.xxx.xxx.xxx
nameserver xxx.xxx.xxx.xxx

```

where xxx.xxx.xxx.xxx = dns ip address from your isp.

---

### Post by kd5lwu on 2007-01-18
Thank you Thank you! it may be a dns issue i will check that out too but what i am needing is the stuff that goes in the modem commands window as it is completely empty and may be part of the problem. I do appreciate the help. Johnny KD5LWU

---

### Post by kd5lwu on 2007-01-18
Still working on this but have the command script it is...

30
ATZ
BLANK
30
70
OK
ATX3
ATDT
CONNECT
BUSY
NO CARRIER
NO DIALTONE
+++ATH
PK
ATA
RING
CONNECT
DIGITAL LINE DETECTED
+++
OK
50
M0L0 M1L1 M1L3

STILL NO JOY SO WILL NEXT WORK ON THE DNS I DID PUT IT IN KPPP. It now dials, logs in but stalls on browse so still more work here tomorrow

johnny kD5lwu

---

### Post by FXWGBill on 2007-01-18
I always had a little trouble with my US Robotics and what I found to work the best was using a terminal and running   pppconfig    follow through that and set everything up and then, I believe all ya have to do is type sudo ppp in a terminal window and it will connect up, you might not have to use the 'sudo' but that always worked great for me...

P.S.

Oh... Inciddentally Johnny, you are just over there to the west of me... I am WE5Q and presently in Fort Dodge, Kansas... A bit off topic, but I'll try and reach ya through the website etc as I am setting up a small station here at the Kansas Soldiers Home in the dorm...

---

### Post by FXWGBill on 2007-01-18
delete

---

### Post by kd5lwu on 2007-01-19
Thanks Bill if you use echolink my repeater is node 24336.

Now I have tried to write a new  /etc/resolv.conf as the original is pointing to the 127.x.x.x and needs to be 66.118.220.37 and 66.118.220.37 of course I became su to do this but vim will not let me write and gedit does not work in root so I am at loss how to change the text in this file and it obviously is my problem! What editor can I easily use in root. Mind you nothing complicated for this newbie!!! LOL I will try the pppconf while I am waiting for responses. thanks Johnny KD5LWU

---

### Post by FXWGBill on 2007-01-19
Open a terminal and type:  sudo gedit /etc/resolv.conf

that will do the trick

---

### Post by redden on 2007-01-20
[QUOTE=I had to set the dialler to port dev/ttyS0 since I am connected to the "first" serial port.  [/QUOTE]

Have you checked that you have a /dev/ttyS0? I just installed 6.10 because I was hav a problem with 6.6 and I do not have any /dev/ttyS# devices.

---

### Post by kd5lwu on 2007-01-22
Hi Bill - My reply to you on Friday did not get posted for some reason. If you use Echolink my repeater is node 24336 give me a call sometime. I cannot find a text editor in root to allow me to rewrite resolve.conf which does not have the dns numbers in it. I tried VIM but it will not allow me to write for some reason. I also tried GEdit but it will not run in root.

What Text editor can I use in root (a simple one I hope) to allow me to change the resolv.conf to the right settings?

---

### Post by kd5lwu on 2007-01-22
> **redden said:**
> Have you checked that you have a /dev/ttyS0? I just installed 6.10 because I was hav a problem with 6.6 and I do not have any /dev/ttyS# devices.

Thanks Redden - I have /dev/ttys0 and it works I can connect just not browse but think it a dns issue and as soon as I can get a root editor that I understand to work I will set dns and let you know. Johnny KD5LWU

---

### Post by kd5lwu on 2007-01-22
> **FXWGBill said:**
> Open a terminal and type:  sudo gedit /etc/resolv.conf

that will do the trick

Thanks Bill but when I open gedit in root I get errors from it so another one to figure out but not as important. I really need to get this box setup so I can use it for dial-in and proxy server and get rid of xp pro. 73 Johnny KD5LWU

---

### Post by unisol on 2007-01-22
if youre using a us robitics modem and its an internal pci try system/adminstration/networking and set your modem to ttyS14. thats the one that worked for me when i had a the same modem. did you try running sudo /etc/wvdial/wvdial.conf? give it a try

---

### Post by kd5lwu on 2007-01-22
> **unisol said:**
> if youre using a us robitics modem and its an internal pci try system/adminstration/networking and set your modem to ttyS14. thats the one that worked for me when i had a the same modem. did you try running sudo /etc/wvdial/wvdial.conf? give it a try

Thanks - well here is the update status....I managed to get gedit working changed the DNS setting but still no joy! Here is the situation...Ububtu sees the modem it can dial out and log in all looks good until I go to browse then it cannot find [www.google.com](www.google.com) or any other webpage. I have set the DNS stuff in /etc/resolv.conf.  it looks like kppp is shutting down the DNS address here is the file after attempting to connect...

domain ANIMAS.NET 		#kppp temp entry
# nameserver 66.118,220,37 	#entry disabled by kppp
# nameserver 66.118,220,38 	#entry disabled by kppp
nameserver 66.118.220.37 	#kppp temp entry
nameserver 66.118.220.38 	#kppp temp entry


I have one more thing to try then I am at loss from there

Johnny kd5lwu

---

### Post by kd5lwu on 2007-01-22
Still no joy BUT...I have found the problem it's (whatever it's is) is logging the DNS server as 209.244.0.3 and 209.244.0.4 (it should be 66.118.220.37/38)  I have changed everything I can think of but am missing something somewhere...anyone have an ideal where this DNS address is coming from? and how to correct it I rewrote the wvdial.conf and the KPPP setup DNS and still not joy. Johnny KD5LWU who is determined to get this!

---

### Post by odin1965 on 2007-01-31
Have you set PPP0 (the modem) as the default route to the internet? I haven't done it in KDE, but in Gnome (ubuntu) it is under   System => Administration => Networking. Then select the modem connection and set it as the default gateway. Make sure your phone line is plugged into the modem when you do this. It would not let me use the modem as default until it had a dialtone. Anybody else know how to set this in KDE?

---

