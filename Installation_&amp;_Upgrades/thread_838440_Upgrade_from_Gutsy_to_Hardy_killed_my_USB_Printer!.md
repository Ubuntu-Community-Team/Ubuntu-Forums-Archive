---
title: "Upgrade from Gutsy to Hardy killed my USB Printer!"
date: 2008-06-23
forum: Installation &amp; Upgrades
---

### Post by Cotopaxi on 2008-06-23
Hi all.

System: Kubuntu 8.04
Printer: Brother MFC-5440CN connected via USB.

I was working under Gutsy and I was in heaven with it! I was proposed an upgrade to Hardy, which I accepted, and everything went fine.

But, after a few system updates, I could not print anymore!

The printer is recognized by the printer manager, but when I want to print a test page nothing happens. When I go to &#8220;System Settings&#8221; - &#8220;Printers&#8221; and choose &#8220;Add Printer/Class&#8221;, the &#8220;Add Printer Wizard&#8221; comes up and, on the second screen, the clickable option &#8221;Local printer (parallel, serial, USB)&#8221; is just whitened out, so I can't choose it.

I have been reading around in the forums, I do not seem to be the first person, who has this problem, but nobody managed to find a solution. I other threads I read that it is a kernel problem, which is not just a Ubuntu/kubuntu problem, but also a Debian problem.
Some people managed to solve the problem, installing an older kernel, but I don't dare to do that (and I don't know how to do it).

So now two questions:

1)What can I do on the printer side to track the problem?
2)What can I do on the USB side to track the problem?

Sorry I am opening an new thread for this problem, but I really have read everything I could about this problem, I have followed all the recommendations, listed in other threads, with no results. It is now the third week that I am unable to print and it is critical.

Thanks for your help.

---

### Post by avtolle on 2008-06-23
I don't know what you have read and tried, so it you have already done this, I apologize. Remove the printer from the system totally. Turn off the printer and computer. Power the printer up and then the computer. Go to Synaptic and find the correct Brother cups driver for your printer. Install the drivers. Then, add printer and go through the steps in the Wizard. HTH.

EDIT: By remove, I mean to remove it as a printer on your system in the printer window, so the only printer that shows up is "Print to PDF" under local printers. Also, once added back, with the drivers, etc., installed, restart your computer with the printer plugged in to the USB port and powered up. 

Another thing to check: the USB cable you are using itself. If you have another cable handy, you might want to try it. Further, if there is another USB port into which you can plug your printer into and check it.

---

### Post by Cotopaxi on 2008-06-24
Hi avtolle.

First of all, thanks very much indeed for your attempt to help and sorry for my late reply.

Following the deinstallation and reinstallation  according to your description produced the following results:

1)The printer is only recognized as a &#8220;text only printer&#8221;;
2)Now, instead of sending a document to the print manager and staying there, without getting printed, the system reports: &#8220;Error while printing&#8221;;
3)When I try &#8220;System Settings&#8221; - &#8220;Printers&#8221; and choose &#8220;Add Printer/Class&#8221;, I still can't choose the clickable option: &#8220;Local printer (parallel, serial, USB).

Again, thank you very much for your help!

---

