---
title: "CUPS and Printing"
date: 2010-06-10
forum: Installation &amp; Upgrades
---

### Post by ted_001 on 2010-06-10
Dear Forum,
since I installed Ubuntu 10.4 I am having a lot of trouble with CUPS.  When I start the machine it does not recognise my HP LaserJet 1200.  In fact I don't think that the cups demon actually starts at all.  I can't add the printer in /System/Administration/Printing, and trying 

'sudo /etc/init.d/cupsys restart'

gives 

'sudo: /etc/init.d/cupsys: command not found'

However

'sudo /etc/init.d/cups restart'

does restart CUPS, and my printer appears in /System/Administration/Printing.  Is there any way that I can modify the way Ubuntu boots so that it automatically starts CUPS, without my having to do it manually each time?
Regards,
Ted Mason

---

### Post by Morbius1 on 2010-06-10
This seems to work: [http://ubuntuforums.org/showpost.php?p=9405854&postcount=4](http://ubuntuforums.org/showpost.php?p=9405854&postcount=4)

---

### Post by ted_001 on 2010-06-10
Many thanks,
Ted

---

### Post by Morbius1 on 2010-06-10
You're very welcome. It's crazy though , don't you think?

As that great engineer once said: "The more complicated the plumbing, the easier it is to plug up the pipes"

---

### Post by iraparks on 2010-06-14
this is my first install and experience with Linux, using Ubuntu latest version, i've installed the printer but cant get my Windows Seven wireless laptop through linksys e2000 router, to find the printer on the Linux box which has the printer connected via USB and selected to allow share of the printer, Any suggestions?

While I have someone's attention, how do I adjust the screen resolution and how do I find the correct packages to allow me to share files with other Linux machines and windows 7 machines? Lastlly how about the Java plug-ins so I can run the exercises on the Linux learning site which is Java heavy?

Sorry if this is the wrong way to ask many questions but I just don't understand most of the threads i'm reading to fix these issues on my own.

Thanks in advance

---

