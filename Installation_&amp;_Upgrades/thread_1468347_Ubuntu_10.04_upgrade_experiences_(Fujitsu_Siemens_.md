---
title: "Ubuntu 10.04 upgrade experiences (Fujitsu Siemens Esprimo Mobile V6515)"
date: 2010-05-01
forum: Installation &amp; Upgrades
---

### Post by jjaakkol on 2010-05-01
I do not know if this helps anyone but here is my story about upgrading 10.04 :)

First I tried upgrade my 9.10 to 10.04 via update manager, upgrade was halted so had to shutdown laptop manually and after that I tried Linux but it did not worked at all (which wasn't surprise as upgrade was halted). 
Then I removed Ubuntu totally from Windows side (I have Vista also in same laptop) and installed 10.04 with [wubi-r189.exe]("http://people.canonical.com/%7Eevand/wubi/lucid/wubi-r189.exe").  [http://people.canonical.com/~evand/wubi/lucid/]("http://people.canonical.com/%7Eevand/wubi/lucid/") 

First place installation went fine but when I restarted PC in Linux side desktop didn't show anything, only background and mouse cursor was there.

After couple of tries I tried boot linux in "safe graphic mode" (or something like that) and then installation was finished properly.

In the beginning problems with WLAN but now it is almost OK. Wired connection was OK from beginning.

Only problem left is that 10.04 does not automatically connect to my WLAN which is hidden. With 9.10 this was OK. 

My laptop is Fujitsu Siemens Esprimo Mobile V6515 with AR5001 Wireless Network Adapter

---

### Post by jjaakkol on 2010-05-02
Now also automatic connection to hidden wireless works. I edited /etc/network/interfaces with following

# WLAN
allow-hotplug wlan0
auto wlan0
iface wlan0 inet dhcp
 wireless-essid [replace this with essid name]
 wireless-key [replace this with key in hex]

:)

---

### Post by quirinp on 2010-06-02
I have the same machine (Esprimo mobile V6515):)... only with XP installed

I exactely ran through the same... except that I am still trying to install ubuntu with that safe-graphix-mode direct from cd... I really prefered a faster system.
But one question: hadn't you a harddrive-space problem like me?
This is really driving me crazy. I can't do any update!:(
Please if you know that prob tell me how you solved it!!!

---

### Post by nanometer on 2010-07-17
> **jjaakkol said:**
> Now also automatic connection to hidden wireless works. I edited /etc/network/interfaces with following
 
# WLAN
allow-hotplug wlan0
auto wlan0
iface wlan0 inet dhcp
wireless-essid [replace this with essid name]
wireless-key [replace this with key in hex]
 
:)
I have the same problem would you mind telling me what exactly safe graphics mode is?
tnx

---

