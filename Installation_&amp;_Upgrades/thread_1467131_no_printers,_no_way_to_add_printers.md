---
title: "no printers, no way to add printers"
date: 2010-04-30
forum: Installation &amp; Upgrades
---

### Post by jbiwer on 2010-04-30
Installed 10.04 last night.  Most everything looks good and is running fine!
However, I just noticed *all* of my printers are gone and I do not have an option to add printers.  Suggestions?  Thank you!

---

### Post by Dubbayoo on 2010-04-30
Does the Printing applet show in Administration? Is there a printing system even installed?

---

### Post by eltonw on 2010-04-30
> **jbiwer said:**
> Installed 10.04 last night.  Most everything looks good and is running fine!
However, I just noticed *all* of my printers are gone and I do not have an option to add printers.  Suggestions?  Thank you!

Go to System=> Administration=> Printing.

HTH...

---

### Post by jbiwer on 2010-04-30
Previously did that, NOTHING there.

---

### Post by jbiwer on 2010-04-30
Not sure what you mean about printing system in stalled.
Yesterday, it worked with printing on my LAN at work.
Thanks.

---

### Post by jbiwer on 2010-04-30
Clarification: Yesterday, _before_ the upgrade.

---

### Post by eltonw on 2010-04-30
> **jbiwer said:**
> Not sure what you mean about printing system in stalled.
Yesterday, it worked with printing on my LAN at work.
Thanks.
Check and see if you have CUPS (Common UNIX Printing System) installed. Depending on how you did your install, and if you had your printer(s) connected at the time, its possible that it was not installed. You can easily launch Synaptic and search for it.

---

### Post by clevertomato on 2010-04-30
Sounds like same problem I'm having. I did a clean install of Lucid 64. On Karmic I had a network printer setup very easily by going into Printing and telling it the IP and JetDirect Port (ie. 192.168.3.252:9100 ) but in Lucid the interface is different (not good different) and when I choose "connect" and enter 192.168.3.252:9100 it opens a progress window but never succeeds at anything. I have to kill the process.

Edit: There must be ghosts here... the problem magically disappeared. I have no idea why. No updates have been applied, No new software installed. Oh well. It works for me now. Before the print dialog wouldn't even allow me to choose "add" but all works ok now.

---

### Post by jbiwer on 2010-04-30
> **eltonw said:**
> Check and see if you have CUPS (Common UNIX Printing System) installed. Depending on how you did your install, and if you had your printer(s) connected at the time, its possible that it was not installed. You can easily launch Synaptic and search for it.


Thank you!  No printers were attached at the time of the upgrade 
(local or network).  Not sure about Synaptic, where is it how to I run it?
Thanks again.

---

### Post by jbiwer on 2010-04-30
> **eltonw said:**
> Check and see if you have CUPS (Common UNIX Printing System) installed. Depending on how you did your install, and if you had your printer(s) connected at the time, its possible that it was not installed. You can easily launch Synaptic and search for it.

It was installed, but I **_reinstalled_** it.
That helped!  Now I see the LAN printers from yesterday.
Also, the Add Printer option is available. :)

---

### Post by ted_001 on 2010-05-01
I was unable to print any documents in OpenOffice or Abiword.
The Administration/Printing system in 10.04 appears to be broken.  It did not recognise my HP LaserJet 1200 which was plugged into a USB port and switched on during installation.  The Administration/Printing control panel did not do anything, it neither saw the printer, nor was the Add Printer option functioning.
I did whant jbiwer did.  I went to Synaptic Package Manager, searched for CUPS, went through all the green boxes (except OpenOffice), and chose to 'Reinstall'.  After this the printer showed up straight away, without me have to add it.
Also, the way that Abiword installed it would not recognise any fonts not in the default /usr/share/fonts/truetype /usr/share/fonts/type1 directories.  Fonts copied to other directories under /usr/share/fonts were not recognised, even though the font cache had been rebuilt.  The fonts were recognised by OpenOffice though, so it may be something to do with Abiword.
Ted Mason

---

