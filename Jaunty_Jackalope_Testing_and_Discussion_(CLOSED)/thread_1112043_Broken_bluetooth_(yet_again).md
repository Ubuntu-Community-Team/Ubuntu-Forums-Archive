---
title: "Broken bluetooth (yet again)"
date: 2009-03-31
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by David A Knight on 2009-03-31
A couple of weeks ago bluetooth broke for me (yet again).  My keyboard (apple) will pair and work just fine, but doesn't survive a reboot, it is listed as being paired but it fails to reconnect.  I can remove the pairing and reconnect just fine.  Any one else suffering anything similar?  

Rant mode on: this seems to happen constantly through various dev cycles as the bluetooth stuff seems to be always be changed for no obvious benefit, and every time it does it seems to break for me.  The previous round of changes broke things, but then got fixed, that ui featured a checkbox to auto reconnect devices, this has gone with the newer ui that allows setting specific pin codes etc.

---

### Post by imthemp3king on 2009-04-03
I am having the same kind of issue with a Microsoft Bluetooth keyboard.  Only with mine, it will stop working during a period of inactivity and it takes 2 removals and 2 attempts at pairing it to get it to work again.  I do this multiple times a day.  Each time it stops functioning, it shows as still paired.  My mouse however, never has a problem and survives reboots.  I understand that it's beta and I know things will break, but I'm with you in not really understanding why bluetooth seems to break with each new distro.

---

### Post by bcrook88 on 2009-04-03
I can second the Bluetooth Apple Keyboard issue (not Aluminum).
It worked perfectly in Intrepid after editing the /etc/default/bluetooth file and adding the following:

HIDD_ENABLED=1
HIDD_OPTIONS=”–connect KB_ADDRESS –master –server”

Doing this is Jaunty stops me from connecting to the keyboard at all.

I'm using a Dell Bluetooth TruMobile 350 internal bluetooth card.

---

### Post by Dilligaf on 2009-04-04
My Microsoft bluetooth mouse has the same issue, this seems to happen regulary during new releases, I keep a wired mouse handy and end up using that most of the time.

Mike

---

### Post by phenest on 2009-04-04
> **bcrook88 said:**
> I'm using a Dell Bluetooth TruMobile 350 internal bluetooth card.

I have the same bluetooth module and my Kensington bluetooth mouse work fine. As does my bluetooth Interlink remote. As does my mobile phone.

Did you upgrade to Jaunty? Have you tried a fresh install? Do you get problems with the Live CD?

---

### Post by bcrook88 on 2009-04-06
> **phenest said:**
> I have the same bluetooth module and my Kensington bluetooth mouse work fine. As does my bluetooth Interlink remote. As does my mobile phone.

Did you upgrade to Jaunty? Have you tried a fresh install? Do you get problems with the Live CD?

I can connect fine, its just on restart. It will not connect and I have to re-bond. This is on a clean install.

I just tested it with my Logitech Bluetooth Travel Mouse (sorry I forget the model) and it work perfectly on power down/restart. The only difference I can see is the mouse does not use a passcode and there is no key icon beside it in the bluetooth devices list. The apple keyboard does.

---

### Post by imthemp3king on 2009-04-10
> **phenest said:**
> I have the same bluetooth module and my Kensington bluetooth mouse work fine. As does my bluetooth Interlink remote. As does my mobile phone.

Did you upgrade to Jaunty? Have you tried a fresh install? Do you get problems with the Live CD?

Mine is a fresh install of 9.04 on an IBM T60p.  I am using the Microsoft Keyboard Elite for Bluetooth model 1002.  I haven't experienced any issues with my mouse thus far

---

### Post by bcrook88 on 2009-04-10
> **imthemp3king said:**
> Mine is a fresh install of 9.04 on an IBM T60p.  I am using the Microsoft Keyboard Elite for Bluetooth model 1002.  I haven't experienced any issues with my mouse thus far

My understanding is that the Apple Keyboard is very picky about encryption so I suspect that is the issue.

---

