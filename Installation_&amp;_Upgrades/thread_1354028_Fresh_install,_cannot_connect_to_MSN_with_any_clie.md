---
title: "Fresh install, cannot connect to MSN with any client"
date: 2009-12-13
forum: Installation &amp; Upgrades
---

### Post by potatan on 2009-12-13
Hi,

I managed to convert a friend from Windows to Ubuntu.  It wasn't difficult, because Vista was doing its usual tricks on a one year old laptop, blue screens, random reboots, bloated extra software installations, full notification area, constant Zonealarm alerts...  the usual stuff!

So I wiped the hard drive and put a fresh copy of Karmic on there, downloaded all the updates, rebooted, and all was fine.  Internet works fine, wireless works fine, DVDs and music play fine and she was already a Gimp and OpenOffice user in Windows so no change there.

But.. I cannot get connected to MSN.  I tried with Empathy, Pidgin and aMSN, but none of them would connect to either her account or mine.  The connections would just time out.  I tried uninstalling all three from Software Centre and reinstalling separately, but still no connection.  Both hers and my accounts are active on MSN, and I can log into my account on my own desktop also running Karmic (having performed a release upgrade).  I have also recently installed a fresh copy of Karmic on my own laptop, and Pidgin / aMSN work fine there also.

Her laptop is a Sony Vaio PCG-7144M.

I did a bit of googling and tried a solution to kill telepathy-butterfly, but this didn't do anything as there was no such process running at that time.  I also tried installing pidgin-pecan, but this didn't help either.

