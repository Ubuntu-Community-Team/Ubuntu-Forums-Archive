---
title: "Jackd,qjackctl error"
date: 2013-02-02
forum: Installation &amp; Upgrades
---

### Post by eGelor on 2013-02-02
After today's update i can't open qjackctl with the error :
> 
Cannot connect to server socket err = No such file or directory
Cannot connect to server socket
jack server is not running or cannot be started
Registered event listener change listener:  true 

5 D-BUS: JACK server could not be started. Sorry
Sat Feb  2 11:06:37 2013: Starting jack server...
Sat Feb  2 11:06:37 2013: JACK server starting in realtime mode with priority 10
Sat Feb  2 11:06:37 2013: control device hw:0
Sat Feb  2 11:06:37 2013: control device hw:0
Sat Feb  2 11:06:37 2013: Acquired audio card Audio0
Sat Feb  2 11:06:37 2013: creating alsa driver ... hw:0|hw:0|512|3|44100|0|0|nomon|swmeter|-|32bit
Sat Feb  2 11:06:37 2013: control device hw:0
QSpiAccessible::accessibleEvent not handled:  "2"  obj:  QMessageBox(0x7fff7ac8cf00) "" 
FIXME: handle dialog start. 
Sat Feb  2 11:06:37 2013: [1m[31mERROR: 
ATTENTION: The playback device "hw:0" is already in use. Please stop the application using it and run JACK again[0m
Sat Feb  2 11:06:37 2013: [1m[31mERROR: Cannot initialize driver[0m
Sat Feb  2 11:06:37 2013: [1m[31mERROR: JackServer::Open() failed with -1[0m
Sat Feb  2 11:06:37 2013: [1m[31mERROR: Failed to open server[0m

---

### Post by eGelor on 2013-02-02
A deamon runs behind jackd and use alsa... i remove 3-4 so i can't tell which is at the moment.

---

