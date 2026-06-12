---
title: "Dell inspiron 510m, wlan not working."
date: 2005-06-29
forum: Installation &amp; Upgrades
---

### Post by vha on 2005-06-29
Just installed latest version on a dell laptop (for a friend of mine), and it went quite fine,atleast as far as i can see for now, except wlan.

been trying different settings , but i it wouldn't work at all. Ordinary i use i Ibook, and the network works fine with that machine. the wlan router is a Linksys, but normally their quite nice.

Someone who got some ideas ?

thanks

vha

---

### Post by emperor on 2005-06-29
Which "Dell" wireless card is in your 510m?
<use "sudo lspci -v" in a terminal if neccessary!>

Some of the 510m's have the Intel 2200 wireless card, if so you just need to install the firmware. Their should be more info on the forum concerning this. 

[http://ipw2200.sourceforge.net/#news]("http://ipw2200.sourceforge.net/#news")

You will need to get familiar with the wireless tools; see "iwconifg"

If you are using WEP, some settings will either need to be set manually vi iwconfig or you can edit the releated network config file. 

I can help you further this evening when I am sitting in front of my Dell i9300.

---

### Post by vha on 2005-06-29
[QUOTE=emperor]Which "Dell" wireless card is in your 510m?
<use "sudo lspci -v" in a terminal if neccessary!>

Some of the 510m's have the Intel 2200 wireless card, if so you just need to install the firmware. Their should be more info on the forum concerning this. 

[http://ipw2200.sourceforge.net/#news]("http://ipw2200.sourceforge.net/#news")

You will need to get familiar with the wireless tools; see "iwconifg"

If you are using WEP, some settings will either need to be set manually vi iwconfig or you can edit the releated network config file. 

I can help you further this evening when I am sitting in front of my Dell i9300.[/QUOTE]
 Did the comand and the card is a 2100 3B mini pci adapter .. 

So now its just to look around for some info about that .

thanks.

Looking forward till its working.

vha

---

### Post by emperor on 2005-06-30
Check using:  "lsmod" to see what driver Ubuntu is loading.
 
My bet is it the "ipw2100" which would be the Intel Pro 2100. 

[http://ipw2100.sourceforge.net/#news]("http://ipw2100.sourceforge.net/#news")

Ubuntu Hoary's kernel has both the ipw2200 and ipw2100 drivers. But you must install the firmware. You will want to download and install the latest ([v0.55-current firmware]("http://ipw2100.sourceforge.net/firmware.php?fid=4")) firmware from here:

 [http://ipw2100.sourceforge.net/firmware.php]("http://ipw2100.sourceforge.net/firmware.php")

extract the file to the "/lib/hotplug/firmware" directory using:

sudo tar -xzvf ipw2100-fw-1.3.tgzu 

Then you can will configure some of your wireless setting using the "System-Administration-Networking" . Some settings like "restricted[1]" for wep will require manual edits to the "Networking" config file in "/etc/network/interfaces"

#-----------------------------------------------------------------------------------------------------------------------
You should use the wireless tools, specifically "iwconfig" first for testing and then edit the "interfaces file. For example my "interfaces" file looks like this:

# The loopback network interface
iface lo inet loopback
 
auto lo

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
#mapping hotplug
#    script grep
#    map eth0


# The primary network interface
iface eth1 inet static
address 192.168.10.103
netmask 255.255.255.0
gateway 192.168.10.1
wireless-essid FlyingPenguin
wireless-key C1e9cEb75d restricted[1]
wireless-channel 4
wireless-mode managed
wireless-ap 00:0C:E5:4F:E8:BE
auto eth1 

iface eth0 inet static
address 192.168.10.7
netmask 255.255.255.0
gateway 192.168.10.1

#--------------------------------------------------------------------------------------------------------------------------

---

### Post by anno on 2005-06-30
Hello my friend!
I found a similar case, maybe his solution can help you?
Check out : [http://ubuntuforums.org/showthread.php?t=2586](http://ubuntuforums.org/showthread.php?t=2586)

anno.

---

### Post by vha on 2005-06-30
--
tania@ombsas:~/Desktop/2100$ iwconfig
lo        no wireless extensions.

sit0      no wireless extensions.

eth0      unassociated  ESSID:"ombsas"  Nickname:"ipw2100"
          Mode:Managed  Channel=0  Access Point: 00:00:00:00:00:00
          Bit Rate=0 kb/s   Tx-Power:off
          Retry:on   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

eth1      no wireless extensions.
--

My brain hurts and i have absolutely no idea what it says nor what to do.
It should be logic, but it is. Think i´ll have to get this working and then just stick to my Ibook.

Think it´s time for siesta.

vha. :(

---

### Post by mingus on 2005-06-30
But did you install the firmware?  My card uses a diff chipset, but the installation is essentially the same - and just like on W$, although a bit more easily packaged.

---

### Post by vha on 2005-06-30
[QUOTE=mingus]But did you install the firmware?  My card uses a diff chipset, but the installation is essentially the same - and just like on W$, although a bit more easily packaged.[/QUOTE]
 Then it starts moving ..   added the line acpi_irq_isa=7 in menu.lst and rebooted.
Still a error message, tried to ping via cable from the router, an that works now, can use net, tried that before I added the line and it was dead.
 but now i get "SIOCGIFFLAGS error: No such device" as a error, has also tried to start the wlan0 fromm root . . didnt work,  "ignoring unknown interface wlan0=wlan0." was the respond for that.
Will try to install the firmware uppdate when i manage to understand how to . . . have the file, know where to place it, but no more knowledge longer than that.

Think I´ll have a look at it tomorrow .. , now it´s coffee time ;)

Thanks.

vha

---

### Post by mingus on 2005-07-01
[QUOTE=vha]
Will try to install the firmware uppdate when i manage to understand how to . . . have the file, know where to place it, but no more knowledge longer than that.
[/QUOTE]

Suggestion:  If you have WEP enabled in the router, turn it off for now.

---

