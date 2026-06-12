---
title: "Added ver 6.06,  lost internet"
date: 2006-05-08
forum: Installation &amp; Upgrades
---

### Post by bathhm on 2006-05-08
I have installed Ubuntu ver 5.10, updated/upgraded it,  augmented with Automatix, and updated to 6.06 = Dapper Beta using the procedure in tinyurl.com/FL5CL.  There seemed to be no problems.

But I have lost internet access.  ifconfig says that eth0 is up and running, but that there are Rx packet errors. (none on Tx).  I can successfully ping 127.0.0.1,  the local inet address, and the inet address of a second computer sharing a router.  I cannot ping the router (tho I can from the second, normally behaving computer).  My hardware has not suddenly died:  I can shut down Dapper and reboot with the Live Dapper CD and access internet just fine.  The settings at System --> Administration --> Networking seem OK and consistent with those supplied automatically by a Live-CD boot.  Obvously, the net connection was working just fine during the update to 6.06

What switch do I have to throw?  Help

---

### Post by Dr. Nick on 2006-05-08
fire up a terminal and run 
```
sudo ifdown eth0
sudo ifup eth0
```

This will disable/enable your lan card. Watch on the ifup and see if you get an IP address. It should say "bound to yada yada renewal in ... seconds"

If you aren't getting a ip then your dhcp client is most likely messed up. I had trouble going hoary to breezy in the past and always had to run
```
sudo dhclient eth0
``` to get a IP

---

### Post by bathhm on 2006-05-09
Thanks for the suggestions.

I have tried them  ----   unsuccessfully.   I don't get an inet address after the "ifup" after the "ifdown"  [ "ifdown" *does* disconnect eth0, as shown by ifconfig, and "ifup" reconnects -- in a sense:  the second line under " eth0 ", which normally contains the inet addr, broadcase addr and mask is missing. ]  " dhclient " also doesn't bring up any sort of an address.

I you can provide any other suggestions, I would be delighted to try them out.  But I am about ready to give up and settle for a Live CD install of 6.06 and wait for Automatix to catch up.

Regards,  and tnx agn

---

### Post by Dr. Nick on 2006-05-09
Weird, My last suggestion would be to get all the infomation like ip, subnet, gateway etc and specify a static Ip address in the network tool. I am not sure what would cause that problem

---

### Post by bathhm on 2006-05-09
The last weird clue is that when 6.06 boots and all the " OK 's " go parading up the screen,  there is an OK after the "setting up the net access" or words to that effect.  When boot is complete and ifconfig is run, the line containing inet, broadcast and mask *is present*, and the inet addr is correct -- it is what it always is for this particular computer.  But "sudo apt-get update" hangs.  I would conclude that it is not the browser that is at fault.

Let's declare defeat.   Regards,

---

### Post by Dr. Nick on 2006-05-09
We Lost :(:([-(
Hehe, I guess thats how it goes sometimes with beta software. Sometimes its just not worth fighting something when you know you could be doing other things. You mentioned using the live cd install, I did this yesterday and was stunned how nice it went, Its took 7 easy steps all done from a gui until your in a brand new clean dapper  :)

I came to that point after admitting defeat with a trashed grub, and am glad I did instead of fighting for my old messed up breezy. Dapper+XGL = :cool:

---

