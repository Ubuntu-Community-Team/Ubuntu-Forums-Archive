---
title: "Intel wireless flaky??"
date: 2009-07-23
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by mariner09 on 2009-07-23
Is anyone having really flaky Intel wireless on the current release?  NM constantly bounces up and down with a WEP connection.

---

### Post by psyke83 on 2009-07-23
What wireless chipset? Any pertinent information in dmesg? And for the love of God, why are you using WEP "encryption"?

---

### Post by mariner09 on 2009-07-23
Because there's nobody else in my hood doing wireless...

I have the 4965 chipset.  Both NM and WICD were bouncing every 2 minutes.  My VPN app isn't persistent, so it's very annoying.

I saw nothing in dmesg that looked to be a problem and I was tailing any log I could think of while watching it bounce with no indicators forthcoming.

I could see what else my router supports and play with different security.

---

### Post by OliW on 2009-07-23
> **mariner09 said:**
> Because there's nobody else in my hood doing wireless...Just because you can't see any other APs, doesn't mean they're not all using yours =)

---

### Post by wayne_cat on 2009-07-23
> **OliW said:**
> Just because you can't see any other APs, doesn't mean they're not all using yours =)

:lolflag:

---

### Post by mariner09 on 2009-07-23
Actually, I frequently check the logs and limit connection by MAC address.  If anyone else was using it, I should be able to tell.  That it unless they know any of my hostnames or spoof the MACs.

---

### Post by MacUntu on 2009-07-23
Seriously, try to upgrade to WPA2 as soon as possible - WEP isn't secure.

Back to topic: you can install the package "linux-backports-modules-karmic", which should contain updated drivers (IIRC). If it doesn't work, you can simply uninstall that package.

---

### Post by psyke83 on 2009-07-24
> **mariner09 said:**
> Actually, I frequently check the logs and limit connection by MAC address.  If anyone else was using it, I should be able to tell.  That it unless they know any of my hostnames or spoof the MACs.

It's trivially easy to spoof a MAC address and hostname, and since WEP encryption is a joke, a hacker would know it by now. MAC address whitelisting and turning off router SSID broadcast are very weak security measures, and doesn't stop the WEP data getting intercepted and cracked.

You really need to upgrade to at least WPA1/TKIP or WPA2/AES if possible. If your router doesn't appear to support it, there may be firmware upgrades available from the manufacturer.

---

### Post by mariner09 on 2009-07-24
I generally install the backports drivers, but maybe that's not such a good idea in this case.  

Also looking into router firmware...

---

### Post by hugmenot on 2009-07-24
> **psyke83 said:**
> You really need to upgrade to at least WPA1/TKIP or WPA2/AES if possible. If your router doesn't appear to support it, there may be firmware upgrades available from the manufacturer.

Myself, I run completely open, unencrypted. And now? Why are people not more friendly to their neighbors anyhow?

---

### Post by BCurtisWX on 2009-07-24
> **hugmenot said:**
> Myself, I run completely open, unencrypted. And now? Why are people not more friendly to their neighbors anyhow?

</sarcasm>

---

### Post by hugmenot on 2009-07-24
> **BCurtisWX said:**
> </sarcasm>

No?

---

### Post by hugmenot on 2009-07-24
Maybe I should mention that I do have some tracking features in place.
I can track guest clients via a captive portal. I get their MAC and IP and how much traffic they caused in 12h windows. Then they get shown the page again and have to click the button. Ports for guests are limited to web, pop/smtp, and IM and some other ports.

If they use my network for more than a couple of months I walk to their door and ask if they consider it fair to contribute to the monthly bill like two of my other neighbors.

---

### Post by infamousrev on 2009-07-24
> **hugmenot said:**
> Myself, I run completely open, unencrypted. And now? Why are people not more friendly to their neighbors anyhow?

People like you make wardriving easy, Next time you recieve SPAM thank yourself for supporting it.


> 
 				 				**Re: Intel wireless flaky??** 			
 			 			 		   		 		 		Seriously, try to upgrade to WPA2 as soon as possible - WEP isn't secure.

Back to topic: you can install the package "linux-backports-modules-karmic", which should contain updated drivers (IIRC). If it doesn't work, you can simply uninstall that package.
 		                   		  		  		 		

This wrecked my internet connection when I tried it, watch out!

---

### Post by hugmenot on 2009-07-24
> **infamousrev said:**
> People like you make wardriving easy, Next time you recieve SPAM thank yourself for supporting it.