It is not (as far as I'm aware) a router issue in her home, as she used to log in to MSN through Windows before I converted her machine.

Any ideas anyone?

Bear in mind that I don't have the machine in front of me, so any suggestions for me to try will take a little while for me to get results because I will have to email her the details of the proposed solution for now.

Many thanks in advance.

---

### Post by MaindotC on 2009-12-13
I can tell you this: It doesn't have anything to do with your hardware, and rather than installing/uninstalling apps all you'd have to worry about is the configuration folder in your user directory that relates to whatever client you are using.  So, if you think you need to start fresh with the application, just move (or remove) the folder for your configuration settings...it's probably .amsn or something preceded with a dot.  I use pidgin with just adding my username (email address) and password and it works just fine.

---

### Post by potatan on 2009-12-14
Cheers for the tip about uninstalling, but I still need a solution to this error of not being able to connect to MSN with any client.

What I should do is take my own laptop round to see if I can connect, at least then I will know it's not her machine and possibly the router. But in the meantime does anyone else have any ideas?

Actually, does anyone know if Microsoft Live Messenger/MSN uses different ports to Pidgin / aMSN / Empathy?  I would very much imagine not, but it'd be nice to have it confirmed.

Thanks.

---

### Post by MaindotC on 2009-12-14
> **potatan said:**
> Cheers for the tip about uninstalling, but I still need a solution to this error of not being able to connect to MSN with any client.

I'm trying to help you narrow down the problem by reducing the number of angles you pursue in solving the problem.  If you think the access point is the problem (although I sincerely doubt it is - nor is this a port issue), just remove the access point and plug into your cable modem or whatever you use to connect to your ISP.

---

### Post by potatan on 2009-12-14
Sorry, I wasn't trying to be picky :-)

But trying three separate clients, which would presumably have three separate ~/. hidden config directories, would seem to be enough to indicate that the problem is a little beyond a mere MSN-type client configuration issue.  

I guess I'm going to have to lug my laptop round to my friend's house and see if I can diagnose it further with a client that I at least *know* is working through my router.  Good idea to plug her machine straight in the router (instead of connecting over wireless), but if the rest of the internet works (well at least the WWW bit...) then it's difficult to believe that MSN ports are blocked wirelessly whilst other ports are open.

Cheers,
Paul

---

### Post by j3rryf4n on 2009-12-14
Hello,
I'm using Empathy, it comes with Ubuntu 9.10.

To get it working follow this:
Applications / Internet / Empathy. Then follow the setup of Empathy.
If you already own a MSN account then click: Yes, I'll give my account informations (or something like this), click next.

On the next page, you've to select which client you'd like to use, then in the next line you've to enter your Windows Live Username, for example: [email]myacc@hotmail.com[/email], then type in your password.

If you've other accounts and you'd like to add any, then click 'Yes' if no then click 'No'.

When you are done then click 'Accept'.

The setup has been finished, if you wait about 6 seconds till it logs in then you'll see your MSN contact list.

---

### Post by j3rryf4n on 2009-12-14
> **j3rryf4n said:**
> Hello,
I'm using Empathy, it comes with Ubuntu 9.10.

To get it working follow this:
Applications / Internet / Empathy. Then follow the setup of Empathy.
If you already own a MSN account then click: Yes, I'll give my account informations (or something like this), click next.

On the next page, you've to select which client you'd like to use, then in the next line you've to enter your Windows Live Username, for example: [EMAIL="myacc@hotmail.com"]myacc@hotmail.com[/EMAIL], then type in your password.

If you've other accounts and you'd like to add any, then click 'Yes' if no then click 'No'.

When you are done then click 'Accept'.

The setup has been finished, if you wait about 6 seconds till it logs in then you'll see your MSN contact list.
Oops, sorry I didn't read the other posts before posting. It's my fault...

Well, anyways I don't have any problem with router connection. What's about your driver?

---

### Post by MaindotC on 2009-12-14
> **j3rryf4n said:**
> What's about your driver?

This has nothing to do with a driver.  You're likely entering account information incorrectly.

---

### Post by potatan on 2009-12-14
> **strAlan said:**
> This has nothing to do with a driver.  You're likely entering account information incorrectly.

I think j3rryf4n is okay, judging by his posts, but I agree it's unlikely a driver issue of any sort.  As for me, my account info is correct.

---

### Post by MaindotC on 2009-12-14
Based on the information you've provided, it has nothing to do with Ubuntu.  If you are certain you are entering your account information correctly, and you have removed the associated configuration files (or temporarily removed them) and started anew, there is nothing more to troubleshoot from a Ubuntu standpoint.  What settings are you showing in the Advanced tab?

---

### Post by potatan on 2009-12-14
I can't answer that as I don't have the affected machine in front of me (it belongs to a friend).  Will update when I've tried deleting the settings and re-installing.

cheers
Paul

---

### Post by MaindotC on 2009-12-14
Thanks - keep us updated and hopefully we'll get this worked out.

---

### Post by potatan on 2009-12-20
I took my laptop round to my friend's house and I couldn't connect either (despite connecting at my own home an hour earlier).  Additionally, she has a new housemate and she couldn't connect using Vista.  So as suspected... it was nothing to do with Pidgin, aMSN, Empathy.  

Turns out it was an ISP problem that has now been cleared!

Cheers for the helps.

---

### Post by MaindotC on 2009-12-20
> **potatan said:**
> Turns out it was an ISP problem that has now been cleared!

This is highly unlikely and I'm going to call your bluff.  Please explain.

---

### Post by potatan on 2009-12-20
You obviously don't use TalkTalk as your ISP.

Simple process of elimination really.  I used Pidgin at my sister's house on my laptop, on her ISP, it worked fine.  I then visited my friend with the problem an hour later. Pidgin wouldn't work on *my* laptop, using her ISP (TalkTalk).  I then went home, and Pidgin worked fine using my ISP.

Additionally, her new housemate could not connect to MSN with her Vista laptop either.  There had been no changes to their router setup for instance, but I eliminated that just in case by resetting the router config and re-connecting.  Same problem.  As well as the MSN problems they were both having difficulty connecting to some websites (but not all) - BBC worked, Yahoo mail didn't (though Yahoo news did).

The next night, everything started to work again, with no intervention from either me, my friend or her housemate.  So I can only deduce from that that it was some sort of ISP problem, considering we tried three different laptops using two different OSes.

Sound reasonable?

---

### Post by potatan on 2009-12-20
Here's a list of current and recent TalkTalk outages, for instance:

[http://www.talktalk.co.uk/outages](http://www.talktalk.co.uk/outages)

---

### Post by MaindotC on 2009-12-20
> **potatan said:**
> Sound reasonable?

Absolutely absurd.  The ISP simply provides a connection to the user - it doesn't filter services or firewall anything, except in the most extreme cases like known abusive IP's or emails or other attacks - certainly not one of the most widely used chat clients in the world.  Unless you have an official quote from a representative or documentation you have no right to accuse the ISP, especially seeing as how you don't know. I work at an ISP and I am so sick and tired of people calling for help with issues that have nothing to do with the ISP!  All they do is provide a connection!!

---

### Post by potatan on 2009-12-20
Well unless you're prepared to offer a better answer, I'm sticking with it.  As well as no MSN, speedtest.net gave her a normal download speed, but no ability to upload.  And the same was true for the ISP's own speed test page, which she went through whilst on the phone to their support people.

Can you think of a situation whereby these things can happen? DNS problems at the ISP perhaps?  Or alternatively, an explanation as to how they can happen if there is no apparent fault in either the local LAN inside the router, or on the router itself?  I'm genuinely interested (as an IT consultant with 25 years experience)

Cheers
Paul

---