### Post by ratcheer on 2010-05-01
I had the exact same problem as most of you, above. I solved it by simply running: sudo service cups start. Then, it let me add a printer, install the driver, and print to it. The printer I used is connected to a Windows XP host on my LAN, and that caused no trouble, at all.

Tim

---

### Post by Tteddo on 2010-05-02
Reinstalling CUPS worked for me. I didn't have either printer hooked up for the install. Once I reinstalled CUPS they magically appeared.

---

### Post by flipper9 on 2010-05-04
Epic fail.  Forcing users to run terminal commands to do basic stuff like printing?  Newbies will be so lost, and this is a LTS release!  This should be marked as a critical bug and fixed ASAP.

---

### Post by jbrice on 2010-05-13
Glad to hear I'm not the only one affected by this. Similar problem here on a clean Lucid install on my desktop machine. After a restart there seems to be a 50:50 chance of all printers (one local and two network) disappearing. 

Running "sudo service cups start" restores everything to normal until the next reboot - when printing may or may not work. :(

---

### Post by Tteddo on 2010-05-13
Maybe as a workaround put "service cups start &&" in your /etc/rc.local until it gets fixed?

---

### Post by jbrice on 2010-05-15
> Maybe as a workaround put "service cups start &&" in your /etc/rc.local until it gets fixed? 

Thanks - good idea. 

Hmm, what's the purpose of the "&&" at the end of the command? It looks like a boolean without a second argument?

---

### Post by Tteddo on 2010-05-15
> **jbrice said:**
> Thanks - good idea. 

Hmm, what's the purpose of the "&&" at the end of the command? It looks like a boolean without a second argument?

In that file (or in shell scripts? I don't know the proper terminology..) it runs the command and doesn't wait for it. For instance, the reason I know about it is I have the following in mine:
> mount -t cifs //Phaedrus/www /var/www -o rw,uid=tteddo,username=tteddo,password=xxxxxx &&
to mount a windows share on another machine. If that machine is not on, the boot process would stop and wait forever. One of those things I learned the hard way at some point in the past. fstab doesn't work that way to allow that, that is why I don't mount it in there.

---

### Post by jbrice on 2010-05-16
> In that file (or in shell scripts? I don't know the proper terminology..) it runs the command and doesn't wait for it. 

Thanks - I'm slowly learning this stuff.

---

### Post by Tteddo on 2010-05-16
One of the biggest things is keep notes. A lot of what you do is something you might only do once a year and you'll forget. I learned that the hard way also on my 2nd MythTV install!

---

### Post by jbrice on 2010-05-22
Hmm, this bug seems to affect more than just CUPS. The VirtualBox kernel driver is also failing to load reliably - and I'm not the only one seeing this, e.g. [http://www.virtualbox.org/ticket/5877]("http://http://www.virtualbox.org/ticket/5877")

Just as well that Lucid boots fast as I'm frequently having to reboot it on startup just to get everything working. I wonder if I am seeing the tip of an iceberg of start-up script issues? :(

---

### Post by Tteddo on 2010-05-22
> **jbrice said:**
> Hmm, this bug seems to affect more than just CUPS. The VirtualBox kernel driver is also failing to load reliably - and I'm not the only one seeing this, e.g. [http://www.virtualbox.org/ticket/5877]("http://http://www.virtualbox.org/ticket/5877")

Just as well that Lucid boots fast as I'm frequently having to reboot it on startup just to get everything working. I wonder if I am seeing the tip of an iceberg of start-up script issues? :(

I am running Virtualbox also, but it runs fine? Did you see this link on the page you linked to.
[https://bugs.launchpad.net/ubuntu/+source/upstart/+bug/500520]("https://bugs.launchpad.net/ubuntu/+source/upstart/+bug/500520")? Although I wonder why I am not having a problem.

Edit: Well, that's odd the link loads from the email but not when I clicked it on the forum.

---

### Post by jbrice on 2010-05-23
> I am running Virtualbox also, but it runs fine? Did you see this link on the page you linked to.
[https://bugs.launchpad.net/ubuntu/+s...rt/+bug/500520?](https://bugs.launchpad.net/ubuntu/+s...rt/+bug/500520?) Although I wonder why I am not having a problem.

I do not understand the mechanics of Ubuntu startup at all, but wonder if it's some sort of race condition. The affected PC sometimes starts up OK, sometimes not, and I have no problem with CUPS on other Ubuntu installations - even on other dual-processor hardware.

Just hope someone gets a fix together for this soon as it spoils what is otherwise a great OS.

---

### Post by jbrice on 2010-05-25
I'm finding that this is a worse problem than I thought. Not only are CUPS and the VirtualBox driver failing to load, but when this happens there are no sound devices either (PulseAudio failing to load?). 

Is anyone else seeing anything similar? I wonder if I need to do a complete re-install or whether a fix for this is in the pipeline?

---

### Post by Tteddo on 2010-05-25
Did you install from scratch, or do an upgrade? Sounds like there might be some permission/timing problems. Every time I have tried to upgrade, while it works, I always end up with some weird things that are from previous configurations. Like one time the new logout section was gone from that panel, or it keeping grub1 instead of using grub2. This time I just saved out my home folder and then put it back when I was done.

---

### Post by jbrice on 2010-05-25
> Did you install from scratch, or do an upgrade? Sounds like there might be some permission/timing problems. Every time I have tried to upgrade, while it works, I always end up with some weird things that are from previous configurations. Like one time the new logout section was gone from that panel, or it keeping grub1 instead of using grub2. This time I just saved out my home folder and then put it back when I was done.

It's a clean install - done using the release candidate version of Lucid. It seemed to be working fine until some updates a few weeks ago.

---

### Post by Tteddo on 2010-05-25
I only know about the startup process in a vague way. I think the next step would be picking one of your problems (like CUPS) and check the logs after rebooting to see when it gets hung up. Looks like they really improved the Log File Viewer.

---

### Post by Tteddo on 2010-06-08
Ok, after the updates yesterday, now my cups isn't starting with the computer and I have to start it manually. Anyone have any luck with that?

---

### Post by Tteddo on 2010-06-09
For anyone with the disappearing printers problem, this post fixed it for me:
[http://ubuntuforums.org/showpost.php?p=9213567&postcount=7]("http://ubuntuforums.org/showpost.php?p=9213567&postcount=7")
Here's the whole thread:
[http://ubuntuforums.org/showthread.php?p=9213567]("http://ubuntuforums.org/showthread.php?p=9213567")

---

### Post by whiteman on 2010-12-12
I am intrigued by the idea of REINSTALLING Cups. I hadnt tried that. I have a dlink router and my Ubuntu desktop kinda runs everything. I have several wireless laptops...and a win7 desktop(hardwired)
I have tried to upgrade several times. EACH TIME MY PRINTERS DISAPPEARED. Once my Canon mp470 showed as a drive?
The only drivers that show up are HP. I have always kept printers connected.
I have tried upgrading to Karmic and then upgrading to Lynx..in one session. NOTHING. Also lose my sound when I upgrade. Then there is the odd password thing? When I upgrade and enter usrname..it wont accept my password, unless I try the safemode thing. Then I have to logout to dif user. Then it takes my password. Go figure.
Sooooo I tried a clean install. Formatted HD. Used a disk I got in mail for Karmic. Same thing. Odd logons, no sound...NO PRINTERS. 
My wife works for an important Credit card agency writing firewalls. She doesnt have much patience with my experimenting. But I wanna use Handbrake!?>&^%$??
Not possible with Jaunty anymore. Were it not for updating problems I would stay with Jaunty. EVERYTHING WORKS WUNNERFUL WITH JAUNTY. Upgrades should make stuffbetter. I never had this problem before. I have been Ubuntu user since two upgrades before Jaunty. They went flawlessly. Never a htich. Just used the upgrading thing.
Anyone else had this?
The one thing I notice is that CUPS version changes from yellow page to white page when ya upgrade to LLynx. Knowhatimean?

---

