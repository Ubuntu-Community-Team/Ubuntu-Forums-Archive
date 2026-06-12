---
title: "File sharing (security?) problems between Win7 &amp; Ubuntu"
date: 2015-04-05
forum: MINT
---

### Post by branden4 on 2015-04-05
I'll prelude this with I that I tried Damn Small Linux and one other versions before deciding on "Linux Mint 17.1 Cinnamon 64-bit" aka Rebecca. I thought this would be the most 'feature rich' version with things like samba..etc pre-installed.

I had an Alienware laptop running with 7 Home Premium. Long story short, it got a virus and in the process of disabling it, I (or it) nuked half my system and I decided to try going back to ground zero with it. However, I would like to get my data files off first (movies..etc) and things that need no installation. Normally I just throw linux on a jumpdrive, live boot and use a USB and in an hour I am done.

Well for some reason the jumpdrive I got from new egg was 128GB (for only 15) and turned out to be a dud and is highly unreliable. My other jump is what I am using to boot Mint onto the Alienware with. So I figured why not just set sharing permissions on the folders and drag/drop. However, I am having an incredibly difficult time accomplishing this. I can (usually) see the both computers from both computers. However, accessing any given folder is extremely hit and miss. 

Laptop / Alienware / Mint (which is running live from Ram)
-If I make a new folder (Temp Drop) Shared / Others create & delete / Guest allowed. I can fully see AND access that folder (Temp Drop) across the network via the desktop. Of course its in the OS, which is ram, so it doesnt really exist per say. On restart it.. and thus anything in it is getting destroyed. Hence part of why I am trying to avoid it. I thought it might be windows permissions causing an error. So I tried creating Temp2 via Mint on the harddrive.. the desktop cannot access that folder though.


So I *could* drag them 1 by 1 into the temporary folder created in ram and send them across the network that way, but that would be twice the work and some of the files are several GB as individual files.

My desktop (Win7 Ultimate SP1, but a somewhat old PC)
-C:\NetDrop is set so Admin, my account (an admin) and 'Everyone' has 'Full Control" on it.
-C: shared the same way (not advisable I know, but just trying to get ANY kind of stable connection for short term work)
-Can see the Mint OS root shared folder and "Temp Drop". However it can only access "Temp Drop" and not the OS Root on the mint which contains the former Win OS and my data files

-Advanced file sharing, on.
-Network discovery, on.
-Ive tried 128 bit and 40/56 bit encryption.
-I've tried turning windows firewall both on and off.
-I've made sure the windows firewall rules for file/print sharing were enabled. 

Homegroup listener / provider are disabled since thats only designed for Win7.
Services turned on (basically anything I could think of that even remotely involved networking got turned on at some point)
-Server
-Computer Browser
-Function Discovery Provider Host
-Function Discovery Resource Publication
-Group Policy Client
-IPsec Policy Agent
-Network Connections
-Network List Service
-Network Location Awareness
-Peer Name Resolution Protocol
-Peer Networking Grouping
-Peer Networking Identity Manager
-SSDP Discovery
-Windows Time

Why am I having access or security problems? This is all done via personal netgear router over wifi. I tried a direct wifi ad hoc, but I wasn't able to see either computer from the other when I did that regardless of WPA, WEP or no encryption/security at all. They did appear to connect, they just wouldnt show any resources. How can I setup a stable file sharing environment between Win7 and Linux Mint Rebecca Live?

---

### Post by branden4 on 2015-04-05
Quick follow up with some additional details.

I dont have Windows Live Sign In installed. On the wireless connection on my desktop I also confirmed Network & Internet > Network Connections > Wireless Network Connection > Properties > IP 4 Properties > Advanced > WINS has LMHOSTS lookup enabled and NetBIOS is set to default.

---

### Post by Bucky Ball on 2015-04-05
*Thread moved to **MINT**.*

While Mint is based on Ubuntu, it is not officially supported in the main areas here. Please feel free to post in this section. Mint also has a vibrant community with a very active forum. Good luck. ;)

---

### Post by branden4 on 2015-04-06
Well to be honest I didn't have my heart set on Mint per say if something would work better. I just thought it would be a good starting place. I tried the regular Ubuntu and didnt have any success. If someone has a regular ubuntu live setup that will work, I would gladly put it to use.

Follow Up

My Mint can now see my Win7 and read/write. (May have just needed a restart for some changes to take effect?). However, my Win7 still cannot access my Mint.

---

### Post by Bucky Ball on 2015-04-07
Win7 will not access Mint. Your Mint install will be on an EXT* filesystem partition. Windows has no idea what they are and cannot read/write them. 

If you want to share data, best to have create a /shared NTFS partition for data you wish to use in both Ubuntu and Win.

---

### Post by branden4 on 2015-04-07
Oh right. Duh. I read something similar at one point and it never clicked once I got the other half up and running. I think because the live version didn't explicitly say anywhere what file system it was running it never flipped the light bulb on.

I knew there was a reason I've been wanting to move to Linux / Ubuntu, it always seems to do what windows cant.. and faster when it can.

Thanks!

---

### Post by Bucky Ball on 2015-04-07
All good. I have a small partition for sharing files (about 20Gb from memory) but use Win so rarely it sees action perhaps once a year. ;)

---

