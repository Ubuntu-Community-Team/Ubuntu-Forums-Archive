---
title: "Printer Driver Fuji Xerox C1110"
date: 2010-09-20
forum: Installation &amp; Upgrades
---

### Post by rayle on 2010-09-20
Hello Ubuntu Forums, long time no see.

I'm trying to install our work networked printer on my new 10.04.1 x64 ubuntu install. It is a Fuji Xerox DocuPrint C1110. I have tried downloading the appropriate linux driver and using alien to convert it from rpm to deb, to no avail. Currently, i'm using a Generic PCL6 driver pxlcolor, but it only prints grayscale. Any ideas?

---

### Post by rayle on 2010-09-20
Just an update, I may not need the driver. Turns out I had it set to grayscale in Printer settings, and i've changed it to color and it's printing fine.

---

### Post by suomaf on 2010-10-13
I just got this printer and I am running it through the network. Which driver did you use in generic? I could not find the pxlcolor

Thanks

---

### Post by suomaf on 2010-10-13
Found it through google.. thanks for the info.. got the printer working

---

### Post by koshari on 2011-07-16
attached is a copy of the generic.ppd file (renamed for reference purposes as fuji-c1110.txt and saved as a text file)

download and rename as fuji-c1110.ppd

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=197590&stc=1&d=1310800863[/IMG]

---

### Post by koshari on 2012-07-17
Download the attached archive with 4 files in it, 

Open it with Archive Manager.


    As root, copy the 3 files, pdftopjlfx, pstopdffx and pstopdffx inti /usr/lib/cups/filter/ dir

In  Add Printer dialog, select "Network printer" then "LDP", and type the printer's IP address.
    It looks for a driver but can't find it, so you are presented with a large list of manufacturers.
    Above this list, click the PPD addition button.
    Select the fxlinuxprint.ppd you have copied from the archive.

enjoy, 

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=221381&stc=1&d=1342518515[/IMG]

---

### Post by Elfy on 2012-07-17
Deleted out of date post and closed thread - old threads are rarely useful.

If the information is useful - the place for it is on the community wiki, help is available, if necessary, to accomplish that. 

[http://ubuntuforums.org/showpost.php?p=11802464&postcount=1](http://ubuntuforums.org/showpost.php?p=11802464&postcount=1)

---

