---
title: "Firefox updates and BT Hubs"
date: 2010-11-09
forum: Installation &amp; Upgrades
---

### Post by Hopalong on 2010-11-09
Firefox updates do it again! My web connections are as follows:
  Dell desktop running Ubuntu 10.10 Lucd. Connected to a BT Hub by wire.
  Asus laptop running Lucid. Connects to the same BT Hub wirelessly.
  The latest updates to Firefox (loaded by the update manager as they come) renders the desktop firefox useless. The top line symbol shows 'Networking disabled', starting Firefox gives (a copy of?) "Welcome to Ubuntu 10.04 LTS!" but selecting a stored tab tells me it is in offline mode. Unticking the 'Work offline' in the filemenu and retrying gives "Server not found"
  This has happened before sometime sround June. I then laoded an old version of Firefox, which worked, and refused all online updates until a new version came out. Trying that worked, and I've been using it since.
  The laptop continues serenely on via wireless (its where I am right now)!
  What's afoot, what should I do about it, and what can the Fiefox experts do wuith this info?

---

### Post by efflandt on 2010-11-09
I doubt if a Firefox update is affecting networking, but lack of networking can affect Firefox when it cannot access the internet.  It is not clear if you are having trouble with one of the computers or both.

It is also confusing that you mention "Dell desktop running Ubuntu 10.10 Lucd." when 10.10 is Maverick (Lucid was 10.04), and installing an older Firefox version in June (which computer).  If you have multiple versions of Firefox installed (manually and through repositories or updates) that could confuse the issue.

If the network applet indicates that the network is down, you first need to figure out why that is happening.  The output of **sudo lspci -v** (or **sudo lsusb -v** if a USB device) related to the network device not connecting might reveal something that someone may be familiar with.  Or if both are having trouble, it may be an issue with the BT Hub.  But you cannot expect help for unknown hardware.

Current version of Firefox in both 10.04 and 10.10 is 3.6.12.  Help > About Mozilla Firefox may reveal if you are running the most recent version or older version.

---

### Post by Hopalong on 2010-11-10
Sorry for the confusion: 1) I am having trouble with the Dell desktop but not the laptop. As I see it, the crucial difference is the hub connection: wired with the desktop, but wireless for the laptop.  2) Both machines are runnimg Lucid - 10.04 (I've heard so much about 10.10 it's stuck in my head!), 3) The Fiefox is that I loaded in the summer to try after I had the problem, and found to work' I have since taken the online updates. Its the only version of Firefox on the machine.
  What I find baffling is that the wireless link to the hub works, but the wired link does not. Also has come about, presumably, due to a Firefox online update, as it obviously did before. (The earlier version of a Firefox releae was alright so long as I refused the updates.) 
  The network itself is fine: accessed wirelessly. it is simply the desktop that is telling me it is unavailable. Why is the mystery.
  When I have the time, my next step woill be to take out the wired connecion and try to run the desktop wirelessly. But what worries me is that it is when I take a particualr online update to Firefox that these events conme about. That, to me indicates a bug somewhere in the Firefox code, that went away in the latest full release, and is now back again via an update. Doesn't that seem a reasonable view? Thanks for the attention.

---

### Post by Hopalong on 2010-11-17
Further mysteries. Talks with BT, and resulting trials produce the following. 1. Windows Vista on the desktop runs Explorer quite happily - with its wired connection. (This is how I'm placing this here.) 2. I don't have Windows on the laptop. (The retailers put it on, but the partitioning - four partitions each with something in - made it impossible to run Ubuntu as well, so I ditched Windows: so I cannot try Windows with the laptop's wirless connection 3. I cannot try Ubuntu Firefox wirelessly in the desktop unless I get a wireless module into it - how do I do that? 4. It is the the latest Firefox that will not connect from this machine. I would like to try an earlier Firefox. How do I get one - must I unload the existing one first? 5. I've tried talking to BT about this, but they are only concerned with shifting the blame to Firefox.
 Grateful thanks to anyone who can get me out of this mess!

---

