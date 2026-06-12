---
title: "how to install canon mf 4320d printer and scanner in ubuntu 12.4 LTS"
date: 2013-06-17
forum: Installation &amp; Upgrades
---

### Post by rohitchaudhary on 2013-06-17
Can you please help me to install canon mf 4320d printer and scanner in ubuntu 12.4 LTS

---

### Post by pdc on 2013-06-17
You don't tell us if you have a 32bit or 64bit install; let us know

__________________________________________________________________

the essence is that you are going to install the Canon UFR driver; 

get it from here

[http://support-asia.canon-asia.com/contents/ASIA/EN/0100270810.html](http://support-asia.canon-asia.com/contents/ASIA/EN/0100270810.html)

and you will download the [COLOR="#008000"]Linux_UFRII_PrinterDriver_V260_uk_EN.tar.gz[/COLOR]

having downloaded to your Downloads directory; if you open that directory and right-click on the file and select [COLOR="#FF0000"]open[/COLOR] with [COLOR="#EE82EE"]Archive Manager or whatever your version of ubuntu offers[/COLOR] (I am using Mint today so its name may be different): 

Navigate to the Debian directory; look for the 32bit or 64bit; whichever is right for you; and install the [COLOR="#0000FF"]COMMON[/COLOR] package first; then the [COLOR="#0000FF"]SPECIFIC[/COLOR] one

(Install by right-click on package; and install with ubuntu software manager)

_________________________________________________________________________________________

Now I recommend you read the instructions!!

Inside the above package; is a folder called Documents: if you EXTRACT that to your desktop; you open it from the Desktop; look inside it for a file called index.html

if you click or double-click or whatever on index.html it should open your web browser and the instructions are all there for you to see: 

_______________________________________________________________________________________________________________-

so step 1) install the drivers is done

________________________________________________

step 2) is register the printer: 

before that, we re-start CUPS > [COLOR="#FF0000"]sudo service cups restart[/COLOR]

***if your setup is: computer with single 4320D attached by USB cable; command should be as below...........***
____________________________________________________________________

let's check what your device is registered as.......

issue the command

> [COLOR="#FF0000"]/usr/sbin/lpinfo -v[/COLOR]

you should seem something like direct [COLOR="#FF8C00"]cnusb:/dev/usb/lp0[/COLOR] and we only want the [COLOR="#0000FF"]cnusb:/dev/usb/lp0[/COLOR] part of this result

to register the printer the command should be

> [COLOR="#FF0000"]sudo /usr/sbin/lpadmin -p MF4320D -m CNCUPSMF4350ZK.ppd -v cnusb:/dev/usb/lp0 -E[/COLOR]

_______________________________________________________________________________________________________________________________

let us know how you get along

---

### Post by rohitchaudhary on 2013-06-18
Hi pdc.......

Thank you very much......

Now it's working fine........

Again thanks..........

---

### Post by rohitchaudhary on 2013-06-18
\\:d/

---

### Post by pdc on 2013-06-19
great! enjoy

---

