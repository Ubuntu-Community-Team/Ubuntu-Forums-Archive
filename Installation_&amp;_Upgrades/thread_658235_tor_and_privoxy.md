---
title: "tor and privoxy"
date: 2008-01-04
forum: Installation &amp; Upgrades
---

### Post by nagla on 2008-01-04
> [http://blog.aizatto.com/2006/09/01/protecting-your-privacy-setting-up-tor-in-ubuntu-dapper-drake/](http://blog.aizatto.com/2006/09/01/protecting-your-privacy-setting-up-tor-in-ubuntu-dapper-drake/)

1. Run the command: sudo apt-get install tor privoxy
2. Run the command: sudo gedit /etc/privoxy/config
3. Add the line (including the period at the end): forward-socks4a / localhost:9050 .
4. Comment out the line: logfile logfile
5. Comment out the line: jarfile jarfile
6. Restart the Privoxy service: sudo /etc/init.d/privoxy restart

How to set up Firefox to work with Tor:

1. Install the torbutton extension.
2. Restart Firefox
3. In the bottom right corner you’ll have a text blurb saying: Tor Disabled
4. Enable Tor by clicking the blurb; it should say: Tor Enabled
5. Surf the web

(Note: I'm using Tor on Fiesty, using the above steps and all works well...as a final step, check your IP with Tor button off, turn it on and refresh...if the numbers are different, you're gold.) 

i found this on the web but i dont kno what it means by 


4. Comment out the line: logfile logfile
5. Comment out the line: jarfile jarfile

can someone help me...?

---

### Post by djrobthaman on 2008-01-04
So....  what do you want to do?

If you just want to install tor and have firefox browse the web that way just do the following.

Open synaptic package manager

Search for privoxy

Click on tor and tell it to install

Go to mozilla.com and search for the foxyproxy addon

Install foxyproxy

Follow the instructions

---

### Post by nagla on 2008-01-04
that accually helped alolt...
but is it possible to use a random ip adress every time i enable it or change what the ip will be?

---

### Post by djrobthaman on 2008-01-04
Tor is just a bunch of servers pieced together over the tor network.  So when you browse through tor, you are browsing through random ip addresses.... kind of

---

### Post by Sef on 2008-01-05
> 4. Comment out the line: logfile logfile
5. Comment out the line: jarfile jarfile

To comment out a line, you put a # at the beginning of a line.  It tell the computer to not read that line.

Thus if you had line like this:

This line is a test.

You would comment it out like this:

# This line is a test.

---

