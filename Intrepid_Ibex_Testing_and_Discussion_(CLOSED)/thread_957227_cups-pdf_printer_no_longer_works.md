---
title: "cups-pdf printer no longer works"
date: 2008-10-24
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by pelikan555 on 2008-10-24
Hello,
I am using the Intrepid Beta with all the latest updates. One of my most used tools in Ubuntu is the PDF printer (not 'Print to file', but the separate printer). I installed cups-pdf, as it doesn't seem to be installed by default.

The problem is, nothing happens when I print from any application nor indeed when I push the 'Print Test Page' button - that is, nothing appears in my ~/PDF folder, and when I look at the print queue it seems the PDF printer jobs were 'cancelled'.

I don't know what further information I should provide, other that that when I push the 'Print Test Page' button a message appears under 'Printer State' on the printer panel saying 'No %%Pages: comment in header!'.

Any help would be very much appreciated!

---

### Post by ntetreau on 2008-10-24
I know this is not going to help much, but I just thought I'd let you know cups-pdf works without problem on my system.  So it doesn't seem to be a generally broken cups-pdf.

---

### Post by shane19174 on 2008-10-24
I only know that cups-pdf was removed when I upgraded from Hardy (there's a discussion somewhere in the forum), but after reinstalling it worked fine. Maybe try purging and reinstalling?

---

### Post by bash on 2008-10-24
You might want to check out this thread. From the replies there it seemed that a workable solution has been found.

Link: [http://ubuntuforums.org/showthread.php?t=947960](http://ubuntuforums.org/showthread.php?t=947960)

---

### Post by shane19174 on 2008-10-24
Yeah, that was the thread I was thinking of too, but does it offer a solution other than reinstalling a missing cups-pdf? If I understand correctly, the problem here this time is that cups-pdf is installed but apparently not working.

---

### Post by bash on 2008-10-24
Well for me the "Print to file" option and selecting PDF as output works without any problems. 

Just saw you posted in the other thread as well. Sorry to hear you don't seem to have as much luck with that option than I do.

---

### Post by kaibob on 2008-10-29
The print-to-file option does not meet my needs, so I installed cups-pdf. By default, the PDF files are supposed to be saved to ~/PDF, but that didn't work for me (don't know why as it seems to work for others). I wanted to change the default save directory to something else anyways, so I followed the procedure detailed in post 12 of the following thread:

[http://ubuntuforums.org/showthread.php?t=626718&page=2](http://ubuntuforums.org/showthread.php?t=626718&page=2)

Basically what you do is:

1) Install cups-pdf with synaptic.

2) Change the default directory in cups-pdf.conf.

3) Change the usr.sbin.cupsd file.

4) Restart everything. 

After making the above changes cups-pdf began working fine. The primary reason for doing this is to change the default directory, but it may be worth a try for those experiencing problems after installing cups-pdf.

---

### Post by mdurham on 2008-10-29
Hi guys, my print to PDF has never worked in this 8.10 or any prev Ubuntu.
It seems like it's working but never produces a file.
Here is part of dmesg that maybe someone might be kind enough to decipher for me. What does it all mean?
Cheers, Mike

I should add that I'm talking about cups-pdf, it does work if I print to PDF file.

> [20467.494957] type=1505 audit(1225269808.728:21): operation="profile_replace" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=9638
[20467.496384] type=1505 audit(1225269808.728:22): operation="profile_replace" name="/usr/sbin/cupsd" name2="default" pid=9638
[20610.045725] type=1503 audit(1225269951.280:23): operation="capable" name="dac_override" pid=9688 profile="/usr/lib/cups/backend/cups-pdf"
[20610.045740] type=1503 audit(1225269951.280:24): operation="capable" name="dac_read_search" pid=9688 profile="/usr/lib/cups/backend/cups-pdf"
[20845.073993] type=1503 audit(1225270186.308:25): operation="capable" name="dac_override" pid=9811 profile="/usr/lib/cups/backend/cups-pdf"
[20845.074011] type=1503 audit(1225270186.308:26): operation="capable" name="dac_read_search" pid=9811 profile="/usr/lib/cups/backend/cups-pdf"
[21299.112162] type=1503 audit(1225270640.348:27): operation="capable" name="dac_override" pid=10105 profile="/usr/lib/cups/backend/cups-pdf"
[21299.112181] type=1503 audit(1225270640.348:28): operation="capable" name="dac_read_search" pid=10105 profile="/usr/lib/cups/backend/cups-pdf"
[28966.745904] type=1503 audit(1225278307.980:29): operation="capable" name="dac_override" pid=10443 profile="/usr/lib/cups/backend/cups-pdf"
[28966.745941] type=1503 audit(1225278307.980:30): operation="capable" name="dac_read_search" pid=10443 profile="/usr/lib/cups/backend/cups-pdf"

---

### Post by _sAm_ on 2008-10-29
Just want to say that installing cups-pdf made it work at my system(it was missing).

---

