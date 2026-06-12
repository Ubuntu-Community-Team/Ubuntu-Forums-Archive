---
title: "Installing cisco packet tracer"
date: 2012-12-08
forum: Installation &amp; Upgrades
---

### Post by natarajan ramakrishnan on 2012-12-08
hi. can anyone tell me how to over come this problem which i face while installing cisco packet tracer?
i gave the below command to install the software which is a bin file.

 [COLOR="Red"]sh PacketTracer533_i386_no_tutorials_installer-rpm.bin[/COLOR]

but i get the following error when i accpet the EULA,

[COLOR="red"]You have accepted the terms to the EULA. Cisco Packet Tracer will now be installed.
Attempting to install package now
rpm: please use alien to install rpm packages on Debian, if you are really sure use --force-debian switch. See README.Debian for more details.[/COLOR]

i tried using alien , but i get error in that also.

[COLOR="red"]alien -i PacketTracer533_i386_no_tutorials_installer-rpm.bin 
Unknown type of package, PacketTracer533_i386_no_tutorials_installer-rpm.bin.[/COLOR]

please tell me how to overcome this. i tried using [COLOR="red"]--force-depends[/COLOR] also. but, it is not helping too.

---

### Post by The Cog on 2012-12-08
I think the rpm.bin file is a kind of self-extracting executable that extracts the rpm file from itself and then tries to install that. It's possible that it leaves the true rpm file in a temporary folder somewhere, but I guess it might just extract straight into a pipe, which would then be more difficult.

I think you need to have a look at the .bin file with a text editor and see what it does - the first part of it will be shell script that does the extracting of the rpm contents (which will be tacked on the end of the script).

---

