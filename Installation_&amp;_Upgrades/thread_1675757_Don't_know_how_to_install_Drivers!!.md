---
title: "Don't know how to install Drivers!!"
date: 2011-01-26
forum: Installation &amp; Upgrades
---

### Post by padfootpak on 2011-01-26
[SIZE=2][FONT=Lucida Sans Unicode]I installed ubuntu two or three hours ago, after using the LiveCd. in the live cd the OS at first did not detect my wirless chip but after 30 seconds it gave me a prompt to enable the Broadcom STA driver. so i enabled it. the OS then downloaded it (even though there was no internet access, I am assuming it copied it from the CD) and then the WiFi worked like a charm. 
But after installing Maverick Meerkat it did not do the same thing and did not prompt me to enable the driver. I looked in Hardware devices in the administration menu but there were no drivers available. Why ? 

to remedy that i downloaded the Linux drivers for the Wireless from the Broadcom site. it gave me a "tar.gz" file.( [/FONT][/SIZE][http://www.broadcom.com/support/802.11/linux_sta.php](http://www.broadcom.com/support/802.11/linux_sta.php)[SIZE=2][FONT=Lucida Sans Unicode] ) But i do not know how to install it and i could not find any tutorial on the internet.  Can you tell me how to.
[/FONT][/SIZE]

---

### Post by ajgreeny on 2011-01-26
It is much easier if you simply attach the machine by cable and carry out the updates available, then enable the STA driver whist cable connected, and from then on you should be good to go with your wireless.

---

### Post by realzippy on 2011-01-26
+1


otherwise you have to compile the driver as described in the [README]("http://www.broadcom.com/docs/linux_sta/README.txt").

---

### Post by padfootpak on 2011-01-26
I am so so so sorry that i did not read the readme file. i tend to do that a lot. SORRY!!

---

### Post by realzippy on 2011-01-26
No prob,but suggest to do what *ajgreeny* suggested...


[I]Ubuntu:
------
Go to System->Administration->Hardware Drivers
Choose the Broadcom STA wireless driver
Activate

Sometimes the driver does not show up in the Hardware Drivers choices.  In
this case, try reintalling the driver from the GUI or shell like this:

From the GUI:
Package Manager (System>Administration>Synaptic Package Manager). Click the 
Reload button in the upper left corner of Synaptic to refresh your index then 
search for and reinstall the package named bcmwl-kernel-source.

From the shell:
sudo apt-get update
sudo apt-get --reinstall install bcmwl-kernel-source

In either GUI or text case, after reinstalling, reboot your machine.

Now go back to System->Administration->Hardware Drivers
and you should see the driver enabled and working.[/I]

---

### Post by padfootpak on 2011-01-26
Thank you guys. I guess I'm not so "on the game" since I didn't get my cup of joe today.

---

