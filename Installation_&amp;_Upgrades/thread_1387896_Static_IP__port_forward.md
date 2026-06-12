---
title: "Static IP / port forward"
date: 2010-01-22
forum: Installation &amp; Upgrades
---

### Post by rflores2323 on 2010-01-22
I am currently using transmisson on ubuntu 9.10 however want to switch over to Utorrent using wine to get more options as rss feeds etc..  I will still use transmission some aswell. 

I want to see if there is a guide on how to configure a static IP address on karmic? 

I have found the following how to on port forward (my router WNDR3300 for utorrent) [http://portforward.com/english/routers/port_forwarding/Netgear/WNDR3300/Utorrent.htm](http://portforward.com/english/routers/port_forwarding/Netgear/WNDR3300/Utorrent.htm)

but this pertains to using windows and not linux.  I am also a linux noobie.

---

### Post by darkod on 2010-01-22
Right-click the Network Manager icon, top right on your desktop. Select Edit Connections.
Then select the Wired, if you are using the LAN connection. I don't remember on top of my head how the buttons are called, but you should be able to figure it out from there. Look around. What you are looking for is Static IP, not automatic. It will allow to set manual IP, netmask and gateway. Also manual DNS servers (usually your router would do this role too).
If you have problems, ask.

---

### Post by doas777 on 2010-01-22
you should be able to follow the instructiosn for configuring the router exactly as they are, just replace firefox wherever you see IE. you may need to make sure that you have the sun java jre installed first though.

---

### Post by Saq on 2010-01-22
I had installed Protege4.2 and jdk1.6 also I had set the path in .profile, but whenever I am trying to open owl whiz tab in the terminal getting error
java.io.IOException: Bad file descriptor
	at java.io.FileInputStream.readBytes(Native Method)
	at java.io.FileInputStream.read(FileInputStream.java:199)
	at sun.nio.cs.StreamDecoder.readBytes(StreamDecoder.java:264)
	at sun.nio.cs.StreamDecoder.implRead(StreamDecoder.java:306)
	at sun.nio.cs.StreamDecoder.read(StreamDecoder.java:158)
	at java.io.InputStreamReader.read(InputStreamReader.java:167)
	at java.io.BufferedReader.fill(BufferedReader.java:136)
	at java.io.BufferedReader.readLine(BufferedReader.java:299)
	at java.io.BufferedReader.readLine(BufferedReader.java:362)
	at uk.ac.man.cs.mig.util.graph.layout.dotlayoutengine.DotProcess$1.run(DotProcess.java:112)
strange exception 
java.io.IOException: Bad file descriptor
	at java.io.FileInputStream.readBytes(Native Method)
	at java.io.FileInputStream.read(FileInputStream.java:199)
	at sun.nio.cs.StreamDecoder.readBytes(StreamDecoder.java:264)
	at sun.nio.cs.StreamDecoder.implRead(StreamDecoder.java:306)
	at sun.nio.cs.StreamDecoder.read(StreamDecoder.java:158)
	at java.io.InputStreamReader.read(InputStreamReader.java:167)
	at java.io.BufferedReader.fill(BufferedReader.java:136)
	at java.io.BufferedReader.readLine(BufferedReader.java:299)
	at java.io.BufferedReader.readLine(BufferedReader.java:362)
	at uk.ac.man.cs.mig.util.graph.layout.dotlayoutengine.DotProcess$1.run(DotProcess.java:112)

I have installed jdk from package manager but the same problem exists can anyone help me.

---

### Post by rflores2323 on 2010-01-23
edited
[IMG]http://yfrog.com/hqscreenshot004lp[/IMG]

---

### Post by darkod on 2010-01-23
You are using public IP for the ubuntu desktop setting. The public address is for your router, as per the screenshot.

On the other side of the interface, your router has private IP towards your network. That's the 192.168.1.1 you can see as gateway on your automatic desktop settings. For your desktop, your router private interface is the gateway.

Keep the router settings as they are (although it should work with the setting Get Dynamically From ISP too).
For the desktop, set the settings for example as:
IP 192.168.1.11
Netmask 255.255.255.0
Gateway 192.168.1.1
DNS 68.87.85.102; 68.87.69.150

Delete the value in Search Domains, the second DNS value shouldn't be there.

Then in router port forwarding set the port you want to be forwarded to 192.168.1.11. That's it. The fourth link for router port settings can't open so I can't see them.

Note: IP addresses starting with 192.168.x.x are known as private, to play with in your own home networks. Also 10.0.x.x. The others are public and only devices directly on the internet usually have them.

---

### Post by rflores2323 on 2010-01-24
edited

---

### Post by darkod on 2010-01-25
Not sure if it makes any difference, but you left the netmask in ubuntu LAN connection as 255.255.248.0, change it to 255.255.255.0.

Also, save the changes you did on the router, there should be option to save settings. Also try powering off the router, and after 10sec power it on again (but only after settings are saved or you will lose the changes you did).

Other than that, you did everything right. I can't see an error. If it still doesn't work try to talk to customer support of the router manufacturer, maybe they'll have an idea.

PS. Also, in the desktop settings between the two DNS values put ; not , I'm not sure if it makes difference but I use ;

---

