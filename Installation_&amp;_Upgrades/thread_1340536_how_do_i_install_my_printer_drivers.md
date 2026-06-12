---
title: "how do i install my printer drivers?"
date: 2009-11-28
forum: Installation &amp; Upgrades
---

### Post by expxe on 2009-11-28
i downloaded them from samsung's website and extracted them, now what? i tried double clicking on various files, no workie. **comon ubuntu, always gotta do things the hard way! **now i can;t believe i have to ask this, this should have been made simpler in linux. the programmers can take a lesson from windows and apple. so now how do you install programs in linux? :popcorn:

is there a way to contact the ubuntu programmers directly to let them know that their OS is still in the dumps and let them know of the ways to improve it?

---

### Post by wilee-nilee on 2009-11-28
Did you try system-administration-printing-add to see if your printers drivers were already available in the data base.

---

### Post by sgosnell on 2009-11-28
If they're .deb files, as they should be, you can just right-click on them and select Open with gdebi.  I have no idea how Samsung distributes its drivers, though.  What I've always done with other brands is just open System/Administration/Printing, select Add a new printer, and let the wizard get and install the drivers.

---

### Post by expxe on 2009-11-28
> **wilee-nilee said:**
> Did you try system-administration-printing-add to see if your printers drivers were already available in the data base.

my printer isn't listed, the model is samsung ml-2240

> **sgosnell said:**
> If they're .deb files, as they should be, you can just right-click on them and select Open with gdebi.  I have no idea how Samsung distributes its drivers, though.  What I've always done with other brands is just open System/Administration/Printing, select Add a new printer, and let the wizard get and install the drivers.

all i get is a bunch of files in folders, here is the download link if you want to see what i mean (click on Driver to get a list): [http://www.samsung.com/au/consumer/print-solutions/print-multifunctions-copiers/archive/ML-2240/XSA/index.idx?pagetype=prd_detail&tab=support](http://www.samsung.com/au/consumer/print-solutions/print-multifunctions-copiers/archive/ML-2240/XSA/index.idx?pagetype=prd_detail&tab=support)

i downloaded the first two files

---

### Post by samigina on 2009-11-28
What kind of file has you downloaded? Sure is for linux?

And, yes, theres a way to tell the developers what you think, but please, be gentle, remember that Linux is an OS made by the community for the community, there no big corporations behind... so, if you disagree with the printer support for linux you must disagree with the manufacturer, not with the os.

Mhhh i found the way... just a little search in samsug website:

[http://ars.samsung.com/customer/usa/jsp/faqs/faqs_view_us.jsp?AT_ID=60562&PROD_ID=29&PG_ID=-1&PROD_SUB_ID=0]("http://ars.samsung.com/customer/usa/jsp/faqs/faqs_view_us.jsp?AT_ID=60562&PROD_ID=29&PG_ID=-1&PROD_SUB_ID=0")

---

### Post by expxe on 2009-11-28
> **samigina said:**
> What kind of file has you downloaded? Sure is for linux?

And, yes, theres a way to tell the developers what you think, but please, be gentle, remember that Linux is an OS made by the community for the community, there no big corporations behind... so, if you disagree with the printer support for linux you must disagree with the manufacturer, not with the os.

Mhhh i found the way... just a little search in samsug website:

[http://ars.samsung.com/customer/usa/jsp/faqs/faqs_view_us.jsp?AT_ID=60562&PROD_ID=29&PG_ID=-1&PROD_SUB_ID=0](http://ars.samsung.com/customer/usa/jsp/faqs/faqs_view_us.jsp?AT_ID=60562&PROD_ID=29&PG_ID=-1&PROD_SUB_ID=0)

hmmm, that link shows how to install from cd. 

i downloaded the files from the samsung website and extracted them to my desktop, i am unsure what is the next step

---

### Post by samigina on 2009-11-28
Again, what kind of files?

THeres something like a "setup.sh" thats an srcitp, right click, permissions, and make it executable; linux is so secure that it dont leave the files to be  executables by default.

---

### Post by expxe on 2009-11-28
yep, i see a install.sh, so i right clicked and selected run in terminal and then it states the root permission needed.

---

### Post by sgosnell on 2009-11-29
I've had luck with the wizard by just selecting the nearest available model, but again I've never used a Samsung printer.

For the root privileges, you need to use sudo.  In a terminal, cd to the directory containing install.sh, then type "sudo ./install.sh", enter your password when prompted, and it should run.  Or you can run Nautilus as root, either from the menus or from a terminal with "gksudo nautilus &", and then run it in a terminal as you already did.  You need superuser or root privileges to make any changes to your system files in Linux, as a security feature, to prevent virus/trojan/malware from hosing your system.

---

### Post by samigina on 2009-11-29
So, the problem is solved?

If not, i will give you a short instructions:

Right click on your "setup.sh" file.
Choose the properties, go to the permissions tab, and select "allow execute the file like a program".
Then try to run it just with a double click, if doesn't work, open a terminal in the location of the file (theres a nautilus extension "terminal here" in synaptic) and type "sudo ./setup.sh".

---

### Post by expxe on 2009-11-29
> **samigina said:**
> So, the problem is solved?

If not, i will give you a short instructions:

Right click on your "setup.sh" file.
Choose the properties, go to the permissions tab, and select "allow execute the file like a program".
Then try to run it just with a double click, if doesn't work, open a terminal in the location of the file (theres a nautilus extension "terminal here" in synaptic) and type "sudo ./setup.sh".

nope, i got this error

[IMG]http://img12.imageshack.us/img12/2387/screenshot1tk.png[/IMG]

comon ubuntu......its suppose to be easy :popcorn:

---

### Post by samigina on 2009-11-30
Sure you are using the "sudo" command I give you? That command is for run with admin privileges .

It seems like the program need a library that is not installed in your system, that libstdc... but is asking for an old version. Are you sure that your printer model is not already in the database, what model is it?

Please try running it with the "sudo".

---

### Post by expxe on 2009-11-30
my printer is a samsung ml 2240

---

### Post by expxe on 2009-11-30
ok, i installed the printer by sudo ./install.sh

now it can print, but when i switch the usb plug from my computer to my usb hub and try to print, it asks for authentication password, i did not set this, what is going on and how to fix this strange problem?

---

