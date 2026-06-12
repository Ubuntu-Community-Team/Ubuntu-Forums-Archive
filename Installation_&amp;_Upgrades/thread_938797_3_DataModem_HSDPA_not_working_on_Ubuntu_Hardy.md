---
title: "3 DataModem HSDPA not working on Ubuntu Hardy?"
date: 2008-10-05
forum: Installation &amp; Upgrades
---

### Post by fikelfikel on 2008-10-05
Hi. I recently decided to switch to Ubuntu, after a nasty virus hit Vista. I destroyed all my files. Anyhow, I'm from Ireland and I bought a 3 Datamodem HSDPA, to get ready for the net, before installing Ubuntu. I have a dual-boot system, Vista and Ubuntu. I looked at Ubuntu's site for help. I found something but it didn't work. It was called Gnome-PPP. (Now, I'm almost a complte beginer on Ubuntu, so most of this I won't understand) It was a solution for Huawei E220. It is my modem al right, but the instructions were for the origional version. I even tried istalling Wine, to see if it would work with the drivers for Windows. (Sorry if I'm a bit confusing, I'm natrally like that) Didn't work.

Oh Please, just PLEASE have a solution, as I don't want Vista on it anymore.

:(

I tried the vodafone driver, but came up as an error "Not satisfiable" or something.

---

### Post by stepol on 2008-10-05
I am using this modem also but in Intrepid and it is working out of the box . My advice is to upgrade to the beta of Intrepid and use this .:)

---

### Post by Plumtreed on 2008-10-05
I think the E220 should work 'out of the box' with Hardy and GnomePPP.

Use *99#  as the phone number and,in setup, change the 'type' to usb. I suspect you have to put something in as a password but anything short and sweet will do.

You have to be aware that your browsers and machine may 'think' as if offline. All appearances will be as if offline! Go to  FILE>OFFLINE Click that in your browser once connected. My machine has a 'key' to select/deselect WIFI and I have to turn that to off.

Good luck but if it doesn't work, give us more details.

---

### Post by fikelfikel on 2008-10-07
Hi, I'm just about to switch to Linux now. Thanks, I'll keep you posted. I'm using Windows at the moment

---

### Post by Plumtreed on 2008-10-09
> **fikelfikel said:**
> Hi, I'm just about to switch to Linux now. Thanks, I'll keep you posted. I'm using Windows at the moment

There are other things you can try and you should also be aware that Intrepid, Ubuntu version 8.10, is due out the end of Oct, reportedly, the new NetworkManager takes care of these things 'seamlessly'! You could wait a couple of weeks or even download the 'unofficial' version now. 

However, GnomePPP works, check the following things;

Open GnomePPP and in "setup" make sure you have USB Modem selected.

In "OPTIONS" have only the following selected; Check Carrier Line, Check Default Line,Ignore Terminal Strings(Stupid Mode). Each should have a 'tick' mark.

Also, because you are in Ireland,  use as 'Username' 3ireland and also as your password, 3ireland.

If you are asked for an ISP (APN) use 3ireland.ie

Good luck and let us know what happens?????

---

### Post by fikelfikel on 2008-10-10
Oh my GOD! A million thanks to you! It updated n' everything! Now I can trash vista and use Ubuntu. Oh thanks!

---

### Post by fikelfikel on 2008-10-10
I just did a fresh install of Ubuntu over Vista and Internet is working brill! Now I can get the track names in Rythembox and update security and stuff like that. A huge thanks for that!

---

### Post by Plumtreed on 2008-10-10
I am pleased to hear you are able to switch to Ubuntu and get on the net.
Sorry about not spelling your name correctly!

What course of action did you take? Are you using GnomePPP or did you go to Feisty 8.10?

How is the 'speed' and is the 3 pricing reasonable? Did you consider using you mobile as a modem or isn't that done in Ireland?

---

### Post by fikelfikel on 2008-10-11
Hi plumtreed! I used Gnome PPP. Speed, I have to say is actually an improvement to Vista. I don't have a three phone, and anyhow, Three DataModem is very resonably priced. I contacted Three before seeing if they had a Linux driver, but they didn't. I contacted them again and told them what to put in. I also told them about you aswell, as you were the one who figured it out. Howdidya figure it out anyway? I also made a link to this thred. I'm happy now, and sending this post with Ubuntu?

Do you think I could improve the speed by changing the speed setting? Or should I just leave well enough alone?

---

### Post by Plumtreed on 2008-10-11
It's all here in these forums! As you get used to finding your way around you will discover why Ubuntu is so popular. If you can't locate the solution on the forum, someone on the forum will help.

It works because everybody contributes, even in small ways!

Leave well enough alone for the moment. See what comes out of the new version 8.10 to be released at the end of the month!

---

