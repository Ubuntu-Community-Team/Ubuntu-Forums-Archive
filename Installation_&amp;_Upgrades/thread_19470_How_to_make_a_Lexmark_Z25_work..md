---
title: "How to make a Lexmark Z25 work."
date: 2005-03-12
forum: Installation &amp; Upgrades
---

### Post by Ulongu on 2005-03-12
I need a step by step how-to.  The whole driver business is driving me bonkers.

---

### Post by IceAxe18 on 2005-03-12
I checked to see if theres a Lexmark Z25 & I don't see one.

1. Click on System
2. Hilight Administration
3. Click on Printing
4. Double Click on New Printer

Then you can select your printer, but like I said I don't see it.  Im sure some one will be able to help you find a way to use your Lexmark Z25.

---

### Post by bored2k on 2005-03-12
[QUOTE=IceAxe18]I checked to see if theres a Lexmark Z25 & I don't see one.

1. Click on System
2. Hilight Administration
3. Click on Printing
4. Double Click on New Printer

Then you can select your printer, but like I said I don't see it.  Im sure some one will be able to help you find a way to use your Lexmark Z25.[/QUOTE]
 [http://ubuntuforums.org/showthread.php?t=19471](http://ubuntuforums.org/showthread.php?t=19471) Z51 worked on this person. Weird that one doesnt.

---

### Post by Ulongu on 2005-03-12
Yes, the Z25 (or the Z35) is not on Ubuntu's list.  When I go to Lexmark and download their drivers and try to unzip, tar, and run them I end up stuck in an error or dependancy problem.

---

### Post by Swab on 2005-04-04
OK, this was adapted from a howto on the Xandros boards, I've tested it and was able to get my Z25 working in Ubuntu.

First of all, lets make sure the printer is plugged in and all connections are good.

Now, open up a Root terminal and download the driver from: 

[http://downloads.lexmark.com/cgi-perl/downloads.cgi?ccs=229:1:0:337:0:0&emeaframe=&fileID=1242](http://downloads.lexmark.com/cgi-perl/downloads.cgi?ccs=229:1:0:337:0:0&emeaframe=&fileID=1242) 

Make a directory and put the Lexmark driver in it... Let's assume we named it LEX, and that folder is sitting in /root OK? (in all of the commands, you do not type the # key, this is just to signify the prompt) 

OK, so we have moved the driver into the folder now, and we will go into the folder by opening a command prompt and typing: 

# cd /root/LEX 

We will now extract the archive by typing the following command: 

# tar -xzvf CJLZ35LE-CUPS-2.0-1.TAR.GZ 

This now leaves us with a shell script rpm installer called lexmarkz35-CUPS-2.0-1.gz.sh... not very useful to a Debian distribution like Ubuntu, so now comes the fun part...We will make another directory now, and extract the files into it... 

# mkdir lextemp 

# tail -n +143 lexmarkz35-CUPS-2.0-1.gz.sh | gzip -cd | tar xvf - -C lextemp 

Now we will enter the lextemp directory and convert the rpm files, since Ubuntu does not use rpms. 

# cd lextemp 

# alien -t *.rpm 


Next, we will use the tar command to extract the files to their proper place. 

# tar -zxf lexmarkz35-CUPS-2.0.tgz -C / 

# tar -zxf z35llpddk-2.0.tgz -C / 

Now for some editing... type the following commands in the order shown below.. 

# cd /usr/local/z35llpddk/utility 

# ln -s auckUS.lut bnsi1.lut 

# cd /usr/lib 

# ln -s liblexz35core.so.0.0.0 liblexz35core.so.0 

# ln -s liblexz35printer.so.0.0.0 liblexz35printer.so.0 

# ln -s liblexz35printjob.so.0.0.0 liblexz35printjob.so.0 

Now to test and see if the driver is working... 

# /usr/lib/cups/backend/z35 

Output should not error out, and give an output similar to this... 

direct z35:/dev/usb/lp0 "Lexmark Inkjet color printer" "Lexmark Printer" 

OK, if all is well, we align the print heads by typing; 

# /usr/lib/cups/backend/z35 utilities 

Follow the on screen instructions to align the heads.

Finally, we click System > Administration > Printing.  Double-click on New Printer.  We should have the option to select Lexmark Z25-Z35 then click forward.   Now lets choose the Z35 v 2.0-1 driver and click apply.  And you're done...  You should now be able to print!

---

### Post by JayDB on 2005-04-16
Thanks for the info.

I followed all of the instructions but when I reached...
> Finally, we click System > Administration > Printing. Double-click on New Printer. We should have the option to select Lexmark Z25-Z35 then click forward. Now lets choose the Z35 v 2.0-1 driver and click apply. And you're done... You should now be able to print!the printer did not show up in any list. I have the file /usr/lib/cups/backend/z35 and I ran the alignment utility. Am I maybe missing a step?

---

### Post by eudemon on 2005-04-18
[QUOTE=JayDB]Thanks for the info.

I followed all of the instructions but when I reached...
the printer did not show up in any list. I have the file /usr/lib/cups/backend/z35 and I ran the alignment utility. Am I maybe missing a step?[/QUOTE]

I had the same problem

DISCLAIMER
I am new at Linux, and this is a quick and dirty solution, and almost certainly not the best way to do this.  Unless your need to print is very urgent, like mine was, I suggest getting advice from someone else before following these instructions.  It did work for me, but I take no responsibilty if your system blows up, etc. :)  You've been warned.
/DISCLAIMER

Here's what I did:

1.  Find the z35 driver you just put on your system.  Should be here:  /usr/share/cups/model/Lexmark-Z35-lxz35cj-cups.ppd.gz

2.  Copy the file to the same directory as all the other printer drivers that came with Ubuntu:

# cp /usr/share/cups/model/Lexmark-Z35-lxz35cj-cups.ppd.gz /usr/share/cups/model/foomatic-ppds/Lexmark/

3.  Now here's the reason for the disclaimer above:  you're going to overwrite one of the lexmark drivers that came with your system.  I chose to overwrite the Z32 driver.  First make a backup of the file you're going to overwrite:

# cp /usr/share/cups/model/foomatic-ppds/Lexmark/Lexmark-Z22-lxm3200-tweaked.ppd.gz /usr/share/cups/model/foomatic-ppds/Lexmark/Lexmark-Z22-lxm3200-tweaked.ppd.gz-backup

Next overwrite the old driver with the new one:

# cp /usr/share/cups/model/foomatic-ppds/Lexmark/Lexmark-Z35-lxz35cj-cups.ppd.gz /usr/share/cups/model/foomatic-ppds/Lexmark/Lexmark-Z22-lxm3200-tweaked.ppd.gz

4.  Now leave the terminal and go to your gnome menu:  System -> Administration -> Printing.  Setup a new printer.  Choose "Lexmark Z25-Z35".  Say it is a Z22 printer and select the lxm3200-tweaked driver (which is actually our new driver), and apply.

5.  Now to be sure your printer is working, double click the newly created Z22 icon, and from that menu select Printer -> Print Test Page.  If the page prints then congratulations, you're done!  :)

---

### Post by Efwis on 2005-05-06
i just installed ubuntu, I'm wondering has this already been pre-installed as the z22  lxm3200-tweaked driver?

if so it doesn't work on my system. I have the z25 also, and the z22 printer at least makes my printer do something, but nothing actually gets printed, its just a blank page.

If that driver still needs to be tweaked just let me know so I can do it.

---

### Post by Efwis on 2005-05-06
just an update, I can't get root priviledges to allow the download to go into the /root/LEX directory wiht Hoary Hedghog Ubuntu

---

### Post by Efwis on 2005-06-05
now that I finally got a chance to get around to it, the printer worked fine wihtout having to do the instructions by eudemon.

just have to make sure that you click on the box, where the driver usually is listed at the bottom of the screen and choose standard, before hitting apply

---

