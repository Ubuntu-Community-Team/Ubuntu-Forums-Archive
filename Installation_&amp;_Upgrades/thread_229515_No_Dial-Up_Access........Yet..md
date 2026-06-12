---
title: "No Dial-Up Access........Yet."
date: 2006-08-04
forum: Installation &amp; Upgrades
---

### Post by danrael on 2006-08-04
[I][COLOR="Blue"]

OK. Here is where I am at:

After succesfully configuring my ISP with: sudo pppconfig, as was suggested, I open a terminal window, and type:

      pon copper

('copper' being the name of my ISP, which I used instead of
'provider', which was suggested by the pppconfig utility.)

I press 'Enter', but nothing happens, except for another prompt, consisting of: user@ubuntu:~$

_________________________________

These are the files in my etc/ppp/peers folder:

copper
copper.bak
ppp0
provider.bak
wvdial
wvdial-pipe

Where do I go from here?[/COLOR][/I]

---

### Post by zxee on 2006-08-04
Dial up in dapper has problems IMO as I said before.
Try sudo in front of the pon command-also there is an advanced section to the pppconfig utility where you can add your user to those who can dial out.
If none of that works you can also try > wvdial copper with and/or without the sudo. You shouldn't need to use sudo for those commands but...like I said..problems.

---

### Post by danrael on 2006-08-05
> **zxee said:**
> Dial up in dapper has problems IMO as I said before.
Try sudo in front of the pon command-also there is an advanced section to the pppconfig utility where you can add your user to those who can dial out.
If none of that works you can also try  with and/or without the sudo. You shouldn't need to use sudo for those commands but...like I said..problems.

The first thing I did was to delete all existing configs and to create a new one using the name "provider" as suggested by the utility.  Whether I enter the **pon** command or the **sudo pon** command, or **pon provider**, I only get another prompt.

Entering the commands **wvdial**  or **sudo wvdial** returns the following:

WvDial:  Internet dialer version 1.55
Cannot open dev/modem:  no such file or directory

If I enter the commands:   **wvdial provider** or **sudo wvdial provider** I receive the following:

WvDial:  Internet dialer version 1.55
Warning:  section (Dialer provider) does not exist in wvdial.conf
Cannot open dev/modem:  no such file or directory
__________________________________

Here are the the current files in my *etc/ppp/peers* folder:

ppp0
provider
wvdial
wvdial-pipe

---

### Post by danrael on 2006-08-05
Referring to the link you provided:  DialupModemHowto, I came across two pointers, both of which allowed me to make a bit more progress on two fronts:  

(To backtrack a moment:  I have a US Robotics 5610 PCI internal hardware modem which works with all the other Linux distros I have tried, including Ubuntu Breezy Badger.)

**Procedure #1**  

Under the section titled:  **wvdialconf & wvdial**
I entered the suggested command in a terminal:

 **sudo wvdialconf /etc/wvdial.conf**

A long string of parameters was returned, with the final message:

Found a modem on /dev/ttyS4.
Modem configuration written to /etc/wvdial.conf

The ModemHowTo then suggested I enter the command:

**sudo nano /etc/wvdial.conf**

which returned the following:

[Dialer Defaults]
Init1 = ATZ
Init2 = ATQO V1 E1 SO=O &C1 &D2 +FCLASS=O
Modem Type = Analog Modem
; Phone = <Target Phone Number>
ISDN = O
; Password = <Your Password>
New PPPD = yes
; Username = <Your Login Name>
Modem = /dev/ttyS4
Baud = 115,200

The ModemHowTo instructs one to enter phone number, password, and username, but here is where I am stuck:  I cannot seem to edit these fields.  
_______________________________________

**Procedure #2**

Looking further into the ModemHowTo it describes how to install and configure kppp, which is what I wanted to do in the first place.  The ModemHowTo says kppp is useable with both Kubuntu and Ubuntu.  It instructs one to enter the following command:

**sudo apt-get install kppp**

which returns the message:  E:  Could'nt find package kppp

I tried finding it on the Ubuntu CD with apt-get.  No dice.  So I downloaded it on my Mac and x-fered it over to the Ubuntu box on a CD-R, extracted the files into the folder kppp 1.6.25 on the desktop, then re-entered the command as given above, but still no dice.  Does the kppp folder have to be in a particular place so apt-get can find it?  If so, what is the correct procedure to get the kppp folder into the right place, and where exactly would that be?