I highly doubt that people drive around in their cars with the purpose of locating open networks and the intent of sending spam once they associated with one. Why take the effort for only, say, half an hour of sending spam? They still need to find find an open smtp host. They gain nothing by using my public IP. Plus sitting in the car waiting for millions of spam mails to flow out must be really boring and people tend to notice you. They really prefer to use zombies in botnets for that.

Besides, my neighborhood is totally harmless. I never close the door to my roof terrace.

EDIT: Oh, and did you expect that [Bruce Schneier agrees with me]("http://www.schneier.com/blog/archives/2008/01/my_open_wireles.html")?

---

### Post by mariner09 on 2009-07-24
infamousrev, what wrecked your internet connection?

Going to WPA or removing backports?

---

### Post by infamousrev on 2009-07-24
> **mariner09 said:**
> infamousrev, what wrecked your internet connection?

Going to WPA or removing backports?

Installing the backports modules messed up my internet connection,

Uninstalling fixed it again


> I highly doubt that people drive around in their cars with the purpose of locating open networks and the intent of sending spam once they associated with one. Why take the effort for only, say, half an hour of sending spam? They still need to find find an open smtp host. They gain nothing by using my public IP. Plus sitting in the car waiting for millions of spam mails to flow out must be really boring and people tend to notice you. They really prefer to use zombies in botnets for that.

Funny that you say that, a friend of mine actually makes a living war driving.

What is the advantage of it? Spam smtps get blocked as soon as they get detected on special lists. There are live ban list synchronizing with all mayor mailbox sites.

Driving arround with advanged hardware is the most easy way to spread spam. There are special routers that connect to multiple networks at the same time checking their usuability. As soon as it detects a unsecured or WEP encrypted network it will mark that location using GPS.

As soon as they have made a visual map of the available networks they decide were to start sending spam.

I could show you a visual map he sent me of my home time, but I think that is against the Forum rules

---

### Post by hugmenot on 2009-07-24
> **infamousrev said:**
> 
Funny that you say that, a friend of mine actually makes a living war driving.


And I find it funny that you scold me for having an open network which hypothetically might be used for sending illicit email, but at the same time you claim to have a friend that earns money with this illegal activity.

That&#8217;s weird.

---

### Post by infamousrev on 2009-07-24
> **hugmenot said:**
> And I find it funny that you scold me for having an open network which hypothetically might be used for sending illicit email, but at the same time you claim to have a friend that earns money with this illegal activity.

That’s weird.

I did not say I approve that behavior. Because I don't approve it.

But lets stop talking off-topic

---

### Post by psyke83 on 2009-07-24
> **hugmenot said:**
> I highly doubt that people drive around in their cars with the purpose of locating open networks and the intent of sending spam once they associated with one. Why take the effort for only, say, half an hour of sending spam? They still need to find find an open smtp host. They gain nothing by using my public IP. Plus sitting in the car waiting for millions of spam mails to flow out must be really boring and people tend to notice you. They really prefer to use zombies in botnets for that.

Besides, my neighborhood is totally harmless. I never close the door to my roof terrace.

EDIT: Oh, and did you expect that [Bruce Schneier agrees with me]("http://www.schneier.com/blog/archives/2008/01/my_open_wireles.html")?

I guess you don't see the danger. Do you perform online banking on this network? If your network traffic is being intercepted unencrypted, they could compromise even SSL-protected connections with enough patience.

You may feel that you're doing a public service to others by keeping your wireless open, but what you are doing is offering free phone calls whilst simultaneously allowing anybody to lift another receiver and eavesdrop on your phone conversations. You are compromising your own privacy and security.

Neighbours are going to connect to your access point, and if they are using Windows (which is likely) it's going to expose their system's SMB shares to everybody on the network - they may not necessarily realise this. That *is* your fault, even if you didn't anticipate the problem.

Dude, seriously. Enable the encryption and tell your neighbours the password.

---

### Post by hugmenot on 2009-07-24
I&#8217;ll stop off-topic talk after this. Promise.

> **psyke83 said:**
> I guess you don't see the danger. Do you perform online banking on this network? If your network traffic is being intercepted unencrypted, they could compromise even SSL-protected connections with enough patience.


Yes, I do banking. What makes you think that TLS encryption is weaker than WPA encryption or maybe VPN crypto? What kind of patience do you have in mind? If you know of an unpublished way to exploit TLS in workable time please let me know at once. We might get a high impact paper out of it.
I make sure that banking, email, anything of value is always going over https, or imaps, or smtps etc. And I instructed my neighbor friends to do the same, acutely pointing to the fact that eavesdropping is a (hypothetical) possibility.

