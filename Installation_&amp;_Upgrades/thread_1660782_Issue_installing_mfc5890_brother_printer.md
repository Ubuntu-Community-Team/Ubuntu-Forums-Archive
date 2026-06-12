---
title: "Issue installing mfc5890 brother printer"
date: 2011-01-05
forum: Installation &amp; Upgrades
---

### Post by chrisportela on 2011-01-05
I try to follow the instructions [here]("http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/instruction_prn1a.html#dpkg1") but it fails only saying this
> chrisportela@chrisportela-ThinkPad-T60p:~$ sudo dpkg -i --force-all mfc5890cnlpr-1.1.2.2.i386.deb
[sudo] password for chrisportela: 
dpkg: error processing mfc5890cnlpr-1.1.2.2.i386.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 mfc5890cnlpr-1.1.2.2.i386.deb
chrisportela@chrisportela-ThinkPad-T60p:~$ 
What am I supposed to do? Does anyone have this printer even installed under linux? I can't find drivers anywhere for ubuntu.

---

### Post by wojox on 2011-01-05
First create the directories:

```
sudo mkdir /var/spool/lpd
```


```
sudo mkdir /usr/share/cups/model
```

---

### Post by chrisportela on 2011-01-05
nvm turns out that either downloading the drivers using the links on the page I will link to did the trick or copy and pasting of their commands... It installed will report back if the network setup works or not.

[http://www.question-defense.com/2010/10/01/how-to-set-up-a-brother-mfc-5890cn-printer-on-64bit-ubuntu-linux](http://www.question-defense.com/2010/10/01/how-to-set-up-a-brother-mfc-5890cn-printer-on-64bit-ubuntu-linux)

---

### Post by chrisportela on 2011-01-05
Additionally when they say to use the IP address it's not an option. That is the only way to get the printer to actually print. Using friendly names like 'BROTHER1' do not work and it can not find the printer.

---

### Post by wojox on 2011-01-06
If you go into System > Admin > Printing you should see the printer. Delete that one and add a new one and let it search.

How is the printer connected?

---

### Post by chrisportela on 2011-01-06
> **wojox said:**
> If you go into System > Admin > Printing you should see the printer. Delete that one and add a new one and let it search.

How is the printer connected?
The printer works! I printed two essays I needed to turn in today and they printed well. I would have liked the header color to be lighter but reviewing the .odt file I printed it looked like the very same color so it is merely an option change away. To anyone who has the problem it would be best to follow that website, download the ldp files they list and download the CUPS wrapper from brother by finding it on there(the link leads to instructions not a download link), then copy and pasting(to ensure no sp errors) the commands in to a terminal and it should work perfectly as it finally did for me once I did these things
:p

---

