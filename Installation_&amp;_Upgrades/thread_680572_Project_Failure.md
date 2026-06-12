---
title: "Project Failure"
date: 2008-01-28
forum: Installation &amp; Upgrades
---

### Post by cclarkk on 2008-01-28
I'm a Linux newbie and the only experience I have so far is 12 hours of failed attempts at getting Ubuntu to install.  Nothing I have read from any posts or from the documentation seems to work.  The problem may be headspace and timing, i.e. user error, but I know I'm smarter than the average beer.  So what's the trouble?

First off, after readin a few posts about HP notebooks having problems with 7.10, I went with the the 7.04 install.  After all, there's no point in trying to learn a system if I'm gonna have to fight it tooth and nail.  I have a middle-aged HP ze2000 series with one and a quarter gigs of memory, more than enough for the task at hand.  I have already gone through and partitioned my hard drive, allocating 12GB for Ubuntu.  

So, what's the problem?

On startup, the computer bypasses the CD drive and goes right into windows.  Yes, the BIOS is already set to boot from the CD drive.
  
Trying to install with UNetbootin does offer a glimmer of hope, but that soon turns into doom and gloom:
1.   I get the option to choose between Windows and Ubuntu, obviously I select Ubuntu.
2.  Choose a language:  English selected
3.  Choose a country:  United States selected
4.  Configure keyboard:  US keyboard
5.  Detect network hardware: success maybe, no error
6.  Configure network:  eth1-wireless network interface selected as primary
7.  Searching for wireless networks:  failed
8.  Configure network:  wireless ESSID entered
9.  Configure network:  WEP key entered
10.  Configuring network with DHCP:  failed
11.  Configure network manually:  IP address, netmask, gateway, and name server address entered
12.  Configure network:  "Error  An error ocurred and the network configuration process has been aborted.  You may retry it from the installation main menu."
13.  Configure network:  System hostname entered
14.  Choose archive mirror: several countries attempted, all return "Bad archive mirror"  (i'm assuming this is because of all the network failures)

From here, I reconfigure the network for a LAN line, but the exact same errors keep coming up.  From there I can't seem to progress because the option "Download installer components" goes back into that wild goose chase.  The remaining items on the Installation Menu are: 
"Change debconf priority": complete
"Save debug logs: not needed yet"
"Execute a shell": went in, didn't know anyone there, so I left
"Abort installation": completed many times.

So, now you know as much as I do.  I'm stubborn about it for two reasons, 1 - I have already wasted too much time trying to install it, 2-I have been told this was the best to learn on and had the best ease of use, something I have yet to see.  I'm still trying, but obviously I have to draw the line somewhere.

My BIOS doesn't have the option to boot from a USB.  If it ignores the BIOS and skips merrily along past the CD boot, I doubt it will even blink an eye at a flash drive.

Do I need to go to an even older version of Ubuntu?  Why is the installer trying to connect to a mirror when I have the install CD in the CD drive already?  Should I just skip Ubuntu altogether and try Fedora?  Normally, at this point, I would have written off Linux forever, I'm still inclined to, but I have to use it for a CS class, so I'm stuck in this boat for the moment.

Please advise.


EDIT:  it just occurred to me that perhaps 7.04 is not being mirrored so I am attempting to install 7.10 for poops and giggles, however, if it has nothing but problems later, it will obviously have to go.

---

### Post by Partyboi2 on 2008-01-28
Make sure you burn the iso to disk as a iso not data.  Burning at a speed like x4 or less is a good thing. Before you burn the iso to disk make sure that the md5sum matches see [here]("https://help.ubuntu.com/community/HowToMD5SUM")
I hope gusty works for you. :)

---

### Post by cclarkk on 2008-01-29
> **Partyboi2 said:**
> Make sure you burn the iso to disk as a iso not data.  Burning at a speed like x4 or less is a good thing. Before you burn the iso to disk make sure that the md5sum matches see [here]("https://help.ubuntu.com/community/HowToMD5SUM")
I hope gusty works for you. :)

I checked my disks and the not only was the iso burned properly, but the checksums were correct.  I decided to dumb down my efforts and it finally worked.  I downloaded 6.06.1 and burned it with InfraRecorder from the Ubuntu site, and voila.  What the error with that other disks were is beyond me.  I'm going to check them on the another system tomorrow to see if it's this system or simply the disk.  Thanks for the ideas.

---

