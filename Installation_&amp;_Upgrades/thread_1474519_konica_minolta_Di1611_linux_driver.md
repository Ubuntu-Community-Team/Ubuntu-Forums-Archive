---
title: "konica minolta Di1611 linux driver"
date: 2010-05-06
forum: Installation &amp; Upgrades
---

### Post by miroi on 2010-05-06
Dear all,

I donwloaded driver installation files for konica minolta Di1611 printer from [here]("http://forums.linux-foundation.org/file.php?27,file=163") ,
( reachable only from this post in the [thread ]("http://forums.linux-foundation.org/read.php?27,4244"):
**Re: Minolta [di1611]("http://forums.linux-foundation.org/read.php?27,4244")** 
             Posted by: **[EMAIL="wagnerpasinato@terra.com.br"]Wagner[/EMAIL]** (IP  Logged)
       Date: June 06, 2008 07:20AM
).

Installation files in "                      [cups_pclv1.6.tar.gz  (95.5KB)]("http://forums.linux-foundation.org/file.php?27,file=163")" look well, but the problem is perl script "install.pl", giving 
----------------------------------------------------------------- 
 sudo install.pl

Installation procedure for Konica Minolta drivers is starting.
No such file: 
usage:     install [CUPS configuration file]
Exiting
ilias@miro-kch:~/Stiahnuté/cups_pclv1.6/.
--------------------------------------------------

Some help is needed to make them running on Ubuntu Linux. Best, M.

---

### Post by lechien73 on 2010-05-06
Is cups installed and running on your configuration? Can you confirm if the file /etc/cups/cupsd.conf exists, since that's what the script is looking for?

---

### Post by lechien73 on 2010-05-06
Actually, having looked at the cupsd.conf file, the format has changed. The install.pl script will not be able to locate the correct directories.

I've modified the perl script to set the data directories to defaults, if it fails to find them in the cupsd.conf file.

Extract the attached file, and replace the existing install.pl script with this new one, then check the contents of the script before running:

```
sudo ./install.pl
sudo service cups restart

```
Proceed to install the printer through cups as usual.

---

### Post by miroi on 2010-05-12
Thanks, I did it.
-------------------------------------------------------------------------------------------------------------------------------------
[email]ilias@miro-kch:~/Stiahnuté/cups_pclv1.6/.sudo[/email] ./install.pl
[sudo] password for ilias: 

Installation procedure for Konica Minolta drivers is starting.
PPD Dir is: /usr/share/ppd/openprinting/KONICA_MINOLTA, Data Dir is: /etc/cups/ppd.
Installation starting
Installing PPD files to /usr/share/ppd/openprinting/KONICA_MINOLTA

    Installing c350_pcl.ppd! Newer PPD version already installed!
    Installing pi3505e_pcl.ppd! Newer PPD version already installed!
    Installing di2011_cups_foomatic.ppd! Newer PPD version already installed!

Installing Filter files to /usr/lib/cups/filter

Older filter version found!
Overwriting older filter version!
Installing kmfilterpcl 

Installation procedure finished!

To install printers you can use the CUPS webinterface for example.
Please restart the CUPS server now

[email]ilias@miro-kch:~/Stiahnuté/cups_pclv1.6/.sudo[/email] service cups restart
 * Restarting Common Unix Printing System: cupsd                         [ OK ] 
ilias@miro-kch:~/Stiahnuté/cups_pclv1.6/.
-------------------------------------------------------------------------------------------------------------------------------------------

When adding printer, I used Di2011 which appears among konica minolta printers.

---

### Post by chzumbrunnen on 2010-05-12
I had a very similar problem, just another printer from Konica Minolta (C650). The install script seemd to work and I'm now able to install the printer to some degree.

First I'm not sure wich connection I have to choose:

1) AppSocket/JetDirect network printer via DNS-SD
2) IPP network printer via DNS-SD
3) LPD network printer via DNS-SD

In any case drivers are beeing searched (and not found) and I get a chance to enter the path to a PPD file.

I can than enter the path to the downloaded file and get a chance to enter the installable options like Finisher, Punch z-fold unit etc...
This looks great... but sadly after entering the correct data here I next get the form to enter the printer description and than an error message stating something like: missing driver. the printer »KONICA-MINOLTA-C650-Series« needs the program »femperonpsc250mu.pl« which is not installed. Please install before using the printer.

(As I have a Swiss-German system the message is in German:

Fehlender Treiber
Der Drucker »KONICA-MINOLTA-C650-Series« benötigt das Programm »femperonpsc250mu.pl«, welches derzeit nicht installiert ist. Bitte installieren Sie es, bevor Sie den Drucker verwenden.)

The file »femperonpsc250mu.pl« is in the downloaded folder, but I don't know where to copy it to.

---

### Post by cgsharp on 2010-05-27
> **miroi said:**
> Thanks, I did it.
-------------------------------------------------------------------------------------------------------------------------------------
[email]ilias@miro-kch:~/Stiahnuté/cups_pclv1.6/.sudo[/email] ./install.pl
[sudo] password for ilias: 

Installation procedure for Konica Minolta drivers is starting.
PPD Dir is: /usr/share/ppd/openprinting/KONICA_MINOLTA, Data Dir is: /etc/cups/ppd.
Installation starting
Installing PPD files to /usr/share/ppd/openprinting/KONICA_MINOLTA

    Installing c350_pcl.ppd! Newer PPD version already installed!
    Installing pi3505e_pcl.ppd! Newer PPD version already installed!
    Installing di2011_cups_foomatic.ppd! Newer PPD version already installed!

Installing Filter files to /usr/lib/cups/filter

Older filter version found!
Overwriting older filter version!
Installing kmfilterpcl 

Installation procedure finished!

To install printers you can use the CUPS webinterface for example.
Please restart the CUPS server now

[email]ilias@miro-kch:~/Stiahnuté/cups_pclv1.6/.sudo[/email] service cups restart
 * Restarting Common Unix Printing System: cupsd                         [ OK ] 
ilias@miro-kch:~/Stiahnuté/cups_pclv1.6/.
-------------------------------------------------------------------------------------------------------------------------------------------

When adding printer, I used Di2011 which appears among konica minolta printers.

Hi. I did it, but the printing not work. I have installed Ubuntu 10.04. Any suggestions? Thanks.

---

### Post by doi65535 on 2010-06-25
I've also added the printer with above procedure, everything seems ok, but it does not print... any ideas?

---

### Post by margamanos on 2011-01-12
> **doi65535 said:**
> I've also added the printer with above procedure, everything seems ok, but it does not print... any ideas?

Similar problem, any ideas?

Thanks in advance

---

### Post by loupio on 2012-08-08
Hi all, 

Did someone managed to make it work?
I realy need this printer to work cause i'm merging my entreprise to xubuntu, and this printer is my only problem 

*[COLOR="DimGray"]Sorry for my bad english[/COLOR]*

---

### Post by henrycha on 2012-09-15
Same Problem, i hope someone help us

---

### Post by raptor1972 on 2012-12-20
anyone found a solution for this ?

it seems im totally missing the PPD files,
where can I get them ?

---

### Post by jarek3 on 2013-10-08
Hi Guys,

Has anybody got a driver for this printer? The source page of the driver from this thread is missing and it seems that generic drivers are also useless.


Thanks,
J

---