> 
You may feel that you're doing a public service to others by keeping your wireless open, but what you are doing is offering free phone calls whilst simultaneously allowing anybody to lift another receiver and eavesdrop on your phone conversations. You are compromising your own privacy and security.


I don&#8217;t care if people know I visit ubuntuforums. I don&#8217;t want them to read my email or chats, hence they are all going over encrypted connections. In the end, more dangerous people can intercept that stuff after it went out the router to my ISP.

> 
Neighbours are going to connect to your access point, and if they are using Windows (which is likely) it's going to expose their system's SMB shares to everybody on the network - they may not necessarily realise this. That *is* your fault, even if you didn't anticipate the problem.


No, they get educated about the nature of the network by my captive portal. It&#8217;s their call. If they wanted privacy they wouldn&#8217;t use my access point.
When I let a friend use my washing machine she is aware that afterwards I know the type of panties she wears. So what?

> Dude, seriously. Enable the encryption and tell your neighbours the password.
I guess what&#8217;s good for Schneier and Doctorow is also good for me.

Paranoia will only damage your character. I&#8217;m not american. Maybe this is why I&#8217;m not as afraid of fictive bad people as some here are.

---

### Post by MacUntu on 2009-07-24
My first concern wouldn't be _my_ traffic... I'm pretty positive you are legally responsible for what gets transmitted via your connection.

---

### Post by psyke83 on 2009-07-24
> **mariner09 said:**
> Is anyone having really flaky Intel wireless on the current release?  NM constantly bounces up and down with a WEP connection.

What you could do is keep a PC connected via the wired connection, and monitor the router's log/syslog (if available) and, while using the wireless on your laptop, monitor for transmission or encryption errors.

Also try to disable encryption, or other encryption methods (WPA) for testing purposes.

Have you installed the latest 2.6.31-4-generic kernel? If you're using the PAE version, try the regular generic version instead.

---

### Post by psyke83 on 2009-07-24
> **hugmenot said:**
> Yes, I do banking. What makes you think that TLS encryption is weaker than WPA encryption or maybe VPN crypto? What kind of patience do you have in mind? If you know of an unpublished way to exploit TLS in workable time please let me know at once. We might get a high impact paper out of it.
I make sure that banking, email, anything of value is always going over https, or imaps, or smtps etc. And I instructed my neighbor friends to do the same, acutely pointing to the fact that eavesdropping is a (hypothetical) possibility.

Even if I did, it's against the forum policy to post such information.

You're dismissing the threat potential too easily. If a hacker gains administrative access over a Windows PC, they can install a trojan or keylogger, they could modify the hosts file to direct your neighbours' banking web site to a forged copy (which can fools users, despite using invalid or no SSL certificates).

I'm not saying any of these scenarious are going to happen with a high degree of probability, but your "ideology" exposes users on your network to heightened risk.

> I don&#8217;t care if people know I visit ubuntuforums. I don&#8217;t want them to read my email or chats, hence they are all going over encrypted connections. In the end, more dangerous people can intercept that stuff after it went out the router to my ISP.

While I respect your opinion on this matter, I'm sure you can appreciate that others may feel differently.

> No, they get educated about the nature of the network by my captive portal. It&#8217;s their call. If they wanted privacy they wouldn&#8217;t use my access point.
When I let a friend use my washing machine she is aware that afterwards I know the type of panties she wears. So what?

I suspect that you're overstating the level of awareness your neighbours posses with regards to the security of their systems. A single rogue entity can compromise all of your neighbours' computers, it's really that simple.

> I guess what&#8217;s good for Schneier and Doctorow is also good for me.

Paranoia will only damage your character. I&#8217;m not american. Maybe this is why I&#8217;m not as afraid of fictive bad people as some here are.

This is not the place to discuss politics. Also, I'm at a loss to explain how your veiled contempt for - and feelings of superiority towards - Americans, strengthens your arguments. I may not be an American, but as a citizen of the "real world" I can see the value and need of privacy in certain situations.

In case it wasn't obvious, I wasn't suggesting that you should deprive your neighbours from using your access point.

---

### Post by mariner09 on 2009-07-24
I'll need to boot my spare drive tonight and toy with a few things.  It did cross my mind to try the regular kernel to see if it's any different.

---

### Post by mariner09 on 2009-07-24
Looks like backports isn't a solid automatic selection anymore.

I removed that package and my wireless is back to being solid.

---

