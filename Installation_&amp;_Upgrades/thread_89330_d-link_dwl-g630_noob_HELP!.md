---
title: "d-link dwl-g630 noob HELP!"
date: 2005-11-12
forum: Installation &amp; Upgrades
---

### Post by kemmer on 2005-11-12
system:HP Pavilion N5420 laptop
OS:Ubuntu and XP dual boot

Ok I am a complete linux noob. I know nothing. I am a recorvering windows user. 
I have a D-Link DWL-G630 (ar5211). I need to set it up in Ubuntu. It was not recognized at installation. I have read there are one or two things I can do. I think I can do the madwifi or use ndiswrapper. The thing is I dont know what is best. When I look at step by steps I find I cant even do them because I dont know linux well enough. If some one could help me (lay it out like you were telling your grandma) or point me to a place that does that would rock! :p

---

### Post by flobbleobble on 2005-11-12
1. Copy your wireless card drivers to your home folder.

2. Open Applications --> Accessories --> Terminal

3. Type **su** and then your root password

3. Go to your copied driver location: [B]cd /home/*username*/
[/B]
4. Type **ndiswrapper -i *driverfile.inf***

5. Type **ndiswrapper -l** to check that the drivers are present and loaded

6. Type modprobe ndiswrapper

7. Type ndiswrapper -m to load the module at startup

When you go to your system --> administration --> networking menu you should see your wireless card ready to configure.

Hope this helps.

---

### Post by SickTwist on 2005-11-12
[QUOTE=kemmer]system:HP Pavilion N5420 laptop
OS:Ubuntu and XP dual boot

Ok I am a complete linux noob. I know nothing. I am a recorvering windows user. 
I have a D-Link DWL-G630 (ar5211). I need to set it up in Ubuntu. It was not recognized at installation. I have read there are one or two things I can do. I think I can do the madwifi or use ndiswrapper. The thing is I dont know what is best. When I look at step by steps I find I cant even do them because I dont know linux well enough. If some one could help me (lay it out like you were telling your grandma) or point me to a place that does that would rock! :p[/QUOTE]

The madwifi driver is included with ubuntu but is only useful if your DWL-G630 uses the atheros chipset (sometimes manufacturers will switch chipsets without changing the model number).

Open a terminal (Applications --> Accessories --> Terminal) and type this command:

lspci -v

That will list all the pci devices in your computer. The -v flag tells it to be verbose (print more detail). Copy the output and paste it here so that we can make sure your DWL-G630 is using atheros.

---

### Post by kemmer on 2005-11-12
Atheros communications, inc,: 001a(rev 01)
is that good?

---

### Post by SickTwist on 2005-11-12
[QUOTE=kemmer]Atheros communications, inc,: 001a(rev 01)
is that good?[/QUOTE]

OK, sounds like it does have the atheros chipset. To install the driver, open a terminal (Applications --> Accessories --> Terminal) and run this command (just copy and paste it):

sudo apt-get install linux-restricted-modules-`uname -r`

That will install a package that includes the madwifi driver. Reboot the computer and then log-in and start the network manager (System --> Administration --> Networking ). Check to see if the DWL-G630 is on the list of connections.

---

### Post by kemmer on 2005-11-13
It said that nothing happend because it was alredy the newest one?:( I also tried to do ndiswrapper but I got "su: Authenticstion Failure". I am 0 for 2

---

### Post by kemmer on 2005-11-13
In true noob fasion I was alredy good to go. 
I just had to configure it. 
Thanks for the help!:D

---

### Post by SickTwist on 2005-11-13
You're welcome. I'm glad that it worked out for you. To me, it is better to use native Linux drivers when they are available instead of using ndiswrapper.

---

