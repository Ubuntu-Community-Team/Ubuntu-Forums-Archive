---
title: "inspiron internet problem"
date: 2010-08-15
forum: Installation &amp; Upgrades
---

### Post by skkmaths on 2010-08-15
i installed ubuntu 10.04 in inspiron n4010 laptop. No internet connection is detecting. i have both wifi and wired network. in the desktop panel icon of network it shows networking is disabled ..

please help me to resolve this problem...thanks in advance....

---

### Post by xircon on 2010-08-15
What does:
```
cat /var/lib/NetworkManager/NetworkManager.state
```
return (run in a terminal)?

---

### Post by skkmaths on 2010-08-15
i run the command in the terminal and i get the following out put 
[main]
networkingenabled=flase
wireless enabled=true
wwan enabled=true

i dont know  how to proceed further ....no internet is detected in my system ...please reply me ...

---

### Post by xircon on 2010-08-15
OK edit the file and change the false to true:

```
sudo gedit /var/lib/NetworkManager/NetworkManager.state
```

Save and reboot.  

Did you suspend to ram and it failed? (Thats what I did!).

---

### Post by skkmaths on 2010-08-15
i have edited the file and reboot,, but still it showing no network connection in the desktop panel icon.

please help me i am waiting here

---

### Post by xircon on 2010-08-15
Run the first command again (cat /var/lib/NetworkManager/NetworkManager.state) - what does it say?

---

### Post by skkmaths on 2010-08-15
this output i got . and reboot. still it does not work...

[main]
networkingenabled=true
wireless enabled=true
wwan enabled=true

what i do next?

---

### Post by xircon on 2010-08-15
Some questions:

Does it still say networking disabled in the tray icon?

Can you connect via a cable to your router? 

Does your machine have the DW1501 half height wireless card?  The drivers on the CD do not work for this card, you will need to connect via an ethernet cable and update to get the new broadcom-sta drivers.

To see if you have this card run lscpi from a terminal and look for a line like:

```
12:00.0 Network controller: Broadcom Corporation Device 4727 (rev 01)
```

---

### Post by paul.drover on 2010-08-16
I installed 10.04 on an Inspiron 152x last night. Went well, though when I rebooted as per the installation instructions, there was a brief message complaining about the built-in wireless. Went by too fast to see any details.

Sure enough, no wireless capabilities...

Next, I plugged it into my router to see what would happen, and immediately the internet became available. While I was browsing to try to figure out how to get the wireless working, the OS spontaneously popped up a message indicating that there was a proprietary driver available that was needed to make the wireless work. Cool! I accepted the update, rebooted, and, voila, wireless.

So. 
1. Try examining the boot logs to see if there are any indications as to the reason the wireless may not be working.
2. Hard connect to a router for a bit.
3. If available, install 3rd party drivers.

Hope this helps.
Paul.

---

### Post by mike909 on 2010-08-30
For n4010 follow my post here:
[http://ubuntuforums.org/showthread.php?t=1505697&page=9](http://ubuntuforums.org/showthread.php?t=1505697&page=9)

What I can't figure out is the headphone jack.

---

