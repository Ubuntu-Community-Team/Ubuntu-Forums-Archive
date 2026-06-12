---
title: "Step by step with Tor"
date: 2007-04-23
forum: Installation &amp; Upgrades
---

### Post by Neo2 on 2007-04-23
HI all,
This is a long shot, but maybe someone will have mercy on a nube. I want to install Tor and Privoxy into Edgy, tried to download using synaptic (or was it via the terminal, not sure now?) but didn't install, at least the Tor button doesn't work in FF. Could anyone give me a step by step list of things to do to get this to happen, I feel so naked on the net without Tor running! Please!!

Neo

---

### Post by bpont on 2007-04-27
Google is your friend:

[http://blog.aizatto.com/2006/09/01/protecting-your-privacy-setting-up-tor-in-ubuntu-dapper-drake/](http://blog.aizatto.com/2006/09/01/protecting-your-privacy-setting-up-tor-in-ubuntu-dapper-drake/)

   1. Run the command: sudo apt-get install tor privoxy
   2. Run the command: sudo gedit /etc/privoxy/config
   3. Add the line (including the period at the end): forward-socks4a / localhost:9050 .
   4. Comment out the line: logfile logfile
   5. Comment out the line: jarfile jarfile
   6. Restart the Privoxy service: sudo /etc/init.d/privoxy restart

How to set up Firefox to work with Tor:

   1. Install the torbutton extension.
   2. Restart Firefox
   3. In the bottom right corner you&#8217;ll have a text blurb saying: Tor Disabled
   4. Enable Tor by clicking the blurb; it should say: Tor Enabled
   5. Surf the web

(Note: I'm using Tor on Fiesty, using the above steps and all works well...as a final step, check your IP with Tor button off, turn it on and refresh...if the numbers are different, you're gold.)  ;)

---

### Post by discmaster on 2007-05-05
Hello,

bpont - installed TOR as per your instructions.

> Install the torbutton extension
Did that too, but when I run ifconfig in a terminal window with Tor disabled/enabled, the IP address shows no difference. Is it working or not??

How can I be certain it is working?

---

### Post by aashay on 2007-05-06
Tor won't change your local ip. To see the IP used by your machine to connect to the internet, goto [http://www.whatismyip.com]("http://www.whatismyip.com") See if this IP changes. ALso if you have torbutton enabled and FF still works, Tor is working too

---

### Post by klhrevolutionist on 2007-05-22
Can you tell me how to start both tor and privoxy each time I start ubuntu feisty up ? Thanks.

---

### Post by Rashid584 on 2007-05-22
Go to System > Preferences > Sessions.

Click new and type ```
gksudo /etc/init.d/privoxy; gksudo /etc/init.d/tor
``` and click OK

Everytime you login it will ask for your password again...although I'm guessing if you're using tor and such you don't mind a little extra security :p :)

BTW thanks bpont for the instructions, I got tor working :D makes things slower but the button is very handy...cool

-Rashid

---

### Post by incubus on 2007-05-27
But that would be terribly inconvenient!  : )

How about using the startup system links?
```

$ sudo update-rc.d -f tor defaults
$ sudo update-rc.d -f privoxy defaults

```

But it seems that those startup links are automatically created when you install the programs.

incubus

---

