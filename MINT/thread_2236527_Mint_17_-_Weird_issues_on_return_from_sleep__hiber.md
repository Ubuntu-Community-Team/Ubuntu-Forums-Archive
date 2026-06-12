---
title: "Mint 17 - Weird issues on return from sleep / hibernate"
date: 2014-07-27
forum: MINT
---

### Post by RallyDarkstrike on 2014-07-27
Hey all - having issues on my Mint 17 netbook. Upon return from sleep or hibernate (and usually the issues are with hibernate), my computer will claim that networking is disabled and WiFi won't reconnect. Right-clicking the networking icon and selecting 'Enable Networking' does nothing. It only fixes itself once I restart. Any suggestions?

To that end, on my older Mint 14 install on this same netbook, I had a similar issue which I solved by adding a command to restart some sort of networking service automatically every time the machine came out of sleep or hibernate and this solved the problem. I THINK the command was
```
sudo service network-manager restart
```
What file would I have to append this to in order to have it happen automatically on return from sleep / hibernate?

My second issue is that sometimes (not always), on return from sleep / hibernate, Numlock on my keyboard begins to randomly flicker for no reason without me touching it, preventing me from logging in as the computer constantly things I am switching Numlock on and off (therefore changing some of my letter keys required for my password into numbers randomly and back). What could be causing this issue and any ideas on how to solve it? I usually end up clicking 'Switch Users', going back out to the login screen and restarting the machine from there to solve this problem...

Any help or ideas are appreciated! :)

---

### Post by bapoumba on 2014-07-27
*Thread moved to **Other OS/Distro Support**.*

---

### Post by varunendra on 2014-07-27
You may try this script -
```
case "${1}" in
    hibernate|suspend)
        # Stop network-manager service
        service network-manager stop
        ;;
    resume|thaw)
        # Start network-manager service
        service network-manager start
        ;;
esac
```
Copy-paste the above code into a text file, and save it as "**nm_restart**" (no dot or extension name) on your Desktop. Now run the following commands to copy it to /etc/pm/sleep.d directory and make it executable -
```
sudo cp Desktop/nm_restart /etc/pm/sleep.d
sudo chmod +x /etc/pm/sleep.d
```
Suspend/resume to make sure it works.

No idea about the keyboard issue.

---

### Post by RallyDarkstrike on 2014-08-07
Sorry for the late reply! I lost this thread link and only just found it! Tried your suggestion and all seems well so far....crossing my fingers! :)

---

### Post by varunendra on 2014-08-08
It's still just 15 hours since your post above, but I hope I can congratulate you now. :p

---

### Post by RallyDarkstrike on 2014-08-08
Well, we will know for sure today, just leaving for work with my netbook now! Fingers crossed! :D

---

