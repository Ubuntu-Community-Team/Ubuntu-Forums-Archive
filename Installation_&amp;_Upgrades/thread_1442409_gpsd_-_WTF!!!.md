---
title: "gpsd - WTF?!?!?!"
date: 2010-03-29
forum: Installation &amp; Upgrades
---

### Post by LePresident on 2010-03-29
Hey there, well, my problem is the following:

Some days ago I was trying to install a gps program named "tango gps" and during the installation my bro accidentally unplugged my pc from the energy input and obviously it got turned off. Right after that, when I turned on the computer again, everything seemed to be working fine but when I tried to restart the tango gps installation I got the following message: "there were found errors while processing **gpsd**". 

Therefore, I said "ok, well, just un-install (what was installed until that point) that **** and go on with your life" and then it happened again: "there was a ******* error while trying to un-install the gpsd" or something like that.  However, the tango gps' icon at the applications menu disappeared and that was enough for me... until now!

At this very moment I was trying to upgrade my open office suite and guess what? I got the very same ******* message: "there were found errors while processing gpsd".

SOMEONE HELP ME, FOR GOD'S SAKE!!! WHAT CAN I DO TO AVOID HAVING PROBLEMS WITH THAT ************ STUPID GPSD THING?!!!!

---

### Post by uRock on 2010-03-30
Open a terminal via Applications> Accessories> Terminal and enter the following code. If it returns an error, please copy and paste it here, so we can figure out what is going wrong and how to fix it. ```
sudo apt-get update
``` ```
sudo apt-get upgrade
``` ```
sudo apt-get remove gspd
```

---

### Post by LePresident on 2010-03-30
Ook ok, this is what I get when I do the update:

```

W: Error de GPG: http://ppa.launchpad.net karmic Release Las firmas siguientes no se pudieron verificar porque su llave pública no está disponible: NO_PUBKEY 7FB8BEE0A1F196A8
W: Error de GPG: http://ppa.launchpad.net karmic Release Las firmas siguientes no se pudieron verificar porque su llave pública no está disponible: NO_PUBKEY 5A9A06AEF9CB8DB0

```Because it is in spanish, I'll translate it:

```
W: GPG error: http://ppa.launchpad.net karmic Release the following signs can not be verified because your public key is not available: NO_PUBKEY 7FB8BEE0A1F196A8
W: GPG error: http://ppa.launchpad.net karmic Release the following signs can not be verified because your public key is not available: NO_PUBKEY 5A9A06AEF9CB8DB0

```well... something like that...

Also, when I do the upgrade I get:

```
The following errors where found while processing:
 gpsd
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

And when I do the final step, nothing happens but a "couldn't find gspd" message.  Did you mean "gpsd" instead?

---

