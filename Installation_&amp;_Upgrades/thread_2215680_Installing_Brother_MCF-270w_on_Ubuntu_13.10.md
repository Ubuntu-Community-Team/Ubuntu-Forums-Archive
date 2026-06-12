---
title: "Installing Brother MCF-270w on Ubuntu 13.10"
date: 2014-04-07
forum: Installation &amp; Upgrades
---

### Post by Sam_Yang on 2014-04-07
hello. i'm new to Ubunto. installed the OS last night but i am having trouble with installing my network printer.

i have the Brother MCF-270w. i have already installed the LPR printer driver and the CUPSwrapper printer driver. the printer is installed but it does not print.

can someone help me with this?

---

### Post by gifford on 2014-04-08
Welcome to the forum Sam.
I normally would direct you to the Brother site where the directions for a network install is. However, Brother has changed their site in the past week or so and getting to where you want to go is not as easy.
Go to the site, find the drivers for your printer and the directions on how to install. [http://support.brother.com/g/b/countrytop.aspx?c=us&lang=en](http://support.brother.com/g/b/countrytop.aspx?c=us&lang=en)
My best recommendation is to follow their instructions using the command line as the examples will show you.
I have been using Brother printer/scanners for years and the installation, though maybe a little complicated, is solid.
There are a few pre-required procedures so read the notes before downloading.

---

### Post by kurt18947 on 2014-04-08
One thing with Brother printer installations is that they seem to install a USB connection unless told otherwise.  I use Ubuntu-Gnome (gnome shell) so I'm not certain which printer app comes in 13.10.  If it's the same one as gnome-shell, it's very limited.  Part of my initial install is to install "system-config-printer" found in the repositories.  I know Mint and Xubuntu use this by default and I think Lubuntu does as well.  Brother printers seem very similar to H.P. printers.  I've had very good luck assigning a static I.O. address to the printer then in the 'system-config-printer' device URI window  I use this:
```

socket://xxx.xxx.xxx.xxx:9100

``` 
where xxx=i.p. address assigned to the printer.  There are a number of network connection choices offered but I've had good luck with this so have stayed with it.  Brother also has available 2 installer scripts that seems to work quite well.  One is 1.0.4-1 which only installs the printer.  2.0.0-1 install both printer and scanner drivers.  There are two bugs 'normal user USB' edit and another bug which requires copying files manually still need to be done after install.

Here is the 'normal USB user' fix:
[http://support.brother.com/g/s/id/linux/en/instruction_scn1c.html?c=us&lang=en&prod=mfcj4510dw_us_eu_as&redirect=on](http://support.brother.com/g/s/id/linux/en/instruction_scn1c.html?c=us&lang=en&prod=mfcj4510dw_us_eu_as&redirect=on)

The installer problem is addressed under this question.  It's the 4th item.

[HR][/HR]**I'm using Ubuntu 11.10 or higher. I cannot scan from my Brother Machine.**

---

