---
title: "Unable to connect to FTP running inside VirtualBox"
date: 2008-06-26
forum: Installation &amp; Upgrades
---

### Post by junkam on 2008-06-26
I have set up an Ubuntu machine running inside VirtualBox. I also setup an FTP server running on the virtual machine using GPROFTPD. In order to connect to the FTP server I configured NAT port forwarding from the host machine (port 2121) to the virtual machine (port 21).

However I can not connect from the host machine via FTP to the virtual machine. When I connect I'm able to login to the virtual machine's FTP but then the FTP client enters **passive mode** tries to LIST and gets connection timeout.

I'm guessing the problem has someting to do with the passive mode ports, but I don't know what I need to do to configure them correctly. 

Please help

---

### Post by flytripper on 2008-06-27
me too .. i was trying to connect to media centre via my 360 to no avail....i think i need to know what to bind the network card to..trouble is i dont :S

---

### Post by junkam on 2008-07-01
Until a solution is found I just use Active mode in the client which works so far. However I would like to know how to set it up to work with passive mode

---

### Post by turezky on 2008-09-08
Hmm, wierd, active mode didn't work for me :(

---

### Post by friksaw on 2008-10-03
I was facing the same problem (though with a Puppy Linux guest and PureFtpd server). Connecting to the ftp server worked, but opening data connection to list files didn't. I received ```
500 I won't open a connection to 127.0.0.1 (only to 10.0.2.2)
```

My workaround, using FileZilla, is to use Active Mode and make the following Settings:

[IMG]http://img504.imageshack.us/img504/8438/testvs4.png[/IMG]

Where 10.0.2.2 is the guest's gateway address.

And just to be clear, that was done after setting up port forwarding as explained in the VirtualBox manual.

---

