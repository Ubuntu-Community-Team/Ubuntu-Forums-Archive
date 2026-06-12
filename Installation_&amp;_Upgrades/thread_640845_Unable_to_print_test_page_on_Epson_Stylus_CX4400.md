---
title: "Unable to print test page on Epson Stylus CX4400"
date: 2007-12-14
forum: Installation &amp; Upgrades
---

### Post by gsv on 2007-12-14
Hello All,

I have been searching on forums an trying to setup Epson Stylus CX4400 on Ubuntu 7.10, which I installed recently (Thanks to Microsoft that my Windows XP crashed and could not be recovered). 

Ubuntu is able to seacrh my printer but not able to print test page. Its amazing that I am able to scan using iscan application but printer does not work.

Any help is higly appreciated.


Thanks in advance,
GSV

---

### Post by stanley82 on 2007-12-14
First use this interface.  [http://localhost:631/jobs/](http://localhost:631/jobs/)  it uses firefox

Next administration then add printer (avoid find printer)

enter some words to suite NEXT

drop down menu select LPT #1

IMPORTANT USE LPT #1 *** DO NOT USE EPSON //EL PORT OR YOU *****

after that it should be easy to follow your nose.  Enjoy Ian.

---

### Post by gsv on 2007-12-15
First of all, thank you very much stanley82 for reply. 

I followed these instruction and reached till I found the dropdown to select the Device but unfortunately did not find LPT#1 or anything close to LPT.

These are the options available for me:
AppSocket/HP JetDirec
Backend Error Handler
Hal printing backend
HP Fax (HPLIP)
HP Printer (HPLIP)
Internet Printing Protocol (http)
Internet Printing Protocol (ipp)
LPD/LPR Host or Printer
Print into PDF file (Generic PDF file generator)
SCSI Printer
Windows Printer via SAMBA

I tried "LPD/LPR Host or Printer" and "SCSI Printer". I asks for Device URI, which I do not have any idea about.

Am I missing any driver or anything?

Thanks,

GSV

---

### Post by gsv on 2007-12-15
By the way, when I go to Printers TAB, it shows the printer but does not print test page. Here are details it shows:

Description:
Location: GSV-desktop
Printer Driver: EPSON Stylus CX4450, Photo Image Print System
Printer State: stopped, accepting jobs, published.
Device URI: usb://EPSON/Stylus%20CX4400

The printer is CX4400 but the driver is CX4450, I think I got this while installing iscan driver, which works fine for scanning.

---

### Post by stanley82 on 2007-12-15
1  I guess you have cups
2  You need guttenprint
3  1  I think that your printer is jammed with a print job.  Even printer off on and reboot I had difficulties in Feisty.

   What to do.  [http://linuxgazette.net/130/tag.html](http://linuxgazette.net/130/tag.html) was lots of help.  Ben tends to be a bit sharp with my dumb questions.

head -60 /usr/share/dict/words > /dev/lp0 should sort it out only you may not be on the list allowed to do that.

1) Permissions

    ben@Fenrir:~$ ls -l /dev/lp0 
    crw-rw---- 1 root lp 6, 0 2004-04-28 23:43 /dev/lp0
        think I was okay there
At some point I edited a file and added myself to the group who access lp1.  wonder where I got that?  sorry not more help but follow the link I gave you.  good printing Ian.

---

### Post by stanley82 on 2007-12-16
Okay I've found it.  I edited etc/groups and added myself to the line 

sudo gedit etc/groups

disk:x:6:
lp:x:7:cupsys,stanley82  ;this line
mail:x:8:

Use change mode usdo chmod +w +r on dev/lp0 IF
ls -l dev/lp0 tells you that you do not have r/w access

After all that messing the head asc.txt > dev/lp0 printed the file on my stylus 660 but did not eject the paper.  This gets the printer into the neutral position so that you can do what I said in my first post.  If it works it's simpler to off printer then reboot and printer on.

           lots of f*** about not my fault.

---

### Post by helpdeskdan on 2007-12-16
I did the printer section in:

[http://www.uluga.ubuntuforums.org/showthread.php?t=576594](http://www.uluga.ubuntuforums.org/showthread.php?t=576594)

For some reason, test prints from cups don't work, so don't try.  Also, when mine is in energy saving mode (flashing light) and I send it a job, the stupid thing turns off.  Does anybody else have this problem?  Also, my ink light is flashing though I have only printed a few sheets with a total amount of less than a paragraph of black text.  Maybe I have a lemon.

---

### Post by stanley82 on 2007-12-16
Do not change the ink cartridge, I did and the new one was even worse as the cartridge was one of those cheap ones.  I put the original back.

     My problem with an epson stylus 660 was that I would try to print with a bad set up.  In this condition the cups set up would not give the correct sequence.  I think the printer is stuck in the middle of a job, HW, SW or queue who knows.  You must must must get the thing back into the starting state.  Try printer off, reboot, then printer on then look at my first post.  Even more detailed stuff in my following posts all to do with getting into and being sure that you are at the starting line.

    Once there go into the cups in firefox [http://localhost:631/jobs/](http://localhost:631/jobs/) then administration tab then add printer tab type in your favourite words then NEXT then YOU SHOULD GET THE PULL DOWN MENU AND SELECT LPT #1.  If it's not there goodness knows but I suspect that you were not at the starting point.  Oh yes I assume that you have cups and gutenprint installed and you are using a parallel port.

---

### Post by helpdeskdan on 2007-12-17
No offense Stan, but what are you talking about?  The CX4400 is a usb printer.  What's this talk of the epson 660?  

I printed one more page (just one) and now it is out of ink.  I am so mad at this printer I could throw it out the window.  Not for the price, it was essentially free after rebate, but rather, it took me a while to get working under Linux.  

A forewarning to other users - DO NOT BUY THIS PRINTER!  If you bought it, DON'T TRY TO GET IT TO WORK IN LINUX!  It's not worth the time, go, RUN back to where you bought and return it now!!

---

### Post by stanley82 on 2007-12-18
Sorry, did not realize that.  I guess I should have said that before I started.  Try asking the guys at the article I quoted in one of the previous posts.  Linux gazette I think it was.  They seem to know there stuff but can be as vexing as me in there assumptions.

---

### Post by donald_ud on 2008-01-17
I got it working by installing the latest cups and gutenprint from source and uninstalling the default one in ubuntu. The latest gutenprint includes the cx4400 ppd. The version installed in gutsy by default does not.

---

