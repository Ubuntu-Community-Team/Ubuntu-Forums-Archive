---
title: "ADSL connection problems   9.10Beta"
date: 2009-10-04
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by ubiubi on 2009-10-04
Hi all

I have a triple boot system with Karma installed in a unique partition. I am currently connected on the net with my jaunty partition.

 I tried to configure my modem in the network configurations  configuration panel by pressing the DSL tab and adding a new connection . After entering my parameters I received the following message.


[COLOR="Red"]Error editing connection: property '%s' / '%s' invalid: %d
NMSettingPPPOE[/COLOR]


[COLOR="Black"][/COLOR]
I then ran pppoeconf in the terminal and managed to make a connection This worked!

[COLOR="Red"]
mark@mark-desktop:~$ sudo pppoeconf 
[sudo] password for mark: 
Plugin rp-pppoe.so loaded. 
RP-PPPoE plugin version 3.8p compiled against pppd 2.4.5 
mark@mark-desktop:~$ [/COLOR

[/COLOR]
After restarting the computer I discovered there was again no connection. I tried pppoeconf in the terminal and received the following.


[COLOR="Red"]
Sorry, I scanned 1 interface, but the Access             &#9474; 
          &#9474; Concentrator of your provider did not respond. Please    &#9474; 
          &#9474; check your network and modem cables. Another reason      &#9474; 
          &#9474; for the scan failure may also be another running pppoe   &#9474; 
          &#9474; process which controls the modem.                        &#9474; 
          &#9474;                                      
[/COLOR]
[COLOR="Black"][/COLOR]

Any ideas anyone.  crash message  (only relating to the failed launch of the connection) is launched inviting me to send a bug report, but this is clearly inpossible for me to report. I tried to report it under Jaunty by entering a code in terminal emulator bu I don't think anything happened, so I'm starting this thread!

Thanks in advance for any help!

---

### Post by Joe_Bishop on 2009-10-04
It's general 2.6.31 ppp regression. Try to download and install 2.6.30 from [http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.30.8/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.30.8/) and test with it.

---

### Post by nilarimogard on 2009-10-04
I have the exact same problem. Until I find a real way to fix it, I added a script in my startup applications:


```

#!/bin/bash
poff -a ppp0 && poff -a ppp1 && sleep 5 && pon dsl-provider
```...which temporarily fixes it.

---

### Post by ubiubi on 2009-10-04
> **Joe_Bishop said:**
> It's general 2.6.31 ppp regression. Try to download and install 2.6.30 from [http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.30.8/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.30.8/) and test with it.


Hello and thanks for responding, Joe. I'm not greatly experienced so maybe I did something silly. I downloaded on jaunty four files; the two *X38.deb files and the two general.deb files.  Non of them would install in 9.10 Beta with the typical error message of "..unable to read file header flags.."


Should I have removed some files first?

Thanks again for your help.

---

### Post by ubiubi on 2009-10-04
> **nilarimogard said:**
> I have the exact same problem. Until I find a real way to fix it, I added a script in my startup applications:


```

#!/bin/bash
poff -a ppp0 && poff -a ppp1 && sleep 5 && pon dsl-provider
```...which temporarily fixes it.


Hello nilarimogard.

Thanks for the tip. I cut and pasted it into the command line and I now have internet access. 

I suppose I should mark this thread solved, albeit temporarily! Thanks again to you and Joe:popcorn:

---

### Post by ikisham on 2009-10-04
Create a file with that script then right-click it and under the 'Permissions' tab check 'Allow executing file as a program'.
Then go to System > Preferences > Startup Applications, open it and choose to add an application and add the file.

---

### Post by nilarimogard on 2009-10-04
That's not an actual fix, just a temporary workaround...

---

### Post by TheMixtureMedia on 2009-10-06
How do I get this to work for wifi

---

