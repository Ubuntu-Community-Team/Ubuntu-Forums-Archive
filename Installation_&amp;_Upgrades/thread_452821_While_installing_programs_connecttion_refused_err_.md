---
title: "While installing programs connecttion refused err or encountered"
date: 2007-05-23
forum: Installation &amp; Upgrades
---

### Post by psanu on 2007-05-23
Hi,

While installing any application using synaptic i am getting the following error.

> 
W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/pool/universe/2/2vcard/2vcard_0.5-1ubuntu1_i386.deb](http://gb.archive.ubuntu.com/ubuntu/pool/universe/2/2vcard/2vcard_0.5-1ubuntu1_i386.deb)
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)


please help?

Thanks 

psanu

---

### Post by Metacarpal on 2007-05-23
What was the last change you made to your system before this started happening?

Port 4001 is closed on my computer, and since I haven't been playing with my firewall settings, I imagine it is on yours, too.  What puzzles me is why apt is trying to connect to localhost on that port.

---

### Post by psanu on 2007-05-24
Hi Metacarpal,

I am a newb in ubuntu and i have not been playing with my system much.I guess the last change updating the system with update manager. I am not very sure of this but i have not changed firewall settings , rather i do'nt know how to.
I am connected to internet via adsl usb modem. does this has to do with that?

I am not sure what to do.

Thanks 

Psanu

---

### Post by djchandler on 2007-05-24
> **psanu said:**
> Hi Metacarpal,

I am a newb in ubuntu and i have not been playing with my system much.I guess the last change updating the system with update manager. I am not very sure of this but i have not changed firewall settings , rather i do'nt know how to.
I am connected to internet via adsl usb modem. does this has to do with that?

I am not sure what to do.

Thanks 

Psanu

First, did update manager complete the previous update without problems or interruption?

My best guess is the error message means port 4001 failed to address the proper USB device, which would be the adsl modem. Try turning everything else off connected to your USB except your ADSL modem, disconnect everything else you can that draws power from USB and see if that works. If your keyboard and/or mouse are connected by USB, you have no choice obviously but to leave them connected. If that doesn't work, my suggestion is shut down the system, and power up again with only the ADSL modem (and your mouse and keyboard if they use USB) connected to your USB. Then run Synaptic.

Caution: I don't use USB for network connection. This is only an educated guess on my part.  Port 4001 uses UDP protocol, not TCP. Go to
[http://www.auditmypc.com/port/udp-port-4001.asp](http://www.auditmypc.com/port/udp-port-4001.asp)
for a description of port 4001 functions. HTTP connections usually use port 80. This is why I assume port 4001 is specific to USB connected devices.

---

### Post by psanu on 2007-05-24
Hi,

> 
First, did update manager complete the previous update without problems or interruption?


Yes it did.

And i have only the modem connected to USB. I have tried restarting to no effect. MY system is Dell 6400 Pentium Core 2 Duo Laptop. No other device has been attached to USB port.

I am stumped because ia have installed softwares like Wine and XMPlayer using 2-3 days back.

Thanks

Psanu

---

### Post by djchandler on 2007-05-25
> **psanu said:**
> Hi,



Yes it did.

And i have only the modem connected to USB. I have tried restarting to no effect. MY system is Dell 6400 Pentium Core 2 Duo Laptop. No other device has been attached to USB port.

I am stumped because ia have installed softwares like Wine and XMPlayer using 2-3 days back.

Thanks

Psanu

Is this a dual boot system, and if so, can you still boot Windows?

---

### Post by psanu on 2007-05-25
Yes ,it is a dual boot system.with Vista. I am able to Boot into Vista as well as Feisty. While inside feisty i am still able to browse internet using firefox. However i can't update the system neither install via synaptic. However no problem with download from same repositories .

Thanks Psanu

---

### Post by djchandler on 2007-05-25
> **psanu said:**
> Yes ,it is a dual boot system.with Vista. I am able to Boot into Vista as well as Feisty. While inside feisty i am still able to browse internet using firefox. However i can't update the system neither install via synaptic. However no problem with download from same repositories .

Thanks Psanu
If you can browse the internet and download e-mail, I think the only problem is that for some reason the repository you're trying to reach is offline, or you don't have permission to access it. I don't think there is anything actually wrong on your end except that your repository database is somehow incompatible with the repository you're trying to use. Or your connection may be getting refused due to high traffic at that location. But try this. Open Synaptic, go to settings, then repositories, make sure you're on the Ubuntu tab, then go down to "download from." On that drop down menu you should see "Main Server", then maybe the country closest to you geographically (mine says United States), and then "others." Try a different server and see if that works for you. Also go through each tab in Repositories and make sure the updates you want to get are checked. I had to go back in and re-check a box to get my Scribus to update.

---

### Post by psanu on 2007-05-29
hi

I finally got rid of the problem. I typed the following command

> 
sudo dpkg-reconfigure anon-proxy


and stopped anonymizing proxy service.Now i wonder when did started this . Does this start by default .Ama i supposed to use it?

Thanks for your help.

Psanu

---

### Post by djchandler on 2007-05-30
> **psanu said:**
> hi

I finally got rid of the problem. I typed the following command

sudo dpkg-reconfigure anon-proxy

and stopped anonymizing proxy service.Now i wonder when did started this . Does this start by default .Ama i supposed to use it?

Thanks for your help.

Psanu

Psanu,

Now you now know something the rest us didn't until you made this last post. Thanks for sharing the solution. You would think a setting like that wouldn't change unless you did purposely. You know you didn't, but who knows what might happen if you lost power with a file open. It happens here occasionally here in Kansas. We're right on the east edge of what is known as Tornado Alley. We can get some fierce storms here this time of year. I'm glad I could help what little I did. At least I hope it helped narrow your search for a solution. Good job! :D

Ciao,
D. J. Chandler

---

