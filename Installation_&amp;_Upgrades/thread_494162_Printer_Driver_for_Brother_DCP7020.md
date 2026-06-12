---
title: "Printer Driver for Brother DCP7020"
date: 2007-07-06
forum: Installation &amp; Upgrades
---

### Post by Robert L. Neale on 2007-07-06
I have been using Ubuntu for two days!  It found and installed my hp printer, but I just bought a new Brother DCP7020 and can't get it to work.  It works in my XP partition, but not in Ubuntu.  The drivers that come up list a DCP7025 and others, but they won't work.  I went to the Brother website and found drivers but they had CUPS or I think it was LPD or something, but none had the required ppd or ppd.gz and therefore wouldn't work.  What can I do?

---

### Post by linuxwizard on 2007-07-06
This show the recommended driver help this will help

[http://www.openprinting.org/show_printer.cgi?recnum=Brother-DCP-7020](http://www.openprinting.org/show_printer.cgi?recnum=Brother-DCP-7020)

---

### Post by dabl on 2007-07-06
Congratulations -- you've won a learning experience!  :)

Start here:

[http://openprinting.org/show_printer.cgi?recnum=Brother-DCP-7020](http://openprinting.org/show_printer.cgi?recnum=Brother-DCP-7020)

:)

drat you, linuxwizard, you are too fast on the keyboard!

---

### Post by grandmk on 2007-12-27
Here's a little something slightly more helpful...

1) Go to the PPD-o-matic for the Brother HL1250 (which is the laser printer component of the DCP-7020 all-in-one). Here's a direct link: [http://openprinting.org/show_driver.cgi?driver=hl1250&fromprinter=Brother-DCP-7020](http://openprinting.org/show_driver.cgi?driver=hl1250&fromprinter=Brother-DCP-7020)

2) Select "Brother HL1250" from the drop down, choose "download" as your option, and click "Generate PPD File". Save the file somewhere memorable. 

3) In Ubuntu, go to System>Administration>Printing. If you've turned your printer on with the USB plugged in (and it sounds like you have), there will probably already be an entry for the automatically detected DCP-7020, and Ubuntu will have guessed a driver (listed when you see "Make and Model") but it will be for a 7025, not your 7020. 

4) Click the "Change..." button beside "Make and Model" to manually change Ubuntu's guess. A window will pop up. Choose the "Provide PPD File" option. Locate the PPD file you downloaded earlier and click next through the menus. The "Make and Model" should now read something like "Brother HL-1250 Foomatic/hl1250 (recommended)". This is the right printer! 

5) You should be good to go! Depending on your system, it might help to turn the printer off then back on while its still plugged into the USB. You should be able to click "Print Test Page" and it should work. 

REMEMBER: This is just for setting up the printer. Since all-in-ones are really just Frankensteined together out of printers/scanners lying around the manufacturer, you'll have to set up your scanner separately.

---

### Post by aeecee on 2008-02-06
THANK YOU grandmk!!!  I'm the culprit who installed Gutsy on my hubby's comp (toshiba satellite which came with and could NOT handle ick-sta).  He has a college class in an hour and needed to print from his comp from a DCP 7020 and I couldn't figure out what I was doing wrong - your post helped me and I had it working perfectly in less than five minutes.

---

### Post by Beto0707 on 2008-03-16
Your advice really helped me out grandmk.  I just started using Linux about 8 hours ago and already have my printer working, which is shared by my wife's xp machine on the network!

---

### Post by pavlick on 2008-03-20
this is great, i got the printer working thank you
but does anybody have any idea on how we can get the scanner and the scanner button working on gutsy?
thx again

---

### Post by tgale47 on 2008-03-30
Wonderful!  I was having the exact same problem and this gets it working.
Thanks     :)

---

### Post by mahasmb on 2008-05-30
It won't work for me :( . 

Can anyone help me out?

---

### Post by mbrierst on 2008-06-05
Got it working on Slackware thanks to grandmk.  If only everyone on the internet provided useful advice.

---