### Post by Rashid584 on 2007-05-27
I would have thought they start when you boot feisty anyway...try going to something like "System > Administration > Services" in Ubuntu (can't check now, using KDE) in KDE its in KControl, System Administration > System Services. 

You can just tick a box or something next to the things you want to start up at root...

To do it from a command line (ncurses actually, I think) do ```
sudo aptitude install sysv-rc-conf; sysv-rc-onf
```

You can use the space button to tick/untick a box. Remove it from all runlevels to remove it, add it to 2, 3 4 & 5 for most other things.

-Rashid

---

### Post by Sp|ke on 2007-09-22
I've managed to set up Tor and Privoxy with no problems but I'm trying to work out how to force Tor to change it's routing when I want it to (a la vidalia). It's trivial enough to restart it using
```

sudo /etc/init.d/tor restart

```

but thats less than ideal. I've gone through the man pages/online help/docs etc etc etc and unless I'm being blind I cant find it for the life of me.

Any help most apreciated cheers!

---

### Post by Neo2 on 2007-09-23
You need to get a Firefox extension called Live IP Address. When it's installed it has a function (in the drop down tools menu) which says force update now. Click that and it changes the IP!

Neo

---

### Post by Sp|ke on 2007-09-23
Thanks Neo, unfortunately I want it specifically for IRC sessions (dalnet K-lines an awfull lot of TOR exit nodes thanks to idiots abusing it) I'll download it anyway as I can pull the extension apart and work it out from there with a bit of luck.

Thanks.

edit 
Unless I'm missing something this appears only to display your current ip address, the force option merely updates the ip if it has changed?
/edit

---

### Post by Neo2 on 2007-09-23
Yes, this thought occurred to me after I posted too. I'm not sure but whenever I click on update the speed increaes and the IP changes, so naturally assumed that it was changing it. You may be right):P

Neo

---

### Post by Sp|ke on 2007-09-23
Heh, no problem, I think that's probably coincidental with TOR finding a new / faster route.

edit. Now sorted, just needed to telnet into Tor's control port with the right command (signal newnym) /edit

---

### Post by kcallis on 2007-09-24
How does one make sure that they get a specific geographical IP address? For instance, I am in Mexico, but I need my appearance to look from the US. I keep trying to start a service, but it tells me that this service is only available in the US.

---

### Post by Sp|ke on 2007-09-25
> **kcallis said:**
> How does one make sure that they get a specific geographical IP address? For instance, I am in Mexico, but I need my appearance to look from the US. I keep trying to start a service, but it tells me that this service is only available in the US.

This should do what you want kcallis

> 
source: [http://en.linuxreviews.org/HOWTO_use_the_Internet_anonymously_using_Tor_and_Privoxy](http://en.linuxreviews.org/HOWTO_use_the_Internet_anonymously_using_Tor_and_Privoxy)

use MapAddress for given sites. It allows you to make sure every connection to a given site goes through the same connection. This is also a good option if you need given sites to be visited from a given country. 

For example, 
MapAddress [www.nsa.gov](www.nsa.gov) [www.nsa.gov.nadia.exit](www.nsa.gov.nadia.exit)

will make all visits to [www.nsa.gov](www.nsa.gov) always use the edit node nadia, which is located in the US. There are anonymity issues with this; if you're the only one using it then [www.nsa.gov](www.nsa.gov) can at least figure out that it's the same guy who's visiting when connections are coming from that exit node.

---

### Post by Seisen on 2007-09-25
Thanks for the information about  Map Address. I use tor once in a while and I didn't know that you could do that.

---

### Post by catfacts on 2008-01-31
Thanks, the proxy settings are what threw me. Now, will this affect all my internet or just FF? I hope i dont have to uninsall it because it kills my torrents. (Legal ones)

---

### Post by Wartooth on 2008-02-11
I followed the instructions linked and posted above, but when I click the Tor button on my browser, well, I can't browse:

>  404  	
This is Privoxy 3.0.3 on localhost (127.0.0.1), port 8118, enabled
No such domain

Your request for [http://whatismyipaddress.com/](http://whatismyipaddress.com/) could not be fulfilled, because the domain name whatismyipaddress.com could not be resolved.

This is often a temporary failure, so you might just try again.


What sort of stupid mistake have I made, or what have I overlooked?

---

### Post by ceminino on 2008-02-21
> **catfacts said:**
> Thanks, the proxy settings are what threw me. Now, will this affect all my internet or just FF? I hope i dont have to uninsall it because it kills my torrents. (Legal ones)

I have the same question, and it seems to me that unfortunately the this only affects firefox. Is it possible to change the IP in bittorent also? I use ktorrent.

---

### Post by siar on 2008-06-24
> **aashay said:**
> Tor won't change your local ip. To see the IP used by your machine to connect to the internet, goto [http://www.whatismyip.com]("http://www.whatismyip.com") See if this IP changes. ALso if you have torbutton enabled and FF still works, Tor is working too


 i installed torbutton for ff and my internet works but it is displaying my real ip address when i go to that site, and i have tor installed and privoxy installed and forwarding to tor with that config line and restarted it after but still no go, so there is some problem maybe with the configuration of torbutton i think i have anyway

---