---

### Post by Cariboo1938 on 2006-08-05
> **danrael said:**
> The ModemHowTo then suggested I enter the command:

**sudo nano /etc/wvdial.conf**

which returned the following:

[Dialer Defaults]
Init1 = ATZ
Init2 = ATQO V1 E1 SO=O &C1 &D2 +FCLASS=O
Modem Type = Analog Modem
; Phone = <Target Phone Number>
ISDN = O
; Password = <Your Password>
New PPPD = yes
; Username = <Your Login Name>
Modem = /dev/ttyS4
Baud = 115,200

The ModemHowTo instructs one to enter phone number, password, and username, but here is where I am stuck:  I cannot seem to edit these fields.
No, you can't edit this file. It gives you the very important information that your modem is /dev/ttyS4 (the same as mine). You have to follow the instructions in the ModemHowTo where it starts with "pppconfig & pon/poff". Under sudo pppconfig you you are asked, among other, for the port your modem is on and this is ttyS4. It took me long time to get this...and now it works:idea: 
Juergen

---

### Post by danrael on 2006-08-06
OK.  I opened up **pppconfig** again in a terminal window, and simply changed the port to /dev/tyS4.  Closed that program.  Then I entered the command:  **sudo nano /etc/wvdial.conf**

which again returned the following:

[Dialer Defaults]
Init1 = ATZ
Init2 = ATQO V1 E1 SO=O &C1 &D2 +FCLASS=O
Modem Type = Analog Modem
; Phone = <Target Phone Number>
ISDN = O
; Password = <Your Password>
New PPPD = yes
; Username = <Your Login Name>
Modem = /dev/ttyS4
Baud = 115,200

According to the instructions in the ModemHowTo, the next step reads as follows:  
[B][I][COLOR="Blue"]
"After opening the wvdial.conf file, input your ISP information where needed (look inside the file for fields) and add other options that might be needed for your software modem."[/COLOR][/I][/B]

.......which suggests that the fields CAN be edited, contrary to what you are saying?  (confusion here).

The very next instruction is this:

***[COLOR="Blue"]"Once you are ready, save the file (Ctrl-o) and exit (Ctrl-x), and try to dial:[/COLOR]***  **sudo wvdial**"

This returns the following:

--> WvDial:  Internet Dialer version 1.55
--> Initializing modem
--> Sending:  ATZ
ATZ
OK
--> Sending ATQO V1 E1 SO+O &C1 &D2 +FCLASS=O
ATQO V1 E1 SO=O &D2 +FCLASS=O
OK
-->  Modem initialized
-->  Configuration does not specify a valid phone number.
-->  Configuration does not specify a valid login name.
-->  Configuration does not specify a valid password.

So it appears that the modem is OK but that I must edit the wvdial.conf file with the required information.  How can I do this?

---

### Post by zxee on 2006-08-06
> OK. I opened up pppconfig again in a terminal window, and simply changed the port to /dev/tyS4. Closed that program. Then I entered the command: sudo nano /etc/wvdial.conf

which again returned the following:

[Dialer Defaults]
Init1 = ATZ
Init2 = ATQO V1 E1 SO=O &C1 &D2 +FCLASS=O
Modem Type = Analog Modem
; Phone = <Target Phone Number>
ISDN = O
; Password = <Your Password>
New PPPD = yes
; Username = <Your Login Name>
Modem = /dev/ttyS4
Baud = 115,200

According to the instructions in the ModemHowTo, the next step reads as follows:

"After opening the wvdial.conf file, input your ISP information where needed (look inside the file for fields) and add other options that might be needed for your software modem."

.......which suggests that the fields CAN be edited, contrary to what you are saying? (confusion here).
 

Yes you will need to edit wvdial.conf and nano is probably the best editor for someone new to linux to use although you could use gedit also. Just use an editor you feel comfortable with. 
I recommend that you make a copy of wvdial.conf before you edit it so that you can go back to the orginal in case of any problems.
Open a terminal. You will need to replace the phone, password, and username values with the actual values. 
After making a copy of wvdial e.g > sudo cp /etc/wvdial.conf /home/(yourusername) simply type, still in terminal, > gedit /etc/wvdial.conf Enter the values I've indicated-save the file and then try wvdial again. You should not need to enter anything but the command wvdial as you're editing the default entry. To close a connection you just use the keys Ctrl+c. Hope that helps.

---

